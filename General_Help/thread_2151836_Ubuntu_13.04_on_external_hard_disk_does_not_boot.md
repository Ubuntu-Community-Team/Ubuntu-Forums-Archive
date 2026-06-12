---
title: "Ubuntu 13.04 on external hard disk does not boot"
date: 2013-06-05
forum: General Help
---

### Post by hsuazo62 on 2013-06-05
I have a Windows 8 computer and I have installed Ubuntu 13.04 on a external 500 GB hard disk. The hard disk has a 34 GB ext 4 and a 2 GB swap partitions, the rest is NTFS.

When I start the computer always do it in Windows 8.

If I select to start from the external hard disk I got the "No such partition, Grub rescue >" black screen message.

Is there a way to boot ubuntu from the external hard drive if I selected to do so ???

Please help.

Thanks

---

### Post by DJWYMAN on 2013-06-06
maybe try a grub repair from a live cd.  [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by DJWYMAN on 2013-06-06
oh I forgot to ask do you know if grub is installed on your external or your internal drive?  if it is on your external then you should be able to boot from the external.  if it is installed on your internal drive then you would have to boot up to the internal drive and then select the distro that is on your external.

---

### Post by oldfred on 2013-06-07
Is this a Windows 8 pre-installed system? It then is UEFI and external drive needs to be gpt with Ubuntu installed in UEFI mode.

Best to see details:
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by gordintoronto on 2013-06-07
When I installed from a LiveUSB onto a USB drive, it set up grub to boot from SDC1. When I removed the LiveUSB, my USB drive was promoted to SDB. Bad, Bad, Bad.

I managed to edit /boot/grub/grub.cfg, search and replace sdc1 with sdb1, and all was well.

---

### Post by hsuazo62 on 2013-06-08
Guys, thanks a lot, for your responses. I already tried boot repair but it did not work. I do not know [COLOR=#000000]if grub is installed on my external disk. What is Distro ???. I do not have a W[/COLOR][COLOR=#000000]indows 8 pre-installed system. Originally it was Windows 7 and I made an upgrade.[/COLOR]

---

### Post by oldfred on 2013-06-08
If you can boot live installer, you can download Boot-Repair into it. Or download its full repair CD.

Post link to BootInfo report, otherwise we are just guessing.

One guess is that you did not install grub to the MBR of the external drive as mentioned several times above.

---

### Post by hsuazo62 on 2013-06-10
I downloaded full boot repair CD. I sent this information to [email]boot.repair@gmail.com[/email] : http//paste.ubuntu.com/5749736.
I do not have any answer so far. I still have the same problem, I can not boot ubuntu from my external HD.

---

### Post by oldfred on 2013-06-11
Boot-Repair says it reinstalled grub to the MBR of sdb, your external. If you select with your one time boot key (f12 on my system) or change BIOS to boot external drive , does it not boot?
You should get grub menu with the option to boot either Ubuntu or Windows.

---

### Post by hsuazo62 on 2013-06-12
[COLOR=#000000]When I start the computer, I [/COLOR][COLOR=#000000]change BIOS to boot from external drive, but I got this message:[/COLOR][COLOR=#000000] "No such partition, Grub rescue >" black screen message.[/COLOR]

---

### Post by Dreamer Fithp Apprentice on 2013-06-12
I had a lot of problems trying to install 12.04 to an external usb HD. You might like to look at the thread [http://ubuntuforums.org/showthread.php?t=2102970](http://ubuntuforums.org/showthread.php?t=2102970) wherein a lot of people went to a lot of work suggesting things to try. None of them worked for me but they might for you. Or they may give you some ideas. My problem (which was specific to 12.04 - earlier versions and other distros installed just fine) was apparently solved by my deleting the partitions and repartitioning with a significantly different allocation of space. Good luck.

---

### Post by oldfred on 2013-06-12
We have seen where larger drives connected with USB and boot files far into drive often do not work. Often a separate /boot partition within the first 100GB of drive solves issue. Sometimes it is a BIOS setting also. What mode is BIOS set to read drives. Should be AHCI or LBA but not IDE nor RAID.

---

