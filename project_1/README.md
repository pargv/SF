# Проект 1. Анализ вакансий на hh.ru

<img src = https://raw.githubusercontent.com/AndreyRysistov/DatasetsForPandas/main/hh%20label.jpg alt="drawing" style="width:300px;">

## Оглавление  
[1. Описание проекта](.README.md#Описание-проекта)  
[2. Какой кейс решаем?](.README.md#Какой-кейс-решаем)  
[3. Краткая информация о данных](.README.md#Краткая-информация-о-данных)  
[4. Этапы работы над проектом](.README.md#Этапы-работы-над-проектом)  
[5. Результат](.README.md#Результат)    
[6. Выводы](.README.md#Выводы) 

## Описание проекта   
Мы исследуем данные с вакансиями с HeadHunter.  
Проблема, с которой столкнулась компания, состоит в том, что часть соискателей не указывает желаемую заработную плату, когда составляют своё резюме. Это является помехой для рекомендательной системы HeadHunter, которая подбирает соискателям список наиболее подходящих вакансий, а работодателям — список наиболее подходящих специалистов. Компания HeadHunter хочет построить модель, которая бы автоматически определяла примерный уровень заработной платы, подходящей пользователю, исходя из информации, которую он указал о себе. В данном проекте мы проводим первичную обработку данных: преобразуем их к удобному виду, очищаем и проводим разведывательный анализ.


## Какой кейс решаем?    
Задача состоит в том, чтобы реализовать средствами Python преобразования реального датасета вакансий с сайта hh.ru к удобному для анализа данных виду (извлечь и создать новые информативные признаки из громоздких и "сырых" данных). Затем провести очистку данных, включая поиск выбросов, а также первичный разведовательный анализ. 

**Что практикуем**     
Навыки преобразования, очистки и первичного разведовательного анализа данных с помощью методов визуализации Python для Data Science.

## Краткая информация о данных:

Данные представляют собой таблицу с вакансиями с сайта hh.ru, где содержится основная информация о соикателях, включающая опыт работы, возраст, город проживания, желаемую заработную плату, пожелания о занятости и др. Ссылка на датасет:

https://disk.yandex.ru/d/e5O6Gge0bHk98g

В папке data приложен файл ExchangeRates.csv с данными о курсах валют с сайта MDF.ru

## Этапы работы над проектом:

1) Базовый анализ структуры данных.

2) Преобразование данных.

3) Разведывательный анализ.

4) Очистка данных.

5) Загрузка jupyter-ноутбука в репозиторий на GitHub
и оформление описания проекта в README.md.


## Результат  

В качестве результата проекта получен DataFrame (cleaned_df), содержащий преобразованный и очищенный датасет с вакансиями с сайта hh.ru. 

В процессе работы проведены следующие преобразования:

1) Признак "Образование и ВУЗ" удален и преобразован в категориальный признак "Образование" с 4 уровнями: "высшее", "неоконченное высшее", "среднее", "среднее специальное";

2) Признак "Пол и возраст" преобразован в два отдельных признака "Пол" и "Возраст". 

3) Признак "Опыт работы", содержащий строки (например, "Опыт работы 1 год" или "Опыт работы 4 месяца" и т.п.) преобразован к более удобному признаку "Опыт работы (месяц)", содержащий целочисленное значение (число месяцев, сколько проработал соискатель).

4) Признак «Город, переезд, командировки» преобразован в
отдельные признаки «Город», «Готовность к переезду», «Готовность к командировкам». Признак «Город» категориальный: «Москва», «Санкт-Петербург», «город-миллионник» и «другие». Признаки «Готовность к переезду» и «Готовность к командировкам» имеют два возможных варианта: True или False.

5) Признаки «Занятость» и «График» преобразованы с помощью метода One Hot Encoding (см. схему).

<img src=https://raw.githubusercontent.com/AndreyRysistov/DatasetsForPandas/main/ohe.jpg>

6) Признак заработной платы «ЗП» преобразован в признак «ЗП (руб)» — заработная плата в рублях, причем при его преобразовании использовались реальные данные по курсам валют на даты, соответствующие датам загрузок резюме соискателей в исходном датасете.

7) Данные очищены от дупликатов, удалены строки, где есть пропуски в столбцах с местом работы и должностью,
Пропуски в столбце с опытом работы заполнены медианным значением. Удалены аномальные резюме, в которых указана заработная плата либо выше 1 миллиона рублей, либо ниже 1 тысячи рублей. В процессе разведывательного анализа были обнаружены резюме, в которых опыт работы в годах превышал возраст соискателя. Такие резюме также были удалены из данных.


## Выводы  

Проект демонстрирует методы для преобразования и очистки данных средствами Pandas на примере с реальными данными о вакансиях с hh.ru. Процесс преобразования неподготовленных, сырых данных в подходящий для анализа вид требует много различных манипуляций. Продемонстрировано создание новых информативных признаков. Проведен небольшой разведывательный анализ с помощью средств визуализации Python. Показано, что в данных присутствуют выбросы. 