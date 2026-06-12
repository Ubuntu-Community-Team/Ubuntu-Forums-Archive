---
title: "Default status in Ubuntu is changed by other browsers"
date: 2015-06-13
forum: General Help
---

### Post by ineuw on 2015-06-13
Although I need other browsers to check changes to css files of Wikipedia, FF is my default. Every time Chromium or Opera update themselves, FF default status in the "x-www-browser" file is changed from 200 to 40. I suspect Opera, but can't tell for sure because it shows no date for their latest update. I am using FF 38.0.5 beta version which is updated every couple of days and that's when the default status is lost. It is a locked root file to which access requires a password and I have no idea how an external file can override file security. Is there any way I can stop this?

By the way, this happened before when Google replaced my DDG search engine with their own.

-rw-r--r-- 1 root root 191 Jun 13 00:15 x-www-browser

contents
manual

/usr/bin/x-www-browser
x-www-browser.1.gz
/usr/share/man/man1/x-www-browser.1.gz

/usr/bin/firefox
40

/usr/bin/chromium-browser
40

/usr/bin/opera
40
/usr/share/man/man1/opera.1.gz

---

