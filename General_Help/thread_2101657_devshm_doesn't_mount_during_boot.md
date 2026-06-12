---
title: "dev/shm doesn't mount during boot"
date: 2013-01-05
forum: General Help
---

### Post by beerbunny on 2013-01-05
Since installing yesterday's (4th Jan 2013) updates, I've been getting an error message during the boot process telling me that dev/shm could not be mounted and to press S to skip or M to manually fix (or something similar). I've tried both options without success.

I've Googled the problem, and searched the forum, but didn't find anything helpful (i.e. a moron's step-by-step guide to fixing this problem :)), so here I am asking for assistance.

Can anybody help, please?

Thanks,

John

---

### Post by rnerwein on 2013-01-05
> **beerbunny said:**
> Since installing yesterday's (4th Jan 2013) updates, I've been getting an error message during the boot process telling me that dev/shm could not be mounted and to press S to skip or M to manually fix (or something similar). I've tried both options without success.

I've Googled the problem, and searched the forum, but didn't find anything helpful (i.e. a moron's step-by-step guide to fixing this problem :)), so here I am asking for assistance.

Can anybody help, please?

Thanks,

John
hi 
have the contents of the files: in /proc/sys/kernel (use cat to see the contents)
 shmall  shmmax  shmmni  shm_rmid_forced
should be (but must not be the same)
2097152 - 33554432 - 4096 - 0

another file to have a look at is: /proc/sysvipc/shm

sorry - no more ideas.
ups - i just see that on my second box (10.04 lucid) is shm mounted on [COLOR=Red]/dev/shm[/COLOR] and on the box i am sitting (12.04 precise) it' mounted on[COLOR=Red] /run/shm[/COLOR]. that's may be a problem with the update !?
cheers

---

### Post by beerbunny on 2013-01-05
Hi, and thanks for the response.

I've had a look at all the files you mentioned, and they're all empty files (0 bytes). Is that right?

You mentioned seeing that in 10.04, shm is mounted on /dev/shm and on 12.04, it's mounted on /run/shm. I'm running 12.04 , but the error message said /dev/shm. Odd. Can you tell me where you looked to find this info, please?

In my opinion, yes, the problem was caused by the update and I'm hoping for a correction in the near future, but in the meantime, I thought I'd have a look and see if I could find a way to fix it. I don't know much about Linux (or any other OS), but I'm happy to get my hands dirty if I can find the relevant information.

Cheers,

John

---

### Post by ajgreeny on 2013-01-05
All files in /proc appear empty if you use nautilus or other file manager, but if you use ```
cat /proc/path/to/file
``` you may find there is content there.

This is because everything in /proc is a virtual file, not a real one.  Try it and you'll see what I mean.

---

### Post by rnerwein on 2013-01-05
> **beerbunny said:**
> Hi, and thanks for the response.

I've had a look at all the files you mentioned, and they're all empty files (0 bytes). Is that right?

You mentioned seeing that in 10.04, shm is mounted on /dev/shm and on 12.04, it's mounted on /run/shm. I'm running 12.04 , but the error message said /dev/shm. Odd. Can you tell me where you looked to find this info, please?

In my opinion, yes, the problem was caused by the update and I'm hoping for a correction in the near future, but in the meantime, I thought I'd have a look and see if I could find a way to fix it. I don't know much about Linux (or any other OS), but I'm happy to get my hands dirty if I can find the relevant information.

Cheers,

John
hi
no zero is not ok - the sizes are a default. but you ain't have /run/shm. have a look if your /run exists and isn't empty (i think there is no mountpoint /run/shm :-((  )
shm i of tpye tmpfs and it is not persistent (contence is lost by reboot. but on boot it
must be created by the system.
have a look at /etc/sysctl.conf if there is some nonsens about shm in it - it's the configuration file for the sysctl command to set tuning parameter at startup)

i used the mount command in a terminal just type: mount ( i did this on my two boxes 
(10.04 and 12.04)
just have another look at /run and see that lightdm and pulse is using "shm". that means
if you are running lightdm that sould be an entry for shm in /run
cheers

---

### Post by beerbunny on 2013-01-05
> **rnerwein said:**
> hi
no zero is not ok - the sizes are a default. but you ain't have /run/shm. have a look if your /run exists and isn't empty (i think there is no mountpoint /run/shm :-((  )
shm i of tpye tmpfs and it is not persistent (contence is lost by reboot. but on boot it
must be created by the system.
have a look at /etc/sysctl.conf if there is some nonsens about shm in it - it's the configuration file for the sysctl command to set tuning parameter at startup)

i used the mount command in a terminal just type: mount ( i did this on my two boxes 
(10.04 and 12.04)
just have another look at /run and see that lightdm and pulse is using "shm". that means
if you are running lightdm that sould be an entry for shm in /run
cheers

I tried again with cat and got the same results as you; - 2097152 - 33554432 - 4096 - 0.

/run/shm/ exists and has 4 pulse-shm files in it, each with a different 10 digit number in the name.

No mention of shm in /etc/sysctl.conf.

I also ran mount in the terminal and this is what I got;-

john@john-GA-870A-USB3L:~$ mount
/dev/sda4 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda3 on /home type ext4 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sdb1 on /media/TOSHIBA EXT type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda1 on /media/D0E830B5E8309BA2 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
gvfs-fuse-daemon on /home/john/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=john)

No mention of shm that I could find. Not surprising, really, as it couldn't be mounted.

Thanks for your help so far.

Thanks also to  ajgreeny; I didn't understand how to use cat before, but I've got it now.

Cheers,

John

---

### Post by rnerwein on 2013-01-06
> **beerbunny said:**
> I tried again with cat and got the same results as you; - 2097152 - 33554432 - 4096 - 0.

/run/shm/ exists and has 4 pulse-shm files in it, each with a different 10 digit number in the name.

No mention of shm in /etc/sysctl.conf.

I also ran mount in the terminal and this is what I got;-

john@john-GA-870A-USB3L:~$ mount
/dev/sda4 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda3 on /home type ext4 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sdb1 on /media/TOSHIBA EXT type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda1 on /media/D0E830B5E8309BA2 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
gvfs-fuse-daemon on /home/john/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=john)

No mention of shm that I could find. Not surprising, really, as it couldn't be mounted.

Thanks for your help so far.

Thanks also to  ajgreeny; I didn't understand how to use cat before, but I've got it now.

Cheers,

John
hi
your system take a mick out of you. shm is mounted 
 none on /run/shm type tmpfs (rw,nosuid,nodev)
and is ok. pulse is using it.
the only difference is i have no binfmt_misc ( i now what it is - i think you are running msdoz in a VM ?)
Result: everything seems ok - except the suspect error message.
cheers

---

### Post by beerbunny on 2013-01-07
> **rnerwein said:**
> hi
your system take a mick out of you. shm is mounted 
 none on /run/shm type tmpfs (rw,nosuid,nodev)
and is ok. pulse is using it.
the only difference is i have no binfmt_misc ( i now what it is - i think you are running msdoz in a VM ?)
Result: everything seems ok - except the suspect error message.
cheers

I think you're right; my system is indeed taking the mick. I did some more googling on the subject, and I was able to determine that shm is mounted, along with tmpfs (?).

So I'm going to just live with the problem for now; everything seems to be running okay. Except, as you say, for that d****d error message. I'm still hoping that a fix will be issued soon, but if not, I'll have to live with it; I don't know enough to fix it myself.

No, I'm not running msdos in VM. I haven't got anything like that installed. When I need Windows to run an app that I can't get to work in Wine, I reboot into Windows 7.

Thanks again for your help.

Cheers,

John

---

