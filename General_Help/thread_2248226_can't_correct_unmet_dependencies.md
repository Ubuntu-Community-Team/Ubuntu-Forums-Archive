---
title: "can't correct unmet dependencies"
date: 2014-10-13
forum: General Help
---

### Post by Rockling on 2014-10-13
Ubuntu 12.04 LTS
When i try 
sudo apt-get install - f 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-image-extra-3.2.0-61-virtual linux-headers-3.2.0-25 linux-headers-3.2.0-61 linux-headers-3.2.0-64 linux-headers-3.2.0-65
  linux-headers-3.2.0-67 linux-image-extra-3.2.0-64-virtual linux-image-extra-3.2.0-67-virtual linux-headers-3.2.0-61-virtual
  linux-image-3.2.0-61-virtual linux-headers-3.2.0-64-virtual linux-headers-3.2.0-25-virtual linux-image-3.2.0-64-virtual
  linux-image-extra-3.2.0-65-virtual linux-headers-3.2.0-67-virtual linux-image-3.2.0-67-virtual linux-headers-3.2.0-65-virtual
  linux-image-3.2.0-65-virtual
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-headers-3.2.0-70 linux-headers-3.2.0-70-virtual
The following NEW packages will be installed:
  linux-headers-3.2.0-70 linux-headers-3.2.0-70-virtual
0 upgraded, 2 newly installed, 0 to remove and 8 not upgraded.
10 not fully installed or removed.
Need to get 0 B/12.7 MB of archives.
After this operation, 67.7 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 367174 files and directories currently installed.)
Unpacking linux-headers-3.2.0-70 (from .../linux-headers-3.2.0-70_3.2.0-70.105_all.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-70_3.2.0-70.105_all.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.2.0-70/drivers/uwb/Kconfig.dpkg-new' (while processing `./usr/src/linux-headers-3.2.0-70/drivers/uwb/Kconfig'): No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking linux-headers-3.2.0-70-virtual (from .../linux-headers-3.2.0-70-virtual_3.2.0-70.105_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-70-virtual_3.2.0-70.105_i386.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.2.0-70-virtual/include/config/intel/mei.h.dpkg-new' (while processing `./usr/src/linux-headers-3.2.0-70-virtual/include/config/intel/mei.h'): No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-3.2.0-70_3.2.0-70.105_all.deb
 /var/cache/apt/archives/linux-headers-3.2.0-70-virtual_3.2.0-70.105_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

When I try sudo apt-get autoremove

```
sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-headers-virtual : Depends: linux-headers-3.2.0-70-virtual but it is not installed
E: Unmet dependencies. Try using -f.
```

Any ideas?

---

### Post by nerdtron on 2014-10-13
I see a "disk full" error, what is the output of:
```
df -Th
```

---

### Post by Bashing-om on 2014-10-13
Rockling; Hi !

This:
> 
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-70-virtual_3.2.0-70.105_i386.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.2.0-70-virtual/include/config/intel/mei.h.dpkg-new' (while processing `./usr/src/linux-headers-3.2.0-70-virtual/include/config/intel/mei.h'): [color=red]No space left on device[/color]

Should have our attention, as a place to start. No space, can do nothing 'til we have the operating head room.

let's look and see where the space is consumed, and find out the why -> and what can be done about it.
```

df -h
df -i
cd /
sudo du -sx * | sort -n
cd

```
If you need to drill down further, use 'cd' to move to a directory of interest then repeat the 'du' command.
The results are in megabytes.

[INDENT][INDENT]so a tale is told
[/INDENT][/INDENT]

---

### Post by Rockling on 2014-10-13
Thanks for the help guys. This OS was a virtual machine using virtual box and the vmdk drive file was  90% full as seen from the df -h although the home folder has almost 17G of space

```
$ df -h
Filesystem      Size  Used Avail Use% Mounted on
**/dev/sda1       6.0G  5.3G  636M  90% /**
udev            937M  4.0K  937M   1% /dev
tmpfs           189M  796K  188M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            944M  124K  944M   1% /run/shm
/dev/sdc1        20G  3.1G   17G  16% /home
09:17:17 ~$ 
```

---

### Post by Bashing-om on 2014-10-13
Rockling; Hey;

Have you removed old kernels to free up disk space ?

[INDENT]it's a thought
[/INDENT]

---

