## Overview

이 레포지토리는 네이버, 카카오, 무신사 등 다양한 플랫폼에서 가게 정보, 리뷰, 상품 정보 등 여러 데이터를 크롤링하는 파이썬 및 셀레니움 기반의 노트북을 모아둔 프로젝트입니다.


## Detailed Explanation

웹 페이지에서 데이터를 수집할 때, 가장 먼저 확인할 수 있는 방법은 크롬 개발자도구의 Network > Fetch/XHR 탭입니다. 이곳에 JSON 응답 URL이 보인다면, **해당 요청을 직접 API 형태로 호출**하여 빠르고 안정적으로 데이터를 수집할 수 있습니다. 예를 들어, requests 등을 통해 데이터를 가져올 수 있습니다. 이는 **서버와 비동기 통신을 통해 데이터를 주고받는** 전형적인 구조입니다.

반면, XHR이나 fetch 요청이 전혀 없고, HTML 소스도 비어 있다면, 해당 웹페이지는 **JavaScript가 직접 렌더링하거나 내부 변수로 DOM을 구성하는 구조**일 가능성이 높습니다. 즉, **초기에는 아무 데이터가 없지만, 브라우저가 JavaScript를 실행하면서 화면이 완성되는 방식입니다.** 이 경우에는 API 호출만으로는 데이터를 얻을 수 없기 때문에, 실제 브라우저 환경에서 JavaScript가 실행된 결과를 가져올 수 있는 Selenium 같은 브라우저 자동화 도구가 필요합니다. [비동기통신과 동기통신 feat. 크롤링](https://until.blog/@kirise/%EB%B9%84%EB%8F%99%EA%B8%B0%ED%86%B5%EC%8B%A0%EA%B3%BC-%EB%8F%99%EA%B8%B0%ED%86%B5%EC%8B%A0-feat--%ED%81%AC%EB%A1%A4%EB%A7%81-97uupn5z)


## Notebook Info

1. [카카오 가게 정보 및 리뷰 크롤링](https://github.com/suri-pu-bi/crawling-notebook/blob/main/kakao_place_review.ipynb) 
    - **Selenium 없이 API 요청을 통해** 음식점, 카페, 관광명소, 문화시설 정보와 각 장소에 대한 리뷰를 크롤링합니다.
    - Selenium 보다 API 요청이 더 빠릅니다. 
    - 완료 시 Slack 알림을 보낼 수 있습니다.

2. [무신사 카테고리별 랭킹 상품 정보 크롤링](https://github.com/suri-pu-bi/crawling-notebook/blob/main/musinsa_ranking_product.ipynb)
    - **무신사 랭킹 페이지에서 카테고리별 랭킹 상품 정보를 크롤링**합니다.
    - Selenium으로 상품명, 브랜드, 카테고리, 평점, 리뷰수, 가격, 이미지 URL 등 상세 정보를 수집합니다.

3. [네이버 가게 정보 및 리뷰 크롤링](https://github.com/suri-pu-bi/crawling-notebook/blob/main/naver_place_review.ipynb)
    - 네이버 지도에서 '성수동 놀거리', '성수동 맛집' 등 키워드로 가게 리스트와 리뷰를 크롤링합니다.
    - Selenium을 이용해 가게 이름, 카테고리, 주소, 리뷰 개수, 평점, 방문자 리뷰 등 상세 정보를 수집합니다.
    - **두 개의 iframe을 전환**하며 리뷰 탭, 더보기 버튼 등 동적 요소를 처리합니다.

4. [네이버 블로그 포스팅 및 네이버 플레이스 크롤링](https://github.com/suri-pu-bi/crawling-notebook/blob/main/naver_blog_map_place.ipynb)
    - 네이버 블로그에서 '서울 핫플', 데이트 코스, 맛집 등 키워드로 포스팅을 크롤링합니다.
    - 블로그 본문 중 네이버 플레이스 지도 바로가기 있는 블로그만 추출합니다.
    - 블로그 제목, URL, 날짜, **지도 정보(네이버 플레이스 링크, 주소, 위도/경도 등)를 추출**합니다.


## Ref
- 각 노트북은 크롤링 대상 사이트의 구조 변경 시 정상 동작하지 않을 수 있습니다.
- 대량 데이터 수집 시 서버 부하 및 차단에 유의하세요.
