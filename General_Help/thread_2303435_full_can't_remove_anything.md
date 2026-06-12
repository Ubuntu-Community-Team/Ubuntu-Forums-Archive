---
title: "/ full can't remove anything"
date: 2015-11-18
forum: General Help
---

### Post by cmcanulty on 2015-11-18
I have a mess on a remote machine. / is full so it won't let me open synaptic or even remove a ton of old kernels because it is full see the following however there is some space left 16MB I could remove a ton of old kernels but can't seem to get it to let me
```
librarian@Office:~$ dpkg -l | grep linux-image
ii  linux-image-3.13.0-24-generic               3.13.0-24.47                                   amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-49-generic               3.13.0-49.83                                   amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-51-generic               3.13.0-51.84                                   amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-54-generic               3.13.0-54.91                                   amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-55-generic               3.13.0-55.94                                   amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-61-generic               3.13.0-61.100                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-62-generic               3.13.0-62.102                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-63-generic               3.13.0-63.103                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-65-generic               3.13.0-65.106                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rH  linux-image-3.13.0-66-generic               3.13.0-66.108                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-68-generic               3.13.0-68.111                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.16.0-38-generic               3.16.0-38.52~14.04.1                           amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-3.16.0-39-generic               3.16.0-39.53~14.04.1                           amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-3.16.0-41-generic               3.16.0-41.57~14.04.1                           amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-3.16.0-45-generic               3.16.0-45.60~14.04.1                           amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-3.16.0-46-generic               3.16.0-46.62~14.04.1                           amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-3.16.0-48-generic               3.16.0-48.64~14.04.1                           amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-3.16.0-49-generic               3.16.0-49.65~14.04.1                           amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-3.16.0-50-generic               3.16.0-50.67~14.04.1                           amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-3.16.0-51-generic               3.16.0-51.69~14.04.1                           amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-3.16.0-53-generic               3.16.0-53.72~14.04.1                           amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-25-generic               3.19.0-25.26~14.04.1                           amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-26-generic               3.19.0-26.28~14.04.1                           amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-28-generic               3.19.0-28.30~14.04.1                           amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-30-generic               3.19.0-30.34~14.04.1                           amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-31-generic               3.19.0-31.36~14.04.1                           amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-33-generic               3.19.0-33.38~14.04.1                           amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-24-generic         3.13.0-24.47                                   amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-49-generic         3.13.0-49.83                                   amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-51-generic         3.13.0-51.84                                   amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-54-generic         3.13.0-54.91                                   amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-55-generic         3.13.0-55.94                                   amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-61-generic         3.13.0-61.100                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-62-generic         3.13.0-62.102                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-63-generic         3.13.0-63.103                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-65-generic         3.13.0-65.106                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rH  linux-image-extra-3.13.0-66-generic         3.13.0-66.108                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-68-generic         3.13.0-68.111                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.16.0-38-generic         3.16.0-38.52~14.04.1                           amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-extra-3.16.0-39-generic         3.16.0-39.53~14.04.1                           amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-extra-3.16.0-41-generic         3.16.0-41.57~14.04.1                           amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-extra-3.16.0-45-generic         3.16.0-45.60~14.04.1                           amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-extra-3.16.0-46-generic         3.16.0-46.62~14.04.1                           amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-extra-3.16.0-48-generic         3.16.0-48.64~14.04.1                           amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-extra-3.16.0-49-generic         3.16.0-49.65~14.04.1                           amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-extra-3.16.0-50-generic         3.16.0-50.67~14.04.1                           amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-extra-3.16.0-51-generic         3.16.0-51.69~14.04.1                           amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-extra-3.16.0-53-generic         3.16.0-53.72~14.04.1                           amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-25-generic         3.19.0-25.26~14.04.1                           amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-26-generic         3.19.0-26.28~14.04.1                           amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-28-generic         3.19.0-28.30~14.04.1                           amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-30-generic         3.19.0-30.34~14.04.1                           amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-31-generic         3.19.0-31.36~14.04.1                           amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-33-generic         3.19.0-33.38~14.04.1                           amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-generic                         3.13.0.68.74                                   amd64        Generic Linux kernel image
ii  linux-image-generic-lts-utopic              3.16.0.53.44                                   amd64        Generic Linux kernel image
ii  linux-image-generic-lts-vivid               3.19.0.33.20                                   amd64        Generic Linux kernel image
librarian@Office:~$ sudo dpkg -r linux-image-3.13.0-24-generic    
[sudo] password for librarian: 
dpkg: unrecoverable fatal error, aborting:
 unable to fill /var/lib/dpkg/updates/tmp.i with padding: No space left on device
librarian@Office:~$ sudo apt-get purge linux-image-3.13.0-24-generic
librarian@Office:~$ s... 98%

```

