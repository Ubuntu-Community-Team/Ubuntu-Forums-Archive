---
title: "Moving /home to new partition"
date: 2007-05-01
forum: General Help
---

### Post by merlinus on 2007-05-01
I have been trying to move /home to a new partition, sda 7.

I tried following various  directions, but in the midst of the process, having moved /home to /home_backup, I inadvertently closed the terminal window, and then nothing worked.

So I booted from the Live CD, where I am now.

I have a backup of my old /home as /home_backup, but cannot do anything with it.

I have mounted the various partitions using the file manager, but terminal commands such as

sudo mount -t ext3 /dev/sda8/

do not work.

The mounts I can see on the desktop are disk, which is the filesystem and contains a directory /home which is empty, and a directory home_backup, which contains a subdirectory merlin, and disk-1, where is where I attempted to move /home. disk-1 contains a directory merlin, which used to be a subdirectory of /home.

/etc/fstab also seems totally trashed.

But since I have a full copy of my original /home directory, it would seem that not much is needed to copy it over to the new partition, sda7, fix fstab, and boot to it.

sda8 is my root partition,

System/Administration/System Monitor/File Systems lists the following:

device directory

/dev/sda8 /media/disk

/dev/sda7 /media/disk-1

Help is greatly appreciated!  

Many thanks....

-merlin

---

### Post by Gaunty on 2007-05-01
Wouldn't it be nice if you could simply click on your home folder, point to a new location and let the operating system do the rest.  Windowz might be a pile of crap but some things it does well.

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

I've never tried to move home but this how-to looks like it could help you.

Kind regards.

---

