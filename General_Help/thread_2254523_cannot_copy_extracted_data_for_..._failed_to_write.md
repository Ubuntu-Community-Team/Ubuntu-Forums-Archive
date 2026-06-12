---
title: "cannot copy extracted data for ... failed to write (No space left on device)"
date: 2014-11-27
forum: General Help
---

### Post by Dedsec on 2014-11-27
Hello I'am new here and i need some help. Every time i try to upgrade via the command line (Terminal) this just recently happened I get this error. I have tried Google before posting here. But did not find help i would appreciate any help that will be given at this time. Please and thank you in advanced. 

wolfbot@WolfBot:~$ sudo apt-get upgrade
[sudo] password for wolfbot: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-image-extra-3.13.0-40-generic : Depends: linux-image-3.13.0-40-generic but it is not installed
 linux-image-generic : Depends: linux-image-3.13.0-40-generic but it is not installed
E: Unmet dependencies. Try using -f.
wolfbot@WolfBot:~$ sudo apt-get -f upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  linux-image-3.13.0-40-generic
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
100 not fully installed or removed.
Need to get 0 B/15.1 MB of archives.
After this operation, 42.1 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 335878 files and directories currently installed.)
Preparing to unpack .../linux-image-3.13.0-40-generic_3.13.0-40.69_amd64.deb ...
Done.
Unpacking linux-image-3.13.0-40-generic (3.13.0-40.69) ...
No apport report written because the error message indicates a disk full error
                                                                              dpkg: error processing archive /var/cache/apt/archives/linux-image-3.13.0-40-generic_3.13.0-40.69_amd64.deb (--unpack):
 cannot copy extracted data for './boot/System.map-3.13.0-40-generic' to '/boot/System.map-3.13.0-40-generic.dpkg-new': failed to write (No space left on device)
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-40-generic /boot/vmlinuz-3.13.0-40-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-40-generic /boot/vmlinuz-3.13.0-40-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
wolfbot@WolfBot:~$

---

### Post by matt_symes on 2014-11-27
Hi

It's telling you the error: no space left on device.

You need to free up some space on the partition containing the directory /boot.

Please post the output of these two commands into your next post.

```

df -h
df -i

```

Kjnd regards

---

### Post by Dedsec on 2014-12-06
Sorry it took so long been sick here is the 2 outputs from them commands. 
```
wolfbot@WolfBot:~$ df -h
Filesystem                    Size  Used Avail Use% Mounted on
/dev/mapper/kubuntu--vg-root  1.8T  452G  1.3T  27% /
none                          4.0K     0  4.0K   0% /sys/fs/cgroup
udev                          3.9G   12K  3.9G   1% /dev
tmpfs                         799M  1.5M  797M   1% /run
none                          5.0M     0  5.0M   0% /run/lock
none                          3.9G   27M  3.9G   1% /run/shm
none                          100M   24K  100M   1% /run/user
/dev/sda1                     236M  233M     0 100% /boot
/home/wolfbot/.Private        1.8T  452G  1.3T  27% /home/wolfbot
/dev/sdd1                     917G   72M  871G   1% /media/wolfbot/Backup
wolfbot@WolfBot:~$ df -i
Filesystem                      Inodes  IUsed     IFree IUse% Mounted on
/dev/mapper/kubuntu--vg-root 121552896 686540 120866356    1% /
none                           1021955      2   1021953    1% /sys/fs/cgroup
udev                           1018084    624   1017460    1% /dev
tmpfs                          1021955    671   1021284    1% /run
none                           1021955      4   1021951    1% /run/lock
none                           1021955     43   1021912    1% /run/shm
none                           1021955     20   1021935    1% /run/user
/dev/sda1                        62248    327     61921    1% /boot
/home/wolfbot/.Private       121552896 686540 120866356    1% /home/wolfbot
/dev/sdd1                     61046784     11  61046773    1% /media/wolfbot/Backup
wolfbot@WolfBot:~$
```

---

### Post by matt_symes on 2014-12-06
Hi

your boot partition (sda1) is full up. You need to remove some old kernels.

can you post the output of this command

```
dpkg -l | grep -G "linux.*image.*"
```

That's a capital G above.

Kind regards

---

