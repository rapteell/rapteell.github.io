---
title: Інформація
layout: page
permalink: /info
store: false
---

{%- assign utils = false -%}
{%- assign lootboxes = false -%}
{%- assign puppeteer = false -%}
{%- for mod in site.data.modlist -%}
    {%- case mod.name -%}
        {%- when 'ToolkitUtils' %}
            {%- assign utils = true -%}
        {%- when 'ToolkitUtils - Testing' -%}
            {%- assign utils = true -%}
        {%- when 'Puppeteer' -%}
            {%- assign puppeteer = true -%}
        {%- when 'TwitchToolkit - Lootboxes' -%}
            {%- assign lootboxes = true -%}
    {%- endcase -%}
{%- endfor -%}


{%- assign bal = '!bal' -%}
{%- assign buy = '!buy' -%}
{%- for command in site.data.commands -%}
    {%- if command.data.isBal -%}
        {%- assign bal = command.usage -%}
        {%- continue -%}
    {%- endif -%}

    {%- if command.data.isBuy -%}
        {%- assign buy = command.usage -%}
        {%- continue -%}
    {%- endif -%}
{%- endfor -%}

# Ласкаво просимо

Ласкаво просимо на стрім [{{ site.data.social.twitch }}](https://twitch.tv/{{ site.data.social.twitch }}).
Цей стрім використовує мод [Twitch Toolkit](https://steamcommunity.com/sharedfiles/filedetails/?id=3013874066) для забезпечення інтерактивного досвіду. 
У цьому моді є багато речей, які можуть здатися складними навіть досвідченим користувачам, але цей короткий посібник допоможе вам розібратися з ними. 

<br/>

## Що таке Twitch Toolkit?

Twitch Toolkit - це мод від hodlhodl, який дозволяє глядачам впливати на гру кількома способами. 
Найвідомішим є його [крамниця]({{- "/" | relative_url -}}), яка дозволяє вам придбати низку речей, які курує стрімер. 
Залежно від покупки, ці речі з'являються в грі або якимось чином впливають на гру. Ще один спосіб взаємодії 
глядачів з грою - це опитування, які проводить модератор. Вибір в цих опитуваннях значною мірою залежить від того, що увімкнено в моді.

<br/>

## Що таке Coins?

Coins - це валюта моду. Ви можете переглянути свій баланс за допомогою команди `{{ bal }}`. 
{% if utils == true %}
Ви можете помітити що результат використання команди може містити нові смайлики. 
Якщо це так, то ось опис цих смайликів:

- 💰  позначає кількість монет, яку ви маєте на даний момент.
- ⚖  позначає вашу поточну карму.
- 📈 позначає кількість монет, які ви отримуєте щоразу, коли мод нараховує coins.
- 📉 позначає кількість монет, які ви втрачаєте щоразу, коли мод нараховує coins.

{% endif %}

{%- if lootboxes == true -%}
Ви також помітите, що отримаєте повідомлення від бота про наявність лутбоксу. Ви можете відкрити цей лутбокс
за допомогою команди `!openlootbox`, а також перевірити кількість лутбоксів за допомогою `!lootboxes`.
Ви завжди будете отримувати новий лутбокс щодня.
{%- endif -%}

<br/>

## Що таке карма?

Карма - це система, яка намагається обмежити кількість негативних подій, які глядач може придбати за один раз. 
Ця система працює, безпосередньо змінюючи кількість coins, які глядачі періодично отримують. Це означає, що 
чим нижча ваша карма, тим менше ви отримаєте. З надією на те, що негативні події стануть менш інтенсивними, і колонія зможе відновитися.

<br/>

## Використання?

Ви можете використовувати Twitch Toolkit кількома способами, найпоширеніший з яких - через 
[команди]({{- "/commands" | relative_url -}}). Найважливішою командою є команда `{{- buy -}}`, яка є "точкою входу" до купівлі речей у крамниці. 
Іншими помітними командами є команди з префіксом `!mypawn`, які дозволяють вам бачити різноманітну інформацію про вашого пішака. 
Ми не розглядатимемо кожну команду тут, але більшість команд мають бути очевидними або мати опис того, що вони роблять, на сторінці [команди]({{- "/commands" | relative_url -}}). 


{%- if puppeteer -%}
<br/>
## Що таке Puppeteer?

[Puppeteer](https://steamcommunity.com/sharedfiles/filedetails/?id=2057192142) - це мод від Brrainz, який
дозволяє глядачам безпосередньо керувати своїми пішаками, і навіть переглядати деяку інформацію про вашого пішака у
графічному вигляді. Він також перенаправляє деякі відповіді з Twitch Toolkit на свій сайт, щоб трохи почистити чат
. Отже, якщо ви увійшли в Puppeeter і вам цікаво, чому бот не відповідає вам,
спершу перевірте вкладку `TT` на сайті.

{%- endif -%}
