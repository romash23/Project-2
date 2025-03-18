# <center> Проект 2. Анализ вакансий из HeadHunter

## Оглавление
[1. Описание проекта](https://github.com/romash23/project-2/blob/master/README.md#Описание-проекта)  
[2. Какой кейс решаем?](https://github.com/romash23/project-2/blob/master/README.md#Какой-кейс-решаем)  
[3. Краткая информация о данных](https://github.com/romash23/project-2/blob/master/README.md#Краткая-информация-о-данных)  
[4. Этапы работы над проектом](https://github.com/romash23/project-2/blob/master/README.md#Этапы-работы-над-проектом)  
[5. Результат](https://github.com/romash23/project-2/blob/master/README.md#Результат)    
[6. Выводы](https://github.com/romash23/project-2/blob/master/README.md#Выводы) 


### Описание проекта

В данном проекте будет проводится анализ базы данных о вакансиях, взятые с сайта HeadHunter.ru. Суть проекта: попрактиковаться в написании *SQL*-запросов на реальнных данных и проанализировать их.

### Краткая информация о данных

 Сама база данных является являтся интелектаульной собственностью компании Skillfactory :sunglasses: . По это причине в данной проекте нет возможности выложить исходные данные или ссылку на них.

 *Сама база данных состоит из нескольких таблиц:*
 * VACANCIES - эта таблица хранит в себе данные по вакансиям и содержит следующие столбцы: 
 
 <img src=https://lms-cdn.skillfactory.ru/assets/courseware/v1/837cf6ff79f483e387a16c993634f3e4/asset-v1:SkillFactory+DST-3.0+28FEB2021+type@asset+block/SQL_pj2_2_2.png width="600" height="280">

 * AREAS - таблица-справочник, которая хранит код региона и его название

 <img src=https://lms-cdn.skillfactory.ru/assets/courseware/v1/682c2306f3d46a25915a89d4ec7e16ed/asset-v1:SkillFactory+DST-3.0+28FEB2021+type@asset+block/SQL_pj2_2_3.png width="600" height="95">

 * EMPLOYERS - таблица-справочник со списком работодателей

<img src=https://lms-cdn.skillfactory.ru/assets/courseware/v1/d2a26db623c75572c71923b57241e038/asset-v1:SkillFactory+DST-3.0+28FEB2021+type@asset+block/SQL_pj2_2_4.png width="600" height="130">

* INDUSTIES - таблица-справочник вариантов сфер деятельности работодателей

<img src=https://lms-cdn.skillfactory.ru/assets/courseware/v1/2c76bca09937a1a05a9e66d51008e298/asset-v1:SkillFactory+DST-3.0+28FEB2021+type@asset+block/SQL_pj2_2_5.png width="600" height="95">

* EMMPLOYERS_INDUSTRIES - дополнительная таблица, которая существует для организации связи между работодателями и сферами их деятельности

<img src=https://lms-cdn.skillfactory.ru/assets/courseware/v1/16ff3df0bb0ddecd922562f3c4bdd32c/asset-v1:SkillFactory+DST-3.0+28FEB2021+type@asset+block/SQL_pj2_2_6.png width="600" height="110">

Сами таблицы связаны друг с другом через специальные колонки - id следующим образом:

<img src=https://lms-cdn.skillfactory.ru/assets/courseware/v1/efd63819603e7d4f4433ed2fedec717c/asset-v1:SkillFactory+DST-3.0+28FEB2021+type@asset+block/SQL_pj2_2_1.png width="400" height="400">

:point_right: [К оглавлению](https://github.com/romash23/project-2/blob/master/README.md#%D0%9E%D0%B3%D0%BB%D0%B0%D0%B2%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5)


### Этапы работы над проектом

Работа над проектом была разбита на несколько частей:

#### 1. *Знакомство с данными* 

То есть это первичное знакомство с данными, не подразумевающее какие-либо серьезных вычислений. На данном этапе были изучены взаимосвязи между таблицами, а также что содержат в себе сами колонки с данными. Также в данном блоке был изучен метод *read_sql_query* из библиотки *Pandas* и было настроено соеденение с базой данных с помощью библиотки *psycopg2*.

#### [2. *Предварительный анализ данных*](https://github.com/romash23/Project-2/blob/master/%D0%9F%D1%80%D0%BE%D0%B5%D0%BA%D1%82-2.%20%D0%90%D0%BD%D0%B0%D0%BB%D0%B8%D0%B7%20%D0%B2%D0%B0%D0%BA%D0%B0%D0%BD%D1%81%D0%B8%D0%B9%20%D0%B8%D0%B7%20HeadHunter.ipynb#Юнит)

После знакомства с данными, мы приступили непосредственно к анализу данных. В данном блоке было сделано несколько простейших *SQL*-запросов к БД с помошью агрегатной функии *count*: было вычислено количетсво строк (уникальных *id*):  в таблицах *vacancies, employers, areas* и *industries*

#### [3. *Детальный анализ вакансий*](https://github.com/romash23/Project-2/blob/master/%D0%9F%D1%80%D0%BE%D0%B5%D0%BA%D1%82-2.%20%D0%90%D0%BD%D0%B0%D0%BB%D0%B8%D0%B7%20%D0%B2%D0%B0%D0%BA%D0%B0%D0%BD%D1%81%D0%B8%D0%B9%20%D0%B8%D0%B7%20HeadHunter.ipynb#%D0%AE%D0%BD%D0%B8%D1%82-4-%20%D0%94%D0%B5%D1%82%D0%B0%D0%BB%D1%8C%D0%BD%D1%8B%D0%B9-%D0%B0%D0%BD%D0%B0%D0%BB%D0%B8%D0%B7-%D0%B2%D0%B0%D0%BA%D0%B0%D0%BD%D1%81%D0%B8%D0%B9)

На этом этапе были применены более сложыне *SQL*-запросы к БД. Была использована фильтрация данных с помошью *WHERE*, а также применена группировка данных с помощью *GROUP BY*. В итоге были получены такие данные как: Топ-5 городов по количеству вакансий, границы зарплатной вилки, количество вакансий для каждого группы из графы *experience* (Опыта работы) и другие значения.

#### 4. *Анализ работодателей*

В данной блоке работа проходила преимущественно с таблице о работодателях - EMPLOYERS. Но по причине того, что сама таблица содержит не очень много данных, а именно: название ограгизации, ее id и название региона (города), который она представляет. Поэтому в данном разделе помимо фильтрации и группировки данных были использованы соединения с другими таблицами с помощью различных видов *JOIN*-ов. Также в этом разделе были полученны данные (список городов-миллионников) с сайта [*Wikipedia*](https://ru.wikipedia.org/wiki/%D0%93%D0%BE%D1%80%D0%BE%D0%B4%D0%B0-%D0%BC%D0%B8%D0%BB%D0%BB%D0%B8%D0%BE%D0%BD%D0%B5%D1%80%D1%8B_%D0%A0%D0%BE%D1%81%D1%81%D0%B8%D0%B8). Для этого были использованы библиотки *requests* и *BeautifulSoup*.
После анализа выяснилось, что компания Яндекс является самой популярной компанией в этой БД: у нее больше всего вакансий, самый большой охват по регионам, а также, что ее вакансии представлены во всех городах-миллиониках России

#### 5. *Предметный анализ*

Этот блок был посвящен детальному анализу таблицы VACANCIES. Также на этапе работы был создан шаблон запросов для вакансий, подходящих датасайентистам. Была изучена графа *key_skills* (ключевые навыки) специалистов-DS, а также вычислен их средний уровень зарплаты. Для этого были использованы функикции *avg, roung, coalesce*.

#### 6. *Дополнительные исследования*

Допольнительно было проведено 2 исследования: изучены данные о сферах деятельности, а также получена зависимость среднего уровня заработной платы от числа ключевых навыков и опыта работы. Оба этих исследования были визуализированы для наглядядности с помощью библиотек *matplotlib* и *seaborn*.

:point_right: [К оглавлению](https://github.com/romash23/project-2/blob/master/README.md#%D0%9E%D0%B3%D0%BB%D0%B0%D0%B2%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5)

### Выводы

В данном проекте мы на практике применили знания, полученные ранее: работа с библиотеками *psycopg2*, *requests*, *BeautifulSoup*, создание запросов к базам данных с помощью языка *SQL*. Одним из ключевых навыков датасайентиста оказалось знание SQL, что ж в данном проекте мы смогли удостовериться в его необходимости. Но также, мы узнали, что владения инструментами *SQL* и *Python* для специалиста-DS крайне важно, но недостаточно: в среднем для устройства на работу на должность ученого по данным нужно иметь в среднем 6,41 ключевой навык. Поэтому не стоит останавливаться на достигнутом, нас  ждет еще масса интересных заданий и увлекательных проектов 

:point_right: [К оглавлению](https://github.com/romash23/project-2/blob/master/README.md#%D0%9E%D0%B3%D0%BB%D0%B0%D0%B2%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5)
