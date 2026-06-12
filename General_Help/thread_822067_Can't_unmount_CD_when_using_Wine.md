---
title: "Can't unmount CD when using Wine"
date: 2008-06-07
forum: General Help
---

### Post by aikomiko on 2008-06-07
Hi,

  Any time I try to install a game that uses more than one CD for install under wine, I cannot unmount the first CD so I can insert the second CD.  The install app itself seems to lock the cdrom as busy, but the app is requesting the 2nd CD.  I have tried both with .iso files and Cds but neither work.  In particular I have been trying Elite Forces2 with no luck.

Any help would be much appreciated.

---

### Post by Shazaam on 2008-06-07
I ran into this problem before.:)  See here.....
[http://ubuntuforums.org/showthread.php?p=2817955#post2817955](http://ubuntuforums.org/showthread.php?p=2817955#post2817955)
sudo eject works if you get stuck.

---

### Post by mc4man on 2008-06-07
I don't exactly remember method (never install from multiple cd's ) but i think it goes like this (run the setup from wine drive)
Find what your drive designation is in winecfg (mine is E)
```
doug@doug-desktop:~$ cd .wine
doug@doug-desktop:~/.wine$ wine E:\setup.exe
```
replace setup.exe with what's on cd if different
This should allow you to eject

---

### Post by aikomiko on 2008-06-08
Wine Eject.  Beautiful,  exactly what I needed.

  Thanks all!

- Ubuntu forums rock!  No wonder Billy G is scared of Linux. :guitar:

---

### Post by rkrisher on 2008-06-13
I just discovered by playing around and tested a way to do it before coming across this post.  Spreading it around to a lot of posts because I've been searching for months for ways to do it.

in terminal or under start/run, type "wineconsole cmd"

This brings you to a windows like dos terminal.

change into your CDROM disk typing "d:" or whatever your drive letter is

type in your setup program name, i.e.: "setup.exe" or "install.exe"

the install will start. Change to your C drive with "C:"

When prompted for disk x, type in "eject"

insert next disk and continue.

Repeat until application is complete.

Remember to let your CD auto-mount by selecting "open in window" or manually mount it before clicking OK at the "Insert CD X" prompt.

Hope it helps.

BTW, you need to use dos commands when exploring around in the command prompt.  Like "dir" instead of the "ls" we got used to.

---

