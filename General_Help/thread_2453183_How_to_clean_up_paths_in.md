---
title: "How to clean up paths in /"
date: 2020-11-04
forum: General Help
---

### Post by oygle on 2020-11-04
I have been using the following to clean up disk space

```
sudo apt-get autoclean # only removes files that cannot be downloaded anymore (obsolete)
sudo apt-get autoremove #removes old obsolete/orphaned files
sudo apt-get clean #clears out the local repository of retrieved package files
sudo apt update
sudo apt upgrade
sudo apt -f install #to check/fix any broken packages

```

and then noticed that the /usr path has 238,911 files and 34,720 sub-folders. Digging deeper ..

```
$ sudo du -shc /usr/*
```

> 271M    /usr/bin
1.6M    /usr/games
24M     /usr/include
3.4G    /usr/lib
4.0K    /usr/lib32
4.0K    /usr/lib64
1.3M    /usr/libexec
4.0K    /usr/libx32
116K    /usr/local
53M     /usr/sbin
1.7G    /usr/share
395M    /usr/src
5.8G    total

```
$ sudo du -shc /usr/src/*
```

> 109M    /usr/src/linux-headers-5.3.0-18
24M     /usr/src/linux-headers-5.3.0-18-generic
109M    /usr/src/linux-headers-5.3.0-62
24M     /usr/src/linux-headers-5.3.0-62-generic
109M    /usr/src/linux-headers-5.3.0-64
24M     /usr/src/linux-headers-5.3.0-64-generic
395M    total

```
$ uname -a
```

> Linux ********-Inspiron-3542 5.3.0-64-generic #58-Ubuntu SMP Fri Jul 10 19:33:51 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

Can I remove these paths ?

>  /usr/src/linux-headers-5.3.0-18
/usr/src/linux-headers-5.3.0-18-generic
/usr/src/linux-headers-5.3.0-62
/usr/src/linux-headers-5.3.0-62-generic

---

### Post by GhX6GZMB on 2020-11-04
Don't even think about it. You're meddling where you shouldn't IMO.

If you check out your / you'll see that it contains symbolic links that point exactly to the /usr directories you're listing. So it's not like something is duplicated here. The files are actually in /usr and not in /

For freeing up space, check /var where the log files tend to bloat over time.

EDIT: I wonder about the 5.3.0-18 files, though. sudo autoremove should have deleted those, I think.

---

### Post by oldfred on 2020-11-04
What kernel are you using?
uname -a

New versions now only keep two versions if you houseclean as you are.
But if an upgrade, you may have older kernel & various other cruft. Old log files?
Part of why I like a clean install & restore from backups, so all the misc is then housecleaned.

