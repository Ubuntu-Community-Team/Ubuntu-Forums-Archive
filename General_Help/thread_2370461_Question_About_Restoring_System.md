---
title: "Question About Restoring System"
date: 2017-09-03
forum: General Help
---

### Post by bilkay on 2017-09-03
After doing an 'upgrade, it looks like I may have to wipe 16.04 and revert back to 14.04. I have the old system (14.04) backed up to a dump file. Reading in the Tutorial section about restoring a system leaves me with a big question. The tutorial says to just extract everything from the backup tar file (I'd be doing the same from a dump file). But that would leave a lot of useless files from the release being replaced taking up a lot of space. I'd prefer deleting everything before doing the restore. Is this possible to do without doing a livecd boot?

---

### Post by TheFu on 2017-09-04
Yes. You may use a live-boot flash drive too or external USB disk or SDHC card or microSDHC card or ... any other bootable storage.  It doesn't have to be a CDROM, it could be any of those options or a DVD.

No, cannot perform these tasks FROM the system you want to wipe, if that was the question.  Making and using a live-boot distro/install is a basic Linux skill.  Learn it. Know it. Love it.

---

### Post by bilkay on 2017-09-04
Thanks for responding. Could you be so kind as to answer one more question? If I livecd boot, then mount my root directory,  chroot to it, and then delete everything and restore to it, will running update-grub from that condition properly update grub? I've tried to find a comprehensive procedure for restoring a system and couldn't find a good one, and the one on this forum looks to me to be junk.

Another thought: Obviously, completely wiping a running system and then trying to restore to it wouldn't work because the programs needed to restore wouldn't be there. But here's another possibility: Restore the old system to a different location, then use rsync with --delete option to restore critical directories (/bin, /usr/bin, /sbin) and then delete/restore the rest.

---

### Post by bilkay on 2017-09-04
p.s. Thanks for not being pedantic.

---

### Post by TheFu on 2017-09-04
Feel free to try anything. It isn't like you have anything to loose. Worst case, you get to do it again.

If you don't have the time to screw around, use some other boot media.

---

### Post by bilkay on 2017-09-04
I'd feel a lot freer if I had some assurance that my plan isn't going to leave me with no way to boot.

---

### Post by bilkay on 2017-09-05
I had the old system (14.04) backed up to a dump file. I created a new directory /recovery and restored the dump to it (NOTE: If you use dump and restore for your backup, when you restore, answer NO when it asks if you want to set user mode). I'm planning to run the following script (as root) to see if it works:

```
#! /bin/bash

# Assume system to be recovered has been restored to directory /recovery
# located on the same filesystem as /. Also assume that everything is on the
# same partition.

# The following based on what directories in /recovery have anything in them.

cd /recovery

mv /var /var.bak
mv var /
mv /usr /usr.bak
mv usr /
mv /sbin /sbin.bak
mv sbin /
mv /run /run.bak
mv run /
mv /lib /lib.bak
mv lib /
mv /etc /etc.bak
mv etc /
mv /debian /debian.bak
mv debian /
mv /boot /boot.bak
mv boot /
mv /dev /dev.bak
mv dev /
mv /initrd.img /initrd.img.bak
mv initrd.img /
mv /initrd.img.old initrd.img.old.bak
mv initrd.img.old /
mv /vmlinuz /vmlinuz.bak
mv vmlinuz /
mv /vmlinuz.old /vmlinuz.old.bak
mv vmlinuz.old /

./bin/mv /bin /bin.bak
/bin.bak/mv bin /

echo -n "Continue to update-grub? ";read x
[ "${x}" == "y" -o "${x}" == "Y" ] || exit

update-grub

echo -n "Continue to reboot? ";read x
[ "${x}" == "y" -o "${x}" == "Y" ] || exit

shutdown -r now

```

