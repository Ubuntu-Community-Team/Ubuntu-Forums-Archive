---
title: "error: no such partition.  Entering rescue mode…  Grub rescue&gt;"
date: 2020-10-01
forum: General Help
---

### Post by SUPERFITTER on 2020-10-01
When I booted computer I got this message: 
[SIZE=1] **error: no such partition.**[/SIZE]
[SIZE=1]**Entering rescue mode…**[/SIZE]
[SIZE=1]**Grub rescue>**[/SIZE]

I ran ls and got my partitions.  Then I ran ls (hd0,msdos[each partition]), then hit enter.  I got file system is ext2.  

Next: set boot=(hd0,msdos2)

Next: set prefix=(hdo,msdos2)/boot/grub

Next: insmod normal

Next: normal

As soon as I hit enter I got a grub menu.  The grub menu looked different than the one I was using before. 

 I clicked on a system and it booted and ran as it always did. 

The problem started again when I rebooted to use a different system.

I re did the commands above and got the same different grub menu.  I clicked on a different system and it boot right up.

What am I doing wrong?

Thank You

---

### Post by oldfred on 2020-10-01
If you installed another system, did it not install grub correctly?

Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by TheFu on 2020-10-01
Sorry, I don't have any clues to fix it.

In early July, my 3-week old 20.04 Ubuntu-Mate system had a similar issue.  After screwing around trying to get everything working using a mix of guides and *Try Ubuntu* environments (which usually solve everything), I gave up. Normally, a little chroot action, grub-install, update-grub solves this stuff easily. Not for me, not this time.

I'd wasted 45 minutes and decided that was enough.  I have daily, automatic, versioned, backups for a reason.  This is exactly why.  When something goes bad, I don't have to screw around too much - just wipe, do a fresh install and restore from backups. That's the point.

45 min later, with a fresh install, all my data, settings restored and applications installed, it was "my system" again. That was 90 minutes wasted, but at least it was just a bad day, no data lost, and I was back using the system.

The **boot-info** data will be very helpful, if you have time.

---

### Post by TygerTung on 2020-10-01
How do you recommend to carry out the automatic versioned backups?

---

### Post by oldfred on 2020-10-01
You can search forum for more from TheFu.

Best practice for Backups - theFu
[https://ubuntuforums.org/showthread.php?t=2436006](https://ubuntuforums.org/showthread.php?t=2436006)
[https://ubuntuforums.org/showthread.php?t=2368992&](https://ubuntuforums.org/showthread.php?t=2368992&) 
[https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986](https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986)
[https://ubuntuforums.org/showthread.php?t=2311501](https://ubuntuforums.org/showthread.php?t=2311501)
[https://ubuntuforums.org/showthread.php?t=2419993](https://ubuntuforums.org/showthread.php?t=2419993)
More backup info from 1clue
[https://ubuntuforums.org/showthread.php?t=2377810](https://ubuntuforums.org/showthread.php?t=2377810)
[https://askubuntu.com/questions/569679/whats-a-good-back-up-strategy-for-1-desktop-pc](https://askubuntu.com/questions/569679/whats-a-good-back-up-strategy-for-1-desktop-pc)

[https://rdiff-backup.net/](https://rdiff-backup.net/)
Discussion of issues on rsync bash file &  rdiff-backup  - TheFu
[https://ubuntuforums.org/showthread.php?t=2440020](https://ubuntuforums.org/showthread.php?t=2440020)
[https://ubuntuforums.org/showthread.php?t=2392127](https://ubuntuforums.org/showthread.php?t=2392127)
[http://ubuntuforums.org/showthread.php?t=2224428](http://ubuntuforums.org/showthread.php?t=2224428)
[http://www.kirya.net/articles/backups-using-rdiff-backup/--delete](http://www.kirya.net/articles/backups-using-rdiff-backup/--delete)

---

### Post by TheFu on 2020-10-02
> **TygerTung said:**
> How do you recommend to carry out the automatic versioned backups?

There are certain basic skills that are necessary. If you don't have those skills, then my methods could be very frustrating. I don't point-n-click.

Here's a simple script for backing up HOME directories:
[https://ubuntuforums.org/showthread.php?t=2447368&p=13973172#post13973172](https://ubuntuforums.org/showthread.php?t=2447368&p=13973172#post13973172)

I kept that script really simple so eyes don't glaze over. I also showed some best practice techniques for all scripting, but left out some best practice techniques in the way I'd actually do it for simplicity. The filename isn't too important, but the location for it **is** important. There are subtle reasons for almost everything in that script. About the only thing that could be changed is the TARGET location for the backup storage mount.

Stuff that you might want to add to the script is listed in that thread. The real scripts I use to backup systems is more complex, because I want more data, more system settings, and some files to make the restore easier. Until I've actually tested a restore, I don't know if the script for any specific system is working.  I use lots of virtual machines, so testing isn't hard.  I just bring up a new VM and test a restore there.

Some of the basic skills are:
[LIST]
[*]simple bash scripting
[*]understanding of crontabs/cron
[*]ability to use manpages for references (rdiff-backup mainly, but any command in the script)
[*]understanding of Unix file and directory permissions
[*]understanding of mount and umount
[*]understanding of different file systems and why NTFS/FAT-whatever cannot be used
[*]For networked backups, understanding of ssh, ssh-keys, and network backup tools
[/LIST]

Most of those skills are covered in: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) but can take years to learn or a few months for someone specifically working towards the goal.

---

### Post by SUPERFITTER on 2020-10-03
I found the problem installation and formatted the partition it was located in. I reinstalled the operating system back into that partition.  If I have a large hard drive, I partition it so I have a section to put the operating systems in and a larger partition to put folders in like pictures, music, documents, downloads etc.  This way if I have a problem with a operating system and it will consume a lot of time trying to figure out how to fix it, I just reinstall that operating system.

On the machines that have two drives, I do the same thing, one has operating systems and the other has all my stuff that I want to save.  I can back up the second drive on an external drive easily.

---

