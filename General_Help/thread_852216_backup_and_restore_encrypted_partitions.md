---
title: "backup and restore encrypted partitions"
date: 2008-07-07
forum: General Help
---

### Post by treymul on 2008-07-07
Hey everyone, I have a problem.  I have a dual boot system with vista and Ubuntu 7.10.  I have one windows partition, a small boot partition, and an encrypted partition using LVM that contains a / and a swap.  I can backup the entire encrypted partition with tar commands found on this forum no problem.  I can even restore it no problem, until I reboot, then I get kernal errors.  I can't give you the exact error ( 17 or 18 I think) because its been a while and I'm scared to test my restore again for fear of having to start all over from scratch.  

What I want to know is the seperate boot partition, is it being backed up with this command: tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /?  If so, why am I getting kernal errors?  

Last time I tried, I tried restoring grub as described here: 
[http://ubuntuforums.org/showthread.php?t=24113&highlight=grub+restore](http://ubuntuforums.org/showthread.php?t=24113&highlight=grub+restore), but it didn't work.  I'm thinking it might have something to do with kernal upgrades.  The backup up was made with one kernal, but when I tried to restore, there were two kernals present.  Could that be the problem?

Or if anyone can point me to a walk through of how to do this properly, I would greatly appreciate it. Thanks

---

### Post by treymul on 2008-07-10
Nobody have any experience with this?

---

### Post by treymul on 2008-07-14
bump

---

### Post by bodhi.zazen on 2008-07-14
Well, it is a little complex as you can imagine.

You have 3 partitions, 2 are encrypted (/ and swap), 1 is not (boot).

I would unmount /boot and tar up / as you are (skipping /swap as well)

Then tar up your boot partition.

Then I would restore them separately /.tar to / and boot.tar to /boot

My guess is when you restore from your current tar you are putting the contents of /boot back onto an encrypted partition and not into your separate boot partition (unless you are doing this from a live CD and have mounted the boot partition at /boot).

---

### Post by treymul on 2008-07-15
Thanks, I will give that a try.

---

### Post by chmac on 2008-12-15
treymul, have you had a chance to test? Any feedback to report?

I also run an encrypted LVM so I'd be interested to see how you managed to restore. I don't currently keep full backups of my LVM as my laptop disk is bigger than my back updis. But that is about to change. :)

---

### Post by treymul on 2009-03-28
I did get it working if anyone is interested.

---

### Post by bodhi.zazen on 2009-03-28
> **treymul said:**
> I did get it working if anyone is interested.

If you have the time , post back how ;)

---

### Post by treymul on 2009-03-28
There is probably an easier way, but this was the only way I could get it to work.  You were right about having to do boot seperately.  I also had to reinstall the base system, which changed the partition records to something different than when I backed up.  This caused problems when ever I rebooted after backing up.

Anyways this is what I came up with.

install new base system, redoing your partition setup if you want.  After installing the base system, make copies of grub/menu.lst,etc/fstab,etc/crypttab for later use.  untar your backup into /. replace the uuid info from the copies you just made above to the newly untarred versions.

run "update-initramfs -k all -c" and save these somewhere.  mount boot partition and erase it. untar boot.backup into boot partition.
edit menu.lst to match original uuid info from the copy you made earlier.
replace initramfs with the newly generated ones from earlier.

This has gotten me up and running several times.

---

### Post by jpullen on 2010-07-17
Would you be willing to share your backup scripts?

---

### Post by chmac on 2010-07-17
I found [this thread]("http://ubuntuforums.org/showthread.php?t=1205372") very useful to upgrade within an encrypted disk. Parts might be relevant here, maybe saving and restoring /etc/crypttab? I backup /home, /etc and other critical data, rather than backing up the whole encrypted disk in one go.

---

