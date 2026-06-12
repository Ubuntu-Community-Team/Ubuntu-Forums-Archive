---
title: "help needed. hard drive lost"
date: 2020-08-23
forum: General Help
---

### Post by bike2work on 2020-08-23
Hi,

I messed up my usb hard drive of 4T. I was preparing ubuntu installation USB but mistakenly used my USB connected hard drive thinking that was the USB stick. Now I cannot see the hard drive anymore. I could not upload a picture for whatever reason. What used to be the hard drive name (Seagate something) became Ubuntu 20.04 LTS .... When clicked, the error mounting the drive is shown: error mounting /dev/sdb1 at /media/nianqing/Ubuntu 20.04 ....

I tried ntfsfix /dev/sdb1 which give me error:

[INDENT][I]Mounting volume... NTFS signature is missing.
FAILED
Attempting to correct errors... NTFS signature is missing.
FAILED
Failed to startup volume: Invalid argument
NTFS signature is missing.
Trying the alternate boot sector
Unrecoverable error
Volume is corrupt. You should run chkdsk.
[/I][/INDENT]

fdisk -l show this is the drive:[INDENT][I]
Disk /dev/sdb: 2.75 TiB, 3000592977920 bytes, 732566645 sectors
Disk model: Expansion Desk  
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x15f006ae

Device     Boot   Start     End Sectors  Size Id Type
/dev/sdb1  *          0 5303231 5303232 20.2G  0 Empty
/dev/sdb2       4222640 4230575    7936   31M ef EFI (FAT-12/16/32)[/I]
[/INDENT]

I tried to see if I can find it on windows but no use. The drive does not show up.

What should I do now? Did I lose all the 4T data (or 2.75T as reported by fdisk but it should be 4T)? Any way to recover it?


Thanks for your help!

---

### Post by zebra2 on 2020-08-23
1. you cannot access more than about 2.2T of your 4T HD unless you are using a 64bit OS and have formatted the drive with a partition such as GPT that will support 4T.  Linux 
wk4 and Windows NTFS will not format the entire 4T. 

2. If you were creating an install media with Startup Disk Creator, the system would have deleted the partition on the drive and reformatted it with its default Partition and everything on the drive would be deleted. The system warns you of this before you ok the operation.  It will only do what you ask.

3. Be careful when you use any program that can format a disk. 

4. Can the data be recovered? I doubt it, but you can wait for a post from someone that knows more about this than I do.  

Congratulations on your new knowledge experience.  Hope you do well with it.

---

### Post by TheFu on 2020-08-23
**Step one - make a clone of the disk, now, before you do anything else.** Use **ddrescue** to create the clone of the entire disk. The new HDD must be at least the same size as the current one.  Everything below is high risk for losing all the data, beyond the 10GB that is probably already overwritten and gone, gone, gone.

> **zebra2 said:**
> 1. you cannot access more than about 2.2T of your 4T HD unless you are using a 64bit OS and have formatted the drive with a partition such as GPT that will support 4T.  Linux 
wk4 and Windows NTFS will not format the entire 4T. 

Looks like whatever you did, created an MSDOS partition table when a GPT partition table is required.  Forget the 64-bit OS remark - that isn't true.  32-bit Linux has supported huge partitions for decades. Just depends on the storage management and the file system used.  20TB hasn't been any problem with XFS since the 1990s, perhaps before then. XFS supports petabytes now.  EXT4 has supported huge partitions for a long time too.

The limitation for a single disk isn't the 32-bit OS. It is the partition table type.  MS-Windows has many arbitrary limitations on 64-bit vs 32-bit, UEFI booting and a few other things that aren't actually in any standards. Linux follows the standards for those things.  In short, MSFT decided they needed a way to force people to move to 64-bit OSes when it wasn't really needed, so they abused UEFI booting for that purpose. Linux doesn't do that.

> **zebra2 said:**
> 
3. Be careful when you use any program that can format a disk. 

+1.  Everyone does something like you have once.  Hopefully, you'll learn from this and not have it happen again. Whenever doing anything that can be destructive, take extra care, don't be in any hurry, and always, always, have a backup that you know can be restored. A backup that hasn't been tested is only hope, not a plan. You and your data deserve to have a plan.

> **zebra2 said:**
> 
4. Can the data be recovered? I doubt it, but you can wait for a post from someone that knows more about this than I do.  
Congratulations on your new knowledge experience.  Hope you do well with it.

It might be possible to get the data back that was not overwritten, but the correct answer is to have backups that can be restored.  After all, if something is important enough to keep, then there should be backups for that data.
I'd have backups - I do have backups - so I'd never be in the same situation you are, but if I was going to attempt anything, I'd have the exact disk layout from before the new partition table and any new partitions were created. Without that, you are really screwed and have to hope that some forensics tools can magically locate that data.

So - there is "some" good news.  GPT is better for all disks because it stores 2 copies of the partition table.
[LIST]
[*]a) at the front of the disk
[*]b) at the opposite end of the disk
[/LIST]

When the MS-DOS partition was created, it only saw a 2.2TB disk and couldn't "reach" the far end to overwrite that 2nd GPT copy.  There must be a GPT tool that can take that 2nd copy and force it back onto the first/beginning of the drive.  I don't know which tool can do that, but I'd start with **gdisk**. Other tools are **testdisk** and **photorec**.  Testdisk can search for partition separation markers. It won't be fast - expect the scan to take a day or 2.

