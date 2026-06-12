---
title: "packages' upgrade process failed - not enough space on `/' partition."
date: 2013-11-11
forum: General Help
---

### Post by mafeuser on 2013-11-11
Hi

During apt-get upgrade on my ubuntu 12.04 i386 box there was not enough space to fulfill the upgrade and it failed on linux kernel upgrade (to 3.2.0-56).

Then I cleaned my / partition (I do not have /boot partition), to get 1.4GB on /.

But installing linux-image-generic-pae linux-headers-generic-pae failed:
ubuntu.12.04:/usr/src$ sudo apt-get install linux-image-generic-pae linux-headers-generic-pae
.....
 unable to create `/usr/src/linux-headers-3.2.0-56/include/linux/dma-attrs.h.dpkg-new' (while processing `./usr/src/linux-headers-3.2.0-56/include/linux/dma-attrs.h'): No space left on device
.....

I searched through simillar threads, but those cases not enough space on /boot partition was the case. I do not have /boot partition. /boot is directory within /.

I'm stuck

Below is detailed view of commands I performed.






================= PARTITION STATUS:
ubuntu.12.04:~$ df -h
Filesystem                              Size  Used Avail Use% Mounted on
/dev/mapper/speed_machine-linux2         12G  9.9G  1.4G  88% /
udev                                    1.8G   12K  1.8G   1% /dev
tmpfs                                   706M  952K  705M   1% /run
none                                    5.0M     0  5.0M   0% /run/lock
none                                    1.8G  200K  1.8G   1% /run/shm
/dev/mapper/speed_machine-tmp--wibrys   1.9G   35M  1.8G   2% /tmp
/dev/mapper/speed_machine-home--wibrys   14G  8.1G  5.7G  59% /home

============== CURRENT RUNNING KERNEL IS:
ubuntu.12.04:~$ uname -a
Linux wibrys 3.2.0-54-generic-pae #82-Ubuntu SMP Tue Sep 10 20:29:22 UTC 2013 i686 i686 i386 GNU/Linux


ubuntu.12.04:/usr/src$ sudo dpkg --purge linux-headers-generic-pae linux-image-3.2.0-56-generic-pae linux-image-generic-pae
(Reading database ... 723622 files and directories currently installed.)
Removing linux-headers-generic-pae ...
Removing linux-image-3.2.0-56-generic-pae ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-56-generic-pae /boot/vmlinuz-3.2.0-56-generic-pae
update-initramfs: Deleting /boot/initrd.img-3.2.0-56-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-56-generic-pae /boot/vmlinuz-3.2.0-56-generic-pae
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-54-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-54-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-53-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-53-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda2
Found Ubuntu 12.04.1 LTS (12.04) on /dev/sdc1
Found Ubuntu 12.10 (12.10) on /dev/mapper/speed_machine-linux1
done
Purging configuration files for linux-image-3.2.0-56-generic-pae ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-56-generic-pae /boot/vmlinuz-3.2.0-56-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-56-generic-pae /boot/vmlinuz-3.2.0-56-generic-pae
Removing linux-image-generic-pae ...

=========== THEN INSTALLED NEWEST (3.2.0-56) KERNEL AGAIN: 
ubuntu.12.04:/usr/src$ sudo apt-get install linux-image-generic-pae linux-headers-generic-pae
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  linux-headers-3.2.0-56 linux-headers-3.2.0-56-generic-pae linux-image-3.2.0-56-generic-pae
Suggested packages:
  fdutils linux-doc-3.2.0 linux-source-3.2.0 linux-tools
