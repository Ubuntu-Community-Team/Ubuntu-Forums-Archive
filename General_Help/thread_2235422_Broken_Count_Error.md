---
title: "Broken Count Error"
date: 2014-07-21
forum: General Help
---

### Post by vik2 on 2014-07-21
Please help, I've had a look and tried some of the online advice, but I still get the red circle with white line across with the error broken count 0^. I tried to repair in software manager and get the following, 
Unpacking linux-image-extra-3.13.0-30-generic (3.13.0-30.55) over (3.13.0-30.54) ...dpkg: error processing archive /var/cache/apt/archives/linux-image-extra-3.13.0-30-generic_3.13.0-30.55_amd64.deb (--unpack):
 unable to create `/lib/modules/3.13.0-30-generic/kernel/drivers/media/common/btcx-risc.ko.dpkg-new' (while processing `./lib/modules/3.13.0-30-generic/kernel/drivers/media/common/btcx-risc.ko'): No space left on device
No apport report written because the error message indicates a disk full error
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-30-generic /boot/vmlinuz-3.13.0-30-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-30-generic /boot/vmlinuz-3.13.0-30-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-extra-3.13.0-30-generic_3.13.0-30.55_amd64.deb
Error in function: 
dpkg: dependency problems prevent configuration of linux-signed-image-3.13.0-30-generic:
 linux-signed-image-3.13.0-30-generic depends on linux-image-extra-3.13.0-30-generic (= 3.13.0-30.55); however:
  Version of linux-image-extra-3.13.0-30-generic on system is 3.13.0-30

---

### Post by plucky on 2014-07-21
> unable to create `/lib/modules/3.13.0-30-generic/kernel/drivers/media/common/btcx-risc.ko.dpkg-new' (while processing `./lib/modules/3.13.0-30-generic/kernel/drivers/media/common/btcx-risc.ko'): No space left on device
No apport report written because the error message indicates a disk full error

More than likely your /boot partition is full if you have a separate /boot partition.

Open a terminal and post output for ```
ls /boot
df -h
df -i
```

---

### Post by vik2 on 2014-07-26
Thanks, I typed the above commands and got the following below, don't get it, on disk information I have  51 GB &#8212; 38 GB free (25.6% full), /dev/sda2, Linux Filesystem why does below say Filesystem Inodes /dev/sda2 100% full? I still get broken count error with installed packages have unmet dependencies?? I have a 60g ssd, 51g for linux and 8g for saves, the other 1g is in use by the system.

Filesystem      Size  Used Avail Use% Mounted on
/dev/sda2        47G   12G   33G  26% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            3.9G  4.0K  3.9G   1% /dev
tmpfs           795M  1.2M  794M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            3.9G   15M  3.9G   1% /run/shm
none            100M   44K  100M   1% /run/user
/dev/sda1       511M  3.4M  508M   1% /boot/efi

Filesystem      Inodes   IUsed   IFree IUse% Mounted on
/dev/sda2      3112960 3111412    1548  100% /
none           1017321       2 1017319    1% /sys/fs/cgroup
udev           1014625     503 1014122    1% /dev
tmpfs          1017321     516 1016805    1% /run
none           1017321       1 1017320    1% /run/lock
none           1017321      10 1017311    1% /run/shm
none           1017321      28 1017293    1% /run/user
/dev/sda1            0       0       0     - /boot/efi

---

### Post by george63 on 2014-08-06
I have similar problems...

any ideas are welcome

root@AsH:~# apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  linux-image-3.13.0-30-generic linux-image-3.13.0-32-generic
  linux-image-extra-3.13.0-30-generic linux-image-extra-3.13.0-32-generic
The following packages will be upgraded:
  accountsservice apport base-files biosdevname bsdutils byobu grub-common
  grub-pc grub-pc-bin grub2-common ifupdown initramfs-tools
  initramfs-tools-bin language-pack-en language-pack-en-base
  language-pack-gnome-en language-pack-gnome-en-base language-selector-common
  libaccountsservice0 libblkid1 libboost-iostreams1.54.0 libcgmanager0
  libfreetype6 libmount1 libpam-systemd libsystemd-daemon0 libsystemd-login0
  libudev1 libuuid1 linux-firmware locales ltrace mount openssh-client
  openssh-server openssh-sftp-server python3-apport python3-gi
  python3-problem-report python3-software-properties resolvconf
  software-properties-common systemd-services udev upstart util-linux
  uuid-runtime
