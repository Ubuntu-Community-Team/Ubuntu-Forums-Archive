---
title: "Fail to run &quot;apt upgrade&quot;"
date: 2018-08-15
forum: General Help
---

### Post by satimis on 2018-08-15
Hi,

Ubuntu 16.04.4 desktop

$ uname -a```

Linux ub1604 4.4.0-130-generic #156-Ubuntu SMP Thu Jun 14 08:53:28 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

```

&#10219; sudo apt upgrade```

.....
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-21 linux-headers-4.4.0-21-generic
  linux-image-4.4.0-21-generic linux-image-extra-4.4.0-21-generic
Use 'sudo apt autoremove' to remove them.
The following packages will be upgraded:
  virtualbox-5.2
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 73.5 MB of archives.
After this operation, 25.6 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Err:1 https://download.virtualbox.org/virtualbox/debian xenial/contrib amd64 virtualbox-5.2 amd64 5.2.18-124319~Ubuntu~xenial
  404  Not Found
E: Failed to fetch https://download.virtualbox.org/virtualbox/debian/pool/contrib/v/virtualbox-5.2/virtualbox-5.2_5.2.18-124319~Ubuntu~xenial_amd64.deb  404  Not Found

E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

Have tried running;
&#10219; sudo rm -rf /var/lib/apt/lists/*
&#10219; sudo apt clean
&#10219; sudo apt update

But problem still remains.  Please help.  Thanks

Regards
satimis

---

### Post by thomashansen on 2018-08-15
Same error here.
The problem is with oracle's virtualbox repository: if you go to:

[https://download.virtualbox.org/virtualbox/debian/pool/contrib/v/virtualbox-5.2/]("https://download.virtualbox.org/virtualbox/debian/pool/contrib/v/virtualbox-5.2/")

,there you are able to download the files for version 5.2.14, but all for version 5.2.18 (the one **apt** is looking for) are returning 404-not found...

---

### Post by kc1di on 2018-08-15
go to software and updates other tab and see if there is anything from virtualbox.  if there is uncheck it for the time being and retry update and upgrade.

---

### Post by satimis on 2018-08-15
> **thomashansen said:**
> Same error here.
The problem is with oracle's virtualbox repository: if you go to:

[https://download.virtualbox.org/virtualbox/debian/pool/contrib/v/virtualbox-5.2/]("https://download.virtualbox.org/virtualbox/debian/pool/contrib/v/virtualbox-5.2/")

,there you are able to download the files for version 5.2.14, but all for version 5.2.18 (the one **apt** is looking for) are returning 404-not found...
Hi,

Thanks for your advice.

VirtualBox Version```

VirtualBox Graphical User Interface
Version 5.2.16 r123759 (Qt5.6.1)
Copyright © 2018 Oracle Corporation and/or its affiliates. All rights reserved.

```

I performed following steps to install VirtualBox


Steps:-
Add following line at the bottom of /etc/apt/sources.list```

deb https://download.virtualbox.org/virtualbox/debian bionic contrib

```

$ wget -q [https://www.virtualbox.org/download/oracle_vbox_2016.asc](https://www.virtualbox.org/download/oracle_vbox_2016.asc) -O- | sudo apt-key add - ```

OK

```

$ wget -q [https://www.virtualbox.org/download/oracle_vbox.asc](https://www.virtualbox.org/download/oracle_vbox.asc) -O- | sudo apt-key add -```

OK

```

$ sudo apt-get update```

Hit:1 http://hk.archive.ubuntu.com/ubuntu bionic InRelease
Hit:2 http://hk.archive.ubuntu.com/ubuntu bionic-updates InRelease                           
Hit:3 http://hk.archive.ubuntu.com/ubuntu bionic-backports InRelease                         
Get:4 https://download.virtualbox.org/virtualbox/debian bionic InRelease [4,429 B]                                 
Get:5 http://security.ubuntu.com/ubuntu bionic-security InRelease [83.2 kB]                           
Get:6 https://download.virtualbox.org/virtualbox/debian bionic/contrib amd64 Packages [1,440 B]
Fetched 89.1 kB in 1s (71.6 kB/s)                                     
Reading package lists... Done
N: Skipping acquire of configured file 'contrib/binary-i386/Packages' as repository 'https://download.virtualbox.org/virtualbox/debian bionic InRelease' doesn't support architecture 'i386'

```

$ sudo apt-get install virtualbox-5.2```

Reading package lists... Done
Building dependency tree       
.....
Setting up gcc-7 (7.3.0-16ubuntu3) ...
Setting up gcc (4:7.3.0-3ubuntu2) ...
Setting up libqt5printsupport5:amd64 (5.9.5+dfsg-0ubuntu1) ...
Setting up libqt5opengl5:amd64 (5.9.5+dfsg-0ubuntu1) ...
Setting up libqt5svg5:amd64 (5.9.5-0ubuntu1) ...
Setting up virtualbox-5.2 (5.2.16-123759~Ubuntu~bionic) ...
Adding group `vboxusers' (GID 127) ...
Done.
Processing triggers for libc-bin (2.27-3ubuntu1) ...

```

VirtualBox Manager installed```

VirtualBox Graphical User Intertace
Version 5.2.16 r123759(Qt5.9.5)

```

What shall I do?  Delete VirtualBox Version 5.2.16 and install version 5.2.14?

Regards
satimis

---

### Post by satimis on 2018-08-15
> **kc1di said:**
> go to software and updates other tab and see if there is anything from virtualbox.  if there is uncheck it for the time being and retry update and upgrade.
Hi,

Thanks for your advice.

Performed following steps:-

-> Search your computer -> Ubuntu Software -> Updates
```

OS Updates - Includes performance, stability and security improvements
-> Install

```

After finish popup;
```

Software is up to date

```

On Terminal run;
&#10219; sudo apt update ; sudo apt upgrade```

.....
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-21 linux-headers-4.4.0-21-generic
  linux-image-4.4.0-21-generic linux-image-extra-4.4.0-21-generic
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

&#10219; sudo apt autoremove```

.....
/vmlinuz-4.4.0-21-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-21-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-21-generic /boot/vmlinuz-4.4.0-21-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-133-generic
Found initrd image: /boot/initrd.img-4.4.0-133-generic
Found linux image: /boot/vmlinuz-4.4.0-130-generic
Found initrd image: /boot/initrd.img-4.4.0-130-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
Found Ubuntu 16.04.5 LTS (16.04) on /dev/sda1
done

```

&#10219; sudo apt update ; sudo apt upgrade```

Hit:1 http://hk.archive.ubuntu.com/ubuntu xenial InRelease
Hit:2 http://hk.archive.ubuntu.com/ubuntu xenial-updates InRelease
Hit:3 http://hk.archive.ubuntu.com/ubuntu xenial-backports InRelease
Hit:4 https://download.virtualbox.org/virtualbox/debian xenial InRelease       
Hit:5 http://security.ubuntu.com/ubuntu xenial-security InRelease              
Reading package lists... Done                      
Building dependency tree       
Reading state information... Done
All packages are up to date.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Now problem solved.  Thanks again

Regards
satimis

---

### Post by kc1di on 2018-08-15
Glad you got it going.

---

### Post by thomashansen on 2018-08-16
Looks like the problem was solved by oracle itself - the link for the package is up and running now... :)

---

