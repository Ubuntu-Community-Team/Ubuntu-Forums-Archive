---
title: "Seagate Backup Plus 3TB external USB disk drive bricked?"
date: 2012-10-31
forum: General Help
---

### Post by oregonbob on 2012-10-31
I purchased a new Seagate Backup Plus external USB hard drive. I plugged it into an Ubuntu PC and decided it was slow. I assumed I could improve it by deleting to default NTFS filesystem that comes with it and creating a new partition with Ext3 or Ext4 type. I hoped this would improve performance and compatibility with Ubuntu linux.

So I plugged it in. It automatically mounted the NTFS just fine. Then I went into disk utility and deleted the existing NTFS filesystem. It did that OK.

Then I tried to create a new Ext4 partition. It failed. So then I tried Ext3. It failed to. After that I plugged it into a Windows PC hoping to recover something. But Windows disk utility don't help.

I think I bricked it!

Has anyone else been there and done that, hopefully found a solution?

---

### Post by oregonbob on 2012-10-31
I managed to get a new NTFS partition installed and working on it. The trick was in Windows disk manager to make it a GUID (GPT) disk, then I could create a new NTFS. As I mentioned I thought it would be better to run ext3 or ext4. It would appear this unit is not compatible with those linux filesystem types.

Anyone else used these with a linux partition?

---

### Post by jerome1232 on 2012-10-31
I have a Seagate External with Ext4 on it right now, there is no reason  that I know of that would prevent you from putting whatever file system  you please on there.

---

### Post by oregonbob on 2012-10-31
I have **other** external USB drives of different models that I had no problem installing ext3 or ext4 on. But this one it would not do. It may have something to do with the Seagate firmware or the fact that it is a 3TB drive.

After getting it to work on a Windows 7 PC again, I went back to Ubuntu 12.04 to try making a ext filesystem. The Ubuntu disk utility allows me to delete the NTFS filesystem OK, but when I try to create any type of filesystem with Ubuntu it fails. I tried smaller partition sizes (<2TB), I tried ext3, ext4, NTFS. None of these attempts would work. Here is the "Details" of a typical error message is Disk Utility:
--------------------------
[COLOR="Blue"][/COLOR]Error creating partition: helper exited with exit code 1: In part_add_partition: device_file=/dev/sdc, start=134242304, size=1500000000000, type=
Entering MS-DOS parser (offset=0, size=3000592977920)
MSDOS_MAGIC found
found partition type 0xee => protective MBR for GPT
Exiting MS-DOS parser
Entering EFI GPT parser
No GPT_MAGIC found
Leaving EFI GPT parser
Entering Apple parser
No MAC_MAGIC found
Leaving Apple parser
No known partition table found
got it
got disk
Error: Can't have a partition outside the disk!
ped_partition_new() failed
-----------------------------------------

---

### Post by oregonbob on 2012-10-31
I think I solved this by experimentation. I was able to create a nearly 3TB Ext3 filesystem with gparted . The standard Ubuntu disk utility would not handle it.

First I took it back to a Windows 7 PC, where I ran Disk Manager on it and chose the option to make it a GPT (GUID?) drive. This was the only way Windows 7 could create a partition larger than 2TB.

The process of converting it to a GPT drive placed a small 128MB partition at the beginning. Then I left the remainder unallocated.

Then I plugged the external drive back into my Ubuntu 12.04 and installed the optional "gparted" program. It allowed me to create the large parition and format it Ext3. All appears to be well now. It will mount just fine on my Ubuntu 12.04. Now my real test will be to mount it on a Ubuntu 8.10 server.

---

### Post by jerome1232 on 2012-10-31
Didn't realize you were trying to use the Disk Utility in Ubuntu (you even said that in your OP), I've never actually tried to use that. You should be good to redo the disk label as MBR (or leave it GPT) from Gparted and format it as your preferred file system, getting rid of that small partition, which would annoy the crap out of me even it is insignificant.

---

