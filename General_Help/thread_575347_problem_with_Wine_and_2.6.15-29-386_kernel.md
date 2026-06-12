---
title: "problem with Wine and 2.6.15-29-386 kernel"
date: 2007-10-13
forum: General Help
---

### Post by brian724 on 2007-10-13
There is a problem with Wine 0.9.9 and the 2.6.15-29-386 kernel. 
If you try to run an exe with wine from a FAT partition it will cause wine to hang.
I am also seeing Picasa hang on the add media dialog if I have any FAT partitions mounted. 
The Wine developers are blaming this on the kernel and it does not appear that they are going to make any changes to resolve the problem. 
2.6.15-29-386 is the most recent kernel in the repository for Dapper. 
It seems that until a new kernel is added the options to get around this are:
1. don't run exes from FAT partitions
2. revert to an older kernel
3. get the source, compile, and install a new kernel on your own. 
4. recompile wine with the option specified in the bug report (below)



[http://bugs.winehq.org/show_bug.cgi?id=9607](http://bugs.winehq.org/show_bug.cgi?id=9607)
Distro: Kubuntu Dapper 6.06
Wine: 0.9.9-0ubuntu2 (tested also with 0.9.39 from winehq.org)
Kernel: 2.6.15-29-386 (2.6.15-29.58)

This is kernel bug, but affects only wine, so workaround in wine is easier.

When .exe is run from FAT partition, wine process gets stuck in kernel in "D"
state and cannot be killed.

I have straced the process and it appears it is stuck in:
 ioctl(9, TUNIOCGETINFO or VFAT_IOCTL_READDIR_BOTH
This way user can prevent unmounting FAT partition by running wine on FAT
partition.
To reproduce:
 1. Mount any FAT volume (for example USB pendrive)
 2. Copy some file.exe file to it.
 3. Run: wine /media/mydisk/file.exe
 4. Wine hangs and cannot be killed.

Possible workaround is to recompile wine with "#define VFAT_IOCTL_READDIR_BOTH"
in dlls/ntdll/directory.c commented out.
I have checked that it works.

See also here: [https://bugs.launchpad.net/ubuntu/+source/wine/+bug/137978](https://bugs.launchpad.net/ubuntu/+source/wine/+bug/137978)

---

