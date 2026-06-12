---
title: "Can't mount NTFS external drive"
date: 2008-04-27
forum: General Help
---

### Post by aggierandy on 2008-04-27
**So i installed Hardy Friday and have been having trouble getting my external HDD to mount. I ran the commands:**

sudo mount -t ntfs-3g /dev/sdc2 

(as this is where the drive appears to be under fdisk -l)

it returns a message of:

~$ sudo mount -t ntfs /dev/sdc2
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

**I tried to use the -o force command at the end and that didn't work either. So i chocked it up to me screwing something up. So I ran ntfsfix and it says:**

Mounting volume... Failed to startup volume: Invalid argument.
FAILED
Attempting to correct errors... FAILED
Failed to startup volume: Invalid argument.
Volume is corrupt. You should run chkdsk.

[B]so maybe my HDD has been corrupted, so after not figuring a way to fix it. Really I haven't had any luck. I don't want to have to reformat. Any suggestions? 

I don't think I made a partitioning error when installing hardy but there's no way to make sure. The external is a 250 GB western digital. When it was originally partitioned under windows i was pretty new to things and accidentally made an 8 MB fat32 partition (i think). The rest is formatted NTFS. Gparted sees it as htfs/ntfs.

If anything else would help I would be happy to give it to you. (etc/fstab, fdisk -l, etc.)

Please help!
[/B]

---

### Post by ryanhaigh on 2008-04-27
Your post isn't particularly clear. The first problem that I can see is that you are not specifying a mount point. 
```
sudo mkdir /media/external 
sudo mount -t ntfs-3g /dev/sdc2 /media/external
```

Then the output you give is clearly for a different command
> sudo mount -t ntfs /dev/sdc2

You may want to try installing ntfs-config which provides a simple GUI to configure behaviour associated with ntfs partitions.

---

### Post by aggierandy on 2008-04-27
Thanks for your reply

Ok i see that I did enter that command wrong but I followed your commands and it gives me the following:

~$ sudo mkdir /media/external 
mkdir: cannot create directory `/media/external': Input/output error
randy@lappy:~$ sudo mount -t ntfs-3g /dev/sdc2 /media/external
Unexpected clusters per mft record (-128).
Failed to mount '/dev/sdc2': Invalid argument
The device '/dev/sdc2' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
randy@lappy:~$ sudo mount -t ntfs-3g /dev/sdc2 /media/external
Unexpected clusters per mft record (-128).
Failed to mount '/dev/sdc2': Invalid argument
The device '/dev/sdc2' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

First I don't see why I can't make the directory. Secondly I don't see why it won't mount. I installed and started ntfs-config and all I got was a dialog box with checkboxes for read and write support for NTFS. I checked the write support box and hit ok. (the read support box was greyed out)

Sorry I'm still very green at the hard drive stuff under ubuntu. Do you have anymore suggestions?

---

### Post by vanadium on 2008-04-27
Strange the output you have. the mkdir command suggests that the system does not succeed in creating a directory /media/external. However, the error in the subsequent mount command does not complain about a missing /media/external, so it would mean that that directory does exist. The output however is worrying in that it would suggest a corrupt disk.

Because it is an ntfs disk, you should first of all check the disk in MS Windows. If Windows can read and repair it, next time you connect it to Ubuntu it should auto mount.

---

### Post by ryanhaigh on 2008-04-27
Well I am quite concerned with the ouput of the mkdir command, can you create directories/files on that partition in other places? 

As for mounting the ntfs drive, it appears to me at least that you are either using the wrong device node (/dev/sdc2) or that the filesystem is indeed corrupt. I recommend as vanadium sugggests rebooting into windows to check the integrity of that partition. Then can you boot back into ubuntu and if the partition is not automounted post the output of ```
sudo fdisk -l 
```

---

### Post by lauriejb on 2008-05-02
I had this problem recently and by mounting the drive in Windows XP and using the icon at bottom left, something about disconnecting a drive, the problem resolved and I could then see everything, and do everything, with ntfs-3g.  In fact I just connected it to the Linux box and it all worked from the GUI.  I think something gets written to the HD which Ubuntu cannot get past and the NTFS system in XP has to deal with.

---

### Post by caljohnsmith on 2008-05-02
BTW, make sure that when you run ntfsfix, you run it as root, otherwise you can get errors similar to the ones you got. Try:
sudo ntfsfix /dev/sdc2

---

### Post by aggierandy on 2008-05-06
wow...connected it to a windows pc and it worked ok then connected it to linux and it was like nothing had ever gone wrong....weird. Thanks guys.

---

