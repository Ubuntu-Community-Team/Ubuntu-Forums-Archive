---
title: "Another Grub Problem"
date: 2007-01-29
forum: General Help
---

### Post by anabelle on 2007-01-29
I installed kubuntu on my pc, but never could get grub to load at startup, always entered directly into XP, but when i used live CD and from there selected the option boot from fist hard disk, it loaded grub, today i removed a 200GB drive and now i can-t even boot using the live cd first.

I tried to install grub, and 

```
find /boot/grub/stage1
```

returned (hd0,2) but when i type 

```
setup (hd0,2)
```

it returns invalid device requested....


what could be wrong

---

### Post by anabelle on 2007-01-31
ok since no one seems to help me, i've decided to post more info...

the output of my fdisk -l is

```

 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3403    27334566    7  HPFS/NTFS
/dev/sda2            3404       18210   118937227+   f  W95 Ext'd (LBA)
/dev/sda3           18211       19457    10016527+  83  Linux
/dev/sda5            3404       18152   118471311    7  HPFS/NTFS
/dev/sda6           18153       18210      465853+  82  Linux swap / Solaris


```

the find /boot/grub/stage1 returns

```
(hd0,2)
```

and setup (hd0,2) returns

```
Error 12: Invalid device requested

```

i've been searching for an answer for two days now, and cant find anything!! im starting te get really frustrated.

Please could someone at least point me in the right direction??? i dont want to go back to XP!! but it seems easier that getting ubuntu to start....

---

### Post by nikhilk on 2007-01-31
> **anabelle said:**
> today i removed a 200GB drive and now i can-t even boot using the live cd first.

I don't know if this will help; can you confirm that your BIOS is configured to boot from CD first.

---

### Post by anabelle on 2007-01-31
yes it is booting from cd

---

### Post by Herman on 2007-01-31
Hello anabelle,
It sounds like you are doing everything almost alright. Hang in there! :D
If you want to install grub to your hard disk's MBR, you should be able to do that but you should type 'setup (hd0)'.
'setup (hd0,2)' would be installing Grub to the first sector (boot sector) of your Ubuntu partition. That should be okay too, that's a good thing to do, I have no idea why you are getting an error message from that, except if there is a 'syntax error' ( for example if someone types a capital 'O' instead of a zero when they type '(hd0,2)'.
I would expect you to get an error message and nothing to happen if you tried to install grub to Windows bootsector though. That's why it is best to use the Grub shell as you are doing, that is very good, you are doing well.

Here is a detailed description of how to use the Grub shell to install grub to various locations, I hope that will explain things better for you, 
                                           Re-install Grub with a GRUB shell eg; with Live CD........................[GO]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD")

It is best to learn how to use the grub shell and how to use the command line to do things if you can. If you get too impatient and you still have trouble you can always use [Super Grub Disk]("http://supergrub.forjamari.linex.org/") to boot your computer and install grub anywhere you like and do numerous other jobs with Grub.

Also, if you still have problems, keep on asking for help. Sometimes answers don't come as quickly as you hope, but sooner or later your questions will be answered. 

Regards, Herman :D

---

### Post by anabelle on 2007-01-31
:guitar: ok, i finally got it working, thanx to the super grub disk, but not only doing that, i first had to do lots of things.

First...

Code:

$
Code:

```
sudo mkdir /mnt/root
```

$
Code:

```
sudo mount -t ext3 /dev/sda6 /mnt/root
```

Code:
```

$
```
Code:

```
sudo mount -t proc none /mnt/root/proc

$
```
Code:

```
sudo mount -o bind /dev /mnt/root/dev
```

Code:

```
$
```
Code:

```
sudo chroot /mnt/root /bin/bash
```

Code:

```
#
```
Code:

```
sudo grub
```

grub>
Code:

```
find /boot/grub/stage1
```

Code:

```
grub>
```
Code:

```
root (hd0,2)
```

Code:

grub>
Code:

```
setup (hd0)
```

It installed Grub on the MBR and it loaded at startup!! yeah!! but when i selected any OS it said Error 21:  Selected disk doesn not exist. ...

so here i needed the Super Grub Disk (wich now i love), i loaded GRUB, and edited the partitions locations that for some rason where pointing to (hd1,2) for linux and (hd1,0) for XP. After editing that i managed to login to ubuntu!! yeah!!!

But i had to do this each time i started my pc, so i had to edit the menu.lst file under grub.

code:
```
sudo kwrite /boot/grub/menu.lst
```

*---note kwrite is only for KDE for gnome use gedit*

And i edited each place where it said (hd1,2) to (hd0.2)
and under XP options i replaced all the ones for zeros...

It didn't work at first, so i tried grub-update but it restored the (hd1,2)s again, so i had to edit them again and save. 

The second time it worked. And now im in love with kubuntu again. But i do think it shouldn't be that hard to get simple tasks done, im very new to linux and lucky me im very patient with computers, but i think the regular XP user may find the linux experience frustrating... at least at first.

---

### Post by Herman on 2007-01-31
Congratulations and well done, anabelle! :D
I'm glad you got it working.
It is unusual to have that much trouble, I guess you must have a special computer or something. Most of the time Grub just gets installed automatically without any problems. 
Re-installing Grub, likewise, is easy in most machines. I have read other people saying they need to chroot into the partition first, and perform all those extra steps. I have never needed to do all that myself, but I believe you if you say it was necessary, and I will take note of it for future reference. Catlett has added the chroot stuff to his Grub tutorial. I just didn't think anyone needed to do that in Ubuntu because I have never needed to. Thanks for your feedback, it will help others.

Super Grub Disk is almost a must-have for people setting up dual and multiple boots. Usually you can just re-install Grub with [Super Grub Disk]("http://supergrub.forjamari.linex.org/") by going 'English Super Grub disk'-->'Gnu/Linux'-->'Fix Boot of Gnu/Linux (Grub). That's just two or three steps and it's all done. (Normally).
I guess Grub is easier to install in some computers and harder in others then. I wonder what it could be exactly that makes some machines hard to install Grub in? Oh well...
You will probably find everything else in Linux easy after you have overcome a hurdle like that!  Again, congratulations and well done! 

Regards, Herman :D

---

