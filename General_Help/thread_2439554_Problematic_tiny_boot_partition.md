---
title: "Problematic tiny /boot partition"
date: 2020-03-29
forum: General Help
---

### Post by gene14 on 2020-03-29
Greetings All -
The /boot partition from the default installation is relatively tiny. Every time I add or update packages, updater tries to update /boot as well.

So one day I attacked the problem. The way things are set up, I apparently can't expand the partition. So the obvious solution was to clean it up and be sure that updater cleaned up after itself. The initial /boot looked like:

total 227193K
-rw-r--r-- 1 root root   217278 Jun 24  2019 config-4.15.0-54-generic
-rw-r--r-- 1 root root   217278 Jul  2  2019 config-4.15.0-55-generic
drwxr-xr-x 5 root root     1024 Mar 19 18:01 grub
-rw-r--r-- 1 root root 29749029 Mar 19 18:07 initrd.img-4.15.0-51-generic
-rw-r--r-- 1 root root 60780249 Mar 19 18:07 initrd.img-4.15.0-54-generic
-rw-r--r-- 1 root root 60792038 Mar 19 18:07 initrd.img-4.15.0-55-generic
-rw-r--r-- 1 root root 18235027 Mar 19 18:08 initrd.img-4.4.0-103-generic
-rw-r--r-- 1 root root 18235069 Mar 19 18:08 initrd.img-4.4.0-93-generic
-rw-r--r-- 1 root root 18235052 Mar 19 18:08 initrd.img-4.4.0-96-generic
drwx------ 2 root root    12288 Mar 12  2016 lost+found
-rw-r--r-- 1 root root   182704 Jan 28  2016 memtest86+.bin
-rw-r--r-- 1 root root   184380 Jan 28  2016 memtest86+.elf
-rw-r--r-- 1 root root   184840 Jan 28  2016 memtest86+_multiboot.bin
-rw------- 1 root root  4051606 Jun 24  2019 System.map-4.15.0-54-generic
-rw------- 1 root root  4051807 Jul  2  2019 System.map-4.15.0-55-generic
-rw------- 1 root root  8294136 Jun 24  2019 vmlinuz-4.15.0-54-generic
-rw------- 1 root root  8294136 Jul  2  2019 vmlinuz-4.15.0-55-generic

After clean up I had this:
-rw-r--r-- 1 root root   217278 Jun 24  2019 config-4.15.0-54-generic
-rw-r--r-- 1 root root   217278 Jul  2  2019 config-4.15.0-55-generic
drwxr-xr-x 5 root root     1024 Mar 19 18:01 grub
-rw-r--r-- 1 root root 60780249 Mar 19 18:07 initrd.img-4.15.0-54-generic
-rw-r--r-- 1 root root 60792038 Mar 19 18:07 initrd.img-4.15.0-55-generic
drwx------ 2 root root    12288 Mar 12  2016 lost+found
-rw-r--r-- 1 root root   182704 Jan 28  2016 memtest86+.bin
-rw-r--r-- 1 root root   184380 Jan 28  2016 memtest86+.elf
-rw-r--r-- 1 root root   184840 Jan 28  2016 memtest86+_multiboot.bin
-rw------- 1 root root  4051606 Jun 24  2019 System.map-4.15.0-54-generic
-rw------- 1 root root  4051807 Jul  2  2019 System.map-4.15.0-55-generic
-rw------- 1 root root  8294136 Jun 24  2019 vmlinuz-4.15.0-54-generic
-rw------- 1 root root  8294136 Jul  2  2019 vmlinuz-4.15.0-55-generic

Note that the following were no longer there:
-rw-r--r-- 1 root root 29749029 Mar 19 18:07 initrd.img-4.15.0-51-generic
-rw-r--r-- 1 root root 18235027 Mar 19 18:08 initrd.img-4.4.0-103-generic
-rw-r--r-- 1 root root 18235069 Mar 19 18:08 initrd.img-4.4.0-93-generic
-rw-r--r-- 1 root root 18235052 Mar 19 18:08 initrd.img-4.4.0-96-generic

