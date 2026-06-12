---
title: "Problem auto-mounting ext4 partitions"
date: 2014-06-24
forum: General Help
---

### Post by jeff7181 on 2014-06-24
I have a physical Ubuntu 14.04 sever with a PERC6i raid controller. I have three logical disks being presented to the OS by that controller. One is basically the boot disk, where /, /swap, and /boot live. The other two are data partitions formatted as ext4. I used to have these on a 12.04 installation and had no issues. However, since doing the reinstall, they will not automatically mount either at boot or by using the GUI. If I run the mount command they mount just fine, but when I reboot, they can't be automatically mounted.

Here is a screenshot of the config for mounting one of the partitions:
[IMG]http://s22.postimg.org/hf3pylaq9/mount_options.png[/IMG]

And here is a screenshot of the error when trying to mount it:
[IMG]http://s27.postimg.org/53i1laiib/mount_error.png[/IMG]

The command ```
mount /dev/sdc /samba/data
``` works fine.

I've spent quite a bit of time searching Google for answers and I can't find anything. I ran fsck on the partitions and found no bad blocks or file system errors, so I don't think there's any truth to that part of the error message, especially considering I can mount them from the command line myself.

---

