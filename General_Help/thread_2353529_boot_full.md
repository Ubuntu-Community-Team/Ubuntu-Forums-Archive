---
title: "/boot full"
date: 2017-02-22
forum: General Help
---

### Post by Cider on 2017-02-22
So i figured out that my /boot is full. When I try and purge/delete old kernels it still complains there isnt enough space to do this. Is there anyway around this besides formatting?

```
 sudo apt-get purge linux-image-4.4.0-38-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-4.4.0-38-generic* linux-image-extra-4.4.0-38-generic*
0 upgraded, 0 newly installed, 2 to remove and 84 not upgraded.
4 not fully installed or removed.
After this operation, 218 MB disk space will be freed.
Do you want to continue? [Y/n] y
Setting up initramfs-tools (0.122ubuntu8.8) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.122ubuntu8.8) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-59-generic
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.4.0-59-generic with 1.
dpkg: error processing package initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by Bashing-om on 2017-02-22
Cider; Hummmmm ...

'dpkg' has the less operational overhead needs over that of 'apt' ..maybe we can sic dpkg on the old kernels ?
Worth a shot to see.
Post back - Between Code Tags -
```

df -h
df -i
dpkg -l | grep linux-
ls -al /boot/

```
see what we have to do and then what we can do and finally clean up .

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by Cider on 2017-02-22
Hey, 

Thank you so much for the reply. 

```
ciderza@fs1:/boot$ df -h
Filesystem                Size  Used Avail Use% Mounted on
udev                      1.9G  4.0K  1.9G   1% /dev
tmpfs                     391M  1.3M  390M   1% /run
/dev/mapper/fs1--vg-root  106G   17G   83G  17% /
none                      4.0K     0  4.0K   0% /sys/fs/cgroup
none                      5.0M     0  5.0M   0% /run/lock
none                      2.0G  8.0K  2.0G   1% /run/shm
none                      100M     0  100M   0% /run/user
cgmfs                     100K     0  100K   0% /run/cgmanager/fs
/dev/sda1                 932G  912G   21G  98% /windows
/dev/sdb2                 473M  438M   11M  98% /boot
/dev/sdb1                 511M  3.6M  508M   1% /boot/efi
tmpfs                     391M     0  391M   0% /run/user/1000
/home/ciderza/.Private    106G   17G   83G  17% /home/ciderza

ciderza@fs1:/boot$ df -i
Filesystem                 Inodes  IUsed    IFree IUse% Mounted on
udev                       495147    498   494649    1% /dev
tmpfs                      500149    594   499555    1% /run
/dev/mapper/fs1--vg-root  7004160 450094  6554066    7% /
none                       500149      3   500146    1% /sys/fs/cgroup
none                       500149      4   500145    1% /run/lock
none                       500149      3   500146    1% /run/shm
none                       500149      2   500147    1% /run/user
cgmfs                      500149     14   500135    1% /run/cgmanager/fs
/dev/sda1                21330448   6969 21323479    1% /windows
/dev/sdb2                  124928    344   124584    1% /boot
/dev/sdb1                       0      0        0     - /boot/efi
tmpfs                      500149      1   500148    1% /run/user/1000
/home/ciderza/.Private    7004160 450094  6554066    7% /home/ciderza