One thing that bothers me is that the /recovery/dev directory doesn't have any devices for sda{n} or anything that looks like a device for disks. Is this to be expected? I don't understand why they're not included in the dump.

---

### Post by bilkay on 2017-09-06
First run failed! Constructive comments (positive or negative) welcome.

The attempt to move /run returned a device busy message. Since `df /run` shows it mounted on tmpfs, I kind of understand, but since my linux education is strictly trial and error (with occasional help), my understanding is only "kind of".

Everything after that failed with error /bin/mv not found. This I don't understand since the only changes to that point involved /usr /var and /sbin.

Next anomoly: I boot with livecd and mount /dev/sda1 successfully on /mnt. When I tried to chroot to /mnt it failed with an error about /bin/bash not being found. After I changed (mv'd) everything on /mnt back to where it was before running my script, I could chroot.

Any advice or comments (negative or positive) will be greatly appreciated!

---

### Post by TheFu on 2017-09-06
If you don't have the time to screw around, use some other boot media, mount the storage, move everything from a different, running, OS.  You were doing it the hard way.

As I said before:
> No, cannot perform these tasks FROM the system you want to wipe, if that was the question. Making and using a live-boot distro/install is a basic Linux skill. Learn it. Know it. Love it. 

Boot from alternate boot media with an alternate running OS.  Mount the old OS storage.  Wipe it.  Install any tools you need to restore the 'dump' (probably restore) and use that tool to put everything back the way you backed it up.  If you put things back where they were, /boot, /boot/efi, /, and whatever else.  Then use a chroot to mount the newly restored OS and change all the /usr, /bin, /boot from the new area so you can use those tools and re-install grub, then update grub.  Back out of the chroot and reboot.  There are chroot guides in a few reputable websites. I'll google ... [https://help.ubuntu.com/community/LiveCdRecovery#Update_Failure](https://help.ubuntu.com/community/LiveCdRecovery#Update_Failure) - follow the **Failed Update** section.  The important part is to use the programs FROM the newly recovered OS to perform all the grub stuff.
 
Learn about the Linux File System Hierarchy.  Wikipedia has an overview article. It explains what goes where and why.

---

### Post by raleigh3 on 2017-09-06
> **bilkay said:**
> After doing an 'upgrade, it looks like I may have to wipe 16.04 and revert back to 14.04. I have the old system (14.04) backed up to a dump file. Reading in the Tutorial section about restoring a system leaves me with a big question. The tutorial says to just extract everything from the backup tar file (I'd be doing the same from a dump file). But that would leave a lot of useless files from the release being replaced taking up a lot of space. I'd prefer deleting everything before doing the restore. Is this possible to do without doing a livecd boot?

I suggest using Clonezilla in the future to do backups.

---

### Post by bilkay on 2017-09-06
> **TheFu said:**
> Feel free to try anything. It isn't like you have anything to loose. Worst case, you get to do it again.

If you don't have the time to screw around, use some other boot media.

You did say to try anything. :)

At risk of being a pain, could you please look at the following script and tell me if it's likely to succeed? 

```

#! /bin/bash

# To be run after booting with livecd

# Assume system to be recovered has been restored to directory /recovery
# located on the same filesystem as /. Also assume that everything is on the
# same partition.

# The following based on what directories in /recovery have anything in them.

mount /dev/sda1 /mnt
cd /mnt/recovery

mv ../var ../var.bak
mv var ..
mv ../usr ../usr.bak
mv usr ..
mv ../sbin ../sbin.bak
mv sbin ..
mv ../run ../run.bak
mv run ..
mv ../lib ../lib.bak
mv lib ..
mv ../etc ../etc.bak
mv etc ..
mv ../debian ../debian.bak
mv debian ..
mv ../boot ../boot.bak
mv boot ..
mv ../dev ../dev.bak
mv dev ..
mv ../bin ../bin.bak
mv bin ..
mv ../initrd.img ../initrd.img.bak
mv initrd.img ..
mv ../initrd.img.old initrd.img.old.bak
mv initrd.img.old ..
mv ../vmlinuz ../vmlinuz.bak
mv vmlinuz ..
mv ../vmlinuz.old ../vmlinuz.old.bak
mv vmlinuz.old ..


ls ..

# If successful:
# $ cd /
# $ mount -t proc proc /mnt/proc
# $ mount -t sysfs sys /mnt/sys
# $ mount -o bind /dev /mnt/dev
# $ chroot /mnt
# $ update-grub
```

