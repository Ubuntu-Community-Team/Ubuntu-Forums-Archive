---
title: "dpkg error - E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2017-11-05
forum: General Help
---

### Post by iahmedani on 2017-11-05
Hi everyone, 

I wanted to install nodejs but getting package error, so in resolution I tried ```
sudo apt-get install -f 
``` but this didn't work and gave me following error. Please help

Here is the copy of result. 

```
root@mewfppak:/var/crash# apt-get install -fReading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  linux-image-4.4.0-79-generic linux-image-4.4.0-83-generic linux-image-4.4.0-92-generic linux-image-4.4.0-93-generic linux-image-4.4.0-96-generic
  linux-image-4.4.0-98-generic
Suggested packages:
  fdutils linux-doc-4.4.0 | linux-source-4.4.0 linux-tools linux-headers-4.4.0-96-generic
The following NEW packages will be installed:
  linux-image-4.4.0-79-generic linux-image-4.4.0-83-generic linux-image-4.4.0-92-generic linux-image-4.4.0-93-generic linux-image-4.4.0-96-generic
  linux-image-4.4.0-98-generic
0 upgraded, 6 newly installed, 0 to remove and 159 not upgraded.
15 not fully installed or removed.
Need to get 0 B/132 MB of archives.
After this operation, 402 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
dpkg: warning: files list file for package 'linux-headers-4.4.0-93-generic' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'linux-headers-4.4.0-79' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'linux-headers-4.4.0-79-generic' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'linux-headers-4.4.0-93' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'linux-headers-4.4.0-83-generic' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'linux-headers-4.4.0-92' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'linux-headers-4.4.0-92-generic' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'linux-headers-4.4.0-83' missing; assuming package has no files currently installed
(Reading database ... 420847 files and directories currently installed.)
Preparing to unpack .../linux-image-4.4.0-98-generic_4.4.0-98.121_amd64.deb ...
Done.
Unpacking linux-image-4.4.0-98-generic (4.4.0-98.121) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-4.4.0-98-generic_4.4.0-98.121_amd64.deb (--unpack):
 cannot copy extracted data for './boot/abi-4.4.0-98-generic' to '/boot/abi-4.4.0-98-generic.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-98-generic /boot/vmlinuz-4.4.0-98-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-98-generic /boot/vmlinuz-4.4.0-98-generic
Preparing to unpack .../linux-image-4.4.0-79-generic_4.4.0-79.100_amd64.deb ...
Done.
Unpacking linux-image-4.4.0-79-generic (4.4.0-79.100) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-4.4.0-79-generic_4.4.0-79.100_amd64.deb (--unpack):
 cannot copy extracted data for './boot/vmlinuz-4.4.0-79-generic' to '/boot/vmlinuz-4.4.0-79-generic.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-79-generic /boot/vmlinuz-4.4.0-79-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-79-generic /boot/vmlinuz-4.4.0-79-generic
Preparing to unpack .../linux-image-4.4.0-83-generic_4.4.0-83.106_amd64.deb ...
Done.
Unpacking linux-image-4.4.0-83-generic (4.4.0-83.106) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-4.4.0-83-generic_4.4.0-83.106_amd64.deb (--unpack):
 cannot copy extracted data for './boot/vmlinuz-4.4.0-83-generic' to '/boot/vmlinuz-4.4.0-83-generic.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-83-generic /boot/vmlinuz-4.4.0-83-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-83-generic /boot/vmlinuz-4.4.0-83-generic
Preparing to unpack .../linux-image-4.4.0-92-generic_4.4.0-92.115_amd64.deb ...
Done.
Unpacking linux-image-4.4.0-92-generic (4.4.0-92.115) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-4.4.0-92-generic_4.4.0-92.115_amd64.deb (--unpack):
 cannot copy extracted data for './boot/abi-4.4.0-92-generic' to '/boot/abi-4.4.0-92-generic.dpkg-new': failed to write (No space left on device)
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-92-generic /boot/vmlinuz-4.4.0-92-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-92-generic /boot/vmlinuz-4.4.0-92-generic
Preparing to unpack .../linux-image-4.4.0-93-generic_4.4.0-93.116_amd64.deb ...
Done.
Unpacking linux-image-4.4.0-93-generic (4.4.0-93.116) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-4.4.0-93-generic_4.4.0-93.116_amd64.deb (--unpack):
 cannot copy extracted data for './boot/System.map-4.4.0-93-generic' to '/boot/System.map-4.4.0-93-generic.dpkg-new': failed to write (No space left on device)
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-93-generic /boot/vmlinuz-4.4.0-93-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-93-generic /boot/vmlinuz-4.4.0-93-generic
Preparing to unpack .../linux-image-4.4.0-96-generic_4.4.0-96.119_amd64.deb ...
Done.
Unpacking linux-image-4.4.0-96-generic (4.4.0-96.119) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-4.4.0-96-generic_4.4.0-96.119_amd64.deb (--unpack):
 cannot copy extracted data for './boot/abi-4.4.0-96-generic' to '/boot/abi-4.4.0-96-generic.dpkg-new': failed to write (No space left on device)
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-96-generic /boot/vmlinuz-4.4.0-96-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-96-generic /boot/vmlinuz-4.4.0-96-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-4.4.0-98-generic_4.4.0-98.121_amd64.deb
 /var/cache/apt/archives/linux-image-4.4.0-79-generic_4.4.0-79.100_amd64.deb
 /var/cache/apt/archives/linux-image-4.4.0-83-generic_4.4.0-83.106_amd64.deb
 /var/cache/apt/archives/linux-image-4.4.0-92-generic_4.4.0-92.115_amd64.deb
 /var/cache/apt/archives/linux-image-4.4.0-93-generic_4.4.0-93.116_amd64.deb
 /var/cache/apt/archives/linux-image-4.4.0-96-generic_4.4.0-96.119_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

---

### Post by missmansirao on 2017-11-05
Hello Iahmedan..

You can solve your concern following simple instructions mentioned in [ASKUBUNTU]("https://askubuntu.com/questions/603295/how-to-fix-dpkg-error-2").
(And also you've gone through two more links in the first answer of the above link, as they also belongs to the same concern)
Hope this helps you.

~Mansi Rao

---

### Post by deadflowr on 2017-11-06
Your disk is full so you need to clear out some space.
Probably because you're system is trying to install 6 different kernels when you only need to install one.
post back what
```
df -h
dpkg -l | grep linux | grep -E "(image|headers)" | awk '{print $1,$2}'
```
show

---

### Post by iahmedani on 2017-11-06
```
wfpadmin@mewfppak:~$ df -hFilesystem                     Size  Used Avail Use% Mounted on
udev                           1.8G     0  1.8G   0% /dev
tmpfs                          371M   39M  332M  11% /run
/dev/mapper/mewfppak--vg-root   57G   29G   26G  54% /
tmpfs                          1.9G  5.4M  1.9G   1% /dev/shm
tmpfs                          5.0M     0  5.0M   0% /run/lock
tmpfs                          1.9G     0  1.9G   0% /sys/fs/cgroup
/dev/sda1                      472M  471M     0 100% /boot
tmpfs                          371M     0  371M   0% /run/user/1000
wfpadmin@mewfppak:~$ dpkg -l | grep linux | grep -E "(image|headers)" | awk '{pr                                                                                        int $1,$2}'
ii linux-base
iU linux-generic
ii linux-headers-4.4.0-57
ii linux-headers-4.4.0-57-generic
ii linux-headers-4.4.0-59
ii linux-headers-4.4.0-59-generic
ii linux-headers-4.4.0-62
ii linux-headers-4.4.0-62-generic
ii linux-headers-4.4.0-63
ii linux-headers-4.4.0-63-generic
ii linux-headers-4.4.0-64
ii linux-headers-4.4.0-64-generic
ii linux-headers-4.4.0-66
ii linux-headers-4.4.0-66-generic
ii linux-headers-4.4.0-70
ii linux-headers-4.4.0-70-generic
ii linux-headers-4.4.0-71
ii linux-headers-4.4.0-71-generic
ii linux-headers-4.4.0-72
ii linux-headers-4.4.0-72-generic
ii linux-headers-4.4.0-75
ii linux-headers-4.4.0-75-generic
ii linux-headers-4.4.0-78
ii linux-headers-4.4.0-78-generic
ii linux-headers-4.4.0-79
ii linux-headers-4.4.0-79-generic
ii linux-headers-4.4.0-83
ii linux-headers-4.4.0-83-generic
ii linux-headers-4.4.0-92
ii linux-headers-4.4.0-92-generic
ii linux-headers-4.4.0-93
ii linux-headers-4.4.0-93-generic
ii linux-headers-4.4.0-98
ii linux-headers-4.4.0-98-generic
ii linux-headers-generic
rc linux-image-4.4.0-31-generic
rc linux-image-4.4.0-47-generic
rc linux-image-4.4.0-51-generic
rc linux-image-4.4.0-53-generic
ii linux-image-4.4.0-57-generic
ii linux-image-4.4.0-59-generic
ii linux-image-4.4.0-62-generic
ii linux-image-4.4.0-63-generic
ii linux-image-4.4.0-64-generic
ii linux-image-4.4.0-66-generic
ii linux-image-4.4.0-70-generic
ii linux-image-4.4.0-71-generic
ii linux-image-4.4.0-72-generic
iF linux-image-4.4.0-75-generic
iF linux-image-4.4.0-78-generic
rc linux-image-extra-4.4.0-31-generic
rc linux-image-extra-4.4.0-47-generic
rc linux-image-extra-4.4.0-51-generic
rc linux-image-extra-4.4.0-53-generic
ii linux-image-extra-4.4.0-57-generic
ii linux-image-extra-4.4.0-59-generic
ii linux-image-extra-4.4.0-62-generic
ii linux-image-extra-4.4.0-63-generic
ii linux-image-extra-4.4.0-64-generic
ii linux-image-extra-4.4.0-66-generic
ii linux-image-extra-4.4.0-70-generic
ii linux-image-extra-4.4.0-71-generic
iF linux-image-extra-4.4.0-72-generic
iU linux-image-extra-4.4.0-75-generic
iU linux-image-extra-4.4.0-78-generic
iU linux-image-extra-4.4.0-79-generic
iU linux-image-extra-4.4.0-83-generic
iU linux-image-extra-4.4.0-92-generic
iU linux-image-extra-4.4.0-93-generic
iU linux-image-extra-4.4.0-96-generic
iU linux-image-extra-4.4.0-98-generic
iU linux-image-generic



