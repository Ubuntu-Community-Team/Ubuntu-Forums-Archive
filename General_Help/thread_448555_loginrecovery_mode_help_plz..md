---
title: "login/recovery mode help plz."
date: 2007-05-19
forum: General Help
---

### Post by logan1441 on 2007-05-19
hey everyone,
like others i get everything installed ok, but i cant log in.  i heard something about recovery mode, so here's my question:
how do i open the grub menu?? sorry im really a newbie @ this.  like if its where you reboot and it asks you which operating system, i have that but theres no recovery mode

---

### Post by logan1441 on 2007-05-19
plz someone??

---

### Post by logan1441 on 2007-05-19
anyone?

---

### Post by logan1441 on 2007-05-19
ok i got into grub and safe mode, but when its booting a bunch of errors like dircolors not a command, apt- get not a command, tells me to install apt get, all kinds of stuff right there, so i push ctrl+d and it just boots into normal mode. any ideas??

---

### Post by ecology2007 on 2007-05-19
You do not need to manually edit menu.lst, boot.ini or anything like that.
You do not need to type any command.
I assume you have only one disk. The best thing for you is to uninstall and reinstall.
1 ) locate c:\wubi folder.
2 ) copy paste /wubi/install/ubuntu-7.04-alternate-i386.iso, put it in the same folder than wubi-test-1.exe
3) run wubi-test-1.exe, do full uninstall.
4) run wubi-test-1.exe, do install with default setting
Do not use spaces or weird characters in your username and passwords.
5) reboot.
6) select ubuntu.

If that does not work, come here and give exact error messages and a description of your computer and hard disks.

---

### Post by ecology2007 on 2007-05-19
Post here the content of c:\boot.ini.

---

### Post by Death_Sargent on 2007-05-19
press escape before the timer counts down. you have 3 seconds by default

---

### Post by logan1441 on 2007-05-19
c:/boot.ini :
[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
c:\grldr="Ubuntu"

---

### Post by logan1441 on 2007-05-19
> **ecology2007 said:**
> You do not need to manually edit menu.lst, boot.ini or anything like that.
You do not need to type any command.
I assume you have only one disk. The best thing for you is to uninstall and reinstall.
1 ) locate c:\wubi folder.
2 ) copy paste /wubi/install/ubuntu-7.04-alternate-i386.iso, put it in the same folder than wubi-test-1.exe
3) run wubi-test-1.exe, do full uninstall.
4) run wubi-test-1.exe, do install with default setting
Do not use spaces or weird characters in your username and passwords.
5) reboot.
6) select ubuntu.

If that does not work, come here and give exact error messages and a description of your computer and hard disks.

THAT WORKED. THANK YOU SOOOOOOO MUCH!!! :):):):):):):)

---

### Post by ecology2007 on 2007-05-19
> **logan1441 said:**
> c:/boot.ini :
[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
c:\grldr="Ubuntu"
It is correct you do not have to edit boot.ini manually.
You should have 15 seconds to choose between windows and ubuntu.

---

### Post by akuakulondon on 2009-12-02
Hi, I've got the same problem - just enabled username and password login on 9.04 jaunty which i've been runing persisently on a flash drive.  The username and password I thought I'd entered isn't working.

These instructions look easy enough but I do not have recovery mode with this version of ubuntu.  Any suggestions?

---

