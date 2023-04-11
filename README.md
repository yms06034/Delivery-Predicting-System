
# Delivery-Predicting-System
## 개요

해외 Shopping Data를 활용해 정시 배송 예측을 하는 프로젝트 입니다.

## 데이터

- ID: ID Number of Customers.
- Warehouse block: The Company have big Warehouse which is divided in to block such as A,B,C,D,E.
- Mode of shipment:The Company Ships the products in multiple way such as Ship, Flight and Road.
- Customer care calls: The number of calls made from enquiry for enquiry of the shipment.
- Customer rating: The company has rated from every customer. 1 is the lowest (Worst), 5 is the highest (Best).
- Cost of the product: Cost of the Product in US Dollars.
- Prior purchases: The Number of Prior Purchase.
- Product importance: The company has categorized the product in the various parameter such as low, medium, high.
- Gender: Male and Female.
- Discount offered: Discount offered on that specific product.
- Weight in gms: It is the weight in grams.
- Reached on time: It is the target variable, where 1 Indicates that the product has NOT reached on time and 0 indicates it has reached on time.

## 과정

결측치와 이상치에 대해 분석을 진행하고 정의한 가설을 확인합니다.
출고 창고 위치에 따른 정시 도착 배소 여부 확인 등 데이터 비교 등을 확인하였습니다.
또한 각 특성별 분포 KDE를 확인하여 가설의 증빙을 더 해 주었습니다.
XGBoost 모델을 사용해 예측을 하였으며, SelectKBest를 적용해 Features 이전 모델과 비교하여 최종 모델을 선택하였습니다.
PDP(Partial Dependence Plot)로 모델 해석을 진행 하였습니다.

## 결과

이 과정을 통해 몇몇 특성들이 정시 배송도착 여부에 영향을 주는 것을 확인 하였습니다.
가장 큰 특징 중의 하나는 제품의 할인률에 따라 정시배송이 나뉜다는 점이 였습니다.
그 특성은 제품의 무게, 제품의 가격, 제품 출고지와 비교하여도 할인률이 10%가 넘어가면 정시 배송 도착이 안된다고 하였습니다.
너무 의아해서 다른 모델로 적용도 해보고, 가중치를 변경해서 학습도 진행하였지만 동일한 결과치가 나왔습니다.
이러한 경우라면 제가 분석한 데이터 이외의 다른 데이터를 확인하여 할인된 제품이 어떤 것인지를 파악하고 FFM 전략을 고려해 볼 수 있을 것입니다.

## 출력 예시
- 각 특성별 분포 kde

![image](https://user-images.githubusercontent.com/98085184/231072990-cdc256eb-832c-4cc6-8e61-12961b5dd25c.png)

- 모델 예측 점수  

![1111](https://user-images.githubusercontent.com/98085184/231073752-69b6bdf9-8d24-4aad-aa0b-c7ea76e5059b.png)

- PDP 차트  

![image](https://user-images.githubusercontent.com/98085184/231073267-4d00b517-619f-4e10-8dc0-84f2884fe622.png)
