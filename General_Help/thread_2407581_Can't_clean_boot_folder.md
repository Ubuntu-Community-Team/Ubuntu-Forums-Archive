---
title: "Can't clean /boot folder"
date: 2018-12-06
forum: General Help
---

### Post by lipesmile on 2018-12-06
I'm trying to install vsftpd on Ubuntu 18.04 LTS, but when I run apt-get install vsftpd I get this error:

```
    You might want to run apt --fix-broken install to correct these.
    
    The following packages have unmet dependencies:

    linux-image-generic : Depends: linux-image-4.15.0-42-generic but it is not going to be installed
    
    Recommends: thermald but it is not going to be installed
    linux-modules-extra-4.15.0-39-generic : Depends: linux-image-4.15.0-39-generic but it is not going to be installed or
    
    linux-image-unsigned-4.15.0-39-generic but it is not going to be installed
    
    linux-modules-extra-4.15.0-42-generic : Depends: linux-image-4.15.0-42-generic but it is not going to be installed or
    
    linux-image-unsigned-4.15.0-42-generic but it is not going to be installed
    
    E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).


```

I've tried run apt --fix-broken install and apt-get install -f vsftpd but with no sucess.


df -h output:

```
    Filesystem      Size  Used Avail Use% Mounted on
    /dev/root        39G  7.3G   30G  21% /
    devtmpfs        989M     0  989M   0% /dev
    tmpfs           992M     0  992M   0% /dev/shm
    tmpfs           992M  680K  992M   1% /run
    tmpfs           5.0M     0  5.0M   0% /run/lock
    tmpfs           992M     0  992M   0% /sys/fs/cgroup
    /dev/xvda1      232M  224M     0 100% /boot
    tmpfs           199M     0  199M   0% /run/user/0
```

df -i output:

```
    Filesystem      Inodes  IUsed   IFree IUse% Mounted on
    /dev/root      2537760 337826 2199934   14% /
    devtmpfs        253100    434  252666    1% /dev
    tmpfs           253889      1  253888    1% /dev/shm
    tmpfs           253889    606  253283    1% /run
    tmpfs           253889      4  253885    1% /run/lock
    tmpfs           253889     18  253871    1% /sys/fs/cgroup
    /dev/xvda1       62248    326   61922    1% /boot
    tmpfs           253889     10  253879    1% /run/user/0
```


apt-cache policy linux-image-generic output:

```
    linux-image-generic:
      Installed: 4.15.0.42.44
      Candidate: 4.15.0.42.44
      Version table:
     *** 4.15.0.42.44 500
            500 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 Packages
            500 http://security.ubuntu.com/ubuntu bionic-security/main amd64 Packages
            100 /var/lib/dpkg/status
         4.15.0.20.23 500
            500 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 Packages
         4.4.0.139.145 500
            500 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages
```

uname -r output:

```
    4.15.0-36-generic
```

I also tried this command:

```
    dpkg -l linux-image-\* | grep ^ii
```

it shows only one kernel:
```

    ii  linux-image-4.15.0-36-generic          4.15.0-36.39  amd64        Signed kernel image generic
```

When I try to remove:

```
    apt-get remove linux-image-4.15.0-36-generic
```

The return is:

```
    ou might want to run 'apt --fix-broken install' to correct these.
    The following packages have unmet dependencies:
     linux-image-generic : Depends: linux-image-4.15.0-42-generic but it is not going to be installed
                           Recommends: thermald but it is not going to be installed
     linux-modules-extra-4.15.0-36-generic : Depends: linux-image-4.15.0-36-generic but it is not going to be installed or
                                                      linux-image-unsigned-4.15.0-36-generic but it is not going to be installed
     linux-modules-extra-4.15.0-39-generic : Depends: linux-image-4.15.0-39-generic but it is not going to be installed or
                                                      linux-image-unsigned-4.15.0-39-generic but it is not going to be installed
     linux-modules-extra-4.15.0-42-generic : Depends: linux-image-4.15.0-42-generic but it is not going to be installed or
                                                      linux-image-unsigned-4.15.0-42-generic but it is not going to be installed
    E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
```

---

### Post by TheFu on 2018-12-06
```
/dev/xvda1      232M  224M     0 100% /boot
```
shows that /boot is full.


I have 2 kernels on a debian server in my /boot/ and it looks like this:```

$ df -h .
Filesystem      Size  Used Avail Use% Mounted on
/dev/vda1       228M   53M  164M  25% /boot

and

$ ll
total 43362
drwxr-xr-x  4 root root     1024 Nov 20 06:30 ./
drwxr-xr-x 23 root root     4096 Oct  5 06:30 ../
-rw-r--r--  1 root root   157842 Jul 14 17:45 config-3.16.0-6-amd64
-rw-r--r--  1 root root   157842 Oct  4 09:42 config-3.16.0-7-amd64
drwxr-xr-x  5 root root     5120 Oct  6 10:04 grub/
-rw-r--r--  1 root root 16077029 Jul 15 06:49 initrd.img-3.16.0-6-amd64
-rw-r--r--  1 root root 16079820 Nov 20 06:30 initrd.img-3.16.0-7-amd64
drwxr-xr-x  2 root root    12288 Apr  7  2016 lost+found/
-rw-r--r--  1 root root  2684515 Jul 14 17:45 System.map-3.16.0-6-amd64
-rw-r--r--  1 root root  2686499 Oct  4 09:42 System.map-3.16.0-7-amd64
-rw-r--r--  1 root root  3172432 Jul 14 17:44 vmlinuz-3.16.0-6-amd64
-rw-r--r--  1 root root  3174656 Oct  4 09:39 vmlinuz-3.16.0-7-amd64

```
shows the expected files.  So something larger than expected is down there on your box.  Start looking for files that don't belong.  Perhaps an fsck is needed for that file system?  How big is /boot/lost+found?

I'm guessing you are running this inside some virtual machine - perhaps Xen?

Fix the space issue first.

---

### Post by Impavidus on 2018-12-06
Don't remove linux-image-4.15.0-36-generic. It's the kernel you're currently running and the only one correctly installed. Fortunately, your command to remove it failed.