The following NEW packages will be installed:
  linux-headers-3.2.0-56 linux-headers-3.2.0-56-generic-pae linux-headers-generic-pae linux-image-3.2.0-56-generic-pae linux-image-generic-pae
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/51.0 MB of archives.
After this operation, 181 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously unselected package linux-image-3.2.0-56-generic-pae.
(Reading database ... 719235 files and directories currently installed.)
Unpacking linux-image-3.2.0-56-generic-pae (from .../linux-image-3.2.0-56-generic-pae_3.2.0-56.86_i386.deb) ...
Done.
Unpacking linux-headers-3.2.0-56 (from .../linux-headers-3.2.0-56_3.2.0-56.86_all.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-56_3.2.0-56.86_all.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.2.0-56/include/linux/dma-attrs.h.dpkg-new' (while processing `./usr/src/linux-headers-3.2.0-56/include/linux/dma-attrs.h'): No space left on device
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking linux-headers-3.2.0-56-generic-pae (from .../linux-headers-3.2.0-56-generic-pae_3.2.0-56.86_i386.deb) ...
Selecting previously unselected package linux-headers-generic-pae.
Unpacking linux-headers-generic-pae (from .../linux-headers-generic-pae_3.2.0.56.66_i386.deb) ...
Selecting previously unselected package linux-image-generic-pae.
Unpacking linux-image-generic-pae (from .../linux-image-generic-pae_3.2.0.56.66_i386.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-3.2.0-56_3.2.0-56.86_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


======= watch -n 1 df -h displayed free space on / above 1GB, so not enough free space should not be the problem.
======= BUT, INSTALLING linux-image-generic-pae, WITHOUT linux-headers-generic-pae ALMOST DOES THE JOB (IE. DKMS PROBLEM).
ubuntu.12.04:/usr/src$ sudo apt-get install linux-image-generic-pae 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  linux-image-3.2.0-56-generic-pae
Suggested packages:
  fdutils linux-doc-3.2.0 linux-source-3.2.0 linux-tools
The following NEW packages will be installed:
  linux-image-3.2.0-56-generic-pae linux-image-generic-pae
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/38.4 MB of archives.
After this operation, 114 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously unselected package linux-image-3.2.0-56-generic-pae.
(Reading database ... 717487 files and directories currently installed.)
Unpacking linux-image-3.2.0-56-generic-pae (from .../linux-image-3.2.0-56-generic-pae_3.2.0-56.86_i386.deb) ...
Done.
Selecting previously unselected package linux-image-generic-pae.
Unpacking linux-image-generic-pae (from .../linux-image-generic-pae_3.2.0.56.66_i386.deb) ...
Setting up linux-image-3.2.0-56-generic-pae (3.2.0-56.86) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.2.0-56-generic-pae /boot/vmlinuz-3.2.0-56-generic-pae
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-56-generic-pae /boot/vmlinuz-3.2.0-56-generic-pae
Error! Your kernel headers for kernel 3.2.0-56-generic-pae cannot be found.
Please install the linux-headers-3.2.0-56-generic-pae package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 3.2.0-56-generic-pae cannot be found.
Please install the linux-headers-3.2.0-56-generic-pae package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-56-generic-pae /boot/vmlinuz-3.2.0-56-generic-pae
update-initramfs: Generating /boot/initrd.img-3.2.0-56-generic-pae
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-56-generic-pae /boot/vmlinuz-3.2.0-56-generic-pae
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-56-generic-pae /boot/vmlinuz-3.2.0-56-generic-pae
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-56-generic-pae /boot/vmlinuz-3.2.0-56-generic-pae
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-56-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-56-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-54-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-54-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-53-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-53-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda2
Found Ubuntu 12.04.1 LTS (12.04) on /dev/sdc1
Found Ubuntu 12.10 (12.10) on /dev/mapper/speed_machine-linux1
done
Setting up linux-image-generic-pae (3.2.0.56.66) ...


==================== CURRENT STATE OF MY *3.2.0-56 PACKAGES IS:
ubuntu.12.04:/usr/src$ sudo dpkg --list | grep linux | grep 56
ii  linux-image-3.2.0-56-generic-pae              3.2.0-56.86                                          Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-generic-pae                       3.2.0.56.66                                          Generic Linux kernel image
ii  linux-libc-dev

---

### Post by jeanjd63 on 2013-11-11
Hi

Can you give the return of commands :
**df  -i**
and 
**dpkg  -l  |  grep -Ei "linux-headers|linux-image"**

@+

---

### Post by mafeuser on 2013-11-11
Hi Jeand64

ubuntu.12.04$ df -i
/dev/mapper/speed_machine-linux2       786432 772411  14021   99% /
udev                                   209804    607 209197    1% /dev
tmpfs                                  214795    551 214244    1% /run
none                                   214795      4 214791    1% /run/lock
none                                   214795      7 214788    1% /run/shm
/dev/mapper/speed_machine-tmp--wibrys  121920     41 121879    1% /tmp
/dev/mapper/speed_machine-home--wibrys 915712  55227 860485    7% /home

ubuntu.12.04 $ dpkg -l | grep -Ei "linux-headers|linux-image"
ii  linux-headers-3.2.0-23                        3.2.0-23.36                                          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-23-generic-pae            3.2.0-23.36                                          Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-24                        3.2.0-24.39                                          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-24-generic-pae            3.2.0-24.39                                          Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-25                        3.2.0-25.40                                          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-25-generic-pae            3.2.0-25.40                                          Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-26                        3.2.0-26.41                                          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-26-generic-pae            3.2.0-26.41                                          Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-27                        3.2.0-27.43                                          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-27-generic-pae            3.2.0-27.43                                          Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-29                        3.2.0-29.46                                          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-29-generic-pae            3.2.0-29.46                                          Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-30                        3.2.0-30.48                                          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-30-generic-pae            3.2.0-30.48                                          Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-31                        3.2.0-31.50                                          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-31-generic-pae            3.2.0-31.50                                          Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-32                        3.2.0-32.51                                          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-32-generic-pae            3.2.0-32.51                                          Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-36                        3.2.0-36.57                                          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-36-generic-pae            3.2.0-36.57                                          Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-37                        3.2.0-37.58                                          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-37-generic-pae            3.2.0-37.58                                          Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-38                        3.2.0-38.61                                          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-38-generic-pae            3.2.0-38.61                                          Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-39                        3.2.0-39.62                                          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-39-generic-pae            3.2.0-39.62                                          Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-40                        3.2.0-40.64                                          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-40-generic-pae            3.2.0-40.64                                          Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-41                        3.2.0-41.66                                          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-41-generic-pae            3.2.0-41.66                                          Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-44                        3.2.0-44.69                                          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-44-generic-pae            3.2.0-44.69                                          Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-48                        3.2.0-48.74                                          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-48-generic-pae            3.2.0-48.74                                          Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-49                        3.2.0-49.75                                          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-49-generic-pae            3.2.0-49.75                                          Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-51                        3.2.0-51.77                                          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-51-generic-pae            3.2.0-51.77                                          Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-52                        3.2.0-52.78                                          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-52-generic-pae            3.2.0-52.78                                          Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-53                        3.2.0-53.81                                          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-53-generic-pae            3.2.0-53.81                                          Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-54                        3.2.0-54.82                                          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-54-generic-pae            3.2.0-54.82                                          Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-53-generic-pae              3.2.0-53.81                                          Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-54-generic-pae              3.2.0-54.82                                          Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-56-generic-pae              3.2.0-56.86                                          Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-generic-pae                       3.2.0.56.66                                          Generic Linux kernel image

best regards

---

### Post by ian-weisser on 2013-11-11
The df shows your / at 99%.
Looks like you can delete about 20 header packages. That will free up quite a bit of space.

---

### Post by mafeuser on 2013-11-11
did the job!:)

