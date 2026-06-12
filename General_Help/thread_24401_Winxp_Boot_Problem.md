---
title: "Winxp Boot Problem"
date: 2005-04-06
forum: General Help
---

### Post by millarrp on 2005-04-06
I had a dual boot system with winxp earlier with mandrake linux.  I replaced mandrake with ubuntu and the installation appeard to go off without a hitch.  When I installed the boot loader, it saw my existing winxp partition and I gave approval to add it to the boot manager.  When I try to access the winxp partition I get the follwoing message:

root (hd0,0)
  filesystem type unknown partition type 0x7
save default
make active
chainloader +1

Any suggestions on how to fix this?

---

### Post by Alex4R on 2005-04-06
[QUOTE=millarrp]I had a dual boot system with winxp earlier with mandrake linux.  I replaced mandrake with ubuntu and the installation appeard to go off without a hitch.  When I installed the boot loader, it saw my existing winxp partition and I gave approval to add it to the boot manager.  When I try to access the winxp partition I get the follwoing message:

root (hd0,0)
  filesystem type unknown partition type 0x7
save default
make active
chainloader +1

Any suggestions on how to fix this?[/QUOTE]
 When this happened to me, I went into BIOS and set the hard disk to Large or LBA and it fixed the problem.

---

### Post by Ezlo on 2005-04-06
[QUOTE=Alex4R]When this happened to me, I went into BIOS and set the hard disk to Large or LBA and it fixed the problem.[/QUOTE]
 Hi, I have the same problem. I've tried doing what Alex4R suggested, same problem. I've also tried a repair from the XP disc. No avail. Help would be wonderful.


-Ezlo.

---

### Post by Alex4R on 2005-04-06
[QUOTE=Ezlo]Hi, I have the same problem. I've tried doing what Alex4R suggested, same problem. I've also tried a repair from the XP disc. No avail. Help would be wonderful.


-Ezlo.[/QUOTE]
 You could also check to make sure your CMOS is up-to-date.

Sorry I cant be of more help! :(

---

### Post by Ezlo on 2005-04-07
[QUOTE=Alex4R]You could also check to make sure your CMOS is up-to-date.

Sorry I cant be of more help! :([/QUOTE]
 My CMOS is totally up to date, maybe Windows Server 2003 goes corrupt when you install Linux? lol that'd sure be a microsoft strategy.. But seriously, would anyone else know the solution?

---

### Post by theChauvinist on 2005-04-07
I have no idea if this will work, but you could check the /boot/grub/menu.lst file, and make sure the section to boot Windows reads

title		Windows XP
root		(hd0,0)
makeactive
chainloader	+1

But, like I said, I have no idea if that could work.

---

### Post by jstrutter on 2005-04-15
Hi, all,
     I have a similar problem, pehaps someone can help.  I am a linux newbie.  I just built a new Athlon 64 system and am trying to multiboot XP Pro (32 bit), Enterprise Server 2003, and Ubuntu 4.10 (32 bit).  On a raw hard drive I create 1st partition and install XP.  Then create second partition and intall server '03.  Then install Ubuntu, choosing "install on largest contiguous free space."  After install, i get the boot menu, XP and Ubuntu work fine, When I choose server 03 i get error saying that windows cannot find <System root>\System32\ntoskrnl.dll.  The file is there, i can see it from XP.  I thought maybe i screwed up so I started over, deleting all partitions, and re-installing everything.  Same thing.  I came to Ubuntu web site and saw new version is out, so I download it, start over again.  Same thing.  I checked bios, it is set to LBA.  Someone suggested this was built into server 03 by microshaft.  I tried the same setup w/ SuSE 9.2.  No problem, I can boot into all three OS's.  I would prefer to use Ubuntu.  Any suggestions would be greatly appreciated.

---

### Post by LordNikon9x on 2005-05-16
[QUOTE=theChauvinist]I have no idea if this will work, but you could check the /boot/grub/menu.lst file, and make sure the section to boot Windows reads

title		Windows XP
root		(hd0,0)
makeactive
chainloader	+1

But, like I said, I have no idea if that could work.[/QUOTE]
 I have similar problem with gentoo and now with (k)ubuntu 5.04

My part table is as follow:
17GB winxp  (primary, bootable)
61GB Ext3 (ubuntu) (primary, bootable)
2gb swap (logical on extended)

Some time ago, when I had Slackware/win multiboot and used LILO
machine booted to linux and windows without problems.

It may look like grub problem or it is in the filter between keyboard and chair ;)

---

### Post by LordNikon9x on 2005-05-16
Some googling revealed this:
> 
For those who are technically inclined I include here a brief explanation of what is going on.  The drive has not been damaged and your partition table is fine.  The problem is that Windows demands a "sane" CHS table. This table has been altered by Fedora Cores installer and Windows hangs. Luckily, the actual table, in LBA format, is not  corrupted.  For those seeing a strange partition table, take note that you are probably looking at the table in CHS values and these values are derived from the geometry.  The GNU/Linux operating system does not use these values and operates purely with LBA values.  Windows should not be using CHS either, but for some reason it at least checks this geometry and can be prevented from booting by them being bad.  Changing the drive geometry changes the CHS partition table because this is a virtualization of the true state of affairs on the drive which are best described as being mystical.  Think of CHS geometry as a compass.  If you change the geometry you have recalibrated where the needles reference point is and you are no longer looking at true north.

To fix this, simply
```
sfdisk -d /dev/hda | sfdisk --no-reread -H255 /dev/hda
```
Some more techical information about it can be found at
[http://www.redhat.com/archives/fedora-devel-list/2004-May/msg00908.html](http://www.redhat.com/archives/fedora-devel-list/2004-May/msg00908.html)
As you can see, it is in fedora mail list, but the main thing is I got my own old (workplace) machine to boot win98 with this guide. If I get back home, I can test it on my own machine.

---

