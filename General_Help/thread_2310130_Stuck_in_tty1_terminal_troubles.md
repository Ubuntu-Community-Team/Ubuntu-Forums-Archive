---
title: "Stuck in tty1 terminal troubles"
date: 2016-01-16
forum: General Help
---

### Post by rivendell2 on 2016-01-16
So I'm just gonna start off with I'm not a big user of Ubuntu because it never seems to work how it should, now to my problem. 
After finally finishing the long process of installing and updating repositories on a Ubuntu branch OS, I restart the computer to make some changes it pushes me into the tty1 Terminal.

The tty1 terminal immediately requests a username and password sorta like ssh does so I put in root followed by my password and it logs in, I read up that when this happens you just type
 startx and it opens up the GUI like magic, but when I do it fails to start and I have to begin the long process of installing the OS and everything again, is there a possible way to NEVER allow 
the computer from entering this limbo world by closing off the tty1 terminal or just uninstalling this feature completely as its out of date?

---

### Post by ajgreeny on 2016-01-16
Simple answer; no.

The lack of a GUI desktop after an update is very often the result of a graphic card driver or kernel update that needs the driver reinstalling.

You will, however, have to tell us a lot more about your hardware and your ubuntu version, plus a bit more about exactly what you see when you do this:-
> so I put in root followed by my password and it logs inwhich does not make much sense to me as there is no root account enabled in ubuntu by default.

So please; much more information and we'll try to help.

---