ciderza@fs1:/boot$ dpkg -l | grep linux-
ii  linux-base                         4.0ubuntu1                               all          Linux image base package
ii  linux-firmware                     1.157.6                                  all          Firmware for Linux kernel drivers
iU  linux-generic                      4.4.0.59.62                              amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.4.0-31             4.4.0-31.50                              all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-31-generic     4.4.0-31.50                              amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-38             4.4.0-38.57                              all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-38-generic     4.4.0-38.57                              amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-42             4.4.0-42.62                              all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-42-generic     4.4.0-42.62                              amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-45             4.4.0-45.66                              all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-45-generic     4.4.0-45.66                              amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-47             4.4.0-47.68                              all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-47-generic     4.4.0-47.68                              amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-51             4.4.0-51.72                              all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-51-generic     4.4.0-51.72                              amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-53             4.4.0-53.74                              all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-53-generic     4.4.0-53.74                              amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-57             4.4.0-57.78                              all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-57-generic     4.4.0-57.78                              amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-59             4.4.0-59.80                              all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-59-generic     4.4.0-59.80                              amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-generic              4.4.0.59.62                              amd64        Generic Linux kernel headers
ii  linux-image-4.4.0-31-generic       4.4.0-31.50                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-38-generic       4.4.0-38.57                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-42-generic       4.4.0-42.62                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-45-generic       4.4.0-45.66                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-47-generic       4.4.0-47.68                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-51-generic       4.4.0-51.72                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-53-generic       4.4.0-53.74                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-57-generic       4.4.0-57.78                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-59-generic       4.4.0-59.80                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-31-generic 4.4.0-31.50                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-38-generic 4.4.0-38.57                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-42-generic 4.4.0-42.62                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-45-generic 4.4.0-45.66                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-47-generic 4.4.0-47.68                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-51-generic 4.4.0-51.72                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-53-generic 4.4.0-53.74                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-57-generic 4.4.0-57.78                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iF  linux-image-extra-4.4.0-59-generic 4.4.0-59.80                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-generic                4.4.0.59.62                              amd64        Generic Linux kernel image

ciderza@fs1:/boot$ ls -al /boot/
total 438757
drwxr-xr-x  5 root root     3072 Feb 22 21:59 .
drwxr-xr-x 27 root root     4096 Dec  8  2011 ..
-rw-r--r--  1 root root  1240067 Jul 13  2016 abi-4.4.0-31-generic
-rw-r--r--  1 root root  1242262 Sep  6 21:52 abi-4.4.0-38-generic
-rw-r--r--  1 root root  1242701 Oct  8 05:15 abi-4.4.0-42-generic
-rw-r--r--  1 root root  1242701 Oct 19 19:34 abi-4.4.0-45-generic
-rw-r--r--  1 root root  1243086 Oct 27 01:27 abi-4.4.0-47-generic
-rw-r--r--  1 root root  1243479 Nov 24 23:12 abi-4.4.0-51-generic
-rw-r--r--  1 root root  1243479 Dec  2 21:11 abi-4.4.0-53-generic
-rw-r--r--  1 root root  1243800 Dec 10 06:04 abi-4.4.0-57-generic
-rw-r--r--  1 root root  1244118 Jan  7 02:44 abi-4.4.0-59-generic
-rw-r--r--  1 root root   189558 Jul 13  2016 config-4.4.0-31-generic
-rw-r--r--  1 root root   189732 Sep  6 21:52 config-4.4.0-38-generic
-rw-r--r--  1 root root   189760 Oct  8 05:15 config-4.4.0-42-generic
-rw-r--r--  1 root root   189760 Oct 19 19:34 config-4.4.0-45-generic
-rw-r--r--  1 root root   189809 Oct 27 01:27 config-4.4.0-47-generic
-rw-r--r--  1 root root   189877 Nov 24 23:12 config-4.4.0-51-generic
-rw-r--r--  1 root root   189877 Dec  2 21:11 config-4.4.0-53-generic
-rw-r--r--  1 root root   189991 Dec 10 06:04 config-4.4.0-57-generic
-rw-r--r--  1 root root   190047 Jan  7 02:44 config-4.4.0-59-generic
drwx------  3 root root     4096 Jan  1  1970 efi
drwxr-xr-x  5 root root     1024 Jan 13 02:20 grub
-rw-r--r--  1 root root 36919994 Dec 16 15:51 initrd.img-4.4.0-31-generic
-rw-r--r--  1 root root 37020335 Dec 16 15:51 initrd.img-4.4.0-38-generic
-rw-r--r--  1 root root 37423599 Dec 16 15:51 initrd.img-4.4.0-42-generic
-rw-r--r--  1 root root 37423607 Dec 16 15:51 initrd.img-4.4.0-45-generic
-rw-r--r--  1 root root 37469821 Dec 16 15:51 initrd.img-4.4.0-47-generic
-rw-r--r--  1 root root 37476031 Dec 16 15:50 initrd.img-4.4.0-51-generic
-rw-r--r--  1 root root 37475985 Dec 20 01:57 initrd.img-4.4.0-53-generic
-rw-r--r--  1 root root 37479278 Dec 21 06:26 initrd.img-4.4.0-57-generic
-rw-r--r--  1 root root 37480119 Jan 11 06:34 initrd.img-4.4.0-59-generic
drwx------  2 root root    12288 Sep 22 14:33 lost+found
-rw-------  1 root root  3866473 Jul 13  2016 System.map-4.4.0-31-generic
-rw-------  1 root root  3869329 Sep  6 21:52 System.map-4.4.0-38-generic
-rw-------  1 root root  3869895 Oct  8 05:15 System.map-4.4.0-42-generic
-rw-------  1 root root  3869895 Oct 19 19:34 System.map-4.4.0-45-generic
-rw-------  1 root root  3873447 Oct 27 01:27 System.map-4.4.0-47-generic
-rw-------  1 root root  3874377 Nov 24 23:12 System.map-4.4.0-51-generic
-rw-------  1 root root  3874377 Dec  2 21:11 System.map-4.4.0-53-generic
-rw-------  1 root root  3875329 Dec 10 06:04 System.map-4.4.0-57-generic
-rw-------  1 root root  3875594 Jan  7 02:44 System.map-4.4.0-59-generic
-rw-------  1 root root  7047504 Jul 13  2016 vmlinuz-4.4.0-31-generic
-rw-------  1 root root  7051680 Sep  6 21:52 vmlinuz-4.4.0-38-generic
-rw-------  1 root root  7053472 Oct  8 05:15 vmlinuz-4.4.0-42-generic
-rw-------  1 root root  7054208 Oct 19 19:34 vmlinuz-4.4.0-45-generic
-rw-------  1 root root  7060896 Oct 27 01:27 vmlinuz-4.4.0-47-generic
-rw-------  1 root root  7064208 Nov 24 23:12 vmlinuz-4.4.0-51-generic
-rw-------  1 root root  7065648 Dec  2 21:11 vmlinuz-4.4.0-53-generic
-rw-------  1 root root  7067152 Dec 10 06:04 vmlinuz-4.4.0-57-generic
-rw-------  1 root root  7069136 Jan  7 02:44 vmlinuz-4.4.0-59-generic
ciderza@fs1:/boot$ 
```

---

### Post by Bashing-om on 2017-02-22
Cider; Hey ;

Sorry for the delay in getting back to ya ... busy busy busy ..


Let's try the easier means - see if the package manager will work for us :
```