First have a look at all the kernel packages not correctly installed:```
dpkg --list linux-\*
```Make sure you've got a big terminal window, so that all the output fits. Then we'll see which packages to remove.

---

### Post by lipesmile on 2018-12-10
I raw the command and the output is this:
```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  linux-base     4.5ubuntu1   all          Linux image base package
un  linux-doc-4.15 <none>       <none>       (no description available)
ii  linux-firmware 1.173.1      all          Firmware for Linux kernel drivers
un  linux-firmware <none>       <none>       (no description available)
iU  linux-generic  4.15.0.42.44 amd64        Complete Generic Linux kernel and
un  linux-headers  <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
iU  linux-headers- 4.15.0-30.32 all          Header files related to Linux ker
un  linux-headers- <none>       <none>       (no description available)
iU  linux-headers- 4.15.0-32.35 all          Header files related to Linux ker
ii  linux-headers- 4.15.0-32.35 amd64        Linux kernel headers for version
iU  linux-headers- 4.15.0-33.36 all          Header files related to Linux ker
ii  linux-headers- 4.15.0-33.36 amd64        Linux kernel headers for version
ii  linux-headers- 4.15.0-36.39 all          Header files related to Linux ker
ii  linux-headers- 4.15.0-36.39 amd64        Linux kernel headers for version
iU  linux-headers- 4.15.0-39.42 all          Header files related to Linux ker
ii  linux-headers- 4.15.0-39.42 amd64        Linux kernel headers for version
iU  linux-headers- 4.15.0-42.45 all          Header files related to Linux ker
ii  linux-headers- 4.15.0-42.45 amd64        Linux kernel headers for version
ii  linux-headers- 4.15.0.42.44 amd64        Generic Linux kernel headers
un  linux-image    <none>       <none>       (no description available)
ri  linux-image-4. 4.15.0-30.32 amd64        Signed kernel image generic
ri  linux-image-4. 4.15.0-32.35 amd64        Signed kernel image generic
ri  linux-image-4. 4.15.0-33.36 amd64        Signed kernel image generic
ii  linux-image-4. 4.15.0-36.39 amd64        Signed kernel image generic
in  linux-image-4. <none>       amd64        (no description available)
in  linux-image-4. <none>       amd64        (no description available)
un  linux-image-4. <none>       <none>       (no description available)
rc  linux-image-ex 4.4.0-124.14 amd64        Linux kernel extra modules for ve
iU  linux-image-ge 4.15.0.42.44 amd64        Generic Linux kernel image
un  linux-image-un <none>       <none>       (no description available)
un  linux-image-un <none>       <none>       (no description available)
un  linux-image-un <none>       <none>       (no description available)
un  linux-image-un <none>       <none>       (no description available)
un  linux-image-un <none>       <none>       (no description available)
un  linux-image-un <none>       <none>       (no description available)
un  linux-initramf <none>       <none>       (no description available)
un  linux-kernel-h <none>       <none>       (no description available)
un  linux-kernel-l <none>       <none>       (no description available)
ii  linux-libc-dev 4.15.0-39.42 amd64        Linux Kernel Headers for developm
ii  linux-modules- 4.15.0-30.32 amd64        Linux kernel extra modules for ve
ii  linux-modules- 4.15.0-32.35 amd64        Linux kernel extra modules for ve
ii  linux-modules- 4.15.0-33.36 amd64        Linux kernel extra modules for ve
ii  linux-modules- 4.15.0-36.39 amd64        Linux kernel extra modules for ve
in  linux-modules- <none>       amd64        (no description available)
in  linux-modules- <none>       amd64        (no description available)
ii  linux-modules- 4.15.0-30.32 amd64        Linux kernel extra modules for ve
ii  linux-modules- 4.15.0-32.35 amd64        Linux kernel extra modules for ve
ii  linux-modules- 4.15.0-33.36 amd64        Linux kernel extra modules for ve
ii  linux-modules- 4.15.0-36.39 amd64        Linux kernel extra modules for ve
iU  linux-modules- 4.15.0-39.42 amd64        Linux kernel extra modules for ve
iU  linux-modules- 4.15.0-42.45 amd64        Linux kernel extra modules for ve
un  linux-restrict <none>       <none>       (no description available)
un  linux-source-4 <none>       <none>       (no description available)
un  linux-tools    <none>       <none>       (no description available)


```

---

### Post by CatKiller on 2018-12-10
It's all those linux-headers and linux-modules packages for Linux versions other than the one you're using that you want to remove. The other versions of linux-image have been marked for removal, but haven't yet been removed. Once you're down to just the one complete set of packages for the one version of Linux, you should have the space to upgrade to the newest version of Linux, which is what your initial install request required.

---

### Post by Impavidus on 2018-12-10
It would have been easier if you had made the terminal window a bit larger to make the output fit, but I think this will help to remove some old kernels:```
sudo dpkg --purge linux-image-4.15.0-30-generic linux-modules-4.15.0-30-generic linux-modules-extra-4.15.0-30-generic
sudo dpkg --purge linux-image-4.15.0-32-generic linux-modules-4.15.0-32-generic linux-modules-extra-4.15.0-32-generic
sudo dpkg --purge linux-image-4.15.0-33-generic linux-modules-4.15.0-33-generic linux-modules-extra-4.15.0-33-generic
```
You can, in the same way, remove the linux-headers-* packages with those version numbers and also all kernel and header packages with version number 4.15.0-39 and 4.4.0-124, which is a leftover from before your last release upgrade. Just keep 4.15.0-36 (your current kernel) and 4.15.0-42 (the new one you want to get installed).

Then show the output of```
dpkg --list linux-\*
df -h
```This time, make the terminal window big, so we get full output. With a bit of luck, you can then fix the package manager with```
sudo apt install -f
```

---

### Post by TheFu on 2018-12-10
```
sudo apt autoremove
``` and 
```
sudo apt autoclean
```
will probably remove all the stuff that isn't needed anymore, if the APT DB isn't too messed up.  Those commands can't hurt.

**apt-get** allows using regex pattern matching on package names, unlike the other "apt" commands.

---

### Post by lipesmile on 2018-12-11
I've tried this commands but with no sucess, this linux heardes still there.

---

