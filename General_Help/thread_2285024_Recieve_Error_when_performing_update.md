---
title: "Recieve Error when performing update"
date: 2015-07-02
forum: General Help
---

### Post by Adrian_Padilla on 2015-07-02
i Try to run a update and this is what i get from the comand line window, i looked and saw that it says full disk but there should not be a full disk, any help to clear this up would be great 

thank you 




```
root@muggles:/# sudo apt-get install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.13.0-37 linux-headers-3.13.0-37-generic
  linux-headers-3.13.0-40 linux-headers-3.13.0-40-generic
  linux-headers-3.13.0-43 linux-headers-3.13.0-43-generic
  linux-headers-3.13.0-44 linux-headers-3.13.0-44-generic
  linux-headers-3.13.0-46 linux-headers-3.13.0-46-generic
  linux-image-3.13.0-37-generic linux-image-3.13.0-40-generic
  linux-image-3.13.0-43-generic linux-image-3.13.0-44-generic
  linux-image-3.13.0-46-generic linux-image-extra-3.13.0-37-generic
  linux-image-extra-3.13.0-40-generic linux-image-extra-3.13.0-43-generic
  linux-image-extra-3.13.0-44-generic linux-image-extra-3.13.0-46-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-image-3.13.0-51-generic
Suggested packages:
  fdutils linux-doc-3.13.0 linux-source-3.13.0 linux-tools
The following NEW packages will be installed:
  linux-image-3.13.0-51-generic
0 upgraded, 1 newly installed, 0 to remove and 71 not upgraded.
26 not fully installed or removed.
Need to get 14.7 MB of archives.
After this operation, 32.7 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates/main linux-image-3.13.0-51-generic i386 3.13.0-51.84 [14.7 MB]
Fetched 14.7 MB in 57s (253 kB/s)
(Reading database ... 306042 files and directories currently installed.)
Preparing to unpack .../linux-image-3.13.0-51-generic_3.13.0-51.84_i386.deb ...
Done.
Unpacking linux-image-3.13.0-51-generic (3.13.0-51.84) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-3.13.0-51-generic_3.13.0-51.84_i386.deb (--unpack):
 cannot copy extracted data for './boot/System.map-3.13.0-51-generic' to '/boot/System.map-3.13.0-51-generic.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-51-generic /boot/vmlinuz-3.13.0-51-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-51-generic /boot/vmlinuz-3.13.0-51-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.13.0-51-generic_3.13.0-51.84_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```





ubuntu server 14.04

thank you for your help

---

### Post by deadflowr on 2015-07-03
Three things.
First, since you are already running as root, there is no need to use sudo in the apt-get command.

Second did you try the suggestion
```
apt-get autoremove
```
which will clean up the old and obsolete kernel images, and other cruft.
Doing this will clear up space.

And thirdly, if you tried the autoremove command and it still gives you problems,
 please post the out put for
```
df -h
```
and as a double check that the inodes aren't filling up
post the output for
```
df -i
```

Sidenote, but the 3.13.0-51 image seems to be somewhat old, now.
Current image I see is 3.13.0-55...
Have you an apt-get update recently?

---

### Post by Bucky Ball on 2015-07-03
@deadflowr: 3.13 is correct for installs of 14.04 rather than if you install 14.04.02. My 14.04 was installed a couple of months after release and is still running 3.13 (and I update/upgrade once or twice a week). I just did a 14.04.02 install on my new netbook and it uses 3.16. ;)

But I agree:

```
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
```

Post any and all errors.

---

### Post by deadflowr on 2015-07-03
Oh, I know that.;)
I was wondering why the version to be installed was so old.
I had to dig through some old logfiles to find when the 3.13.0-51 version came out.
That was April 30...

---

### Post by Bucky Ball on 2015-07-03
> **deadflowr said:**
> 
I was wondering why the version to be installed was so old.


Ah. :)

---

### Post by Adrian_Padilla on 2015-07-03
```
df -h results

root@muggles:~# df -h
Filesystem                Size  Used Avail Use% Mounted on
/dev/mapper/muggles-root   34G  4.1G   28G  13% /
none                      4.0K     0  4.0K   0% /sys/fs/cgroup
udev                      1.5G  4.0K  1.5G   1% /dev
tmpfs                     303M  528K  302M   1% /run
none                      5.0M     0  5.0M   0% /run/lock
none                      1.5G     0  1.5G   0% /run/shm
none                      100M     0  100M   0% /run/user
/dev/sda1                 228M  227M     0 100% /boot
```

```
df -l

root@muggles:~# df -i
Filesystem                Inodes  IUsed   IFree IUse% Mounted on
/dev/mapper/muggles-root 2232048 317642 1914406   15% /
none                      217585      2  217583    1% /sys/fs/cgroup
udev                      212592    464  212128    1% /dev
tmpfs                     217585    455  217130    1% /run
none                      217585      6  217579    1% /run/lock
none                      217585      1  217584    1% /run/shm
none                      217585      2  217583    1% /run/user
/dev/sda1                 124496    337  124159    1% /boot
```

```
results from auto remove

root@muggles:~# apt-get autoremove -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-image-3.13.0-51-generic
Suggested packages:
  fdutils linux-doc-3.13.0 linux-source-3.13.0 linux-tools
The following NEW packages will be installed:
  linux-image-3.13.0-51-generic
0 upgraded, 1 newly installed, 0 to remove and 71 not upgraded.
26 not fully installed or removed.
Need to get 0 B/14.7 MB of archives.
After this operation, 32.7 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 306042 files and directories currently installed.)
Preparing to unpack .../linux-image-3.13.0-51-generic_3.13.0-51.84_i386.deb ...
Done.
Unpacking linux-image-3.13.0-51-generic (3.13.0-51.84) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-3.13.0-51-generic_3.13.0-51.84_i386.deb (--unpack):
 cannot copy extracted data for './boot/System.map-3.13.0-51-generic' to '/boot/System.map-3.13.0-51-generic.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-51-generic /boot/vmlinuz-3.13.0-51-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-51-generic /boot/vmlinuz-3.13.0-51-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.13.0-51-generic_3.13.0-51.84_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

ive apt-get update alot and get the error shown above

---

### Post by oldos2er on 2015-07-03
Your /boot partition (228M) is full. There is info on how to remove old kernels here: [http://wernerstrydom.com/2014/01/18/ubuntu-server-12-04-cleaning-full-boot-partition/](http://wernerstrydom.com/2014/01/18/ubuntu-server-12-04-cleaning-full-boot-partition/)

---

