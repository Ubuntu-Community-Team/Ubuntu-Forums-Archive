---
title: "libX11 Segmentation fault &amp; no login"
date: 2014-06-12
forum: General Help
---

### Post by jozamm on 2014-06-12
I am using Ubuntu 14.04 Trusty tahr with the shipped kernel (3.13.29). A couple of days ago the login screen does not allow me to log in and in the error log there is a **gnome-session error Segmentation fault on LibX11.so.6.3 error 4**. This line occurs every time I try to log in. I have a Lenovo W530 and I am using the nouveau display driver.


I installed the gnome desktop environment so at login i can choose the environment I want but this hasn't solved the problem. I re-installed Ubuntu and this error cropped up when I did a dist-upgrade on the system.


Any help please because my linux system is completely unusable. I you need any other info I will provide it.

---

### Post by apatters on 2014-06-12
I'm experiencing the same thing. Trusty Tahr, every time I try to log in a gnome-session error gets logged to .xsession-errors indicating a segfault in libX11.so.6.3. gnome-session was upgraded a day or two ago on my system and I believe that's when the error started.

I have Gnome Flashback and Xmonad installed on this system. I can log into a pure Xmona session with no error. But if I try to log into Unity, Gnome Flashback, or Gnome+Xmonad, the error occurs and I'm sent back to the login screen. Since all 3 of these launch gnome-session (I think) I believe the error is in the new gnome-session package.

---

### Post by jozamm on 2014-06-12
Hi,

Try this [http://askubuntu.com/questions/481680/laptop-using-14-04-wont-get-past-login-gui](http://askubuntu.com/questions/481680/laptop-using-14-04-wont-get-past-login-gui) however I haven't tried it myself yet.

Regards,

jozamm

---

### Post by jozamm on 2014-06-13
> **jozamm said:**
> Hi,

Try this [http://askubuntu.com/questions/481680/laptop-using-14-04-wont-get-past-login-gui](http://askubuntu.com/questions/481680/laptop-using-14-04-wont-get-past-login-gui) however I haven't tried it myself yet.


Regards,

jozamm

This article did the trick and now linux is working again.

---

### Post by apatters on 2014-06-14
Removing the eugenesan ppa and following the instructions in the link fixed it for me too, thanks!

---

