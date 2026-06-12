---
title: "Ubuntu and Physical Drives"
date: 2017-08-29
forum: General Help
---

### Post by sheddupe on 2017-08-29
Hi,

I've played with Ubuntu inside VM's before but now I'm planning to fully replace Windows 10 on my dev laptop with Ubuntu.  Before I do this I want to understand how Ubuntu deals with separate drives.  My laptop has an SSD and a big slow HD for data.  I recall being told that Linux abstracts across all physical drives to create a single filesystem.  Is this true?

Currently I keep the OS and most apps on the SSD and data on the HD especially data that can be buffered into memory so I don't much care about fast access.  I'm used to deciding what drive things should be installed or stored on.  With Ubuntu do I just forget about this distinction and let the OS decide where stuff should go?

Thanks,

---

### Post by sp40140 on 2017-08-29
First, I suggest you try setting up dual boot (create partition in ssd and install ubuntu on it along with win). Spend some time with the set up and then stop using win. (I suggest you keep win for rainy day like when you need MS Office).
As to the drives, Ubuntu treats them almost same as windows (but again depends on how you use it currently with win10).
What kind of data and HOW you store it.
You don't have to forget external drives. (that's absurd). I have four physical drives on my ubuntu. two external HDD, one internal HDD and one internal ssd. 
So, many physical drives shouldn't be a concern when moving to ubuntu.

---

### Post by wheatpenny2 on 2017-08-29
I did what sp40140 suggested and installed a dual-boot before I started using Ubuntu full-time, and had no problems whatsoever with drives with one exception:  It would not mount a flashdrive that was formatted as Fat32, but I backed up everything on the drive (there wasn't that much on it) and formated it as NTFS, and it worked fine after that.  When I went to Ubuntu-only all my drives worked fine. Just unplug them when you install Ubuntu just to be on the safe side.

---

### Post by sheddupe on 2017-08-29
The data I will be transferring is mostly txt and pdfs and various media files, mostly flac.  I had considered converting the "storage" drive to Ext4 with the data in place but from what I've read it is quicker to back up the data, format the drive then restore data (and probably safer)

I've been using Open Office for a while now but I sometimes still need word viewer so dual boot might be a safer short term strategy during the changeover.

The more I consider it dual boot seems a good idea so I can sort out the various drivers for my laptop (it's an asus rog that came pre-installed so I don't know how easy finding correct drivers will be)

My other main reason for changing is Win 10 is unbelievably slow to start up from a complete shutdown, sometimes 15 minutes or longer (it's fast from sleep though). I need to verify that Ubuntu boots fast to eliminate any hardware issues (which seems unlikely anyway).

---

### Post by oldfred on 2017-08-29
Windows should not be that slow. But dual boot requires you turn off the Windows fast start up or always on hibernation which does make it a bit slower. The one Dell I have with Windows 8 & Ubuntu takes less than a minute to boot Windows. Ubuntu is still faster.

You can make two drives as one logical volume. But if either drive fails you lose all data. The LVM install is also required for full drive encryption, but otherwise only advanced users who understand partitioning & have really good backup procedures should consider LVM. 

On my SSD I have several Ubuntu installs typically 25GB / Partition with less than half used.
And I have all data (and more installs) on HDD in a separate /mnt/data partition formatted ext4, but I have to manually set ownership & permissions so I can use it. And then mount into my / so I can easily see it after reboots. Same data partition is used in all installs.

For a newer user, putting /home on the HDD is easier as it automatically assigns correct ownership & permissions & mounts into / in place of the default folder.
You can only have /home as a separate partition during install, by using the Something Else install option. And if thinking of multiple installs of Ubuntu, you should not share /home, but can easily share data partitions. I originally started sharing a NTFS data partition with my now long gone XP install.

Is system UEFI or BIOS? And then is Windows UEFI or BIOS install. You really want Ubuntu installed in the same boot mode.
And if HDD is data, it can be gpt whether UEFI or BIOS, but should be gpt if SSD is gpt, more for consistency or if later you want UEFI install on HDD.

       [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
With 17.04 and later, a separate partition is not created for swap, but if one exists it will be used.

 Backup efi(ESP) partition and Windows partition before Install of Ubuntu. Only one efi partition per hard drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 

If UEFI lots more info in link below in my signature.

---

### Post by wheatpenny2 on 2017-08-29
Yeah, a dual-boot is probably the best alternative, since that way you can always go back to Windows if you decide that Ubuntu doesn't meet your needs

---

### Post by sheddupe on 2017-08-29
I had to check - it's UEFI

---

