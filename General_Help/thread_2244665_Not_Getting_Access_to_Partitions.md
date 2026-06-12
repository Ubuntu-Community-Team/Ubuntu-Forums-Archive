---
title: "Not Getting Access to Partitions"
date: 2014-09-17
forum: General Help
---

### Post by llanitedave on 2014-09-17
I've got an Acer Aspire V3 laptop running 14.04 with two hard drives -- one I rescued from a previous laptop that went kaput.  I have multiple partitions on each drive, some formatted to NTFS, with the idea of consolidating all my old documents onto a single partition.  Everything was accessible for a while.  However, I recently attempted to insert a USB stick, and I was denied access to it with the message "Could not enter folder /media/root/dave_usb".  I then tried to access my hard drive partitions and got the same message.  Only my own home directory was accessible.  I use Dolphin as my main file manager, but both Dolphin and the default file manager gave me the same problem, and when I tried cd on the terminal, I was rewarded with "permission denied."

If I go to 'sudo dolphin', then everything opens as it should.  I checked ownership and permissions, and they were all root:root, and drwxrwxrwx.  I did  'sudo chown -R dave:dave /media/dave' where all the partitions were located, but ownership only changed on two small partitions, others were left untouched on both hard drives.

An interesting message I got when opening dolphin via sudo was a group of errors of the format "Error: '/tmp/kde-dave" is owned by uid 1000 instead of uid 0'.  The fact that I'm user id 1000 led me to think that uid 0 may have been the owner on the previous computer, where my name was also 'dave'.  I thought that might create a mismatch, so I used 'sudo chown -R 1000:1000 /media/dave'.  Unfortunately, that didn't change any of my ownerships.

I don't know what to try next.  I really don't want to have to sudo every time I need to get into my own files.

---

### Post by TheFu on 2014-09-18
Using sudo like you are doing is extremely dangerous.  Running any GUI tool as root can lead to unwanted repercussions. Mainly files that should never be owned by root, being owned by root.

[https://superuser.com/questions/320415/linux-mount-device-with-specific-user-rights](https://superuser.com/questions/320415/linux-mount-device-with-specific-user-rights) has the best solution I know.

Really, these sorts of issues will keep happening until a better understanding of userids, groupids, and permissions is gained. Running sudo should'nt be needed on a properly configured system.  I used to suggest [a tutorial ]("https://help.ubuntu.com/community/FilePermissions")on file permissions, but everyone seemed to get lost - because they didn't have the necessary background for understanding.

[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) seems to be the best, free, solution I can find to gain that background, short of personal training.  Sadly, it doesn't cover the specific mount problem you are experiencing in the book.

**If you are using sudo all the time, something is broken.** For many, many, years only root was allowed to mount any storage - this is a security consideration.  My systems are still configured in that manner, but I have allowed a few specific flash drives to be mounted by specific users automatically on access (not on insertion).  It is only relatively recent (8-10 yrs?) that USB devices have been automatically connected.  It appears to me that something changed with 14.xx to break the prior default behavior of non-Linux automatic mounts under /media/. This is unfortunate, I suppose.

---

### Post by llanitedave on 2014-09-19
Something is definitely broken.  Your link reminded me of /etc/fstab, and that led me to [http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

So, I configured the line that holds the ntfs partition on my main drive as below:

UUID=7E4294CE42948C91	/media/dave/DATA	ntfs-3g	defaults,auto,uid=1000,gid=1000,umask=000,locale=en_US.UTF-8	0	0

I rebooted, but I STILL can't get the partition to mount unless I use 'sudo dolphin'.  I rebooted, and used sudo mount -a, and that had no effect.  Basically, nothing has changed.

---

### Post by TheFu on 2014-09-20
Perhaps removing the "defaults" part will help?  

I'm not a fan of the umask either, but for testing .... fine.

Also ... there appears to be an extra space in the locale - spaces in the options are NOT allowed. 

I'm afraid to use a mount point under /media - that is managed by some other processes and experience has taught me that mixing manual control with "something Ubuntu does automatically" is a bad idea. Perhaps that is just me.  Does the mount point actually exist?

Have you tried NOT using the UUID, just using the actual device? It shouldn't matter, but .... we are troubleshooting here.

Using dolphin to access the storage uses the gvfs. Using mount uses ... er ... mount. Different subsystems, at least in my mind. I am not a fan of gvfs - it has caused me problems over the years.

BTW - using **sudo mount -a** to get storage mounted from the fstab **is** a good use of sudo. ;)

Assuming the UUID is correct, I'd use this:
```
$ sudo mkdir /mnt/TEST
```

The for the fstab:
```
UUID=7E4294CE42948C91 /mnt/TEST ntfs-3g rw,uid=1000,gid=1000,locale=en_US.UTF-8 0 2
```

and don't forget to **umount  /mnt/TEST** between tests.  BTW, the manpage for mount.ntfs says using the locale can lead to unwanted results.

---

### Post by llanitedave on 2014-09-20
OK, real progress now.  Thanks!  The space you saw in my pasted fstab line was just an artifact, it wasn't in the actual file.  But I got rid of my locale flags anyway and tested.  Made no difference.  I then did the following:
$ sudo mkdir /mnt/data
$ sudo umount /media/dave/DATA

opened etc/fstab, and changed the line with /media/dave/DATA to /mnt/data

$ sudo mount -a

And it worked!  I did the same thing to another ntfs partition, and it worked as well.  So now I do have access to the hard drive partitions I need.  Apparently having them on /media was the problem.  That's strange, though, because my previous dead laptop also had 14.04 installed, and it had an ntfs partition that worked just fine.  (Although I honestly can't guarantee at this point that it was assigned to /media).

