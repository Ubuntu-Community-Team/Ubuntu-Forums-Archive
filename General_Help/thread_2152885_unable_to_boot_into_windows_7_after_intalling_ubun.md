---
title: "unable to boot into windows 7 after intalling ubuntu 13.04 over ubuntu 11.04"
date: 2013-06-09
forum: General Help
---

### Post by lokeshmsit on 2013-06-09
hi,

before installing new ubuntu 13.04, my pc constains two OS's : (1) Ububtu 11.04  (2) Windows 7 


two days ago, i decided to upgrade my ubuntu from 11.04 to 13.04.
after installing new Ubuntu 13.04(using USB stick) over already installed ubuntu 11.04, i performed reboot on my PC.

but, after rebooting i didn't find entry point for windows ( i.e grub boot menu list not appeared on screen) and i automatically booted into freshly installed Ubuntu 13.04.

after that,  i installed boot-repair software and performed a boot repiar using "Recommended repair" default settings.
still i failed to get into windows ( i.e grub boot menu list not appered on screen) after rebooting my pc again.

then, i tried to edit grub.cfg, but after editing and rebooting again, my failed to boot even into ubuntu 13.04.

i reintalled ubuntu 13.04 on my PC using USB stick.

i performed boot repair again but this time using "create a BootInfo summary" Option.

here is my boot-repair bootInfo summry :-

    [http://paste.ubuntu.com/5748306/](http://paste.ubuntu.com/5748306/)



please, Help me.

---

### Post by Mark Phelps on 2013-06-09
ALL you really needed to do was -- ask here FIRST -- and you would have learned that the boot selection problem could have been solved in 5 minutes using a simple terminal command.  

Ubuntu 13.04 will use GRUB 2 -- and in that case, you should NEVER edit GRUB.cfg -- something else you would have learned if you had asked.

The forums are here to help you avoid getting into such difficulties but if you go charging ahead like you did, that only makes things worse.

Usually, boot problems like yours arise because someone erroneously forces the installation of GRUB into the Windows boot partition.  Since Windows then has two folders, one named BOOT and the other named Boot, it gets confused and can't boot anymore.  But looking at your report, that did not happen.

Sorry, but you'll have to wait for someone more knowledgable to come along, as nothing jumps out at me from the report.

---

### Post by Sef on 2013-06-09
Grub [Superdisk]("http://www.supergrubdisk.org/") could install a new grub.

---

### Post by greatsirkain on 2013-06-09
supergrub 2 always works for me, have it on a bootable USB stick, the boot loaders on both my hard drives (on this computer at least) are all messed up & I'm too lazy to fix them so I use super grub 2 to detect all operating systems. I just look at it like nobody else can start my computer when I'm not there without the keys & that kind of thought process stops me ever having to fix it.

---

### Post by lokeshmsit on 2013-06-10
omg!!:confused: after performing last boot-repair with "create a BootInfo summary" option, when i rebooted my pc, i failed to boot even into Ubuntu 13.04 again.
so, i'm going to reinstall my ubuntu 13.04 again via USB stick.

i think boot-repair is the root cause of this problem.

---

### Post by lokeshmsit on 2013-06-10
> **greatsirkain said:**
> supergrub 2 always works for me, have it on a bootable USB stick, the boot loaders on both my hard drives (on this computer at least) are all messed up & I'm too lazy to fix them so I use super grub 2 to detect all operating systems. I just look at it like nobody else can start my computer when I'm not there without the keys & that kind of thought process stops me ever having to fix it.


i think as per your suggestion, i should boot into windows using subergrub then try to fix windows boot record using command : fixmbr   ?

---

### Post by greatsirkain on 2013-06-10
I don't know about the commands from the running OS (just pressed ctrl+alt+t to try some out >.<) but go to control panel\all control panel items\backup & restore & you can create a system repair disk that you can boot from, the fixmbr option should be on that. 
That still doesn't fix your problem though it just fixes the windows boot, you'd still have to use supergrub to boot to ubuntu

---

### Post by oldfred on 2013-06-10
Did you just run the BootInfo report without running the suggested repairs by Boot-Repair? It would reinstall grub2 to the MBR and your grub.cfg does show Windows as a boot option.
Sometimes something in grub is not correct and a full uninstall and reinstall of grub2 is required. Boot-Repair can help you do that. Of course a new install will do the same thing.

---

