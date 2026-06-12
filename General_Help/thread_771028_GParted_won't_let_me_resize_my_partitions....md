---
title: "GParted won't let me resize my partitions..."
date: 2008-04-27
forum: General Help
---

### Post by new_at_linux on 2008-04-27
Hello,

When I installed Ubuntu I only set up the partition to be ~9GB, and it turns out that's not enough for all of my files.  Since I used GParted when I was installing Ubuntu 7.1, I knew I could use it to resize my Windows XP partition (to be less) and my ext3 partition (to be more).  First I upgraded to version 8 since it just came out and I wanted to get that over with.

So I reboot my computer and find out that GParted is no longer installed (?) , so I reinstall it and run it.  For some reason or another, it won't let me do anything with any of my partitions except delete them, which would be bad ;).

So... can I fix GParted?  Is there a way to do this without GParted?  Is this a bug in Hardy Heron, or was GParted intentionally left out of the release because there were issues with the software?

Thank you for any help in advance.

---

### Post by kellemes on 2008-04-27
> **new_at_linux said:**
> Hello,

When I installed Ubuntu I only set up the partition to be ~9GB, and it turns out that's not enough for all of my files.  Since I used GParted when I was installing Ubuntu 7.1, I knew I could use it to resize my Windows XP partition (to be less) and my ext3 partition (to be more).  First I upgraded to version 8 since it just came out and I wanted to get that over with.

So I reboot my computer and find out that GParted is no longer installed (?) , so I reinstall it and run it.  For some reason or another, it won't let me do anything with any of my partitions except delete them, which would be bad ;).

So... can I fix GParted?  Is there a way to do this without GParted?  Is this a bug in Hardy Heron, or was GParted intentionally left out of the release because there were issues with the software?

Thank you for any help in advance.

You can't perform such actions on a mounted partition.
Use the LiveCD or something like [GParted LiveCD]("http://gparted.sourceforge.net/livecd.php").

---

### Post by p_quarles on 2008-04-27
You can't edit partitions in Gparted while those partitions are mounted. This is a safety feature. 

To do what you want, you will need to use a boot disk. You can use the Ubuntu live CD and load up Gparted from there, or you can get the Gparted live CD (easily findable either through Google or distrowatch.com), which is a slightly easier to use interface for Gparted. 

Be sure to back up anything important before editing partition tables.

---

### Post by ghost_ryder35 on 2008-04-27
DEFRAG WINDOWS BEFORE DOING THIS!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
I would hate to have another "Cant boot windows" horror story today

---

### Post by robelliott2125 on 2008-04-27
I'm sorry for asking, but does GParted convert file systems too?

I'm looking to change all my NTFS partitions to comply more with Linux, since i've recently ditched Windows fully.

If it doesn't, do you think Hiron's Boot Disk with Partition Magic, would allow me to convert and not corrupt anything?

Just looking for some pro expertise...

Thank you,

---

### Post by p_quarles on 2008-04-27
> **robelliott2125 said:**
> I'm sorry for asking, but does GParted convert file systems too?

I'm looking to change all my NTFS partitions to comply more with Linux, since i've recently ditched Windows fully.

If it doesn't, do you think Hiron's Boot Disk with Partition Magic, would allow me to convert and not corrupt anything?

Just looking for some pro expertise...

Thank you,
Changing a filesystem requires you to format the partition, which means erasing any data that may be on that partition. Gparted can certainly do that, but I am not aware of any tool that will allow you to change the type of filesystem in use without erasing the data.

---

### Post by robelliott2125 on 2008-04-27
> **p_quarles said:**
> Changing a filesystem requires you to format the partition, which means erasing any data that may be on that partition. Gparted can certainly do that, but I am not aware of any tool that will allow you to change the type of filesystem in use without erasing the data.

Without wanting to add to the many "windows" comments, you can convert a filesystem from one format to another, however as i'm new to this, it may only be windows specific, for instance you can convert from Fat / Fat32 to NTFS, as most manufacturers only load operating systems on the Fat32 file system, making Xp and Vista *cough* crap and unstable.

I can mess about with moving things about, but I need another thread replied to before I can do anything, since I'm also wanting to remove a secondary installation of gutsy and resize the partition its sat on, so I can get a 40gb drive back.

Thank you for your reply, and looking forward to your response.

---

### Post by new_at_linux on 2008-05-01
Thank you all for the responses.

I succeeded in shrinking my ntfs partition via the LiveCD.  Unfortunately, it won't let me expand my ext3 partition, despite the fact that I have 19 GB unallocated.  Am I supposed to be able to expand partitions, or do I have to delete my current ext3 partition and make a new one?