### Post by Impavidus on 2018-12-12
So what do you get from the commands I gave you in post #6? The full output may help.

Note that there was a small error in the first three commands, as they need sudo. I fixed the above post. You can run them again; it can't hurt.

---

### Post by lipesmile on 2018-12-12
> **Impavidus said:**
> So what do you get from the commands I gave you in post #6? The full output may help.

Note that there was a small error in the first three commands, as they need sudo. I fixed the above post. You can run them again; it can't hurt.

I ran the commands as root and they return this for me:

```
# dpkg --purge linux-image-4.15.0-30-generic linux-modules-4.15.0-30-generic linux-modules-extra-4.15.0-30-generic
dpkg: warning: ignoring request to remove linux-image-4.15.0-30-generic which isn't installed
dpkg: warning: ignoring request to remove linux-modules-4.15.0-30-generic which isn't installed
dpkg: warning: ignoring request to remove linux-modules-extra-4.15.0-30-generic which isn't installed
# sudo dpkg --purge linux-image-4.15.0-32-generic linux-modules-4.15.0-32-generic linux-modules-extra-4.15.0-32-generic
dpkg: warning: ignoring request to remove linux-image-4.15.0-32-generic which isn't installed
dpkg: warning: ignoring request to remove linux-modules-4.15.0-32-generic which isn't installed
dpkg: warning: ignoring request to remove linux-modules-extra-4.15.0-32-generic which isn't installed
# sudo dpkg --purge linux-image-4.15.0-33-generic linux-modules-4.15.0-33-generic linux-modules-extra-4.15.0-33-generic
dpkg: warning: ignoring request to remove linux-image-4.15.0-33-generic which isn't installed
dpkg: warning: ignoring request to remove linux-modules-4.15.0-33-generic which isn't installed
dpkg: warning: ignoring request to remove linux-modules-extra-4.15.0-33-generic which isn't installed
```

---

### Post by deadflowr on 2018-12-12
The packages in question are listed as ri which means the desired state is removed (r) but the actual state is installed (i).
The output for those though is cut so it's unclear what they really are and the description shows them as signed kernels.
So lets look at those with this
```
dpkg -l | grep linux | awk '/^ri/{print $1,$2}'
```
it will list the 3 problem packages full names.

---

### Post by lipesmile on 2018-12-13
> **deadflowr said:**
> The packages in question are listed as ri which means the desired state is removed (r) but the actual state is installed (i).
The output for those though is cut so it's unclear what they really are and the description shows them as signed kernels.
So lets look at those with this
```
dpkg -l | grep linux | awk '/^ri/{print $1,$2}'
```
it will list the 3 problem packages full names.

I ran this command and it didn't return nothing

```

# dpkg -l | grep linux | awk '/^ri/{print $1,$2}'
# 
```

---

### Post by Impavidus on 2018-12-13
It seems that the state of your package manager has changed since your post of 2 days ago. So again, to finally get some useful diagnostics,```
dpkg --list | grep linux-
```

---

### Post by lipesmile on 2018-12-13
> **Impavidus said:**
> It seems that the state of your package manager has changed since your post of 2 days ago. So again, to finally get some useful diagnostics,```
dpkg --list | grep linux-
```

@Impavidus I ran the command and the output was this:
```
# dpkg --list | grep linux-
ii  binutils-x86-64-linux-gnu             2.30-21ubuntu1~18.04               amd64        GNU binary utilities, for x86-64-linux-gnu target
ii  linux-base                            4.5ubuntu1                         all          Linux image base package
ii  linux-firmware                        1.173.1                            all          Firmware for Linux kernel drivers
iU  linux-generic                         4.15.0.42.44                       amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.15.0-30               4.15.0-30.32                       all          Header files related to Linux kernel version 4.15.0
ii  linux-headers-4.15.0-32               4.15.0-32.35                       all          Header files related to Linux kernel version 4.15.0
ii  linux-headers-4.15.0-32-generic       4.15.0-32.35                       amd64        Linux kernel headers for version 4.15.0 on 64 bit x86 SMP
ii  linux-headers-4.15.0-33               4.15.0-33.36                       all          Header files related to Linux kernel version 4.15.0
ii  linux-headers-4.15.0-33-generic       4.15.0-33.36                       amd64        Linux kernel headers for version 4.15.0 on 64 bit x86 SMP
ii  linux-headers-4.15.0-36               4.15.0-36.39                       all          Header files related to Linux kernel version 4.15.0
ii  linux-headers-4.15.0-36-generic       4.15.0-36.39                       amd64        Linux kernel headers for version 4.15.0 on 64 bit x86 SMP
ii  linux-headers-4.15.0-39               4.15.0-39.42                       all          Header files related to Linux kernel version 4.15.0
ii  linux-headers-4.15.0-39-generic       4.15.0-39.42                       amd64        Linux kernel headers for version 4.15.0 on 64 bit x86 SMP
ii  linux-headers-4.15.0-42               4.15.0-42.45                       all          Header files related to Linux kernel version 4.15.0
ii  linux-headers-4.15.0-42-generic       4.15.0-42.45                       amd64        Linux kernel headers for version 4.15.0 on 64 bit x86 SMP
ii  linux-headers-generic                 4.15.0.42.44                       amd64        Generic Linux kernel headers
ii  linux-image-4.15.0-36-generic         4.15.0-36.39                       amd64        Signed kernel image generic
iU  linux-image-generic                   4.15.0.42.44                       amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                  4.15.0-39.42                       amd64        Linux Kernel Headers for development
ii  linux-modules-4.15.0-36-generic       4.15.0-36.39                       amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-extra-4.15.0-36-generic 4.15.0-36.39                       amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
iU  linux-modules-extra-4.15.0-39-generic 4.15.0-39.42                       amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
iU  linux-modules-extra-4.15.0-42-generic 4.15.0-42.45                       amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP

```

---

### Post by Impavidus on 2018-12-13
Some old stuff was removed. Now, maybe you have enough free space on your /boot partition. Try```
sudo apt install -f
```That may complete installation of the new kernel packages. Then, run```
dpkg --list | grep linux-
df -h
```to see where you're now.

---

