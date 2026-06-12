---
title: "dpkg error (failed to write (No space left on device)"
date: 2017-05-23
forum: General Help
---

### Post by jaesun on 2017-05-23
Ubuntu 16.04.1 LTS (Welcome to Ubuntu 16.04.1 LTS (GNU/Linux 4.4.0-38-generic x86_64))

I was trying to install ZNC.  Something went wrong, and it wasn't installing.  It gave a message to "apt-get install -f"

I went to run this command:

```
/# apt-get install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-42 linux-headers-4.4.0-42-generic linux-headers-4.4.0-45 linux-headers-4.4.0-45-generic linux-headers-4.4.0-47 linux-headers-4.4.0-47-generic linux-headers-4.4.0-51
  linux-headers-4.4.0-51-generic linux-headers-4.4.0-53 linux-headers-4.4.0-53-generic linux-headers-4.4.0-57 linux-headers-4.4.0-57-generic linux-headers-4.4.0-59 linux-headers-4.4.0-59-generic
  linux-headers-4.4.0-62 linux-headers-4.4.0-62-generic linux-headers-4.4.0-66 linux-headers-4.4.0-66-generic linux-image-4.4.0-42-generic linux-image-4.4.0-45-generic linux-image-4.4.0-47-generic
  linux-image-4.4.0-51-generic linux-image-4.4.0-53-generic linux-image-4.4.0-57-generic linux-image-4.4.0-59-generic linux-image-4.4.0-62-generic linux-image-4.4.0-66-generic linux-image-4.4.0-78-generic
  linux-image-extra-4.4.0-42-generic linux-image-extra-4.4.0-45-generic linux-image-extra-4.4.0-47-generic linux-image-extra-4.4.0-51-generic linux-image-extra-4.4.0-53-generic
  linux-image-extra-4.4.0-57-generic linux-image-extra-4.4.0-59-generic linux-image-extra-4.4.0-62-generic linux-image-extra-4.4.0-66-generic linux-image-extra-4.4.0-78-generic
Use 'apt autoremove' to remove them.
The following additional packages will be installed:
  linux-image-4.4.0-66-generic linux-image-4.4.0-78-generic
Suggested packages:
  fdutils linux-doc-4.4.0 | linux-source-4.4.0 linux-tools
The following NEW packages will be installed:
  linux-image-4.4.0-66-generic linux-image-4.4.0-78-generic
0 upgraded, 2 newly installed, 0 to remove and 115 not upgraded.
36 not fully installed or removed.
Need to get 0 B/43.7 MB of archives.
After this operation, 133 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 464778 files and directories currently installed.)
Preparing to unpack .../linux-image-4.4.0-66-generic_4.4.0-66.87_amd64.deb ...
Done.
Unpacking linux-image-4.4.0-66-generic (4.4.0-66.87) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-4.4.0-66-generic_4.4.0-66.87_amd64.deb (--unpack):
 cannot copy extracted data for './boot/System.map-4.4.0-66-generic' to '/boot/System.map-4.4.0-66-generic.dpkg-new': failed to write (No space left on device)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-66-generic /boot/vmlinuz-4.4.0-66-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-66-generic /boot/vmlinuz-4.4.0-66-generic
Preparing to unpack .../linux-image-4.4.0-78-generic_4.4.0-78.99_amd64.deb ...
Done.
Unpacking linux-image-4.4.0-78-generic (4.4.0-78.99) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-4.4.0-78-generic_4.4.0-78.99_amd64.deb (--unpack):
 cannot copy extracted data for './boot/System.map-4.4.0-78-generic' to '/boot/System.map-4.4.0-78-generic.dpkg-new': failed to write (No space left on device)
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-78-generic /boot/vmlinuz-4.4.0-78-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-78-generic /boot/vmlinuz-4.4.0-78-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-4.4.0-66-generic_4.4.0-66.87_amd64.deb
 /var/cache/apt/archives/linux-image-4.4.0-78-generic_4.4.0-78.99_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Shows 2 errors:
> cannot copy extracted data for './boot/System.map-4.4.0-66-generic' to '/boot/System.map-4.4.0-66-generic.dpkg-new': failed to write (No space left on device)
cannot copy extracted data for './boot/System.map-4.4.0-78-generic' to '/boot/System.map-4.4.0-78-generic.dpkg-new': failed to write (No space left on device)

Googling, pretty much says to make sure I have space, or that I have enough INodes

But when I check disk space and INodes:

```
# df -Th
Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  7.8G     0  7.8G   0% /dev
tmpfs          tmpfs     1.6G  153M  1.5G  10% /run
/dev/md2       ext4      5.4T  4.9T  319G  94% /
tmpfs          tmpfs     7.8G     0  7.8G   0% /dev/shm
tmpfs          tmpfs     5.0M     0  5.0M   0% /run/lock
tmpfs          tmpfs     7.8G     0  7.8G   0% /sys/fs/cgroup
/dev/md1       ext3      488M  476M     0 100% /boot
tmpfs          tmpfs     1.6G     0  1.6G   0% /run/user/0
tmpfs          tmpfs     1.6G     0  1.6G   0% /run/user/1000
jaesun:/# df -i
Filesystem     Type     Inodes IUsed IFree IUse% Mounted on
udev           devtmpfs   2.0M   488  2.0M    1% /dev
tmpfs          tmpfs      2.0M   670  2.0M    1% /run
/dev/md2       ext4       175M  514K  174M    1% /
tmpfs          tmpfs      2.0M     1  2.0M    1% /dev/shm
tmpfs          tmpfs      2.0M    12  2.0M    1% /run/lock
tmpfs          tmpfs      2.0M    16  2.0M    1% /sys/fs/cgroup
/dev/md1       ext3       128K   349  128K    1% /boot
tmpfs          tmpfs      2.0M     4  2.0M    1% /run/user/0
tmpfs          tmpfs      2.0M     4  2.0M    1% /run/user/1000

