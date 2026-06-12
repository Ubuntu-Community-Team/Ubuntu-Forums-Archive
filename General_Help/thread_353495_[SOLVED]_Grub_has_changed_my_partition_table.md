---
title: "[SOLVED] Grub has changed my partition table"
date: 2007-02-04
forum: General Help
---

### Post by roe_polak on 2007-02-04
Hi there. I'm in a little bind here, as my harddisk does not show the actual partitions after I added my WinXp hd to the grub menu.lst and tried to boot it. It has all resulted in an error saying "Missing Operating System" when I try to boot the Linux hd. You might want to know my setup.

Dell Desktop
250 Gb Wd Sata
  sda1 /boot
  sda2 /swap
  sda3 extended
       sda5 /
       sda6 /home
  sda4 /winshare

250 Gb Wd Sata
  sdb1 Dell util
  sdb2 WinXp
  sdb3 Dell recovery
  sdb4 Vista

 I installed Ubuntu without the Win disk activated in the BIOS. Then when the whole system was functioning I thought i should add Windows to the Grub menu (making sure it then was activated in the BIOS). I have installed Ubuntu before and also edited the grub menu before, so I thought I was doing it right. Just to be sure I followed some guidelines at Ubuntuguide.org. Since I can't access the disk now I'll try to remember what was written in the grub files.

devices.map
```
hd0 /dev/sda
#This one I added myself
hd1 /dev/sdb
```

menu.lst
```
...
title           Windows XP
map (hd0) (hd1)
map (hd1) (hd0)
chainloader (hd1,1)+1
...
```

 This didn't work so I then tried to boot from (hd1,0) (using 'e' in grub) and it then booted up with the Dell Utility program. Well, so far so good, I thought. But when the box started up again I got the "Missing OS" message.

 I then booted up from the LiveCD to have a look at the disk in GParted. To my great horror and disbelief the partition table was laid out exactly like the win disk. Same sizes and number of partitions, but with "Unknown filesystem" and a bit more unallocated space.

 I now realize that in my first attempt to boot into windows, something was missing in the menu.lst. Should've looked like this:

