---
title: "GRUB - Problem Booting to windows"
date: 2006-12-17
forum: General Help
---

### Post by gerbalblaste on 2006-12-17
I just installed ubuntu 32 bit 6.06

Ubuntu works great but i can't boot into windows.

when i select windows in GRUB i seed the following: 
```
Windows NT/2000/XP (loader)
rootnoverify	(hd0,4)
chainloader	+1
```

and then it just hangs up and i have to ctrl+alt+del to reboot

My windows partion is hda5 and the drive is hd0.

Thanks

---

### Post by bernied on 2006-12-17
Did you move Windows? (hd0,4) is a logical partition, not where you'd normaly find a windows install. 

Is that maybe some utility partition, for booting purposes?

Can you post the output to 
```
sudo fdisk -l
```

---

### Post by gerbalblaste on 2006-12-17
```
Disk /dev/hda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         733     5887791   83  Linux
/dev/hda2             734        9725    72228240    f  W95 Ext'd (LBA)
/dev/hda5             770        9725    71939038+   7  HPFS/NTFS
/dev/hda6             734         769      289107   82  Linux swap / Solaris
```

I did not move windows. i did resize hda2 but i did not move or resize hda5.

---

### Post by bulldog on 2006-12-17
Where your Linux partition is,should windows be.
You can read a lot here about it and maybe you can fix it with this info.

[http://support.microsoft.com/kb/305595/EN-US/](http://support.microsoft.com/kb/305595/EN-US/)

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Windows_Booting_errors](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Windows_Booting_errors)

[http://users.bigpond.net.au/hermanzone/p6.htm#A_Birdss_eye_view_of_Windows_XP](http://users.bigpond.net.au/hermanzone/p6.htm#A_Birdss_eye_view_of_Windows_XP)

---

### Post by bernied on 2006-12-17
This is weird because Windows likes to be in a primary partition (numbered 1-4). If Windows is in hda5 / (hd0,4), then maybe you need to add the makeactive command in the grub menu.lst file, like so:
```
Windows NT/2000/XP (loader)
rootnoverify	(hd0,4)
makeactive
chainloader	+1
```Alternatively, you could set the bootable flag permanently for that partition, using fdisk or similar (that * against the first partition in your fdisk output says that it is currently marked as bootable, but windows is the only OS that needs this flag set, makeactive does it temporarily).

---

### Post by bernied on 2006-12-17
But please tell us if this works, I had no idea that Windows could live in that place.

---

### Post by gerbalblaste on 2006-12-17
Up until i installed ubuntu u was succesfully booting winxp sp2 on hda5 from a boot.ini on hda1.

when i add make active i get a device error of some type and flagging hda5 as bootable did not seem to have any affect.

---

### Post by bernied on 2006-12-18
> **gerbalblaste said:**
> Up until i installed ubuntu u was succesfully booting winxp sp2 on hda5 from a boot.ini on hda1.This suggests to me that hda1 was Windows' boot partition, as might be expected. It looks like the windows boot sequence started in hda1, so you won't be able to chainload hda5, because the windows boot files are just not there (they were in hda1). Do you have a copy of the contents of hda1? What else do you know about it? 

Or am I barking up the wrong tree? 
Maybe did you have two Windows/DOS installs and dual boot, before Ubuntu?

> **gerbalblaste said:**
> when i add make active i get a device error of some type and flagging hda5 as bootable did not seem to have any affect.
I don't know about this - as far as I know, Windows is the only OS that needs this flag and Windows only ever lives on primary partitions, so the flag would only ever be set on a primary partition. So it doesn't surprise me that both makeactive in grub, and trying to set the bootable flag in fdisk, fail.

Herman knows about this stuff, and he's very helpful.
[http://ubuntuforums.org/member.php?u=31861](http://ubuntuforums.org/member.php?u=31861)

---

### Post by Herman on 2006-12-18
gerbalblaste:> Up until i installed ubuntu u was succesfully booting winxp sp2 on hda5 from a boot.ini on hda1.bernied:> This suggests to me that hda1 was Windows' boot partition, as might be expected. It looks like the windows boot sequence started in hda1, so you won't be able to chainload hda5, because the windows boot files are just not there (they were in hda1). Do you have a copy of the contents of hda1? I think this will be tricky to fix, I agree with bernied, your booting files would be deleted when you deleted the old Windows install in hda1. 
Last time I tried to help in a situation like this I wasn't able to. But this time I have though of a few more ideas. 
One of these Windows XP boot floppy disks has all the Windows boot files on it already, but you'll have to make one in another Windows XP computer, 
'How to make your own Windows Xp boot floppy, [Click Here]("http://support.microsoft.com/kb/305595/EN-US/").'

Even with a floppy disk like that, you still might have to copy the whole partition with [GParted -- LiveCD]("http://gparted.sourceforge.net/livecd.php")
 and paste it somewhere into a primary partition before it will be bootable, because I don't think Windows can boot in a logical partition (without the other Windows 'boot partition' in a primary). I have tried pretty hard in a test computer and I couldn't discover how to do it. 

Then when it's booted by the floppy disk, copy the files from the floppy disk into the root of the Windows filesystem and keep your fingers crossed that that is all you'll need to do. 
Or else (better idea), run a Windows [recovery console]("http://www.kellys-korner-xp.com/win_xp_rec.htm") if you can, and use commands in that to install the needed Windows booting files.

These are just ideas I'm pulling from my imagination, I haven't tried them or tested them, I just hope something might help. Use your own judgement and try what you can.

It might be easier and faster to do a Linux file rescue from the partition and just re-install it though. 

Regards, Herman

---

### Post by Malac on 2006-12-18
If you have your windows CD and can boot from that do so.
It will load some files into memory. Then when asked choose the Recovery Console option.
I can't remember the exact wording at the moment but there are 3 choices;
1. Fresh Install
2. Repair Install
3. Repair using Recovery Console.
choose the Recovery Console and then login to the XP session you want to fix.
Then run fixboot and fixmbr.
This should sort it, however this may mean that you will have to sort out the mbr as GRUB and XP boot loader will be fighting for control.
A boot sequence split over two partitions/disks for XP, or any other Windows for that matter, is not a good idea.
Personally, I'd backup the lot and sort out the partitions into a different layout and re-install.

Hope this helps.

---

