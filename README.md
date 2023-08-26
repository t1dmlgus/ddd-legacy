# 키친포스

## 퀵 스타트

```sh
cd docker
docker compose -p kitchenpos up -d
```

## 요구 사항


- kitchenpos 서비스를 구현한다.

- 상품
  - 등록
    - [ ]  상품을 생성한다.
    - [ ]  상품 가격이 없거나 또는 0 미만일 수 없다.
    - [ ]  상품명이 없거나 또는 https://www.purgomalum.com 사이트 내 욕설 및 원치않는 텍스트로 간주되는 상품명을 사용할 수 없다.

  - 가격 변경
    - [ ]  상품 가격을 변경할 수 있다.
    - [ ]  변경할 가격은 필수값이며, 0 미만일 수 없다.
    - [ ]  상품 가격이 변경되었을 때, ***해당 상품이 적용된 메뉴 가격*** 이 더 크면 메뉴를 비활성화 한다.

  - 조회
    - [ ]  전체 상품을 조회할 수 있다.

- 메뉴
  - 등록
    - [ ]  메뉴를 생성한다.
    - [ ]  메뉴 가격이 없거나 또는 0 미만일 수 없다.
    - [ ]  메뉴로 등록될 상품 및 상품 개수는 필수이며, 상품 개수는 0 미만일 수 없다.
    - [ ]  **_[정책] 메뉴가격이 메뉴 생성시 구성되는 *상품가격 * 갯수* 보다 클 수 없다._** 
    - [ ]  메뉴명이 없거나 또는 https://www.purgomalum.com 사이트 내 욕설 및 원치않는 텍스트로 간주되는 메뉴명을 사용할 수 없다.
    - [ ]  전체 상품 개수 != 메뉴 생성시 등록되는 상품 개수가 같지 않을 경우 예외 ?

  - 가격 변경
    - [ ]  메뉴 가격을 변경할 수 있다.
    - [ ]  변경할 가격이 없거나 0 미만일 수 없다.
    - [ ]  **_[정책] 변경된 메뉴 가격은 구성되는 상품의 갯수 * 가격보다 클 수 없다._**

  - 활성화
    - [ ]  메뉴가격이 메뉴로 구성되는 *상품가격 * 갯수* 보다 클 수 없다.
    - [ ]  메뉴 상태를 활성화한다.  

  - 비활성화
    - [ ]  메뉴 상태를 비활성화한다.

  - 조회
    - [ ]  전체 메뉴를 조회할 수 있다.


- 메뉴 그룹
  - 등록
    - [ ]  메뉴 그룹을 생성한다.
    - [ ]  메뉴 그룹명이 없거나, 빈 값일 수 없다.

  - 조회
    - [ ]  전체 메뉴그룹을 조회한다.


- 주문
  - 생성
    - [ ]  주문 타입이 빈 값일 수 없다.
    - [ ]  메뉴 선택없이 주문 할 수 없다.
    - [ ]  주문 타입이 _EAT_IN_ 이 아닌 경우, 주문하는 메뉴 갯수가 0 미만일 수 없다.
    - [ ]  비활성된 메뉴는 주문을 할 수 없다.
    - [ ]  메뉴 가격과 주문하는 메뉴 가격은 동일하다.
    - [ ]  주문 생성시, 초기 주문 상태는 _WAITING_ 이다.
    - [ ]  주문 타입이 _DELIVERY_ 인 경우, 배송지는 빈 값일 수 없다.
    - [ ]  주문 타입이 _EAT_IN_ 인 경우, 주문 테이블은 비어있어야 한다.
    
  - 주문 접수
    - [ ]  주문 상태가 _WAITING_ 인 경우만, 접수를 할 수 있다.
    - [ ]  주문 타입이 _DELIVERY_ 인 경우, 라이더에게 해당 주문을 배달 요청한다.
    - [ ]  주문 상태를 _WAITING_ 에서 _ACCEPTED_ 로 변경된다.

  - 주문 완료
    - [ ]  주문 상태가 _ACCEPTED_ 인 경우만, 주문 완료를 할 수 있다.
    - [ ]  주문 상태를 _ACCEPTED_ 에서 _SERVED_ 로 변경된다.

  - 배달
    - [ ]  주문 타입이 _DELIVERY_ 인 경우만, 배달을 할 수 있다.
    - [ ]  주문 상태가 _SERVED_ 인 경우만, 배달을 할 수 있다.
    - [ ]  주문 상태를 _SERVED_ 에서 _DELIVERING_ 로 변경된다.

  - 배달 완료
    - [ ]  주문 상태가 _DELIVERING_ 인 경우만, 배달 완료를 할 수 있다.
    - [ ]  주문 상태를 _DELIVERING_ 에서 _DELIVERED_ 로 변경된다.

  - 완료
    - [ ] 주문 타입이 DELIVERY 인 경우, 주문 상태는 DELIVERED 여야 한다.
    - [ ] 주문 타입이 TAKEOUT, EAT_IN 인 경우, 주문 상태는 SERVED 여야 한다.
    - [ ] 주문 테이블이 존재하지 않고, 
    - [ ] 주문 상태를 COMPLETED 로 변경한다.


- 주문 테이블
  - 생성
    - [ ]  주문 테이블명이 없거나, 빈 값일 수 없다.
    - [ ]  주문 테이블 초기 세팅 인원수는 0 이다.
    - [ ]  주문 테이블 초기 세팅은 빈 테이블이다.
    
  - 좌석 할당
    - [ ]  테이블 상태를 '빈' 테이블에서 '채워진' 테이블로 변경한다.

  - 좌석 정리
    - [ ]  주문 테이블이 빈 테이블이 아니고, 주문 상태가 _COMPLETED_ 가 아니면 초기화를 할 수 없다.

  - 인원 변경
    - [ ]  변경하는 인원은 0 명 미만일 수 없다.
    - [ ]  빈 테이블은 인원 변경을 할 수 없다.
    - [ ]  인원을 변경한다.

  - 조회
    - [ ] 전체 주문 테이블을 조회한다.






## 용어 사전

| 한글명 | 영문명 | 설명 |
| --- | --- | --- |
|  |  |  |

## 모델링