47 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0 B/31.9 MB of archives.
After this operation, 291 MB disk space will be freed.
Do you want to continue? [Y/n] y
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 88844 files and directories currently installed.)
Removing linux-image-extra-3.13.0-30-generic (3.13.0-30.55) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-30-generic /boot/vmlinuz-3.13.0-30-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-30-generic
run-parts: executing /etc/kernel/postrm.d/zz-runlilo 3.13.0-30-generic /boot/vmlinuz-3.13.0-30-generic
Warning: LBA32 addressing assumed
Fatal: raid_setup: stat("/dev/sdb")
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-30-generic /boot/vmlinuz-3.13.0-30-generic
Generating grub configuration file ...
/etc/grub.d/00_header: 312: /etc/grub.d/00_header: Bad substitution
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-extra-3.13.0-30-generic.postrm line 328.
dpkg: error processing package linux-image-extra-3.13.0-30-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-3.13.0-30-generic (3.13.0-30.55) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-30-generic /boot/vmlinuz-3.13.0-30-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-30-generic
run-parts: executing /etc/kernel/postrm.d/zz-runlilo 3.13.0-30-generic /boot/vmlinuz-3.13.0-30-generic
Warning: LBA32 addressing assumed
Fatal: raid_setup: stat("/dev/sdb")
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-30-generic /boot/vmlinuz-3.13.0-30-generic
Generating grub configuration file ...
/etc/grub.d/00_header: 312: /etc/grub.d/00_header: Bad substitution
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.13.0-30-generic.postrm line 328.
dpkg: error processing package linux-image-3.13.0-30-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-extra-3.13.0-32-generic (3.13.0-32.57) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-32-generic /boot/vmlinuz-3.13.0-32-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-32-generic
run-parts: executing /etc/kernel/postrm.d/zz-runlilo 3.13.0-32-generic /boot/vmlinuz-3.13.0-32-generic
Warning: LBA32 addressing assumed
Fatal: raid_setup: stat("/dev/sdb")
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-32-generic /boot/vmlinuz-3.13.0-32-generic
Generating grub configuration file ...
/etc/grub.d/00_header: 312: /etc/grub.d/00_header: Bad substitution
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-extra-3.13.0-32-generic.postrm line 328.
dpkg: error processing package linux-image-extra-3.13.0-32-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-3.13.0-32-generic (3.13.0-32.57) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-32-generic /boot/vmlinuz-3.13.0-32-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-32-generic
run-parts: executing /etc/kernel/postrm.d/zz-runlilo 3.13.0-32-generic /boot/vmlinuz-3.13.0-32-generic
Warning: LBA32 addressing assumed
Fatal: raid_setup: stat("/dev/sdb")
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-32-generic /boot/vmlinuz-3.13.0-32-generic
Generating grub configuration file ...
/etc/grub.d/00_header: 312: /etc/grub.d/00_header: Bad substitution
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.13.0-32-generic.postrm line 328.
dpkg: error processing package linux-image-3.13.0-32-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-extra-3.13.0-30-generic
 linux-image-3.13.0-30-generic
 linux-image-extra-3.13.0-32-generic
 linux-image-3.13.0-32-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@AsH:~# ls /boot
abi-3.13.0-29-generic  coffee.bmp                debian.bmp     debianlilo.bmp  initrd.img-3.13.0-29-generic  map             memtest86+.elf            onlyblue.bmp  sid.bmp                       tuxlogo.bmp
boot.0810              config-3.13.0-29-generic  debian-de.bmp  grub            inside.bmp                    memtest86+.bin  memtest86+_multiboot.bin  sarge.bmp     System.map-3.13.0-29-generic  vmlinuz-3.13.0-29-generic
root@AsH:~# df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       226G  1.5G  213G   1% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            2.0G  4.0K  2.0G   1% /dev
tmpfs           400M  528K  400M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G     0  2.0G   0% /run/shm
none            100M     0  100M   0% /run/user
root@AsH:~# df -i
Filesystem       Inodes IUsed    IFree IUse% Mounted on
/dev/sda1      15007744 96737 14911007    1% /
none             213745     2   213743    1% /sys/fs/cgroup
udev             208937   462   208475    1% /dev
tmpfs            213745   394   213351    1% /run
none             213745     1   213744    1% /run/lock
none             213745     1   213744    1% /run/shm
none             213745     3   213742    1% /run/user
root@AsH:~#

---

