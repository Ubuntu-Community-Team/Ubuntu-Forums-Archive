---
title: "Broken package catalgue on 12.10"
date: 2013-03-30
forum: General Help
---

### Post by damagu on 2013-03-30
Hi all, 

I have run into a problem with Software Center where I get a message saying "Items cannot be installed or removed until the package catalogue is repaired". I click on the repair button and I then get the following error "Package operation failed" with the details as follows:

    ```
installArchives() failed: (Reading database ...  
    (Reading database ... 5%
    (Reading database ... 10%
    (Reading database ... 15%
    (Reading database ... 20%
    (Reading database ... 25%
    (Reading database ... 30%
    (Reading database ... 35%
    (Reading database ... 40%
    (Reading database ... 45%
    (Reading database ... 50%
    (Reading database ... 55%
    (Reading database ... 60%
    (Reading database ... 65%
    (Reading database ... 70%
    (Reading database ... 75%
    (Reading database ... 80%
    (Reading database ... 85%
    (Reading database ... 90%
    (Reading database ... 95%
    (Reading database ... 100%
    (Reading database ... 201900 files and directories currently installed.)
    Unpacking linux-headers-3.5.0-26-generic (from .../linux-headers-3.5.0-26-generic_3.5.0-26.42_i386.deb) ...
    dpkg: error processing /var/cache/apt/archives/linux-headers-3.5.0-26-generic_3.5.0-26.42_i386.deb (--unpack):
     unable to create `/usr/src/linux-headers-3.5.0-26-generic/include/config/net/vendor/seeq.h.dpkg-new' (while processing `./usr/src/linux-headers-3.5.0-26-generic/include/config/net/vendor/seeq.h'): No space left on device
    No apport report written because MaxReports is reached already
    dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
    Errors were encountered while processing:
     /var/cache/apt/archives/linux-headers-3.5.0-26-generic_3.5.0-26.42_i386.deb
    Error in function:
    dpkg: dependency problems prevent configuration of linux-headers-generic:
     linux-headers-generic depends on linux-headers-3.5.0-26-generic; however:
      Package linux-headers-3.5.0-26-generic is not installed.
     
    dpkg: error processing linux-headers-generic (--configure):
     dependency problems - leaving unconfigured
    dpkg: dependency problems prevent configuration of linux-headers-generic-pae:
     linux-headers-generic-pae depends on linux-headers-generic; however:
      Package linux-headers-generic is not configured yet.
     
    dpkg: error processing linux-headers-generic-pae (--configure):
     dependency problems - leaving unconfigured
    dpkg: dependency problems prevent configuration of linux-generic:
     linux-generic depends on linux-headers-generic; however:
      Package linux-headers-generic is not configured yet.
     
    dpkg: error processing linux-generic (--configure):
     dependency problems - leaving unconfigured

```

I saw the "no space left on device" part and checked that I do have plenty of space:

```
Notebook-PC:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       9.2G  5.7G  3.1G  65% /
udev            801M  4.0K  801M   1% /dev
tmpfs           324M  844K  323M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            809M  152K  808M   1% /run/shm
none            100M   20K  100M   1% /run/user
/dev/sda5       276G  110G  152G  43% /home

```

I thought it might be something to do with old kernel images filling /boot which I've had before but I'm pretty sure that only applies if you have /boot on its own partition which I did have in the past but not on this particular machine. 

I tried doing this:

```
Notebook-PC:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree      
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-headers-generic : Depends: linux-headers-3.5.0-26-generic but it is not installed
E: Unmet dependencies. Try using -f.
```

I then tried
 ```

Notebook-PC:~$ sudo apt-get -f autoremove
Reading package lists... Done
Building dependency tree      
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-headers-3.5.0-26-generic
The following packages will be REMOVED:
  linux-headers-3.5.0-17 linux-headers-3.5.0-17-generic
The following NEW packages will be installed:
  linux-headers-3.5.0-26-generic
