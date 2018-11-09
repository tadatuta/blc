# Код, в котором есть ошибка

За день команда разработки сделала несколько новых фич. Но при подготовке релиза произошли мерж-конфликты, и после их разрешения вёрстка разъехалась. Необходимо срочно избавиться от ошибок минимальным количеством исправлений в коде, чтобы релиз успел попасть в продакшен.

Вам предоставляется HTML-страница с поломанными стилями и макет в формате PNG (результат, который ожидается). Необходимо исправить ошибки, чтобы результат при просмотре в Chrome стал совпадать с оригинальным скриншотом. Исправленную страницу отправьте как решение задачи.

### Макет
![](https://raw.githubusercontent.com/tadatuta/blc/gh-pages/original1.png)

### HTML-страница с поломанными стилями

https://raw.githubusercontent.com/tadatuta/blc/gh-pages/problem1.html

## Решение

В этом задании мы постарались сымитировать ситуацию, с которой регулярно сталкиваются разработчики Яндекса — в огромной кодовой базе найти те самые несколько простых строк кода, исправление которых приводит к нужному результату.
То есть сложность состояла не в том, чтобы написать код, а в том, чтобы понять, где именно его написать (или удалить).

Мы взяли реальный код поисковой выдачи и внесли буквально несколько правок, которые развалили верстку.
У участников соревнования было меньше часа, чтобы разобраться с ~250кб верстки и привести код к состоянию, соответствующему макету.

Понятно, что ограничение времени на соревнование не позволяло прочитать весь код, поэтому участникам следовало воспользоваться инструментами для разработчиков в браузере.

Для исправления одного из четырех вариантов задания достаточно было таких изменений:

```diff
diff --git a/blitz.html b/blitz.html
index 36b9af8..1e30545 100644
--- a/blitz.html
+++ b/blitz.html
@@ -531,10 +531,6 @@ iframe[src$='ext-analytics.html'] {
   height: auto;
 }

-.search2__button .suggest2-form__button :nth-child(1){
-    background: #ff0 !important;
-}
-
 /* ../../blocks-desktop/input/__control/input__control.styl end */
 /* ../../node_modules/islands/common.blocks/input/__clear/input__clear.css begin */
 /* Позиционируется относительно input__box.
@@ -744,10 +740,6 @@ iframe[src$='ext-analytics.html'] {
     background-clip: padding-box;
 }

 .input_theme_websearch .input__clear {
     background-image: url("/static/web4/node_modules/islands/common.blocks/input/_theme/input_theme_websearch.assets/clear.svg");
     background-size: 16px;
@@ -857,6 +849,7 @@ iframe[src$='ext-analytics.html'] {
   background-color: #f2cf46;
 }
 .websearch-button__text:before {
+  position: absolute;
   top: -6px;
   right: -9px;
   width: 0;
@@ -866,8 +859,6 @@ iframe[src$='ext-analytics.html'] {
   border-style: solid;
   border-color: rgba(255,219,76,0);
   border-left-color: inherit;
-  position: relative;
-  z-index: -1000;
 }

 /* ../../blocks-deskpad/websearch-button/websearch-button.styl end */
@@ -1349,6 +1340,7 @@ iframe[src$='ext-analytics.html'] {
   font-size: 14px;
   line-height: 40px;
   position: relative;
+  display: inline-block;
   height: auto;
   padding: 0;
   vertical-align: middle;
```