```
title=Win
map (hd0) (hd1)
map (hd1) (hd0)
root (hd1,1)
makeactive
chainloader +1
```

 I have tried everything I can think of (exept trying to plug in the drive as sata2 or 3 on the motherbord, though, at this point I don't think it will make a difference). I can't reinstall grub as the disk can't be mounted (error 17) and fsck /dev/sda1 tells me the partition table is corrupted.

 It's pretty stupid, as I just got a new harddisk because the previous died from bad blocks. Is there anything I can do to recover my new install or should i just reformat and hope for the best? There's not really any valuable data on the disk yet, but it would be nice to recover the working system. Also, I would like an explanation on how it could go this wrong. Grub ain't supposed to write anything to the drives, is it? The windows disk boots up fine, by the way.

 I have searched the forums for help, but I can't seem to find anyone with the same problem so I hope you can help me.

---

### Post by dcstar on 2007-02-04
> **roe_polak said:**
> Hi there. I'm in a little bind here, as my harddisk does not show the actual partitions after I added my WinXp hd to the grub menu.lst and tried to boot it. It has all resulted in an error saying "Missing Operating System" when I try to boot the Linux hd. You might want to know my setup.
.......
 It's pretty stupid, as I just got a new harddisk because the previous died from bad blocks. Is there anything I can do to recover my new install or should i just reformat and hope for the best? There's not really any valuable data on the disk yet, but it would be nice to recover the working system. Also, I would like an explanation on how it could go this wrong. Grub ain't supposed to write anything to the drives, is it? The windows disk boots up fine, by the way.

 I have searched the forums for help, but I can't seem to find anyone with the same problem so I hope you can help me.

I can imagine how something (not necessarily GRUB) has re-written the boot sector of one drive onto the other - especially if you didn't get the GRUB commands that switch the drives 100% correct.

About the only thing I can think of is you delete all of the partitions of the corrupted drive, and then manually create them again exactly as they were previously (assuming you have that information).

Just out of interest, there is a way to create a backup file of your partition data using the Linux "dd" command, you should be able to search it out in the forums or on the web.

---

### Post by logos34 on 2007-02-05
> This didn't work so I then tried to boot from (hd1,0) (using 'e' in grub) and it then booted up with the Dell Utility program. Well, so far so good, I thought. But when the box started up again I got the "Missing OS" message.


What about (hd1,1)?  Will grub boot winXP (sdb2) with that?
> 
I then booted up from the LiveCD to have a look at the disk in GParted. To my great horror and disbelief the partition table was laid out exactly like the win disk. Same sizes and number of partitions, but with "Unknown filesystem" and a bit more unallocated space.
...
I can't reinstall grub as the disk can't be mounted (error 17) and fsck /dev/sda1 tells me the partition table is corrupted...Is there anything I can do to recover my new install or should i just reformat and hope for the best? There's not really any valuable data on the disk yet, but it would be nice to recover the working system.

I assume you've checked sudo fdisk -l and it's showing the same thing.  If you can't mount /boot and / (sda1 and sda5) from the livecd, and fsck is saying the partition tables are messed up, and you'd rather recover instead of reinstall, then here's what I'd do:

-run Testdisk to fix the partition tables and any other problems. Download [SystemRescueCD]("http://www.sysresccd.org/Main_Page") or Gparted livecd.  Boot from the disk, enter **startx** to get to the desktop, then in a (maximized) terminal type
> testdisk

Go through the analysis and repair for both disks. Hopefully that'll do the trick. 

Then fire up the Ubuntu livecd and try to mount /boot and / partitions so you can get to your grub and fstab files to see what's going on.  

On the livdcd desktop, open a terminal and create temp mount points:
> sudo mkdir /ubuntu1
sudo mkdir /ubuntu5
sudo mount -t auto /dev/sda1 /ubuntu1
sudo mount -t auto /dev/sda5 /ubuntu5
cat /ubuntu1/boot/grub/menu.lst
cat /ubuntu1/boot/grub/device.map
cat /ubuntu5/etc/fstab
sudo fdisk -l


Just post it all if you could so we can see exactly what's up. 

You should probably tweak your windows entry in menu.lst thus:
> title Windows XP
root (hd1,1)  *Or try **rootnoverify (hd1,1)**
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1

> I have tried everything I can think of (exept trying to plug in the drive as sata2 or 3 on the motherbord, though, at this point I don't think it will make a difference)

I remember another ubuntu dual-booter with dual satas who got his to work by switching the drive with Ubuntu and grub to the first channel and the winxp drive to the second channel.  If your setup doesn't work with ubuntu on the first sata channel and windows on the second (I assume that's what you have now), try different channels.

Once you get everything in order, you can reinstall grub to the mbr of sda by booting the livecd, then
> sudo grub
root (hd0,0)  
setup (hd0)

If you end up going the reinstall route then I'd imagine you'd do what dcstar suggested above.

---

### Post by roe_polak on 2007-02-05
Thanks for the replies. I dont know exactly how the partitions was laid out in the end, although i do know how big each one of them is. But these numbers might not be the same next time i try (because of cyllinder rounding, I would think). I'll try the SystemRescueSystem as the testdisk program sounds promising.

I do have one more question. If everything goes wrong, will then damage the harddisk if I was to set a new disk label for it (assuming this action will cause the entire disk to be formated)?

I don't have much time right now, so I'll try it later today.

---

### Post by roe_polak on 2007-02-05
It seemed "just" to be the partition table that was messed up. With the SystemRescueCD I ran testdisk (after I had read through the docs) and it could reconstruct my partition table. I restarted, but booted back into the RescueSytem and reinstalled grub and after another reboot my Ubuntu started up! Thanks a lot. So far i haven't noticed any missing data and the system started up without any trouble.

---

### Post by logos34 on 2007-02-05
Glad to hear you've got Ubuntu up and running again! :)

---

### Post by dcstar on 2007-02-06
> **roe_polak said:**
> It seemed "just" to be the partition table that was messed up. With the SystemRescueCD I ran testdisk (after I had read through the docs) and it could reconstruct my partition table. I restarted, but booted back into the RescueSytem and reinstalled grub and after another reboot my Ubuntu started up! Thanks a lot. So far i haven't noticed any missing data and the system started up without any trouble.

Verrry lucky!!    :)

---