This should only have your current two kernels, and perhaps other files, mine only has [FONT=monospace][COLOR=#5454ff]**libdvd-pkg**[/COLOR][/FONT]:
ls -al /usr/src/
ls -al /lib/modules/

And this has your two current kernels & supporting files by version.
[FONT=monospace][COLOR=#000000]ll /boot[/COLOR]
[/FONT]

---

### Post by SeijiSensei on 2020-11-04
> **ml9104 said:**
> EDIT: I wonder about the 5.3.0-18 files, though. sudo autoremove should have deleted those, I think.
Autoremove is somewhat unreliable when it comes to removing substantially older kernel versions like this one.  If it matters, you'll probably have to delete it manually along with the 5.3.0-18 files in /boot.

/usr contains most the stuff that makes Linux go.  /usr/bin contains all the program binaries.  /usr/lib holds the "libraries" that programs use for common functions. /usr/share has lots of ancillary files that the programs use.  /usr/src contains the "headers" for the Linux kernel. (It can also store other source code, but the headers are the most common on an Ubuntu installation.) Installers will sometimes use these header files to create custom kernel modules; VirtualBox is a good example.  The only place you might muck around is in /usr/local, where programs not managed by apt and their associated libraries are stored. You'd need to have admin rights via sudo.

In general, you should leave /usr alone.  There's a reason why ordinary users only have privileges in their home directories and /tmp. It's to keep users from making mistakes like deleting /usr/share to save space.

---

### Post by Impavidus on 2020-11-05
> **oygle said:**
> I have been using the following to clean up disk space

```
sudo apt-get autoclean # only removes files that cannot be downloaded anymore (obsolete)
sudo apt-get autoremove #removes old obsolete/orphaned files
sudo apt-get clean #clears out the local repository of retrieved package files
sudo apt update
sudo apt upgrade
sudo apt -f install #to check/fix any broken packages

```To get the details straight, command 1 will remove obsolete package files. Command 2 will remove packages that are no longer needed. It doesn't remove the package file (which is an archive and will be remove by command 3), but all files comming from that archive and also run some scripts necessary for clean removal. It will however not completely remove the package, as some configuration files may remain. To remove those too, add the --purge option. Command 3 will remove all package files, including those that would be removed by command 1. You never have to run them both. Command 4 refreshes the list of available packages, command 5 will upgrade all installed packages, installing new ones if dependencies require, but will never remove packages. Command 6 will install or remove packages to fix dependency errors. If you keep your system clean, you never need it. It won't fix other errors.
> ```
$ uname -a
Linux ********-Inspiron-3542 5.3.0-64-generic #58-Ubuntu SMP Fri Jul 10 19:33:51 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

```
This tells us you run kernel 5.3.0-64, compiled on 10 July. It's the last kernel that came with Ubuntu 19.10, which reached end of life a week later. Are you running Ubuntu 19.10 or did something go wrong and you didn't get the new kernel when upgrading to 20.04? If the former, get on 20.04 ASAP. An end-of-life upgrade may work, but you can also try a fresh install. If the latter, show us the output of```
dpkg --list linux-*
```
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by oygle on 2020-11-05
> **ml9104 said:**
> For freeing up space, check /var where the log files tend to bloat over time.

EDIT: I wonder about the 5.3.0-18 files, though. sudo autoremove should have deleted those, I think.

Yes, I have been cleaning up /var/log path. It's not just 5.3.0-18 files , earlier versions also.

> **oldfred said:**
> What kernel are you using?

5.3.0-64-generic 

> **oldfred said:**
> New versions now only keep two versions if you houseclean as you are.

The housekeeping I'm doing seems to keep older versions.

> **oldfred said:**
> But if an upgrade, you may have older kernel & various other cruft. Old log files?
Part of why I like a clean install & restore from backups, so all the misc is then housecleaned.

Yes, I always do a clean install; read too many stories of upgrades failing. The commands you mentioned; here is the output:

```
$ ls -al /usr/src/
total 32
drwxr-xr-x  8 root root 4096 Jul 29 08:06 .
drwxr-xr-x 14 root root 4096 Oct 17  2019 ..
drwxr-xr-x 24 root root 4096 Oct 17  2019 linux-headers-5.3.0-18
drwxr-xr-x  7 root root 4096 Oct 17  2019 linux-headers-5.3.0-18-generic
drwxr-xr-x 24 root root 4096 Jul  2 10:20 linux-headers-5.3.0-62
drwxr-xr-x  7 root root 4096 Jul  2 10:21 linux-headers-5.3.0-62-generic
drwxr-xr-x 24 root root 4096 Jul 28 10:54 linux-headers-5.3.0-64
drwxr-xr-x  7 root root 4096 Jul 28 10:54 linux-headers-5.3.0-64-generic

$ ls -al /lib/modules/
total 52
drwxr-xr-x  13 root root 4096 Jul 28 10:54 .
drwxr-xr-x 122 root root 4096 Oct 26 12:42 ..
drwxr-xr-x   5 root root 4096 Apr  1  2020 5.3.0-18-generic
drwxr-xr-x   2 root root 4096 Apr  8  2020 5.3.0-42-generic
drwxr-xr-x   2 root root 4096 Apr 30  2020 5.3.0-45-generic
drwxr-xr-x   2 root root 4096 May 22 09:29 5.3.0-46-generic
drwxr-xr-x   2 root root 4096 May 28 08:00 5.3.0-51-generic
drwxr-xr-x   2 root root 4096 Jun 11 07:11 5.3.0-53-generic
drwxr-xr-x   2 root root 4096 Jun 26 08:27 5.3.0-55-generic
drwxr-xr-x   2 root root 4096 Jul  3 07:37 5.3.0-59-generic
drwxr-xr-x   2 root root 4096 Jul 29 08:06 5.3.0-61-generic
drwxr-xr-x   5 root root 4096 Jul  2 10:21 5.3.0-62-generic
drwxr-xr-x   5 root root 4096 Jul 28 10:54 5.3.0-64-generic

$ ll /boot
total 231216
drwxr-xr-x  3 root root     4096 Jul 29 08:06 ./
drwxr-xr-x 20 root root     4096 Apr 25  2020 ../
-rw-r--r--  1 root root   236454 Oct  9  2019 config-5.3.0-18-generic
-rw-r--r--  1 root root   235822 Jun 23 20:01 config-5.3.0-62-generic
-rw-r--r--  1 root root   235822 Jul 11 05:22 config-5.3.0-64-generic
drwxr-xr-x  4 root root     4096 Jul 29 08:06 grub/
lrwxrwxrwx  1 root root       27 Jul 28 10:54 initrd.img -> initrd.img-5.3.0-64-generic
-rw-r--r--  1 root root 33129319 Jul  9 11:15 initrd.img-5.3.0-18-generic
-rw-r--r--  1 root root 76982623 Jul  9 11:15 initrd.img-5.3.0-62-generic
-rw-r--r--  1 root root 76985509 Jul 28 10:54 initrd.img-5.3.0-64-generic
lrwxrwxrwx  1 root root       27 Jul 28 10:54 initrd.img.old -> initrd.img-5.3.0-62-generic
-rw-r--r--  1 root root   182704 Jan 28  2016 memtest86+.bin
-rw-r--r--  1 root root   184380 Jan 28  2016 memtest86+.elf
-rw-r--r--  1 root root   184840 Jan 28  2016 memtest86+_multiboot.bin
-rw-------  1 root root  4703701 Oct  9  2019 System.map-5.3.0-18-generic
-rw-------  1 root root  4709896 Jun 23 20:01 System.map-5.3.0-62-generic
-rw-------  1 root root  4710447 Jul 11 05:22 System.map-5.3.0-64-generic
lrwxrwxrwx  1 root root       24 Jul 28 10:54 vmlinuz -> vmlinuz-5.3.0-64-generic
-rw-r--r--  1 root root 11391736 Oct 17  2019 vmlinuz-5.3.0-18-generic
-rw-------  1 root root 11416320 Jun 23 20:04 vmlinuz-5.3.0-62-generic
-rw-------  1 root root 11416320 Jul 11 05:24 vmlinuz-5.3.0-64-generic
lrwxrwxrwx  1 root root       24 Jul 28 10:54 vmlinuz.old -> vmlinuz-5.3.0-62-generic

```

> **SeijiSensei said:**
> Autoremove is somewhat unreliable when it comes to removing substantially older kernel versions like this one.  If it matters, you'll probably have to delete it manually along with the 5.3.0-18 files in /boot.

Well, that explains why the autoremove that I have been runing isn't cleaning up as expected, thanks.

> **SeijiSensei said:**
> In general, you should leave /usr alone.  There's a reason why ordinary users only have privileges in their home directories and /tmp. It's to keep users from making mistakes like deleting /usr/share to save space.

Yes, I think I will leave it alone, despite the fact there is unnecessary files there.

> **Impavidus said:**
> This tells us you run kernel 5.3.0-64, compiled on 10 July. It's the last kernel that came with Ubuntu 19.10, which reached end of life a week later. Are you running Ubuntu 19.10 or did something go wrong and you didn't get the new kernel when upgrading to 20.04? If the former, get on 20.04 ASAP. An end-of-life upgrade may work, but you can also try a fresh install. If the latter, show us the output of```
dpkg --list linux-*
```
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

I'm running 19.10 on this computer. have done a (test) clean install of 20.04.1 on another computer, so after all the backups, should be okay to do a clean install of 20.04.1 on this one.

```
$ dpkg --list linux-* 
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                  Version              Architecture Description
+++-=====================================-====================-============-==============================================================
ii  linux-base                            4.5ubuntu2.2         all          Linux image base package
un  linux-doc-5.3.0                       <none>               <none>       (no description available)
ii  linux-firmware                        1.183.6              all          Firmware for Linux kernel drivers
un  linux-firmware-snapdragon             <none>               <none>       (no description available)
ii  linux-generic                         5.3.0.64.54          amd64        Complete Generic Linux kernel and headers
un  linux-headers                         <none>               <none>       (no description available)
un  linux-headers-3.0                     <none>               <none>       (no description available)
ii  linux-headers-5.3.0-18                5.3.0-18.19          all          Header files related to Linux kernel version 5.3.0
ii  linux-headers-5.3.0-18-generic        5.3.0-18.19          amd64        Linux kernel headers for version 5.3.0 on 64 bit x86 SMP
un  linux-headers-5.3.0-42-generic        <none>               <none>       (no description available)
un  linux-headers-5.3.0-45-generic        <none>               <none>       (no description available)
un  linux-headers-5.3.0-46-generic        <none>               <none>       (no description available)
un  linux-headers-5.3.0-51-generic        <none>               <none>       (no description available)
un  linux-headers-5.3.0-53-generic        <none>               <none>       (no description available)
un  linux-headers-5.3.0-55-generic        <none>               <none>       (no description available)
un  linux-headers-5.3.0-59-generic        <none>               <none>       (no description available)
un  linux-headers-5.3.0-61-generic        <none>               <none>       (no description available)
ii  linux-headers-5.3.0-62                5.3.0-62.56          all          Header files related to Linux kernel version 5.3.0
ii  linux-headers-5.3.0-62-generic        5.3.0-62.56          amd64        Linux kernel headers for version 5.3.0 on 64 bit x86 SMP
ii  linux-headers-5.3.0-64                5.3.0-64.58          all          Header files related to Linux kernel version 5.3.0
ii  linux-headers-5.3.0-64-generic        5.3.0-64.58          amd64        Linux kernel headers for version 5.3.0 on 64 bit x86 SMP
ii  linux-headers-generic                 5.3.0.64.54          amd64        Generic Linux kernel headers
un  linux-image                           <none>               <none>       (no description available)
ii  linux-image-5.3.0-18-generic          5.3.0-18.19+1        amd64        Signed kernel image generic
rc  linux-image-5.3.0-42-generic          5.3.0-42.34          amd64        Signed kernel image generic
rc  linux-image-5.3.0-45-generic          5.3.0-45.37          amd64        Signed kernel image generic
rc  linux-image-5.3.0-46-generic          5.3.0-46.38          amd64        Signed kernel image generic
rc  linux-image-5.3.0-51-generic          5.3.0-51.44          amd64        Signed kernel image generic
rc  linux-image-5.3.0-53-generic          5.3.0-53.47          amd64        Signed kernel image generic
rc  linux-image-5.3.0-55-generic          5.3.0-55.49          amd64        Signed kernel image generic
rc  linux-image-5.3.0-59-generic          5.3.0-59.53          amd64        Signed kernel image generic
rc  linux-image-5.3.0-61-generic          5.3.0-61.55          amd64        Signed kernel image generic
ii  linux-image-5.3.0-62-generic          5.3.0-62.56          amd64        Signed kernel image generic
ii  linux-image-5.3.0-64-generic          5.3.0-64.58          amd64        Signed kernel image generic
ii  linux-image-generic                   5.3.0.64.54          amd64        Generic Linux kernel image
un  linux-image-unsigned-5.3.0-18-generic <none>               <none>       (no description available)
un  linux-image-unsigned-5.3.0-42-generic <none>               <none>       (no description available)
un  linux-image-unsigned-5.3.0-45-generic <none>               <none>       (no description available)
un  linux-image-unsigned-5.3.0-46-generic <none>               <none>       (no description available)
un  linux-image-unsigned-5.3.0-51-generic <none>               <none>       (no description available)
un  linux-image-unsigned-5.3.0-53-generic <none>               <none>       (no description available)
un  linux-image-unsigned-5.3.0-55-generic <none>               <none>       (no description available)
un  linux-image-unsigned-5.3.0-59-generic <none>               <none>       (no description available)
un  linux-image-unsigned-5.3.0-61-generic <none>               <none>       (no description available)
un  linux-image-unsigned-5.3.0-62-generic <none>               <none>       (no description available)
un  linux-image-unsigned-5.3.0-64-generic <none>               <none>       (no description available)
un  linux-initramfs-tool                  <none>               <none>       (no description available)
un  linux-kernel-headers                  <none>               <none>       (no description available)
un  linux-kernel-log-daemon               <none>               <none>       (no description available)
ii  linux-libc-dev:amd64                  5.3.0-64.58          amd64        Linux Kernel Headers for development
ii  linux-modules-5.3.0-18-generic        5.3.0-18.19          amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP
rc  linux-modules-5.3.0-42-generic        5.3.0-42.34          amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP
rc  linux-modules-5.3.0-45-generic        5.3.0-45.37          amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP
rc  linux-modules-5.3.0-46-generic        5.3.0-46.38          amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP
rc  linux-modules-5.3.0-51-generic        5.3.0-51.44          amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP
rc  linux-modules-5.3.0-53-generic        5.3.0-53.47          amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP
rc  linux-modules-5.3.0-55-generic        5.3.0-55.49          amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP
rc  linux-modules-5.3.0-59-generic        5.3.0-59.53          amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP
rc  linux-modules-5.3.0-61-generic        5.3.0-61.55          amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP
ii  linux-modules-5.3.0-62-generic        5.3.0-62.56          amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP
ii  linux-modules-5.3.0-64-generic        5.3.0-64.58          amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.3.0-18-generic  5.3.0-18.19          amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.3.0-42-generic  5.3.0-42.34          amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.3.0-45-generic  5.3.0-45.37          amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.3.0-46-generic  5.3.0-46.38          amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.3.0-51-generic  5.3.0-51.44          amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.3.0-53-generic  5.3.0-53.47          amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.3.0-55-generic  5.3.0-55.49          amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.3.0-59-generic  5.3.0-59.53          amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.3.0-61-generic  5.3.0-61.55          amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP
ii  linux-modules-extra-5.3.0-62-generic  5.3.0-62.56          amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP
ii  linux-modules-extra-5.3.0-64-generic  5.3.0-64.58          amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP
un  linux-restricted-common               <none>               <none>       (no description available)
ii  linux-sound-base                      1.0.25+dfsg-0ubuntu5 all          base package for ALSA and OSS sound systems
un  linux-source-5.3.0                    <none>               <none>       (no description available)
un  linux-tools                           <none>               <none>       (no description available)

```

---

### Post by Impavidus on 2020-11-06
The clean way to remove those 5.3.0-18 files is by using the package manager:```
sudo apt remove linux-headers-5.3.0-18 linux-headers-5.3.0-18-generic linux-image-5.3.0-18-generic linux-modules-5.3.0-18-generic
```One of the packages has a somewhat weird version number with a trailing +1. Maybe that's why it wasn't removed automatically.

But if you're doing a fresh install of 20.04, there's no need to cleanup 19.10 first. Those 4 packages don't take that much disk space anyway.

---

### Post by oygle on 2020-11-06
> **Impavidus said:**
> The clean way to remove those 5.3.0-18 files is by using the package manager:```
sudo apt remove linux-headers-5.3.0-18 linux-headers-5.3.0-18-generic linux-image-5.3.0-18-generic linux-modules-5.3.0-18-generic
```.

Thanks. Also it will help removing apps that I don't use and have no (future) need of, like I run KDE, but only use Dolphin and KMyMoney, no PIM at all, and no need of akonadi services.

---

### Post by oygle on 2020-11-08
The /snap path was 1.2 Gb. Ran this command

```
sudo snap set system refresh.retain=2
```

and now it is 500 Mb. From [https://www.linuxuprising.com/2019/04/how-to-remove-old-snap-versions-to-free.html](https://www.linuxuprising.com/2019/04/how-to-remove-old-snap-versions-to-free.html)

Also 

```
$ sudo journalctl --vacuum-time=3d
Deleted archived journal /var/log/journal/0c28c3557c9c46a284fab91a465ab83e/system@b7da5f0860114cae9c9c39fdb3a6556d-0000000000935985-0005b1e8d5d8ad89.journal (16.0M).
Deleted archived journal /var/log/journal/0c28c3557c9c46a284fab91a465ab83e/user-1000@03110440f6e24a35b6e0b43fffb61a39-0000000000935b79-0005b1e8d6d1ce67.journal (16.0M).
Vacuuming done, freed 32.0M of archived journals from /var/log/journal/0c28c3557c9c46a284fab91a465ab83e.
Vacuuming done, freed 0B of archived journals from /var/log/journal.
```

Every bit helps

---

