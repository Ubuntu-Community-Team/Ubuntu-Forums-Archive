---
title: "Can't transfer files to Android phone"
date: 2018-09-19
forum: General Help
---

### Post by jacatone on 2018-09-19
I'm using Ubuntu 18.04. Been trying to transfer some video files to my Android 6 phone. Ubuntu detects the phone but when I try doing a copy/paste I get the attached error. When I bring it up in my terminal and try to change the permissions, I get the second error. Anyone know how to fix this? Thanks.

$ /run/user/1000/gvfs/mtp:host=%5Busb%3A002%2C003%5D


Latitude-D630 usr # chmod a+rw /1000/gvfs/mtp:host=%5Busb%3A002%2C003%5D
chmod: cannot access ‘/1000/gvfs/mtp:host=%5Busb%3A002%2C003%5D’: No such file or directory

---

### Post by again? on 2018-09-19
Have you switched to files transfer mode?
When you swipe down from top you can change your usb mode.
[ATTACH=CONFIG]281129[/ATTACH]

When connected in this mode you should see Internal storage in your PC file browser.
[ATTACH=CONFIG]281130[/ATTACH]

---