Here is a screenshot, if it helps any:

[[IMG]http://img338.imageshack.us/img338/5985/screenshotdevsdagpartedbq9.th.png[/IMG]](http://img338.imageshack.us/my.php?image=screenshotdevsdagpartedbq9.png)

---

### Post by iSplicer on 2008-05-01
You see the "key" symbol next to the partitions you want to resize? you need to unmount them before you do so. Right click on the drive icon from your desktop/places and select unmount.

Good Luck!

---

### Post by new_at_linux on 2008-05-01
How do I unmount the extended drive?

My desktop has no drives on it, and when I go to "Places", the only drives I can mount are the ntfs, the ext3, and the Floppy Drive (useless).

---

### Post by new_at_linux on 2008-05-03
Bump.

Can anyone please help?

---

### Post by p_quarles on 2008-05-03
No drives should be mounted in the first place if you are doing this correctly. To edit the partition table on your main hard drive, you need to use a live CD with GParted. Possible live CDs include Ubuntu, Puppy, Knoppix, and the GParted live CD itself.

---

### Post by new_at_linux on 2008-05-03
> **p_quarles said:**
> No drives should be mounted in the first place if you are doing this correctly. To edit the partition table on your main hard drive, you need to use a live CD with GParted. Possible live CDs include Ubuntu, Puppy, Knoppix, and the GParted live CD itself.

Thank you for the reply.

I am booting from a Live CD with GParted, but when I run it the extended drive starts out mounted, without anything showing on the desktop or under "Places".

---

### Post by p_quarles on 2008-05-03
> **new_at_linux said:**
> Thank you for the reply.

I am booting from a Live CD with GParted, but when I run it the extended drive starts out mounted, without anything showing on the desktop or under "Places".
Okay. From a terminal on the live CD, type:
```
mount
```
and then paste the output of that command here. Then, I or someone else can give you the exact command to unmount anything needed.

---

### Post by new_at_linux on 2008-05-03
> **p_quarles said:**
> Okay. From a terminal on the live CD, type:
```
mount
```
and then paste the output of that command here. Then, I or someone else can give you the exact command to unmount anything needed.

OK, here is everything from the terminal:

```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ mount
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

```

---

### Post by whitewolf1218 on 2008-05-04
> **iSplicer said:**
> You see the "key" symbol next to the partitions you want to resize? you need to unmount them before you do so. Right click on the drive icon from your desktop/places and select unmount.

Good Luck!

I have been looking for those exact words for the last half-hour. THANK YOU!

---

### Post by new_at_linux on 2008-05-05
> **whitewolf1218 said:**
> I have been looking for those exact words for the last half-hour. THANK YOU!

Nice to know starting this thread helped somebody ^^.

---

### Post by new_at_linux on 2008-05-08
This is my last bump.  If no one knows how to unmount the extended drive, I'll simply delete it, create a new one and reinstall Ubuntu. :)

---

### Post by forestpixie on 2008-05-08
Has the extended got swap in it - if it has the livecd will use it I think, check with ```
top
``` - looks like that is so from the image you posted. If that is the case open a terminal and 

```
sudo swapoff
```

Then the whole of the extended should be unmounted and you can do as you will.

---

### Post by jmore9 on 2008-05-08
I pretty much boot from a gparted 3.4.2 cdrom.  It handles resizing of NTFS and linuux partions without destroying the data on them.  I laos use it for windows stuff also.  Works fine lasts a long time.   It is very easy to use.

---

### Post by adonet on 2008-05-08
To resize any partition that is mounted in anyway you only can use a live CD with Gparted on it.
To change the filesystem of a partition you can use Hirons BootCD with Powerquest Partition Magic on it. PQmagic can convert NTFS to FAT 32 without removing its contents.I dont have any experience with it, so try it at your own risk and let us know. I dont know if PQmagic can convert NTFS to Ext3 filesystem. If it can it's great, but I really don't know. If you try, it 'll probably tell you if it's possible to do so.

Dont use Hirons Boot cd PQ magic with any partiton that's used with Windows Vista. Its NOT compatible and won't be made compatible to.

Gparted newest version should be copmpatible, but my experiences are negative. I had te re-install Vista. (though I never use it).

Jeroen

---

### Post by mettle79 on 2008-08-24
> **new_at_linux said:**
> OK, here is everything from the terminal:

```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ mount
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

```

So what's next? Very interesting thread with an abrupt end... 
I have the same problem: The extended drive and the linux-swap within it have the "Key" symbol... how did you finally umount and finish the next few steps? :confused:

---

