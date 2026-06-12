---
title: "/boot full can't remove old kernels"
date: 2014-10-04
forum: General Help
---

### Post by jason139 on 2014-10-04
```

jason@WIFI:/boot$ df
Filesystem                1K-blocks    Used Available Use% Mounted on
/dev/mapper/WIFI--vg-root 476169264 7918556 444056048   2% /
udev                        2057632       4   2057628   1% /dev
tmpfs                        413264     800    412464   1% /run
none                           5120       0      5120   0% /run/lock
none                        2066304       0   2066304   0% /run/shm
/dev/sda1                    233191  228454         0 100% /boot

```

This is the procedure I am trying to use to clean up /boot 

[COLOR=#333333][FONT=UbuntuRegular]
First check your kernel version, so you won't delete the in-use kernel image, running:
uname -r
Now run this command for a list of installed kernels:
sudo dpkg --list 'linux-image*'
and delete the kernels you don't want/need anymore by running this:
sudo apt-get remove linux-image-VERSION
Replace VERSION with the version of the kernel you want to remove.
When you're done removing the older kernels, you can run this to remove ever packages you won't need anymore:
sudo apt-get autoremove
And finally you can run this to update grub kernel list:
sudo update-grub



[/FONT][/COLOR]
```

jason@WIFI:~$ uname -r
3.8.0-39-generic
jason@WIFI:/boot$ sudo dpkg --list 'linux-image*'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
un  linux-image    <none>         (no description available)
un  linux-image-3. <none>         (no description available)
ii  linux-image-3. 3.8.0-29.42~pr Linux kernel image for version 3.8.0 on 32 b
ii  linux-image-3. 3.8.0-32.47~pr Linux kernel image for version 3.8.0 on 32 b
ii  linux-image-3. 3.8.0-33.48~pr Linux kernel image for version 3.8.0 on 32 b
ii  linux-image-3. 3.8.0-34.49~pr Linux kernel image for version 3.8.0 on 32 b
ii  linux-image-3. 3.8.0-35.52~pr Linux kernel image for version 3.8.0 on 32 b
ii  linux-image-3. 3.8.0-36.52~pr Linux kernel image for version 3.8.0 on 32 b
ii  linux-image-3. 3.8.0-37.53~pr Linux kernel image for version 3.8.0 on 32 b
ii  linux-image-3. 3.8.0-38.56~pr Linux kernel image for version 3.8.0 on 32 b
ii  linux-image-3. 3.8.0-39.57~pr Linux kernel image for version 3.8.0 on 32 b
in  linux-image-3. <none>         (no description available)
iU  linux-image-ge 3.8.0.41.41    Generic Linux kernel image
jason@WIFI:/boot$ sudo apt-get -f remove linux-image-3.8.0-29-generic



[sudo] password for jason:
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-image-generic-lts-raring : Depends: linux-image-3.8.0-41-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
jason@WIFI:/boot$

```

I tried it with -f also and if i try to remove or install any package I get 

```

The following packages have unmet dependencies:
 linux-image-generic-lts-raring : Depends: linux-image-3.8.0-41-generic but it is not going to be installed

```

---

### Post by Bashing-om on 2014-10-04
jason139; Yuk,

You appear:
> 
linux-image-generic-lts-raring : Depends: linux-image-3.8.0-41-generic but it is not going to be installed

to be running  an End-Of-Life release, 'raring' has no support.

It is highly recommended that you do a fresh install of a current release. (12.04, 14.04)

All good things
[INDENT][INDENT][INDENT]must end ( make way for newer and better)
[/INDENT][/INDENT][/INDENT]

---

### Post by Doug S on 2014-10-04
Uninstall the older kernel, not the newest one. start with 3.8.0-29.42.

---

### Post by jason139 on 2014-10-04
got it fixed, I was able to remove old kernel's with

```

sudo dpkg -P linux-image-3.8.0-{29,32,33,34,35,36,37}-generic
sudo dpkg -P linux-headers-3.8.0-{29,32,33,34,35,36,37}-generic
sudo dpkg -P linux-headers-3.8.0-{29,32,33,34,35,36,37}

```

---

