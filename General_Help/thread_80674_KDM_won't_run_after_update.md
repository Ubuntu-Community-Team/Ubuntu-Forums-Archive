---
title: "KDM won't run after update"
date: 2005-10-22
forum: General Help
---

### Post by byourg on 2005-10-22
I updated this morning and when I restarted my computer, Usplash ran OK but instead of running KDM it went to a tty1 login screen. I logged in and typed kdm and it said "root only wants to run kdm". Any help?

---

### Post by Xian on 2005-10-22
First make sure you have KDM installed.
From a terminal:
$ sudo apt-get install kdm

Then attempt to configure it:
$ sudo dpkg-reconfigure kdm

---

### Post by byourg on 2005-10-22
Tried those and did not work. Did a fresh install with update and all is well so far.

---

### Post by IanVaughan on 2006-01-27
Reinstalling seems a bit extream, but it might be my only option as well.

I know KDM is installed as I used it to log in the 1st time, but the thing that stoped KDM showing was me changing the xorg.conf, must of been dislpay size/depth problem.

The reason I was changing xorg.conf? I have a ATI Radeon, of which doesnt go to the highest resolution!

---

### Post by Jucato on 2006-01-27
Just for further info:

[QUOTE=byourg]I logged in and typed kdm and it said "root only wants to run kdm". Any help?[/QUOTE]

Actually, only root can start/stop kdm. so the command should be
```
 sudo /etc/init.d/kdm start 
``` or stop, depending on the case.

If it says that KDM is already running, try typing 
```
startx
``` and see what happens. If there is something wrong, it will throw you back at the terminal, but it will also display what errors occured. It happened to me lots of times, especially after upgrading. Usual problem would be errors in xorg.conf, an updated video card driver using the wrong kernel, etc.

Just keep these in mind next time something goes wrong w/ KDM. Might save you the hassle of reinstalling. :D

---

