---
title: "Interpret &amp; Print HTML/PHP From Command Line"
date: 2007-04-18
forum: General Help
---

### Post by anyjoesoap on 2007-04-18
Hi,

I'm new to Ubuntu/linux (great so far!) and am looking for some general suggestions on how to solve the below...

I want to interpret and print HTML files (which will include php code accessing a database) from my command line. E.g. something like

% PrintCommand 'http://www.domain.com/index.php' | lpr -P PrinterName

I have CUPS setup and working fine. Do I need 3rd party software to ensure the HTML will be interpreted and print correctly? How will PHP be effected. PHP, apache and mysql are also setup and working well the server.

The reason for this is I need to setup a cron job which will automatically print webpages to our office printer every so often.

Many thanks in advance,
Anthony

---

### Post by viciouslime on 2007-04-18
You could maybe look into using a "text-mode" browser, like lynx. Lynx is in the repos (package name lynx) I don't know if it will achieve exactly what you want, but I think it is probably worth a look.

---

### Post by anyjoesoap on 2007-04-18
Thanks viciouslime,

I'll have a look at that. Would ideally like to print images also with text, perhaps creating PDFs would be the way to go? I don't mind having to create specific code and bypassing the need to interpret html/php files, just now looing for a good solution to command line printing. Any further suggestions appreciated.

---

### Post by Renegade of Funk on 2007-04-18
Still have problems with my isa proxy here. But in windows it is posible to use the php.exe file so probably you can also use this in ubuntu. The syntax should be: php index.php for example, but than the output is streamed to the terminal window. So you need to catch that and store it in a file or something. :)

Anway the syntax in linux can be:
php index.php
php-cgi index.php
php-cli index.php

I'm not quite shure but it is worth a try :)

Edit:
Be shure to try the cli (Command Line Interpreter) but i think it is not ported with the default php install so I think you need to apt-get it.

Cheers

---

