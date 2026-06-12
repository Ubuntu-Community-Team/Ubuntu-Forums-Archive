---
title: "File System Check Counter on boot"
date: 2006-07-26
forum: General Help
---

### Post by geco on 2006-07-26
Hi all,
I'm trying to find out how to reset the counter of fsck on boot.
Each 30 times I boot my machine (e.g. Linux mounts the partitions) I have a filesystem check, now I want to reset it because the counter of root FS is 1 unit below the other partitions' counter (it depends by the different scripts run on boot: checkroot.sh and checkfs.sh) and it is a little bit annoying.
Anyone knows how to do it?
I read the init scripts but I didn't find anything... :-k 

Thank you!

---

### Post by nilfilter on 2006-07-26
tune2fs - adjust tunable filesystem parameters on ext2/ext3 filesystems

IIRC, you can change the mount count check by issuing 
```
tune2fs -c# /dev/<partition>
```where # is the new mount count. You can check the currently used settings with 
```
dumpe2fs /dev/<partition>|grep count
```Still, please check the tune2fs man page just to make sure.

---

### Post by geco on 2006-07-26
thank you! I will check the manual!
byebye

---

### Post by geco on 2006-07-26
> **geco said:**
> thank you! I will check the manual!
byebye
if anyone else needs info about this thread... here is a part of tune2fs manual:
[quote=tune2fs man]

-c max-mount-counts
              Adjust the maximal mounts count between two filesystem checks.  If max-mount-counts is 0 or -1,
              the  number of times the filesystem is mounted will be disregarded by e2fsck(8) and the kernel.

              Staggering the mount-counts at which filesystems are forcibly checked will avoid  all  filesys&#8208;
              tems being checked at one time when using journaled filesystems.

              You  should  strongly  consider  the  consequences  of disabling mount-count-dependent checking
              entirely.  Bad disk drives, cables, memory, and kernel bugs  could  all  corrupt  a  filesystem
              without marking the filesystem dirty or in error.  If you are using journaling on your filesys&#8208;
              tem, your filesystem will never be marked dirty,  so  it  will  not  normally  be  checked.   A
              filesystem error detected by the kernel will still force an fsck on the next reboot, but it may
              already be too late to prevent data loss at that point.

              See also the -i option for time-dependent checking.

       -C mount-count
              Set the number of times the filesystem has been mounted.  Can be used in conjunction with -c to
              force an fsck on the filesystem at the next reboot.
[/quote]

---

