---
title: "out of space and inodes on / and can't purge old kernels to make space"
date: 2016-05-18
forum: General Help
---

### Post by ibod on 2016-05-18
I am running Ubuntu 14.04 LTS 32 bit version

I started off with the error...

```

The volume "Filesystem root" has only 311.6MB disk space remaining.

```

So I looked at the space and inodes, here is the output of...

```

df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       9.3G  8.5G  298M  97% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            998M  4.0K  998M   1% /dev
tmpfs           202M  1.1M  201M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none           1007M  156K 1007M   1% /run/shm
none            100M   52K  100M   1% /run/user
/dev/sda2        61G  3.1G   54G   6% /home

df -i
Filesystem      Inodes  IUsed   IFree IUse% Mounted on
/dev/sda1       625856 625856       0  100% /
none            220045      2  220043    1% /sys/fs/cgroup
udev            215240    496  214744    1% /dev
tmpfs           220045    470  219575    1% /run
none            220045      3  220042    1% /run/lock
none            220045      7  220038    1% /run/shm
none            220045     30  220015    1% /run/user
/dev/sda2      4014080  33836 3980244    1% /home

```

From df -h  can see there is very little space left on / as in the error and 
from df -i I can see there are no free inodes on /

I believe the problem here is many old kernels on the / partition taking up a lot of space

I tried ...

```

dpkg -l | tail -n +6 | grep -E 'linux-image-[0-9]+' | grep -Fv $(uname -r)

```

To lists all the kernels excluding the booted kernel, but the terminal closes as soon as I press return.

So I did a file search for 'linux-image' and found kernels  3.13.0-32, 44, 45, 46, 48, 49, 51, 52, 53, 54, 55, 57, 58, 59, (61 the current kernel) and (62 the kernel that caused the lack of space and is waiting to be installed).

```

uname -r
3.13.0-61-generic

```

when I try to purge the oldest kernel...

```

sudo dpkg --purge linux-image-3.13.0-32-generic

```

I get the error....

```

dpkg: error: unable to create new file '/var/lib/dpkg/status-new': No space left on device

```

Now I am stuck,  can anyone help

---

### Post by Bashing-om on 2016-05-18
ibod; Hello;;

While with a great deal of doubt will work ...
```

sudo apt-get autoclean 
sudo apt-get autoremove
sudo apt-get clean

```

As easy as that is to try, worth a shot.

Else we drop down to the level of 'dpkg' and tackle the old kernels at a lower level.
Failing that we get real dirty and remove files manually and clean up the bad mess afterward.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by QIII on 2016-05-18
Also look in /var/log for .gz files of old logs.  Those can take up room and can generally be removed.

---

### Post by grahammechanical on 2016-05-18
Decrease the size of sda2. It is 61 GB with only 3.1 GB used. Increase the size of sda1. It is 9.3 GB. Which is close to the minimum necessary. Then there will be space to install the new kernel and then remove old kernels. The system is in a kind of loop. Until the install of the new kernel is completed it becomes difficult to remove old kernels. 

At the Grub boot menu we have Advanced options for Ubuntu. That is a sub-menu that will let us load with a recovery mode kernel. The recovery menu has an option called Clean - Try to make free space. That will run two commands apt-get clean & apt-get autoremove. It is autoremove that may remove at least one previous kernel.

Another thing that you can try is to remove some of the applications that you do not need. Applications take up more disk space in the  root ( / ) file system than they do in /home.

With Ubuntu 14.04 autoremove only removes one kernel each time it is run. With Ubuntu 16.04 autoremove will remove all previous kernels except one. Which with the active kernel will leave 2 kernels available for loading. The latest kernel & the next to one latest kernel.

You may need to increase the size of sda1 by at least 2 GB to resolve this. And then run autoremove regularly.

Regards.

---

### Post by pfeiffep on 2016-05-18
If you have Synaptic installed search for linux-image mark ONLY the older ones for complete removal

in the case of no Synaptic apt-get
> sudo apt-get remove linux-image-???????-generic Replacing the ??? with information gained from > ls -l /boot

Not super elegant but it will get you out of a jam

---

### Post by ibod on 2016-05-18
Hi Bashing-om

Your doubt was correct...

```

sudo apt-get autoclean

sudo: unable to open /var/lib/sudo/andy/5: No space left on device
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

sudo apt-get autoremove

sudo: unable to open /var/lib/sudo/andy/5: No space left on device
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

sudo apt-get clean

sudo: unable to open /var/lib/sudo/andy/5: No space left on device

```

