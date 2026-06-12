---
title: "[Boot Problem] XP interferes with Ubuntu"
date: 2007-04-08
forum: General Help
---

### Post by silospen on 2007-04-08
Hey,

Been using Ubuntu for a few weeks now, enjoying it, but I have a strange little problem that I can't find any info on. 

My setup:

4 physical HDD's, 1 partitioned so it looks like:

1) Ubuntu
2) Bootable XP (NTFS)
3) Music etc (NTFS)
4) Partition1: Games (FAT)
4) Partition2: Old XP (NTFS)

I have seperate boot stuff, so If I want to boot ubuntu I just have the ubuntu drive set as primary in the Bios, otherwise to boot from XP I set the XP drive as the primary in the Bios.

_The Actual Problem:_

Ok, what you've been waiting for. Ubuntu works fine. But...If I boot up XP and then boot back into Ubuntu, it refuses to boot into Ubuntu. I end up with an "EXT3 FS error" and it tells me my "Group descriptors" are corrupted. I get into some kind of command line utility thats very limited (which i've forgotten the name of).

To fix it:

I boot with the Ubuntu CD and hit fsck on the Ubuntu drive. It fixes a bunch of stuff and then returns. When I reboot, Ubuntu seems to work fine. Until I boot XP again...

Any ideas what the heck is going on, or more importantly, how to fix it? It doesnt appear to be doing any damage, but it is annoying as hell. It's like XP is somehow corrupting the drive and I have no idea how to stop it.

Thanks a bunch!

---

### Post by krussell on 2007-04-08
Hello :-)
Windowz is stupid so you have to install it in the first partition.
The preferable order would be:
1) Bootable XP (NTFS)
2) Ubuntu

---

### Post by silospen on 2007-04-08
> **krussell said:**
> Hello :-)
Windowz is stupid so you have to install it in the first partition.
The preferable order would be:
1) Bootable XP (NTFS)
2) Ubuntu

Excuse my confusion, but I don't understand what you mean by the "first partition"?

Ubutu and the Bootable XP are on completely seperate hard drives and so I don't quite see what you mean by "first partition".

Thanks for the response though :)

---

### Post by h4mx0r on 2008-03-06
He means if you read up on dual booting there is something about the windows mbr not being within so many data blocks from where the system initially looks, solution is to have it first or relocate the windows boot information to the first partition/drive/location. I don't know exact figures but that could cause issues.

However I think you just have some crappy ext3 drivers for windows messing with that drive perhaps they're outdated? Perhaps you have some windows virus trying to hide within empty sectors of your other partition? Also are you doing some sort of raid setup with multiple drives?

---

### Post by tbadal09 on 2008-03-08
hi! i have dell inspiration 530 that orignally came with ubunto, tried to install XP home won't work. and after couple of unsuccessful attempts, i finally got it to work but have to get rid of ubuntu. once xp home was up and running and tried to install ubuntu it was piece of cake but the next morning window will show up in boot menu but would not load . any help please.
i think it is somthing with dell computers. not sure.

---

### Post by h4mx0r on 2008-04-02
did you change the /boot/grub/menu.lst file? if so put it back to default and it should work like it did the day before.

---

