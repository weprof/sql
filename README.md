# SQL Ödevler

## SQL ödev 1

- **film** tablosunda bulunan **title** ve **description** sütunlarındaki verileri sıralayınız. 

  ``SELECT title, description FROM film; ``

- **film** tablosunda bulunan tüm sütunlardaki verileri film uzunluğu (length) 60 dan büyük **VE** 75 ten küçük olma koşullarıyla sıralayınız.

  `` SELECT * FROM film WHERE length > 60 AND length < 75; ``

- **film** tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99 **VE** replacement_cost 12.99 **VEYA** 28.99 olma koşullarıyla sıralayınız.

  `` SELECT * FROM film WHERE rental_rate = 0.99 AND replacement_cost < 12.99 OR replacement_cost = 28.99;``

- **customer** tablosunda bulunan first_name sütunundaki değeri 'Mary' olan müşterinin last_name sütunundaki değeri nedir?

  `` SELECT * FROM CUSTOMER WHERE first_name = 'Mary';`` Smith

- **film** tablosundaki uzunluğu(length) 50 ten büyük OLMAYIP aynı zamanda rental_rate değeri 2.99 veya 4.99 OLMAYAN verileri sıralayınız.

  `` SELECT * FROM film WHERE NOT(NOT(NOT(length > 50 AND rental_rate = 2.99 OR rental_rate = 4.99)));``
  


 ## SQL ödev 2

- **film** tablosunda bulunan tüm sütunlardaki verileri replacement cost değeri 12.99 dan büyük eşit ve 16.99 küçük olma koşuluyla sıralayınız ( BETWEEN - AND yapısını kullanınız.)

  `` SELECT * FROM film WHERE replacement_cost BETWEEN 12.99 AND 16.99; ``

- .**actor** tablosunda bulunan first_name ve last_name sütunlardaki verileri first_name 'Penelope' veya 'Nick' veya 'Ed' değerleri olması koşuluyla sıralayınız. ( IN operatörünü kullanınız.)

  `` SELECT * FROM actor WHERE (first_name IN ('Penelope', 'Nick', 'Ed')) AND (last_name IN ('Penelope', 'Nick', 'Ed'));``

- **film** tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99, 2.99, 4.99 **VE** replacement_cost 12.99, 15.99, 28.99 olma koşullarıyla sıralayınız. ( IN operatörünü kullanınız.)

  `` SELECT * FROM film WHERE rental_rate IN(0.99,2.99,4.99) AND replacement_cost IN(12.99,15.99,28.99);``

## SQL Ödev 3

- **country** tablosunda bulunan **country** sütunundaki ülke isimlerinden 'A' karakteri ile başlayıp 'a' karakteri ile sonlananları sıralayınız.

  `` SELECT * FROM country WHERE country LIKE 'A%a';``

- **country** tablosunda bulunan **country** sütunundaki ülke isimlerinden en az 6 karakterden oluşan ve sonu 'n' karakteri ile sonlananları sıralayınız.

  `` SELECT * FROM country WHERE country LIKE '______%n'; ``

- **film** tablosunda bulunan **title** sütunundaki film isimlerinden en az 4 adet büyük ya da küçük harf farketmesizin 'T' karakteri içeren film isimlerini sıralayınız.

  ``SELECT * FROM film WHERE title LIKE '____%' OR title ILIKE '%t%';``

- **film** tablosunda bulunan tüm sütunlardaki verilerden **title** 'C' karakteri ile başlayan ve uzunluğu (length) 90 dan büyük olan ve rental_rate 2.99 olan verileri sıralayınız.

  ``SELECT * FROM film WHERE title LIKE 'C%' AND length > 90 AND rental_rate = 2.99;``
  
## SQL Ödev 4

- **film** tablosunda bulunan **replacement_cost** sütununda bulunan birbirinden farklı değerleri sıralayınız.

  ``SELECT DISTINCT replacement_cost FROM film;``

