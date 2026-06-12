---
title: "error: unknown filesystem grub rescue:_v2"
date: 2014-07-08
forum: General Help
---

### Post by radek.manda on 2014-07-08
I am using Ubuntu 14.04. I do not have any other os installed. Without any special reason after restart I got message:

error: unknown filesystem
grub rescue: 

I tried boot-repair tool using another Ubuntu system from USB, but without success, because "Recommended repair" button was not there. Probably the issue was not recognized by tool and that's why there is no recommendation. Anyway this tool generate some informations about my drive:
[http://paste.ubuntu.com/7766545/](http://paste.ubuntu.com/7766545/)

As visible my drive is Corsair Force GS 128GB.
Than I tried commands "set prefix=(hd0,1)/boot/grub" and "set root=(hd0,1)" and so on but not able to see my files.

entering this : insmod /boot/grub/linux.mod
I get : error unknown filesystem

Same issue appeared here under Title [error: unknown filesystem grub rescue:]("http://ubuntuforums.org/showthread.php?t=1576735") but without any solution. 

Please help.

---

### Post by Bashing-om on 2014-07-08
radek.manda; Hello;

Looks to me like the partition table is hammered. Wont hurt a thing to take a look at what the file system check reports, and be prepared to spare off the superblock. 
slickymaster has excellent guidance on this link:
[http://ubuntuforums.org/showthread.php?t=2177756](http://ubuntuforums.org/showthread.php?t=2177756)

If that is all there is to it
[INDENT][INDENT][INDENT][INDENT]it is fixable
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by yancek on 2014-07-08
Your boot repair output posted above shows Grub installed to the master boot record and the core.img file where it should be.  Other than that, nothing else is correct.  It doesn't show and Grub file, no grub.cfg menu file, and it also shows not fstab or uuid output which is usually included.  You should be able to run a filesystem check from your installation media on sda1 to see if that helps.

---

