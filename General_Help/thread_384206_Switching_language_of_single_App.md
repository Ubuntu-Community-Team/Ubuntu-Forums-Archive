---
title: "Switching language of single App"
date: 2007-03-14
forum: General Help
---

### Post by muxecoid on 2007-03-14
Hi. Want everything except epiphany browser to be in English and Epiphany to be in Russian. The only possibility I see is to switch language at login, but it changes the language of absolutely everything. How do I change switch locales of single apps? And how do I allow different users have different locales?

---

### Post by daengbo on 2007-03-14
use the LANGUAGE environmental variable to set the language of an individual application. For example:

LANGUAGE="ko_KR.utf8" epiphany

on the command line will launch epiphany with Korean menus. Create a launcher for this and put it on the desktop or in a panel to make it easy to start.

---

### Post by muxecoid on 2007-04-14
Did not work:

Failed to execute child process "LANGUAGE=ru_RU.utf8" (No such file or directory)

---