0 upgraded, 1 newly installed, 2 to remove and 47 not upgraded.
3 not fully installed or removed.
Need to get 0 B/950 kB of archives.
After this operation, 58.6 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 201900 files and directories currently installed.)
Unpacking linux-headers-3.5.0-26-generic (from .../linux-headers-3.5.0-26-generic_3.5.0-26.42_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.5.0-26-generic_3.5.0-26.42_i386.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.5.0-26-generic/include/config/net/vendor/seeq.h.dpkg-new' (while processing `./usr/src/linux-headers-3.5.0-26-generic/include/config/net/vendor/seeq.h'): No space left on device
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-3.5.0-26-generic_3.5.0-26.42_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I also tried:

```
Notebook-PC:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree      
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.5.0-17 linux-headers-3.5.0-17-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-headers-3.5.0-26-generic
The following NEW packages will be installed:
  linux-headers-3.5.0-26-generic
0 upgraded, 1 newly installed, 0 to remove and 47 not upgraded.
3 not fully installed or removed.
Need to get 0 B/950 kB of archives.
After this operation, 11.2 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 201900 files and directories currently installed.)
Unpacking linux-headers-3.5.0-26-generic (from .../linux-headers-3.5.0-26-generic_3.5.0-26.42_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.5.0-26-generic_3.5.0-26.42_i386.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.5.0-26-generic/include/config/net/vendor/seeq.h.dpkg-new' (while processing `./usr/src/linux-headers-3.5.0-26-generic/include/config/net/vendor/seeq.h'): No space left on device
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-3.5.0-26-generic_3.5.0-26.42_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

So I seem to have unmet dependencies but I can't install them because it seems to think I have no space even though I do and I can't remove the packages with unmet dependencies either.   

I've also tried sudo apt-get clean and autoclean. 

In case this adds useful info relating to the problem:

```
Notebook-PC:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x864b96be

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    19531775     9764864   83  Linux
/dev/sda2        19533822   616818687   298642433    5  Extended
/dev/sda4       616818688   625140399     4160856    c  W95 FAT32 (LBA)
/dev/sda5        19533824   605468671   292967424   83  Linux
/dev/sda6       605470720   616818687     5673984   82  Linux swap / Solaris
```

```
Notebook-PC:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=bfb418ba-1e8f-43a1-965d-ae74705ba437 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=e51047f4-b1e9-4b39-a949-4fafd7287fb1 /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=7adbb58f-db14-41f8-ba65-e17ac14b282e none            swap    sw              0       0

```

