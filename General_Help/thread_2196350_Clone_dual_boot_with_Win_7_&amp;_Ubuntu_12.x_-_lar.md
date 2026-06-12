---
title: "Clone dual boot with Win 7 &amp; Ubuntu 12.x - larger drive to smaller SSD"
date: 2013-12-29
forum: General Help
---

### Post by Umberto_gladys on 2013-12-29
First post... I've read the online suggestions for cloning dual boot as well as those for larger to smaller drives but not one that combines all the elements needs to clone both at the same time... Here is the system in question:

[TABLE="class: outer_border, width: 700"]
[TR]
[TD][B]Partition
[/B][/TD]
[TD][B]File System
[/B][/TD]
[TD][B]Mount Point
[/B][/TD]
[TD][B]Label
[/B][/TD]
[TD][B]Size
[/B][/TD]
[TD][B]Used
[/B][/TD]
[TD][B]Unused
[/B][/TD]
[TD][B]Flags
[/B][/TD]
[/TR]
[TR]
[TD]/dev/sda1[/TD]
[TD]ntfs[/TD]
[TD][/TD]
[TD]System Reserved[/TD]
[TD]100[/TD]
[TD]33.59[/TD]
[TD]66.41[/TD]
[TD]boot[/TD]
[/TR]
[TR]
[TD]/dev/sda2[/TD]
[TD]ntfs[/TD]
[TD][/TD]
[TD][/TD]
[TD]195.32[/TD]
[TD]53.49[/TD]
[TD]141.83[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]/dev/sda3[/TD]
[TD]extended[/TD]
[TD][/TD]
[TD][/TD]
[TD]102.67[/TD]
[TD]-[/TD]
[TD]-[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]/dev/sda5[/TD]
[TD]ext4[/TD]
[TD][/TD]
[TD][/TD]
[TD]94.93[/TD]
[TD]4.88[/TD]
[TD]90.05[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]/dev/sda6[/TD]
[TD]linux-swap[/TD]
[TD][/TD]
[TD][/TD]
[TD]7.74[/TD]
[TD]-[/TD]
[TD]-[/TD]
[TD][/TD]
[/TR]
[/TABLE]

The source drive - /dev/sda is 300GiB. The new SSD is a Samsung 830 120GiB.

I have tried Ghost... got a blinking cursor. Tried Clonezilla in advanced mode but it would not copy the larger drive to the smaller even with the switches. Tried Boot-Rescue from the Live USB but it was caught in the "loop" of asking to unmount a partition. Lastly, tried G4L and that went nowhere because of the RAW copy method.

So what is the best approach to clone the dual boot scenario listed above to a smaller SSD while retaining the boot capabilities of GRUB2 with Win 7 and Ubuntu 12.x?

---

### Post by Mark Phelps on 2013-12-29
By definition, you can not "clone" from a larger space to a smaller because "cloning" means making an "exact copy"; since the new version is smaller, it can not be an "exact copy".  The safest solution is to migrate data files to an external drive and then shrink down your partitions until they fit on the new drive.

---

### Post by oldfred on 2013-12-29
Are you keeping old drive plugged in as a data drive?
If so cloning will have issues of duplicate UUIDs.

Not sure about Windows which you may have to clone/copy, but often with Ubuntu it is easier just to reinstall and copy /home with your data. With Windows you should defrag and use Windows to shrink its partition, but leave at least 30% free space in NTFS partition for Windows to work well.

Some with SSD, keep system on SSD and have data on rotating drive (What I do). But I have two / (root) partitions with current working and future installs and all data on rotating drives.
I also like to keep every drive with a bootable system and its boot loader on that drive.

---

### Post by Umberto_gladys on 2013-12-29
No, I do not plan on keeping the old drive as a data drive. It's an internal 300GB 5400rpm 2.5" drive. I'll probably just re-purpose it in an older laptop. The plan is to run everything on the new SSD with dual boot to Ubuntu and Win 7 x64.

The table in the first post details the current partition structure. Sda1 & sda2 are the Win 7 partitions. Sda5 & sda6 are the ones Ubuntu created on what was a 100GB slice that I allocated. With a 120 GB drive I was thinking 2/3 to Win 7 and 1/3 to Ubuntu (80GB and 40GB).

Ghost once did a great job with retaining both ext2 and ext3 but ext4 doesn't come across and ends up rendering the PC unbootable and unfortunately not repairable by any methods I have tried.

I was hoping there would be an easy way to do this without re-installation of either OS. I guess that's not possible.

---

### Post by Umberto_gladys on 2013-12-29
> **Mark Phelps said:**
> By definition, you can not "clone" from a larger space to a smaller because "cloning" means making an "exact copy"; since the new version is smaller, it can not be an "exact copy".  The safest solution is to migrate data files to an external drive and then shrink down your partitions until they fit on the new drive.

Correct. Technically it's not an "exact clone" because the partition tables would differ from a larger to smaller drive. However, relative to the apps, data, OS... etc, it would be an exact duplication.

---

### Post by sudodus on 2013-12-29
I think you must shrink the Windows partition which is possible but slow and risky. I think Mark Phelps's suggestion is good. Migrate all the data (that does not belong to the system) to make it easier to shrink it.

All data in the linux partition can be copied (and reimported after shrinking), but ***if you move the head end of the partition, you will have some extra steps to make it boot again***. Oldfred's suggestion, to only save the data in /home (and make a separate /home partiition) but reinstall the system might be the best way to do it, because it will make the bootloader point to the correct place at once.

***rsync*** is a good tool to copy /home. If you prefer to copy the whole ubuntu system, you can make a tarball with the ***One Button Installer*** (and wait with reinstalling directly into a root partition and swap partition on the SSD).

After shrinking Windows (and maybe linux), you can use ***Clonezilla*** to transfer the system from the HDD to the smaller SSD. If you transfer only Windows via Clonezilla, you can edit partitions for Ubuntu with ***gparted***.

---

