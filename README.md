# Верстка одностраничного приложения
Тестовое задание ШРИ-2018, вторая часть: задание на верстку.

Мы хотим проверить, насколько хорошо вы умеете верстать и знаете особенности браузеров. Предлагаем вам сверстать две страницы для сервиса бронирования переговорок из первого задания.

## Задание

Нужно сверстать страницу списка переговрок и форму редактирования встречи. Для каждой страницы дизайнер подготовил макет (отдельно для большого экрана и мобильных телефонов).

Макет (https://yandex-shri-msk-2018.github.io/entrance-task-2)
Репозиторий на GitHub (https://github.com/yandex-shri-msk-2018/entrance-task-2)

Важно сверстать страницы в точном соответствии с макетами. Если какие-то части макетов покажутся вам непонятными, обязательно задавайте уточняющие вопросы — пишите на адрес frontendschool@yandex-team.ru.

### Страница списка переговорок

* В шапке отображается логотип сервиса и кнопка «Создать встречу».
* Слева отображается список переговорок с разбивкой по этажам.
* Справа от списка отображается диаграмма встреч.
* При клике на встречу всплывает тултип с информацией о ней.
* При наведении на свободное время появляется кнопка добавления встречи и подсвечивается название комнаты.
* Названия переговорок, у которых не осталось свободных периодов времени, отображаются менее контрастно.
* На диаграмме вертикальной линией показано текущее время.
* Сверху от списка отображается текущая дата и кнопки перехода к соседним датам.
* При клике на текущую дату отображается календарь на три месяца.
* Макет календаря дизайнер не нарисовал, сверстайте этот блок на своё усмотрение.

### Страница редактирования встречи

* Есть возможность ввести название встречи, дату и время начала и окончания встречи, выбрать участников и переговорку.
* Выпадающий календарь для поля выбора даты делать необязательно, но это будет плюсом.
* Участники встречи выбираются из списка, который появляется, когда пользователь переходит на поле поиска сотрудника.
* Выбранные участники отображаются под полем ввода.
* Если переговорка не выбрана, отображается список доступных комнат.
* Если переговорка выбрана, то вместо списка отображается только она (с возможностью отменить выбор).

## Критерии

В первую очередь мы будем проверять, свёрстаны ли страницы в точном в соответствии с макетами.
Всё должно работать в двух последних версиях Google Chrome, Яндекс.Браузера, Microsoft Edge, Mozilla Firefox, Safari, Opera. По возможности используйте приёмы безопасной деградации CSS.

Уделите внимание организации и оформлению кода. Оптимизация производительности и автоматизация будут плюсом.



# Процесс

## Запуск
```
npm i
npm run start  //Сборка папки "build" и запуск локального сервера
```

Главная страница: https://alivander.github.io/shri-2018-task-2/build/index.html

Страница создания встречи: https://alivander.github.io/shri-2018-task-2/build/event-create.html

Страница редактирования встречи: https://alivander.github.io/shri-2018-task-2/build/event-edit.html

Страница создания встречи с модальным окном: https://alivander.github.io/shri-2018-task-2/build/event-create-modal.html

Страница редактирования встречи с модальным окном: https://alivander.github.io/shri-2018-task-2/build/event-edit-modal.html

1. Изучаем ТЗ и макеты.
2. Скачиваем и конвертируем необходимые шрифты.
3. Готовим HTML. Стараемся сохранить доступность для людей с ограниченными возможностями (хоть это и внутренний сервис, но я знаю, что в Яндексе есть такие замечательные люди как Алексей Любимов), поэтому кое-где рзметка слегка избыточна.
4. Настраиваем автоматизацию сборки с помощью Gulp - преобразование SASS(SCSS) в css, прогон через автопрефиксер, минификацию html, css, js, svg и других изображений при необходимости.
5. Для стилизации используем следующую последовательность шрифтов (информацию о веб-безопасных шрифтах брала здесь https://www.cssfontstack.com):
  * Helvetica Neue - шрифт макета, не является веб-безопасным шрифтом;
  * Helvetica - наиболее схожий веб-беопасный шрифт для Mac;
  * Open Sans - шрифт-fallback для Windows (взят из переписки с Максимовой Мариной по вопросам к тз - frontendschool@yandex-team.ru), не является веб-безопасным шрифтом и не имеет начертания Medium, поэтому начертание Semi-bold сознательно описываем как font-weight: 500, вместо реального веса в 600;
  * Tahoma - веб-беопасный шрифт для Windows;
  * sans-serif - общее семейство шрифтов.
  ВАЖНО! Helvetica Neue - платный шрифт (возможно поэтому он не был предоставлен вместе с макетами), а найденный нелицензионный аналог в интернете некорректно конвертируется в woff2 или woff (кривые скачущие буквы в Firefox) - было проверено на 4х разных конвертерах шрифтов. Приобрести лицензионный у меня нет возможности, поэтому в сборке оставлен имеющийся.
6. Верстаем главную страницу, поля в диаграмме немного выравниваем - все по 66px, наиболее близко к макету. Периоды до 8ч и после 23ч в макетах гуляют от 13px до 52px - берем среднее значение и делаем одинаковыми по 33px (полчаса). Правда в этом случае максимальная ширина макета составит 1301px, а не 1280px, поэтому при 1280px диаграмма все еще будет немного скролиться по горизонтали, но все равно отображаться будет идентично макету.
Чтобы пользователь легко ориентировался по диаграмме, шкала времени остается видна сверху даже при прокрутке диаграммы вниз, но скроллится по горизонтали.
На данном этапе кнопка "+" в свободном слоте оставляем просто по центру. Если останется время попробую заставить ее следовать за курсором в пределах слота.
7. Создаем календарь - в десктопной версии календарь содержит три месяца (текущий - центральный), как и указано в ТЗ, но в мобильной - один. Возможно это отступление от ТЗ, но если пытаться втиснуть 3 месяца на экран телефона, то числа-ссылки будут очень маленькими, пользователю будет крайне сложно попасть по нужной дате. В обычной ситуации я бы обговорила этот момент с дизайнером.
8. Всплывающий тултип с информацией о встрече центруется по ее слоту, а не по экрану как в мобильной версии. Если успею попробую на JS дописать автоматический скролл для того, чтобы центр экрана смещался на тултип при его появлении.
9. Верстаем форму как отдельную секцию главной страницы - при переключении на форму с помощью JS скрывается диаграмма, при открытой диаграмме скрывается форма (это мой первый SPA, другого способа не придумала) - все поля ввода type="text" (Safari не поддерживает type="date" и time="time", select или datalist не поддаются нормальной стилизации). Поля делаем немного резиновыми и с перестроением в два ряда уже на ширине 904px (ширина основного содержимого в десктопной версии), чтобы задействовать больше места на маленьких экранах.
В форме создания встречи добавляем кнопку "Отменить", которой нет в макете (на стриме я спрашивала про нее - сказали что это ошибка макета и она нужна). Так как кнопок теперь две, не увеличиваем "Создать встречу" до размера как в макете - она не влезет. Выравниваем кнопки аналогично странице редактирования встречи - по правому краю, ближе к пальцам пользователя, но и здесь и там немного ровняем отступ - по краю остальных полей.
У календаря в форме тот же принцип - один месяц на маленьких экранах, три на больших. Но здесь текущий месяц - первый, а за ним два следующих. Я не исправляла ссылки на кнопки для единообразия блока, но у прошедших дней отсутствует href, а у текущих с помощью JS будут отменены события по умолчанию.
10. Emoji в модальных окнах вставляем как png. Костыль, но времени мало и всего две emoji на весь макет, которые не будут меняться. Также нет полей, где была бы возможность их ввода пользователем, поэтому такое решение. Разрешение png в два раза больше экранного - для ретины.
11. Частично оживляем верстку с помощью JS. Чтобы можно было проверить переходы по кнопкам, появление кнопок, появление тултипов. Некоторые элементы сверстаны, но скрыты в разметке, так как должны появляться только при определенных условиях.
12. Пока javascript не закончен, чтобы сделать проверку верстки более удобной создаю отдельные html страницы (создание, редактирование встречи, модальные окна) для демонстрации. С главной страницы на них не перейти (пришлось бы менять уже готовую разметку), поэтому прикреплю ссылки в начале описания процесса работы.
13. Что еще можно было добавить, если бы позволяло время: плавные смены состояний у интерактивных элементов, анимации появления/скрытия формы встречи, модальных окон, тултипов, кроссбраузерную поддержку emoji.