I still have an issue with usb drives, though.  They are formatted as FAT32, and have some important data on them.  I can't get them to mount.  They also try to open under /media/dave.  Is there a way to assign them a more cooperative directory?  I examined them with the Disks utility and it reports them to be mounted at /mnt.  I can still only access them with sudo.

---

### Post by yancek on 2014-09-20
Having a flash drive which mounts in the /mnt directory as read-only for a user is default behavior.  Pretty standard is that the only files a user has read/write access to are the directories/files in /home/user.  You need to give your self permissions or change the owner.  You could also put an entry in the /etc/fstab directory but if you are not going to have them attached all the time that can create other problems.  If you use them only on occasion, it would probably be better just to mount them manually, preferably by UUID.

---

### Post by TheFu on 2014-09-20
> **llanitedave said:**
> And it worked!  I did the same thing to another ntfs partition, and it worked as well.  So now I do have access to the hard drive partitions I need.  Apparently having them on /media was the problem.  That's strange, though, because my previous dead laptop also had 14.04 installed, and it had an ntfs partition that worked just fine.  (Although I honestly can't guarantee at this point that it was assigned to /media).
So - this is one of those things that only experience would solve. BTW - it was just a guess on my side. I've seen this before, but not in exactly this manner. Things that happen automatically, often screw with things that happen manually. It is just the way of things these day - especially when GUIs are involved - that's just my opinion and personal experience from observation.

> **llanitedave said:**
> I still have an issue with usb drives, though.  They are formatted as FAT32, and have some important data on them.  I can't get them to mount.  They also try to open under /media/dave.  Is there a way to assign them a more cooperative directory?  I examined them with the Disks utility and it reports them to be mounted at /mnt.  I can still only access them with sudo.

USB2 or USB3? That's a question about the drives AND/OR the ports.  Is EHCI enabled in the bios?  On my systems with USB3, I had to disable EHCI and live with USB 1.1 speeds on USB2 ports to get the USB3 ports to work at all.  From my reading, this seems to solved USB3 issues about 20% of the time. It did for me on 2 systems.  Sadly, 1 system had 8 USB2 ports and no way to disable UHCI - had to completely disable USB2 in the BIOS. That sucked, but having USB1.1 speeds for mouse and keyboard isn't an issue - then USB3 for other stuff was well worth it.

BTW - doing this also allowed a USB3 7-port hub to work - previously, it didn't at all. Now it does USB3 and USB2 for that machine.

---

