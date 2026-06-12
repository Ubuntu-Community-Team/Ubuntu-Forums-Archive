---
title: "[SOLVED] FAT32 Mount: Switches from writable to unwritable"
date: 2007-10-15
forum: General Help
---

### Post by dopplerdjay on 2007-10-15
I figured out the problem, there was an error on the disc and anytime I tried the access the folder (where the error was found), it would lock the partition out. Ironically I found this out when trying to access it under Windows.


> First off,  I am running Ubuntu 6.06 LTS - the Dapper Drake and a newbie.

My FAT32 mount has been working perfect ever since I followed instructions on setting it up. However, today, when it mounts, I cannot write any files to it, I get an error "You do not have permissions to write to this folder."

So I went ahead and did:
```

swerner@swerner-laptop:~$ sudo umount /dev/hda4
swerner@swerner-laptop:~$ sudo mount -a

```

After remounting all the drives, I open up Nautilus, where I am allowed to write files to the partition. However, the moment I close out, the mount becomes locked and I get the same error message, "You do not have permissions to write to this folder." when I attempt to write files again.

Here is what my fstab file looks like:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda4    	/mnt/shared 	vfat  iocharset=utf8,umask=000  0    0

```

Any ideas?

---

### Post by greenstar on 2007-10-17
That's great that you figured it out.:) Please mark your thread as solved, so that others may benefit. Instruction link is in my signature.

Thanks,
Greenstar

---