sudo apt autoremove

```

else we do different .. long hard way to also do this.

[INDENT][INDENT]there is a way
[/INDENT][/INDENT]

---

### Post by Cider on 2017-02-22
tried autoremove already - same story :(

---

### Post by Bashing-om on 2017-02-22
Cider; Ho Kay;

Then we roll our sleeves up and go to work :
show me a new:
```

sudo dpkg -l | grep linux-

```
between code tags to maintain the formatting - so I can easier work with it . We got our work cut out for us:
code tag tutorial:
[http://ubuntuforums.org/showthread.php](http://ubuntuforums.org/showthread.php)

make this as painless 
[INDENT][INDENT][INDENT]as possible
[/INDENT][/INDENT][/INDENT]

---

### Post by Cider on 2017-02-22
```
ciderza@fs1:/$ sudo dpkg -l | grep linux-
[sudo] password for ciderza: 
ii  linux-base                         4.0ubuntu1                               all          Linux image base package
ii  linux-firmware                     1.157.6                                  all          Firmware for Linux kernel drivers
iU  linux-generic                      4.4.0.59.62                              amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.4.0-31             4.4.0-31.50                              all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-31-generic     4.4.0-31.50                              amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-38             4.4.0-38.57                              all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-38-generic     4.4.0-38.57                              amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-42             4.4.0-42.62                              all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-42-generic     4.4.0-42.62                              amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-45             4.4.0-45.66                              all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-45-generic     4.4.0-45.66                              amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-47             4.4.0-47.68                              all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-47-generic     4.4.0-47.68                              amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-51             4.4.0-51.72                              all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-51-generic     4.4.0-51.72                              amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-53             4.4.0-53.74                              all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-53-generic     4.4.0-53.74                              amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-57             4.4.0-57.78                              all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-57-generic     4.4.0-57.78                              amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-59             4.4.0-59.80                              all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-59-generic     4.4.0-59.80                              amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-generic              4.4.0.59.62                              amd64        Generic Linux kernel headers
ii  linux-image-4.4.0-31-generic       4.4.0-31.50                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-38-generic       4.4.0-38.57                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-42-generic       4.4.0-42.62                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-45-generic       4.4.0-45.66                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-47-generic       4.4.0-47.68                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-51-generic       4.4.0-51.72                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-53-generic       4.4.0-53.74                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-57-generic       4.4.0-57.78                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-59-generic       4.4.0-59.80                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-31-generic 4.4.0-31.50                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-38-generic 4.4.0-38.57                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-42-generic 4.4.0-42.62                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-45-generic 4.4.0-45.66                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-47-generic 4.4.0-47.68                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-51-generic 4.4.0-51.72                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-53-generic 4.4.0-53.74                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-57-generic 4.4.0-57.78                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iF  linux-image-extra-4.4.0-59-generic 4.4.0-59.80                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-generic                4.4.0.59.62                              amd64        Generic Linux kernel image



