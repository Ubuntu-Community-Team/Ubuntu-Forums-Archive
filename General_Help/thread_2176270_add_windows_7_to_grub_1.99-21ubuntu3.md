---
title: "add windows 7 to grub 1.99-21ubuntu3"
date: 2013-09-23
forum: General Help
---

### Post by orkman on 2013-09-23
hi there , i'm completely new to ubuntu and yesterday i downloaded ubuntu64 and bruned it on a dvd , installed it so that i would have w7 and ubuntu at the same time... so far so good ... when i restarted the laptop after the installation of ubuntu i came to a grub terminal where i couldn't do anything except press tab to get some commands or something like this ... i managed to solve the problem by starting the installation dvd again and searching a long long time on google to fix this problem... so grub has been repaired and i restarted the laptop... and finally grub started ... but here is where the new problem comes .... it shows me the normal ubuntu and ubuntu in save mode or something like this .. but no windows 7 .... but windows is still installed on the laptop as far as i see ... so i just have to add it in the menu.lst as far as i have seen by checking the problem via google ... but i can't find the menu.lst ... and the command /boot/... menu.lst doesn't work either ... so ... i need help guys ... would be awesome to solve this fast ;)
so the login screen to ubuntu shows me that i have ubuntu 12.04 LTS and my grub is grub 1.99-21ubuntu3 as marked in the title :D

PS: sry if this isn't the right place to post it in

---

### Post by oldfred on 2013-09-23
Welcome to the forums.

If you are finding instructions showing menu.lst they are very old. Ubuntu converted to grub2 with 9.10 and grub legacy used menu.lst. Grub2 uses grub.cfg.

But for a new user better just to use Boot-Repair. It can fix simple issues. But cannot repair most Windows issues which may need a Windows repairCD or flash drive.

Normally during install grub2's os-prober should add Windows to menu.  Try this first, if not run Boot-Repair and post link to BootInfo report so we can see what the issue may be.
```

sudo update-grub
```

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Flash drive Installer with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by orkman on 2013-09-23
brilliant, it worked ... i was looking now for more then 2-3 hours to get a solution via google and it was a simple command like that ... haha ... now it shows me 3 times w7 and 2 times ubuntu but both work , that's the most important ;) ty very much

---

### Post by oldfred on 2013-09-23
Glad that worked.

With Windows you may get boot partition, main install and recovery. Best not to ever boot into recovery as that usually overwrites partition table.
Ubuntu will keep adding entries with every new kernel. I usually house clean down to two, one older one just in case after several new ones have been added.

---

