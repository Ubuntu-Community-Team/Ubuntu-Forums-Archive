---
title: "Viewing init ... is this dangerous?"
date: 2014-08-03
forum: General Help
---

### Post by cecilieaux on 2014-08-03
I'm taking an online Linux course at edx.org (LinuxFoundationX: LFS101x Introduction to Linux, it's normally expensive but currently free to audit) and I've come across /sbin/init.

Of course, curiosity killed the Cecilieaux and I wanted to view the file that is so vital to the bootup process. I opened my Gnome Commander (I love two-paned MC-like file managers) and viewed it (read only), but it comes up kinda garbled even viewing it as text.

QUESTION: if I go sudo and open it in, say, gedit, promising (cross my heart and hope to die) that I will NOT save it but merely close it without saving, is there a danger completely breaking my system? I just want to see what init looks like.

TIA

C :shock:

---

### Post by Impavidus on 2014-08-03
/sbin/init is a binary executable. It's not human readable. Ever tried opening a Windows .exe in notepad? Also, it has read permissions for all users so you don't need root permission to read it and the result of reading it with root permissions would be the same.

But to your question: If you don't modify and save init, your won't break your computer. If you do, you'll make your system unbootable and you'll have to boot from a live disk, chroot and reinstall upstart. Not something you'll like.

---

### Post by cecilieaux on 2014-08-04
OK, thanks. How would I go about looking at the source code? I'm just fascinated to have a better idea of what it does.

---

### Post by tgalati4 on 2014-08-04
Init is the "Mother of all processes"  It is the first process (PID=1) that gets started and it spawns (creates) new processes as the system boots and runs.  Try killing it and see what happens.  I won't give you the command, but a student can figure it out.

> tgalati4@Mint14-Extensa ~ $ ps aux | grep init
root         1  0.0  0.1  24440  2212 ?        Ss   Jul21   0:02 /sbin/init

Poking around a live running linux system is interesting and sure to cause breakage.  Be careful with anything in /proc.  You have been warned.

---

### Post by Rob Sayer on 2014-08-05
There's an old saying in computing.

You'll never really understand an OS until you have completely broken it and then had to fix it (not reinstall, *fix*).

Happy hunting, and don't say you haven't been warned ...

---

### Post by tgalati4 on 2014-08-05
Try watching RAM locations with a hex editor and change a few values or delete /usr/bin (you know, to free up space) and see what happens.  Nothing.  At first.

---

