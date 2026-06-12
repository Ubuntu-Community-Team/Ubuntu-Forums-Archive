---
title: "Mounting a Partition"
date: 2007-07-24
forum: General Help
---

### Post by kshane on 2007-07-24
I have a second Linux partition to store my media files.  This partition has to be manually mounted every time I boot up my system.  How do I get it to mount with my other partitions?  I have posted my fstab below...

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=5a194828-b5a4-4979-a99f-272da9db1a6f /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=0808BFC708BFB1D4 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda3
UUID=977617a0-7b33-450e-b508-28ee05f8039b none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
#Added by diskmounter utility
/dev/sda1 /media/sda1 ntfs ro,user,fmask=0133,dmask=0022,uid=1000,gid=1000 0 0
/dev/hda5 /disk ext3 defaults 0 0

hda5 is my media partition

Can some please help??

Kevin

---

### Post by kshane on 2007-07-24
Any one?  Please....

---

### Post by ajgreeny on 2007-07-24
Normally you would need to add the following line to your fstab file, after making the folder /media/hda5 first.:-
/dev/hda5      /media/hda5  ext3    defaults  0  1
instead of
/dev/hda5 /disk ext3 defaults 0 0
Are you sure you have the mount point /disk already made and available in your system?  If not make it now and try again.

However, I wonder if you need to add the UUID instead of just the hda5 for the partition name.  Perhaps you need to look at the output of sudo fdisk -l and add the UUID to the line instead.  I've found this UUID system much more of a problem since it started being used instead of the hdXX system, and if you ever reinstall, the UUID can change, making another thing to edit in your fstab.  No doubt there are advantages to it as well, but personally I wish it was back where it used to be.

---

### Post by kshane on 2007-07-24
Thanks ...   I'm giving it a try now..

Kevin

---

### Post by kshane on 2007-07-27
I still have to manually mount each time I boot the system.

How do you include the new partition at boot up?

---

### Post by nutz on 2007-07-27
I would be interested to know this also.

---

### Post by Fallen_62 on 2007-07-27
try changing the line from ```
/dev/hda5 /disk ext3 defaults 0 0
```

to this

```
/dev/hda5 /mountpount ext3 uid=1000,gid=1000,rw,users,auto 0 0
```

Making sure you change the /mountpoint to the folder you are mounting it to.  Any questions on what the options are, just ask.  I used this on my external HD (I wanted to mount it with different options) and it works fine and mounts on system load.

edit:  This is also assuming that you are the user with the user id of 1000 (and in the group with group id of 1000).  If not, change it to your UID and GID.

---

### Post by kshane on 2007-07-28
> **Fallen_62 said:**
> try changing the line from ```
/dev/hda5 /disk ext3 defaults 0 0
```

to this

```
/dev/hda5 /mountpount ext3 uid=1000,gid=1000,rw,users,auto 0 0
```

Making sure you change the /mountpoint to the folder you are mounting it to.  Any questions on what the options are, just ask.  I used this on my external HD (I wanted to mount it with different options) and it works fine and mounts on system load.

edit:  This is also assuming that you are the user with the user id of 1000 (and in the group with group id of 1000).  If not, change it to your UID and GID.

Okay!  Got it...  No difference...  (I am user 1000, etc...)

I still have to manually mount the drive on boot up...

Any more ideas?

Kevin

---

### Post by Fallen_62 on 2007-07-29
The only thing that I can think of is that the hda5 is too high of a number.  HD's can only have 4 primary partitions, so an hda5 seems a bit odd...  Try changing it to hda4 possibly...?  Let me know if it works...  It's about the only thing i can think of.  If it works to mount manually on hda5, hda4 may not make a difference...  But I dont see one in your fstab file (unless im blind...), so it's worth a shot.

---

### Post by rillip on 2007-07-29
I honestly don't know what to do from the command line, but in Kubuntu, if you go to system settings -> disk and file systems -> administrator, right click on the disk, choose modify, and click the check box "enable at start up."

Seems like Gnome should have some way of doing that as well...

---

### Post by merlinus on 2007-07-29
What is the output of these commands:

```

sudo fdisk -l

```

(l is a lowercase L)

```

mount

```

-merlin

---

### Post by kshane on 2007-07-30
> **rillip said:**
> I honestly don't know what to do from the command line, but in Kubuntu, if you go to system settings -> disk and file systems -> administrator, right click on the disk, choose modify, and click the check box "enable at start up."

Seems like Gnome should have some way of doing that as well...