Thank YOu for neat idea

best regards

---

### Post by jeanjd63 on 2013-11-13
Hello
If its'nt done you can suppress old headers :
**sudo  apt-get  purge  "[COLOR=#000000]linux-headers-3.2.0-2 *"           [/COLOR]**[COLOR=#000000]attention the space between 2 and * is very important
[/COLOR][B]sudo  apt-get  purge  "[COLOR=#000000]linux-headers-3.2.0-3 *" 
[/COLOR][/B][B]sudo  apt-get  purge  "[COLOR=#000000]linux-headers-3.2.0-4 *" 
[/COLOR][/B][COLOR=#000000]
After this you can vérifies with a :
[B]df  -i
[/B]
Bye

[/COLOR]

---

### Post by rsena on 2013-12-26
I am having the same problem but I haven't had any success - I've included the following:
ras@noc1:~$ df -i
df: `/var/lib/lightdm/.gvfs': Permission denied
Filesystem      Inodes  IUsed   IFree IUse% Mounted on
/dev/sda1       512064 130939  381125   26% /
udev            125564    518  125046    1% /dev
tmpfs           128111    456  127655    1% /run
none            128111      4  128107    1% /run/lock
none            128111      4  128107    1% /run/shm
/dev/sda8      1417056  21766 1395290    2% /home
/dev/sda6       512064 326410  185654   64% /usr
/dev/sda7       455168  16109  439059    4% /var


[sudo] password for ras:
ii  linux-firmware                                1.79.6                                     Firmware for Linux kernel drivers
iU  linux-generic                                 3.2.0.53.63                                Complete Generic Linux kernel
ii  linux-headers-3.2.0-31                        3.2.0-31.50                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-31-generic                3.2.0-31.50                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-31-generic-pae            3.2.0-31.50                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-38                        3.2.0-38.61                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-39                        3.2.0-39.62                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-39-generic                3.2.0-39.62                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-39-generic-pae            3.2.0-39.62                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-40                        3.2.0-40.64                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-40-generic                3.2.0-40.64                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-40-generic-pae            3.2.0-40.64                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-41                        3.2.0-41.66                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-41-generic                3.2.0-41.66                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-41-generic-pae            3.2.0-41.66                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-43                        3.2.0-43.68                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-44                        3.2.0-44.69                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-44-generic                3.2.0-44.69                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-44-generic-pae            3.2.0-44.69                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-45                        3.2.0-45.70                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-45-generic                3.2.0-45.70                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-45-generic-pae            3.2.0-45.70                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-48                        3.2.0-48.74                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-48-generic-pae            3.2.0-48.74                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-49                        3.2.0-49.75                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-49-generic                3.2.0-49.75                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-51                        3.2.0-51.77                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-51-generic                3.2.0-51.77                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-51-generic-pae            3.2.0-51.77                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-52                        3.2.0-52.78                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-52-generic-pae            3.2.0-52.78                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-55                        3.2.0-55.85                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-55-generic                3.2.0-55.85                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-55-generic-pae            3.2.0-55.85                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-56                        3.2.0-56.86                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-56-generic                3.2.0-56.86                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-56-generic-pae            3.2.0-56.86                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-57                        3.2.0-57.87                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-57-generic                3.2.0-57.87                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-57-generic-pae            3.2.0-57.87                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-58                        3.2.0-58.88                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-58-generic                3.2.0-58.88                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-58-generic-pae            3.2.0-58.88                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
iU  linux-headers-generic                         3.2.0.53.63                                Generic Linux kernel headers
iU  linux-headers-generic-pae                     3.2.0.53.63                                Generic Linux kernel headers
rc  linux-image-2.6.31-14-generic                 2.6.31-14.48                               Linux kernel image for version 2.6.31 on x86/x86_64
rc  linux-image-2.6.31-19-generic                 2.6.31-19.56                               Linux kernel image for version 2.6.31 on x86/x86_64
rc  linux-image-2.6.31-21-generic                 2.6.31-21.59                               Linux kernel image for version 2.6.31 on x86/x86_64
rc  linux-image-2.6.32-22-generic                 2.6.32-22.36                               Linux kernel image for version 2.6.32 on x86/x86_64
rc  linux-image-2.6.32-23-generic                 2.6.32-23.37                               Linux kernel image for version 2.6.32 on x86/x86_64
rc  linux-image-2.6.32-26-generic                 2.6.32-26.48                               Linux kernel image for version 2.6.32 on x86/x86_64
rc  linux-image-2.6.32-27-generic                 2.6.32-27.49                               Linux kernel image for version 2.6.32 on x86/x86_64
rc  linux-image-2.6.32-28-generic                 2.6.32-28.55                               Linux kernel image for version 2.6.32 on x86/x86_64
rc  linux-image-2.6.32-30-generic                 2.6.32-30.59                               Linux kernel image for version 2.6.32 on x86/x86_64
rc  linux-image-2.6.32-31-generic                 2.6.32-31.61                               Linux kernel image for version 2.6.32 on x86/x86_64
rc  linux-image-2.6.32-32-generic                 2.6.32-32.62                               Linux kernel image for version 2.6.32 on x86/x86_64
rc  linux-image-2.6.32-33-generic                 2.6.32-33.72                               Linux kernel image for version 2.6.32 on x86/x86_64
ii  linux-image-3.2.0-26-generic                  3.2.0-26.41                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-27-generic                  3.2.0-27.43                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-31-generic                  3.2.0-31.50                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-32-generic                  3.2.0-32.51                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-34-generic                  3.2.0-34.53                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-36-generic                  3.2.0-36.57                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-37-generic                  3.2.0-37.58                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-38-generic                  3.2.0-38.61                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-39-generic                  3.2.0-39.62                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-41-generic                  3.2.0-41.66                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-43-generic                  3.2.0-43.68                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-44-generic                  3.2.0-44.69                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-48-generic                  3.2.0-48.74                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-52-generic                  3.2.0-52.78                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-53-generic                  3.2.0-53.81                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-54-generic                  3.2.0-54.82                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-55-generic                  3.2.0-55.85                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-56-generic                  3.2.0-56.86                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-57-generic                  3.2.0-57.87                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-58-generic                  3.2.0-58.88                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-generic                           3.2.0.58.69                                Generic Linux kernel image
ii  linux-libc-dev                                3.2.0-53.81                                Linux Kernel Headers for development
ii  linux-sound-base                              1.0.25+dfsg-0ubuntu1.1                     base package for ALSA and OSS sound systems
ii  syslinux-common                               2:4.05+dfsg-2                              collection of boot loaders (common files)
ii  syslinux-legacy                               2:3.63+dfsg-2ubuntu5                       Bootloader for Linux/i386 using MS-DOS floppies

---

### Post by mörgæs on 2013-12-26
How does it work with

```
sudo apt-get clean
audo apt-get autoremove

```
?

---

### Post by rsena on 2013-12-27
ras@noc1:~$ sudo apt-get clean
ras@noc1:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-generic : Depends: linux-image-generic (= 3.2.0.53.63) but 3.2.0.58.69 is installed
 linux-headers-generic : Depends: linux-headers-3.2.0-53-generic but it is not installed
 linux-headers-generic-pae : Depends: linux-headers-3.2.0-53-generic-pae but it is not installed
E: Unmet dependencies. Try using -f.

It told me to use the -f flag:

ras@noc1:~$ sudo apt-get -f autoremove
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-generic linux-headers-generic linux-headers-generic-pae
The following packages will be REMOVED:
  firefox-globalmenu gir1.2-ubuntuoneui-3.0 libubuntuoneui-3.0-1 linux-headers-3.2.0-39 linux-headers-3.2.0-39-generic linux-headers-3.2.0-39-generic-pae linux-headers-3.2.0-40 linux-headers-3.2.0-40-generic
  linux-headers-3.2.0-40-generic-pae linux-headers-3.2.0-41 linux-headers-3.2.0-41-generic linux-headers-3.2.0-41-generic-pae linux-headers-3.2.0-43 linux-headers-3.2.0-44 linux-headers-3.2.0-44-generic
  linux-headers-3.2.0-44-generic-pae linux-headers-3.2.0-45 linux-headers-3.2.0-45-generic linux-headers-3.2.0-45-generic-pae linux-headers-3.2.0-48 linux-headers-3.2.0-48-generic-pae linux-headers-3.2.0-49
  linux-headers-3.2.0-49-generic linux-headers-3.2.0-51 linux-headers-3.2.0-51-generic linux-headers-3.2.0-51-generic-pae
The following packages will be upgraded:
  linux-generic linux-headers-generic linux-headers-generic-pae
3 upgraded, 0 newly installed, 26 to remove and 289 not upgraded.
3 not fully installed or removed.
Need to get 6,440 B of archives.
After this operation, 665 MB disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-proposed/main linux-generic i386 3.2.0.58.69 [1,716 B]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-proposed/main linux-headers-generic i386 3.2.0.58.69 [2,360 B]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-proposed/main linux-headers-generic-pae i386 3.2.0.58.69 [2,364 B]
Fetched 6,440 B in 0s (31.2 kB/s)
(Reading database ... 695302 files and directories currently installed.)
Removing firefox-globalmenu ...
Removing gir1.2-ubuntuoneui-3.0 ...
Removing libubuntuoneui-3.0-1 ...
Removing linux-headers-3.2.0-39-generic-pae ...
Removing linux-headers-3.2.0-39-generic ...
Removing linux-headers-3.2.0-39 ...
Removing linux-headers-3.2.0-40-generic-pae ...
dpkg: warning: while removing linux-headers-3.2.0-40-generic-pae, directory '/lib/modules/3.2.0-40-generic-pae' not empty so not removed.
Removing linux-headers-3.2.0-40-generic ...
dpkg: warning: while removing linux-headers-3.2.0-40-generic, directory '/lib/modules/3.2.0-40-generic' not empty so not removed.
Removing linux-headers-3.2.0-40 ...
Removing linux-headers-3.2.0-41-generic-pae ...
dpkg: warning: while removing linux-headers-3.2.0-41-generic-pae, directory '/lib/modules/3.2.0-41-generic-pae' not empty so not removed.
Removing linux-headers-3.2.0-41-generic ...
Removing linux-headers-3.2.0-41 ...
Removing linux-headers-3.2.0-43 ...
Removing linux-headers-3.2.0-44-generic-pae ...
dpkg: warning: while removing linux-headers-3.2.0-44-generic-pae, directory '/lib/modules/3.2.0-44-generic-pae' not empty so not removed.
Removing linux-headers-3.2.0-44-generic ...
Removing linux-headers-3.2.0-44 ...
Removing linux-headers-3.2.0-45-generic-pae ...
dpkg: warning: while removing linux-headers-3.2.0-45-generic-pae, directory '/lib/modules/3.2.0-45-generic-pae' not empty so not removed.
Removing linux-headers-3.2.0-45-generic ...
dpkg: warning: while removing linux-headers-3.2.0-45-generic, directory '/lib/modules/3.2.0-45-generic' not empty so not removed.
Removing linux-headers-3.2.0-45 ...
Removing linux-headers-3.2.0-48-generic-pae ...
dpkg: warning: while removing linux-headers-3.2.0-48-generic-pae, directory '/lib/modules/3.2.0-48-generic-pae' not empty so not removed.
Removing linux-headers-3.2.0-48 ...
Removing linux-headers-3.2.0-49-generic ...
dpkg: warning: while removing linux-headers-3.2.0-49-generic, directory '/lib/modules/3.2.0-49-generic' not empty so not removed.
Removing linux-headers-3.2.0-49 ...
Removing linux-headers-3.2.0-51-generic-pae ...
dpkg: warning: while removing linux-headers-3.2.0-51-generic-pae, directory '/lib/modules/3.2.0-51-generic-pae' not empty so not removed.
Removing linux-headers-3.2.0-51-generic ...
dpkg: warning: while removing linux-headers-3.2.0-51-generic, directory '/lib/modules/3.2.0-51-generic' not empty so not removed.
Removing linux-headers-3.2.0-51 ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-3.2.0-53-generic; however:
  Package linux-headers-3.2.0-53-generic is not installed.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.2.0.53.63); however:
  Version of linux-image-generic on system is 3.2.0.58.69.
 linux-generic depends on linux-headers-generic (= 3.2.0.53.63); however:
  Package linux-headers-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-headers-generic-pae:
 linux-headers-generic-pae depends on linux-headers-3.2.0-53-generic-pae; however:
  Package linux-headers-3.2.0-53-generic-pae is not installed.
dpkg: error processing linux-headers-generic-pae (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-headers-generic
 linux-generic
 linux-headers-generic-pae
E: Sub-process /usr/bin/dpkg returned an error code (1)
ras@noc1:~$

---

### Post by mörgæs on 2013-12-27
> **rsena said:**
> 
You might want to run 'apt-get -f install' to correct these.


How did that work? 

If you don't get success within a few attempts I would suggest a fresh install. You have a system which has been upgraded (at least) from 10.04, and 289 packages need update. It's a shaky foundation.

---

### Post by rsena on 2013-12-28
didn't work - I'm in a loop here - I guess I could whack it in try again - it has been brought up from 10.04 so I guess doing a fresh 13.10 might be best...

---

### Post by rsena on 2013-12-30
Before I slash and burn the box - any other suggestions?

---

### Post by ian-weisser on 2013-12-30
Looks like you solved the original out-of-space problem. Now you just have a rather minor dependency issue to resolve.

Reinstall the metapackages *linux-generic*,  *linux-image-generic* and *linux-headers-generic*
They seem to be stuck on an old version. That old version is not in the repositories and cannot be installed.

> ```
ldconfig deferred processing now taking place
dpkg: dependency problems prevent configuration of linux-headers-generic:
 [COLOR=#ff0000]linux-headers-generic depends on linux-headers-3.2.0-53-generic; however:
  Package linux-headers-3.2.0-53-generic is not installed. [/COLOR]        ### And it won't be - the current version is 3.2.0-58-generic
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of linux-generic:
 [COLOR=#ff0000]linux-generic depends on linux-image-generic (= 3.2.0.53.63); however:
  Version of linux-image-generic on system is 3.2.0.58.69.[/COLOR]        ### Newer version already installed. System looking for older
 linux-generic depends on linux-headers-generic (= 3.2.0.53.63); however:
  Package linux-headers-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
dpkg:  dependency problems prevent configuration of linux-headers-generic-pae:
 [COLOR=#ff0000]linux-headers-generic-pae depends on linux-headers-3.2.0-53-generic-pae; however:
  Package linux-headers-3.2.0-53-generic-pae is not installed.[/COLOR]       ### System depends on older version, no longer in repository
dpkg: error processing linux-headers-generic-pae (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is re
```

---

### Post by rsena on 2013-12-30
OK I didn't have a space problem - I jumped the thread - I'd love to take your suggestion but I need a full swing with the clue-by-four - cuz I'm at a loss to clean up the dependencies - I rely on this box - and that's part of the problem it's been a bit of a set and forget and I don't have a lot of time to rebuild it ATM. If there is a way to get it back to limping along I'd be ecstatic...

---

### Post by ian-weisser on 2013-12-30
Er, don't jump threads. It confuses us. And then you may get inappropriate advice.

What happened when you reinstalled those three packages I suggested?

---

### Post by rsena on 2013-12-31
ras@noc1:~$ sudo apt-get install --reinstall linux-headers-generic
[sudo] password for ras:
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-generic : Depends: linux-image-generic (= 3.2.0.53.63) but 3.2.0.58.69 is to be installed
                 Depends: linux-headers-generic (= 3.2.0.53.63) but 3.2.0.58.69 is to be installed
 linux-headers-generic-pae : Depends: linux-headers-3.2.0-53-generic-pae but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

ras@noc1:~$ sudo apt-get install --reinstall linux-generic
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-generic : Depends: linux-headers-generic (= 3.2.0.58.69) but 3.2.0.53.63 is to be installed
 linux-headers-generic : Depends: linux-headers-3.2.0-53-generic but it is not going to be installed
 linux-headers-generic-pae : Depends: linux-headers-3.2.0-53-generic-pae but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

ras@noc1:~$ sudo apt-get install --reinstall  linux-headers-generic-pae
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-generic : Depends: linux-image-generic (= 3.2.0.53.63) but 3.2.0.58.69 is to be installed
 linux-headers-generic : Depends: linux-headers-3.2.0-53-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

### Post by ian-weisser on 2013-12-31
Did you notice how the error message changed?
Read the error message, and follow the chain of dependencies.

> ```
ras@noc1:~$ sudo apt-get install --reinstall  linux-headers-generic-pae
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 [COLOR=#ff0000]**linux-generic** : Depends: **linux-image-generic** (= 3.2.0.53.63) but 3.2.0.58.69 is to be installed
 **linux-headers-generic** : Depends: linux-headers-3.2.0-53-generic but it is not going to be installed[/COLOR]
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

Generally, work from the bottom up. Reinstalling a package only works if it's dependencies are satisfied.
Reinstalling linux-headers-generic won't work until *after* you reinstall linux-headers-generic-pae.
Reinstalling linux-generic won't work until *after* you reinstall linux-image-generic.

So next you try reinstalling linux-headers-generic-pae, linux-headers-generic, linux-image-generic, and linux-generic...in the right order. If you get the order wrong, the error message will tell you the right order.

---

### Post by rsena on 2013-12-31
OK - I will try mixing it up - ya know I'm not a rocket scientist *but* since I tried them all independently wouldn't that mean I got the order right at least 1 time? At the moment I hit it with a hammer and did a force dist-upgrade to see if it can figure out the dependencies on it's own - I'm expecting it to fail but for now it appears to be running... I will try mixing the order up but like I said above - since I did them independently doesn't that rule the order out? Or is my cluelessness shining through?

---

### Post by jeanjd63 on 2013-12-31
Hello

You have to do this :
[COLOR=#000000][FONT=Arial]**sudo dpkg -P linux-headers-generic**
**sudo dpkg -P linux-headers-generic-pae**
**sudo dpkg -P linux-generic**[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Then do :
**sudo  apt-get  -f install**[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Then terminate by :[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][B]sudo  apt-get  install  linux-headers-generic
sudo  apt-get  install  linux-headers-generic-pae
sudo  apt-get  install  linux-generic[/B][/FONT][/COLOR]

---

### Post by ian-weisser on 2013-12-31
> **rsena said:**
> *but* since I tried them all independently wouldn't that mean I got the order right at least 1 time? 

Yes. That's one reason the error message changed.

> At the moment I hit it with a hammer and did a force dist-upgrade to see if it can figure out the dependencies on it's own

It *did* figure out the dependencies on it's own.
Your system is trying very hard to tell you exactly what you need to do.
It's even telling you the right order.

 > I will try mixing the order up

Well, in that case, save your data before you reinstall.

---

### Post by rsena on 2013-12-31
[[COLOR=#000000]jeanjd63[/COLOR]]("http://ubuntuforums.org/member.php?u=1879871")[COLOR=#000000]  there is no-one better than you - you are a g0d! thank you problem solved!!!!!!!!!!![/COLOR]

---

### Post by jeanjd63 on 2013-12-31
Enjoy for you.

Bye

---