```

Most of my space is used up, but it should be plenty of space (320GB free)

INodes is hardly being used (1% used on all)

So not sure where to go from here?  


Any help would be greatly appreciated

Edit 1:  I noticed in df -Th that the /boot is 100% full

I tried to run the command:

apt-get autoremove --purge

```
/# apt-get autoremove --purgeReading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-image-extra-4.4.0-66-generic : Depends: linux-image-4.4.0-66-generic but it is not installed
 linux-image-extra-4.4.0-78-generic : Depends: linux-image-4.4.0-78-generic but it is not installed
E: Unmet dependencies. Try using -f.
```

Of course, running apt-get -f install gives the above error.

Do I have to remove some of these packages from the /boot directory?  which ones can I remove?

```
# ls -l /boot
total 467M
-rw-r--r-- 1 root root 1.2M Sep  6  2016 abi-4.4.0-38-generic
-rw-r--r-- 1 root root 1.2M Oct  8  2016 abi-4.4.0-42-generic
-rw-r--r-- 1 root root 1.2M Oct 19  2016 abi-4.4.0-45-generic
-rw-r--r-- 1 root root 1.2M Oct 27  2016 abi-4.4.0-47-generic
-rw-r--r-- 1 root root 1.2M Nov 24 22:12 abi-4.4.0-51-generic
-rw-r--r-- 1 root root 1.2M Dec  2 20:11 abi-4.4.0-53-generic
-rw-r--r-- 1 root root 1.2M Dec 10 05:04 abi-4.4.0-57-generic
-rw-r--r-- 1 root root 1.2M Jan  7 01:44 abi-4.4.0-59-generic
-rw-r--r-- 1 root root 1.2M Jan 18 16:59 abi-4.4.0-62-generic
-rw-r--r-- 1 root root 1.2M Feb  1 20:39 abi-4.4.0-63-generic
-rw-r--r-- 1 root root 1.2M Feb 20 14:40 abi-4.4.0-64-generic
-rw-r--r-- 1 root root 186K Sep  6  2016 config-4.4.0-38-generic
-rw-r--r-- 1 root root 186K Oct  8  2016 config-4.4.0-42-generic
-rw-r--r-- 1 root root 186K Oct 19  2016 config-4.4.0-45-generic
-rw-r--r-- 1 root root 186K Oct 27  2016 config-4.4.0-47-generic
-rw-r--r-- 1 root root 186K Nov 24 22:12 config-4.4.0-51-generic
-rw-r--r-- 1 root root 186K Dec  2 20:11 config-4.4.0-53-generic
-rw-r--r-- 1 root root 186K Dec 10 05:04 config-4.4.0-57-generic
-rw-r--r-- 1 root root 186K Jan  7 01:44 config-4.4.0-59-generic
-rw-r--r-- 1 root root 186K Jan 18 16:59 config-4.4.0-62-generic
-rw-r--r-- 1 root root 186K Feb  1 20:39 config-4.4.0-63-generic
-rw-r--r-- 1 root root 186K Feb 20 14:40 config-4.4.0-64-generic
drwxr-xr-x 5 root root 1.0K Feb 21 11:29 grub
-rw-r--r-- 1 root root  34M Feb 10 13:24 initrd.img-4.4.0-38-generic
-rw-r--r-- 1 root root  34M Feb 10 13:24 initrd.img-4.4.0-42-generic
-rw-r--r-- 1 root root  34M Feb 10 13:24 initrd.img-4.4.0-45-generic
-rw-r--r-- 1 root root  34M Feb 10 13:23 initrd.img-4.4.0-47-generic
-rw-r--r-- 1 root root  34M Feb 10 13:23 initrd.img-4.4.0-51-generic
-rw-r--r-- 1 root root  34M Feb 10 13:23 initrd.img-4.4.0-53-generic
-rw-r--r-- 1 root root  34M Feb 10 13:23 initrd.img-4.4.0-57-generic
-rw-r--r-- 1 root root  34M Feb 10 13:22 initrd.img-4.4.0-59-generic
-rw-r--r-- 1 root root  34M Feb 10 13:22 initrd.img-4.4.0-62-generic
-rw-r--r-- 1 root root  34M Feb 21 11:29 initrd.img-4.4.0-63-generic
drwx------ 2 root root  12K Oct 19  2016 lost+found
-rw------- 1 root root 3.7M Sep  6  2016 System.map-4.4.0-38-generic
-rw------- 1 root root 3.7M Oct  8  2016 System.map-4.4.0-42-generic
-rw------- 1 root root 3.7M Oct 19  2016 System.map-4.4.0-45-generic
-rw------- 1 root root 3.7M Oct 27  2016 System.map-4.4.0-47-generic
-rw------- 1 root root 3.7M Nov 24 22:12 System.map-4.4.0-51-generic
-rw------- 1 root root 3.7M Dec  2 20:11 System.map-4.4.0-53-generic
-rw------- 1 root root 3.7M Dec 10 05:04 System.map-4.4.0-57-generic
-rw------- 1 root root 3.7M Jan  7 01:44 System.map-4.4.0-59-generic
-rw------- 1 root root 3.7M Jan 18 16:59 System.map-4.4.0-62-generic
-rw------- 1 root root 3.8M Feb  1 20:39 System.map-4.4.0-63-generic
-rw------- 1 root root 3.8M Feb 20 14:40 System.map-4.4.0-64-generic
-rw------- 1 root root 6.8M Sep  6  2016 vmlinuz-4.4.0-38-generic
-rw------- 1 root root 6.8M Oct  8  2016 vmlinuz-4.4.0-42-generic
-rw------- 1 root root 6.8M Oct 19  2016 vmlinuz-4.4.0-45-generic
-rw------- 1 root root 6.8M Oct 27  2016 vmlinuz-4.4.0-47-generic
-rw------- 1 root root 6.8M Nov 24 22:12 vmlinuz-4.4.0-51-generic
-rw------- 1 root root 6.8M Dec  2 20:11 vmlinuz-4.4.0-53-generic
-rw------- 1 root root 6.8M Dec 10 05:04 vmlinuz-4.4.0-57-generic
-rw------- 1 root root 6.8M Jan  7 01:44 vmlinuz-4.4.0-59-generic
-rw------- 1 root root 6.8M Jan 18 16:59 vmlinuz-4.4.0-62-generic
-rw------- 1 root root 6.8M Feb  1 20:39 vmlinuz-4.4.0-63-generic
-rw------- 1 root root 6.8M Feb 20 14:40 vmlinuz-4.4.0-64-generic
```

---

### Post by oldfred on 2017-05-23
Most desktops do not need separate /boot partition. If using LVM or full drive encryption you normally have a /boot and the /boot full issue.
If /boot is folder inside / (root) then all available space is shared. You still should regularly houseclean.
And issue has been fixed in 16.04, if some settings are correct. For me it has just worked.

       [https://ubuntuforums.org/showthread.php?t=2361761](https://ubuntuforums.org/showthread.php?t=2361761)
/boot full or Not enough disk space on updates
[http://ubuntuforums.org/showthread.php?t=2308938&p=13418808#post13418808](http://ubuntuforums.org/showthread.php?t=2308938&p=13418808#post13418808)
[https://help.ubuntu.com/community/RemoveOldKernels](https://help.ubuntu.com/community/RemoveOldKernels)
Check current kernel I also keep one older just in case:
#Current kernel:
uname -a
# kernels, shows older also?
dpkg --list | grep linux-image
-s is simulate so you can see what it will do
sudo apt-get -s autoremove
# 
            I prefer synatic and keeping 2 kernels, current and one known working older on. 
 In synaptic search for linux-image to choose to delete old ones
Using synaptic
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521) 


You may just have to manually delete the older kernel. Just to make space for dpkg to work to delete the other old kernels.
But I might reinstall that one kernel you manual deleted, and properly delete, so all the related files and some files in other locations also get correctly purged.

Generally this is the rule.
Only use rm on files not in dpkg

---

### Post by Bashing-om on 2017-05-24
jinja'd by oldfred :)

---

