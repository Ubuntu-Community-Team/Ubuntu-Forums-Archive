---
title: "Lag when starting any application"
date: 2007-10-28
forum: General Help
---

### Post by carvalhais on 2007-10-28
I am experiencing a very odd behaviour after my first install of Ubuntu. Whenever I try to start an application (any one), it takes a long lag before the application appears on the screen.
I can start the app from the menu, or just type it's name in the terminal. I'm running Gusty in a HP Pavilion DV5000, and went trough the install procedure with all the default settings (except for choosing reiserfs as the file system, instead of ext3)... the strange thing, is that I saw that other users have having issues with Gutsy and HP laptops, but the whole thing just worked out of the box for me.
Does anyone have any clue?

---

### Post by samosamo on 2007-10-28
do this: sudo hdparm -Tt /dev/hdX and post your results, could be an hd controller driver problem

---

### Post by carvalhais on 2007-10-28
After running the command, I got the following answer:

```
/dev/sda:
 Timing cached reads:   2540 MB in  2.00 seconds = 1270.74 MB/sec
 Timing buffered disk reads:  116 MB in  3.03 seconds =  38.28 MB/sec

```

---

### Post by kapoc on 2007-11-01
Hi, I have same symptoms. When I tried:
'ifconfig eth0 down'
lags dissapeared. Try and report. I don't know resolution yet :(

---

### Post by kapoc on 2007-11-01
I have found resolution :) (ok, I have been told resolution)

Append your hostname to localhost line in /etc/hosts. And that's all :).
so my looks like:

127.0.0.1 localhost kaponote

---