### Post by TheFu on 2018-12-13
```
sudo apt-get remove linux-headers-4.15.0-3[0-8]* linux-modules-extra-4.15.0-3*
```
will remove the unneeded headers and some old modules.

Then ```
sudo apt autoremove && sudo apt autoclean
```

But the headers aren't stored in /boot/.  They are in /usr/.  Same for modules.

If there are excess files in /boot/ now, beyond the 1 kernel that remains, please post that list of files **ls -l /boot/** so we can specify which are safe to manually remove.  Hopefully, those files were already cleaned up by the prior commands.

---

### Post by lipesmile on 2018-12-13
I ran all the commands and I let the results here, I try to use tha tag spoiler to hide these big outputs, but appears this forum doens't have this tag.

apt install -f didn't work:

```
dpkg: error processing archive /var/cache/apt/archives/linux-image-4.15.0-39-generic_4.15.0-39.42_amd64.deb (--unpack):
 cannot copy extracted data for './boot/vmlinuz-4.15.0-39-generic' to '/boot/vmlinuz-4.15.0-39-generic.dpkg-new': failed to write (No space left on device)
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: paste subprocess was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-modules-4.15.0-42-generic_4.15.0-42.45_amd64.deb
 /var/cache/apt/archives/linux-image-4.15.0-42-generic_4.15.0-42.45_amd64.deb
 /var/cache/apt/archives/linux-modules-4.15.0-39-generic_4.15.0-39.42_amd64.deb
 /var/cache/apt/archives/linux-image-4.15.0-39-generic_4.15.0-39.42_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

apt autoremove && sudo apt autoclean:
```
# apt autoremove && sudo apt autoclean
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 linux-image-generic : Depends: linux-image-4.15.0-42-generic but it is not installed
                       Recommends: thermald but it is not installed
 linux-modules-extra-4.15.0-39-generic : Depends: linux-image-4.15.0-39-generic but it is not installed or
                                                  linux-image-unsigned-4.15.0-39-generic but it is not installed
 linux-modules-extra-4.15.0-42-generic : Depends: linux-image-4.15.0-42-generic but it is not installed or
                                                  linux-image-unsigned-4.15.0-42-generic but it is not installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
```

The result of  dpkg --list | grep linux-
```
# dpkg --list | grep linux-
ii  binutils-x86-64-linux-gnu             2.30-21ubuntu1~18.04               amd64        GNU binary utilities, for x86-64-linux-gnu target
ii  linux-base                            4.5ubuntu1                         all          Linux image base package
ii  linux-firmware                        1.173.1                            all          Firmware for Linux kernel drivers
iU  linux-generic                         4.15.0.42.44                       amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.15.0-30               4.15.0-30.32                       all          Header files related to Linux kernel version 4.15.0
ii  linux-headers-4.15.0-32               4.15.0-32.35                       all          Header files related to Linux kernel version 4.15.0
ii  linux-headers-4.15.0-32-generic       4.15.0-32.35                       amd64        Linux kernel headers for version 4.15.0 on 64 bit x86 SMP
ii  linux-headers-4.15.0-33               4.15.0-33.36                       all          Header files related to Linux kernel version 4.15.0
ii  linux-headers-4.15.0-33-generic       4.15.0-33.36                       amd64        Linux kernel headers for version 4.15.0 on 64 bit x86 SMP
ii  linux-headers-4.15.0-36               4.15.0-36.39                       all          Header files related to Linux kernel version 4.15.0
ii  linux-headers-4.15.0-36-generic       4.15.0-36.39                       amd64        Linux kernel headers for version 4.15.0 on 64 bit x86 SMP
ii  linux-headers-4.15.0-39               4.15.0-39.42                       all          Header files related to Linux kernel version 4.15.0
ii  linux-headers-4.15.0-39-generic       4.15.0-39.42                       amd64        Linux kernel headers for version 4.15.0 on 64 bit x86 SMP
ii  linux-headers-4.15.0-42               4.15.0-42.45                       all          Header files related to Linux kernel version 4.15.0
ii  linux-headers-4.15.0-42-generic       4.15.0-42.45                       amd64        Linux kernel headers for version 4.15.0 on 64 bit x86 SMP
ii  linux-headers-generic                 4.15.0.42.44                       amd64        Generic Linux kernel headers
ii  linux-image-4.15.0-36-generic         4.15.0-36.39                       amd64        Signed kernel image generic
iU  linux-image-generic                   4.15.0.42.44                       amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                  4.15.0-39.42                       amd64        Linux Kernel Headers for development
ii  linux-modules-4.15.0-36-generic       4.15.0-36.39                       amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-extra-4.15.0-36-generic 4.15.0-36.39                       amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
iU  linux-modules-extra-4.15.0-39-generic 4.15.0-39.42                       amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
iU  linux-modules-extra-4.15.0-42-generic 4.15.0-42.45                       amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP

```

df -h
```
Filesystem      Size  Used Avail Use% Mounted on
/dev/root        39G  7.7G   29G  22% /
devtmpfs        989M     0  989M   0% /dev
tmpfs           992M     0  992M   0% /dev/shm
tmpfs           992M  640K  992M   1% /run
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs           992M     0  992M   0% /sys/fs/cgroup
/dev/xvda1      232M  224M     0 100% /boot
tmpfs           199M     0  199M   0% /run/user/0

```

The result of ls -l /boot/
```
 #  ls -l /boot/
total 219654
-rw-r--r-- 1 root root  1536934 Apr 24  2018 abi-4.15.0-20-generic
-rw-r--r-- 1 root root  1537050 May 23  2018 abi-4.15.0-23-generic
-rw-r--r-- 1 root root  1537161 Jul 26 12:20 abi-4.15.0-30-generic
-rw-r--r-- 1 root root  1537455 Aug 10 14:22 abi-4.15.0-32-generic
-rw-r--r-- 1 root root  1537455 Aug 15 09:50 abi-4.15.0-33-generic
-rw-r--r-- 1 root root  1537821 Sep 24 11:08 abi-4.15.0-36-generic
-rw-r--r-- 1 root root   216807 Jul 26 12:20 config-4.15.0-30-generic
-rw-r--r-- 1 root root   216860 Aug 10 14:22 config-4.15.0-32-generic
-rw-r--r-- 1 root root   216905 Aug 15 09:50 config-4.15.0-33-generic
-rw-r--r-- 1 root root   216954 Sep 24 11:08 config-4.15.0-36-generic
drwxr-xr-x 5 root root     1024 Dec  5 01:12 grub
-rw-r--r-- 1 root root 55190450 Oct  7 17:12 initrd.img-4.15.0-30-generic
-rw-r--r-- 1 root root 55190881 Oct  7 17:13 initrd.img-4.15.0-32-generic
-rw-r--r-- 1 root root 55189955 Oct  7 17:13 initrd.img-4.15.0-33-generic
drwx------ 2 root root    12288 Sep 19  2016 lost+found
-rw-r--r-- 1 root root        0 Jul 26 12:20 retpoline-4.15.0-30-generic
-rw-r--r-- 1 root root        0 Aug 10 14:22 retpoline-4.15.0-32-generic
-rw-r--r-- 1 root root        0 Aug 15 09:50 retpoline-4.15.0-33-generic
-rw-r--r-- 1 root root        0 Sep 24 11:08 retpoline-4.15.0-36-generic
-rw------- 1 root root  4040419 Jul 26 12:20 System.map-4.15.0-30-generic
-rw------- 1 root root  4042389 Aug 10 14:22 System.map-4.15.0-32-generic
-rw------- 1 root root  4042247 Aug 15 09:50 System.map-4.15.0-33-generic
-rw------- 1 root root  4046393 Sep 24 11:08 System.map-4.15.0-36-generic
-rw------- 1 root root  8257272 Jul 27 03:51 vmlinuz-4.15.0-30-generic
-rw------- 1 root root  8265464 Aug 10 14:35 vmlinuz-4.15.0-32-generic
-rw------- 1 root root  8265464 Aug 15 09:57 vmlinuz-4.15.0-33-generic
-rw------- 1 root root  8277752 Sep 24 12:54 vmlinuz-4.15.0-36-generic
```

---

### Post by TheFu on 2018-12-14
Out of all the commands, the most important to be run was missed:
```
sudo apt-get remove linux-headers-4.15.0-3[0-8]* linux-modules-extra-4.15.0-3*
```

Then run the other commands that I listed.
Please.  With each of us suggesting commands, it can be confusing.  You have a halfway-installed kernel based on the error. It failed because there isn't any free space in /boot.  

I'm suggesting that we work backwards and remove the old headers and old kernel modules. These are tied to older kernels.  We aren't touching the vmlinuz-4.15.0-36-generic kernel, headers or modules.  

The the apt autoremove will see that the headers are gone and should be able to remove the older kernels in /boot/.  Then the error
> You might want to run 'apt --fix-broken install' to correct these.
should be followed:
```
sudo apt --fix-broken install
```
 Until some space is freed in /boot/ we can't fix broken packages. That's my theory. 

The list of packages isn't showing the older kernels.  If that really, really, is the full output, then I'd manually delete those older kernels.  If you do delete them and the package manager still thinks they are there, it will be REALLY bad. We are trying to avoid this situation, since it would be worse than the current problem.

---

### Post by Impavidus on 2018-12-14
The fact you've got several files in /boot belonging to packages you don't have installed is remarkable. Furthermore, the initrd.img for your current kernel is missing (that is, if you're still running 4.15.0-36). The clean way to remove these files is by reinstalling the old kernels, then removing them, but that won't work as long as your /boot partition is full. Maybe we can remove some stuff by manually calling update-initramfs. It may be possible to manually remove some other files belonging to old kernels, but I suggest you keep track of which files exactly you remove that way, so you can later clean things up. Manually removing files from /boot is usually a recipe for even more trouble.

Verify which kernel you currently run with```
uname -r
```. Is it still 4.15.0-36, or at least not 4.15.0-30? Then try to remove one old initramfs.img:```
sudo update-initramfs -d -k 4.15.0-30-generic
```That is, if TheFu agrees with me. We should be consistent. If you remove the wrong initramfs.img, your system will be unbootable (not something we can't fix, but it will make it more difficult).

---

### Post by lipesmile on 2018-12-14
> **Impavidus said:**
> The fact you've got several files in /boot belonging to packages you don't have installed is remarkable. Furthermore, the initrd.img for your current kernel is missing (that is, if you're still running 4.15.0-36). The clean way to remove these files is by reinstalling the old kernels, then removing them, but that won't work as long as your /boot partition is full. Maybe we can remove some stuff by manually calling update-initramfs. It may be possible to manually remove some other files belonging to old kernels, but I suggest you keep track of which files exactly you remove that way, so you can later clean things up. Manually removing files from /boot is usually a recipe for even more trouble.

Verify which kernel you currently run with```
uname -r
```. Is it still 4.15.0-36, or at least not 4.15.0-30? Then try to remove one old initramfs.img:```
sudo update-initramfs -d -k 4.15.0-30-generic
```That is, if TheFu agrees with me. We should be consistent. If you remove the wrong initramfs.img, your system will be unbootable (not something we can't fix, but it will make it more difficult).

Now I have good news guys, I try the command for remove initrd.img manually and it worked, see the command output below:

```
update-initramfs -d -k 4.15.0-30-generic
update-initramfs: Deleting /boot/initrd.img-4.15.0-30-generic
```

After that reboot the system and run df -h:
```
root@vps9835:~# df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/root        39G  7.8G   29G  22% /
devtmpfs        989M     0  989M   0% /dev
tmpfs           992M     0  992M   0% /dev/shm
tmpfs           992M  660K  992M   1% /run
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs           992M     0  992M   0% /sys/fs/cgroup
/dev/xvda1      232M  171M   45M  80% /boot
tmpfs           199M     0  199M   0% /run/user/0
```


The boot directory was 100% now is 80%.

Now what I should do ?
Try to remove manually the other files ? Run the apt install -f, autoclean, remove linux-headers ? Or should I install byobut to remove old kernels ? Or Do I need to do another thing ?


Edit:
Before I ran the command to delete initrd.img I ran this apt-get remove:
```
apt-get remove linux-headers-4.15.0-3[0-8]* linux-modules-extra-4.15.0-3*
Reading package lists... Done
Building dependency tree
Reading state information... Done
Note, selecting 'linux-headers-4.15.0-32-generic' for glob 'linux-headers-4.15.0-3[0-8]*'
Note, selecting 'linux-headers-4.15.0-36-generic' for glob 'linux-headers-4.15.0-3[0-8]*'
Note, selecting 'linux-headers-4.15.0-38-generic' for glob 'linux-headers-4.15.0-3[0-8]*'
Note, selecting 'linux-headers-4.15.0-33-lowlatency' for glob 'linux-headers-4.15.0-3[0-8]*'
Note, selecting 'linux-headers-4.15.0-30' for glob 'linux-headers-4.15.0-3[0-8]*'
Note, selecting 'linux-headers-4.15.0-32' for glob 'linux-headers-4.15.0-3[0-8]*'
Note, selecting 'linux-headers-4.15.0-33' for glob 'linux-headers-4.15.0-3[0-8]*'
Note, selecting 'linux-headers-4.15.0-34' for glob 'linux-headers-4.15.0-3[0-8]*'
Note, selecting 'linux-headers-4.15.0-36' for glob 'linux-headers-4.15.0-3[0-8]*'
Note, selecting 'linux-headers-4.15.0-38' for glob 'linux-headers-4.15.0-3[0-8]*'
Note, selecting 'linux-headers-4.15.0-30-lowlatency' for glob 'linux-headers-4.15.0-3[0-8]*'
Note, selecting 'linux-headers-4.15.0-32-lowlatency' for glob 'linux-headers-4.15.0-3[0-8]*'
Note, selecting 'linux-headers-4.15.0-34-lowlatency' for glob 'linux-headers-4.15.0-3[0-8]*'
Note, selecting 'linux-headers-4.15.0-30-generic' for glob 'linux-headers-4.15.0-3[0-8]*'
Note, selecting 'linux-headers-4.15.0-36-lowlatency' for glob 'linux-headers-4.15.0-3[0-8]*'
Note, selecting 'linux-headers-4.15.0-34-generic' for glob 'linux-headers-4.15.0-3[0-8]*'
Note, selecting 'linux-headers-4.15.0-38-lowlatency' for glob 'linux-headers-4.15.0-3[0-8]*'
Note, selecting 'linux-headers-4.15.0-33-generic' for glob 'linux-headers-4.15.0-3[0-8]*'
Note, selecting 'linux-modules-extra-4.15.0-33-generic' for glob 'linux-modules-extra-4.15.0-3*'
Note, selecting 'linux-modules-extra-4.15.0-36-generic' for glob 'linux-modules-extra-4.15.0-3*'
Note, selecting 'linux-modules-extra-4.15.0-39-generic' for glob 'linux-modules-extra-4.15.0-3*'
Note, selecting 'linux-modules-extra-4.15.0-38-generic' for glob 'linux-modules-extra-4.15.0-3*'
Note, selecting 'linux-modules-extra-4.15.0-30-generic' for glob 'linux-modules-extra-4.15.0-3*'
Note, selecting 'linux-modules-extra-4.15.0-32-generic' for glob 'linux-modules-extra-4.15.0-3*'
Note, selecting 'linux-modules-extra-4.15.0-34-generic' for glob 'linux-modules-extra-4.15.0-3*'
Package 'linux-headers-4.15.0-30-generic' is not installed, so not removed
Package 'linux-headers-4.15.0-30-lowlatency' is not installed, so not removed
Package 'linux-headers-4.15.0-32-lowlatency' is not installed, so not removed
Package 'linux-headers-4.15.0-33-lowlatency' is not installed, so not removed
Package 'linux-headers-4.15.0-34' is not installed, so not removed
Package 'linux-headers-4.15.0-34-generic' is not installed, so not removed
Package 'linux-headers-4.15.0-34-lowlatency' is not installed, so not removed
Package 'linux-headers-4.15.0-36-lowlatency' is not installed, so not removed
Package 'linux-headers-4.15.0-38' is not installed, so not removed
Package 'linux-headers-4.15.0-38-generic' is not installed, so not removed
Package 'linux-headers-4.15.0-38-lowlatency' is not installed, so not removed
Package 'linux-modules-extra-4.15.0-30-generic' is not installed, so not removed
Package 'linux-modules-extra-4.15.0-32-generic' is not installed, so not removed
Package 'linux-modules-extra-4.15.0-33-generic' is not installed, so not removed
Package 'linux-modules-extra-4.15.0-34-generic' is not installed, so not removed
Package 'linux-modules-extra-4.15.0-38-generic' is not installed, so not removed
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 linux-image-generic : Depends: linux-image-4.15.0-42-generic but it is not going to be installed
                       Recommends: thermald but it is not going to be installed
 linux-modules-extra-4.15.0-42-generic : Depends: linux-image-4.15.0-42-generic but it is not going to be installed or
                                                  linux-image-unsigned-4.15.0-42-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).

```

---

### Post by TheFu on 2018-12-14
You should get to 1 working kernel, no excess files, then patch, autoremove and stay patched with 2-3 kernels going forward.  IMHO.
But it is your system. Do whatever you like.

Over the decades, I've learned how to avoid "APT hell" since avoiding it is much easier than fixing it after the fact.

---

### Post by Impavidus on 2018-12-15
Try to remove initrd.img-4.15.0-32-generic (assuming you're still running 4.15.0-36):```
sudo update-initramfs -d -k 4.15.0-32-generic
```That should give some more breathing room. Then you hopefully have enough room to fix the package manager and install 4.15.0-42:```
sudo apt install -f
```Then it would be nice to get a new overview of your sitiation:```
uname -r
dpkg --list | grep linux-\*
ls /boot
df -h
```

---

### Post by lipesmile on 2018-12-15
> **TheFu said:**
> You should get to 1 working kernel, no excess files, then patch, autoremove and stay patched with 2-3 kernels going forward.  IMHO.
But it is your system. Do whatever you like.

Over the decades, I've learned how to avoid "APT hell" since avoiding it is much easier than fixing it after the fact.

@TheFu
How I do this ?

> You should get to 1 working kernel

For this I need to use update-initramfs -d -k  until left just my current kernel ? Should I remove old and new versions of kernel ?

>  no excess files
What is excess files ? Is unnecessary files ?

> then patch
To do this is just follow this link ?
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

> autoremove
I guess this part is just run apt autoremove

>  I've learned how to avoid "APT hell" since avoiding it is much easier than fixing it after the fact
How I avoid APT ?


**Edit:**
*Sorry*, I didn't saw Impavidus answer. I ran the commands and here are the results 

The worked update-initramfs -d -k 4.15.0-32-generic, but I forgot to save the result.

apt install -f return error:
```
dpkg: error processing package linux-image-4.15.0-42-generic (--configure):
 installed linux-image-4.15.0-42-generic package post-installation script subprocess returned error exit status 1
Processing triggers for linux-image-4.15.0-39-generic (4.15.0-39.42) ...
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-4.15.0-39-generic
cryptsetup: WARNING: failed to detect canonical device of /dev/xvda3
cryptsetup: WARNING: could not determine root device from /etc/fstab

gzip: stdout: No space left on device
E: mkinitramfs failure find 141 cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.15.0-39-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-4.15.0-39-generic (--configure):
 installed linux-image-4.15.0-39-generic package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 linux-image-4.15.0-42-generic
 linux-image-4.15.0-39-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

The overview:

```
# uname -r
4.15.0-36-generic


# dpkg --list | grep linux-\*
ii  binutils-x86-64-linux-gnu             2.30-21ubuntu1~18.04               amd64        GNU binary utilities, for x86-64-linux-gnu target
ii  console-setup-linux                   1.178ubuntu2.7                     all          Linux specific part of console-setup
ii  libselinux1:amd64                     2.7-2build2                        amd64        SELinux runtime shared libraries
ii  linux-base                            4.5ubuntu1                         all          Linux image base package
ii  linux-firmware                        1.173.1                            all          Firmware for Linux kernel drivers
ii  linux-generic                         4.15.0.42.44                       amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.15.0-30               4.15.0-30.32                       all          Header files related to Linux kernel version 4.15.0
ii  linux-headers-4.15.0-32               4.15.0-32.35                       all          Header files related to Linux kernel version 4.15.0
ii  linux-headers-4.15.0-32-generic       4.15.0-32.35                       amd64        Linux kernel headers for version 4.15.0 on 64 bit x86 SMP
ii  linux-headers-4.15.0-33               4.15.0-33.36                       all          Header files related to Linux kernel version 4.15.0
ii  linux-headers-4.15.0-33-generic       4.15.0-33.36                       amd64        Linux kernel headers for version 4.15.0 on 64 bit x86 SMP
ii  linux-headers-4.15.0-36               4.15.0-36.39                       all          Header files related to Linux kernel version 4.15.0
ii  linux-headers-4.15.0-36-generic       4.15.0-36.39                       amd64        Linux kernel headers for version 4.15.0 on 64 bit x86 SMP
ii  linux-headers-4.15.0-39               4.15.0-39.42                       all          Header files related to Linux kernel version 4.15.0
ii  linux-headers-4.15.0-39-generic       4.15.0-39.42                       amd64        Linux kernel headers for version 4.15.0 on 64 bit x86 SMP
ii  linux-headers-4.15.0-42               4.15.0-42.45                       all          Header files related to Linux kernel version 4.15.0
ii  linux-headers-4.15.0-42-generic       4.15.0-42.45                       amd64        Linux kernel headers for version 4.15.0 on 64 bit x86 SMP
ii  linux-headers-generic                 4.15.0.42.44                       amd64        Generic Linux kernel headers
ii  linux-image-4.15.0-36-generic         4.15.0-36.39                       amd64        Signed kernel image generic
iF  linux-image-4.15.0-39-generic         4.15.0-39.42                       amd64        Signed kernel image generic
iF  linux-image-4.15.0-42-generic         4.15.0-42.45                       amd64        Signed kernel image generic
ii  linux-image-generic                   4.15.0.42.44                       amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                  4.15.0-39.42                       amd64        Linux Kernel Headers for development
ii  linux-modules-4.15.0-36-generic       4.15.0-36.39                       amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-4.15.0-39-generic       4.15.0-39.42                       amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-4.15.0-42-generic       4.15.0-42.45                       amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-extra-4.15.0-36-generic 4.15.0-36.39                       amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-extra-4.15.0-39-generic 4.15.0-39.42                       amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-extra-4.15.0-42-generic 4.15.0-42.45                       amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  util-linux                            2.31.1-0.4ubuntu3.2                amd64        miscellaneous system utilities

# ls /boot
abi-4.15.0-20-generic  config-4.15.0-30-generic      initrd.img-4.15.0-39-generic  System.map-4.15.0-30-generic  vmlinuz-4.15.0-33-generic
abi-4.15.0-23-generic  config-4.15.0-32-generic      lost+found                    System.map-4.15.0-32-generic  vmlinuz-4.15.0-36-generic
abi-4.15.0-30-generic  config-4.15.0-33-generic      retpoline-4.15.0-30-generic   System.map-4.15.0-33-generic  vmlinuz-4.15.0-39-generic
abi-4.15.0-32-generic  config-4.15.0-36-generic      retpoline-4.15.0-32-generic   System.map-4.15.0-36-generic  vmlinuz-4.15.0-42-generic
abi-4.15.0-33-generic  config-4.15.0-39-generic      retpoline-4.15.0-33-generic   System.map-4.15.0-39-generic
abi-4.15.0-36-generic  config-4.15.0-42-generic      retpoline-4.15.0-36-generic   System.map-4.15.0-42-generic
abi-4.15.0-39-generic  grub                          retpoline-4.15.0-39-generic   vmlinuz-4.15.0-30-generic
abi-4.15.0-42-generic  initrd.img-4.15.0-33-generic  retpoline-4.15.0-42-generic   vmlinuz-4.15.0-32-generic

# df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/root        39G  7.9G   29G  22% /
devtmpfs        989M     0  989M   0% /dev
tmpfs           992M     0  992M   0% /dev/shm
tmpfs           992M  672K  992M   1% /run
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs           992M     0  992M   0% /sys/fs/cgroup
/dev/xvda1      232M  199M   17M  93% /boot
tmpfs           199M     0  199M   0% /run/user/0

```

---

### Post by Impavidus on 2018-12-16
The update-initramfs commands are an emergency measure to get you back to a working system. When everything works again, you should only need regular autoremoves, then you should automatically get new kernels with your regular upgrades.

Have you rebooted recently? If not, don't. I suspect your system is currently unbootable.

First get rid of kernel 4.15.0-39. It was never installed correctly and is old already:```
sudo dpkg --purge linux-image-4.15.0-39-generic linux-modules-4.15.0-39-generic linux-modules-extra-4.15.0-39-generic
```Then try again to install 4.15.0-42:```
sudo apt install -f
```Then show us another overview of the new situation.

We first want to get kernel 4.15.0-42 installed. That's the latest kernel you can use. When we have confirmed it's been properly installed, you can reboot using 4.15.0-42. Then it's time to cleanup all the old and improperly installed kernels.

---

### Post by lipesmile on 2018-12-16
> **Impavidus said:**
> The update-initramfs commands are an emergency measure to get you back to a working system. When everything works again, you should only need regular autoremoves, then you should automatically get new kernels with your regular upgrades.

Have you rebooted recently? If not, don't. I suspect your system is currently unbootable.

First get rid of kernel 4.15.0-39. It was never installed correctly and is old already:```
sudo dpkg --purge linux-image-4.15.0-39-generic linux-modules-4.15.0-39-generic linux-modules-extra-4.15.0-39-generic
```Then try again to install 4.15.0-42:```
sudo apt install -f
```Then show us another overview of the new situation.

We first want to get kernel 4.15.0-42 installed. That's the latest kernel you can use. When we have confirmed it's been properly installed, you can reboot using 4.15.0-42. Then it's time to cleanup all the old and improperly installed kernels.

I run uname -r and it return that i'm in 4.15.0-36-generic.

When I try to run purge it return dependecies errors like this:
```
dpkg: warning: files list file for package 'libquadmath0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python-apt-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'zerofree' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libnpth0:amd64' missing; assuming package has no files currently installed
```

And this is the return of apt install -f

```
dpkg: error processing package linux-image-4.15.0-39-generic (--remove):
 installed linux-image-4.15.0-39-generic package post-removal script subprocess returned error exit status 1
Errors were encountered while processing:
 linux-image-4.15.0-39-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Impavidus on 2018-12-17
> **lipesmile said:**
> I run uname -r and it return that i'm in 4.15.0-36-generic.

When I try to run purge it return dependecies errors like this:
```
dpkg: warning: files list file for package 'libquadmath0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python-apt-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'zerofree' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libnpth0:amd64' missing; assuming package has no files currently installed
```Those aren't errors, those are warnings, telling us your package system is in an even worse shape that we already thought. If there are errors, show them. I'd like to see the complete output of every command you try.

> And this is the return of apt install -f

```
dpkg: error processing package linux-image-4.15.0-39-generic (--remove):
 installed linux-image-4.15.0-39-generic package post-removal script subprocess returned error exit status 1
Errors were encountered while processing:
 linux-image-4.15.0-39-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
The actual error should be a bit higher up in the output. It does tell us there's some problem removing old kernels, which may partially explain the various files of old kernels in /boot. Have you used any tools like bleachbit or grub-customizer? Those tools are known to break your system if used improperly.

Let's see this:```
sudo apt install -f
dpkg --list | grep linux-\*
ls -l /boot 
df -h
```

---

### Post by lipesmile on 2018-12-18
> **Impavidus said:**
> Those aren't errors, those are warnings, telling us your package system is in an even worse shape that we already thought. If there are errors, show them. I'd like to see the complete output of every command you try.


The actual error should be a bit higher up in the output. It does tell us there's some problem removing old kernels, which may partially explain the various files of old kernels in /boot. Have you used any tools like bleachbit or grub-customizer? Those tools are known to break your system if used improperly.

Let's see this:```
sudo apt install -f
dpkg --list | grep linux-\*
ls -l /boot 
df -h
```

No, I haven't used this tools.

The output the commands are to big, so I put then on github gist:
[https://gist.github.com/lipesmile/cff59f9145c62b5f815085801f50f2f0](https://gist.github.com/lipesmile/cff59f9145c62b5f815085801f50f2f0)

---

### Post by Impavidus on 2018-12-19
It's getting weirder...
You've got a load of packages with missing file lists. Some day something went wrong. See this link for a way to solve that: [https://askubuntu.com/questions/949760/dpkg-warning-files-list-file-for-package-missing](https://askubuntu.com/questions/949760/dpkg-warning-files-list-file-for-package-missing). The answer by fronk seems fine. But you'll have to fix the package manager before that works and it will take a long time.

```
Found kernel: /vmlinuz-4.4.0-38-generic
Found kernel: /vmlinuz-4.4.0-36-generic
Found kernel: /vmlinuz-4.4.0-21-generic
run-parts: /etc/kernel/postrm.d/x-grub-legacy-ec2 exited with return code 10
dpkg: error processing package linux-image-4.15.0-39-generic (--remove):
```That's the error. x-grub-legacy-ec2 belongs to the package grub-legacy-ec2. I don't know about EC2, I do know that grub legacy sounds ol[SIZE=2]d. Kernel 4.4.0-38 sounds old too. The description says about grub-legacy-ec2:> EC2 instances that use grub-legacy as a bootloader need a way to keep
/boot/grub/menu.lst up to date while not conflicting with grub-pc.
This package provides that.And EC2 is the Amazon Elastic Compute Cloud. I guess you need it for some reason, but n[/SIZE][SIZE=2]ow I'm getting out of my comfort zone.

The next step is to investigate why tha[/SIZE]t script terminates with return code 10, but I'm not familiar enough with grub-legacy-ec2 to be of much help. I do however have the impression that this is all caused by leftovers from older releases. Simply speaking, it's a mess. A quick and clean solution might not exist.

---

### Post by lipesmile on 2018-12-22
I'm thinking in re intall this server, because it not in use yet, I'm just preparing it for enter in production.

---

### Post by Impavidus on 2018-12-23
A clean install is definitely the fastest solution to your problem, is particular if there's nothing to lose on this system.

---