- **film** tablosunda bulunan **replacement_cost** sütununda birbirinden farklı kaç tane veri vardır?

  ``SELECT COUNT(DISTINCT replacement_cost) FROM film;``

  21

- **film** tablosunda bulunan film isimlerinde (title) kaç tanesini T karakteri ile başlar ve aynı zamanda rating 'G' ye eşittir?

  ``SELECT COUNT(*) FROM film WHERE title LIKE 'T%' AND rating = 'G';``

  9

- **country** tablosunda bulunan ülke isimlerinden (country) kaç tanesi 5 karakterden oluşmaktadır?

  ``SELECT COUNT(*) FROM country WHERE country LIKE '_____';``  

  13

- **city** tablosundaki şehir isimlerinin kaçtanesi 'R' veya r karakteri ile biter?

  ``SELECT COUNT(*) FROM city WHERE city LIKE 'R%' OR city LIKE '%r';``

  45

## SQL Ödev 5 

- **film** tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en uzun (length) 5 filmi sıralayınız.

  ``SELECT * FROM film WHERE title LIKE ('%n') ORDER BY length DESC LIMIT 5;``

- **film** tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en kısa (length) ikinci 5 filmi sıralayınız.

  ``SELECT * FROM film WHERE title LIKE ('%n') ORDER BY length ASC OFFSET 5 LIMIT 5;``

- **customer** tablosunda bulunan last_name sütununa göre azalan yapılan sıralamada store_id 1 olmak koşuluyla ilk 4 veriyi sıralayınız.

  ``SELECT * FROM CUSTOMER WHERE store_id = 1 ORDER BY last_name LIMIT 4;``
  
  ## SQL Ödev 6

- **film** tablosunda bulunan **rental_rate** sütunundaki değerlerin ortalaması nedir?

  ``SELECT AVG(rental_rate) FROM film;``

- **film** tablosunda bulunan filmlerden kaçtanesi 'C' karekteri ile başlar

  ``SELECT COUNT(title) FROM film WHERE title LIKE ('C%');``

- **film** tablosunda bulunan filmlerden rental_rate değeri 0.99 a eşit olan en uzun (length) film kaç dakikadır?

  ``SELECT MAX(length) FROM film WHERE rental_rate = 0.99;``

- **film** tablosunda bulunan filmlerin uzunluğu 150 dakikadan büyük olanlarına ait kaç farklı replacement_cost değeri vardır?

  ``SELECT COUNT(DISTINCT(replacement_cost)) FROM film WHERE length > 150;``

## SQL Ödev 7

- **film** tablosunda bulunan filmleri **rating** değerlerine göre gruplayınız.

  ``SELECT * FROM film ORDER BY rating;``

- **film** tablosunda bulunan filmleri **replacement_cost** sütununa göre grupladığımızda film sayısı 50 den fazla olan replacement_cost değerini ve karşılık gelen film sayısını sıralayınız.

  ``SELECT replacement_cost, COUNT(*) FROM film GROUP BY replacement_cost HAVING COUNT(*) > 50;``

- **customer** tablosunda bulunan store_id değerlerine karşılık gelen müşteri sayılarını nelerdir? 

  ``SELECT store_id, COUNT(customer_id) FROM customer GROUP BY store_id;``

  1 = 326

  2 = 273

- **city** tablosunda bulunan şehir verilerini **country_id** sütununa göre gruplandırdıktan sonra en fazla şehir sayısı barındıra country_id bilgisini ve şehir sayısını paylaşınız.

  ``SELECT country_id, COUNT(*) FROM city GROUP BY country_id ORDER BY COUNT(*) DESC LIMIT 1;``

  44 - 60
  
  
  ## SQL Ödev 9

- **city** tablosu ile **country** tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.

  ``SELECT * FROM CITY JOIN COUNTRY ON COUNTRY.COUNTRY_ID=CITY.COUNTRY_ID;``

- **customer** tablosu ile **payment** tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.

  ``SELECT PAYMENT.PAYMENT_ID, CUSTOMER.FIRST_NAME, CUSTOMER.LAST_NAME FROM PAYMENT JOIN CUSTOMER ON CUSTOMER.CUSTOMER_ID=PAYMENT.CUSTOMER_ID;``

