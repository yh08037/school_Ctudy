# C터디 4주차 [2018.11.28]

## 공지사항
* 이 문서의 단축 URL은 https://goo.gl/HpuFRN 입니다.

<br>

## 문제 4-1 3초 세기 [3]

대헌이는 <2018 국제 시계 안보고 3초 세기(count)> 대회에 출전하려고 합니다. 대헌이는 그 대회에 출전하기 위해서, 피나는 연습을 할 것입니다.

<2018 국제 시계 안보고 3초 세기> 대회는 3초 세는것을 5번 시행하여 나온 시간의 오차를 점수로 환원하여 순위를 가립니다. 국제대회에서 설정하는 점수는 다음과 같습니다.
<br>

| 오차(초) | 1번 시행당 점수 |
|----|----|
|±0.05|20|
|±0.1|12|
|±0.15|7|
|±0.2|3|

이를테면 측정값이 3.021초이면 20점을 얻고 2.900초이면 12점을 얻게 되고, 3.201초이면 점수를 받지 못하는 시스템입니다.

<보기>를 참고하여 3초 주기마다 엔터(\n)를 입력하여, 엔터를 입력한 사이의 시간을 소수 3째자리까지 출력하고, 그에 대한 적절한 점수를 판정하여 출력하세요.

<보기>
time.h 헤더 파일에 들어있는 명령어중, clock() 명령어는 함수를 선언한 시점으로부터 현재까지의 시간을 ms단위로 저장합니다. clock()를 사용하기 위해서 사전에 time.h의 헤더파일을 불러오고 clock_t clock(void) 를 입력하여 함수 선언이 선행되어야 합니다.
```C
#include <stdio.h>
#include <time.h>

int main(void)
{
    clock_t clock(void); //함수 선언
    float time1, time2;
    char empty;

    printf("엔터를 입력해 보세요. ");
    scanf("%c", &empty);
    time1 = clock();

    printf("엔터를 입력해 보세요. ");
    scanf("%c", &empty);
    time2 = clock();

    printf("엔터를 입력하는데 걸리는 시간은 %.2fms, %.2fms.\n", time1, time2);

    return 0;
}
```
굵은 글씨는 기대 입력입니다.

**실행 예제 1**

엔터를 눌러 시작합니다. 3초마다 엔터키를 5번 누르세요.
**\n *(단순 엔터키 입니다.)*
\n
\n
\n
\n
\n**
각각 실행시키는데 걸리는 시간은 3.165 2.855 3.142 2.880 2.952초 입니다.
각각의 점수는 3 7 7 7 20점이고 총 44점입니다.

**실행 예제 2**

엔터를 눌러 시작합니다. 3초마다 엔터키를 5번 누르세요.
**\n
\n
\n
\n
\n
\n**
각각 실행시키는데 걸리는 시간은 3.181 3.186 3.467 3.428 2.862초 입니다.
각각의 점수는 3 3 0 0 7점이고 총 13점입니다.


## 문제 4-2 물 이등분하기 [9][힌트와 실행예제가 함께라면 3]


세 물통 A, B, C가 있다. 물통 A, B, C의 용량이 주어진다.
물통에 물이 가득차지 않았을 때 일부의 용량을 측정할 수 있는 눈금은 없다고 한다.
현재 물통 A에만 물이 가득 차 있고, 물통 B, C는 비어있다.
이 때 물통 A에 있는 물을 물통 A와 B에 각각 반씩 정확하게 나누어 담으려고 한다.
이와 같이 나누어 담는 방법이 존재하면, 그 방법을 순서대로 출력하고,
나누어 담는 방법이 존재하지 않는다면 "나누어 담는 방법이 존재하지 않습니다."를 출력하는 프로그램을 작성하시오.
단, A의 용량은 짝수이며, B의 용량은 A의 용량의 반보다 크거나 같으며, C의 용량은 A의 용량의 반보다 작거나 같다.

<힌트1> 봉 인 해 제
물은 항상 A에서 C, C에서 B, B에서 A로 순환한다. 예를 들어 A->C, C->A 과정이 함께 존재한다면 비효율적인 알고리즘이 될 뿐이다. 또한 A에서 B, B에서 C, C에서 A로 순환시키는 것은 불가능하다.
<힌트2>
물통 A는 측량의 기능을 가지고있지 않다. 측량이 가능한 물통은 B와 C뿐이다. 이때 A에서 C로 보내는 과정은 C의 용량의 단위로 물을 담아내는 과정이고, B에서 A로 보내는 과정은 B의 용량만큼 모아서 측량된 물을 없애는 과정이다.
<힌트3>
A->C의 횟수를 m, B->A의 횟수를 n이라 했을 때, (B의 용량)* m-(C의 용량)* n=A/2를 만족하는 음이 아닌 정수 m, n이 존재하면 물을 반으로 나누어 담는 방법이 존재한다.
<힌트4>
A의 용량/2가 B의 용량과 C의 용량의 최대공약수의 배수이면 A에 가득 담긴 물을  반으로 나누어 담는 방법이 존재한다.