### Post by mac.ryan on 2007-05-01
I am a bit confused by your original post (I haven't understood what you need help on, exactly).

When I moved my /home from one partition to another, I simply followed the following procedure:
[LIST=1]
[*]booted from liveCD.
[*]mounted the box HD's (I am not sure, but your attempt to mount it from CLI could have failed because you omitted the target directory)
[*]copied the entire content of <old home partition> to <new home partition>
[*]edited the /etc/fstab **of the installed version** of ubuntu in order to mount the new partition into /home
[*]rebooted normally[/LIST]Anywhere you got stuck in your procedure, the above one will still work, provided you have an intact version of your /home directory as it was before the crash.

I hope this helps... (?)

---

### Post by mac.ryan on 2007-05-01
> **Gaunty said:**
> Wouldn't it be nice if you could simply click on your home folder, point to a new location and let the operating system do the rest.  Windowz might be a pile of crap but some things it does well.

Of course you could do (nearly) that in ubuntu as well. But in order not to create problems with session files, you should first activate the root account, log off as a normal user and re-log-in as an administrator. In windows you are by default the administrator, this is why there is a passage less. (this is why root's files are in /root and not /home, btw...)

---

### Post by merlinus on 2007-05-01
> **mac.ryan said:**
> I am a bit confused by your original post (I haven't understood what you need help on, exactly).

When I moved my /home from one partition to another, I simply followed the following procedure:
[LIST=1]
[*]booted from liveCD.
[*]mounted the box HD's (I am not sure, but your attempt to mount it from CLI could have failed because you omitted the target directory)
[*]copied the entire content of <old home partition> to <new home partition>
[*]edited the /etc/fstab **of the installed version** of ubuntu in order to mount the new partition into /home
[*]rebooted normally[/LIST]Anywhere you got stuck in your procedure, the above one will still work, provided you have an intact version of your /home directory as it was before the crash.

I hope this helps... (?)

Is there a way to run the cd live file manager as root?  This would make things much, much easier, for me, as the CLI drives me nuts.

Thanks....

-merlin

---

### Post by stchman on 2007-05-01
> **merlinus said:**
> I have been trying to move /home to a new partition, sda 7.

I tried following various  directions, but in the midst of the process, having moved /home to /home_backup, I inadvertently closed the terminal window, and then nothing worked.

So I booted from the Live CD, where I am now.

I have a backup of my old /home as /home_backup, but cannot do anything with it.

I have mounted the various partitions using the file manager, but terminal commands such as

sudo mount -t ext3 /dev/sda8/

do not work.

The mounts I can see on the desktop are disk, which is the filesystem and contains a directory /home which is empty, and a directory home_backup, which contains a subdirectory merlin, and disk-1, where is where I attempted to move /home. disk-1 contains a directory merlin, which used to be a subdirectory of /home.

/etc/fstab also seems totally trashed.

But since I have a full copy of my original /home directory, it would seem that not much is needed to copy it over to the new partition, sda7, fix fstab, and boot to it.

sda8 is my root partition,

System/Administration/System Monitor/File Systems lists the following:

device directory

/dev/sda8 /media/disk

/dev/sda7 /media/disk-1

Help is greatly appreciated!  

Many thanks....

-merlin

I personally don't use the /home/<my_home> at all.  When files are created there I move them to my storage partition.  I created a new partition on my hard drive and mounted it in the /media/storage folder.

If I ever have to reinstall Ubuntu I just make /dev/sda1 free space using Gparted.  That way during installation you can tell Ubuntu to install on the largest free space.

The purpose of using the /media folder gives me a desktop icon for that partition.  I then changed the ownership with sudo chown and that was it.  I keep everything on that partition.  It works very well.  I have a procedure to do partition access on my website:

[http://www.stchman.com/part.html](http://www.stchman.com/part.html)

I hope it helps you.

---

### Post by lukew on 2007-05-01
> **merlinus said:**
> Is there a way to run the cd live file manager as root?  This would make things much, much easier, for me, as the CLI drives me nuts.

Thanks....

-merlin

Recovery logs you in as root.

---

### Post by psusi on 2007-05-01
Do this:

sudo -s
cp -a /media/disk/home_backup/* /media/disk-1/
nano /media/disk/etc/fstab

You said before that your fstab was hosed, but I am assuming this is because you were actually looking at the livecd fstab, not the one on your hard disk.  Now you should be editing your fstab and you need to add a line for /home.  It should read something like:

/dev/sda7 /home ext3 defaults 0 0

Save then type exit to return to your non root shell.  You should be able to reboot normally now and your new /home should  be in place, and you will still have /home_backup as well, which you can delete once you are satisfied that everything is ok.

---

### Post by merlinus on 2007-05-01
I followed your instructions.  Now on disk-1 I have a home directory with a ubuntu subdirectory, and a merlin directory that has all the original files, etc.

But shouldn't merlin be a subdirectory of home?

Here is the output of /etc/fstab

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config --
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda7 :
UUID=74ea0d79-f0a5-4381-a98d-08258758e696 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda1 :
UUID=143857E33857C302 /media/sda1 ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/sda5 :
UUID=18082DAD082D8B38 /media/sda5 ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/sda6 :
UUID=D444F4A544F48B8C /media/sda6 ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/sda8 :
UUID=8d0e34ce-515e-4595-b8d3-f04930ca0baa none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/scd1 /media/cdrom udf,iso9660 user,noauto 0 0

Thanks hugely!

-merlin

---

### Post by psusi on 2007-05-01
I assume that merlin is your user name?  You should see a directory named merlin in disk-1, not home with merlin in it.  Add the line to fstab like I said and you should be set.

---

### Post by merlinus on 2007-05-01
YES!!!!!!!

Thank you, thank you, thank you!

A question --

In File Manager, I now see an icon merlin at the top.  Are the contents of this on sda7?  I assume that File System is on sda8, as it always was.

And can I then delete all of the home_backup files?

-merlin

---

### Post by psusi on 2007-05-01
Huh?  What do you mean "at the top"?  Yes, you can delete the home_backup.

---

### Post by merlinus on 2007-05-01
> **psusi said:**
> Huh?  What do you mean "at the top"?  Yes, you can delete the home_backup.

In Places/Computer is a Merlin icon at the top of the list.  But it seems clear, even to me, that this is located on sda7, as your wonderful instructions helped me to do.

Thanks again.... you bailed me out of a very untenable position.

-merlin

---

### Post by psusi on 2007-05-01
Sounds like something is not right.... what is the output of the df command?

---

### Post by merlinus on 2007-05-01
> **psusi said:**
> Sounds like something is not right.... what is the output of the df command?

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda8             16342452   3692480  11819816  24% /
varrun                  777972        96    777876   1% /var/run
varlock                 777972         0    777972   0% /var/lock
procbususb              777972       120    777852   1% /proc/bus/usb
udev                    777972       120    777852   1% /dev
devshm                  777972         0    777972   0% /dev/shm
lrm                     777972     33788    744184   5% /lib/modules/2.6.20-15-generic/volatile
/dev/disk/by-uuid/143857E33857C302
                      21414613   9485411  11929203  45% /media/sda1
/dev/disk/by-uuid/18082DAD082D8B38
                       4618656    825156   3793500  18% /media/sda5
/dev/disk/by-uuid/D444F4A544F48B8C
                       3100513    130801   2969713   5% /media/sda6
/dev/sda7             10135768   1327356   8293532  14% /home
/dev/sda7             10135768   1327356   8293532  14% /media/sda7

---

### Post by psusi on 2007-05-02
Oh my, you seem to have sda7 mounted twice, once in /home and once in /media/sda7.  You shouldn't even be able to do that.  Make sure there is only one entry for sda7 in your fstab mounting it under /home.

---

