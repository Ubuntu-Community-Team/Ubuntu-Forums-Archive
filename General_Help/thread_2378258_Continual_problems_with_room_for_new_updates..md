---
title: "Continual problems with room for new updates."
date: 2017-11-21
forum: General Help
---

### Post by grey1beard on 2017-11-21
Since about April , whenever Software updater produces a new Linux build(if that's the correct term), usually about 70Mb, my 14.04 version tells me that there is not enough room to install it.

This never occurred last year, and as far as I am aware, I have not installed any major packages that would give rise to this problem.

When I follow the help I was given back in the spring, of manually cleaning out various appropriate files of previous builds, all proceeds ok for perhaps one or two more downloads, then I have to manually remove old builds once again.

Should the removal of previous builds occur automagically, and have I lost some crucial software that enables this to happen, or is this behaviour the new (?)  'normal' ?

John

---

### Post by howefield on 2017-11-21
Running the command

```
sudo apt-get autoremove
```

periodically should keep the boot partition from filling up to the point of being a problem.

---

### Post by QIII on 2017-11-21
Hello!

Just as a bit of background --

Removing packages and their components "manually" is not a particularly good idea.  The package manager should be used so that it is able to keep track of what has been happening.  If you remove things manually, the package manager may fail because it has no idea what you have done.

Another thing to consider is that the amount of space on a drive may appear sufficient, but the inodes table may be filled with a huge number of tiny files.  If the inodes are all spoken for, no amount of "disk space available" is of any consequence.  Files cannot be added because the inode table is full.

This sort of thing happens quite often in / if things like kernel headers are not removed, either automatically or as described above using autoremove.  16.04 does take care of this automagically when the kernel is updated.  Like Fedora has done for some time now, updating the kernel clears up old ones and leaves you with the current and previous kernel (as a fall-back).

Cheers!

---

### Post by grey1beard on 2017-11-21
Thanks.
I've run autoremove as per above, and Terminal shows this -

[sudo] password for john: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 to upgrade, 0 to newly install, 0 to remove and 17 not to upgrade.

I suspect the '17 not to upgrade' may be the collection of headers etc, that I have been manually removing on previous occasions, so it looks as though I'm stuck with it, unless or until I upgrade to 16.04.

---

### Post by ajgreeny on 2017-11-21
Let's see the output of ```
dpkg -l linux-image* linux-headers*
``` in terminal please, followed one at a time by ```
df -hT
df -i
```
This will tell us exactly what kernels and header packages are installed and also how much space and how many inodes are available for the system.

Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by grey1beard on 2017-11-22
Thanks for your help.
John

```

john@john-RM:~$ dpkg -l linux-image* linux-headers*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
un  linux-headers  <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
ii  linux-headers- 4.4.0-101.12 all          Header files related to Linux ker
ii  linux-headers- 4.4.0-101.12 i386         Linux kernel headers for version 
pi  linux-headers- 4.4.0-66.87~ all          Header files related to Linux ker
ii  linux-headers- 4.4.0-66.87~ i386         Linux kernel headers for version 
pi  linux-headers- 4.4.0-67.88~ all          Header files related to Linux ker
ii  linux-headers- 4.4.0-67.88~ i386         Linux kernel headers for version 
pi  linux-headers- 4.4.0-70.91~ all          Header files related to Linux ker
ii  linux-headers- 4.4.0-70.91~ i386         Linux kernel headers for version 
pi  linux-headers- 4.4.0-72.93~ all          Header files related to Linux ker
ii  linux-headers- 4.4.0-72.93~ i386         Linux kernel headers for version 
pi  linux-headers- 4.4.0-79.100 all          Header files related to Linux ker
ii  linux-headers- 4.4.0-79.100 i386         Linux kernel headers for version 
ii  linux-headers- 4.4.0-89.112 all          Header files related to Linux ker
ii  linux-headers- 4.4.0-89.112 i386         Linux kernel headers for version 
ii  linux-headers- 4.4.0-92.115 all          Header files related to Linux ker
ii  linux-headers- 4.4.0-92.115 i386         Linux kernel headers for version 
ii  linux-headers- 4.4.0-93.116 all          Header files related to Linux ker
ii  linux-headers- 4.4.0-93.116 i386         Linux kernel headers for version 
ii  linux-headers- 4.4.0-96.119 all          Header files related to Linux ker
ii  linux-headers- 4.4.0-96.119 i386         Linux kernel headers for version 
ii  linux-headers- 4.4.0-97.120 all          Header files related to Linux ker
ii  linux-headers- 4.4.0-97.120 i386         Linux kernel headers for version 
ii  linux-headers- 4.4.0-98.121 all          Header files related to Linux ker
ii  linux-headers- 4.4.0-98.121 i386         Linux kernel headers for version 
ii  linux-headers- 4.4.0.101.84 i386         Generic Linux kernel headers
un  linux-image    <none>       <none>       (no description available)
iF  linux-image-4. 4.4.0-101.12 i386         Linux kernel image for version 4.
pi  linux-image-4. 4.4.0-89.112 i386         Linux kernel image for version 4.
pi  linux-image-4. 4.4.0-92.115 i386         Linux kernel image for version 4.
pi  linux-image-4. 4.4.0-93.116 i386         Linux kernel image for version 4.
pi  linux-image-4. 4.4.0-96.119 i386         Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-97.120 i386         Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-98.121 i386         Linux kernel image for version 4.
iU  linux-image-ex 4.4.0-101.12 i386         Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-89.112 i386         Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-92.115 i386         Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-93.116 i386         Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-96.119 i386         Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-97.120 i386         Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-98.121 i386         Linux kernel extra modules for ve
iU  linux-image-ge 4.4.0.101.84 i386         Generic Linux kernel image

```

```

john@john-RM:~$ df -hT
Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  1.4G  4.0K  1.4G   1% /dev
tmpfs          tmpfs     289M  1.4M  288M   1% /run
/dev/dm-0      ext4      144G   43G   94G  32% /
none           tmpfs     4.0K     0  4.0K   0% /sys/fs/cgroup
none           tmpfs     5.0M     0  5.0M   0% /run/lock
none           tmpfs     1.5G   23M  1.4G   2% /run/shm
none           tmpfs     100M   72K  100M   1% /run/user
/dev/sda1      ext2      236M  219M  5.2M  98% /boot

```
```

john@john-RM:~$ df -i
Filesystem      Inodes  IUsed   IFree IUse% Mounted on
udev            211327    516  210811    1% /dev
tmpfs           217119    577  216542    1% /run
/dev/dm-0      9568256 575486 8992770    7% /
none            217119      2  217117    1% /sys/fs/cgroup
none            217119      4  217115    1% /run/lock
none            217119     22  217097    1% /run/shm
none            217119     33  217086    1% /run/user
/dev/sda1        62248    332   61916    1% /boot

```

---

### Post by ajgreeny on 2017-11-22
OK, as you can see from this bottom line of the df -hT output your /boot partition is almost completely full meaning there is no room for any further kernel installation ```
/dev/sda1      ext2      236M  219M  5.2M  98% /boot
```
That also means that the command suggested by by howefield in post #2 will not work as that needs some headroom.

I now thing the quickest way I know of to repair this situation is using **dpkg** to remove a couple of kernels and their associated packages and then try the autoremove command once more.

So let's start with ```
sudo dpkg -P linux-image-extra-4.4.0-{89,92,93}-generic
``` to see if that works and we can move on from there.
Any of the linux-headers packages that are no longer needed should be removed by the autoremove command shown above, but let's move one step at a time.

---

### Post by grey1beard on 2017-11-22
Re-run df -hT
```

john@john-RM:~$ df -hT
Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  1.4G   12K  1.4G   1% /dev
tmpfs          tmpfs     289M  1.4M  288M   1% /run
/dev/dm-0      ext4      144G   43G   95G  31% /
none           tmpfs     4.0K     0  4.0K   0% /sys/fs/cgroup
none           tmpfs     5.0M     0  5.0M   0% /run/lock
none           tmpfs     1.5G   23M  1.4G   2% /run/shm
none           tmpfs     100M   72K  100M   1% /run/user
/dev/sda1      ext2      236M  183M   41M  82% /boot

```
John

---

### Post by ajgreeny on 2017-11-22
Have you run the **sudo apt autoremove** command again?  If not do so now and hopefully it will remove other unneeded kernels and packages.

If that is successful run a system upgrade with ```
sudo apt update
sudo apt full-upgrade
``` which will finish the installation of kernel 4.4.0-101 which is installed at the moment but not fully configured and therefore not being used.  To check this run command ```
uname -a
``` which I imagine will show 4.4.0-98 at the moment.

---

### Post by grey1beard on 2017-11-22
I've carried out those operations, and just run uname -a, which shows 4.4.0-98, then df -hT
```

Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  1.4G   12K  1.4G   1% /dev
tmpfs          tmpfs     289M  1.4M  288M   1% /run
/dev/dm-0      ext4      144G   43G   95G  31% /
none           tmpfs     4.0K     0  4.0K   0% /sys/fs/cgroup
none           tmpfs     5.0M     0  5.0M   0% /run/lock
none           tmpfs     1.5G   23M  1.4G   2% /run/shm
none           tmpfs     100M   80K  100M   1% /run/user
/dev/sda1      ext2      236M  205M   20M  92% /boot

```

John

---

### Post by ajgreeny on 2017-11-22
OK, so now show us the output of the ```
sudo apt autoremove
``` command as it looks as if it is not doing what it should be, ie removing a lot more kernel packages and releasing more space.

Have you manually removed any files from the /boot partition using **sudo rm /boot/filename**, or even using the file manager with root permissions?

---

### Post by Yellow Pasque on 2017-11-22
> **ajgreeny said:**
> Have you manually removed any files from the /boot partition using **sudo rm /boot/filename**, or even using the file manager with root permissions?

Don't do that. Remove/purge the corresponding packages. IIRC, autoremove won't take out old kernels.

---

### Post by grey1beard on 2017-11-22
Er....
```

john@john-RM:~$ sudo apt autoremove
[sudo] password for john: 
E: Invalid operation autoremove
john@john-RM:~$
 
```

No, I haven't performed any manual removal along the lines you ask.
Inthe past, I've only used the method posted in an earlier post, similar to **sudo dpkg -P linux-image-extra-4.4.0-{89,92,93}-generic**

---

### Post by ajgreeny on 2017-11-23
Ah!  I have just noticed that you are using 14.04; I thought you were using 16.04 from the kernel versions listed, so my apologies for the **sudo apt autoremove** command, which I think may need to be ```
sudo apt-get autoremove
``` in 14.04.

Try that and again report back here the output from the command.

And as Temüjin said above **never remove anything from the /boot folder or partition manually; always use the package manager or apt/dpkg commands.**

---

### Post by Yellow Pasque on 2017-11-23
> Ah! I have just noticed that you are using 14.04; I thought you were using 16.04

Good catch. I believe we are looking at this issue, which was fixed in 16.04: [https://bugs.launchpad.net/ubuntu/+source/unattended-upgrades/+bug/1357093](https://bugs.launchpad.net/ubuntu/+source/unattended-upgrades/+bug/1357093)

EDIT: Also see this (as bug report suggests) to set up automatic removal in the future: [https://help.ubuntu.com/community/RemoveOldKernels](https://help.ubuntu.com/community/RemoveOldKernels)

---

### Post by grey1beard on 2017-11-23
As per request
```

john@john-RM:~$ sudo apt-get autoremove
[sudo] password for john: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
john@john-RM:~$ 

```

---

### Post by grey1beard on 2017-11-23
Temujin - thanks for that link.
Even a cursory read shows me that that contains the probable answer to my op.
Tied up with Thanksgiving activity, so I'll look at it again later.
So, Happy Thanksgiving to all.
John

---

### Post by ajgreeny on 2017-11-25
When you get back to this thread it will be useful to see once more the output of the command ```
dpkg -l linux-image* linux-headers*
``` as your last output from the ```
df -hT
``` command showed an unexpectedly high use if you have only two kernels installed and the autoremove command had done its job.

---

### Post by grey1beard on 2017-11-25
Back again.
```

john@john-RM:~$ dpkg -l linux-image* linux-headers*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
un  linux-headers  <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
ii  linux-headers- 4.4.0-101.12 all          Header files related to Linux ker
ii  linux-headers- 4.4.0-101.12 i386         Linux kernel headers for version 
pi  linux-headers- 4.4.0-66.87~ all          Header files related to Linux ker
ii  linux-headers- 4.4.0-66.87~ i386         Linux kernel headers for version 
pi  linux-headers- 4.4.0-67.88~ all          Header files related to Linux ker
ii  linux-headers- 4.4.0-67.88~ i386         Linux kernel headers for version 
pi  linux-headers- 4.4.0-70.91~ all          Header files related to Linux ker
ii  linux-headers- 4.4.0-70.91~ i386         Linux kernel headers for version 
pi  linux-headers- 4.4.0-72.93~ all          Header files related to Linux ker
ii  linux-headers- 4.4.0-72.93~ i386         Linux kernel headers for version 
pi  linux-headers- 4.4.0-79.100 all          Header files related to Linux ker
ii  linux-headers- 4.4.0-79.100 i386         Linux kernel headers for version 
ii  linux-headers- 4.4.0-89.112 all          Header files related to Linux ker
ii  linux-headers- 4.4.0-89.112 i386         Linux kernel headers for version 
ii  linux-headers- 4.4.0-92.115 all          Header files related to Linux ker
ii  linux-headers- 4.4.0-92.115 i386         Linux kernel headers for version 
ii  linux-headers- 4.4.0-93.116 all          Header files related to Linux ker
ii  linux-headers- 4.4.0-93.116 i386         Linux kernel headers for version 
ii  linux-headers- 4.4.0-96.119 all          Header files related to Linux ker
ii  linux-headers- 4.4.0-96.119 i386         Linux kernel headers for version 
ii  linux-headers- 4.4.0-97.120 all          Header files related to Linux ker
ii  linux-headers- 4.4.0-97.120 i386         Linux kernel headers for version 
ii  linux-headers- 4.4.0-98.121 all          Header files related to Linux ker
ii  linux-headers- 4.4.0-98.121 i386         Linux kernel headers for version 
ii  linux-headers- 4.4.0.101.84 i386         Generic Linux kernel headers
un  linux-image    <none>       <none>       (no description available)
ii  linux-image-4. 4.4.0-101.12 i386         Linux kernel image for version 4.
pi  linux-image-4. 4.4.0-89.112 i386         Linux kernel image for version 4.
pi  linux-image-4. 4.4.0-92.115 i386         Linux kernel image for version 4.
pi  linux-image-4. 4.4.0-93.116 i386         Linux kernel image for version 4.
pi  linux-image-4. 4.4.0-96.119 i386         Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-97.120 i386         Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-98.121 i386         Linux kernel image for version 4.
ii  linux-image-ex 4.4.0-101.12 i386         Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-96.119 i386         Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-97.120 i386         Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-98.121 i386         Linux kernel extra modules for ve
ii  linux-image-ge 4.4.0.101.84 i386         Generic Linux kernel image
john@john-RM:~$ 

```

John
This is showing what I've found each time I've had to clear out old packages myself, and I thought that the .66 and .72 builds had gone, but not so, apparently.

---

### Post by ajgreeny on 2017-11-25
Something has certainly gone astray here as there are far too may packages still sitting on your system.

I am reading this on a small Android screen which I find difficult to work on so give me some time to get back to a propper computer and I will see what next to suggest.

---

### Post by Yellow Pasque on 2017-11-25
So what have you tried since the last time I posted? It is unclear what you did, if anything.
See: [https://help.ubuntu.com/community/RemoveOldKernels#Safely_Removing_Old_Kernels](https://help.ubuntu.com/community/RemoveOldKernels#Safely_Removing_Old_Kernels)

> This is showing what I've found each time I've had to clear out old packages myself, and I thought that the .66 and .72 builds had gone, but not so, apparently. 
The -headers remain, but it looks like you removed the images. I would not be too concerned about headers at the moment since they're not using space on /boot partition.
Also, it looks like the install of the latest kernel has succeeded/finished, as opposed to the earlier output you gave which listed the 4.4.0-102 packages as half-installed or unpacked.

---

### Post by Yellow Pasque on 2017-11-25
I'm also curious what happens if you run:
```
sudo dpkg --configure -a
```

---

### Post by grey1beard on 2017-12-08
Hi Temujin.
Just getting back to where I was a couple of weeks ago, and had to re-read the last few posts to catch up.
The current state of play is that once again I'm getting the not enough room message, which is what gave me a heads up on the unresolved problem.
Just for immediate info, I ran **sudo dpkg --configure -a** and after entering my password, nothing happened.

---

### Post by ian-weisser on 2017-12-08
Can you please show us the current output of:
```
dkpg -l linux-image-*
ls -l /boot
uname -r
uptime
```

Let's check how many kernels your /boot is holding (should be 4)
Let's check that your metapackages are current
Let's cross-check those installed kernels against /boot and see if there are any orphaned space hogs in there
Let's check which kernel you are using. A common reason for autoremove to fail is that newer kernels than currently-running are ineligble for autoremove.

---

### Post by grey1beard on 2017-12-09
```
john@john-RM:~$ dpkg -l linux-image-*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  linux-image-4. 4.4.0-101.12 i386         Linux kernel image for version 4.
pi  linux-image-4. 4.4.0-89.112 i386         Linux kernel image for version 4.
pi  linux-image-4. 4.4.0-92.115 i386         Linux kernel image for version 4.
pi  linux-image-4. 4.4.0-93.116 i386         Linux kernel image for version 4.
pi  linux-image-4. 4.4.0-96.119 i386         Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-97.120 i386         Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-98.121 i386         Linux kernel image for version 4.
ii  linux-image-ex 4.4.0-101.12 i386         Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-96.119 i386         Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-97.120 i386         Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-98.121 i386         Linux kernel extra modules for ve
ii  linux-image-ge 4.4.0.101.84 i386         Generic Linux kernel image

```
```

john@john-RM:~$ ls -l /boot
total 200097
-rw-r--r-- 1 root root  1243428 Nov 10 14:54 abi-4.4.0-101-generic
-rw-r--r-- 1 root root  1242941 Aug  1 18:52 abi-4.4.0-89-generic
-rw-r--r-- 1 root root  1242941 Aug 10 11:15 abi-4.4.0-92-generic
-rw-r--r-- 1 root root  1243375 Aug 14 13:01 abi-4.4.0-93-generic
-rw-r--r-- 1 root root  1243375 Sep 13 05:49 abi-4.4.0-96-generic
-rw-r--r-- 1 root root  1243326 Sep 20 12:19 abi-4.4.0-97-generic
-rw-r--r-- 1 root root  1243451 Oct 11 09:07 abi-4.4.0-98-generic
-rw-r--r-- 1 root root   193853 Nov 10 14:54 config-4.4.0-101-generic
-rw-r--r-- 1 root root   193759 Aug  1 18:52 config-4.4.0-89-generic
-rw-r--r-- 1 root root   193759 Aug 10 11:15 config-4.4.0-92-generic
-rw-r--r-- 1 root root   193759 Aug 14 13:01 config-4.4.0-93-generic
-rw-r--r-- 1 root root   193851 Sep 13 05:49 config-4.4.0-96-generic
-rw-r--r-- 1 root root   193851 Sep 20 12:19 config-4.4.0-97-generic
-rw-r--r-- 1 root root   193851 Oct 11 09:07 config-4.4.0-98-generic
drwxr-xr-x 5 root root     1024 Nov 22 13:18 grub
-rw-r--r-- 1 root root 22708338 Dec  7 10:06 initrd.img-4.4.0-101-generic
-rw-r--r-- 1 root root  3311013 Dec  7 10:08 initrd.img-4.4.0-31-generic
-rw-r--r-- 1 root root 10192504 Dec  7 10:08 initrd.img-4.4.0-89-generic
-rw-r--r-- 1 root root 10192865 Dec  7 10:08 initrd.img-4.4.0-92-generic
-rw-r--r-- 1 root root 10192332 Dec  7 10:08 initrd.img-4.4.0-93-generic
-rw-r--r-- 1 root root 22706851 Dec  7 10:08 initrd.img-4.4.0-96-generic
-rw-r--r-- 1 root root 22707339 Dec  7 10:07 initrd.img-4.4.0-97-generic
-rw-r--r-- 1 root root 22708973 Dec  7 10:07 initrd.img-4.4.0-98-generic
drwx------ 2 root root    12288 Dec 23  2016 lost+found
-rw-r--r-- 1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r-- 1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r-- 1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw------- 1 root root  3114808 Nov 10 14:54 System.map-4.4.0-101-generic
-rw------- 1 root root  3112411 Aug  1 18:52 System.map-4.4.0-89-generic
-rw------- 1 root root  3112411 Aug 10 11:15 System.map-4.4.0-92-generic
-rw------- 1 root root  3113202 Aug 14 13:01 System.map-4.4.0-93-generic
-rw------- 1 root root  3113981 Sep 13 05:49 System.map-4.4.0-96-generic
-rw------- 1 root root  3113972 Sep 20 12:19 System.map-4.4.0-97-generic
-rw------- 1 root root  3114664 Oct 11 09:07 System.map-4.4.0-98-generic
-rw------- 1 root root  6706880 Nov 10 14:54 vmlinuz-4.4.0-101-generic
-rw------- 1 root root  6698864 Aug  1 18:52 vmlinuz-4.4.0-89-generic
-rw------- 1 root root  6700576 Aug 10 11:15 vmlinuz-4.4.0-92-generic
-rw------- 1 root root  6701792 Aug 14 13:01 vmlinuz-4.4.0-93-generic
-rw------- 1 root root  6703360 Sep 13 05:49 vmlinuz-4.4.0-96-generic
-rw------- 1 root root  6703776 Sep 20 12:19 vmlinuz-4.4.0-97-generic
-rw------- 1 root root  6705152 Oct 11 09:07 vmlinuz-4.4.0-98-generic
john@john-RM:~$ 

```

```
john@john-RM:~$ uname -r
4.4.0-101-generic
```

```
john@john-RM:~$ uptime
 15:10:32 up  1:07,  2 users,  load average: 0.19, 0.26, 0.32
```

---

### Post by Yellow Pasque on 2017-12-09
If I give you this a third time, maybe it will be the charm? [https://help.ubuntu.com/community/RemoveOldKernels#Safely_Removing_Old_Kernels](https://help.ubuntu.com/community/RemoveOldKernels#Safely_Removing_Old_Kernels)
If you read it and don't understand, ask for clarification.

---

### Post by ian-weisser on 2017-12-09
> **grey1beard said:**
> ```
john@john-RM:~$ dpkg -l linux-image-*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  linux-image-4. 4.4.0-101.12 i386         Linux kernel image for version 4.
pi  linux-image-4. 4.4.0-89.112 i386         Linux kernel image for version 4.
pi  linux-image-4. 4.4.0-92.115 i386         Linux kernel image for version 4.
pi  linux-image-4. 4.4.0-93.116 i386         Linux kernel image for version 4.
pi  linux-image-4. 4.4.0-96.119 i386         Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-97.120 i386         Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-98.121 i386         Linux kernel image for version 4.
ii  linux-image-ex 4.4.0-101.12 i386         Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-96.119 i386         Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-97.120 i386         Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-98.121 i386         Linux kernel extra modules for ve
ii  linux-image-ge 4.4.0.101.84 i386         Generic Linux kernel image

```

Oh, I think I see part of the problem.
See those kernels marked 'pi"?
You marked them to be removed...but you didn't actually remove them.

Here's one possibility why: The corresponding linux-image-extra-xx package wasn't marked for removal.

Try this.
```
sudo dpkg --purge linux-image-4.4.0-96.119-generic linux-image-extra-4.4.0-96.119-generic 
```

If it works, then shift to apt:
```
sudo apt-get autoremove
```

Then update your kernel metapackage which is stuck at the wrong version:
```
sudo apt-get clean linux-image-generic linux-image-extra-generic
sudo apt-get install --reinstall linux-image-generic linux-image-extra-generic
```

The see if  dpkg -l linux-image-* has changed


[EDIT:] Changed 'apt' to 'apt-get', since the OP is using 14.04. Future readers using 16.04 and newer can use 'apt'

---

### Post by Yellow Pasque on 2017-12-09
> Here's one possibility why: The corresponding linux-image-extra-xx package wasn't marked for removal.
Ironically, You need space in /boot to purge the packages. For example, see: [https://askubuntu.com/questions/898499/why-there-is-an-update-initramfs-error-when-removing-a-kernel-by-dpkg](https://askubuntu.com/questions/898499/why-there-is-an-update-initramfs-error-when-removing-a-kernel-by-dpkg)
That's why you have to run the update-initramfs -d command(s) manually - to free up enough space to allow apt to install/purge kernels

I guess I should be more explicit with my suggestion:
```
sudo update-initramfs -d -k 4.4.0-89-generic
sudo update-initramfs -d -k 4.4.0-92-generic
sudo update-initramfs -d -k 4.4.0-93-generic
sudo update-initramfs -d -k 4.4.0-96-generic
```

EDIT: After that, you should be able to purge the corresponding image and image-extra packages as suggested.

---

### Post by grey1beard on 2017-12-10
First, my apologies to all helping me. For reasons I don't understand, my option 'notify me instantly by email' isn't working.
Not had this happen before, so I've been unaware of the help being offered.

After breakfast, I'll come back and see what progress I can make.
Thanks everyone for your forbearance.
John

---

### Post by grey1beard on 2017-12-10
Progress.

I used the** sudo update-initramfs -d -k 4.4.0-#-generic** code for each [89,92,93,96] in turn.
Then ran **sudo dpkg --purge linux-image-4.4.0-#-generic linux-image-extra-4.4.0-#-generic** for each in turn.

But then **sudo apt autoremove** gave me an error - *autoremove invalid operation*

Typo ?

---

### Post by Holger_Gehrke on 2017-12-10
> **grey1beard said:**
> 
But then **sudo apt autoremove** gave me an error - *autoremove invalid operation*

Typo ?

No, more likely an operation which hadn't yet been put into apt in 14.04. Try 'sudo apt**-get** autoremove'.

Holger

---

### Post by grey1beard on 2017-12-10
Thanks, Holger, that worked, even though it tells me there's nothing to install remove or upgrade !
At least it processed the command.
John

---

### Post by grey1beard on 2017-12-10
Current position -

```
john@john-RM:~$ dpkg -l linux-image-*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                    Version          Architecture     Description
+++-=======================-================-================-===================================================
ii  linux-image-4.4.0-101-g 4.4.0-101.124~14 i386             Linux kernel image for version 4.4.0 on 32 bit x86 
ii  linux-image-4.4.0-103-g 4.4.0-103.126~14 i386             Linux kernel image for version 4.4.0 on 32 bit x86 
ii  linux-image-4.4.0-97-ge 4.4.0-97.120~14. i386             Linux kernel image for version 4.4.0 on 32 bit x86 
ii  linux-image-4.4.0-98-ge 4.4.0-98.121~14. i386             Linux kernel image for version 4.4.0 on 32 bit x86 
ii  linux-image-extra-4.4.0 4.4.0-101.124~14 i386             Linux kernel extra modules for version 4.4.0 on 32 
ii  linux-image-extra-4.4.0 4.4.0-103.126~14 i386             Linux kernel extra modules for version 4.4.0 on 32 
ii  linux-image-extra-4.4.0 4.4.0-97.120~14. i386             Linux kernel extra modules for version 4.4.0 on 32 
ii  linux-image-extra-4.4.0 4.4.0-98.121~14. i386             Linux kernel extra modules for version 4.4.0 on 32 
ii  linux-image-generic-lts 4.4.0.103.86     i386             Generic Linux kernel image
```

So I'm tempted to remove .97 and .98, both* image *and *image-extra* to keep ahead, but I assume that there is more work to be done in order to avoid this situation in the future ?

---

### Post by Yellow Pasque on 2017-12-10
Yes, you can remove the 97 and 98 kernels, unless you want to keep more than the latest two kernels. Hopefully, you can now just use apt/dpkg and not have to bother with initramfs command(s).

>  but I assume that there is more work to be done in order to avoid this situation in the future ? 

[https://help.ubuntu.com/community/RemoveOldKernels#Enable_Unattended_Upgrades_.28Ubuntu_14.04.29](https://help.ubuntu.com/community/RemoveOldKernels#Enable_Unattended_Upgrades_.28Ubuntu_14.04.29)

---

### Post by grey1beard on 2017-12-10
Grateful thanks for that last link, as well as all the other help.
John

---

