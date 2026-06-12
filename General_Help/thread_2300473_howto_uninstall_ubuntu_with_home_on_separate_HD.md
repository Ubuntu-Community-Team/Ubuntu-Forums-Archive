---
title: "howto uninstall ubuntu with /home on separate HD"
date: 2015-10-26
forum: General Help
---

### Post by Old Jimma on 2015-10-26
Hi Community:

I've got Ubuntu 14.04 installed with the operating system on and SSD and the /home on a separate hard drive.

I don't remember how I did this!

I'm having a problem with Ubuntu giving the message "The volume boot has only 0 bytes disk space remaining error."

I used > sudo apte-get autoremove to free up space on the SSD, but it does not seem to work. I just keep getting the same message.

So I want to reinstall Ubuntu with the operating system on an SSD and the /home on a separate hard drive.

Can anybody sketch exactly how I do that? 

Thanks,
Old Jimma

---

### Post by howefield on 2015-10-26
Firstly, is the command you have above a typo, or did you really use apt**e**-get ?

---

### Post by dragonfly41 on 2015-10-26
This is a snippet I picked up from forum .. I don't have the source of quote below ..

sudo apt-get autoremove && sudo apt-get autoclean
> 
The first part uninstalls unused leftover dependencies from software you've previously 
uninstalled and the second part removes leftover installation packages for that software.

[p.s.]

By coincidence I'm about to start cloning my local /home to another partition.  I would just like to have confirmed
that the root folder in the target /home partition is actually named "home" - i.e. a single directory into which contents of /home is cloned.

I've read about /etc/fstab and mounting.

---

### Post by yancek on 2015-10-26
You can select which partition on which to put /home if you use the Something Else option.  If you do not have a separate partition with a Linux filesystem on it, create it using GParted which is on the install medium before beginning the install.

Is boot currently a separate partitiion?
Is it full?  Run df -h to check.

---

### Post by coldraven on 2015-10-26
AFAIK there will be a folder on your root drive (not your /home drive) called /boot. It tends to get full of old kernels when updates appear. Do a search for "Remove old kernels". I think someone wrote a script that will do this for you. You could use Synaptic but **be very careful** not to remove the current kernel or your machine will not boot any more!
Use uname to find your current kernel, like in this example on my laptop. As you see my kernel version is 4.2.0-16-generic
```
uname -r
4.2.0-16-generic
```

---

### Post by Old Jimma on 2015-10-26
Hi All:

thanks for your reply on the Forums.

I investigated Yanek's comment to do a df -h

I suspect it is full the output list listed below.

I am very grateful all of your comments!

What should I do? This problem persists regardless of autoremove and autoclearn.

Thanks.
Old Jimma

> 
/dev/sda6                  44G   41G  449M  99% /
none                       4.0K     0  4.0K   0% /sys/fs/cgroup
udev                       4.0G   12K  4.0G   1% /dev
tmpfs                      810M  1.6M  808M   1% /run
none                       5.0M     0  5.0M   0% /run/lock
none                       4.0G   88K  4.0G   1% /run/shm
none                       100M   60K  100M   1% /run/user
/dev/sdc5                  917G  432G  439G  50% /home
/dev/sdb1                  917G  432G  439G  50% /mnt/WISDOM
/dev/sda1                  361M   37M  302M  11% /boot
192.168.1.79:/nfs/Public   2.7T  432G  2.3T  17% /mntWD/Public


---

### Post by Old Jimma on 2015-10-26
Output to uname -r is

3.13.0-66-generic

Old Jimma

---

### Post by dragonfly41 on 2015-10-26
Just to clarify ...

Although you have separate /home .. here .. /dev/sdc5                  917G  432G  439G  50% /home

is it possible that you still have original /home directory (or perhaps /home_old) in here .. /dev/sda6                  44G   41G  449M  99%

i.e. you have duplicate /home locations?

---

### Post by yancek on 2015-10-26
Your problem is not the /boot partition which is on sda1 and only 11% used, it is your root filesystem partition which is 99% full and that is why it won't boot.  Your home partition is much larger and only 50% full.  41GB seems like an awful lot for a root partition but what you need to do is to boot from a Live CD/flash drive, mount the root partition (sda6) and copy some data from it to either your home partition or external media.

---

