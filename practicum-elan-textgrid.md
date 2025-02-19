## ELAN - токенизация, грамматическая разметка, импорт/экспорт

В этом практикуме мы будем работать с расшифровками, созданными вами ранее. Для разных слоев реплик и переводов мы создадим дочерние слои с разметкой на уровне слова.      

### 1.1 Токенизация   
Письменный текст, в том числе письменную расшифровку устного текста, в корпусной разметке принято делить на предложения, а предложения, в свою очередь, на токены.
К токенам, в частности, относятся:
* словоформа  
* знак пунктуации   
* эмодзи (или их комбинация, записанная без пробелов)  
* хэштег  
* мультитокен (multi-word expression) - сложный предлог (_в течение_), союз (_но и_) и т.д., состоящий из нескольких словоформ - в тех корпусах, где принято выделять мультитокены  


### 1.2 Токенизация слоя в ELAN   
* Создайте новый тип, если нужно, и слой для токенов   
* Слой > Токенизировать слой... 
* Укажите родительский слой, который будет разбиваться на токены, и слой, в который должны быть вставлены словоформы   
  * (стандартные параметры: разделитель - пробел)
* PROFIT!
* Еще раз проведите токенизацию, указав особые параметры деления на токены  
  * разделитель - пробел   
  * знаки препинания - укажите те знаки препинания, которые вам нужно выделить в отдельные токены    
* <img src="https://github.com/olesar/lingdata/blob/gh-pages/fig/elan_9.png">


### 2.1. Частеречная разметка токенов   
Если у вас нет слоя частей речи (POS), импортируйте его из файла образца. Переименуйте его и перепривяжите к слою Words одного из говорящих. (Слой -> Изменить...)

* Слой -> Создать аннотации на зависимых слоях... (выбрать слой-источник) -> Next -> (выбрать конечный слой)
В слое POS должны появиться пустые аннотации. Выберите часть речи из открывающегося списка, double-кликая на каждой аннотации.


### 3. Конвертация между ELAN и TextGrid  

#### 3.1. Экспорт в TextGrid  
Разметку .eaf файла можно представить в TextGrid вьюере и сохранить в табличном формате  
* Файл -> Экспорт -> Текст с разделителями (CSV)
* Параметры таблицы: имя слоя, начальное время, конечное время, аннотация  

#### 3.2. Импорт из TextGrid  
* Файл -> Импорт -> Текст с разделителями (CSV)  
Укажите, какие столбцы какому типу информации соответствуют (имя слоя, начальное время, конечное время, аннотация).  
После этого нужно указать свойства каждого слоя,  так как TextGrid эту информацию не хранит.  
* Тип -- Импортируйте типы слоев из файла-образца ELAN, чтобы у вас появились типы utterance, word и т. д.  
* Слой - Изменить -- задайте свойства слоя (тип utterance, метку говорящего, разметчика, язык)  

