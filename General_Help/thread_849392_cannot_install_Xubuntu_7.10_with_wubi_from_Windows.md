---
title: "cannot install Xubuntu 7.10 with wubi from Windows"
date: 2008-07-04
forum: General Help
---

### Post by plastichero on 2008-07-04
from Windows, I tried to install Xubuntu 7.10 from CD.
 
My Windows XP running on D:, tried to install xubuntu onto G: (NTFS, 3.9 GB, blank ). It automatically chose G: and put the folders. Now, when rebooted .. after selecting "Ubuntu-Linux" from OS menu ... only a blank screen with:

[COLOR="DarkOrange"]Busybox v1.1.3 (Debian 1.1.1.3-5ubunu7) Bult-in shell (ash)
Enter help for a list of built in commands.
(initramfs) [/COLOR] 

then if I give the command "return" or "exit" .. it runs the LIVE version.

now, I replced "quiet splash" with "all_generic_ide" in the file g:\ubuntu\disks\boot\grub\menu.lst and rebooted. Now installation begins and at some point it says many errors like:

[COLOR="#ff8c00"]Buffer I/O error on device fd0, logical block 0
SQUASHFS error: Unable to read fragment cache block [2fbf030][/COLOR]
... and some others ..

then again it starts the LIVE version.

I'm not getting the problem ... I want to get it installed. is fd0 is for floppy drive? the floppy drive is attached but rotten.

MY PC: 256MB RAM, WIN XP, Windows 98 running on C: and XP on D:

any help?

---

### Post by ago on 2008-07-04
Can you please try with Wubi 8.04.1
Wubi 7.10 is not supported

---

### Post by plastichero on 2008-07-04
thnx.
wubi 8.04 doesnt run on 256 RAM. it denies to run, I tried.
wubi is already provided in XUbuntu 7.10 cd, I run that. Why won't it work? :confused:

---

### Post by ago on 2008-07-04
8.04.1 adresses this

---

### Post by plastichero on 2008-07-05
I tried wubi 8.04.1 but it also didn't run. 
any idea from experts? :confused:

---

### Post by ago on 2008-07-05
What is the exact text you see?

Can you please send the log in your user temp folder (%temp%)?

In any case you should be able to run wubi with the --skip-memory-check flag

---

### Post by plastichero on 2008-07-05
How can I be able to run wubi with the --skip-memory-check flag?

I ran the wubi exe from inside windows.

---

### Post by plastichero on 2008-07-05
ok .. I finally got rid of the previous problem. Installation process was looking for the floppy drive though it was not attached. I disabled that from BIOS and now installation begins.

BUT ...
Now, I'm onto a new problem! The installation begins and after showing couple of screens on initialization .. the xubuntu opens from the LIVE cd!
why it is running the live version instead of installing it? 

I'm going nuts.

---

### Post by ago on 2008-07-05
what is the output of

cat /proc/comdline

and please also post syslog and casper.log

---

