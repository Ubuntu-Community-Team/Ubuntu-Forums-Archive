---
title: "deleting old kernels"
date: 2015-04-02
forum: General Help
---

### Post by Bleakley on 2015-04-02
Hi, 

I'm trying to delete old kernels and do a reinstall of Ubuntu. Getting the following problem: /dev/sda1 is totally full (for some reason) and I can't add anything even a simple .txt file. 

```
dhc@analog:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       1.4T  1.4T     0 100% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            3.9G  320K  3.9G   1% /dev
tmpfs           797M  1.1M  796M   1% /run
none            5.0M  4.0K  5.0M   1% /run/lock
none            3.9G  216K  3.9G   1% /run/shm
none            100M     0  100M   0% /run/user
overflow        1.0M   12K 1012K   2% /tmp
dhc@analog:~$ uname -r
3.16.0-31-generic
dhc@analog:~$ dpkg -l | grep linux-image
rc  linux-image-3.16.0-23-generic                        3.16.0-23.31                               amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-3.16.0-30-generic                        3.16.0-30.40                               amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-3.16.0-31-generic                        3.16.0-31.43                               amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-4.0.0-999-generic                        4.0.0-999.201503171627                     amd64        Linux kernel image for version 4.0.0 on 64 bit x86 SMP
ii  linux-image-4.0.0-999-lowlatency                     4.0.0-999.201503171627                     amd64        Linux kernel image for version 4.0.0 on 64 bit x86 SMP
rc  linux-image-extra-3.16.0-23-generic                  3.16.0-23.31                               amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-extra-3.16.0-30-generic                  3.16.0-30.40                               amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-extra-3.16.0-31-generic                  3.16.0-31.43                               amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-generic                                  3.16.0.31.32                               amd64        Generic Linux kernel image
dhc@analog:~$ sudo apt-get purge linux-image-3.16.0-23-generic
dhc@analog:~$ e lists... 0%
dhc@analog:~$ dpkg -l | grep linux-image
rc  linux-image-3.16.0-23-generic                        3.16.0-23.31                               amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-3.16.0-30-generic                        3.16.0-30.40                               amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-3.16.0-31-generic                        3.16.0-31.43                               amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-4.0.0-999-generic                        4.0.0-999.201503171627                     amd64        Linux kernel image for version 4.0.0 on 64 bit x86 SMP
ii  linux-image-4.0.0-999-lowlatency                     4.0.0-999.201503171627                     amd64        Linux kernel image for version 4.0.0 on 64 bit x86 SMP
rc  linux-image-extra-3.16.0-23-generic                  3.16.0-23.31                               amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-extra-3.16.0-30-generic                  3.16.0-30.40                               amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-extra-3.16.0-31-generic                  3.16.0-31.43                               amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-generic                                  3.16.0.31.32                               amd64        Generic Linux kernel image
dhc@analog:~$ uname -r
3.16.0-31-generic
dhc@analog:~$ sudo apt-get purge linux-image-3.16.0-23-generic
Reading package lists... Error!
E: Write error - write (28: No space left on device)
E: Can't mmap an empty file
E: Failed to truncate file - ftruncate (9: Bad file descriptor)
E: The package lists or status file could not be parsed or opened.
dhc@analog:~$ sudo apt-get purge linux-image-3.16.0-23-generic
Reading package lists... Error!
E: Write error - write (28: No space left on device)
E: Can't mmap an empty file
E: Failed to truncate file - ftruncate (9: Bad file descriptor)
E: The package lists or status file could not be parsed or opened.
dhc@analog:~$
```


Thanks!

---

### Post by Impavidus on 2015-04-02
1.4TB is a lot. It's not caused by a few old kernels. Find out which directories take all that space. See this guide for some tips: [http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670). Use the du command.

On the other hand, if you want to reinstall, don't bother and just wipe everything. But keep in mind that whatever caused your free space to disappear may do so again.

---

### Post by Kirkx on 2015-04-03
Here is a thread about removing old kernels:

[http://ubuntuforums.org/showthread.php?t=2240697](http://ubuntuforums.org/showthread.php?t=2240697)

---

### Post by ortermagic on 2015-04-03
Ubuntu tweak seems to work for me

---

### Post by ajgreeny on 2015-04-03
Come on chaps! It's not just old kernels taking 1.4TB; there are only four kernels on the machine which would use around 1 - 2GB at most and probably not that much.

My guess is that there is some huge log file building up in /var, but what we need to see is the output of command ```
sudo du -h --max-depth=1 /
``` which will show us which main system folder is using all that disk space.  It may take a few seconds to get the output of that command so be just a little patient and wait for the terminal prompt to reappear.

---

### Post by dragonfly41 on 2015-04-03
Here is just one recent experience...

I found an extra 35GB in my /var/ folder .. just by experimenting with an installation of ubuntu-sdk

[http://ubuntuforums.org/showthread.php?t=2271669](http://ubuntuforums.org/showthread.php?t=2271669)

I have yet to purge this schroot "os within an os" after backup.


[COLOR=#b22222][a follow up edit]

I'm adding this as just another possible cause for disk running out of space ..

[http://www.ivankuznetsov.com/2010/02/no-space-left-on-device-running-out-of-inodes.html](http://www.ivankuznetsov.com/2010/02/no-space-left-on-device-running-out-of-inodes.html)[/COLOR]

---