### Post by Dedsec on 2014-12-06
```
wolfbot@WolfBot:~$ dpkg -l | grep -G "linux.*image.*"rc  linux-image-3.13.0-32-generic               3.13.0-32.57                          amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-33-generic               3.13.0-33.58                          amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-34-generic               3.13.0-34.60                          amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-35-generic               3.13.0-35.62                          amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-36-generic               3.13.0-36.63                          amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-37-generic               3.13.0-37.64                          amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-39-generic               3.13.0-39.66                          amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-32-generic         3.13.0-32.57                          amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-33-generic         3.13.0-33.58                          amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-34-generic         3.13.0-34.60                          amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-35-generic         3.13.0-35.62                          amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-36-generic         3.13.0-36.63                          amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-37-generic         3.13.0-37.64                          amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
iF  linux-image-extra-3.13.0-39-generic         3.13.0-39.66                          amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
iU  linux-image-extra-3.13.0-40-generic         3.13.0-40.69                          amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
iU  linux-image-generic                         3.13.0.40.47                          amd64        Generic Linux kernel image
wolfbot@WolfBot:~$ 
```

---

### Post by matt_symes on 2014-12-06
Hi. 

Open a a terminal and type

```
sudo dpkg -P linux-image{-extra}-3.13.0-{33,34,35,36}-generic
```

It will remove all but your newest two kernels.

Then type

```
sudo apt-get -f install
```

You then may want to remove the associated kernel header files.

Kind regards

---

### Post by Dedsec on 2014-12-06
> **matt_symes said:**
> Hi. 

Open a a terminal and type

```
sudo dpkg -P linux-image{-extra}-3.13.0-{33,34,35,36}-generic
```

It will remove all but your newest two kernels.

Then type

```
sudo apt-get -f install
```

You then may want to remove the associated kernel header files.

Kind regards
------------------------------------------------------------------------------------
When I did the first command i got this I assume just replace {} brackets with () ? 
```
wolfbot@WolfBot:~$ sudo dpkg -P linux-image{-extra}-3.13.0-{33,34,35,36}-generic[sudo] password for wolfbot: 
dpkg: error: --purge needs a valid package name but 'linux-image{-extra}-3.13.0-33-generic' is not: illegal package name in specifier 'linux-image{-extra}-3.13.0-33-generic': character `{' not allowed (only letters, digits and characters `-+._')


Type dpkg --help for help about installing and deinstalling packages 
[*];
Use 'apt' or 'aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;


Options marked 
[*] produce a lot of output - pipe it through 'less' or 'more' !