I have since cleaned up my fstab.  It appears below:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=5a194828-b5a4-4979-a99f-272da9db1a6f /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=0808BFC708BFB1D4 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda3
UUID=977617a0-7b33-450e-b508-28ee05f8039b none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
#Added by diskmounter utility
/dev/sda1 /media/sda1 ntfs ro,user,fmask=0133,dmask=0022,uid=1000,gid=1000 0 0
#/dev/hda4 /media/disk ext3 uid=1000,gid=1000,rw,users,auto 0 0


```

As you can see, I have since commented out the line for my "media" partition.  It is hda4 (I removed a small partition not being used which put the partiton in question back as hda4).

Under the current settings, I can right click to mount the partition from the Nautilus File Browser.  This seems like such a silly problem, but I have tried almost everything to get this partition to automatically mount on boot up.

AMD Sempron (1.6gHz)
SiS Chipset
768 MB RAM
ATI-X1650

Any ideas?

Kevin

---

### Post by flar on 2007-07-30
I seem to be having the same problem.  Very annoying because I've done this many many times before.  I've never had trouble like this with fstab in the past.  This should be easy.

I noticed that when the system boots, it complains "mount point doesn't exist" (this can be seen by pressing ctrl-alt-F8 during the boot process).

But the mount point does exist and fstab is correct.

---

### Post by flar on 2007-07-30
As usual, I figured out my problem right after I posted :)

I was mounting the partitions in the wrong order.  A simple fix by moving the partition's line in fstab down to the bottom.

That doesn't seem to be the problem for the original poster, sorry kshane.  Though you might try mounting your partition in your home directory, perhaps /home/kshane's user/media

---

### Post by kshane on 2007-07-30
> **merlinus said:**
> What is the output of these commands:

```

sudo fdisk -l

```

(l is a lowercase L)

```

mount

```

-merlin

sudo fdisk -l :
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4717    37889271    7  HPFS/NTFS
/dev/sda2            5738        9561    30716280   83  Linux
/dev/sda3            5100        5737     5124735   82  Linux swap / Solaris
/dev/sda4            9562       19457    79489620   83  Linux

Partition table entries are not in disk order

```

mount
```

/dev/sda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
/dev/sda1 on /media/hda1 type ntfs (rw,nls=utf8,umask=007,gid=46)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sda4 on /media/disk type ext3 (rw,noexec,nosuid,nodev)

```

Thanks for the help...

Kevin

---

### Post by merlinus on 2007-07-30
Just to be clear, what is the partition you are wishing to mount automatically, and what is the mountpoint you have created for it?

-merlin

---

### Post by kshane on 2007-07-30
I found some errors in my previous setup.  Sooo...  I redid things.  The partition is hda4.  It should mount from /storage.

Here's fstab now. It manually mounts from Nautilus.

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=5a194828-b5a4-4979-a99f-272da9db1a6f /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=0808BFC708BFB1D4 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda3
UUID=977617a0-7b33-450e-b508-28ee05f8039b none            swap    sw              0       0
# /dev/hda4
/dev/hda4 /storage ext3 defaults 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```


When I enter mount -a 

```

kevin@home:~$ sudo mount -a
mount: special device /dev/hda4 does not exist

```

Hope this helps..

Kevin

---

### Post by merlinus on 2007-07-30
You might try mounting it at /media/storage.  That is what I do with one of my ext3 partitions.

Make the mountpoint manually, change /etc/fstab, restart, and see what happens.

Also, after mounting it manually, you might post results of:

```

sudo fdisk -l

```

-merlin

---

### Post by kshane on 2007-07-30
> **merlinus said:**
> You might try mounting it at /media/storage.  That is what I do with one of my ext3 partitions.

Make the mountpoint manually, change /etc/fstab, restart, and see what happens.

Also, after mounting it manually, you might post results of:

```

sudo fdisk -l

```

-merlin

No change.  But it does mount manually, at least.  

Here ya go:
```

kevin@home:~$ sudo fdisk -l
Password:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4717    37889271    7  HPFS/NTFS
/dev/sda2            5738        9561    30716280   83  Linux
/dev/sda3            5100        5737     5124735   82  Linux swap / Solaris
/dev/sda4            9562       19457    79489620   83  Linux

Partition table entries are not in disk order

```

Thanks for the time and help...  Got any other ideas?  :biggrin:

Kevin

---

### Post by merlinus on 2007-07-30
From what I can see, /dev/hda4 is listed as /dev/sda4 in sudo fdisk -l, no?  

Perhaps this is the problem???

If so, it should be mounted at /media/sda4.

And if you change this in /etc/fstab and restart, what happens?

-merlin

---

### Post by kshane on 2007-07-30
:KS

:popcorn:

Thank you very much, Merlinus!  It works....

And I learned more in the process....

Thanks very much!

Kevin

---

### Post by merlinus on 2007-07-30
Good news!  Glad I could help...

All the best...

-merlin

---

