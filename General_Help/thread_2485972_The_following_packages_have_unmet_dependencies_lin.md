---
title: "The following packages have unmet dependencies: linux-modules-5.15.0-50-generic"
date: 2023-04-15
forum: General Help
---

### Post by akhilakkapelli on 2023-04-15
[COLOR=#232629][FONT=-apple-system]I have updated my Ubuntu 22.04 LTS and I got some errors while updating and I coudn't able to install new softwares or run some of my old softwares.[/FONT][/COLOR]

[COLOR=#232629][FONT=-apple-system]Upgrade:
```

[/FONT][/COLOR]akhil@KHUSHI:~/.config$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).[COLOR=#232629][FONT=-apple-system]
```

Update:
```

[/FONT][/COLOR]akhil@KHUSHI:~/.config$ sudo apt-get update
Hit:1 https://deb.nodesource.com/node_16.x jammy InRelease
Hit:2 http://packages.microsoft.com/repos/code stable InRelease                
Hit:3 http://security.ubuntu.com/ubuntu jammy-security InRelease               
Hit:4 https://packages.microsoft.com/repos/edge stable InRelease               
Hit:5 https://dl.winehq.org/wine-builds/ubuntu jammy InRelease                 
Hit:6 https://dl.google.com/linux/chrome/deb stable InRelease                  
Hit:7 http://in.archive.ubuntu.com/ubuntu jammy InRelease     
Hit:8 http://in.archive.ubuntu.com/ubuntu jammy-updates InRelease
Hit:9 http://in.archive.ubuntu.com/ubuntu jammy-backports InRelease
Reading package lists... Done
W: https://dl.winehq.org/wine-builds/ubuntu/dists/jammy/InRelease: Key is stored in legacy trusted.gpg keyring (/etc/apt/trusted.gpg), see the DEPRECATION section in apt-key(8) for details.[COLOR=#232629][FONT=-apple-system]
```

Full Upgrade:
```

[/FONT][/COLOR]akhil@KHUSHI:~/.config$ sudo apt full-upgrade
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).[COLOR=#232629][FONT=-apple-system]
```

[/FONT][/COLOR][COLOR=#232629][FONT=-apple-system]Fix Broken Packages:
```

[/FONT][/COLOR]
akhil@KHUSHI:~/.config$ sudo apt -f install
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  linux-image-unsigned-5.15.0-50-generic
Suggested packages:
  fdutils linux-doc | linux-source-5.15.0 linux-tools
  linux-headers-5.15.0-50-generic linux-modules-extra-5.15.0-50-generic
The following packages will be REMOVED:
  linux-image-5.15.0-50-generic
The following NEW packages will be installed:
  linux-image-unsigned-5.15.0-50-generic
0 upgraded, 1 newly installed, 1 to remove and 8 not upgraded.
6 not fully installed or removed.
Need to get 0 B/11.6 MB of archives.
After this operation, 379 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
dpkg: linux-image-5.15.0-50-generic: dependency problems, but removing anyway as
 you requested:
 linux-modules-5.15.0-50-generic depends on linux-image-5.15.0-50-generic | linu
x-image-unsigned-5.15.0-50-generic; however:
  Package linux-image-5.15.0-50-generic is to be removed.
  Package linux-image-unsigned-5.15.0-50-generic is not installed.

(Reading database ... 331119 files and directories currently installed.)
Removing linux-image-5.15.0-50-generic (5.15.0-50.56) ...
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-5.15.0-50-generic
/etc/kernel/postrm.d/zz-update-grub:
/usr/sbin/grub-probe: error: failed to get canonical path of `rpool/ROOT/ubuntu_
zs8jjk'.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 1
dpkg: error processing package linux-image-5.15.0-50-generic (--remove):
 installed linux-image-5.15.0-50-generic package post-removal script subprocess 
returned error exit status 1
dpkg: too many errors, stopping
Errors were encountered while processing:
 linux-image-5.15.0-50-generic
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)[COLOR=#232629][FONT=-apple-system]
```

[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]Update GRUB:[/FONT][/COLOR]
```

akhil@KHUSHI:~$ sudo update-grub
/usr/sbin/grub-probe: error: failed to get canonical path of `rpool/ROOT/ubuntu_zs8jjk'.
```

```

akhil@KHUSHI:~$ sudo apt-get install --reinstall grub-efi-amd64
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 linux-modules-5.15.0-50-generic : Depends: linux-image-5.15.0-50-generic but it is not going to be installed or
                                            linux-image-unsigned-5.15.0-50-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
```


[COLOR=#232629][FONT=-apple-system]Force remove linux-modules-5.15.0-50-generic:
```

[/FONT][/COLOR]
akhil@KHUSHI:~$ sudo dpkg --purge --force-remove-reinstreq linux-image-5.15.0-50-generic
(Reading database ... 329778 files and directories currently installed.)
Removing linux-image-5.15.0-50-generic (5.15.0-50.56) ...
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-5.15.0-50-generic
/etc/kernel/postrm.d/zz-update-grub:
/usr/sbin/grub-probe: error: failed to get canonical path of `rpool/ROOT/ubuntu_zs8jjk'.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 1
dpkg: error processing package linux-image-5.15.0-50-generic (--purge):
 installed linux-image-5.15.0-50-generic package post-removal script subprocess returned error exit status 1
Errors were encountered while processing:
 linux-image-5.15.0-50-generic[COLOR=#232629][FONT=-apple-system]
```

```

[/FONT][/COLOR]
akhil@KHUSHI:~$ sudo apt-get remove --purge linux-image-5.15.0-50-generic
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages will be REMOVED:
  linux-image-5.15.0-50-generic
0 upgraded, 0 newly installed, 1 to remove and 22 not upgraded.
2 not fully installed or removed.
After this operation, 11.6 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 329778 files and directories currently installed.)
Removing linux-image-5.15.0-50-generic (5.15.0-50.56) ...
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-5.15.0-50-generic
/etc/kernel/postrm.d/zz-update-grub:
/usr/sbin/grub-probe: error: failed to get canonical path of `rpool/ROOT/ubuntu_zs8jjk'.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 1
dpkg: error processing package linux-image-5.15.0-50-generic (--remove):
 installed linux-image-5.15.0-50-generic package post-removal script subprocess returned error exit status 1
dpkg: too many errors, stopping
Errors were encountered while processing:
 linux-image-5.15.0-50-generic
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)[COLOR=#232629][FONT=-apple-system]
```

I couldn't able to install new applications or run some of the existing apps or get software updates because of this issue.

I trying for the solution from lot of days in the internet and I couldn't able to find the solution.[/FONT][/COLOR]

---

### Post by Bashing-om on 2023-04-15
akhilakkapelli; Hello

As kernel version 5.15.0-50 is old; maybe we can best approach this with dpkg to purge it ?
Though I do show that the -50 kernel is still supported in the repository.

Currently 22.04 is running:
> 
sysop@x2204mini:~$ uname -r
5.15.0-69-generic


so to that end please show us:
```

uname -r
dpkg -l | grep linux-

```
as a place to start.
//
As to "error: failed to get canonical path of `rpool/ROOT/ubuntu_
zs8jjk'." ... I have no idea of what is not taking place here. That will take some digging.

[INDENT]longest journey starts with the 1st step
[/INDENT]

---

### Post by akhilakkapelli on 2023-04-16
Uname:
```

akhil@KHUSHI:~$ uname -r
5.15.0-52-generic

```

```

akhil@KHUSHI:~$ uname -r
dpkg -l | grep linux-
5.15.0-52-generic
ii  binutils-x86-64-linux-gnu                  2.38-4ubuntu2.1                         amd64        GNU binary utilities, for x86-64-linux-gnu target
ii  linux-base                                 4.5ubuntu9                              all          Linux image base package
ii  linux-firmware                             20220329.git681281e4-0ubuntu3.12        all          Firmware for Linux kernel drivers
ii  linux-generic-hwe-22.04                    5.19.0.40.41~22.04.13                   amd64        Complete Generic Linux kernel and headers
ii  linux-headers-5.15.0-52                    5.15.0-52.58                            all          Header files related to Linux kernel version 5.15.0
ii  linux-headers-5.15.0-52-generic            5.15.0-52.58                            amd64        Linux kernel headers for version 5.15.0 on 64 bit x86 SMP
ii  linux-headers-5.19.0-40-generic            5.19.0-40.41~22.04.1                    amd64        Linux kernel headers for version 5.19.0 on 64 bit x86 SMP
ii  linux-headers-generic-hwe-22.04            5.19.0.40.41~22.04.13                   amd64        Generic Linux kernel headers
ii  linux-hwe-5.19-headers-5.19.0-40           5.19.0-40.41~22.04.1                    all          Header files related to Linux kernel version 5.19.0
rc  linux-image-5.15.0-25-generic              5.15.0-25.25                            amd64        Signed kernel image generic
rc  linux-image-5.15.0-37-generic              5.15.0-37.39                            amd64        Signed kernel image generic
rc  linux-image-5.15.0-39-generic              5.15.0-39.42                            amd64        Signed kernel image generic
rc  linux-image-5.15.0-41-generic              5.15.0-41.44                            amd64        Signed kernel image generic
rc  linux-image-5.15.0-43-generic              5.15.0-43.46                            amd64        Signed kernel image generic
rc  linux-image-5.15.0-46-generic              5.15.0-46.49                            amd64        Signed kernel image generic
rc  linux-image-5.15.0-47-generic              5.15.0-47.51                            amd64        Signed kernel image generic
rc  linux-image-5.15.0-48-generic              5.15.0-48.54                            amd64        Signed kernel image generic
rH  linux-image-5.15.0-50-generic              5.15.0-50.56                            amd64        Signed kernel image generic
ii  linux-image-5.15.0-52-generic              5.15.0-52.58                            amd64        Signed kernel image generic
pF  linux-image-5.19.0-40-generic              5.19.0-40.41~22.04.1                    amd64        Signed kernel image generic
ii  linux-image-generic-hwe-22.04              5.19.0.40.41~22.04.13                   amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                       5.15.0-70.77                            amd64        Linux Kernel Headers for development
rc  linux-modules-5.15.0-25-generic            5.15.0-25.25                            amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP
rc  linux-modules-5.15.0-37-generic            5.15.0-37.39                            amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP
rc  linux-modules-5.15.0-39-generic            5.15.0-39.42                            amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP
rc  linux-modules-5.15.0-41-generic            5.15.0-41.44                            amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP
rc  linux-modules-5.15.0-43-generic            5.15.0-43.46                            amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP
rc  linux-modules-5.15.0-46-generic            5.15.0-46.49                            amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP
rc  linux-modules-5.15.0-47-generic            5.15.0-47.51                            amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP
rc  linux-modules-5.15.0-48-generic            5.15.0-48.54                            amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP
ic  linux-modules-5.15.0-50-generic            5.15.0-50.56                            amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP
ii  linux-modules-5.15.0-52-generic            5.15.0-52.58                            amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP
ii  linux-modules-5.19.0-40-generic            5.19.0-40.41~22.04.1                    amd64        Linux kernel extra modules for version 5.19.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.15.0-25-generic      5.15.0-25.25                            amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.15.0-37-generic      5.15.0-37.39                            amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.15.0-39-generic      5.15.0-39.42                            amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.15.0-41-generic      5.15.0-41.44                            amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.15.0-43-generic      5.15.0-43.46                            amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.15.0-46-generic      5.15.0-46.49                            amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.15.0-48-generic      5.15.0-48.54                            amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.15.0-50-generic      5.15.0-50.56                            amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP
ii  linux-modules-extra-5.15.0-52-generic      5.15.0-52.58                            amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP
ii  linux-modules-extra-5.19.0-40-generic      5.19.0-40.41~22.04.1                    amd64        Linux kernel extra modules for version 5.19.0 on 64 bit x86 SMP
rc  linux-modules-nvidia-510-5.15.0-25-generic 5.15.0-25.25                            amd64        Linux kernel nvidia modules for version 5.15.0-25
rc  linux-modules-nvidia-510-5.15.0-37-generic 5.15.0-37.39                            amd64        Linux kernel nvidia modules for version 5.15.0-37
rc  linux-modules-nvidia-510-5.15.0-39-generic 5.15.0-39.42                            amd64        Linux kernel nvidia modules for version 5.15.0-39
rc  linux-modules-nvidia-510-5.15.0-41-generic 5.15.0-41.44+1                          amd64        Linux kernel nvidia modules for version 5.15.0-41
rc  linux-modules-nvidia-515-5.15.0-47-generic 5.15.0-47.51                            amd64        Linux kernel nvidia modules for version 5.15.0-47
rc  linux-objects-nvidia-510-5.15.0-25-generic 5.15.0-25.25                            amd64        Linux kernel nvidia modules for version 5.15.0-25 (objects)
rc  linux-objects-nvidia-510-5.15.0-37-generic 5.15.0-37.39                            amd64        Linux kernel nvidia modules for version 5.15.0-37 (objects)
rc  linux-objects-nvidia-510-5.15.0-39-generic 5.15.0-39.42                            amd64        Linux kernel nvidia modules for version 5.15.0-39 (objects)
rc  linux-objects-nvidia-510-5.15.0-41-generic 5.15.0-41.44+1                          amd64        Linux kernel nvidia modules for version 5.15.0-41 (objects)
rc  linux-objects-nvidia-510-5.15.0-43-generic 5.15.0-43.46+1                          amd64        Linux kernel nvidia modules for version 5.15.0-43 (objects)
rc  linux-objects-nvidia-510-5.15.0-47-generic 5.15.0-47.51                            amd64        Linux kernel nvidia modules for version 5.15.0-47 (objects)
rc  linux-objects-nvidia-515-5.15.0-47-generic 5.15.0-47.51                            amd64        Linux kernel nvidia modules for version 5.15.0-47 (objects)
ii  linux-sound-base                           1.0.25+dfsg-0ubuntu7                    all          base package for ALSA and OSS sound systems

```

---

### Post by MAFoElffen on 2023-04-16
This was installed as ZFS... Was this machine installed originally as 20.04 or 22.04.

Please post the result of these commands:
```

df -H | grep -v 'tmpfs'
sudo zpool list
sudo zfs list
sudo zfs list -t snapshot
sudo zpool status -v
sudo apt list zsys --installed

```
What I see right off is many old kernels. The default Ubuntu ZFS install via the checkmark, creates a /boot within a pool called bpool. It is a set size. If it was installed as 20.04 and you did a do-release-upgrade, then back in 20.04, the install installed ZSys... which is a ZFS util that automaticially created snapshots very time there was some kind of update, or any other apt type of action, which if not maintained (rolling off the older snapshots), then it filled the bpool up, and ever though rpool had lots of room, the /boot container was full, so it would have upgrade error with broken package dependencies, because there was not enough run to complete the update.

The thing that needs to be done is to remove/purge the older kernels, so there is enough room in bpool, to be able to run
```

sudo apt install -f

```
If there is ZSys installed and snapshots in bpool, then the older snapshots need to be remove/destroyed, along with the corresponding rpool snapshots.

That is what I see and suspect.

---

### Post by akhilakkapelli on 2023-04-16
I installed Ubuntu 22.04 lts version directly to my empty hard disk nearly 10 months ago. I saw instructions from the internet and I found ZFS is better than the alternatives. am I wrong? I dont know what it means or how it works.

Results of commands:

```

akhil@KHUSHI:~$ df -H | grep -v 'tmpfs'
Filesystem                                        Size  Used Avail Use% Mounted on
/dev/mapper/keystore-rpool                        459M   29k  423M   1% /run/keystore/rpool
rpool/ROOT/ubuntu_zs8jjk                          357G   17G  340G   5% /
rpool/USERDATA/root_pltcof                        354G   14G  340G   4% /root
rpool/ROOT/ubuntu_zs8jjk/usr/local                341G  274M  340G   1% /usr/local
rpool/ROOT/ubuntu_zs8jjk/srv                      340G  263k  340G   1% /srv
rpool/ROOT/ubuntu_zs8jjk/var/games                340G  263k  340G   1% /var/games
rpool/ROOT/ubuntu_zs8jjk/var/lib                  350G  9.9G  340G   3% /var/lib
rpool/ROOT/ubuntu_zs8jjk/var/snap                 340G  8.4M  340G   1% /var/snap
rpool/ROOT/ubuntu_zs8jjk/var/spool                340G  394k  340G   1% /var/spool
rpool/ROOT/ubuntu_zs8jjk/var/www                  340G  263k  340G   1% /var/www
rpool/ROOT/ubuntu_zs8jjk/var/mail                 340G  263k  340G   1% /var/mail
rpool/ROOT/ubuntu_zs8jjk/var/lib/AccountsService  340G  394k  340G   1% /var/lib/AccountsService
rpool/ROOT/ubuntu_zs8jjk/var/lib/apt              341G  113M  340G   1% /var/lib/apt
rpool/ROOT/ubuntu_zs8jjk/var/lib/NetworkManager   340G  918k  340G   1% /var/lib/NetworkManager
rpool/ROOT/ubuntu_zs8jjk/var/lib/dpkg             341G  131M  340G   1% /var/lib/dpkg
rpool/USERDATA/akhil_pltcof                       437G   97G  340G  23% /home/akhil
rpool/ROOT/ubuntu_zs8jjk/var/log                  341G   96M  340G   1% /var/log
bpool/BOOT/ubuntu_zs8jjk                          1.9G  304M  1.6G  17% /boot
/dev/sda1                                         536M   17M  520M   4% /boot/efi

```

```

akhil@KHUSHI:~$ sudo zpool list
NAME    SIZE  ALLOC   FREE  CKPOINT  EXPANDSZ   FRAG    CAP  DEDUP    HEALTH  ALTROOT
bpool  1.88G   292M  1.59G        -         -     0%    15%  1.00x    ONLINE  -
rpool   460G   129G   331G        -         -    34%    27%  1.00x  DEGRADED  -

```

```

akhil@KHUSHI:~$ sudo zfs list
NAME                                               USED  AVAIL     REFER  MOUNTPOINT
bpool                                              292M  1.46G       96K  /boot
bpool/BOOT                                         290M  1.46G       96K  none
bpool/BOOT/ubuntu_zs8jjk                           290M  1.46G      290M  /boot
rpool                                              129G   317G      192K  /
rpool/ROOT                                        25.4G   317G      192K  none
rpool/ROOT/ubuntu_zs8jjk                          25.4G   317G     15.6G  /
rpool/ROOT/ubuntu_zs8jjk/srv                       216K   317G      216K  /srv
rpool/ROOT/ubuntu_zs8jjk/usr                       261M   317G      192K  /usr
rpool/ROOT/ubuntu_zs8jjk/usr/local                 260M   317G      260M  /usr/local
rpool/ROOT/ubuntu_zs8jjk/var                      9.52G   317G      192K  /var
rpool/ROOT/ubuntu_zs8jjk/var/games                 216K   317G      216K  /var/games
rpool/ROOT/ubuntu_zs8jjk/var/lib                  9.42G   317G     9.20G  /var/lib
rpool/ROOT/ubuntu_zs8jjk/var/lib/AccountsService   260K   317G      260K  /var/lib/AccountsService
rpool/ROOT/ubuntu_zs8jjk/var/lib/NetworkManager    784K   317G      784K  /var/lib/NetworkManager
rpool/ROOT/ubuntu_zs8jjk/var/lib/apt               107M   317G      107M  /var/lib/apt
rpool/ROOT/ubuntu_zs8jjk/var/lib/dpkg              124M   317G      124M  /var/lib/dpkg
rpool/ROOT/ubuntu_zs8jjk/var/log                  90.5M   317G     90.5M  /var/log
rpool/ROOT/ubuntu_zs8jjk/var/mail                  216K   317G      216K  /var/mail
rpool/ROOT/ubuntu_zs8jjk/var/snap                 7.94M   317G     7.94M  /var/snap
rpool/ROOT/ubuntu_zs8jjk/var/spool                 324K   317G      324K  /var/spool
rpool/ROOT/ubuntu_zs8jjk/var/www                   216K   317G      216K  /var/www
rpool/USERDATA                                     103G   317G      192K  /
rpool/USERDATA/akhil_pltcof                       90.1G   317G     90.1G  /home/akhil
rpool/USERDATA/root_pltcof                        13.0G   317G     13.0G  /root
rpool/keystore  

```

```

akhil@KHUSHI:~$ sudo zfs list -t snapshot
no datasets available

```

```

akhil@KHUSHI:~$ sudo zpool status -v
  pool: bpool
 state: ONLINE
  scan: scrub repaired 0B in 00:00:01 with 0 errors on Sun Apr  9 00:24:02 2023
config:


    NAME                                    STATE     READ WRITE CKSUM
    bpool                                   ONLINE       0     0     0
      4f9732b2-2838-4e48-9aa1-62687a2c4315  ONLINE       0     0     0


errors: No known data errors


  pool: rpool
 state: DEGRADED
status: One or more devices has experienced an unrecoverable error.  An
    attempt was made to correct the error.  Applications are unaffected.
action: Determine if the device needs to be replaced, and clear the errors
    using 'zpool clear' or replace the device with 'zpool replace'.
   see: https://openzfs.github.io/openzfs-docs/msg/ZFS-8000-9P
  scan: scrub repaired 0B in 00:02:33 with 0 errors on Sun Oct  9 00:26:34 2022
config:


    NAME                                    STATE     READ WRITE CKSUM
    rpool                                   DEGRADED     0     0     0
      499a9b9e-724f-dc4c-95ad-71d1af5b0105  DEGRADED     0     0     0  too many errors


errors: No known data errors

```

```

akhil@KHUSHI:~$ sudo apt list zsys --install
E: Command line option --install is not understood in combination with the other options

```

This error first appeared while I was updating and upgrading my Ubuntu after a long break.

---

### Post by MAFoElffen on 2023-04-17
The rpool is degraded...

I am just getting ready for work, about out the door, and have a 10 hours shift tonight. Will look at this when I get off or early tomorrow morning. Please have patience. The problem may just an out pf space issue somewhere.

---

### Post by #&amp;thj^% on 2023-04-17
> **MAFoElffen said:**
> The rpool is degraded...

I am just getting ready for work, about out the door, and have a 10 hours shift tonight. Will look at this when I get off or early tomorrow morning. Please have patience. The problem may just an out pf space issue somewhere.

Same with me, close to gone  offline.
Please run this:
```
sudo add-apt-repository ppa:mafoelffen/system-info
sudo apt update
sudo apt install system-info
```
MAFoElffen is the Team Lead for that project, and it will gather important information so we don't have to ask willy nilly questions.
Post the link back here so we can take a peek at possibles.
EDIT: BTW this is a invalid request "sudo apt list zsys --install"

---

### Post by MAFoElffen on 2023-04-18
LOL. Then run the report via
```

system-info --details

```
When it offers to upload the report, enter <Y><Enter> for yes, then copy down the URL to post for us to go over the information it that report. The '--details' flag will toggle it to ask more details queries on ZFS.

After seeing that info, that may show us more on what is happening.

---

### Post by MAFoElffen on 2023-04-18
Dang. Typo corrected.
```

sudo apt list zsys --installed

```

---

### Post by MAFoElffen on 2023-04-18
Your root pool is degraded. This happens for several reasons: capacity exceeded, disk or filesystem errors. It doesn't look like you have a storage full condition. Rather, you have too many errors reported (of an unknown type). But the stats are not showing those errors as read, write or checksum errors. (???)

My initial thoughts would be that if you already had smartmontools installed, that I would ask you to run smartctl to check the errors on your drive's SMART data to see if it is healthy or if it has errors logged.
```

sudo smartctl -H /dev/sda

```
But since your rpool is degraded and you have broken apt packages, unless you already had that installed, there is no way to install that now, to check that...

ZFS does have have fsck, like ext4... But rather has it's own version which is called 'scrub'.

Regardless of what the report says about your hardware (which would be great if we can see it, to point out what Linux see's there)... It first needs the filesystem checked to rule that problem out.
```

sudo zpool scrub rpool

```
It will run in the background until it is finished. Your last scrub was on Sun Oct  9 00:26:34 2022 and took 00:01:33. That was 7 months ago... It is setup to run as a cron job to run automatically at midnight, on the second Sunday of the month. (There is a ZFS Trim job that happens on the first Sunday of the month.) Which means that computer needs to be on, for that to happen. Recommends are that pools on Commercial Enterprise grade drives get scrubbed once a month, and home type desktop drives get scrubbed once a week. If you are not going to leave your computer running for these to happens, then you should run them manually.

Based on your last scrub job, I would let it run for about 10 minutes, then check it with
```

sudo zpool status -v rpool

```
Hopefully it finds and corrects errors for you and goes back "online"...

---

### Post by #&amp;thj^% on 2023-04-18
> **MAFoElffen said:**
> LOL. Then run the report via
```

system-info --details

```
When it offers to upload the report, enter <Y><Enter> for yes, then copy down the URL to post for us to go over the information it that report. The '--details' flag will toggle it to ask more details queries on ZFS.

After seeing that info, that may show us more on what is happening.
@ MAFoElffen i guess i forgot that>>>"system-info --details" I'm so tired..:D
But ask to see the OP's Repos, by the sound of this OP may have mixed Source Repos (I'm guessing Impish)

---

### Post by MAFoElffen on 2023-04-18
I have been looking at what you posted and thinking about this...

I am waiting to see the report to give you specific commands to run on your machine based on how Linux see's it and ID's certain hardware. *** It will also show us your source list and such...

There are two things that needs to be done. One is from a normal boot from your machine. The other would be from an Ubuntu Desktop Installer LiveUSB. Please have one handy t follow those instructions if needed.

Let's talk about what I see initially. Ubuntu installed with an EXT type of filesystem, uses what is called fsck to be run at boot after so many boots to check the ext4 filesystem, and repair it, if needed. To use fsck, the disks cannot be mounted yet. That's why that runs at boot... Or if needed, while booted from a Live Environment.

ZFS does not use fsck. It has it's own filesystem utility called scrub. ZFS pools can be mounted and online while this is running. Recommends for Commercial Enterprise grade drives is once a month. For Desktop grade drives, the recommends are once a week. Ubuntu has 2 cron jobs scheduled for normal maintenance fro ZFS. One the 1st Sunday, a ZFS Trim job. On the 2nd Sunday, a ZFS Scrub job. You rlast scrub job was run in October, over 7 months ago. That means that your system was not on past midnight, for those jobs to run. If you are not going to leave your Computer on for those to run, then you need to run those manually. That will be your normal maintenance to keep your system healthy.

Along with that, other normal maintenance is routine upgrades, and using "apt autoremove" to clean out old kernels.

I think we can assume that when we get this resolved that you will try harder to keep up with the maintenance of your system.

Another subject would be ZFS snapshots and backups. Those give you two different avenues to recover from a disaster. You could have said (previously), that would never happen... But you can see that things happen when we don't plan for them.

Waiting to see that report so we can suggest some commands to get you back working.

EDIT: Sorry of this is mostly a repeat of my last post. Tired, and couldn't see if it had posted, so thought it didn't post. So i rewrote it with this one. On things that are the same, you can tell what I feel is important with this. LOL

---

### Post by akhilakkapelli on 2023-04-18
Reply to @1fallen's post :

Installation of system-info:
```

akhil@KHUSHI:~$ sudo add-apt-repository ppa:mafoelffen/system-info
Repository: 'deb https://ppa.launchpadcontent.net/mafoelffen/system-info/ubuntu/ jammy main'
Description:
This PPA contains an easy installation Debian package to install the 'system-info' script to your system. We are trying to make this easier to new users, than downloading it from the Forum's GitHub Repository, Homepage located at:
    https://github.com/UbuntuForums/system-info
                   
More info: https://launchpad.net/~mafoelffen/+archive/ubuntu/system-info
Adding repository.
Press [ENTER] to continue or Ctrl-c to cancel.
Found existing deb entry in /etc/apt/sources.list.d/mafoelffen-ubuntu-system-info-jammy.list
Adding deb entry to /etc/apt/sources.list.d/mafoelffen-ubuntu-system-info-jammy.list
Found existing deb-src entry in /etc/apt/sources.list.d/mafoelffen-ubuntu-system-info-jammy.list
Adding disabled deb-src entry to /etc/apt/sources.list.d/mafoelffen-ubuntu-system-info-jammy.list
Adding key to /etc/apt/trusted.gpg.d/mafoelffen-ubuntu-system-info.gpg with fingerprint 8277871A5663940AEF865DACABC6867CBB2280AF
Hit:1 http://packages.microsoft.com/repos/code stable InRelease
Hit:2 https://dl.winehq.org/wine-builds/ubuntu jammy InRelease                 
Hit:3 https://deb.nodesource.com/node_16.x jammy InRelease                     
Hit:4 https://packages.microsoft.com/repos/edge stable InRelease               
Hit:5 https://dl.google.com/linux/chrome/deb stable InRelease                  
Hit:6 http://security.ubuntu.com/ubuntu jammy-security InRelease               
Hit:7 http://in.archive.ubuntu.com/ubuntu jammy InRelease                      
Hit:8 http://in.archive.ubuntu.com/ubuntu jammy-updates InRelease
Hit:9 http://in.archive.ubuntu.com/ubuntu jammy-backports InRelease
Hit:10 https://ppa.launchpadcontent.net/mafoelffen/system-info/ubuntu jammy InRelease
Reading package lists... Done                                  
W: https://dl.winehq.org/wine-builds/ubuntu/dists/jammy/InRelease: Key is stored in legacy trusted.gpg keyring (/etc/apt/trusted.gpg), see the DEPRECATION section in apt-key(8) for details.
akhil@KHUSHI:~$ sudo apt update
Hit:1 https://deb.nodesource.com/node_16.x jammy InRelease
Hit:2 https://dl.winehq.org/wine-builds/ubuntu jammy InRelease                 
Hit:3 http://packages.microsoft.com/repos/code stable InRelease                
Hit:4 http://in.archive.ubuntu.com/ubuntu jammy InRelease                      
Hit:5 http://security.ubuntu.com/ubuntu jammy-security InRelease               
Hit:6 https://packages.microsoft.com/repos/edge stable InRelease               
Hit:7 https://dl.google.com/linux/chrome/deb stable InRelease                  
Hit:8 http://in.archive.ubuntu.com/ubuntu jammy-updates InRelease              
Hit:9 http://in.archive.ubuntu.com/ubuntu jammy-backports InRelease            
Hit:10 https://ppa.launchpadcontent.net/mafoelffen/system-info/ubuntu jammy InRelease
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
40 packages can be upgraded. Run 'apt list --upgradable' to see them.
W: https://dl.winehq.org/wine-builds/ubuntu/dists/jammy/InRelease: Key is stored in legacy trusted.gpg keyring (/etc/apt/trusted.gpg), see the DEPRECATION section in apt-key(8) for details.
akhil@KHUSHI:~$ sudo apt install system-info
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages will be REMOVED:
  linux-image-5.15.0-50-generic
The following NEW packages will be installed:
  system-info
0 upgraded, 1 newly installed, 1 to remove and 40 not upgraded.
2 not fully installed or removed.
Need to get 0 B/33.3 kB of archives.
After this operation, 11.4 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 329778 files and directories currently installed.)
Removing linux-image-5.15.0-50-generic (5.15.0-50.56) ...
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-5.15.0-50-generic
/etc/kernel/postrm.d/zz-update-grub:
/usr/sbin/grub-probe: error: failed to get canonical path of `rpool/ROOT/ubuntu_
zs8jjk'.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 1
dpkg: error processing package linux-image-5.15.0-50-generic (--remove):
 installed linux-image-5.15.0-50-generic package post-removal script subprocess 
returned error exit status 1
dpkg: too many errors, stopping
Errors were encountered while processing:
 linux-image-5.15.0-50-generic
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
akhil@KHUSHI:~$ system-info --details
system-info: command not found


```

Couldn't able to install this software.

Zys Installed?
```

akhil@KHUSHI:~$ sudo apt list zsys --installed
Listing... Done

```

SmartCtl:
```

akhil@KHUSHI:~$ sudo smartctl -H /dev/sda
smartctl 7.2 2020-12-30 r5155 [x86_64-linux-5.15.0-52-generic] (local build)
Copyright (C) 2002-20, Bruce Allen, Christian Franke, www.smartmontools.org


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

```

Rpool Status:
```

akhil@KHUSHI:~$ sudo zpool status -v rpool
  pool: rpool
 state: DEGRADED
status: One or more devices has experienced an unrecoverable error.  An
	attempt was made to correct the error.  Applications are unaffected.
action: Determine if the device needs to be replaced, and clear the errors
	using 'zpool clear' or replace the device with 'zpool replace'.
   see: https://openzfs.github.io/openzfs-docs/msg/ZFS-8000-9P
  scan: scrub repaired 0B in 00:07:43 with 0 errors on Wed Apr 19 01:17:47 2023
config:


	NAME                                    STATE     READ WRITE CKSUM
	rpool                                   DEGRADED     0     0     0
	  499a9b9e-724f-dc4c-95ad-71d1af5b0105  DEGRADED     0     0     0  too many errors


errors: No known data errors

```

---

### Post by #&amp;thj^% on 2023-04-18
What shows with 
```
sudo zpool clear rpool
```
This will clear all errors associated with the virtual devices in the pool, and clear any data error counts associated with the pool.
Now show:
```
zpool status

```

---

### Post by akhilakkapelli on 2023-04-18
Zpool clear command:

```

akhil@KHUSHI:~$ sudo zpool clear rpool
[sudo] password for akhil: 



akhil@KHUSHI:~$ sudo zpool status -v rpool
  pool: rpool
 state: ONLINE
  scan: scrub repaired 0B in 00:07:43 with 0 errors on Wed Apr 19 01:17:47 2023
config:


    NAME                                    STATE     READ WRITE CKSUM
    rpool                                   ONLINE       0     0     0
      499a9b9e-724f-dc4c-95ad-71d1af5b0105  ONLINE       0     0     0


errors: No known data errors


akhil@KHUSHI:~$ zpool status
  pool: bpool
 state: ONLINE
  scan: scrub repaired 0B in 00:00:01 with 0 errors on Sun Apr  9 00:24:02 2023
config:


    NAME                                    STATE     READ WRITE CKSUM
    bpool                                   ONLINE       0     0     0
      4f9732b2-2838-4e48-9aa1-62687a2c4315  ONLINE       0     0     0


errors: No known data errors


  pool: rpool
 state: ONLINE
  scan: scrub repaired 0B in 00:07:43 with 0 errors on Wed Apr 19 01:17:47 2023
config:


    NAME                                    STATE     READ WRITE CKSUM
    rpool                                   ONLINE       0     0     0
      499a9b9e-724f-dc4c-95ad-71d1af5b0105  ONLINE       0     0     0


errors: No known data errors

```

When I upgrade:

```

akhil@KHUSHI:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 linux-image-5.15.0-50-generic : Depends: linux-modules-5.15.0-50-generic but it is not going to be installed
                                 Recommends: grub-pc but it is not going to be installed or
                                             grub-efi-amd64 or
                                             grub-efi-ia32 but it is not going to be installed or
                                             grub but it is not installable or
                                             lilo but it is not going to be installed
E: Broken packages

```

I cannot upgrade but I can install new applications using sudo apt install.

---

### Post by #&amp;thj^% on 2023-04-18
How's your package manager now?
```
sudo apt update && sudo apt upgrade -y
```

---

### Post by akhilakkapelli on 2023-04-18
Update and Upgrade:

```

akhil@KHUSHI:~$ sudo apt update && sudo apt upgrade -y
[sudo] password for akhil: 
Hit:1 http://packages.microsoft.com/repos/code stable InRelease                
Hit:2 https://packages.microsoft.com/repos/edge stable InRelease               
Hit:3 https://dl.google.com/linux/chrome/deb stable InRelease                  
Get:4 http://security.ubuntu.com/ubuntu jammy-security InRelease [110 kB]      
Hit:5 https://ppa.launchpadcontent.net/mafoelffen/system-info/ubuntu jammy InRelease
Hit:6 https://dl.winehq.org/wine-builds/ubuntu jammy InRelease                 
Hit:7 https://deb.nodesource.com/node_16.x jammy InRelease                     
Hit:8 http://in.archive.ubuntu.com/ubuntu jammy InRelease    
Hit:9 http://in.archive.ubuntu.com/ubuntu jammy-updates InRelease
Get:10 http://in.archive.ubuntu.com/ubuntu jammy-backports InRelease [108 kB]
Fetched 218 kB in 5s (46.6 kB/s)    
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
40 packages can be upgraded. Run 'apt list --upgradable' to see them.
W: https://dl.winehq.org/wine-builds/ubuntu/dists/jammy/InRelease: Key is stored in legacy trusted.gpg keyring (/etc/apt/trusted.gpg), see the DEPRECATION section in apt-key(8) for details.
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
Get more security updates through Ubuntu Pro with 'esm-apps' enabled:
  python2.7-minimal libjs-jquery-ui libmaven3-core-java libopenexr25
  libpostproc55 libavcodec58 libavutil56 libswscale5 libswresample3
  libavformat58 python2.7 libpython2.7-minimal libpython2.7-stdlib
  libavfilter7
Learn more about Ubuntu Pro at https://ubuntu.com/pro
The following packages have been kept back:
  gnome-remote-desktop
The following packages will be upgraded:
  apport apport-gtk code ghostscript ghostscript-x google-chrome-stable libgs9
  libgs9-common libldb2 liblouis-data liblouis20 libpulse-mainloop-glib0
  libpulse0 libpulse0:i386 libpulsedsp libsmbclient libwbclient0
  microsoft-edge-dev pulseaudio pulseaudio-module-bluetooth pulseaudio-utils
  python3-apport python3-ldb python3-louis python3-problem-report samba-libs
  sudo thunderbird thunderbird-gnome-support thunderbird-locale-en
  thunderbird-locale-en-us tzdata vim-common vim-tiny xserver-common
  xserver-xephyr xserver-xorg-core xserver-xorg-legacy xxd
39 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
25 standard LTS security updates
Need to get 306 MB/414 MB of archives.
After this operation, 3,275 kB of additional disk space will be used.
Get:1 https://packages.microsoft.com/repos/edge stable/main amd64 microsoft-edge-dev amd64 114.0.1793.0-1 [147 MB]
Get:2 https://dl.google.com/linux/chrome/deb stable/main amd64 google-chrome-stable amd64 112.0.5615.121-1 [93.8 MB]
Get:3 http://in.archive.ubuntu.com/ubuntu jammy-updates/main amd64 thunderbird amd64 1:102.10.0+build2-0ubuntu0.22.04.1 [62.5 MB]
Get:4 http://in.archive.ubuntu.com/ubuntu jammy-updates/main amd64 thunderbird-gnome-support amd64 1:102.10.0+build2-0ubuntu0.22.04.1 [8,628 B]
Get:5 http://in.archive.ubuntu.com/ubuntu jammy-updates/main amd64 thunderbird-locale-en-us all 1:102.10.0+build2-0ubuntu0.22.04.1 [9,248 B]
Get:6 http://in.archive.ubuntu.com/ubuntu jammy-updates/main amd64 xserver-common all 2:21.1.4-2ubuntu1.7~22.04.1 [28.0 kB]
Get:7 http://in.archive.ubuntu.com/ubuntu jammy-updates/main amd64 xserver-xephyr amd64 2:21.1.4-2ubuntu1.7~22.04.1 [1,012 kB]
Get:8 http://in.archive.ubuntu.com/ubuntu jammy-updates/main amd64 xserver-xorg-legacy amd64 2:21.1.4-2ubuntu1.7~22.04.1 [34.7 kB]
Get:9 http://in.archive.ubuntu.com/ubuntu jammy-updates/main amd64 xserver-xorg-core amd64 2:21.1.4-2ubuntu1.7~22.04.1 [1,476 kB]
Fetched 221 MB in 39s (5,609 kB/s)                                             
Extracting templates from packages: 100%
Preconfiguring packages ...
setting xserver-xorg-legacy/xwrapper/allowed_users from configuration file
(Reading database ... 329811 files and directories currently installed.)
Preparing to unpack .../00-google-chrome-stable_112.0.5615.121-1_amd64.deb ...
Unpacking google-chrome-stable (112.0.5615.121-1) over (111.0.5563.146-1) ...
Preparing to unpack .../01-python3-ldb_2%3a2.4.4-0ubuntu0.22.04.2_amd64.deb ...
Unpacking python3-ldb (2:2.4.4-0ubuntu0.22.04.2) over (2:2.4.4-0ubuntu0.22.04.1)
 ...
Preparing to unpack .../02-libldb2_2%3a2.4.4-0ubuntu0.22.04.2_amd64.deb ...
Unpacking libldb2:amd64 (2:2.4.4-0ubuntu0.22.04.2) over (2:2.4.4-0ubuntu0.22.04.
1) ...
Preparing to unpack .../03-libsmbclient_2%3a4.15.13+dfsg-0ubuntu1.1_amd64.deb ..
.
Unpacking libsmbclient:amd64 (2:4.15.13+dfsg-0ubuntu1.1) over (2:4.15.13+dfsg-0u
buntu1) ...
Preparing to unpack .../04-libwbclient0_2%3a4.15.13+dfsg-0ubuntu1.1_amd64.deb ..
.
Unpacking libwbclient0:amd64 (2:4.15.13+dfsg-0ubuntu1.1) over (2:4.15.13+dfsg-0u
buntu1) ...
Preparing to unpack .../05-samba-libs_2%3a4.15.13+dfsg-0ubuntu1.1_amd64.deb ...
Unpacking samba-libs:amd64 (2:4.15.13+dfsg-0ubuntu1.1) over (2:4.15.13+dfsg-0ubu
ntu1) ...
Preparing to unpack .../06-microsoft-edge-dev_114.0.1793.0-1_amd64.deb ...
Unpacking microsoft-edge-dev (114.0.1793.0-1) over (113.0.1754.0-1) ...
Preparing to unpack .../07-libpulse-mainloop-glib0_1%3a15.99.1+dfsg1-1ubuntu2.1_
amd64.deb ...
Unpacking libpulse-mainloop-glib0:amd64 (1:15.99.1+dfsg1-1ubuntu2.1) over (1:15.
99.1+dfsg1-1ubuntu2) ...
Preparing to unpack .../08-pulseaudio-utils_1%3a15.99.1+dfsg1-1ubuntu2.1_amd64.d
eb ...
Unpacking pulseaudio-utils (1:15.99.1+dfsg1-1ubuntu2.1) over (1:15.99.1+dfsg1-1u
buntu2) ...
Preparing to unpack .../09-pulseaudio-module-bluetooth_1%3a15.99.1+dfsg1-1ubuntu
2.1_amd64.deb ...
Unpacking pulseaudio-module-bluetooth (1:15.99.1+dfsg1-1ubuntu2.1) over (1:15.99
.1+dfsg1-1ubuntu2) ...
Preparing to unpack .../10-pulseaudio_1%3a15.99.1+dfsg1-1ubuntu2.1_amd64.deb ...
Unpacking pulseaudio (1:15.99.1+dfsg1-1ubuntu2.1) over (1:15.99.1+dfsg1-1ubuntu2
) ...
Preparing to unpack .../11-libpulsedsp_1%3a15.99.1+dfsg1-1ubuntu2.1_amd64.deb ..
.
Unpacking libpulsedsp:amd64 (1:15.99.1+dfsg1-1ubuntu2.1) over (1:15.99.1+dfsg1-1
ubuntu2) ...
Preparing to unpack .../12-libpulse0_1%3a15.99.1+dfsg1-1ubuntu2.1_amd64.deb ...
De-configuring libpulse0:i386 (1:15.99.1+dfsg1-1ubuntu2), to allow configuration
 of libpulse0:amd64 (1:15.99.1+dfsg1-1ubuntu2) ...
Unpacking libpulse0:amd64 (1:15.99.1+dfsg1-1ubuntu2.1) over (1:15.99.1+dfsg1-1ub
untu2) ...
Preparing to unpack .../13-libpulse0_1%3a15.99.1+dfsg1-1ubuntu2.1_i386.deb ...
Unpacking libpulse0:i386 (1:15.99.1+dfsg1-1ubuntu2.1) over (1:15.99.1+dfsg1-1ubu
ntu2) ...
Preparing to unpack .../14-sudo_1.9.9-1ubuntu2.4_amd64.deb ...
Unpacking sudo (1.9.9-1ubuntu2.4) over (1.9.9-1ubuntu2.3) ...
Preparing to unpack .../15-tzdata_2023c-0ubuntu0.22.04.0_all.deb ...
Unpacking tzdata (2023c-0ubuntu0.22.04.0) over (2023b-0ubuntu0.22.04.0) ...
Preparing to unpack .../16-vim-tiny_2%3a8.2.3995-1ubuntu2.5_amd64.deb ...
Unpacking vim-tiny (2:8.2.3995-1ubuntu2.5) over (2:8.2.3995-1ubuntu2.4) ...
Preparing to unpack .../17-xxd_2%3a8.2.3995-1ubuntu2.5_amd64.deb ...
Unpacking xxd (2:8.2.3995-1ubuntu2.5) over (2:8.2.3995-1ubuntu2.4) ...
Preparing to unpack .../18-vim-common_2%3a8.2.3995-1ubuntu2.5_all.deb ...
Unpacking vim-common (2:8.2.3995-1ubuntu2.5) over (2:8.2.3995-1ubuntu2.4) ...
Preparing to unpack .../19-python3-problem-report_2.20.11-0ubuntu82.4_all.deb ..
.
Unpacking python3-problem-report (2.20.11-0ubuntu82.4) over (2.20.11-0ubuntu82.3
) ...
Preparing to unpack .../20-python3-apport_2.20.11-0ubuntu82.4_all.deb ...
Unpacking python3-apport (2.20.11-0ubuntu82.4) over (2.20.11-0ubuntu82.3) ...
Preparing to unpack .../21-apport_2.20.11-0ubuntu82.4_all.deb ...
Unpacking apport (2.20.11-0ubuntu82.4) over (2.20.11-0ubuntu82.3) ...
Preparing to unpack .../22-apport-gtk_2.20.11-0ubuntu82.4_all.deb ...
Unpacking apport-gtk (2.20.11-0ubuntu82.4) over (2.20.11-0ubuntu82.3) ...
Preparing to unpack .../23-code_1.77.3-1681292746_amd64.deb ...
Unpacking code (1.77.3-1681292746) over (1.77.0-1680085573) ...
Preparing to unpack .../24-ghostscript-x_9.55.0~dfsg1-0ubuntu5.2_amd64.deb ...
Unpacking ghostscript-x (9.55.0~dfsg1-0ubuntu5.2) over (9.55.0~dfsg1-0ubuntu5.1)
 ...
Preparing to unpack .../25-ghostscript_9.55.0~dfsg1-0ubuntu5.2_amd64.deb ...
Unpacking ghostscript (9.55.0~dfsg1-0ubuntu5.2) over (9.55.0~dfsg1-0ubuntu5.1) .
..
Preparing to unpack .../26-libgs9_9.55.0~dfsg1-0ubuntu5.2_amd64.deb ...
Unpacking libgs9:amd64 (9.55.0~dfsg1-0ubuntu5.2) over (9.55.0~dfsg1-0ubuntu5.1) 
...
Preparing to unpack .../27-libgs9-common_9.55.0~dfsg1-0ubuntu5.2_all.deb ...
Unpacking libgs9-common (9.55.0~dfsg1-0ubuntu5.2) over (9.55.0~dfsg1-0ubuntu5.1)
 ...
Preparing to unpack .../28-liblouis-data_3.20.0-2ubuntu0.2_all.deb ...
Unpacking liblouis-data (3.20.0-2ubuntu0.2) over (3.20.0-2ubuntu0.1) ...
Preparing to unpack .../29-liblouis20_3.20.0-2ubuntu0.2_amd64.deb ...
Unpacking liblouis20:amd64 (3.20.0-2ubuntu0.2) over (3.20.0-2ubuntu0.1) ...
Preparing to unpack .../30-thunderbird-locale-en_1%3a102.10.0+build2-0ubuntu0.22
.04.1_amd64.deb ...
Unpacking thunderbird-locale-en (1:102.10.0+build2-0ubuntu0.22.04.1) over (1:102
.9.0+build1-0ubuntu0.22.04.1) ...
Preparing to unpack .../31-thunderbird_1%3a102.10.0+build2-0ubuntu0.22.04.1_amd6
4.deb ...
Unpacking thunderbird (1:102.10.0+build2-0ubuntu0.22.04.1) over (1:102.9.0+build
1-0ubuntu0.22.04.1) ...
Preparing to unpack .../32-thunderbird-gnome-support_1%3a102.10.0+build2-0ubuntu
0.22.04.1_amd64.deb ...
Unpacking thunderbird-gnome-support (1:102.10.0+build2-0ubuntu0.22.04.1) over (1
:102.9.0+build1-0ubuntu0.22.04.1) ...
Preparing to unpack .../33-thunderbird-locale-en-us_1%3a102.10.0+build2-0ubuntu0
.22.04.1_all.deb ...
Unpacking thunderbird-locale-en-us (1:102.10.0+build2-0ubuntu0.22.04.1) over (1:
102.9.0+build1-0ubuntu0.22.04.1) ...
Preparing to unpack .../34-xserver-common_2%3a21.1.4-2ubuntu1.7~22.04.1_all.deb 
...
Unpacking xserver-common (2:21.1.4-2ubuntu1.7~22.04.1) over (2:21.1.3-2ubuntu2.9
) ...
Preparing to unpack .../35-xserver-xephyr_2%3a21.1.4-2ubuntu1.7~22.04.1_amd64.de
b ...
Unpacking xserver-xephyr (2:21.1.4-2ubuntu1.7~22.04.1) over (2:21.1.3-2ubuntu2.9
) ...
Preparing to unpack .../36-xserver-xorg-legacy_2%3a21.1.4-2ubuntu1.7~22.04.1_amd
64.deb ...
Unpacking xserver-xorg-legacy (2:21.1.4-2ubuntu1.7~22.04.1) over (2:21.1.3-2ubun
tu2.9) ...
Preparing to unpack .../37-xserver-xorg-core_2%3a21.1.4-2ubuntu1.7~22.04.1_amd64
.deb ...
Unpacking xserver-xorg-core (2:21.1.4-2ubuntu1.7~22.04.1) over (2:21.1.3-2ubuntu
2.9) ...
Preparing to unpack .../38-python3-louis_3.20.0-2ubuntu0.2_all.deb ...
Unpacking python3-louis (3.20.0-2ubuntu0.2) over (3.20.0-2ubuntu0.1) ...
Setting up libgs9-common (9.55.0~dfsg1-0ubuntu5.2) ...
Setting up code (1.77.3-1681292746) ...
Setting up google-chrome-stable (112.0.5615.121-1) ...
Setting up libgs9:amd64 (9.55.0~dfsg1-0ubuntu5.2) ...
Setting up libpulse0:amd64 (1:15.99.1+dfsg1-1ubuntu2.1) ...
Setting up libpulse0:i386 (1:15.99.1+dfsg1-1ubuntu2.1) ...
Setting up python3-problem-report (2.20.11-0ubuntu82.4) ...
Setting up libpulsedsp:amd64 (1:15.99.1+dfsg1-1ubuntu2.1) ...
Setting up ghostscript (9.55.0~dfsg1-0ubuntu5.2) ...
Setting up libwbclient0:amd64 (2:4.15.13+dfsg-0ubuntu1.1) ...
Setting up xxd (2:8.2.3995-1ubuntu2.5) ...
Setting up python3-apport (2.20.11-0ubuntu82.4) ...
Setting up tzdata (2023c-0ubuntu0.22.04.0) ...


Current default time zone: 'Asia/Kolkata'
Local time is now:      Wed Apr 19 03:10:03 IST 2023.
Universal Time is now:  Tue Apr 18 21:40:03 UTC 2023.
Run 'dpkg-reconfigure tzdata' if you wish to change it.


Setting up vim-common (2:8.2.3995-1ubuntu2.5) ...
Setting up liblouis-data (3.20.0-2ubuntu0.2) ...
Setting up libpulse-mainloop-glib0:amd64 (1:15.99.1+dfsg1-1ubuntu2.1) ...
Setting up pulseaudio-utils (1:15.99.1+dfsg1-1ubuntu2.1) ...
Setting up sudo (1.9.9-1ubuntu2.4) ...
Setting up thunderbird (1:102.10.0+build2-0ubuntu0.22.04.1) ...
Setting up microsoft-edge-dev (114.0.1793.0-1) ...
Setting up xserver-common (2:21.1.4-2ubuntu1.7~22.04.1) ...
Setting up libldb2:amd64 (2:2.4.4-0ubuntu0.22.04.2) ...
Setting up xserver-xorg-legacy (2:21.1.4-2ubuntu1.7~22.04.1) ...
setting xserver-xorg-legacy/xwrapper/allowed_users from configuration file
Setting up liblouis20:amd64 (3.20.0-2ubuntu0.2) ...
Setting up xserver-xorg-core (2:21.1.4-2ubuntu1.7~22.04.1) ...
Setting up ghostscript-x (9.55.0~dfsg1-0ubuntu5.2) ...
Setting up vim-tiny (2:8.2.3995-1ubuntu2.5) ...
Setting up pulseaudio (1:15.99.1+dfsg1-1ubuntu2.1) ...
Setting up thunderbird-locale-en (1:102.10.0+build2-0ubuntu0.22.04.1) ...
Setting up apport (2.20.11-0ubuntu82.4) ...
apport-autoreport.service is a disabled or a static unit, not starting it.
Setting up thunderbird-locale-en-us (1:102.10.0+build2-0ubuntu0.22.04.1) ...
Setting up python3-louis (3.20.0-2ubuntu0.2) ...
Setting up xserver-xephyr (2:21.1.4-2ubuntu1.7~22.04.1) ...
Setting up thunderbird-gnome-support (1:102.10.0+build2-0ubuntu0.22.04.1) ...
Setting up python3-ldb (2:2.4.4-0ubuntu0.22.04.2) ...
Setting up pulseaudio-module-bluetooth (1:15.99.1+dfsg1-1ubuntu2.1) ...
Setting up apport-gtk (2.20.11-0ubuntu82.4) ...
Setting up samba-libs:amd64 (2:4.15.13+dfsg-0ubuntu1.1) ...
Setting up libsmbclient:amd64 (2:4.15.13+dfsg-0ubuntu1.1) ...
Processing triggers for desktop-file-utils (0.26-1ubuntu3) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Processing triggers for gnome-menus (3.36.0-1ubuntu3) ...
Processing triggers for libc-bin (2.35-0ubuntu3.1) ...
Processing triggers for man-db (2.10.2-1) ...
Processing triggers for dbus (1.12.20-2ubuntu4.1) ...
Processing triggers for shared-mime-info (2.1-2) ...
Processing triggers for mailcap (3.70+nmu1ubuntu1) ...

```

Is my system back to normal? What was the problem?

---

### Post by #&amp;thj^% on 2023-04-18
> **akhilakkapelli said:**
> 

Is my system back to normal?

Should be, this is a bonus running zfs-root
> **akhilakkapelli said:**
> What was the problem?
I'm not even going to guess here, just stay on top of your systems errors and warnings, and take action then and not later. :)
Your just going through growing pains of a "New to You" system and the forums are a key asset to help.

---

### Post by MAFoElffen on 2023-04-18
Just back from picking the dogs up from the groomer (day off).

Glad everything worked out. Yes, the scrub seems to have corrected the errors and clearing the log brought it back online. 

Right not, since you know the last scrub was done 7 months ago, I would run a scrub on the bpool
```

sudo zpool scrub bpool

```
Then create a snapshot for each pool, so you have a good point to role back to for recovery, for the just-in-cases.
```

zfs snapshot -r rpool@rpool.20230418
zfs snapshot -r bpool@bpool.20230418

```
After that, you can learn to take snapshots of individual datasets, such as your Home, or a specific user's Home. That is why you set up datasets. That way you can rollback a specific dataset to a specific point. I usually am lazy and decide when I am at a good point for a snapshot, then keep only 2-3 back, in case the 1st one back has a problem that I want to get past, and didn't notice.

For my last Admin Job, it was weekly's monthly's and yearly's. Yearly were keep for 7 years. And copies of snapshots were also exported to it's own media and kept offsite. These were complemented by Backups. Snapshots are not a replacement for backups. "Things" happen. Doing things that way, give you multiple paths, with multiple chances at success.

Now that you know how to run a scrub on your pools, and how easy it is, you need to do that every once in a while to make sure your system stays healthy.

The 'trim' job is not really that important to you, but if you wanted to, then do
```

sudo zpool trim bpool
sudo zpool trim rpool

```
What that does is notifies a drive of unallocated blocks for it to reclaim, which would affect thin-provisioned ZFS Pools to shrink in size... Which the install you did is static, not thin-provisioned. So really would have no affect that I know of. Honestly, I am not sure why that specific 'trim' cron job is there for this type of ZFS installation.

The one to keep up on is 'scrub'.

---