```
Also how do I remove kernel header files?

---

### Post by matt_symes on 2014-12-06
Hi

Sorry. My typo. Using my phone to type these posts and sometimes it auto incorrects my typing.

There's a missing comma in the command. Try this instead.

```
sudo dpkg -P linux-image{,-extra}-3.13.0-{33,34,35,36}-generic
```

Then update as instructed in the last post.

EDIT: To remove the kernel headers

```
sudo dpkg -P linux-headers-3.13.0-{33,34,35,36}
```

Kind regards

---

### Post by Dedsec on 2014-12-06
Okay I did that command and this is the output I got. No errors from what I seen but figured i will post for any problems if they come up. 
```
wolfbot@WolfBot:~$ sudo dpkg -P linux-image{,-extra}-3.13.0-{33,34,35,36}-generic[sudo] password for wolfbot: 
(Reading database ... 335877 files and directories currently installed.)
Removing linux-image-extra-3.13.0-33-generic (3.13.0-33.58) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-33-generic /boot/vmlinuz-3.13.0-33-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-33-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-33-generic /boot/vmlinuz-3.13.0-33-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-39-generic
Found initrd image: /boot/initrd.img-3.13.0-39-generic
Found linux image: /boot/vmlinuz-3.13.0-37-generic
Found initrd image: /boot/initrd.img-3.13.0-37-generic
Found linux image: /boot/vmlinuz-3.13.0-36-generic
Found initrd image: /boot/initrd.img-3.13.0-36-generic
Found linux image: /boot/vmlinuz-3.13.0-35-generic
Found initrd image: /boot/initrd.img-3.13.0-35-generic
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.13.0-33-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
Found Windows 7 (loader) on /dev/sdb1
done
Purging configuration files for linux-image-extra-3.13.0-33-generic (3.13.0-33.58) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-33-generic /boot/vmlinuz-3.13.0-33-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-33-generic /boot/vmlinuz-3.13.0-33-generic
Removing linux-image-extra-3.13.0-34-generic (3.13.0-34.60) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-34-generic /boot/vmlinuz-3.13.0-34-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-34-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-34-generic /boot/vmlinuz-3.13.0-34-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-39-generic
Found initrd image: /boot/initrd.img-3.13.0-39-generic
Found linux image: /boot/vmlinuz-3.13.0-37-generic
Found initrd image: /boot/initrd.img-3.13.0-37-generic
Found linux image: /boot/vmlinuz-3.13.0-36-generic
Found initrd image: /boot/initrd.img-3.13.0-36-generic
Found linux image: /boot/vmlinuz-3.13.0-35-generic
Found initrd image: /boot/initrd.img-3.13.0-35-generic
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.13.0-33-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
Found Windows 7 (loader) on /dev/sdb1
done
Purging configuration files for linux-image-extra-3.13.0-34-generic (3.13.0-34.60) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-34-generic /boot/vmlinuz-3.13.0-34-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-34-generic /boot/vmlinuz-3.13.0-34-generic
Removing linux-image-extra-3.13.0-35-generic (3.13.0-35.62) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-35-generic /boot/vmlinuz-3.13.0-35-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-35-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-35-generic /boot/vmlinuz-3.13.0-35-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-39-generic
Found initrd image: /boot/initrd.img-3.13.0-39-generic
Found linux image: /boot/vmlinuz-3.13.0-37-generic
Found initrd image: /boot/initrd.img-3.13.0-37-generic
Found linux image: /boot/vmlinuz-3.13.0-36-generic
Found initrd image: /boot/initrd.img-3.13.0-36-generic
Found linux image: /boot/vmlinuz-3.13.0-35-generic
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.13.0-33-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
Found Windows 7 (loader) on /dev/sdb1
done
Purging configuration files for linux-image-extra-3.13.0-35-generic (3.13.0-35.62) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-35-generic /boot/vmlinuz-3.13.0-35-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-35-generic /boot/vmlinuz-3.13.0-35-generic
Removing linux-image-extra-3.13.0-36-generic (3.13.0-36.63) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-36-generic /boot/vmlinuz-3.13.0-36-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-36-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-36-generic /boot/vmlinuz-3.13.0-36-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-39-generic
Found initrd image: /boot/initrd.img-3.13.0-39-generic
Found linux image: /boot/vmlinuz-3.13.0-37-generic
Found initrd image: /boot/initrd.img-3.13.0-37-generic
Found linux image: /boot/vmlinuz-3.13.0-36-generic
Found linux image: /boot/vmlinuz-3.13.0-35-generic
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.13.0-33-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
Found Windows 7 (loader) on /dev/sdb1
done
Purging configuration files for linux-image-extra-3.13.0-36-generic (3.13.0-36.63) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-36-generic /boot/vmlinuz-3.13.0-36-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-36-generic /boot/vmlinuz-3.13.0-36-generic
Removing linux-image-3.13.0-33-generic (3.13.0-33.58) ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.13.0-33-generic /boot/vmlinuz-3.13.0-33-generic
dkms: removing: bbswitch 0.7 (3.13.0-33-generic) (x86_64)


-------- Uninstall Beginning --------
Module:  bbswitch
Version: 0.7
Kernel:  3.13.0-33-generic (x86_64)
-------------------------------------


Status: Before uninstall, this module version was ACTIVE on this kernel.


bbswitch.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.13.0-33-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


depmod....


DKMS: uninstall completed.
dkms: removing: nvidia-331 331.38 (3.13.0-33-generic) (x86_64)


-------- Uninstall Beginning --------
Module:  nvidia-331
Version: 331.38
Kernel:  3.13.0-33-generic (x86_64)
-------------------------------------


Status: Before uninstall, this module version was ACTIVE on this kernel.


nvidia_331.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.13.0-33-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


depmod....


DKMS: uninstall completed.
dkms: removing: virtualbox 4.3.10 (3.13.0-33-generic) (x86_64)


-------- Uninstall Beginning --------
Module:  virtualbox
Version: 4.3.10
Kernel:  3.13.0-33-generic (x86_64)
-------------------------------------


Status: Before uninstall, this module version was ACTIVE on this kernel.


vboxdrv.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.13.0-33-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.




vboxnetadp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.13.0-33-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.




vboxnetflt.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.13.0-33-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.




vboxpci.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.13.0-33-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


depmod....


DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-33-generic /boot/vmlinuz-3.13.0-33-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-33-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-33-generic /boot/vmlinuz-3.13.0-33-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-39-generic
Found initrd image: /boot/initrd.img-3.13.0-39-generic
Found linux image: /boot/vmlinuz-3.13.0-37-generic
Found initrd image: /boot/initrd.img-3.13.0-37-generic
Found linux image: /boot/vmlinuz-3.13.0-36-generic
Found linux image: /boot/vmlinuz-3.13.0-35-generic
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
Found Windows 7 (loader) on /dev/sdb1
done
Purging configuration files for linux-image-3.13.0-33-generic (3.13.0-33.58) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-33-generic /boot/vmlinuz-3.13.0-33-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-33-generic /boot/vmlinuz-3.13.0-33-generic
Removing linux-image-3.13.0-34-generic (3.13.0-34.60) ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.13.0-34-generic /boot/vmlinuz-3.13.0-34-generic
dkms: removing: bbswitch 0.7 (3.13.0-34-generic) (x86_64)


-------- Uninstall Beginning --------
Module:  bbswitch
Version: 0.7
Kernel:  3.13.0-34-generic (x86_64)
-------------------------------------


Status: Before uninstall, this module version was ACTIVE on this kernel.


bbswitch.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.13.0-34-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


depmod....


DKMS: uninstall completed.
dkms: removing: nvidia-331 331.38 (3.13.0-34-generic) (x86_64)


-------- Uninstall Beginning --------
Module:  nvidia-331
Version: 331.38
Kernel:  3.13.0-34-generic (x86_64)
-------------------------------------


Status: Before uninstall, this module version was ACTIVE on this kernel.


nvidia_331.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.13.0-34-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


depmod....


DKMS: uninstall completed.
dkms: removing: virtualbox 4.3.10 (3.13.0-34-generic) (x86_64)


-------- Uninstall Beginning --------
Module:  virtualbox
Version: 4.3.10
Kernel:  3.13.0-34-generic (x86_64)
-------------------------------------


Status: Before uninstall, this module version was ACTIVE on this kernel.


vboxdrv.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.13.0-34-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.




vboxnetadp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.13.0-34-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.




vboxnetflt.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.13.0-34-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.




vboxpci.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.13.0-34-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


depmod....


DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-34-generic /boot/vmlinuz-3.13.0-34-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-34-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-34-generic /boot/vmlinuz-3.13.0-34-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-39-generic
Found initrd image: /boot/initrd.img-3.13.0-39-generic
Found linux image: /boot/vmlinuz-3.13.0-37-generic
Found initrd image: /boot/initrd.img-3.13.0-37-generic
Found linux image: /boot/vmlinuz-3.13.0-36-generic
Found linux image: /boot/vmlinuz-3.13.0-35-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
Found Windows 7 (loader) on /dev/sdb1
done
Purging configuration files for linux-image-3.13.0-34-generic (3.13.0-34.60) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-34-generic /boot/vmlinuz-3.13.0-34-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-34-generic /boot/vmlinuz-3.13.0-34-generic
Removing linux-image-3.13.0-35-generic (3.13.0-35.62) ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.13.0-35-generic /boot/vmlinuz-3.13.0-35-generic
dkms: removing: bbswitch 0.7 (3.13.0-35-generic) (x86_64)


-------- Uninstall Beginning --------
Module:  bbswitch
Version: 0.7
Kernel:  3.13.0-35-generic (x86_64)
-------------------------------------


Status: Before uninstall, this module version was ACTIVE on this kernel.


bbswitch.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.13.0-35-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


depmod....


DKMS: uninstall completed.
dkms: removing: nvidia-331 331.38 (3.13.0-35-generic) (x86_64)


-------- Uninstall Beginning --------
Module:  nvidia-331
Version: 331.38
Kernel:  3.13.0-35-generic (x86_64)
-------------------------------------


Status: Before uninstall, this module version was ACTIVE on this kernel.


nvidia_331.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.13.0-35-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


depmod....


DKMS: uninstall completed.
dkms: removing: virtualbox 4.3.10 (3.13.0-35-generic) (x86_64)


-------- Uninstall Beginning --------
Module:  virtualbox
Version: 4.3.10
Kernel:  3.13.0-35-generic (x86_64)
-------------------------------------


Status: Before uninstall, this module version was ACTIVE on this kernel.


vboxdrv.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.13.0-35-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.




vboxnetadp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.13.0-35-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.




vboxnetflt.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.13.0-35-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.




vboxpci.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.13.0-35-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


depmod....


DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-35-generic /boot/vmlinuz-3.13.0-35-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-35-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-35-generic /boot/vmlinuz-3.13.0-35-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-39-generic
Found initrd image: /boot/initrd.img-3.13.0-39-generic
Found linux image: /boot/vmlinuz-3.13.0-37-generic
Found initrd image: /boot/initrd.img-3.13.0-37-generic
Found linux image: /boot/vmlinuz-3.13.0-36-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
Found Windows 7 (loader) on /dev/sdb1
done
Purging configuration files for linux-image-3.13.0-35-generic (3.13.0-35.62) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-35-generic /boot/vmlinuz-3.13.0-35-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-35-generic /boot/vmlinuz-3.13.0-35-generic
Removing linux-image-3.13.0-36-generic (3.13.0-36.63) ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.13.0-36-generic /boot/vmlinuz-3.13.0-36-generic
dkms: removing: bbswitch 0.7 (3.13.0-36-generic) (x86_64)


-------- Uninstall Beginning --------
Module:  bbswitch
Version: 0.7
Kernel:  3.13.0-36-generic (x86_64)
-------------------------------------


Status: Before uninstall, this module version was ACTIVE on this kernel.


bbswitch.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.13.0-36-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


depmod....


DKMS: uninstall completed.
dkms: removing: nvidia-331 331.38 (3.13.0-36-generic) (x86_64)


-------- Uninstall Beginning --------
Module:  nvidia-331
Version: 331.38
Kernel:  3.13.0-36-generic (x86_64)
-------------------------------------


Status: Before uninstall, this module version was ACTIVE on this kernel.


nvidia_331.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.13.0-36-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


depmod....


DKMS: uninstall completed.
dkms: removing: virtualbox 4.3.10 (3.13.0-36-generic) (x86_64)


-------- Uninstall Beginning --------
Module:  virtualbox
Version: 4.3.10
Kernel:  3.13.0-36-generic (x86_64)
-------------------------------------


Status: Before uninstall, this module version was ACTIVE on this kernel.


vboxdrv.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.13.0-36-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.




vboxnetadp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.13.0-36-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.




vboxnetflt.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.13.0-36-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.




vboxpci.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.13.0-36-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


depmod....


DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-36-generic /boot/vmlinuz-3.13.0-36-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-36-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-36-generic /boot/vmlinuz-3.13.0-36-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-39-generic
Found initrd image: /boot/initrd.img-3.13.0-39-generic
Found linux image: /boot/vmlinuz-3.13.0-37-generic
Found initrd image: /boot/initrd.img-3.13.0-37-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
Found Windows 7 (loader) on /dev/sdb1
done
Purging configuration files for linux-image-3.13.0-36-generic (3.13.0-36.63) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-36-generic /boot/vmlinuz-3.13.0-36-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-36-generic /boot/vmlinuz-3.13.0-36-generic
```
Btw thank you for all your help

---

### Post by matt_symes on 2014-12-06
Hi

Did you see the edit of my last post; removing the header files ?

Kind regards

---

### Post by Dedsec on 2014-12-06
Also is there any way so this does not happen again? I normally use my software manger to update and this happened should i just stick to using the terminal? The commands which i run each time i do updates and upgrades are sudo apt-get updates and sudo apt-get upgrade. In this case it was the [FONT=Ubuntu Mono, monospace][COLOR=#000000]sudo apt-get -f install. Is there any other command i should know for future reference?[/COLOR][/FONT]

---

### Post by Dedsec on 2014-12-06
> **matt_symes said:**
> Hi

Did you see the edit of my last post; removing the header files ?

Kind regards
No not until i refreshed my page if i do that after a upgrade will it damage anything?

---

### Post by matt_symes on 2014-12-06
Hi

> **Dedsec said:**
> No not until i refreshed my page if i do that after a upgrade will it damage anything?

No. It'll be fine as it's just removing headers you no longer need.

BTW: I hope you're feeling better after being sick. 

Kind regards

---

### Post by Dedsec on 2014-12-06
> **matt_symes said:**
> Hi

No. It'll be fine as it's just removing headers you no longer need.

BTW: I hope you're feeling better after being sick. 

Kind regards


Yes I am been out of work for a week and still out till Monday. Had pneumonia and cold mixed from what it felt like doctors said just pneumonia. Thank you again for all the help i really appreciate it. :D:D

---

### Post by Impavidus on 2014-12-06
> **Dedsec said:**
> Also is there any way so this does not happen again? I normally use my software manger to update and this happened should i just stick to using the terminal? The commands which i run each time i do updates and upgrades are sudo apt-get updates and sudo apt-get upgrade. In this case it was the [FONT=Ubuntu Mono][COLOR=#000000]sudo apt-get -f install. Is there any other command i should know for future reference?[/COLOR][/FONT]

```
sudo apt-get autoremove --purge
```can remove old kernels and headers.

---

