---
title: "this makes me want to cry a little, lol"
date: 2007-03-05
forum: General Help
---

### Post by marshall.robert on 2007-03-05
hi, im having real problems here and im in need of some help, im an very new to linux (this is my first try)and i havnt used it much since i installed it cos its a bit difficult to get where i want, but im still trying :P

i installed a new boot of xp specially for games on a seperate partition.
i now cannot boot into linux (ok, so that was slightly predictable, but i didnt think).
my first boot of windows has now taken control of the MBR.
ive tried what i can think of with the boot.ini file, knowing that it might not do much, and it hasnt.
ive followed everything said on [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub) but it fails at everything.
ive tried to use the live cd to do a fresh install over the current version, but it thinks my hdd is empty (dunno why, rather confusing).

can somebody plleeeaaaseee help me, its saddens me that i have failed at recovering from this dilema.

many thanks

-rob

---

### Post by eggdeng on 2007-03-05
I would download the gparted live CD to sort out the partitions before trying to install. This is a really powerful & easy to use partioning tool you can get at [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php). Be careful which version of ubuntu you install, I would recommend the long term support release 6.06 (Dapper Drake) as 6.10 seems to have a lot of wireless and other issues and 7.04 is still testing. Good luck with Linux. It's always going to require a little extra, but it gives back extra too.

---

### Post by marshall.robert on 2007-03-05
ive already got a boot of ubuntu(6.10), my problem is i cant get to it, in a nutshell

but could i use gparted to sort out grub?

-rob

---

### Post by FIONEX on 2007-03-05
There are linux boot disks that bring up a shell.  Find those start up disks in order to restore mbr to grub control!

---

### Post by Gerard Barberi on 2007-03-05
Have you tried the super grub disk? [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

If it didn't work try these solutions here

[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

If it still doesn't work, you can try to partition out ~2GB of your hard drive, install dapper to it which will rewrite grub.  Then just format it back to empty and recombine it to the original partition.

---

### Post by eggdeng on 2007-03-05
If grub is the problem, gparted won't help.

---

### Post by marshall.robert on 2007-03-05
> **FIONEX said:**
> There are linux boot disks that bring up a shell.  Find those start up disks in order to restore mbr to grub control!

ive never heard of these things ^^

> **Gerard Barberi said:**
> Have you tried the super grub disk? [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

If it didn't work try these solutions here

[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

If it still doesn't work, you can try to partition out ~2GB of your hard drive, install dapper to it which will rewrite grub.  Then just format it back to empty and recombine it to the original partition.

yeah, tried super grub, wouldnt boot into it, probably cos i used the built in windows cd writer

but partitioning 2 gigs sounds like a clever idea, ill have to be carefull where i place the partition cos the ubuntu live cd thinks my hdd is empty, lol. think i might take a shot now...
------------------------------------
does anyone know why the live cd would think that my hdd is completely empty (wants to erase the hdd if i try to partition it), whereas is has no trouble finding the partitions of my older hdd thats plugged in?

the help so far is really appreciated, and i think the idea of installing dapper on a seperate partition to recover grub is clever. now, time for bed....

-rob

---

### Post by FuturePilot on 2007-03-05
Well if in fact the Ubuntu partition is unharmed and still exists you might want to try this.
1 Boot the live CD
2 Mount the Ubuntu partition
3 Then run this in a terminal
```
sudo /sbin/grub-install /dev/hda
```
You might have to change hda depending on what type of hard drive you have. I've seen it as sda also.
4 Reboot and you should get a Grub menu again

---

### Post by marshall.robert on 2007-03-06
how would i go about mounting the Ubuntu partition?

-rob

---

