# 그리디(탐욕법) 알고리즘

- 현재 상황에서 당장 좋은 것만 선택하는 알고리즘

## 예제 3-1 거스름돈

### 문제
- 거스름돈을 거슬러 줘야할 때, 500원,100원,50원,10원짜리 동전이 무한히 존재한다고 가정
- 이 때, 줘야할 동전의 최소 개수를 구하라, 단 거슬러 줘야할 돈 N는 항상 10의 배수이다.

### 문제 해설
- 가장 큰 화폐 단위부터 돈을 거슬러 주면 된다.
---
남은 돈 : 1260원

| 화폐단위 | 500   |100   |50   |10   |
|------|------|------|------|------|
|   갯수  | 0|0|0|0|

---

남은 돈 : 260원

| 화폐단위 | 500   |100   |50   |10   |
|------|------|------|------|------|
|   갯수  | 2|0|0|0|

---

남은 돈 : 60원

| 화폐단위 | 500   |100   |50   |10   |
|------|------|------|------|------|
|   갯수  | 2|2|0|0|
---

남은 돈 : 10원

| 화폐단위 | 500   |100   |50   |10   |
|------|------|------|------|------|
|   갯수  | 2|2|1|0|
---

남은 돈 : 0원

| 화폐단위 | 500   |100   |50   |10   |
|------|------|------|------|------|
|   갯수  | 2|2|1|1|
---
<code>

    n = 1260  
    count = 0  

    // 큰 단위의 화폐뷰터 차례대로 확인  
    list = [500, 100, 50, 10]
    cnt = []
    result = {}

    for coin in list:
        cnt.append(n // coin)
        n %= coin

    result = dict(zip(list,cnt))
    print('동전별 갯수 : ',result)
    print('총 동전의 갯수 :  ',sum(cnt))

</code>

### Point
위 소스코드의 시간 복잡도는 O(k)이다.  
이 알고리즘의 시간 복잡도는 동전의 총 종류에만 영향을 받고, 거슬러 줘야하는 금액의 크기와는 무관하다.

### 정당성
거스름 돈 문제를 그리디 알고리즘으로 해결할 수 있는 이유는 
> 가지고 있는 동전 중에서 큰 단위가 항상 작은 단위의 배수이다.  

따라서 작은 단위의 동전들을 종합해 다른 해가 나올 수 없기 때문이다.

다른 예시를 보면
> 거스름 돈 800원  
> [case1] 500 + 100 + 100 + 100 = 4개  
> [case2] 400 + 400 = 2개   

이렇게 위 알고리즘을 따를 경우 case1이 되지만 실제 최적의 해는 case2이다. 이 경우에는 그리디 알고리즘으로 해결할 수 없고, 다이나믹 프로그래밍을 이용하여 해결할 수 있다. 


대부분의 그리디 알고리즘 문제에서는 이처럼 문제 풀이를 위한 최소한의 아이디어를 떠올리고 이것이 정당한지 검토할 수 있어야 답을 도출할 수 있다.






## 다시 풀어야할 문제
- 숫자카드게임
- 만들수없는금액
- 볼링공
- 무지의먹방라이브