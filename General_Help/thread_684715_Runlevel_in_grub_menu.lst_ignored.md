---
title: "Runlevel in grub menu.lst ignored"
date: 2008-02-01
forum: General Help
---

### Post by randominternet on 2008-02-01
I have setup some different environments I want to use on runlevels 2,3,4,5 which works quite well from telinit. Now I want to be able to boot into them. I can change the default runlevel ok but i want to be able to choose from a menu. I have done this before on CentOS using Grub by adding the number to the end of the kernel line, but this doesn't seem to work in ubuntu, it always goes to the default runlevel

Thanks for your help.

TCA

---

### Post by kellemes on 2008-02-01
Can you please post /boot/grub/menu.lst

---

### Post by randominternet on 2008-02-01
password 	--md5 
default		saved
timeout		10

hiddenmenu

color white/blue

title		Windows XP
root		(hd0,0)
makeactive
chainloader	+1
savedefault	1

title		FAST RESTORE
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-server root=/dev/sda2 ro quiet splash 2
initrd		/boot/initrd.img-2.6.20-15-server
quiet
savedefault	0

title		FULL RESTORE
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-server root=/dev/sda2 ro quiet splash 3
initrd		/boot/initrd.img-2.6.20-15-server
quiet
savedefault	0

title		UPDATE BACKUP
password 	--md5 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-server root=/dev/sda2 ro quiet splash 4
initrd		/boot/initrd.img-2.6.20-15-server
quiet
savedefault	0

title		Linux BASH prompt
password 	--md5 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-server root=/dev/sda2 ro quiet splash 5
initrd		/boot/initrd.img-2.6.20-15-server
quiet
savedefault	0


obviously i have removed the md5 hash of my pw

just tried it again now and my "hello and welcome to runlevel 2!" script runs in every one, and runlevel always reports N 2

Thanks

---

### Post by kellemes on 2008-02-01
Not sure if I'm helping.. can't test it myself atm.
Couple of links..
[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=661357](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=661357)
[https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/85014](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/85014)

---

### Post by randominternet on 2008-02-01
thankyou very much

that bug is exactly my problem, which isn't solved, BUT it did make me realise that the option I pass from grub can be found by 

cat /proc/cmdline

So instead I will just make a script in the default runlevel 2 that works based on that instead of bothering with different runlevels. acheive the same effect anyway

The upstart docs does say that runlevel stuff in rcX.d is only compatibility anyway.

---

### Post by randominternet on 2008-02-01
for anyone reading this thread in the future

ask yourself if you really need runlevels anyway?

all i wanted to do was run different programs from grub, and i found i can just look at /proc/cmdline in my script to see what i want to run. Now I don't even use numbers, I am passing the "normal/restore/backup" from the command line which the kernel ignores then my script runs in the defualt runlevel, see's the command and does the appropriate action, I then set the rmnologin script to only run if it doesn't see one of my special commands

TCA

---