dpkg says:
rc  linux-image-4.15.0-43-generic                                    4.15.0-43.46                                                  
rc  linux-image-4.15.0-52-generic                                    4.15.0-52.56                                                  
ii  linux-image-4.15.0-54-generic                                    4.15.0-54.58                                                  
ii  linux-image-4.15.0-55-generic                                    4.15.0-55.60                                                  
rc  linux-image-4.2.0-16-generic                                     4.2.0-16.19                                                   
rc  linux-image-4.2.0-30-generic                                     4.2.0-30.36                                                   
rc  linux-image-4.2.0-34-generic                                     4.2.0-34.39                                                   
rc  linux-image-4.2.0-35-generic                                     4.2.0-35.40                                                   
rc  linux-image-4.4.0-21-generic                                     4.4.0-21.37                                                   
rc  linux-image-4.4.0-22-generic                                     4.4.0-22.40                                                   
rc  linux-image-4.4.0-24-generic                                     4.4.0-24.43                                                   
rc  linux-image-4.4.0-28-generic                                     4.4.0-28.47                                                   
rc  linux-image-4.4.0-31-generic                                     4.4.0-31.50                                                   
rc  linux-image-4.4.0-34-generic                                     4.4.0-34.53                                                   
rc  linux-image-4.4.0-36-generic                                     4.4.0-36.55                                                   
rc  linux-image-4.4.0-38-generic                                     4.4.0-38.57                                                   
rc  linux-image-4.4.0-42-generic                                     4.4.0-42.62                                                   
rc  linux-image-4.4.0-43-generic                                     4.4.0-43.63                                                   

Every time updater runs or I add a new package those four files reappear:
-rw-r--r-- 1 root root 29749029 Mar 19 18:07 initrd.img-4.15.0-51-generic
-rw-r--r-- 1 root root 18235027 Mar 19 18:08 initrd.img-4.4.0-103-generic
-rw-r--r-- 1 root root 18235069 Mar 19 18:08 initrd.img-4.4.0-93-generic
-rw-r--r-- 1 root root 18235052 Mar 19 18:08 initrd.img-4.4.0-96-generic

Clearly I managed to screw it up somewhere. Can anyone point me in the right direction to figure out what's going on here ?

Thanks
Gene

---

### Post by oldfred on 2020-03-29
It looks like an upgraded system.
You probably are booting with 4.15 kernels, but still have old 4.4 kernels that should have been housecleaned before update.
Generally you only uninstall kernels using dpkg, but if upgrade you may not have 4.4 shown?
Check using synaptic is kernels are still shown installed as manually removing them, is not just kernel, but packages and other parts of system.

Or check with command line if kernels shown.
Check current kernel I also keep one older just in case:
#Current kernel:
uname -a
# kernels, shows older also?
dpkg --list | grep linux-image
-s is simulate so you can see what it will do, then run without -s
sudo apt-get -s autoremove

[https://help.ubuntu.com/community/RemoveOldKernels](https://help.ubuntu.com/community/RemoveOldKernels)
[https://askubuntu.com/questions/89710/how-do-i-free-up-more-space-in-boot](https://askubuntu.com/questions/89710/how-do-i-free-up-more-space-in-boot)
[https://askubuntu.com/questions/976327/again-boot-is-full](https://askubuntu.com/questions/976327/again-boot-is-full)
[https://ubuntuforums.org/showthread.php?t=2361761](https://ubuntuforums.org/showthread.php?t=2361761)
/boot full or Not enough disk space on updates
[http://ubuntuforums.org/showthread.php?t=2308938&p=13418808#post13418808](http://ubuntuforums.org/showthread.php?t=2308938&p=13418808#post13418808)

If you have to manually remove, check all these also:
[http://askubuntu.com/questions/301466/files-are-piling-up-in-usr-src-how-can-i-stop-this](http://askubuntu.com/questions/301466/files-are-piling-up-in-usr-src-how-can-i-stop-this)
in /boot by version: abi, config, initrd.img, vmlinuz
[https://ubuntuforums.org/showthread.php?t=2413216](https://ubuntuforums.org/showthread.php?t=2413216)

---

### Post by westie457 on 2020-03-29
> [COLOR=#000000]The /boot partition from the default installation is relatively tiny[/COLOR]
If you mean the /boot partition when installing with LVM then please say so.
How did you go about removing the unneeded files?

---

### Post by TheFu on 2020-03-29
I&#8217;m an LVM guy.  

First, let's see what the issue is. Post,
```
df -hT -x squashfs -x tmpfs -x devtmpfs
```
output. Use code tags or  it will be too hard to read. 
Let's see where and what  is using LVM on the system. Next, post,
```
lsblk -e 7 -o name,size,type,fstype,mountpoint
```
also using code tags.

The df command will show which partitions are full.
The lsblk command will show what the rest of the disk looks like and how the LVM, if used, is organized.

if you patch weekly using **sudo apt update && sudo apt upgrade**, then old kernels should be removed as needed, but once the /boot/ gets full, manual steps are needed to fix  it, then doing the update/upgrade weekly will work again as it should.

---

### Post by Impavidus on 2020-03-29
Something went wrong removing those initrm.img files, but the packages supplying those old kernels have been removed. Some clever update-initramfs commands may fix it. Few people ever run that command manually. It's too late here for me to figure out the details now.

---