- **customer** tablosu ile **rental** tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.

  ``SELECT RENTAL.RENTAL_ID, CUSTOMER.FIRST_NAME, CUSTOMER.LAST_NAME FROM RENTAL JOIN CUSTOMER ON CUSTOMER.CUSTOMER_ID=RENTAL.CUSTOMER_ID;``

  ## SQL Ödev 10

- **city** tablosu ile **country** tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz LEFT JOIN sorgusunu yazınız.

  ``SELECT city, country FROM city LEFT JOIN country ON city.country_id = country.country_id; ``

- **customer** tablosu ile **payment** tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz RIGHT JOIN sorgusunu yazınız.

  ``SELECT PAYMENT_ID, FIRST_NAME, LAST_NAME FROM CUSTOMER RIGHT JOIN PAYMENT ON PAYMENT.CUSTOMER_ID=CUSTOMER.CUSTOMER_ID;``

- **customer** tablosu ile **rental** tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz FULL JOIN sorgusunu yazınız.

  ``SELECT RENTAL_ID, FIRST_NAME, LAST_NAME FROM CUSTOMER FULL JOIN RENTAL ON RENTAL.CUSTOMER_ID=CUSTOMER.CUSTOMER_ID;``
  
  ## SQL Ödev 11

- **actor** ve **customer** tablolarında bulunan **first_name** sütunları için tüm verileri sıralayalım.

  ``(SELECT FIRST_NAME FROM ACTOR) UNION (SELECT FIRST_NAME FROM CUSTOMER);``

  ``(SELECT FIRST_NAME FROM ACTOR) UNION ALL(SELECT FIRST_NAME FROM CUSTOMER);``

- **actor** ve **customer** tablolarında bulunan **first_name** sütunları için kesişen verileri sıralayalım.

  ``(SELECT FIRST_NAME FROM ACTOR) INTERSECT (SELECT FIRST_NAME FROM CUSTOMER);``

  ``(SELECT FIRST_NAME FROM ACTOR) INTERSECT ALL (SELECT FIRST_NAME FROM CUSTOMER);``

- **actor** ve **customer** tablolarında bulunan **first_name** sütunları için ilk tabloda bulunan ancak ikinci tabloda bulunmayan verileri sıralayalım.

  ``(SELECT FIRST_NAME FROM ACTOR) EXCEPT (SELECT FIRST_NAME FROM CUSTOMER);``

  ``(SELECT FIRST_NAME FROM ACTOR) EXCEPT ALL (SELECT FIRST_NAME FROM CUSTOMER);``

- İlk 3 sorguyu tekrar eden veriler için de yapalım.




## SQL Ödev 12

- **film** tablosunda film uzunluğu **length** sütununda gösterilmektedir. Uzunluğu ortalama film uzunluğundan fazla kaç tane film vardır?

  ``SELECT COUNT(*) FROM FILM WHERE LENGTH >(SELECT AVG(LENGTH) FROM FILM);``

- **film** tablosunda en yüksek rental_rate değerine sahip kaç tane film vardır?

  ``SELECT COUNT(*) FROM FILM WHERE RENTAL_RATE = (SELECT MAX(RENTAL_RATE) FROM FILM);``

- **film** tablosunda en düşük rental_rate ve en düşün replacement_cost değerlerine sahip filmleri sıralayınız.

  ``SELECT * FROM FILM WHERE RENTAL_RATE = (SELECT MIN(RENTAL_RATE) FROM FILM) AND REPLACEMENT_COST = (SELECT MIN(REPLACEMENT_COST) FROM FILM);``

- **payment** tablosunda en fazla sayıda alışveriş yapan müşterileri(customer) sıralayınız.

  ``SELECT customer_id,first_name,last_name,(SELECT COUNT(*) FROM payment p WHERE p.customer_id = c.customer_id) as payment FROM customer C  ORDER BY payment DESC;``