p.s. I got the mount commands in the script for proc, sys and dev from [https://superuser.com/questions/111152/whats-the-proper-way-to-prepare-chroot-to-recover-a-broken-linux-installation](https://superuser.com/questions/111152/whats-the-proper-way-to-prepare-chroot-to-recover-a-broken-linux-installation). Question: should there also be one for run?

---

### Post by TheFu on 2017-09-06
I don't think it will work.  Seems like the hard way, even if you add the missing parts and figure out how to make it work.

---

### Post by bilkay on 2017-09-06
> **raleigh3 said:**
> I suggest using Clonezilla in the future to do backups.

Why?

---

### Post by bilkay on 2017-09-06
> **TheFu said:**
> I don't think it will work.  Seems like the hard way, even if you add the missing parts and figure out how to make it work.

Could you be a little more specific? What won't work and how could I make it easier?

---

### Post by TheFu on 2017-09-06
Wipe the disk.  Restore the dump.  Run grub install. Run update grub.  

There are 50+ different solutions. Sorry that I don't know all of them or even many of them.  I know 1 that will work.  It isn't the one you are trying. Sorry.

You seem to think I **know** how to make your method work. I do not. I just know it is the harder way than what I've already said ... 3 times.

I will tell you that a clone/image is not a backup.  Those are good for 1 purpose - immediately moving data from 1 disk to another.  That's great, but pretty limited.  There are much better methods than cloning disk these days.  I only clone systems when it is time to move disks.  Any other time, it is a waste.  Backups have versions.  We can restore from yesterday, last week, last month easily.  However, my backup method does require that I boot from a live-boot environment, mount the storage I want to target and restore files onto those areas.  Then I chroot and run grub-install followed by update-grub.  THAT is pretty standard for restoring from a backup.  Besides the actual restore, it takes about 3 minutes.

---

### Post by bilkay on 2017-09-06
> **TheFu said:**
> Wipe the disk.  Restore the dump.  Run grub install. Run update grub.  

There are 50+ different solutions. Sorry that I don't know all of them or even many of them.  I know 1 that will work.  It isn't the one you are trying. Sorry.

You seem to think I **know** how to make your method work. I do not. I just know it is the harder way than what I've already said ... 3 times.

I will tell you that a clone/image is not a backup.  Those are good for 1 purpose - immediately moving data from 1 disk to another.  That's great, but pretty limited.  There are much better methods than cloning disk these days.  I only clone systems when it is time to move disks.  Any other time, it is a waste.  Backups have versions.  We can restore from yesterday, last week, last month easily.  However, my backup method does require that I boot from a live-boot environment, mount the storage I want to target and restore files onto those areas.  Then I chroot and run grub-install followed by update-grub.  THAT is pretty standard for restoring from a backup.  Besides the actual restore, it takes about 3 minutes.

That's easy, but wiping a working system is something I'd prefer to avoid. As I've shown, I have a backup of the previous version restored on /dev/sda1:/recovery. If I mount /dev/sda1 on /mnt (in livecd environment) and chroot to /mnt/recovery, wouldn't that be equivalent to what you're describing? Not sure why I'd have to run grub-install if grub is already installed.

---

### Post by raleigh3 on 2017-09-06
> **bilkay said:**
> Why?

You won't have any 'useless' files.

---

### Post by deadflowr on 2017-09-06
> Reading in the Tutorial section about restoring a system leaves me with a big question.
Probably would help if you could link the referenced tutorial...

---

### Post by bilkay on 2017-09-06
> **deadflowr said:**
> Probably would help if you could link the referenced tutorial...

[https://ubuntuforums.org/showthread.php?t=35087]("https://ubuntuforums.org/showthread.php?t=35087")
I'm surprised this thread hasn't been flagged as crap.

Quote in lead message: "One of the beautiful things of Linux is that This'll work even on a  running system; no need to screw around with boot-cd's or anything.

---

### Post by bilkay on 2017-09-06
> **raleigh3 said:**
> You won't have any 'useless' files.

I don't have any useless files now. My backups (using dump) are done automatically and incrementally and obsolete dump files are automatically (using cron) deleted. The nice thing about dump is restore can be run interactively and individual files and/or directories can easily be marked for restoration and be restored to any location. The "bad" thing about it is that the livecd doesn't have restore which is why I restored my backup to /recovery so it will be there when I boot into the livecd environment.

---

### Post by leunam12 on 2017-09-07
I clonezilla my system partition every week, it takes less than 5 minutes (including boot time); if I break my system, all I have to do is restore it from the clonezilla image; it takes less than 5 minutes including boot time. To me nothing could be simpler and more effective than that.

This is my suggestion: Download Clonezilla and make a bootable USB drive, boot from it, clone your working system and then wipe your hard drive and restore your backup to it. If something goes wrong fire up Clonezilla again and restore your working system back; you will not lose anything. 

Now, regarding your script: it is unclear to me what is it that you are trying to achieve with it, all it is doing, as far as I can tell is renaming old directories, and then it tells you that if it is successful install GRUB. But there is nothing there, in the script, that will restore your working backup files  to where they are supposed to be. It seems that your files are in  /recovery, but your system is not going to run from /recovery. those  files and directories that you have in /recovery have to be restored to  their respective place in order to have a working system.

---

### Post by bilkay on 2017-09-07
> **leunam12 said:**
> I clonezilla my system partition every week, it takes less than 5 minutes (including boot time); if I break my system, all I have to do is restore it from the clonezilla image; it takes less than 5 minutes including boot time. To me nothing could be simpler and more effective than that.

What if I just want to retrieve a single file from it? It's super-easy to do with dump/restore. I back up my system incrementally on a daily basis without any action by me. Periodically, I do a level 0 (full) dump to dvd. My backup schedule has level 1 (diff 0-1)  run on Sunday night (I write those to DVD on Monday), level 2 (diff 1-2) on Monday night, etc. thru Saturday night. If did something to a file on Tuesday and then again on Wednesday, I can retrieve either version of it from my dump files. Can Clonezilla do that?

---

### Post by bilkay on 2017-09-07
> **leunam12 said:**
> Now, regarding your script: it is unclear to me what is it that you are trying to achieve with it, all it is doing, as far as I can tell is renaming old directories, and then it tells you that if it is successful install GRUB. But there is nothing there, in the script, that will restore your working backup files  to where they are supposed to be. It seems that your files are in  /recovery, but your system is not going to run from /recovery. those  files and directories that you have in /recovery have to be restored to  their respective place in order to have a working system.

I planned it that way because there are other directories (like /home that are backed up separately) that have to be included. But after further consideration, I think the way I'll do it is to move those directories into /recovery (while in the livecd environment), and then chroot to /mnt/recovery to run update-grub.

---

### Post by bilkay on 2017-09-08
I bit the bullet and livecd'd, restored the root directory to the recovery state and did chroot/update-grub/reboot. So far, everything SEEMS to be OK except for mysql. I get "ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (which doesn't exist)" when I try to run mysql. When I try to start/restart the mysql service, I get "Job failed to start". Going through many bing pages didn't give any answers that I could use. I also tried reinstalling mysql-server and mysql-client with no improvement.

---

