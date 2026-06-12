---
title: "installing Windows AFTER Ubuntu (not the usual question)"
date: 2007-08-08
forum: General Help
---

### Post by joker on 2007-08-08
I just got a new (to me) machine a couple months ago (AMD X2 4000, 2GB ram)  I did a clean install of Ubuntu, leaving a 20GB partition at the beginning of the hard drive for a later install of windows.  So yesterday I decided to install windows, and all was not well.

First I set the partition type to 7 (NTFS) with fdisk.  

Then I rebooted using my Windows 2000 CD, and selected the 20Gb partition for the install. 

Next, windows attempted to format the partition, this is where it all went wrong.  After completing the format process windows went back to the select a drive for install screen, and all my partitions were messed up!  Some were deleted, while others were moved to new locations.  The partition which was selected to format was no longer present.   In short the partition table was corrupted.

So I popped in a live CD and rebuilt the partition table and reinstalled Grub so I could use the machine.  And I tried again, same result.

So does anyone have any idea what is happening?  I have never had an issue like that, windows is definitely corrupting the partition table, and I don't know why.  Please help me.

---

### Post by garlito on 2007-08-08
> **joker said:**
> I just got a new (to me) machine a couple months ago (AMD X2 4000, 2GB ram)  I did a clean install of Ubuntu, leaving a 20GB partition at the beginning of the hard drive for a later install of windows.  So yesterday I decided to install windows, and all was not well.

First I set the partition type to 7 (NTFS) with fdisk.  

Then I rebooted using my Windows 2000 CD, and selected the 20Gb partition for the install. 

Next, windows attempted to format the partition, this is where it all went wrong.  After completing the format process windows went back to the select a drive for install screen, and all my partitions were messed up!  Some were deleted, while others were moved to new locations.  The partition which was selected to format was no longer present.   In short the partition table was corrupted.

So I popped in a live CD and rebuilt the partition table and reinstalled Grub so I could use the machine.  And I tried again, same result.

So does anyone have any idea what is happening?  I have never had an issue like that, windows is definitely corrupting the partition table, and I don't know why.  Please help me.

Hi joker, I did something similar but with Win XP. I found no problems, except losing GRUB of course. So, it must be a matter of your Windows version.

No idea really, it seems a bit strange although I've never installed Win 2000 actually. I would try to create a FAT32 filesystem from Ubuntu before  booting with the Windows CD and watch what happens.

---

### Post by joker on 2007-08-08
I did try setting the file system type to fat32 in fdisk too, forgot to mention that, but it still did the same thing.

---

### Post by garlito on 2007-08-08
> **joker said:**
> I did try setting the file system type to fat32 in fdisk too, forgot to mention that, but it still did the same thing.

I meant also you to create the filesystem:

mkfs.vfat -F 32 /dev/xyzt

Ands perhaps the 2000 installer won't tray to format, but who knows?

---

### Post by joker on 2007-08-09
That I did not try.  I will give it a shot.

---

