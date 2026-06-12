---
title: "Root Partition is too small..."
date: 2014-11-16
forum: General Help
---

### Post by Robbobden on 2014-11-16
Can I get some suggestions on how to expand my root partition ?  I've attached a screenshot of my SSD (Gparted).   I should have ordered root and home differently, then I could have used Swap space to expand my root into.   But I didn't.   I'm getting continously alerts that I'm running out of space.  Any help appreciated.

Regards,
RDL

---

### Post by pqwoerituytrueiwoq on 2014-11-16
wow now that is a mess, probably be faster (or better off) to start over and do it right
1 backup data:
2 change the table to a gpt partition table,as you can have far more than 4 partitions (all data will be deleted)
3 make a 1mb cleared partition, don't forget to mark the grub_bios flag on this one under manage flags (required for booting in gpt tables)
4 make a 20-32gb root partition
5 make your 50-80GB NFTS partition for windows
6 make your 2-5GB home paration
7 make your data partition with the remaining space
8 install windows to the NTFS partition
9 Install linux and don't use manual partition setup

if that is not a option you can delete swap
move home 
expand root
update fstab/mtab so they don't try to mount swap as it no longer exist

---

### Post by oldfred on 2014-11-16
While I often recommend gpt partitioning, it really is for UEFI boot or Ubuntu only drives as Ubuntu can also boot in BIOS mode from gpt.  The advantage of gpt is that there is only one type of partition, essentially all then are primary. If not installing Windows then use gpt.

If booting Windows, also in BIOS mode you must have MBR(msdos) partitioning. Or Windows only boots from gpt drives with UEFI.

Windows only boots with BIOS from a primary NTFS formatted partition with the boot flag. I would create the NTFS partition as sda1, and make entire rest of drive as the extended partition with as many logical partitions as you may want.

I do not suggest a separate /boot partition for most desktop installs. If full drive LVM or LVM encrypted or more of a server type configuration then you may need a separate /boot. Some very old systems or older systems when installed to an external drive do need either /boot or / (root) entirely inside the first 100GB of the drive.

---

### Post by coldcritter64 on 2014-11-17
> **Robbobden said:**
> Can I get some suggestions on how to expand my root partition ?  I've attached a screenshot of my SSD (Gparted).   I should have ordered root and home differently, then I could have used Swap space to expand my root into.   But I didn't.   I'm getting continously alerts that I'm running out of space.  Any help appreciated.

Regards,
RDL

You know if you shrink swap and move it fully to the right inside the extended partition, you can simply pick up the home partition and also drag it fully to the right (moving the home partition) to butt up against swap freeing the space for root to be expanded into ? 

A couple of steps extra but easily accomplished in gparted graphically. 

NOTE if you try this : do **full** (all partitions including any NTFS) system and data backups and store them off the drive being repartitioned for safety, any repartitioning is potentially dangerous to you system/data if mistakes occur.

Personally I'd follow          pqwoerituytrueiwoq's suggestion of fully starting over in this case, taking into account what oldfred posted. Something for you to also consider. Cheers.

**Edit:** I missed the very end of pqwoerituytrueiwoq's post initially OP, basically says the same as the first part of my post but with deleting swap altogether. 
Unless you use hibernation or such and need it, I would tend to shrink swap to only about 1/2 to 1 GB only, freeing up to about 7GB for expanding root (and maybe a bit for home as well, depending on your needs)

---

### Post by Robbobden on 2014-11-17
I'd rather not start over.  I really like the dual boot that I have.  The reason I kept partitions small was so I can fit the image on one DVD.  I used TerrabyteUnlimited 'Image for Linux' to create the image.   So, I'll attempt to shrink/move as Coldcritter64 suggests above.

RDL

---

### Post by Elfy on 2014-11-17
I'll not add much to the thread with the people you've got reading and posting, but, is there any reason for having a seperate home? Especially one so small. Frankly imo you'd be better of adding home to / and letting the system deal with that.

---

### Post by Robbobden on 2014-11-17
I did a dry run:  shrink swap to 4G, move /home to the right, then expanded / into the empty space.   I've got to backup what little stuff I have sitting in folders on the desktop now before I start.   Thanks for the help.   I wasn't aware this could be done in Gparted.   Pretty cool !    If I have the time, I'll post pics of each step for some one else who finds themself in a similar bind.   BTW, I installed Ubuntu 14.04 first on this PC.   Then added Win7 later.   I knew if I placed /boot on a separate partition, all I had do to get grub back as my bootloader (and be able to run Ubuntu again) was to restore the /boot partition from my image.   And that's what I did.

RDL

---

### Post by coldcritter64 on 2014-11-17
> I knew if I placed /boot on a separate partition, all I had do to get  grub back as my bootloader (and be able to run Ubuntu again) was to  **restore the /boot partition from my image**.   And that's what I did. The bolded section may work but really is doing it the hard way. Restoring grub after a windows install is simple to do from a live image, even with no /boot partition. A link is provided below for you to check, it is a very simple proceedure especially the "boot-repair" option.

For future reference for yourself and others following.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Robbobden on 2014-11-17
Ok that's probably the easier way.   But at the time, using IFL took only a min to restore /boot.    I had complete success with the resizing operation, by the way.   Screenshot attached showing results.   Thanks !

RDL

---

### Post by coldcritter64 on 2014-11-17
Those results look good. 
Please mark the thread as solved, a guide on how to do so is in the last link in my sig line, if needed. Cheers.

---

### Post by pqwoerituytrueiwoq on 2014-11-17
> **Elfy said:**
> I'll not add much to the thread with the people you've got reading and posting, but, is there any reason for having a seperate home? Especially one so small. Frankly imo you'd be better of adding home to / and letting the system deal with that.
my guess is /home is for app configs and data is for docs, image, and pictures

---

### Post by oldfred on 2014-11-17
/home is so small that it really is not worth having as a separate partition. You will have to be careful that anything normally saved in /home is really saved into your data partition.

And you have used all 4 primary partitions with a primary after the extended. So you cannot expand extended into the unallocated and create additional partitions. Your only option is to expand ext4 to use the unallocated.

---