```
Notebook-PC:/boot$ ls -al
total 173912
drwxr-xr-x  3 root root    12288 Mar 30 11:23 .
drwxr-xr-x 23 root root     4096 Mar 19 17:26 ..
-rw-r--r--  1 root root   769695 Nov 15 06:47 abi-3.0.0-28-generic
-rw-r--r--  1 root root   769750 Dec  4 21:31 abi-3.0.0-29-generic
-rw-r--r--  1 root root   769860 Jan  3 07:45 abi-3.0.0-30-generic
-rw-r--r--  1 root root   769860 Feb 20 05:17 abi-3.0.0-31-generic
-rw-r--r--  1 root root   769860 Mar  1 07:47 abi-3.0.0-32-generic
-rw-r--r--  1 root root   853738 Oct 10 04:05 abi-3.5.0-17-generic
-rw-r--r--  1 root root   858289 Feb 26 03:32 abi-3.5.0-25-generic
-rw-r--r--  1 root root   858541 Mar  9 07:49 abi-3.5.0-26-generic
-rw-r--r--  1 root root   142015 Nov 15 06:47 config-3.0.0-28-generic
-rw-r--r--  1 root root   142015 Dec  4 21:31 config-3.0.0-29-generic
-rw-r--r--  1 root root   141998 Jan  3 07:45 config-3.0.0-30-generic
-rw-r--r--  1 root root   141998 Feb 20 05:17 config-3.0.0-31-generic
-rw-r--r--  1 root root   141998 Mar  1 07:47 config-3.0.0-32-generic
-rw-r--r--  1 root root   154429 Oct 10 04:05 config-3.5.0-17-generic
-rw-r--r--  1 root root   154500 Feb 26 03:32 config-3.5.0-25-generic
-rw-r--r--  1 root root   154500 Mar  9 07:49 config-3.5.0-26-generic
drwxr-xr-x  5 root root    12288 Mar 19 17:26 grub
-rw-r--r--  1 root root 13647299 Nov 30 11:18 initrd.img-3.0.0-28-generic
-rw-r--r--  1 root root 13647800 Dec 20 08:02 initrd.img-3.0.0-29-generic
-rw-r--r--  1 root root 13642593 Jan 16 07:56 initrd.img-3.0.0-30-generic
-rw-r--r--  1 root root 13639015 Feb 22 09:13 initrd.img-3.0.0-31-generic
-rw-r--r--  1 root root 13725140 Mar  9 21:48 initrd.img-3.0.0-32-generic
-rw-r--r--  1 root root 15063743 Mar 10 13:37 initrd.img-3.5.0-17-generic
-rw-r--r--  1 root root 15082405 Mar 10 13:49 initrd.img-3.5.0-25-generic
-rw-r--r--  1 root root 15108198 Mar 19 17:26 initrd.img-3.5.0-26-generic
-rw-r--r--  1 root root   176764 Jan  4 06:47 memtest86+.bin
-rw-r--r--  1 root root   178944 Jan  4 06:47 memtest86+_multiboot.bin
-rw-------  1 root root  2140742 Nov 15 06:47 System.map-3.0.0-28-generic
-rw-------  1 root root  2140807 Dec  4 21:31 System.map-3.0.0-29-generic
-rw-------  1 root root  2141213 Jan  3 07:45 System.map-3.0.0-30-generic
-rw-------  1 root root  2141854 Feb 20 05:17 System.map-3.0.0-31-generic
-rw-------  1 root root  2141885 Mar  1 07:47 System.map-3.0.0-32-generic
-rw-------  1 root root  2320733 Oct 10 04:05 System.map-3.5.0-17-generic
-rw-------  1 root root  2323653 Feb 26 03:32 System.map-3.5.0-25-generic
-rw-------  1 root root  2318941 Mar  9 07:49 System.map-3.5.0-26-generic
-rw-------  1 root root     1215 Nov 15 06:48 vmcoreinfo-3.0.0-28-generic
-rw-------  1 root root     1215 Dec  4 21:33 vmcoreinfo-3.0.0-29-generic
-rw-------  1 root root     1215 Jan  3 07:46 vmcoreinfo-3.0.0-30-generic
-rw-------  1 root root     1215 Feb 20 05:19 vmcoreinfo-3.0.0-31-generic
-rw-------  1 root root     1215 Mar  1 07:49 vmcoreinfo-3.0.0-32-generic
-rw-------  1 root root  4655648 Nov 15 06:47 vmlinuz-3.0.0-28-generic
-rw-------  1 root root  4655200 Dec  4 21:31 vmlinuz-3.0.0-29-generic
-rw-------  1 root root  4655552 Jan  3 07:45 vmlinuz-3.0.0-30-generic
-rw-------  1 root root  4655584 Feb 20 05:17 vmlinuz-3.0.0-31-generic
-rw-------  1 root root  4655648 Mar  1 07:47 vmlinuz-3.0.0-32-generic
-rw-r--r--  1 root root  5171760 Oct 18 08:08 vmlinuz-3.5.0-17-generic
-rw-------  1 root root  5180432 Feb 26 03:32 vmlinuz-3.5.0-25-generic
-rw-------  1 root root  5167568 Mar  9 07:49 vmlinuz-3.5.0-26-generic
```

```
Notebook-PC:~$ uname -r
3.5.0-26-generic

```

Any help would be appreciated.

---

### Post by plucky on 2013-03-30
What does ```
df -i
``` show you?