```

---

### Post by ajgreeny on 2017-02-22
Hi Cider.
Lets try command ```
sudo dpkg -P linux-image-extra-4.4.0-31-generic linux-image-4.4.0-31-generic
```to see if we are going to get dpkg to work for you.
If that command works it will then be worth trying the ```
sudo apt autoremove
``` again as it might work now you have made some more space.
Once you have removed the linux-images you can also remove the linux-header packages for all except the two most recent versions.

Keep up the good dpkg work Bashing-om; we keep seeing this problem still, even though it should normally be fixed automatically in newer versions if unattended-upgrades are enabled and configured to do this job for the user with no user-input.

---

### Post by Bashing-om on 2017-02-22
Cider; Much better to read, no ?

Ok
Try:
```

sudo dpkg -P linux-image{,-extra}-4.4.0-{31,38,42,45,47,51,53}-generic linux-headers-4.4.0-{31,38,42,45,47,51,53}{,-generic}

```

see what results . post any errors.

[INDENT][INDENT]andddd away we go
[/INDENT][/INDENT]

---

### Post by ajgreeny on 2017-02-22
Great job B-om, I forgot about the bracketed command possibility so left it at the single version followed by autoremove.
Let's hope one or other will do the job; perhaps both commands would have done so.

---

### Post by Cider on 2017-02-22
Thank you - it seemed to do the trick. 

```
ciderza@fs1:/$ df -h /boot
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdb2       473M  105M  344M  24% /boot
```

May I ask why it originally didnt want to let me remove it?

---

### Post by Bashing-om on 2017-02-22
@ajgreeny;   :)
Sometimes I just take a leap of faith . Other times I too take a gentle poke at it .

@Cider: ,,, well ..

> 
May I ask why it originally didnt want to let me remove it? 

seems dpkg does not require the operational overhead that apt can work in ,, and also that we gave dpkg a different bite on the situation.
Still left is the follow through as AJ advises.

what now:
```

sudo apt autoremove
sudo apt update
sudo apt full-upgrade

```

[INDENT][INDENT][INDENT]fat lady sing'n ?
[/INDENT][/INDENT][/INDENT]

---

### Post by Cider on 2017-02-22
Already ran the update/upgrade and all is working. 

Thank you very much for your help.

---

### Post by Bashing-om on 2017-02-22
Cider; Outstanding !


Glad to be of some small amount of assistance - all in this together ... Go team !
Next time around, you can show me a thing or 3 :)

for now as " and all is working. "
Let's close this thread:

Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]just keep on keep'n on
[/INDENT][/INDENT]

---

