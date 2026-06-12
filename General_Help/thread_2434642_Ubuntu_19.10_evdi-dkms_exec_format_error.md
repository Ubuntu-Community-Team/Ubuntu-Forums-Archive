---
title: "Ubuntu 19.10 evdi-dkms exec format error"
date: 2020-01-08
forum: General Help
---

### Post by wilkinsw on 2020-01-08
I am having an issue with the evdi-dkms package installed with apt.

Installation seems okay:
```

$ sudo apt install evdi-dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  evdi-dkms
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 25.3 kB of archives.
After this operation, 137 kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan/universe amd64 evdi-dkms all 1.6.0+dfsg-1ubuntu2 [25.3 kB]
Fetched 25.3 kB in 1s (29.6 kB/s)    
Selecting previously unselected package evdi-dkms.
(Reading database ... 283362 files and directories currently installed.)
Preparing to unpack .../evdi-dkms_1.6.0+dfsg-1ubuntu2_all.deb ...
Unpacking evdi-dkms (1.6.0+dfsg-1ubuntu2) ...
Setting up evdi-dkms (1.6.0+dfsg-1ubuntu2) ...
Loading new evdi-1.6.0+dfsg DKMS files...
Building for 4.15.0-1065-oem
Building initial module for 4.15.0-1065-oem
Secure Boot not enabled on this system.
Done.

evdi.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.15.0-1065-oem/updates/dkms/

depmod...

DKMS: install completed.

```

But when I try to activate the module I get the following error:
```

sudo modprobe evdi -v
insmod /lib/modules/4.15.0-1065-oem/updates/dkms/evdi.ko 
modprobe: ERROR: could not insert 'evdi': Exec format error

```

This is preventing my DisplayLink driver from working.  The issue popped up a month or two ago and I waited awhile to see if another update would resolve the problem, but no luck.

I have tried purging and building the module from the github source as well as the source provided by DisplayLink, but both attempts met with the same error.

Here's some system information:
```

$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 19.10
Release:    19.10
Codename:    eoan

$ uname -r
4.15.0-1065-oem

$ dkms status evdi
evdi, 1.6.0+dfsg, 4.15.0-1065-oem, x86_64: installed

```

Could anyone suggest any additional steps for troubleshooting?

Thanks!
Wilkins

---

### Post by vgerris on 2020-04-10
Hi, it could be the module was compiled against another kernel.
Also, check if libdrm-dev package is installed.
Then reinstall the package by entering in a shell:

sudo apt install --reinstall evdi-dkms

For me that loads the module too.
Unfortunately, my screen on the D6000 dock doesn work with the displayport output.
Anyone has that working?

---