and...

```

sudo dpkg --configure -a

```

starts to work but again the terminal closes part way through

so what's next..

---

### Post by Bashing-om on 2016-05-18
ibod; Hey !

Well we can drop down to 'pkg's level .. However the esteemed grahammechanical's advise is well worth considering. Now would be a great time to address that space usage .

[INDENT][INDENT]more than one path to an end
[/INDENT][/INDENT]

---

### Post by HermanAB on 2016-05-18
1. Go to /boot and rm the old kernels.  You don't need to use a package manager to do that.
2. Go to /var and rm old logs.
3. Now you know why to make /boot and /var separate partitions.

---

### Post by Linuxisfast on 2016-05-19
[https://utappia.org/2016/03/28/ucaresystem-core-v3-0-released-and-available-in-ppa/](https://utappia.org/2016/03/28/ucaresystem-core-v3-0-released-and-available-in-ppa/) one of the best utilities to do its job and has its own PPA as well.

---

### Post by Impavidus on 2016-05-19
I think the old kernels are taking your gigabytes, but your inodes are taken by old kernel headers. You have to free some of those inodes to get the package manager working properly again. Try```
sudo dpkg -P linux-headers-<some old versions>
```If that doesn't work, try it the dirty way by manually removing some files (a few directories, 50,000 files or so) from /usr/src/linux-headers-<some old versions>.

A 9.3GB root partition is indeed rather small.

---

### Post by mörgæs on 2016-05-19
> **grahammechanical said:**
> 
With Ubuntu 14.04 autoremove only removes one kernel each time it is run. With Ubuntu 16.04 autoremove will remove all previous kernels except one. Which with the active kernel will leave 2 kernels available for loading. The latest kernel & the next to one latest kernel.


No, both 14.04 and 16.04 will remove everything but the two latest. It's a good habit to run the command once in a while.

---

### Post by ibod on 2016-05-19
Hi,

It was [**[COLOR=#000000]Impavidus[/COLOR]**]("http://ubuntuforums.org/member.php?u=1417721")' command...

```

sudo dpkg -P linux-headers-<some old version>

```

...that enabled me to delete some of the headers to make some space and free up some inodes.

but I had to delete the generics first due to dependancies

```

sudo dpkg -P linux-headers-<some old version>-generic

```

I had to remove several versions before there was enough space to make things work and ultimately run a normal Software Update in GUI.

I removed the headers for  linux-headers-3.13.0-32, 44, 45, 46, 48, and 49 as well as the -generics for the same versions

Then ...

```

sudo dpkg --configure -a
apt-get install -f
apt-get autoremove
sudo apt-get update

```

...to tidy things up a bit.

Then a Software Update and it worked. 

What I still need some help with is to clear up the mess made by part deleting the kernels above and the other old kernels that I did not mess with.

3.13.0-51, 52, 53, 54, 55, 57, 58, 59 and 61.

I am now using...

```
 
uname -r
3.13.0-86-generic

```

I have tried...

```

sudo apt-get autoremove 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 to upgrade, 0 to newly install, 0 to remove and 14 not to upgrade.

```

...but it is not recognising the remaining six partly deleted kernel packages 3.13.0-32, 44, 45, 46, 48, and 49 
or the nine 3.13.0-51, 52, 53, 54, 55, 57, 58, 59 and 61. remaining old kernels that I have not messed with at all.

How can I tidy up this mess ?

---

### Post by mörgæs on 2016-05-19
Is there a particular reason that you want to keep 14.04? Since you have a separate /home it should be easy to install 16.04.

---

### Post by Impavidus on 2016-05-19
I could never make much sense out of which kernels trusty would autoremove.

You could try requesting their removal explicitly:```
sudo apt-get purge linux-image{,-extra}-3.13.0-{32,44,45,46,48,49,51,52,53,54,55,57,58,59}-generic linux-headers-3.13.0-{51,52,53,54,55,57,58,59}{,-generic}
```Those are the packages (except for the version numbers) on my system. You may have to change it.

By manually removing some kernels you have made a bit of a mess, but I don't think you removed any files necessary for clean uninstallation of those packages (and any packages depending on them). So you should be able to just uninstall them. Else, the package manager will probably complain and then you can reinstall those header and kernel packages and then remove them again. One version at a time of course, i. e., reinstall everything with version 3.13.0-32, unstall everything with version 3.13.0-32, reinstall everything with version 3.13.0-44, etc. But I don't think you'll need that.

---

### Post by Bashing-om on 2016-05-19
ibod; Hey ..

Overall .. look'n good .

At this point I do suggest to make sure all the kernel components ALL agree:
```

ls -al /usr/src/
ls -al /lib/modules/
ls -al /boot/
dpkg -l | grep linux-
ls -al /vmlinuz*
ls -al /initrd.img*

```

Then we decide if there is further work to be done for this install.

[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]together we do
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ibod on 2016-05-19
Hi Bashing-om,

Ok here are the outputs.

```

ls -al /usr/src/
total 88
drwxr-xr-x 22 root root 4096 May 19 14:22 .
drwxr-xr-x 10 root root 4096 Jul 22  2014 ..
drwxr-xr-x 24 root root 4096 Apr 30  2015 linux-headers-3.13.0-51
drwxr-xr-x  7 root root 4096 Apr 30  2015 linux-headers-3.13.0-51-generic
drwxr-xr-x 24 root root 4096 May  9  2015 linux-headers-3.13.0-52
drwxr-xr-x  7 root root 4096 May  9  2015 linux-headers-3.13.0-52-generic
drwxr-xr-x 24 root root 4096 May 23  2015 linux-headers-3.13.0-53
drwxr-xr-x  7 root root 4096 May 23  2015 linux-headers-3.13.0-53-generic
drwxr-xr-x 24 root root 4096 Jun 11  2015 linux-headers-3.13.0-54
drwxr-xr-x  7 root root 4096 Jun 11  2015 linux-headers-3.13.0-54-generic
drwxr-xr-x 24 root root 4096 Jun 20  2015 linux-headers-3.13.0-55
drwxr-xr-x  7 root root 4096 Jun 20  2015 linux-headers-3.13.0-55-generic
drwxr-xr-x 24 root root 4096 Jul  7  2015 linux-headers-3.13.0-57
drwxr-xr-x  7 root root 4096 Jul  7  2015 linux-headers-3.13.0-57-generic
drwxr-xr-x 24 root root 4096 Jul 23  2015 linux-headers-3.13.0-58
drwxr-xr-x  7 root root 4096 Jul 23  2015 linux-headers-3.13.0-58-generic
drwxr-xr-x 24 root root 4096 Jul 28  2015 linux-headers-3.13.0-59
drwxr-xr-x  7 root root 4096 Jul 28  2015 linux-headers-3.13.0-59-generic
drwxr-xr-x 24 root root 4096 Jul 30  2015 linux-headers-3.13.0-61
drwxr-xr-x  7 root root 4096 Jul 30  2015 linux-headers-3.13.0-61-generic
drwxr-xr-x 24 root root 4096 May 19 14:18 linux-headers-3.13.0-86
drwxr-xr-x  7 root root 4096 May 19 14:18 linux-headers-3.13.0-86-generic

```

```

ls -al /lib/modules/
total 72
drwxr-xr-x 18 root root 4096 May 19 14:24 .
drwxr-xr-x 23 root root 4096 May 19 14:40 ..
drwxr-xr-x  5 root root 4096 May 19 14:11 3.13.0-44-generic
drwxr-xr-x  5 root root 4096 May 19 14:11 3.13.0-45-generic
drwxr-xr-x  5 root root 4096 May 19 14:21 3.13.0-46-generic
drwxr-xr-x  5 root root 4096 May 19 14:21 3.13.0-48-generic
drwxr-xr-x  5 root root 4096 May 19 14:21 3.13.0-49-generic
drwxr-xr-x  5 root root 4096 Apr 30  2015 3.13.0-51-generic
drwxr-xr-x  5 root root 4096 May  9  2015 3.13.0-52-generic
drwxr-xr-x  5 root root 4096 May 23  2015 3.13.0-53-generic
drwxr-xr-x  5 root root 4096 Jun 11  2015 3.13.0-54-generic
drwxr-xr-x  5 root root 4096 Jun 20  2015 3.13.0-55-generic
drwxr-xr-x  5 root root 4096 Jul  7  2015 3.13.0-57-generic
drwxr-xr-x  5 root root 4096 Jul 23  2015 3.13.0-58-generic
drwxr-xr-x  5 root root 4096 Jul 28  2015 3.13.0-59-generic
drwxr-xr-x  5 root root 4096 Jul 30  2015 3.13.0-61-generic
drwxr-xr-x  5 root root 4096 May 19 14:10 3.13.0-62-generic
drwxr-xr-x  5 root root 4096 May 19 14:18 3.13.0-86-generic

```

```

ls -al /boot/
total 448472
drwxr-xr-x  3 root root     4096 May 19 14:40 .
drwxr-xr-x 22 root root     4096 May 19 14:18 ..
-rw-r--r--  1 root root  1168937 Dec 16  2014 abi-3.13.0-44-generic
-rw-r--r--  1 root root  1169184 Jan 13  2015 abi-3.13.0-45-generic
-rw-r--r--  1 root root  1169069 Mar 10  2015 abi-3.13.0-46-generic
-rw-r--r--  1 root root  1168940 Mar 12  2015 abi-3.13.0-48-generic
-rw-r--r--  1 root root  1168940 Apr 10  2015 abi-3.13.0-49-generic
-rw-r--r--  1 root root  1168888 Apr 15  2015 abi-3.13.0-51-generic
-rw-r--r--  1 root root  1168888 May  4  2015 abi-3.13.0-52-generic
-rw-r--r--  1 root root  1168888 May 20  2015 abi-3.13.0-53-generic
-rw-r--r--  1 root root  1169023 May 26  2015 abi-3.13.0-54-generic
-rw-r--r--  1 root root  1169023 Jun 18  2015 abi-3.13.0-55-generic
-rw-r--r--  1 root root  1169201 Jun 19  2015 abi-3.13.0-57-generic
-rw-r--r--  1 root root  1169346 Jul  8  2015 abi-3.13.0-58-generic
-rw-r--r--  1 root root  1169346 Jul 25  2015 abi-3.13.0-59-generic
-rw-r--r--  1 root root  1169346 Jul 29  2015 abi-3.13.0-61-generic
-rw-r--r--  1 root root  1169478 Aug 11  2015 abi-3.13.0-62-generic
-rw-r--r--  1 root root  1170277 May 13 02:48 abi-3.13.0-86-generic
-rw-r--r--  1 root root   169818 Dec 16  2014 config-3.13.0-44-generic
-rw-r--r--  1 root root   169818 Jan 13  2015 config-3.13.0-45-generic
-rw-r--r--  1 root root   169818 Mar 10  2015 config-3.13.0-46-generic
-rw-r--r--  1 root root   169843 Mar 12  2015 config-3.13.0-48-generic
-rw-r--r--  1 root root   169843 Apr 10  2015 config-3.13.0-49-generic
-rw-r--r--  1 root root   169832 Apr 15  2015 config-3.13.0-51-generic
-rw-r--r--  1 root root   169832 May  4  2015 config-3.13.0-52-generic
-rw-r--r--  1 root root   169832 May 20  2015 config-3.13.0-53-generic
-rw-r--r--  1 root root   169832 May 26  2015 config-3.13.0-54-generic
-rw-r--r--  1 root root   169832 Jun 18  2015 config-3.13.0-55-generic
-rw-r--r--  1 root root   169832 Jun 19  2015 config-3.13.0-57-generic
-rw-r--r--  1 root root   169832 Jul  8  2015 config-3.13.0-58-generic
-rw-r--r--  1 root root   169832 Jul 25  2015 config-3.13.0-59-generic
-rw-r--r--  1 root root   169833 Jul 29  2015 config-3.13.0-61-generic
-rw-r--r--  1 root root   169833 Aug 11  2015 config-3.13.0-62-generic
-rw-r--r--  1 root root   169988 May 13 02:48 config-3.13.0-86-generic
drwxr-xr-x  5 root root     4096 May 19 14:39 grub
-rw-r--r--  1 root root 18764143 Jan 19  2015 initrd.img-3.13.0-44-generic
-rw-r--r--  1 root root 18771563 Feb 21  2015 initrd.img-3.13.0-45-generic
-rw-r--r--  1 root root 18771584 Mar 12  2015 initrd.img-3.13.0-46-generic
-rw-r--r--  1 root root 18772443 Mar 24  2015 initrd.img-3.13.0-48-generic
-rw-r--r--  1 root root 18772306 Apr 15  2015 initrd.img-3.13.0-49-generic
-rw-r--r--  1 root root 18773720 Apr 30  2015 initrd.img-3.13.0-51-generic
-rw-r--r--  1 root root 18773546 May  9  2015 initrd.img-3.13.0-52-generic
-rw-r--r--  1 root root 18772219 Jun  2  2015 initrd.img-3.13.0-53-generic
-rw-r--r--  1 root root 18771021 Jun 11  2015 initrd.img-3.13.0-54-generic
-rw-r--r--  1 root root 18771701 Jun 20  2015 initrd.img-3.13.0-55-generic
-rw-r--r--  1 root root 18775105 Jul  7  2015 initrd.img-3.13.0-57-generic
-rw-r--r--  1 root root 18780402 Jul 23  2015 initrd.img-3.13.0-58-generic
-rw-r--r--  1 root root 18781256 Jul 28  2015 initrd.img-3.13.0-59-generic
-rw-r--r--  1 root root 18779634 Aug  5  2015 initrd.img-3.13.0-61-generic
-rw-r--r--  1 root root 18780262 May 19 14:10 initrd.img-3.13.0-62-generic
-rw-r--r--  1 root root 18795329 May 19 14:40 initrd.img-3.13.0-86-generic
-rw-r--r--  1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r--  1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r--  1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw-------  1 root root  2699036 Dec 16  2014 System.map-3.13.0-44-generic
-rw-------  1 root root  2699380 Jan 13  2015 System.map-3.13.0-45-generic
-rw-------  1 root root  2699562 Mar 10  2015 System.map-3.13.0-46-generic
-rw-------  1 root root  2699351 Mar 12  2015 System.map-3.13.0-48-generic
-rw-------  1 root root  2699535 Apr 10  2015 System.map-3.13.0-49-generic
-rw-------  1 root root  2699822 Apr 15  2015 System.map-3.13.0-51-generic
-rw-------  1 root root  2699822 May  4  2015 System.map-3.13.0-52-generic
-rw-------  1 root root  2700091 May 20  2015 System.map-3.13.0-53-generic
-rw-------  1 root root  2700583 May 26  2015 System.map-3.13.0-54-generic
-rw-------  1 root root  2700583 Jun 18  2015 System.map-3.13.0-55-generic
-rw-------  1 root root  2701039 Jun 19  2015 System.map-3.13.0-57-generic
-rw-------  1 root root  2701185 Jul  8  2015 System.map-3.13.0-58-generic
-rw-------  1 root root  2701185 Jul 25  2015 System.map-3.13.0-59-generic
-rw-------  1 root root  2701185 Jul 29  2015 System.map-3.13.0-61-generic
-rw-------  1 root root  2701608 Aug 11  2015 System.map-3.13.0-62-generic
-rw-------  1 root root  2702195 May 13 02:48 System.map-3.13.0-86-generic
-rw-------  1 root root  5833648 Dec 16  2014 vmlinuz-3.13.0-44-generic
-rw-------  1 root root  5833648 Jan 13  2015 vmlinuz-3.13.0-45-generic
-rw-------  1 root root  5836592 Mar 10  2015 vmlinuz-3.13.0-46-generic
-rw-------  1 root root  5837296 Mar 12  2015 vmlinuz-3.13.0-48-generic
-rw-------  1 root root  5836528 Apr 10  2015 vmlinuz-3.13.0-49-generic
-rw-------  1 root root  5836848 Apr 15  2015 vmlinuz-3.13.0-51-generic
-rw-------  1 root root  5837072 May  4  2015 vmlinuz-3.13.0-52-generic
-rw-------  1 root root  5837648 May 20  2015 vmlinuz-3.13.0-53-generic
-rw-------  1 root root  5840240 May 26  2015 vmlinuz-3.13.0-54-generic
-rw-------  1 root root  5840240 Jun 18  2015 vmlinuz-3.13.0-55-generic
-rw-------  1 root root  5841552 Jun 19  2015 vmlinuz-3.13.0-57-generic
-rw-------  1 root root  5843472 Jul  8  2015 vmlinuz-3.13.0-58-generic
-rw-------  1 root root  5843504 Jul 25  2015 vmlinuz-3.13.0-59-generic
-rw-------  1 root root  5843472 Jul 29  2015 vmlinuz-3.13.0-61-generic
-rw-------  1 root root  5843696 Aug 11  2015 vmlinuz-3.13.0-62-generic
-rw-------  1 root root  5851984 May 13 02:48 vmlinuz-3.13.0-86-generic

```


```

dpkg -l | grep linux-
ii  linux-firmware                                        1.127.22                                            all          Firmware for Linux kernel drivers
ii  linux-generic                                         3.13.0.86.92                                        i386         Complete Generic Linux kernel and headers
ii  linux-headers-3.13.0-51                               3.13.0-51.84                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-51-generic                       3.13.0-51.84                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-52                               3.13.0-52.86                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-52-generic                       3.13.0-52.86                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-53                               3.13.0-53.89                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-53-generic                       3.13.0-53.89                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-54                               3.13.0-54.91                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-54-generic                       3.13.0-54.91                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-55                               3.13.0-55.94                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-55-generic                       3.13.0-55.94                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-57                               3.13.0-57.95                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-57-generic                       3.13.0-57.95                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-58                               3.13.0-58.97                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-58-generic                       3.13.0-58.97                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-59                               3.13.0-59.98                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-59-generic                       3.13.0-59.98                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-61                               3.13.0-61.100                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-61-generic                       3.13.0-61.100                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-86                               3.13.0-86.131                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-86-generic                       3.13.0-86.131                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-generic                                 3.13.0.86.92                                        i386         Generic Linux kernel headers
rc  linux-image-3.13.0-32-generic                         3.13.0-32.57                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-44-generic                         3.13.0-44.73                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-45-generic                         3.13.0-45.74                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-46-generic                         3.13.0-46.79                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-48-generic                         3.13.0-48.80                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-49-generic                         3.13.0-49.83                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-51-generic                         3.13.0-51.84                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-52-generic                         3.13.0-52.86                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-53-generic                         3.13.0-53.89                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-54-generic                         3.13.0-54.91                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-55-generic                         3.13.0-55.94                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-57-generic                         3.13.0-57.95                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-58-generic                         3.13.0-58.97                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-59-generic                         3.13.0-59.98                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-61-generic                         3.13.0-61.100                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-62-generic                         3.13.0-62.102                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-86-generic                         3.13.0-86.131                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
rc  linux-image-extra-3.13.0-32-generic                   3.13.0-32.57                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-44-generic                   3.13.0-44.73                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-45-generic                   3.13.0-45.74                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-46-generic                   3.13.0-46.79                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-48-generic                   3.13.0-48.80                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-49-generic                   3.13.0-49.83                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-51-generic                   3.13.0-51.84                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-52-generic                   3.13.0-52.86                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-53-generic                   3.13.0-53.89                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-54-generic                   3.13.0-54.91                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-55-generic                   3.13.0-55.94                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-57-generic                   3.13.0-57.95                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-58-generic                   3.13.0-58.97                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-59-generic                   3.13.0-59.98                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-61-generic                   3.13.0-61.100                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-62-generic                   3.13.0-62.102                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-86-generic                   3.13.0-86.131                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-generic                                   3.13.0.86.92                                        i386         Generic Linux kernel image
ii  linux-libc-dev:i386                                   3.13.0-86.131                                       i386         Linux Kernel Headers for development
ii  linux-sound-base                                      1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  syslinux-common                                       3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                       2:3.63+dfsg-2ubuntu5                                i386         Bootloader for Linux/i386 using MS-DOS floppies

```

```

ls -al /vmlinuz*
lrwxrwxrwx 1 root root 30 May 19 14:18 /vmlinuz -> boot/vmlinuz-3.13.0-86-generic
lrwxrwxrwx 1 root root 30 Aug 18  2015 /vmlinuz.old -> boot/vmlinuz-3.13.0-62-generic

```

```

ls -al /initrd.img*
lrwxrwxrwx 1 root root 33 May 19 14:18 /initrd.img -> boot/initrd.img-3.13.0-86-generic
lrwxrwxrwx 1 root root 33 May 19 14:09 /initrd.img.old -> boot/initrd.img-3.13.0-62-generic

```


Quite a mess,  but as expected...

---

### Post by Bashing-om on 2016-05-19
ibod; Yeah ....

Somewhat of a mess .

Did you run Impavidus' suggestion in that last posting ? If it runs will clean things up considerably .
Getting dirty and going behind the package manager's back is the means of last resort.
However, if the need exist, well that is what we will do .

Bear in mind
[INDENT][INDENT]it is not nice to fool mother package manager
[/INDENT][/INDENT]

---

### Post by ibod on 2016-05-20
Hi,

Yes I have now run Impavidus' suggestion... 

```

sudo apt-get purge linux-image{,-extra}-3.13.0-{32,44,45,46,48,49,51,52,53,54,55,57,58,59}-generic linux-headers-3.13.0-{51,52,53,54,55,57,58,59}{,-generic}

```

...note the 'linux-headers-3.13.3-' in his post was intended to be 'linux-headers-3.13.0' other than that one small edit the suggestion worked well, (took some time to run :-) ). 


The results now are as follows...

```

ls -al /usr/src/
total 24
drwxr-xr-x  6 root root 4096 May 20 10:19 .
drwxr-xr-x 10 root root 4096 Jul 22  2014 ..
drwxr-xr-x 24 root root 4096 Jul 30  2015 linux-headers-3.13.0-61
drwxr-xr-x  7 root root 4096 Jul 30  2015 linux-headers-3.13.0-61-generic
drwxr-xr-x 24 root root 4096 May 19 14:18 linux-headers-3.13.0-86
drwxr-xr-x  7 root root 4096 May 19 14:18 linux-headers-3.13.0-86-generic

```

****  Why are linux-headers-3.13.0-62 and linux-headers-3.13.0-62-generic missing above ?? I did not do anything to that version.

```

ls -al /lib/modules/
total 20
drwxr-xr-x  5 root root 4096 May 20 10:25 .
drwxr-xr-x 23 root root 4096 May 19 14:40 ..
drwxr-xr-x  5 root root 4096 Jul 30  2015 3.13.0-61-generic
drwxr-xr-x  5 root root 4096 May 19 14:10 3.13.0-62-generic
drwxr-xr-x  5 root root 4096 May 19 14:18 3.13.0-86-generic

```

```

ls -al /boot/
total 84576
drwxr-xr-x  3 root root     4096 May 20 10:25 .
drwxr-xr-x 22 root root     4096 May 19 14:18 ..
-rw-r--r--  1 root root  1169346 Jul 29  2015 abi-3.13.0-61-generic
-rw-r--r--  1 root root  1169478 Aug 11  2015 abi-3.13.0-62-generic
-rw-r--r--  1 root root  1170277 May 13 02:48 abi-3.13.0-86-generic
-rw-r--r--  1 root root   169833 Jul 29  2015 config-3.13.0-61-generic
-rw-r--r--  1 root root   169833 Aug 11  2015 config-3.13.0-62-generic
-rw-r--r--  1 root root   169988 May 13 02:48 config-3.13.0-86-generic
drwxr-xr-x  5 root root     4096 May 20 10:25 grub
-rw-r--r--  1 root root 18779634 Aug  5  2015 initrd.img-3.13.0-61-generic
-rw-r--r--  1 root root 18780262 May 19 14:10 initrd.img-3.13.0-62-generic
-rw-r--r--  1 root root 18795329 May 19 14:40 initrd.img-3.13.0-86-generic
-rw-r--r--  1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r--  1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r--  1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw-------  1 root root  2701185 Jul 29  2015 System.map-3.13.0-61-generic
-rw-------  1 root root  2701608 Aug 11  2015 System.map-3.13.0-62-generic
-rw-------  1 root root  2702195 May 13 02:48 System.map-3.13.0-86-generic
-rw-------  1 root root  5843472 Jul 29  2015 vmlinuz-3.13.0-61-generic
-rw-------  1 root root  5843696 Aug 11  2015 vmlinuz-3.13.0-62-generic
-rw-------  1 root root  5851984 May 13 02:48 vmlinuz-3.13.0-86-generic

```

```

dpkg -l | grep linux-
ii  linux-firmware                                        1.127.22                                            all          Firmware for Linux kernel drivers
ii  linux-generic                                         3.13.0.86.92                                        i386         Complete Generic Linux kernel and headers
ii  linux-headers-3.13.0-61                               3.13.0-61.100                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-61-generic                       3.13.0-61.100                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-86                               3.13.0-86.131                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-86-generic                       3.13.0-86.131                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-generic                                 3.13.0.86.92                                        i386         Generic Linux kernel headers
ii  linux-image-3.13.0-61-generic                         3.13.0-61.100                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-62-generic                         3.13.0-62.102                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-86-generic                         3.13.0-86.131                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-61-generic                   3.13.0-61.100                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-62-generic                   3.13.0-62.102                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-86-generic                   3.13.0-86.131                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-generic                                   3.13.0.86.92                                        i386         Generic Linux kernel image
ii  linux-libc-dev:i386                                   3.13.0-86.131                                       i386         Linux Kernel Headers for development
ii  linux-sound-base                                      1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  syslinux-common                                       3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                       2:3.63+dfsg-2ubuntu5                                i386         Bootloader for Linux/i386 using MS-DOS floppies

```

**** Also linux-headers-3.13.0-62 and linux-headers-3.13.0-62-generic missing above ?? 

```

ls -al /vmlinuz*
lrwxrwxrwx 1 root root 30 May 19 14:18 /vmlinuz -> boot/vmlinuz-3.13.0-86-generic
lrwxrwxrwx 1 root root 30 Aug 18  2015 /vmlinuz.old -> boot/vmlinuz-3.13.0-62-generic

```

```

ls -al /initrd.img*
lrwxrwxrwx 1 root root 33 May 19 14:18 /initrd.img -> boot/initrd.img-3.13.0-86-generic
lrwxrwxrwx 1 root root 33 May 19 14:09 /initrd.img.old -> boot/initrd.img-3.13.0-62-generic

```

I believe we are almost tidy here with the last 3 kernels 86 being the current and 62 & 61 being backups, but 62 is not quite all there lol. 

**** Can this be fixed ?

The real good news is before, / only 298M and 0 inodes ....

```

df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       9.3G  8.5G  298M  97% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            998M  4.0K  998M   1% /dev
tmpfs           202M  1.1M  201M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none           1007M  156K 1007M   1% /run/shm
none            100M   52K  100M   1% /run/user
/dev/sda2        61G  3.1G   54G   6% /home

df -i
Filesystem      Inodes  IUsed   IFree IUse% Mounted on
/dev/sda1       625856 625856       0  100% /
none            220045      2  220043    1% /sys/fs/cgroup
udev            215240    496  214744    1% /dev
tmpfs           220045    470  219575    1% /run
none            220045      3  220042    1% /run/lock
none            220045      7  220038    1% /run/shm
none            220045     30  220015    1% /run/user
/dev/sda2      4014080  33836 3980244    1% /home

```

and now / 3.9G and 388768 inodes....

```
 
df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            998M  4.0K  998M   1% /dev
tmpfs           202M  1.1M  201M   1% /run
/dev/sda1       9.3G  4.9G  3.9G  56% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
none            5.0M     0  5.0M   0% /run/lock
none           1007M  156K 1007M   1% /run/shm
none            100M   64K  100M   1% /run/user
/dev/sda2        61G  3.0G   55G   6% /home

df -i
Filesystem      Inodes  IUsed   IFree IUse% Mounted on
udev            215228    496  214732    1% /dev
tmpfs           220037    475  219562    1% /run
/dev/sda1       625856 237088  388768   38% /
none            220037      2  220035    1% /sys/fs/cgroup
none            220037      3  220034    1% /run/lock
none            220037      7  220030    1% /run/shm
none            220037     38  219999    1% /run/user
/dev/sda2      4014080  34658 3979422    1% /home

```

---

### Post by Bashing-om on 2016-05-20
ibod; Yeah, Uh Huh ...

Look'n much better.

And yes, let us get the -62 kernel fully installed. - Never can tell what the system might need to build that depends on it.
```

sudo apt install linux-headers-3.13.0-62 linux-headers-3.13.0-62-generic --fix-missing

```

And now what returns:
```

sudo apt update
sudo apt full-upgrade
sudo apt -f install
sudo dpkg -C

```

[INDENT][INDENT]comes back all
[INDENT][INDENT][INDENT]finer than a frog's hair ?
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Impavidus on 2016-05-20
> **ibod said:**
> 
...note the 'linux-headers-3.13.3-' in his post was intended to be 'linux-headers-3.13.0' other than that one small edit the suggestion worked well, (took some time to run :-) ). 

For the sake of correctness, I fixed that. Good you saw the typo.

---

### Post by papibe on 2016-05-20
For the record:  Bug #1089195: [linux-headers will eat your inodes on LTS]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1089195"). 

If you ran out of inodes on your root partition, the easiest way the free some of them is to delete older headers manually. For example:
```
$ ls -1d /usr/src/linux-headers-*
/usr/src/linux-headers-3.13.0-45
/usr/src/linux-headers-3.13.0-45-generic
/usr/src/linux-headers-3.13.0-46
/usr/src/linux-headers-3.13.0-46-generic
/usr/src/linux-headers-3.13.0-48
/usr/src/linux-headers-3.13.0-48-generic
/usr/src/linux-headers-3.13.0-49
/usr/src/linux-headers-3.13.0-49-generic

$ ls -1d /usr/src/linux-headers-3.13.0-4[56]*
/usr/src/linux-headers-3.13.0-45
/usr/src/linux-headers-3.13.0-45-generic
/usr/src/linux-headers-3.13.0-46
/usr/src/linux-headers-3.13.0-46-generic

$ sudo rm -rf /usr/src/linux-headers-3.13.0-4[56]*

```
Once you have freed some inodes, you can run apt-get, and dpkg to clean, remove, etc.

Regards.

---