If / shows 100% for the / partition see [Solution Thread](http://ubuntuforums.org/showthread.php?t=2130652)

Good Luck

---

### Post by damagu on 2013-03-30
> **plucky said:**
> What does ```
df -i
``` show you?

If / shows 100% for the / partition see [Solution Thread](http://ubuntuforums.org/showthread.php?t=2130652)

Good Luck

Thanks for the reply. df -i shows this:

```
Notebook-PC:/boot$ df -i
df: `/root/.gvfs': Permission denied
Filesystem       Inodes  IUsed    IFree IUse% Mounted on
/dev/sda1        610800 605927     4873  100% /
udev             204923    510   204413    1% /dev
tmpfs            206862    426   206436    1% /run
none             206862      3   206859    1% /run/lock
none             206862      6   206856    1% /run/shm
none             206862     17   206845    1% /run/user
/dev/sda5      18317312  32737 18284575    1% /home
```

I looked at the solution but the solution in the thread you pointed to is tailored to what that thread's OP had in the results to their df -i. I'm not sure what I should be removing because my results are different. Here's my results:

```
Notebook-PC:/boot$ dpkg -l | egrep "linux-image|linux-headers"
ii  linux-headers-3.5.0-17                    3.5.0-17.28                               all          Header files related to Linux kernel version 3.5.0
ii  linux-headers-3.5.0-17-generic            3.5.0-17.28                               i386         Linux kernel headers for version 3.5.0 on 32 bit x86 SMP
ii  linux-headers-3.5.0-25                    3.5.0-25.39                               all          Header files related to Linux kernel version 3.5.0
ii  linux-headers-3.5.0-25-generic            3.5.0-25.39                               i386         Linux kernel headers for version 3.5.0 on 32 bit x86 SMP
ii  linux-headers-3.5.0-26                    3.5.0-26.42                               all          Header files related to Linux kernel version 3.5.0
iU  linux-headers-generic                     3.5.0.26.32                               i386         Generic Linux kernel headers
iU  linux-headers-generic-pae                 3.5.0.26.32                               i386         Transitional package
ii  linux-image-3.5.0-17-generic              3.5.0-17.28                               i386         Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-3.5.0-25-generic              3.5.0-25.39                               i386         Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-3.5.0-26-generic              3.5.0-26.42                               i386         Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-extra-3.5.0-17-generic        3.5.0-17.28                               i386         Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-extra-3.5.0-25-generic        3.5.0-25.39                               i386         Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-extra-3.5.0-26-generic        3.5.0-26.42                               i386         Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-generic                       3.5.0.26.32                               i386         Generic Linux kernel image
```

Should I remove all but the 3.5.0-26* items in the list or should I leave the 3.5.0-25* ones too? I figured it'd be okay to remove the 3.5.0-17 items but that only freed up 2%. Then I managed to run sudo apt-get -f install without errors. Running df -i then showed 99% used. I then ran sudo apt-get -f autoremove. It cleared the linux-headers-3.5.0-17 (which I thought I already removed when I ran the first of dpkg commands in the solution thread) and df -i then showed 97%. That still seems really high. Can you tell me what other items it'd be safe to remove? Should I do something about increasing the size of the / partition?

---

### Post by plucky on 2013-03-31
Do you still have the same list in /boot?

There seems to be a lot of other 3.0.0. kernels installed > Notebook-PC:/boot$ ls -al
total 173912
drwxr-xr-x  3 root root    12288 Mar 30 11:23 .
drwxr-xr-x 23 root root     4096 Mar 19 17:26 ..
-rw-r--r--  1 root root   769695 Nov 15 06:47 abi-3.0.0-28-generic
-rw-r--r--  1 root root   769750 Dec  4 21:31 abi-3.0.0-29-generic
-rw-r--r--  1 root root   769860 Jan  3 07:45 abi-3.0.0-30-generic
-rw-r--r--  1 root root   769860 Feb 20 05:17 abi-3.0.0-31-generic
-rw-r--r--  1 root root   769860 Mar  1 07:47 abi-3.0.0-32-generic
-rw-r--r--  1 root root   853738 Oct 10 04:05 abi-3.5.0-17-generic
-rw-r--r--  1 root root   858289 Feb 26 03:32 abi-3.5.0-25-generic
-rw-r--r--  1 root root   858541 Mar  9 07:49 abi-3.5.0-26-generic
-rw-r--r--  1 root root   142015 Nov 15 06:47 config-3.0.0-28-generic
-rw-r--r--  1 root root   142015 Dec  4 21:31 config-3.0.0-29-generic
-rw-r--r--  1 root root   141998 Jan  3 07:45 config-3.0.0-30-generic
-rw-r--r--  1 root root   141998 Feb 20 05:17 config-3.0.0-31-generic
-rw-r--r--  1 root root   141998 Mar  1 07:47 config-3.0.0-32-generic
-rw-r--r--  1 root root   154429 Oct 10 04:05 config-3.5.0-17-generic
-rw-r--r--  1 root root   154500 Feb 26 03:32 config-3.5.0-25-generic
-rw-r--r--  1 root root   154500 Mar  9 07:49 config-3.5.0-26-generic
drwxr-xr-x  5 root root    12288 Mar 19 17:26 grub
-rw-r--r--  1 root root 13647299 Nov 30 11:18 initrd.img-3.0.0-28-generic
-rw-r--r--  1 root root 13647800 Dec 20 08:02 initrd.img-3.0.0-29-generic
-rw-r--r--  1 root root 13642593 Jan 16 07:56 initrd.img-3.0.0-30-generic
-rw-r--r--  1 root root 13639015 Feb 22 09:13 initrd.img-3.0.0-31-generic
-rw-r--r--  1 root root 13725140 Mar  9 21:48 initrd.img-3.0.0-32-generic
-rw-r--r--  1 root root 15063743 Mar 10 13:37 initrd.img-3.5.0-17-generic
-rw-r--r--  1 root root 15082405 Mar 10 13:49 initrd.img-3.5.0-25-generic
-rw-r--r--  1 root root 15108198 Mar 19 17:26 initrd.img-3.5.0-26-generic
-rw-r--r--  1 root root   176764 Jan  4 06:47 memtest86+.bin
-rw-r--r--  1 root root   178944 Jan  4 06:47 memtest86+_multiboot.bin
-rw-------  1 root root  2140742 Nov 15 06:47 System.map-3.0.0-28-generic
-rw-------  1 root root  2140807 Dec  4 21:31 System.map-3.0.0-29-generic
-rw-------  1 root root  2141213 Jan  3 07:45 System.map-3.0.0-30-generic
-rw-------  1 root root  2141854 Feb 20 05:17 System.map-3.0.0-31-generic
-rw-------  1 root root  2141885 Mar  1 07:47 System.map-3.0.0-32-generic
-rw-------  1 root root  2320733 Oct 10 04:05 System.map-3.5.0-17-generic
-rw-------  1 root root  2323653 Feb 26 03:32 System.map-3.5.0-25-generic
-rw-------  1 root root  2318941 Mar  9 07:49 System.map-3.5.0-26-generic
-rw-------  1 root root     1215 Nov 15 06:48 vmcoreinfo-3.0.0-28-generic
-rw-------  1 root root     1215 Dec  4 21:33 vmcoreinfo-3.0.0-29-generic
-rw-------  1 root root     1215 Jan  3 07:46 vmcoreinfo-3.0.0-30-generic
-rw-------  1 root root     1215 Feb 20 05:19 vmcoreinfo-3.0.0-31-generic
-rw-------  1 root root     1215 Mar  1 07:49 vmcoreinfo-3.0.0-32-generic
-rw-------  1 root root  4655648 Nov 15 06:47 vmlinuz-3.0.0-28-generic
-rw-------  1 root root  4655200 Dec  4 21:31 vmlinuz-3.0.0-29-generic
-rw-------  1 root root  4655552 Jan  3 07:45 vmlinuz-3.0.0-30-generic
-rw-------  1 root root  4655584 Feb 20 05:17 vmlinuz-3.0.0-31-generic
-rw-------  1 root root  4655648 Mar  1 07:47 vmlinuz-3.0.0-32-generic
-rw-r--r--  1 root root  5171760 Oct 18 08:08 vmlinuz-3.5.0-17-generic
-rw-------  1 root root  5180432 Feb 26 03:32 vmlinuz-3.5.0-25-generic
-rw-------  1 root root  5167568 Mar  9 07:49 vmlinuz-3.5.0-26-generic

See if you can find them using **Synaptic Package Manager** and remove them and their headers.

Good Luck

---

### Post by schragge on 2013-03-31
I'm not sure Synaptic would help here as if it is still not installed on your system you will not be able to install it. Better try solution from the linked thread adjusted to your situation:
```

sudo dpkg -P ^linux-{image,image-extra,headers}-3.5.0-17 

```
Strangely enough, the 3.0.0 kernels don't show up in the *dpkg -l* output. Before doing anything about them, could you please post the output of
```
dpkg -l|grep '^i.*-3\.0\.0-'
```

---