After you get the GPT partition table back and all the partitions as they were before, then you can start scanning for files using **photorec**.  This will be extremely painful across a 4TB disk and will take days.  There is no way to restore in place with photorec.  The data must be written to a different partition on a different disk. Effectively, you'll need 2 new 4TB HDDs. 
[LIST]
[*]Clone of the original, so when something bad happens and you lose all data, you can re-clone and start over
[*]Target partition to store the recovered, but wrongly named files.
[/LIST]

Be very careful to understand that a disk and a partition are completely different. It is unfortunate that MSFT has incorrectly used those terms since 1980. Linux doesn't use them wrong.  Be certain you don't either.

If the HDD was formatted with the NTFS file system, then using some Windows data recovery software may be able to better restore the files in-place on NTFS. I don't know.  I have backups.

Ubuntu Data Recovery Guide: [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Good luck. It is likely that most of the data is still on the disk, assuming you didn't get impatient and do something foolish. That's what caused this problem. Be slow, deliberate, careful. If you don't understand something, look it up and read until you do.

---

### Post by Quarkrad on 2020-08-24
If the hdd was formatted with NTFS (as TheFu commented above) a good windows tool is GetDataBack.  I have had amazing results with this software back in my Windows days.  Again, as commented above, this is another tool that can take a long time to fully scan the HDD but it is often worth waiting.

---

### Post by bike2work on 2020-08-24
Thanks for your replies, particularly @TheFu!

1) I used ubuntu's "Startup Disk Creator" for creating the usb start up. It does not say which type to format. Do you know? The fdisk -l saying "Empty" (as opposed to NTFS or Fat)
2)The first step by TheFu is to make a copy of the hdd. Going through the document TheFu suggested, I should use ddrecure for this?
3)I tried testdisk before, it says select a drive and hit enter. But enter just move the cursor back. Somehow the menu is with "Previous" selected and I could not move that. I will try to find out about this.

Thanks!

---

### Post by ActionParsnip on 2020-08-24
Do you have backups? If not, why not?

---

### Post by oldfred on 2020-08-24
If drive was gpt which any drive over 2TiB should be, what does this show?
It may then see backup gpt partition table. 

sudo gdisk -l /dev/sdX  # where sdX is your 4TB drive, sdb or whatever it becomes.
I have drives change device order when plugging in flash drive, so my sdb becomes sdc as flash drive becomes sda. Always check if using correct drive if using device.

---

### Post by TheFu on 2020-08-24
1) That is for creating a "Try Ubuntu" or "Install Ubuntu" disk.  Only do that if you don't have a flash drive already with the version of Ubuntu desktop created.  Nothing I wrote above is related to that ... other than to use it.  I have never used "Startup Disk Creator". I would just use dd or ddrescue for creating the flash drive with the Ubuntu.iso on it.  To me, GUIs just get in the way, slow things down, and hide 80% of the capabilities that a tool has.  dd is freakin' amazing.  cp is just dd.  cat is just dd.  ls is just dd, each with a little bit of a wrapper to make it clearer.  Almost everything we do on Linux is about moving bits from a--->b. That's what dd does. Sometimes we need to filter or translate those bits in the middle ... which dd can do as well.  ;)  Sorry, I've digressed, but everything on any Unix system is either a process or a file. dd works on files.

2) Yes.  ddrescue is a smarter dd. It keeps going if there are disk/partition problems like unreadable sectors.  dd and ddrescue are stupid.  Both copies whatever input "bits" to the output "bits" - exactly.  If either the input or output are wrong, it will still copy input ---> output.  It is stupid and assumes that you can read, understand, and enter the correct order for command line arguments.  Get the arguements backwards and both will happily copy the output file(device) to the input file (device).  They don't know if the input or output are incorrect. They don't know if the user is being stupid or a genius - that's hard to tell, so they just do what we ask. People incapable of getting the correct arguments in the correct order with the correct options shouldn't listen to me anymore and should pay someone $3000 to recover the data.  

3) If using testdisk is a problem, read the manpage for it and watch a few youtube videos about it. Often, seeing someone else use it will be eye opening.  If you screw up while using testdisk, you'll need that other cloned disk to re-clone back onto the original.  **DO NOT SKIP THE DISK CLONING.**  Once that is done - disconnect the cloned disk and put it into a different room. Based on the questions, I think it is highly likely data will be destroyed, perhaps a few times, before getting experience and confidence to use the tools to the greatest effectiveness.

Having solid backups makes life easier and less risky. Everything in this thread is a high risk activity.

If you don't know where/how to read the help for every command, ask. Usually, you'll want to read the local documentation, not use google. This way you'll be reading the docs for the exact versions of the software installed on your system, not 2 year newer stuff or 5 yr old stuff.  Options change over time and until we get burned with the wrong option, we seldom notice. The local manpages are, by definition, correct.

Photorec is a pain to use. Here's why:
Any files that photorec recovers will be given completely useless names, f54295323.ext, and you'll need to rename each file.  With 4TB, and assume each file is 2GB, that will be 2,000 files to manually rename.  2GB is a large file average.  Most are 20KB - 20MB.  There is a technical term for how many files like that are on a full 4TB disk, Sh....load.  In short, if the disk is NTFS, you'll be much happier using native Windows data recovery tools.  As I vaguely remember about Windows, only the first character of a filename is removed in Windows file systems at deletion.  Say one of the files is "Sharky's Machine.mkv"  Windows data recovery would show "?harky's Machine.mkv" ... and you could probably fill in the "S" from basic knowledge.  Photorec will make a file named "f38349223.mkv" - so you'd have to watch it, try to remember the real name, and type it in.  For 2,000+ files.  Ouch.  Do you really want to do that?

---

