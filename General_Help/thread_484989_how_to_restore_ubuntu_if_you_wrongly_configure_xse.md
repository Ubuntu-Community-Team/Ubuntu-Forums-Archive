---
title: "how to restore ubuntu if you wrongly configure xserver-xorg"
date: 2007-06-26
forum: General Help
---

### Post by umairsaeed219 on 2007-06-26
ONCE i have  posted a thread 
[http://ubuntuforums.org/showthread.php?t=269811](http://ubuntuforums.org/showthread.php?t=269811)  how to change refresh rate and resolution at that time i was using 6.06
 i have tried the saame command posted in above thread to configure xserver-xorg but some thing went wrong now my pc starts but no Graphical interface comes only text base interface which is unreadable plz tell me how to restore it 
the command which i have tried is 
sudo dpkg-reconfigure xserver-xorg
remember the same command has worked when i was tried it on 6.06 in the past

---

### Post by dreadlord_chris on 2007-06-26
> **umairsaeed219 said:**
> ONCE i have  posted a thread 
[http://ubuntuforums.org/showthread.php?t=269811](http://ubuntuforums.org/showthread.php?t=269811)  how to change refresh rate and resolution at that time i was using 6.06
 i have tried the saame command posted in above thread to configure xserver-xorg but some thing went wrong now my pc starts but no Graphical interface comes only text base interface which is unreadable plz tell me how to restore it 
the command which i have tried is 
sudo dpkg-reconfigure xserver-xorg
remember the same command has worked when i was tried it on 6.06 in the past

You really haven't given enough information to help much - but here goes....

The command hasn't changed. So you need to figure out what you changed. 

There are a couple things you can do to at least get back to you graphical logon:

The easiest would be:
```

sudo dpkg-reconfigure xserver-xorg

```
Leave everything the same **except,** for the **driver** choose **vesa**
This will make use of Ubuntu's generic graphics driver - you should be able to get to your desktop now:
```

sudo /etc/init.d/gdm start

```
if you are using KDE change the **gdm** to **kdm**

If, for some reason, that doesn't work for you:
To reset Xserver back to its default settings and start over:
```

sudo dpkg-reconfigure -phigh xserver-xorg

```
You will only be asked to choose monitor resolutions - everything else will be reset.
Now try starting you Desktop.

---

### Post by umairsaeed219 on 2007-06-26
Thanks for your reply
However i am not using the instructions retun by you because i cant wait to get back to ubuntu as soon as possible so i have reinstall ubuntu 7.04
next time when i will configure my xorg i will definately use your instructions
thanks a lot buddy:popcorn:

---

### Post by paletti on 2007-07-23
when starting ubuntu, instead of getting a graphical interface, i get a blue screen with the message **failed to start Xserver. /usr/bin/x: error loading shared libraries: /usrlib/libXfont.so.1  cannot read data file: invalid argument**

i tried the following commands but they don't work:

*sudo dpkg-reconfigure xserver-xorg* gives message:** unable to excecute /usr/sbin/dpkg-reconfigure: permission denied**

*dpkg --configure -a* gives message **dpkg: requested operation requires superuser privilege**

when i try to login as superuser i get the following reply: **su: authentication failure. sorry.** 

i also entered* sudo gedit /etc/x11/xorg.conf* but then i get the message [B][B]cannot open display: (null)
[/B][/B]

pleeeaase, i'm stuck! :( who can help me?

NEW THREAD STARTED HERE: [http://ubuntuforums.org/showthread.php?t=508399](http://ubuntuforums.org/showthread.php?t=508399)

---

