---
title: "How to make /usr mount with / ?"
date: 2007-09-06
forum: General Help
---

### Post by swistakers on 2007-09-06
I have recently moved my /usr. I simply copied the files to another partition, added an appropriate line in /etc/fstab and removed old /usr. After that I experienced a problem with hardware clock. It was set improperly after each reboot. I figured out that hwclock.sh script is run before mounting /usr. I changed name of the symlink from /etc/rcS.d/S11hwclock.sh to /etc/rcS.d/S38hwclock.sh so that hwclock is run after mounting /usr and it fixed the problem. It seems that hwclock needs some files from /usr to work properly.

After further investigation I found out that readahead may also try to access files from /usr before it is mounted. All these files are listed in /etc/readahead/boot.
In this case it doesn't make sense to move readahead after mountall, because it's meant to load files before using them, and thus to speed up the boot.

Is there any way I can force /usr to be mounted at the very beginning of the boot process? My system works well now, but I'd like to make sure that all scripts can access files they want to.

---

### Post by 505 on 2007-09-06
To answer your original question, I don't know. What I do know is it was a bad idea to just copy the files. I can image moving /usr is the same as moving /home, and just copying is not good enough. See this page for details: [http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

What I would do*: copy (normal cp) /usr back to the original partition, reboot to see if everything works and follow the instruction on the page linked to. Only substituting /home with /usr

*: I'm not that much of a Linux expert, certainly not when it comes to these advanced tasks. I moved /home once to a separate partition, did research before doing the move and everything worked. The above solution sound to me as reasonable, but it might not work. Haven't tested it, and don't intent to.

---

### Post by bettlebrox on 2007-09-06
Post your /etc/fstab

---

### Post by swistakers on 2007-09-06
Here's my /etc/fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=d91add01-abc1-420a-b782-c1a9d0ab7f3b /               reiserfs notail          0       1
#/dev/sda8
UUID=7d18ed07-c84f-4b1f-8323-be31a806dff2 /usr          reiserfs notail         0       1
# /dev/sda1
UUID=944C58844C5862D2 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=79706b63-98c0-4356-a0f5-01b9817856cc /media/sda5     ext3    defaults,noatime        0       2
# /dev/sda6
UUID=4a22f67c-e747-4ba6-b9a1-894c591c674b /media/sda6     ext3    defaults,noatime        0       2
# /dev/sda8
#UUID=7d18ed07-c84f-4b1f-8323-be31a806dff2 /media/sda8     reiserfs defaults        0       2
# /dev/sda9
UUID=ef817c2f-71df-44d0-b595-38ebdbd03c40 /media/sda9     ext3    defaults,noatime        0       2
# /dev/sda10
UUID=1550926f-7e57-4a6a-8703-cd6f8f553acc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

```

I'd be interested in finding out, if there can be any hardlinks in /usr.
If there aren't any hardlinks copying should be just fine.

UPDATE:

I created a file, a hardlink to it and copied it to another partition using mc (as I did copying /usr).
Both file and hardlink were copied and they still had the same inode number. I wouldn't bother about that.

---

### Post by swistakers on 2007-09-10
bump

---

### Post by vanadium on 2007-09-10
What good reason do you have to move /usr, especially since it is residing on the same drive anyway?

---

### Post by swistakers on 2007-09-10
Because there's too little space on system partition.

---

### Post by swistakers on 2007-09-13
The workaround I posted earlier works fine until you do an update (what happens quite often if you use gutsy during its development) and some post-installation scripts revert the contents of /etc/rcS.d. I did some research and found a better solution. Maybe it can help someone, so I post it.

Firstly, using strace I found out that hwclock accesses files from /usr/lib/locale and /usr/lib/gconv. I copied them to usr directory on my / partition. This directory is normally empty just like all /media/sda* directories and is only used as a place where the partition with actual /usr contents is mounted. The files I copied are available even though /usr is not mounted when hwclock starts. Unfortunately that didn't help.
Then I found:
[https://bugs.launchpad.net/ubuntu/+source/dhcp3/+bug/33968](https://bugs.launchpad.net/ubuntu/+source/dhcp3/+bug/33968)

As someone mentioned hwclock reads /etc/localtime which is a symlink to a file from /usr/share/zoneinfo
So I copied /usr/share/zoneinfo to usr on the system partition
Now hwclock sets the time correctly and does it before /usr is mounted.

It still looks like a workaround, but it won't be broken after system update.

---

### Post by GnuSense on 2007-11-30
swistakers, could you post your exact command?  I'm a little slow on the uptake.  I'm not sure I'll have this issue since I use Debian, but it seems like a good bet.

Do you unmount your /usr partition first so you can copy that to the /usr directory?  What exactly happens to that stuff when you mount the /usr partition over the top of data in the "/" partition /usr?  I guess it doesn't snuff it, but I don't see how you'd access it.  

Also, do you still need to copy /usr/lib/locale & /usr/lib/gconv to the /usr on / or is /usr/share/zoneinfo enough?

---

