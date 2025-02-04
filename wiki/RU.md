
# Добро пожаловать в проект модификации регистров для драйверов TRINAMIC, а нынче уже ANALOG DEVICES... 

## О проекте
Прошивка Klipper предоставляет мощные возможности для управления 3D-принтерами, однако, чтобы достичь максимальной производительности и правильной работы такого важного узла как "привод", требуется тщательная настройка параметров управления шаговыми двигателями.
Наш проект создан с целью предоставления вам руководство по оптимизации параметров драйверов для различных типов ШД.

### В данный момент программа поддерживает следующие кинематики: `CoreXY / Hbot / Cartesian` `2/4 WD / CoreXY Hybryd`

## Ликбез
Зачем оно нужно?
 1. Существует как минимум 2 "основных" регистра, это никто иные как TBL (Comparator blank time) и TOFF (Turn-Off Time), они оба отвечают за отключение и подачу питания на мосфеты которые в свою очередь открываются на обмотки ШД, влияя тем самым на потерю токов. Исходя из этого небольшого контекста, можно
    уже сделать вывод, что благодаря подбору правильного управления током на наши обмотки, мы уменьшаем помехи, "лишние" токи, которые мешают работе мотора. То есть сбивают угол ротора, вибрируют, а энергия просто так трансформируется в тепло, поглощаясь корпусом, а это, в свою очередь, означает, что и момент ротора тоже теряется.
 2. Подводя итоги, конечно шаговые двигатели можно использовать на стандартных регистрах, однако это попросту неэффективно. Конечно, может произойти и так, что стандартные регистры окажутся оптимальными, однако это маловероятно. 
    Проведя исследования, мы выяснили, что правильный подбор режимов управления двигателем придает ему до 30% момента, снижает вибрации вплоть до 10ти раз. Что же касается тепловыделения, оно уменьшается на ~15% в моем случае. (Этот тест весьма затяжен и сложен, другого фидбека у меня нет).
 3. Важно обратить внимание, регистры актуальны только для конкретной пары: `драйвер - мотор`, и зависят от конкретной реализации драйвера. Так же стоит учесть, что характеристики мотора по заявлениям производителя имеют до +-20% разбега, как и погрешность замера, акселерометра, так что, не стоит удивляться разбегу параметров на разных установках.

## Содействие
Мы приветствуем вклад от сообщества! Если у вас есть опыт и советы по тюнингу шаговых двигателей, не стесняйтесь делиться материалом с нами. Предоставляйте информацию о протестированных шаговых двигателях.

### Дальнейшие [инструкции](/wiki/wiki.md), удачи!

### [Поддержать](https://ko-fi.com/altzbox) проект

### Контакты -  @altzbox @mrx8024 telegram / discord