and 
```

librarian@Office:~$ sudo apt-get purge linux-image-3.13.0-49-generic 
[sudo] password for librarian: 
Reading package lists... Error!
E: Write error - write (28: No space left on device)
E: Can't mmap an empty file
E: Failed to truncate file - ftruncate (9: Bad file descriptor)
E: The package lists or status file could not be parsed or opened.
librarian@Office:~$ 
```

---

### Post by oldfred on 2015-11-18
You are showing thread different versions of kernels. 
So is this an upgraded computer.
After the upgrade the older kernels are not in dpkg any more, only the current versions. The old versions then can only be manually removed and then depending on how you delete them, they may be in root trash and deleted again.

       Determine your current kernel:
uname -a

    
For the older kernels you may have to just use rm, but be extremely careful. Any typo or even an extra space can then have major unintended consequences. Good backups always required.

       cd /boot
ls -l /boot/vmlinuz*
sudo apt-get purge  linux-image-[version]-generic linux-image-[version]-generic
Multiples, just be sure not to delete your current kernel:
sudo apt-get purge linux-image-3.13.0-{XX,XX,XX,XX,XX,XX}-generic
sudo apt-get purge linux-image-3.13.0-{54,55,57}-generic
Also headers:
dpkg -S /usr/src/*
Example, some did not have -generic at end:
sudo apt-get purge linux-headers-3.13.0-39-generic

    
The normal apt-get purge also cleans up both /lib/modules & /usr/src. But for the manual deletes you may need to also house clean those locations also.

ls /usr/src
ls /lib/modules
ls /var/cache/apt/archives/linux-image*

---

### Post by cmcanulty on 2015-11-18
I am confused as I said I tried the purge but get the error

```
sudo apt-get purge linux-image-3.13.0-49-generic 
```

```
dpkg: unrecoverable fatal error, aborting:
 unable to fill /var/lib/dpkg/updates/tmp.i with padding: No space left on device
```

Here is the result of your command 

```
librarian@Office:~$ sudo uname -a
[sudo] password for librarian: 
Linux Office 3.19.0-33-generic #38~14.04.1-Ubuntu SMP Fri Nov 6 18:17:28 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
librarian@Office:~$
```

---

### Post by pqwoerituytrueiwoq on 2015-11-18
1st run 
[FONT=courier new]sodo apt-get clean[/FONT]
then reboot and start puring old stuff (for some reason even after freeing space the system does not realize it is free)
if you still need more free space you can take advantage of your ram and make /tmp a ram disk (i only suggest this if you have 4gb+ ram)
[FONT=courier new]sudo apt-get autoremove --purge[/FONT]
and anything else you want remove you can now
reboot and install updates
if you need more free space look for large log files you can delete in /var/log

---

### Post by oldfred on 2015-11-18
If you upgraded, then all the old kernels like 3.13, 3.16 will not be in dpkg. 
Only those from the newest version or all the 3.19 versions.

---

### Post by cmcanulty on 2015-11-19
Here is what I get from your commands, it appears being full disables any way to remove things even though there is 16MB left
```

v 6 18:17:28 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
No command 'Linux' found, did you mean:
 Command 'linux' from package 'user-mode-linux' (universe)
Linux: command not found
librarian@Office:~$ librarian@Office:~$ sudo apt-get clean
librarian@Office:~$: command not found
librarian@Office:~$ sudo apt-get autoremove --purge
[sudo] password for librarian: 
Reading package lists... Error!
E: Write error - write (28: No space left on device)
E: Can't mmap an empty file
E: Failed to truncate file - ftruncate (9: Bad file descriptor)
E: The package lists or status file could not be parsed or opened.
librarian@Office:~$E]
```

---

### Post by oldfred on 2015-11-19
You will  have to use the dangerous rm command. See man rm.
I think you have to use it for all older version kernels. The cleanup will only work for all the standard extra kernels in your current version or 3.19 versions. But you have to use rm to delete at least some old version ones to have space for standard housekeeping commands to work like dpkg or using synpatic.

cd /boot
sudo rm -i linux-image-3.13.0-24-generic
You also have to run for each of initrd files, system map, config , abi or any other related system file in /boot with 3.13.0-24 in name.
Why always best to do a major houseclean before upgrade. Or as many of us do a new full clean install to totally houseclean.

You may also have lots of logs, messages and many other old files that need housecleaning.
       Updates, backups, delete old kernels - TheFu in Forums
[http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs](http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs)

   RecoverLostDiskSpace
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)
HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)
HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)
    Caution deborphan will delete anything you manually installed. See comment:

    

Then check if you also the 3.13.0-24 versions of headers or other files in the other locations posted above.

---

### Post by cmcanulty on 2015-11-19
still an error


```
librarian@Office:~$ cd /boot
librarian@Office:/boot$ sudo rm -i linux-image-3.13.0-24-generic
[sudo] password for librarian: 
rm: cannot remove ‘linux-image-3.13.0-24-generic’: No such file or directory
librarian@Office:/boot$ 
```

---

### Post by oldfred on 2015-11-19
That was from your dpkg list, maybe that is outdated with update.
What is in /boot

cd /boot
ls -l

Then use rm command on really old files in /boot to make room for standard commands to work.

---

### Post by pqwoerituytrueiwoq on 2015-11-19
this is the equivalent of apt-get clean
```
rm -r /var/cache/apt/archives/*.deb
```
that should hopefully free up enough space to get apt working

---

### Post by cmcanulty on 2015-11-19
here are the results

```
librarian@Office:~$ rm -r /var/cache/apt/archives/*.deb
rm: cannot remove ‘/var/cache/apt/archives/*.deb’: No such file or directory
librarian@Office:~$ 

```

and

```

librarian@Office:~$ cd /boot
librarian@Office:/boot$ ls -l
total 416828
-rw-r--r-- 1 root root  1158016 May  2  2014 abi-3.13.0-24-generic
-rw-r--r-- 1 root root  1164723 Apr 10  2015 abi-3.13.0-49-generic
-rw-r--r-- 1 root root  1164671 Apr 15  2015 abi-3.13.0-51-generic
-rw-r--r-- 1 root root  1164806 May 26 16:11 abi-3.13.0-54-generic
-rw-r--r-- 1 root root  1164806 Jun 17 21:03 abi-3.13.0-55-generic
-rw-r--r-- 1 root root  1165260 Nov  6 14:57 abi-3.13.0-68-generic
-rw-r--r-- 1 root root  1207096 May  8  2015 abi-3.16.0-38-generic
-rw-r--r-- 1 root root  1207366 May 27 06:42 abi-3.16.0-39-generic
-rw-r--r-- 1 root root  1207366 Jun 18 15:02 abi-3.16.0-41-generic
-rw-r--r-- 1 root root  1207787 Oct  7 16:18 abi-3.16.0-51-generic
-rw-r--r-- 1 root root  1207789 Nov  6 15:09 abi-3.16.0-53-generic
-rw-r--r-- 1 root root  1271518 Oct  2 19:54 abi-3.19.0-30-generic
-rw-r--r-- 1 root root  1271689 Oct  8 08:01 abi-3.19.0-31-generic
-rw-r--r-- 1 root root  1271689 Nov  6 15:39 abi-3.19.0-33-generic
-rw-r--r-- 1 root root   165510 May  2  2014 config-3.13.0-24-generic
-rw-r--r-- 1 root root   165773 Apr 10  2015 config-3.13.0-49-generic
-rw-r--r-- 1 root root   165762 Apr 15  2015 config-3.13.0-51-generic
-rw-r--r-- 1 root root   165762 May 26 16:11 config-3.13.0-54-generic
-rw-r--r-- 1 root root   165762 Jun 17 21:03 config-3.13.0-55-generic
-rw-r--r-- 1 root root   165763 Nov  6 14:57 config-3.13.0-68-generic
-rw-r--r-- 1 root root   171817 May  8  2015 config-3.16.0-38-generic
-rw-r--r-- 1 root root   171817 May 27 06:42 config-3.16.0-39-generic
-rw-r--r-- 1 root root   171817 Jun 18 15:02 config-3.16.0-41-generic
-rw-r--r-- 1 root root   171832 Oct  7 16:18 config-3.16.0-51-generic
-rw-r--r-- 1 root root   171832 Nov  6 15:09 config-3.16.0-53-generic
-rw-r--r-- 1 root root   177730 Oct  2 19:54 config-3.19.0-30-generic
-rw-r--r-- 1 root root   177790 Oct  8 08:01 config-3.19.0-31-generic
-rw-r--r-- 1 root root   177790 Nov  6 15:39 config-3.19.0-33-generic
drwxr-xr-x 3 root root     4096 Nov 18 14:47 extlinux
drwxr-xr-x 5 root root     4096 Nov 11 12:38 grub
-rw-r--r-- 1 root root 19114013 Aug 12 08:43 initrd.img-3.13.0-24-generic
-rw-r--r-- 1 root root 19207045 Aug 12 08:43 initrd.img-3.13.0-49-generic
-rw-r--r-- 1 root root 19207500 Aug 12 08:44 initrd.img-3.13.0-51-generic
-rw-r--r-- 1 root root 19207013 Aug 12 08:44 initrd.img-3.13.0-54-generic
-rw-r--r-- 1 root root 19208713 Aug 12 08:44 initrd.img-3.13.0-55-generic
-rw-r--r-- 1 root root 19213521 Nov 11 12:38 initrd.img-3.13.0-68-generic
-rw-r--r-- 1 root root 19438196 Aug 12 08:44 initrd.img-3.16.0-38-generic
-rw-r--r-- 1 root root 19437720 Aug 12 08:45 initrd.img-3.16.0-39-generic
-rw-r--r-- 1 root root 19437932 Aug 12 08:45 initrd.img-3.16.0-41-generic
-rw-r--r-- 1 root root 19445686 Oct 21 17:48 initrd.img-3.16.0-51-generic
-rw-r--r-- 1 root root 19446786 Nov 11 12:38 initrd.img-3.16.0-53-generic
-rw-r--r-- 1 root root 19796563 Oct 14 12:12 initrd.img-3.19.0-30-generic
-rw-r--r-- 1 root root 19796402 Oct 21 17:49 initrd.img-3.19.0-31-generic
-rw-r--r-- 1 root root 19796631 Nov 11 12:38 initrd.img-3.19.0-33-generic
-rw-r--r-- 1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r-- 1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r-- 1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw------- 1 root root  3372643 May  2  2014 System.map-3.13.0-24-generic
-rw------- 1 root root  3389437 Apr 10  2015 System.map-3.13.0-49-generic
-rw------- 1 root root  3389875 Apr 15  2015 System.map-3.13.0-51-generic
-rw------- 1 root root  3390881 May 26 16:11 System.map-3.13.0-54-generic
-rw------- 1 root root  3390881 Jun 17 21:03 System.map-3.13.0-55-generic
-rw------- 1 root root  3392383 Nov  6 14:57 System.map-3.13.0-68-generic
-rw------- 1 root root  3513313 May  8  2015 System.map-3.16.0-38-generic
-rw------- 1 root root  3514712 May 27 06:42 System.map-3.16.0-39-generic
-rw------- 1 root root  3514712 Jun 18 15:02 System.map-3.16.0-41-generic
-rw------- 1 root root  3516658 Oct  7 16:18 System.map-3.16.0-51-generic
-rw------- 1 root root  3516949 Nov  6 15:09 System.map-3.16.0-53-generic
-rw------- 1 root root  3627906 Oct  2 19:54 System.map-3.19.0-30-generic
-rw------- 1 root root  3628177 Oct  8 08:01 System.map-3.19.0-31-generic
-rw------- 1 root root  3628149 Nov  6 15:39 System.map-3.19.0-33-generic
-rw------- 1 root root  5776416 May  2  2014 vmlinuz-3.13.0-24-generic
-rw------- 1 root root  5815392 Apr 10  2015 vmlinuz-3.13.0-49-generic
-rw------- 1 root root  5818368 Apr 15  2015 vmlinuz-3.13.0-51-generic
-rw------- 1 root root  5821664 May 26 16:11 vmlinuz-3.13.0-54-generic
-rw------- 1 root root  5821984 Jun 17 21:03 vmlinuz-3.13.0-55-generic
-rw------- 1 root root  5822400 Nov  6 14:57 vmlinuz-3.13.0-68-generic
-rw------- 1 root root  6351952 May  8  2015 vmlinuz-3.16.0-38-generic
-rw------- 1 root root  6353360 May 27 06:42 vmlinuz-3.16.0-39-generic
-rw------- 1 root root  6353360 Jun 18 15:02 vmlinuz-3.16.0-41-generic
-rw------- 1 root root  6359728 Oct  7 16:18 vmlinuz-3.16.0-51-generic
-rw------- 1 root root  6359920 Nov  6 15:09 vmlinuz-3.16.0-53-generic
-rw------- 1 root root  6572496 Oct  2 19:54 vmlinuz-3.19.0-30-generic
-rw------- 1 root root  6572336 Oct  8 08:01 vmlinuz-3.19.0-31-generic
-rw------- 1 root root  6572432 Nov  6 15:39 vmlinuz-3.19.0-33-generic
librarian@Office:/boot$ 

```

---

### Post by oldfred on 2015-11-19
Your ls of /boot shows this:
vmlinuz-3.13.0-24-generic

So I do not understand why this did not work. try without the -i?

 librarian@Office:/boot$ sudo rm -i linux-image-3.13.0-24-generic
 

Correction: The linux-image is the package as synaptic or dpkg shows, but files are each of the several  3.13.0-0-24 files

sudo rm vmlinuz-3.13.0-24-generic

and each of these:
 abi-3.13.0-24-generic
config-3.13.0-24-generic
initrd.img-3.13.0-24-generic
System.map-3.13.0-24-generic

---

### Post by cmcanulty on 2015-11-20
still no go here it is

```
librarian@Office:~$ sudo rm vmlinuz-3.13.0-24-generic
[sudo] password for librarian: 
rm: cannot remove \u2018vmlinuz-3.13.0-24-generic\u2019: No such file or directory
librarian@Office:~$ 

```

---

### Post by oldos2er on 2015-11-20
You need to cd to /boot to run sudo rm linux-image-3.13.0-24-generic or add it to the command's path: ```
sudo rm /boot/linux-image-3.13.0-24-generic
```

---

### Post by cmcanulty on 2015-11-20
still an error I would go in manually with gksu nautilus but it won't run


```

librarian@Office:~$ sudo rm /boot/linux-image-3.13.0-24-generic
[sudo] password for librarian: 
rm: cannot remove ‘/boot/linux-image-3.13.0-24-generic’: No such file or directory
librarian@Office:~$ 

```

---

### Post by QDR06VV9 on 2015-11-20
As oldos2er suggested

```
cd /boot
```
Then Try
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo rm vmlinuz-3.13.0-24-generic[/FONT][/COLOR]
```
Kind regards

---

### Post by Tadaen_Sylvermane on 2015-11-20
In the latest above ```
[COLOR=#000000][FONT=Ubuntu Mono]librarian@Office:/boot$ ls -l[/FONT][/COLOR] 
``` I don't see any linux-image* there. Hit it with a sledgehammer...

```
sudo rm -r /boot/*3.13*
sudo rm -r /boot/*3.16*
```

should clean out the 3.13 files and 3.16 files. hopefully will give you enough room as well. Follow up with ```
sudo update-grub
``` For future usage every week, maybe on a script or something run ```
apt-get autoremove
``` to keep old junk like old kernels cleaned up.

---

