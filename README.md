# Wave Elevation Forecasting using Transformer in PyTorch

## 📌 프로젝트 개요
이 프로젝트는 .ele 형식의 파도고(wave elevation) 데이터를 불러와 시계열 예측을 수행하는 Transformer 모델을 구현한 예제입니다.

데이터 파일: LIN_001_IRR_WAVE.ele

모델 아키텍처: PyTorch 기반 Transformer

예측 대상: 연속된 파도고(wave elevation)를 기반으로 다음 시간 스텝의 값을 예측


## ⚙️ 주요 기능
1. 데이터 전처리

- .ele 파일에서 제목 행 및 헤더를 파싱하고, 데이터 라인을 time과 wave_elevation으로 구분하여 DataFrame으로 변환합니다.

- wave_elevation.csv로 저장 가능.

2. 데이터셋 구성

- 입력 시퀀스 길이(sequence_length)를 기준으로 데이터를 잘라 학습/타깃 데이터를 구성합니다.

- PyTorch Dataset과 DataLoader를 사용해 배치 학습 구성.

3. Transformer 모델

- 입력값을 임베딩한 후, Transformer Encoder로 시계열 정보를 처리합니다.

- 마지막 타임스텝의 출력을 사용해 다음 시점의 파도고를 예측.

4. 모델 학습

- 손실 함수: MSELoss

- 옵티마이저: Adam

- 에폭 수, 시퀀스 길이, 모델 크기 등은 상단 하이퍼파라미터에서 조정 가능.


## 🔍 해석
Loss는 모델이 예측한 값과 실제 값 사이의 평균제곱오차(MSE)를 의미합니다.

Epoch 1에서 Loss: 0.052890로 시작했으며, 점차적으로 감소하여 Epoch 30에서 Loss: 0.031097에 도달했습니다.

손실 값의 꾸준한 감소는 모델이 데이터 패턴을 학습하고 있음을 의미하며, 과적합 없이 안정적으로 학습이 진행된 것으로 볼 수 있습니다.

마지막 Loss 값이 더 이상 크게 줄어들지 않는다면, 에폭 수를 늘릴 필요는 없으며, 이 모델은 예측 성능이 비교적 안정화된 상태라고 판단할 수 있습니다.
