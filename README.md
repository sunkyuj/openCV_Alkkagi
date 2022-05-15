# OpenCV를 이용한 알까기 게임

## 1. 목적
키보드나 마우스를 통한 조작 없이 직접 손가락을 튕겨서 알까기 게임을 진행할 수 있도록 한다. 

## 2. 사용한 Library
OpenCV, MediaPipe(손가락 인식), pygame(게임 gui 구현) 등


## 3. How to Run?
### Install Requirements
```
pip install -r requirements.txt
```
### Run python script 
```
python game/main.py
```


## 4. 알까기 게임 - pygame으로 구현 과정
[<참고>](
https://www.petercollingridge.co.uk/tutorials/pygame-physics-simulation/)

1. 손가락으로 자신의 말 고르기 (버튼 or 손가락 수)
    
    1 ) 버튼 - 누를 때 마다 다음 말 지정
    2) 손가락 수 - 버튼 누른 뒤 2초 뒤 인식 영역에서 펴져있는 손가락 수 인식
    -> 손가락 수의 번호 말 지정

2. 알을 발사할 방향 조절

    (버튼 누르면 선택한 알에서 발사 방향 움직임) - L 왼쪽으로 회전, R 오른쪽으로 회전

3. 손가락 튕기기를 통한 파워 계산
    
    엄지손가락 끝과 (검지 혹은 중지) 손가락 끝의 거리가 x 미만일때 측정 시작
    이후 엄지손가락 끝과 해당 손가락 끝의 거리 최대일때까지의 [시간 & 거리] 측정
    
    -> 시간과 거리를 통해 파워 계산
    
    카메라부터 손까지의 거리 : 손바닥 크기를 측정
    일정한 크기의 손바닥을 기준으로 설정



## 5. 게임 진행 방식
1. 게임 시작 후 두 플레이어가 번갈아 가면서 알을 발사
2. while(말이 남아있다면) { 번갈아 가면서 진행

    0\) 확인 버튼 클릭 이후 이전 단계로 돌아가고 싶다면 뒤로 버튼 누르기

    1\) 알 선택 완료 후 확인 버튼 누르기

    2\) 방향 버튼을 통해 방향 설정 확인 버튼 누르기
    
    3\) 발사 준비 버튼 누른 뒤, 손 인식 영역에 손가져오기

    4\) 손가락 튕기기를 통해 알 발사
