---
title: "Recovering Files From Windows With Ubuntu On USB"
date: 2012-12-28
forum: General Help
---

### Post by maggymoo on 2012-12-28
Hey Ubuntu Forums :)

My parents laptop has died not allowing me any access to the OS (Windows Vista). I can fix it, just it would require a wipe of everything. This means I want to recover the data on there first.

I have got very close to a solution using Ubuntu. Pretty much this is my situation:

- Ive got Ubuntu installed on a USB, and my laptop boots from it fine.
- I can see the HDD with windows on it and can navigate around all the folders.
- However I cannot see any of the files that should be on the HDD, only the folders.
- I think this is due to the permissions set on the HDD. Under File Access it is: '---' nothing. I try to change this but once I apply the changes, it reverts back to the odd settings

Is there anyway to change the permissions of my HDD so I can transfer the files to another USB plugged into the computer?

P.S. I do not want to tinker too much with the HDD with windows on it because I dont want to do any irreversible damage, as we can always send it to a specialist to recover the data (expensive). I just want to copy to data onto my USB :)

Thanks for your time,
Maggymoo :)

---

### Post by TheFu on 2012-12-28
The issue you are seeing is NOT NTFS permissions related. It is a corrupted NTFS file system.

Windows not booting is a fairly common issue.  If it isn't due to some new software or device installation 
OR
not due to a hardware failure like the disk controller, disk itself or a cracked motherboard, then it could simply be "lazy bits" on the disk.  Whenever that has happened to my systems, I use a commercial tool, Spinrite [http://spinrite.info](http://spinrite.info), to fix it. At US$89, it is fairly cheap and comes with a money-back guaranty.  I'm just a happy client with ZERO incentive to push the product.

If you want to try something similar to what spinrite does, I'd use **ddrescue** to copy the entire contents of the physical HDD over to a newer HDD of the same size or larger.  This has a 2nd aspect to your solution .... **BACKUPS!@!!!!!@#!@#!@#$!@$!@#@#**!!!!!!
$ sudo ddrescue /dev/sda /dev/sdb /tmp/log
This must be run from an OS that isn't on either sda or sdb - like a liveCD.  Check the man page before using that command to ensure
a) I didn't make a mistake
b) that you understand which specific options are needed for your specific case.

Seriously, the easiest answer would be to just restore everything from a backup, but I suspect your parents do not have that.  With the new HDD, now you can do backups AND sleep better at night. Just be certain that whatever backup method is used, that it is 100% automatic (no human action needed) AND that it stores versioned files - not just 1 copy like a mirror.  A corrupt file that gets mirrored to the backup storage is still corrupt, but if the file is versioned, hopefully, you'll retain enough versions to have a non-corrupt file.  Finding a good backup tool for Windows-whatever is outside the scope of this forum.

Sure, there are other programs that will seek on a HDD and find old files to restore from unused sectors, but those are specifically designed to handle just a few files at a time, not an entire OS.  Plus, it renames every file.  I can't remember the name, but I think is has "record" inside it.  It is designed primarily to recover files from SDHC cards - photos and videos.

If you need to send the HDD to a specialist, can I recommend a friend?  [http://www.myharddrivedied.com/](http://www.myharddrivedied.com/) Scott is fantastic!

Having backups is much easier. Know it, live it, love it.

---

### Post by maggymoo on 2012-12-28
Cheers for the reply dude :)

Yeah I agree about the backups. But this isn't my computer so it is completely neglected. I would guess that this problem wouldn't have even come about if it were my laptop :P

So your telling me, there is so way to move my files from that HDD to my memory stick? It really just looks like its just down to the permissions freaking out?

Because once I have done that I can mess around a little more, knowing that I have the data backed up on my memory stick in case something went wrong.

That software you suggested is cool, but I would rather not spend anything at the moment. Including a new HDD or any software. The computer and its data is not really that valuable, I just thought I could help out and learn a bit from it. I dont even want the whole drive mirrored, I just need a few spreadsheets and photos :P

Just to reiterate, is there absolutely no way I can get something on Ubuntu or my memory stick that can access these windows files?

Thanks :)

---

### Post by Mark Phelps on 2012-12-28
The problem that you are encountering is that in order to properly migrate the files, you first have to be able to successfully MOUNT the filesystem containing the files -- and Linux won't let you do that if the filesystem is corrupted.

Sort of a catch-22.

If you can remove the corrupted hard drive and attach it to a Windows PC, you could try then using RecoverMyFiles (from Runtime Software) on that PC to see if it finds the files you want to save.  It doesn't actually use the filesystem indexes, so it works even if the filesystem is corrupted.

You can download that, install, and run it for free -- to see what it finds. However, you have to PURCHASE it to actually copy the files.  Last time I checked, it was around $80 USD.

---

### Post by TheFu on 2012-12-28
> **maggymoo said:**
> Just to reiterate, is there absolutely no way I can get something on Ubuntu or my memory stick that can access these windows files?

When working on Windows, the best tools for file system corruption issues run in MS-Windows.  The only tool that you should trust to correct it is either **spinrite** OR **ddrescue**.  ddrescue doesn't work on the file level. It works at the partition or disk level.  Using ddrescue will copy every bit, bit-by-bit from the source partition to a target partition.  During that process, it will force the source HDD to attempt reading from the corrupt file system Hopefully, that process will get those bits read and write them to the new partition on the new HDD (or just new-to-you).  The bits will be "refreshed" on the new HDD, thus solving the "lazy bits" aspect of the problem you are seeing.

Again, it is not a permission issue. It is file system corruption, probably caused by lazy bits or some sort of hardware failure.

NTFS access from the Linux side is still a little scary. I think that driver is still beta. If you can mount the partitions from your booted USB stick, then find the files you want to copy off, great. I'd assumed that you had already tried that. I doubt you'll see any better results - as the NTFS file system is still corrupt. THAT is the issue.

Have you tried booting into a Windows rescue mode and running scandisk and chkdsk?  (however those tools are spelled)

Having backups makes this all much easier.

I took control over Mom's PC a few years ago after she got hacked. She's been running Lubuntu ever since.  Just did a system update from 10.04 to 12.04 last week.  Much safer for her that way - plus I find it much easier to have backups of her data shipped to my server a few states away.  backup, backup, backup.

---