**실행 예제 1**
A의 용량 : **12**
B의 용량 : **9**
C의 용량 : **3**

1단계 : 물통 A의 물을 물통 C에, 물통 C가 가득 찰 때까지 붓는다. (9, 0, 3)
2단계 : 물통 C의 물을 전부 물통 B에 붓는다. (9, 3, 0)
3단계 : 물통 A의 물을 물통 C에, 물통 C가 가득 찰 때까지 붓는다. (6, 3, 3)
4단계 : 물통 C의 물을 전부 물통 B에 붓는다. (6, 6, 0)
<br>
**실행 예제2**
A의 용량 : **12**
B의 용량 : **9**
C의 용량 : **5**

1단계 : 물통 A의 물을 물통 C에, 물통 C가 가득 찰 때까지 붓는다. (7, 0, 5)
2단계 : 물통 C의 물을 전부 물통 B에 붓는다. (7, 5, 0)
3단계 : 물통 A의 물을 물통 C에, 물통 C가 가득 찰 때까지 붓는다. (2, 5, 5)
4단계 : 물통 C의 물을 물통 B에, 물통 B가 가득 찰 때까지 붓는다. (2, 9, 1)
5단계 : 물통 B의 물을 전부 물통 A에 붓는다. (11, 0, 1)
6단계 : 물통 C의 물을 전부 물통 B에 붓는다. (11, 1, 0)
7단계 : 물통 A의 물을 물통 C에, 물통 C가 가득 찰 때까지 붓는다. (6, 1, 5)
8단계 : 물통 C의 물을 전부 물통 B에 붓는다. (6, 6, 0)
<br>

**실행 예제3**
A의 용량 : **14**
B의 용량 : **9**
C의 용량 : **6**

나누어 담는 방법이 존재하지 않습니다.


## 문제 4-3 시침, 분침, 초침 사이의 각도? [2]
스위스에서 손목 시계를 산 준형이는 문득 현재 시각에 대해서 바늘과 바늘 사이의 각도를 알고 싶어졌습니다.

현재시각을 시, 분, 초 각각 입력받고, 시침과 분침사이의 각도, 시침과 초침사이의 각도, 분침과 초침사이의 각도(0도보다 크고 180도보다 작은 값, 소수 2째자리까지 출력)를 출력하세요.
<br>

**실행 예제1**

시, 분, 초를 입력하세요. **10 30 0** *//10시 30분 0초*

시침과 분침 사이의 각도는 135.00도 입니다.

시침과 초침 사이의 각도는 45.00도 입니다.

분침과 초침 사이의 각도는 180.00도 입니다.


**실행 예제2**

시, 분, 초를 입력하세요. **10 11 12**

시침과 분침 사이의 각도는 121.60도 입니다.

시침과 초침 사이의 각도는 126.40도 입니다.

분침과 초침 사이의 각도는 4.80도 입니다.

<br>

## 문제 4-4 아파트 그리기 [2]
통일소식을 들은 한재원군은 전자공학에서 바로 건축공학으로 전과하여 졸업해서 취직했습니다. 재원군은 통일된 북한땅에 수많은 건물들을 놓을 생각을 하니 벌써 신이나고 두근거립니다. 그런데 재원군의 상사가 갑!자!기! 모든 길이에 대해 대처할 수 있는 아파트 설계도를 만들라고 하네요!!!

다음 출력 예시에 대한 규칙을 잘 숙지하고 입력값(3보다 큰 홀수)에 대한 적절한 출력값을 만들어 재원이가 상사의 숙제를 잘 마칠 수 있도록 해 주세요

<규칙>
길이가 5 이면
```
*****  *은 벽 D는 창문 `는 지면을 표현한 것입니다.
*   *
*   *
* D *
*   *
'''''
```

길이가 9이면
```
*********
*       *
* D D D *
*       *
* D D D *
*       *
* D D D *
*       *
'''''''''
```

길이가 13이면

```
*************
*           *
* D D D D D *
*           *
* D D D D D *
*           *
* D D D D D *
*           *
* D D D D D *
*           *
'''''''''''''
```

**실행 예제 1**
길이를 입력하세요. **7**
```
*******
*     *
* D D *
*     *
* D D *
*     *
'''''''
```

**실행 예제 2**
길이를 입력하세요. **19**
```
*******************
*                 *
* D D D D D D D D *
*                 *
* D D D D D D D D *
*                 *
* D D D D D D D D *
*                 *
* D D D D D D D D *
*                 *
* D D D D D D D D *
*                 *
* D D D D D D D D *
*                 *
* D D D D D D D D *
*                 *
* D D D D D D D D *
*                 *
'''''''''''''''''''
```