```

---

### Post by Impavidus on 2017-11-06
> **missmansirao said:**
> Hello Iahmedan..

You can solve your concern following simple instructions mentioned in [ASKUBUNTU]("https://askubuntu.com/questions/603295/how-to-fix-dpkg-error-2").
(And also you've gone through two more links in the first answer of the above link, as they also belongs to the same concern)
Hope this helps you.

~Mansi Rao

Welcome to the forum and I appreciate you wish to help, but I wouldn't follow those instructions. "No space left on device" is rather different (and less serious) than "Input/Output error" and the solution offered is a somewhat dirty trick that may make things worse.

@OP:
Run```
uname -r
```That will give you a version number, which is the kernel you're currently running. Then run```
sudo dpkg --purge linux-image{,-extra}-4.4.0-57-generic
```Repeat for all other version numbers of linux-image-extra-4.4.0-xx-generic as listed in above post, except the currently running kernel as shown by uname -r and version 4.4.0-98. Then try again```
sudo apt-get install -f
```

BTW, with 159 upgrades available I recommend you install some other upgrades too. It seems that because of this problem the package manager has been stuck for several months.

---

### Post by iahmedani on 2017-11-06
Many thanks @[COLOR=#DD4814][COLOR=#000000][missmansirao]("https://ubuntuforums.org/member.php?u=2081630") ,@deadflowr, and @[/COLOR][/COLOR][[COLOR=#000000]Impavidus[/COLOR]]("https://ubuntuforums.org/member.php?u=1417721")[COLOR=#000000][FONT=Ubuntubeta]  for your timely support <3[/FONT][/COLOR]

---

