---
title: "Can NOT remove four linux-images, so can't update software."
date: 2017-03-17
forum: General Help
---

### Post by crazybear on 2017-03-17
In both 14.04 and 16.04 I have the same four linux-images that the  system tells me must be removed. I have searched many answers to similar  problems and NONE of the standard fixes have worked. I don't know if  they are only partly installed [or how to find this out], if there is no  room to remove them [or exactly how to find out - as I see this as  sometimes the problem]. No only can they not be removed, but their  presence seems to block the installation of all other software updates  and causes other problems in terminal with endless confusing error  messages.

How do I systematically approach this? I tried to remove some other  unwanted linux-images [not these four], but none could be removed and  also gave error messages. in 16.04 the update manager simply doesn't  work - I think due to this problem. Synaptic works but can not solve  this, and in terminal I have been unable to solve this. 

Help would be much appreciated!

---

### Post by mikewhatever on 2017-03-17
...and what are the error messages? There isn't any in your original post. Did you forget to post them?

---

### Post by ajgreeny on 2017-03-17
Let's see the output of ```
dpkg -l | grep linux-image*
``` to see the current status of kernels installed by the package manager, followed by ```
ls /boot
``` to see all the files in your /boot folder, and finally to check if you have a separate and full /boot partition as a result of using encryption or LVM partitioning```
df -hT
```
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by crazybear on 2017-03-17
Hope this helps....

```
 sudo aptitude dist-upgrade
[sudo] password for xxxxxxxxxx: 
The following packages will be REMOVED:  
  linux-image-3.13.0-54-generic linux-image-3.13.0-57-generic linux-image-3.13.0-59-generic linux-image-3.13.0-62-generic 
  linux-image-3.13.0-63-generic linux-image-3.13.0-79-generic linux-image-3.19.0-51-generic linux-image-extra-3.13.0-57-generic 
  linux-image-extra-3.13.0-59-generic linux-image-extra-3.13.0-62-generic linux-image-extra-3.13.0-63-generic 
  linux-image-extra-3.13.0-79-generic linux-image-extra-3.19.0-51-generic 
The following packages will be upgraded:
  adobe-flash-properties-gtk adobe-flashplugin oem-audio-hda-daily-lts-xenial-dkms 
The following partially installed packages will be configured:
  grub-pc linux-generic linux-generic-lts-vivid linux-image-4.4.0-22-generic linux-image-4.4.0-64-generic linux-image-4.4.0-66-generic 
  linux-image-extra-4.4.0-22-generic linux-image-extra-4.4.0-64-generic linux-image-extra-4.4.0-66-generic linux-image-generic 
  plymouth-theme-ubuntu-gnome-logo 
3 packages upgraded, 0 newly installed, 13 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 1,223 MB will be freed.
Do you want to continue? [Y/n/?] y
E: Can't find a source to download version '3.19.0-58.64~14.04.1' of 'linux-image-3.19.0-58-generic:amd64'
E: Can't find a source to download version '3.19.0-58.64~14.04.1' of 'linux-image-3.19.0-58-generic:amd64'
E: Internal error: couldn't generate list of packages to download

:~$ dpkg -l | grep linux-image*
rc  linux-image-3.13.0-52-generic                               3.13.0-52.86                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-53-generic                               3.13.0-53.89                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rH  linux-image-3.13.0-54-generic                               3.13.0-54.91                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-55-generic                               3.13.0-55.94                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rH  linux-image-3.13.0-57-generic                               3.13.0-57.95                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-58-generic                               3.13.0-58.97                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rH  linux-image-3.13.0-59-generic                               3.13.0-59.98                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-61-generic                               3.13.0-61.100                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rH  linux-image-3.13.0-62-generic                               3.13.0-62.102                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rH  linux-image-3.13.0-63-generic                               3.13.0-63.103                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-64-generic                               3.13.0-64.104                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-65-generic                               3.13.0-65.106                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-66-generic                               3.13.0-66.108                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-67-generic                               3.13.0-67.110                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-70-generic                               3.13.0-70.113                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-72-generic                               3.13.0-72.115                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-73-generic                               3.13.0-73.116                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-74-generic                               3.13.0-74.118                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-77-generic                               3.13.0-77.121                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rH  linux-image-3.13.0-79-generic                               3.13.0-79.123                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-83-generic                               3.13.0-83.127                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-85-generic                               3.13.0-85.129                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-29-generic                               3.19.0-29.31~14.04.1                          amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-30-generic                               3.19.0-30.34~14.04.1                          amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-31-generic                               3.19.0-31.36~14.04.1                          amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-32-generic                               3.19.0-32.37~14.04.1                          amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-36-generic                               3.19.0-36.41~14.04.1                          amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-37-generic                               3.19.0-37.42~14.04.1                          amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-39-generic                               3.19.0-39.44~14.04.1                          amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-41-generic                               3.19.0-41.46~14.04.2                          amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-42-generic                               3.19.0-42.48~14.04.1                          amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-49-generic                               3.19.0-49.55~14.04.1                          amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rH  linux-image-3.19.0-51-generic                               3.19.0-51.58~14.04.1                          amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-56-generic                               3.19.0-56.62~14.04.1                          amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rH  linux-image-3.19.0-58-generic                               3.19.0-58.64~14.04.1                          amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-21-generic                                4.4.0-21.37                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
iF  linux-image-4.4.0-22-generic                                4.4.0-22.40                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
iF  linux-image-4.4.0-64-generic                                4.4.0-64.85                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
iF  linux-image-4.4.0-66-generic                                4.4.0-66.87                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-4.6.0-040600-generic                            4.6.0-040600.201605151930                     amd64        Linux kernel image for version 4.6.0 on 64 bit x86 SMP
rH  linux-image-4.6.0-040600rc3-generic                         4.6.0-040600rc3.201604120934                  amd64        Linux kernel image for version 4.6.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-52-generic                         3.13.0-52.86                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-53-generic                         3.13.0-53.89                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-54-generic                         3.13.0-54.91                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-55-generic                         3.13.0-55.94                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rH  linux-image-extra-3.13.0-57-generic                         3.13.0-57.95                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-58-generic                         3.13.0-58.97                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rH  linux-image-extra-3.13.0-59-generic                         3.13.0-59.98                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-61-generic                         3.13.0-61.100                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rH  linux-image-extra-3.13.0-62-generic                         3.13.0-62.102                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rH  linux-image-extra-3.13.0-63-generic                         3.13.0-63.103                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-64-generic                         3.13.0-64.104                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-65-generic                         3.13.0-65.106                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-66-generic                         3.13.0-66.108                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-67-generic                         3.13.0-67.110                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-70-generic                         3.13.0-70.113                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-72-generic                         3.13.0-72.115                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-73-generic                         3.13.0-73.116                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-74-generic                         3.13.0-74.118                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-77-generic                         3.13.0-77.121                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rH  linux-image-extra-3.13.0-79-generic                         3.13.0-79.123                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-83-generic                         3.13.0-83.127                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-85-generic                         3.13.0-85.129                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-29-generic                         3.19.0-29.31~14.04.1                          amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-30-generic                         3.19.0-30.34~14.04.1                          amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-31-generic                         3.19.0-31.36~14.04.1                          amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-32-generic                         3.19.0-32.37~14.04.1                          amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-36-generic                         3.19.0-36.41~14.04.1                          amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-37-generic                         3.19.0-37.42~14.04.1                          amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-39-generic                         3.19.0-39.44~14.04.1                          amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-41-generic                         3.19.0-41.46~14.04.2                          amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-42-generic                         3.19.0-42.48~14.04.1                          amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-49-generic                         3.19.0-49.55~14.04.1                          amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rH  linux-image-extra-3.19.0-51-generic                         3.19.0-51.58~14.04.1                          amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-56-generic                         3.19.0-56.62~14.04.1                          amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rH  linux-image-extra-3.19.0-58-generic                         3.19.0-58.64~14.04.1                          amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-21-generic                          4.4.0-21.37                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-extra-4.4.0-22-generic                          4.4.0-22.40                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-extra-4.4.0-64-generic                          4.4.0-64.85                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-extra-4.4.0-66-generic                          4.4.0-66.87                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-generic                                         4.4.0.66.70                                   amd64        Generic Linux kernel image

~$ ls /boot
abi-4.4.0-21-generic     config-4.4.0-22-generic  initrd.img-4.4.0-21-generic  memtest86+.elf               System.map-4.4.0-66-generic
abi-4.4.0-22-generic     config-4.4.0-64-generic  initrd.img-4.4.0-22-generic  memtest86+_multiboot.bin     vmlinuz-4.4.0-21-generic
abi-4.4.0-64-generic     config-4.4.0-66-generic  initrd.img-4.4.0-64-generic  System.map-4.4.0-21-generic  vmlinuz-4.4.0-22-generic
abi-4.4.0-66-generic     grub                     initrd.img-4.4.0-66-generic  System.map-4.4.0-22-generic  vmlinuz-4.4.0-64-generic
config-4.4.0-21-generic  grub.bak                 memtest86+.bin               System.map-4.4.0-64-generic  vmlinuz-4.4.0-66-generic
peter-and-crazybear@peterandcrazybear-GA-X58A-UD7:~$ df -hT
Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs   12G     0   12G   0% /dev
tmpfs          tmpfs     2.4G   11M  2.4G   1% /run
/dev/sdd1      ext4      899G  546G  308G  64% /
tmpfs          tmpfs      12G  396K   12G   1% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs      12G     0   12G   0% /sys/fs/cgroup
cgmfs          tmpfs     100K     0  100K   0% /run/cgmanager/fs
tmpfs          tmpfs     2.4G   12K  2.4G   1% /run/user/125
tmpfs          tmpfs     2.4G   92K  2.4G   1% /run/user/1000
/dev/sdc1      vfat       31G   18G   14G  57% /media/Survivor
```

---

### Post by crazybear on 2017-03-17
or trying to do dist-upgrade I now get...

```
:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  linux-image-3.13.0-54-generic linux-image-3.13.0-57-generic linux-image-3.13.0-59-generic linux-image-3.13.0-62-generic
  linux-image-3.13.0-63-generic linux-image-3.13.0-79-generic linux-image-3.19.0-51-generic linux-image-3.19.0-58-generic
  linux-image-4.6.0-040600-generic linux-image-4.6.0-040600rc3-generic linux-image-extra-3.13.0-57-generic linux-image-extra-3.13.0-59-generic
  linux-image-extra-3.13.0-62-generic linux-image-extra-3.13.0-63-generic linux-image-extra-3.13.0-79-generic linux-image-extra-3.19.0-51-generic
  linux-image-extra-3.19.0-58-generic
The following packages will be upgraded:
  adobe-flash-properties-gtk adobe-flashplugin oem-audio-hda-daily-lts-xenial-dkms
3 upgraded, 0 newly installed, 17 to remove and 0 not upgraded.
28 not fully installed or removed.
Need to get 269 kB/10.7 MB of archives.
After this operation, 1,865 MB disk space will be freed.
Do you want to continue? [Y/n] y
Get:1 [http://ppa.launchpad.net/ubuntu-audio-dev/alsa-daily/ubuntu](http://ppa.launchpad.net/ubuntu-audio-dev/alsa-daily/ubuntu) xenial/main amd64 oem-audio-hda-daily-lts-xenial-dkms all 0.201703170731~ubuntu16.04.1 [269 kB]
Fetched 269 kB in 0s (943 kB/s)                              
(Reading database ... 848398 files and directories currently installed.)
Removing linux-image-3.13.0-54-generic (3.13.0-54.91) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-54-generic /boot/vmlinuz-3.13.0-54-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-54-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-54-generic /boot/vmlinuz-3.13.0-54-generic
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_GFXPAYLOAD_LINUX=None'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 64
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.13.0-54-generic.postrm line 328.
dpkg: error processing package linux-image-3.13.0-54-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-extra-3.13.0-57-generic (3.13.0-57.95) ...
depmod: FATAL: could not load /boot/System.map-3.13.0-57-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-57-generic /boot/vmlinuz-3.13.0-57-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-57-generic /boot/vmlinuz-3.13.0-57-generic
Error!  The dkms.conf for this module includes a BUILD_EXCLUSIVE directive which
does not match this kernel/arch.  This indicates that it should not be built.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-57-generic /boot/vmlinuz-3.13.0-57-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-57-generic
depmod: WARNING: could not open /var/tmp/mkinitramfs_pl6Hk6/lib/modules/3.13.0-57-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_pl6Hk6/lib/modules/3.13.0-57-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-57-generic /boot/vmlinuz-3.13.0-57-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.13.0-57-generic /boot/vmlinuz-3.13.0-57-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-57-generic /boot/vmlinuz-3.13.0-57-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-57-generic /boot/vmlinuz-3.13.0-57-generic
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_GFXPAYLOAD_LINUX=None'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 64
dpkg: error processing package linux-image-extra-3.13.0-57-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-3.13.0-57-generic (3.13.0-57.95) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-57-generic /boot/vmlinuz-3.13.0-57-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-57-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-57-generic /boot/vmlinuz-3.13.0-57-generic
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_GFXPAYLOAD_LINUX=None'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 64
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.13.0-57-generic.postrm line 328.
dpkg: error processing package linux-image-3.13.0-57-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-extra-3.13.0-59-generic (3.13.0-59.98) ...
depmod: FATAL: could not load /boot/System.map-3.13.0-59-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-59-generic /boot/vmlinuz-3.13.0-59-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-59-generic /boot/vmlinuz-3.13.0-59-generic
Error!  The dkms.conf for this module includes a BUILD_EXCLUSIVE directive which
does not match this kernel/arch.  This indicates that it should not be built.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-59-generic /boot/vmlinuz-3.13.0-59-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-59-generic
depmod: WARNING: could not open /var/tmp/mkinitramfs_Ae0laI/lib/modules/3.13.0-59-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_Ae0laI/lib/modules/3.13.0-59-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-59-generic /boot/vmlinuz-3.13.0-59-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.13.0-59-generic /boot/vmlinuz-3.13.0-59-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-59-generic /boot/vmlinuz-3.13.0-59-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-59-generic /boot/vmlinuz-3.13.0-59-generic
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_GFXPAYLOAD_LINUX=None'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 64
dpkg: error processing package linux-image-extra-3.13.0-59-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-3.13.0-59-generic (3.13.0-59.98) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-59-generic /boot/vmlinuz-3.13.0-59-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-59-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-59-generic /boot/vmlinuz-3.13.0-59-generic
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_GFXPAYLOAD_LINUX=None'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 64
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.13.0-59-generic.postrm line 328.
No apport report written because MaxReports is reached already
                                                              dpkg: error processing package linux-image-3.13.0-59-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-extra-3.13.0-62-generic (3.13.0-62.102) ...
depmod: FATAL: could not load /boot/System.map-3.13.0-62-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-62-generic /boot/vmlinuz-3.13.0-62-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-62-generic /boot/vmlinuz-3.13.0-62-generic
Error!  The dkms.conf for this module includes a BUILD_EXCLUSIVE directive which
does not match this kernel/arch.  This indicates that it should not be built.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-62-generic /boot/vmlinuz-3.13.0-62-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-62-generic
depmod: WARNING: could not open /var/tmp/mkinitramfs_3ZxI2p/lib/modules/3.13.0-62-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_3ZxI2p/lib/modules/3.13.0-62-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-62-generic /boot/vmlinuz-3.13.0-62-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.13.0-62-generic /boot/vmlinuz-3.13.0-62-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-62-generic /boot/vmlinuz-3.13.0-62-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-62-generic /boot/vmlinuz-3.13.0-62-generic
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_GFXPAYLOAD_LINUX=None'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 64
No apport report written because MaxReports is reached already
                                                              dpkg: error processing package linux-image-extra-3.13.0-62-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-3.13.0-62-generic (3.13.0-62.102) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-62-generic /boot/vmlinuz-3.13.0-62-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-62-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-62-generic /boot/vmlinuz-3.13.0-62-generic
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_GFXPAYLOAD_LINUX=None'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 64
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.13.0-62-generic.postrm line 328.
dpkg: error processing package linux-image-3.13.0-62-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-extra-3.13.0-63-generic (3.13.0-63.103) ...
depmod: FATAL: could not load /boot/System.map-3.13.0-63-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-63-generic /boot/vmlinuz-3.13.0-63-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-63-generic /boot/vmlinuz-3.13.0-63-generic
Error!  The dkms.conf for this module includes a BUILD_EXCLUSIVE directive which
does not match this kernel/arch.  This indicates that it should not be built.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-63-generic /boot/vmlinuz-3.13.0-63-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-63-generic
depmod: WARNING: could not open /var/tmp/mkinitramfs_xFORos/lib/modules/3.13.0-63-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_xFORos/lib/modules/3.13.0-63-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-63-generic /boot/vmlinuz-3.13.0-63-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.13.0-63-generic /boot/vmlinuz-3.13.0-63-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-63-generic /boot/vmlinuz-3.13.0-63-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-63-generic /boot/vmlinuz-3.13.0-63-generic
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_GFXPAYLOAD_LINUX=None'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 64
dpkg: error processing package linux-image-extra-3.13.0-63-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-3.13.0-63-generic (3.13.0-63.103) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-63-generic /boot/vmlinuz-3.13.0-63-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-63-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-63-generic /boot/vmlinuz-3.13.0-63-generic
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_GFXPAYLOAD_LINUX=None'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 64
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.13.0-63-generic.postrm line 328.
dpkg: error processing package linux-image-3.13.0-63-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-extra-3.13.0-79-generic (3.13.0-79.123) ...
depmod: FATAL: could not load /boot/System.map-3.13.0-79-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-79-generic /boot/vmlinuz-3.13.0-79-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-79-generic /boot/vmlinuz-3.13.0-79-generic
Error!  The dkms.conf for this module includes a BUILD_EXCLUSIVE directive which
does not match this kernel/arch.  This indicates that it should not be built.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-79-generic /boot/vmlinuz-3.13.0-79-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-79-generic
depmod: WARNING: could not open /var/tmp/mkinitramfs_EPY8qe/lib/modules/3.13.0-79-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_EPY8qe/lib/modules/3.13.0-79-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-79-generic /boot/vmlinuz-3.13.0-79-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.13.0-79-generic /boot/vmlinuz-3.13.0-79-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-79-generic /boot/vmlinuz-3.13.0-79-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-79-generic /boot/vmlinuz-3.13.0-79-generic
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_GFXPAYLOAD_LINUX=None'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 64
No apport report written because MaxReports is reached already
                                                              dpkg: error processing package linux-image-extra-3.13.0-79-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-3.13.0-79-generic (3.13.0-79.123) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-79-generic /boot/vmlinuz-3.13.0-79-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-79-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-79-generic /boot/vmlinuz-3.13.0-79-generic
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_GFXPAYLOAD_LINUX=None'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 64
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.13.0-79-generic.postrm line 328.
No apport report written because MaxReports is reached already
                                                              dpkg: error processing package linux-image-3.13.0-79-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-extra-3.19.0-51-generic (3.19.0-51.58~14.04.1) ...
depmod: FATAL: could not load /boot/System.map-3.19.0-51-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-51-generic /boot/vmlinuz-3.19.0-51-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.19.0-51-generic /boot/vmlinuz-3.19.0-51-generic
Error!  The dkms.conf for this module includes a BUILD_EXCLUSIVE directive which
does not match this kernel/arch.  This indicates that it should not be built.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-51-generic /boot/vmlinuz-3.19.0-51-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-51-generic
depmod: WARNING: could not open /var/tmp/mkinitramfs_gQZT25/lib/modules/3.19.0-51-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_gQZT25/lib/modules/3.19.0-51-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.19.0-51-generic /boot/vmlinuz-3.19.0-51-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.19.0-51-generic /boot/vmlinuz-3.19.0-51-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.19.0-51-generic /boot/vmlinuz-3.19.0-51-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.19.0-51-generic /boot/vmlinuz-3.19.0-51-generic
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_GFXPAYLOAD_LINUX=None'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 64
dpkg: error processing package linux-image-extra-3.19.0-51-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-3.19.0-51-generic (3.19.0-51.58~14.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-51-generic /boot/vmlinuz-3.19.0-51-generic
update-initramfs: Deleting /boot/initrd.img-3.19.0-51-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-51-generic /boot/vmlinuz-3.19.0-51-generic
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_GFXPAYLOAD_LINUX=None'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 64
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.19.0-51-generic.postrm line 328.
dpkg: error processing package linux-image-3.19.0-51-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-extra-3.19.0-58-generic (3.19.0-58.64~14.04.1) ...
depmod: FATAL: could not load /boot/System.map-3.19.0-58-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-58-generic /boot/vmlinuz-3.19.0-58-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.19.0-58-generic /boot/vmlinuz-3.19.0-58-generic
Error!  The dkms.conf for this module includes a BUILD_EXCLUSIVE directive which
does not match this kernel/arch.  This indicates that it should not be built.
Error! Your kernel headers for kernel 3.19.0-58-generic cannot be found.
Please install the linux-headers-3.19.0-58-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-58-generic /boot/vmlinuz-3.19.0-58-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-58-generic
WARNING: missing /lib/modules/3.19.0-58-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/3.19.0-58-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_SPutg6/lib/modules/3.19.0-58-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_SPutg6/lib/modules/3.19.0-58-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.19.0-58-generic /boot/vmlinuz-3.19.0-58-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.19.0-58-generic /boot/vmlinuz-3.19.0-58-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.19.0-58-generic /boot/vmlinuz-3.19.0-58-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.19.0-58-generic /boot/vmlinuz-3.19.0-58-generic
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_GFXPAYLOAD_LINUX=None'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 64
dpkg: error processing package linux-image-extra-3.19.0-58-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-3.19.0-58-generic (3.19.0-58.64~14.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-58-generic /boot/vmlinuz-3.19.0-58-generic
update-initramfs: Deleting /boot/initrd.img-3.19.0-58-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-58-generic /boot/vmlinuz-3.19.0-58-generic
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_GFXPAYLOAD_LINUX=None'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 64
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.19.0-58-generic.postrm line 328.
dpkg: error processing package linux-image-3.19.0-58-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-4.6.0-040600-generic (4.6.0-040600.201605151930) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.6.0-040600-generic /boot/vmlinuz-4.6.0-040600-generic
update-initramfs: Deleting /boot/initrd.img-4.6.0-040600-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.6.0-040600-generic /boot/vmlinuz-4.6.0-040600-generic
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_GFXPAYLOAD_LINUX=None'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 64
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.6.0-040600-generic.postrm line 328.
dpkg: error processing package linux-image-4.6.0-040600-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-4.6.0-040600rc3-generic (4.6.0-040600rc3.201604120934) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.6.0-040600rc3-generic /boot/vmlinuz-4.6.0-040600rc3-generic
update-initramfs: Deleting /boot/initrd.img-4.6.0-040600rc3-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.6.0-040600rc3-generic /boot/vmlinuz-4.6.0-040600rc3-generic
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_GFXPAYLOAD_LINUX=None'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 64
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.6.0-040600rc3-generic.postrm line 328.
dpkg: error processing package linux-image-4.6.0-040600rc3-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-3.13.0-54-generic
 linux-image-extra-3.13.0-57-generic
 linux-image-3.13.0-57-generic
 linux-image-extra-3.13.0-59-generic
 linux-image-3.13.0-59-generic
 linux-image-extra-3.13.0-62-generic
 linux-image-3.13.0-62-generic
 linux-image-extra-3.13.0-63-generic
 linux-image-3.13.0-63-generic
 linux-image-extra-3.13.0-79-generic
 linux-image-3.13.0-79-generic
 linux-image-extra-3.19.0-51-generic
 linux-image-3.19.0-51-generic
 linux-image-extra-3.19.0-58-generic
 linux-image-3.19.0-58-generic
 linux-image-4.6.0-040600-generic
 linux-image-4.6.0-040600rc3-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by ajgreeny on 2017-03-17
See what happens if you run ```
sudo apt-get remove --purge --autoremove
sudo apt-get autoremove
``` which may get rid of a lot of unneeded packages and the kernel configurations that are remaining for all your 14.04 kernels, version 3.13.0-, and possibly also the 3.19.0- series; I assume you must have version upgraded from 14.04 to 16.04 with possibly some of the intermediate versions on the way.

I often use synaptic to see what packages still have configurations remaining even though the package has been removed; it is one of the many useful things that you can do with synaptic that you can't do so easily in other ways. It might be worth you trying with synaptic by highlighting the **Status** filter in the left hand pane, then choosing **Not Installed (residual config)** and finally choose to "Mark for complete removal" all listed packages.

You did not show us the output of command **df -hT** which I asked for and may explain a bit more about your problem.

---

### Post by crazybear on 2017-03-18
```
$ df -hT
Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs   12G     0   12G   0% /dev
tmpfs          tmpfs     2.4G   11M  2.4G   1% /run
/dev/sdd1      ext4      909G  546G  317G  64% /
tmpfs          tmpfs      12G  368K   12G   1% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs      12G     0   12G   0% /sys/fs/cgroup
cgmfs          tmpfs     100K     0  100K   0% /run/cgmanager/fs
tmpfs          tmpfs     2.4G   12K  2.4G   1% /run/user/125
tmpfs          tmpfs     2.4G   96K  2.4G   1% /run/user/1000
/dev/sde1      ext4      2.7T  2.1T  528G  80% /media/1st-3T-DATA-INFO
/dev/sdc1      vfat       31G   18G   14G  57% /media/SURVIVORUSB
```

I had run the autoremove options you mention above many times. Both of the two variants above give the same result: don't remove anything and give lots of error messages. Help!
I see a lot of mention of some boot area being too full of images to do anything. I know nothing about this, where it is, how to check and if this is part or all of the problem.
I also see some mention of some programs not fully installed, but don't know which they are. At some point it seemed I was told in terminal that some were some of the linux-kernels.
Sorry, the 'Not installed [residual config] suggestion makes no sense to me. I tried and don't understand your suggested instructions.

```
$ sudo apt-get remove --purge --autoremove
[sudo] password for peter-and-crazybear: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-3.13.0-54-generic linux-image-3.13.0-57-generic linux-image-3.13.0-59-generic linux-image-3.13.0-62-generic
  linux-image-3.13.0-63-generic linux-image-3.13.0-79-generic linux-image-3.19.0-51-generic linux-image-3.19.0-58-generic
  linux-image-4.6.0-040600-generic linux-image-4.6.0-040600rc3-generic linux-image-extra-3.13.0-57-generic
  linux-image-extra-3.13.0-59-generic linux-image-extra-3.13.0-62-generic linux-image-extra-3.13.0-63-generic
  linux-image-extra-3.13.0-79-generic linux-image-extra-3.19.0-51-generic linux-image-extra-3.19.0-58-generic
0 upgraded, 0 newly installed, 17 to remove and 51 not upgraded.
28 not fully installed or removed.
After this operation, 1,865 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 848399 files and directories currently installed.)
Removing linux-image-3.13.0-54-generic (3.13.0-54.91) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-54-generic /boot/vmlinuz-3.13.0-54-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-54-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-54-generic /boot/vmlinuz-3.13.0-54-generic
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_GFXPAYLOAD_LINUX=None'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 64
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.13.0-54-generic.postrm line 328.
dpkg: error processing package linux-image-3.13.0-54-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-extra-3.13.0-57-generic (3.13.0-57.95) ...
depmod: FATAL: could not load /boot/System.map-3.13.0-57-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-57-generic /boot/vmlinuz-3.13.0-57-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-57-generic /boot/vmlinuz-3.13.0-57-generic
Error!  The dkms.conf for this module includes a BUILD_EXCLUSIVE directive which
does not match this kernel/arch.  This indicates that it should not be built.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-57-generic /boot/vmlinuz-3.13.0-57-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-57-generic
depmod: WARNING: could not open /var/tmp/mkinitramfs_5cBSFB/lib/modules/3.13.0-57-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_5cBSFB/lib/modules/3.13.0-57-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-57-generic /boot/vmlinuz-3.13.0-57-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.13.0-57-generic /boot/vmlinuz-3.13.0-57-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-57-generic /boot/vmlinuz-3.13.0-57-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-57-generic /boot/vmlinuz-3.13.0-57-generic
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_GFXPAYLOAD_LINUX=None'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 64
dpkg: error processing package linux-image-extra-3.13.0-57-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-3.13.0-57-generic (3.13.0-57.95) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-57-generic /boot/vmlinuz-3.13.0-57-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-57-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-57-generic /boot/vmlinuz-3.13.0-57-generic
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_GFXPAYLOAD_LINUX=None'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 64
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.13.0-57-generic.postrm line 328.
dpkg: error processing package linux-image-3.13.0-57-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-extra-3.13.0-59-generic (3.13.0-59.98) ...
depmod: FATAL: could not load /boot/System.map-3.13.0-59-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-59-generic /boot/vmlinuz-3.13.0-59-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-59-generic /boot/vmlinuz-3.13.0-59-generic
Error!  The dkms.conf for this module includes a BUILD_EXCLUSIVE directive which
does not match this kernel/arch.  This indicates that it should not be built.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-59-generic /boot/vmlinuz-3.13.0-59-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-59-generic
depmod: WARNING: could not open /var/tmp/mkinitramfs_OExMnP/lib/modules/3.13.0-59-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_OExMnP/lib/modules/3.13.0-59-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-59-generic /boot/vmlinuz-3.13.0-59-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.13.0-59-generic /boot/vmlinuz-3.13.0-59-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-59-generic /boot/vmlinuz-3.13.0-59-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-59-generic /boot/vmlinuz-3.13.0-59-generic
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_GFXPAYLOAD_LINUX=None'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 64
dpkg: error processing package linux-image-extra-3.13.0-59-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-3.13.0-59-generic (3.13.0-59.98) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-59-generic /boot/vmlinuz-3.13.0-59-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-59-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-59-generic /boot/vmlinuz-3.13.0-59-generic
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_GFXPAYLOAD_LINUX=None'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 64
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.13.0-59-generic.postrm line 328.
dpkg: error processing package linux-image-3.13.0-59-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-extra-3.13.0-62-generic (3.13.0-62.102) ...
depmod: FATAL: could not load /boot/System.map-3.13.0-62-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-62-generic /boot/vmlinuz-3.13.0-62-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-62-generic /boot/vmlinuz-3.13.0-62-generic
Error!  The dkms.conf for this module includes a BUILD_EXCLUSIVE directive which
does not match this kernel/arch.  This indicates that it should not be built.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-62-generic /boot/vmlinuz-3.13.0-62-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-62-generic
depmod: WARNING: could not open /var/tmp/mkinitramfs_Yp3alc/lib/modules/3.13.0-62-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_Yp3alc/lib/modules/3.13.0-62-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-62-generic /boot/vmlinuz-3.13.0-62-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.13.0-62-generic /boot/vmlinuz-3.13.0-62-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-62-generic /boot/vmlinuz-3.13.0-62-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-62-generic /boot/vmlinuz-3.13.0-62-generic
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_GFXPAYLOAD_LINUX=None'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 64
dpkg: error processing package linux-image-extra-3.13.0-62-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-3.13.0-62-generic (3.13.0-62.102) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-62-generic /boot/vmlinuz-3.13.0-62-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-62-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-62-generic /boot/vmlinuz-3.13.0-62-generic
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_GFXPAYLOAD_LINUX=None'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 64
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.13.0-62-generic.postrm line 328.
No apport report written because MaxReports is reached already
                                                              dpkg: error processing package linux-image-3.13.0-62-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-extra-3.13.0-63-generic (3.13.0-63.103) ...
depmod: FATAL: could not load /boot/System.map-3.13.0-63-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-63-generic /boot/vmlinuz-3.13.0-63-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-63-generic /boot/vmlinuz-3.13.0-63-generic
Error!  The dkms.conf for this module includes a BUILD_EXCLUSIVE directive which
does not match this kernel/arch.  This indicates that it should not be built.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-63-generic /boot/vmlinuz-3.13.0-63-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-63-generic
depmod: WARNING: could not open /var/tmp/mkinitramfs_PBgmxB/lib/modules/3.13.0-63-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_PBgmxB/lib/modules/3.13.0-63-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-63-generic /boot/vmlinuz-3.13.0-63-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.13.0-63-generic /boot/vmlinuz-3.13.0-63-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-63-generic /boot/vmlinuz-3.13.0-63-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-63-generic /boot/vmlinuz-3.13.0-63-generic
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_GFXPAYLOAD_LINUX=None'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 64
No apport report written because MaxReports is reached already
                                                              dpkg: error processing package linux-image-extra-3.13.0-63-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-3.13.0-63-generic (3.13.0-63.103) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-63-generic /boot/vmlinuz-3.13.0-63-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-63-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-63-generic /boot/vmlinuz-3.13.0-63-generic
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_GFXPAYLOAD_LINUX=None'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 64
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.13.0-63-generic.postrm line 328.
No apport report written because MaxReports is reached already
                                                              dpkg: error processing package linux-image-3.13.0-63-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-extra-3.13.0-79-generic (3.13.0-79.123) ...
depmod: FATAL: could not load /boot/System.map-3.13.0-79-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-79-generic /boot/vmlinuz-3.13.0-79-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-79-generic /boot/vmlinuz-3.13.0-79-generic
Error!  The dkms.conf for this module includes a BUILD_EXCLUSIVE directive which
does not match this kernel/arch.  This indicates that it should not be built.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-79-generic /boot/vmlinuz-3.13.0-79-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-79-generic
depmod: WARNING: could not open /var/tmp/mkinitramfs_v1Gr80/lib/modules/3.13.0-79-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_v1Gr80/lib/modules/3.13.0-79-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-79-generic /boot/vmlinuz-3.13.0-79-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.13.0-79-generic /boot/vmlinuz-3.13.0-79-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-79-generic /boot/vmlinuz-3.13.0-79-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-79-generic /boot/vmlinuz-3.13.0-79-generic
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_GFXPAYLOAD_LINUX=None'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 64
dpkg: error processing package linux-image-extra-3.13.0-79-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-3.13.0-79-generic (3.13.0-79.123) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-79-generic /boot/vmlinuz-3.13.0-79-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-79-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-79-generic /boot/vmlinuz-3.13.0-79-generic
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_GFXPAYLOAD_LINUX=None'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 64
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.13.0-79-generic.postrm line 328.
No apport report written because MaxReports is reached already
                                                              dpkg: error processing package linux-image-3.13.0-79-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-extra-3.19.0-51-generic (3.19.0-51.58~14.04.1) ...
depmod: FATAL: could not load /boot/System.map-3.19.0-51-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-51-generic /boot/vmlinuz-3.19.0-51-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.19.0-51-generic /boot/vmlinuz-3.19.0-51-generic
Error!  The dkms.conf for this module includes a BUILD_EXCLUSIVE directive which
does not match this kernel/arch.  This indicates that it should not be built.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-51-generic /boot/vmlinuz-3.19.0-51-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-51-generic
depmod: WARNING: could not open /var/tmp/mkinitramfs_q2IZXd/lib/modules/3.19.0-51-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_q2IZXd/lib/modules/3.19.0-51-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.19.0-51-generic /boot/vmlinuz-3.19.0-51-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.19.0-51-generic /boot/vmlinuz-3.19.0-51-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.19.0-51-generic /boot/vmlinuz-3.19.0-51-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.19.0-51-generic /boot/vmlinuz-3.19.0-51-generic
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_GFXPAYLOAD_LINUX=None'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 64
dpkg: error processing package linux-image-extra-3.19.0-51-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-3.19.0-51-generic (3.19.0-51.58~14.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-51-generic /boot/vmlinuz-3.19.0-51-generic
update-initramfs: Deleting /boot/initrd.img-3.19.0-51-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-51-generic /boot/vmlinuz-3.19.0-51-generic
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_GFXPAYLOAD_LINUX=None'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 64
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.19.0-51-generic.postrm line 328.
dpkg: error processing package linux-image-3.19.0-51-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-extra-3.19.0-58-generic (3.19.0-58.64~14.04.1) ...
depmod: FATAL: could not load /boot/System.map-3.19.0-58-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-58-generic /boot/vmlinuz-3.19.0-58-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.19.0-58-generic /boot/vmlinuz-3.19.0-58-generic
Error!  The dkms.conf for this module includes a BUILD_EXCLUSIVE directive which
does not match this kernel/arch.  This indicates that it should not be built.
Error! Your kernel headers for kernel 3.19.0-58-generic cannot be found.
Please install the linux-headers-3.19.0-58-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-58-generic /boot/vmlinuz-3.19.0-58-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-58-generic
WARNING: missing /lib/modules/3.19.0-58-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/3.19.0-58-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_00qB3h/lib/modules/3.19.0-58-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_00qB3h/lib/modules/3.19.0-58-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.19.0-58-generic /boot/vmlinuz-3.19.0-58-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.19.0-58-generic /boot/vmlinuz-3.19.0-58-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.19.0-58-generic /boot/vmlinuz-3.19.0-58-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.19.0-58-generic /boot/vmlinuz-3.19.0-58-generic
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_GFXPAYLOAD_LINUX=None'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 64
dpkg: error processing package linux-image-extra-3.19.0-58-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-3.19.0-58-generic (3.19.0-58.64~14.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-58-generic /boot/vmlinuz-3.19.0-58-generic
update-initramfs: Deleting /boot/initrd.img-3.19.0-58-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-58-generic /boot/vmlinuz-3.19.0-58-generic
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_GFXPAYLOAD_LINUX=None'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 64
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.19.0-58-generic.postrm line 328.
dpkg: error processing package linux-image-3.19.0-58-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-4.6.0-040600-generic (4.6.0-040600.201605151930) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.6.0-040600-generic /boot/vmlinuz-4.6.0-040600-generic
update-initramfs: Deleting /boot/initrd.img-4.6.0-040600-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.6.0-040600-generic /boot/vmlinuz-4.6.0-040600-generic
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_GFXPAYLOAD_LINUX=None'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 64
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.6.0-040600-generic.postrm line 328.
dpkg: error processing package linux-image-4.6.0-040600-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-4.6.0-040600rc3-generic (4.6.0-040600rc3.201604120934) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.6.0-040600rc3-generic /boot/vmlinuz-4.6.0-040600rc3-generic
update-initramfs: Deleting /boot/initrd.img-4.6.0-040600rc3-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.6.0-040600rc3-generic /boot/vmlinuz-4.6.0-040600rc3-generic
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_GFXPAYLOAD_LINUX=None'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 64
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.6.0-040600rc3-generic.postrm line 328.
dpkg: error processing package linux-image-4.6.0-040600rc3-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-3.13.0-54-generic
 linux-image-extra-3.13.0-57-generic
 linux-image-3.13.0-57-generic
 linux-image-extra-3.13.0-59-generic
 linux-image-3.13.0-59-generic
 linux-image-extra-3.13.0-62-generic
 linux-image-3.13.0-62-generic
 linux-image-extra-3.13.0-63-generic
 linux-image-3.13.0-63-generic
 linux-image-extra-3.13.0-79-generic
 linux-image-3.13.0-79-generic
 linux-image-extra-3.19.0-51-generic
 linux-image-3.19.0-51-generic
 linux-image-extra-3.19.0-58-generic
 linux-image-3.19.0-58-generic
 linux-image-4.6.0-040600-generic
 linux-image-4.6.0-040600rc3-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

---

### Post by mus1cfreak on 2017-03-18
what shows:
cat /etc/apt/sources.list

---

### Post by ajgreeny on 2017-03-18
OK, I think we may have to get down and dirty with the package management in your system.
First let's check what kernel you are running at the present time by using command **uname -a** which I hope will show **Linux *<Hostname>* 4.4.0-21-generic** or similar.

We may then have to try using dpkg to remove old kernels not in use.
You have many kernels that have been removed but still retain configurations, shown in that previous list you showed in the lines starting with **rc**, such as:-
```
rc  linux-image-3.19.0-30-generic                               3.19.0-30.34~14.04.1
rc  linux-image-3.19.0-31-generic                               3.19.0-31.36~14.04.1
rc  linux-image-3.19.0-32-generic                               3.19.0-32.37~14.04.1
rc  linux-image-3.19.0-36-generic                               3.19.0-36.41~14.04.1
rc  linux-image-3.19.0-37-generic                               3.19.0-37.42~14.04.1
rc  linux-image-3.19.0-39-generic                               3.19.0-39.44~14.04.1
rc  linux-image-3.19.0-41-generic                               3.19.0-41.46~14.04.2
rc  linux-image-3.19.0-42-generic                               3.19.0-42.48~14.04.1
rc  linux-image-3.19.0-49-generic                               3.19.0-49.55~14.04.1
```
and several newer kernels that are installed but only half configured, so probably not being used, in lines starting iF, such as:-
```
iF  linux-image-4.4.0-22-generic                                4.4.0-22.40
iF  linux-image-4.4.0-64-generic                                4.4.0-64.85
iF  linux-image-4.4.0-66-generic                                4.4.0-66.87
```
Lets start by trying to get those half configured kernels fully configured with ```
sudo dpkg --configure -a
``` and if that works now try removing the configurations for those old kernels with ```
sudo dpkg -P linux-image-3.19.0*
```
Let us know if that gets you anywhere and then we can take this cleanup process a step further

[COLOR="#FF0000"]EDIT:[/COLOR]
I am glad to see that you do not have a separate /boot partition and filesystem is not so short of space so as to cause any problems similar to what you have here, but one more thing to check my be inode usage with command ```
df -ihT
``` as all those old configurations may be using inodes unnecessarily.

---

### Post by crazybear on 2017-03-18
I have tried 
sudo dpkg --configure -a
endless times with ZERO positive results!

```

$ sudo dpkg --configure -a
[sudo] password for peter-and-crazybear: 
Setting up linux-image-4.4.0-22-generic (4.4.0-22.40) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled 
(4.4.0-22.39 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(4.4.0-22.39 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-22-generic /boot/vmlinuz-4.4.0-22-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-22-generic /boot/vmlinuz-4.4.0-22-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-22-generic /boot/vmlinuz-4.4.0-22-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-22-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-22-generic /boot/vmlinuz-4.4.0-22-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-22-generic /boot/vmlinuz-4.4.0-22-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-22-generic /boot/vmlinuz-4.4.0-22-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-22-generic /boot/vmlinuz-4.4.0-22-generic
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_GFXPAYLOAD_LINUX=None'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 64
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-4.4.0-22-generic.postinst line 1052.
dpkg: error processing package linux-image-4.4.0-22-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up plymouth-theme-ubuntu-gnome-logo (16.04.5) ...
update-initramfs: deferring update (trigger activated)
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_GFXPAYLOAD_LINUX=None'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
dpkg: error processing package plymouth-theme-ubuntu-gnome-logo (--configure):
 subprocess installed post-installation script returned error exit status 64
Setting up grub-pc (2.02~beta2-36ubuntu3.8) ...
Installing for i386-pc platform.
Installation finished. No error reported.
Installing for i386-pc platform.
grub-install: warning: File system `ext2' doesn't support embedding.
grub-install: warning: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
Installation finished. No error reported.
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_GFXPAYLOAD_LINUX=None'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
dpkg: error processing package grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 64
Setting up linux-image-4.4.0-66-generic (4.4.0-66.87) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-66-generic /boot/vmlinuz-4.4.0-66-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-66-generic /boot/vmlinuz-4.4.0-66-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-66-generic /boot/vmlinuz-4.4.0-66-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-66-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-66-generic /boot/vmlinuz-4.4.0-66-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-66-generic /boot/vmlinuz-4.4.0-66-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-66-generic /boot/vmlinuz-4.4.0-66-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-66-generic /boot/vmlinuz-4.4.0-66-generic
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_GFXPAYLOAD_LINUX=None'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 64
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-4.4.0-66-generic.postinst line 1052.
dpkg: error processing package linux-image-4.4.0-66-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-4.4.0-66-generic; however:
  Package linux-image-4.4.0-66-generic is not configured yet.

dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-4.4.0-64-generic (4.4.0-64.85) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-64-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
Generating grub configuration file ...
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_GFXPAYLOAD_LINUX=None'.
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 64
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-4.4.0-64-generic.postinst line 1052.
dpkg: error processing package linux-image-4.4.0-64-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-extra-4.4.0-22-generic:
 linux-image-extra-4.4.0-22-generic depends on linux-image-4.4.0-22-generic; however:
  Package linux-image-4.4.0-22-generic is not configured yet.

dpkg: error processing package linux-image-extra-4.4.0-22-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-extra-4.4.0-64-generic:
 linux-image-extra-4.4.0-64-generic depends on linux-image-4.4.0-64-generic; however:
  Package linux-image-4.4.0-64-generic is not configured yet.

dpkg: error processing package linux-image-extra-4.4.0-64-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-extra-4.4.0-66-generic:
 linux-image-extra-4.4.0-66-generic depends on linux-image-4.4.0-66-generic; however:
  Package linux-image-4.4.0-66-generic is not configured yet.

dpkg: error processing package linux-image-extra-4.4.0-66-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 4.4.0.66.70); however:
  Package linux-image-generic is not configured yet.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic-lts-vivid:
 linux-generic-lts-vivid depends on linux-generic; however:
  Package linux-generic is not configured yet.

dpkg: error processing package linux-generic-lts-vivid (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools (0.122ubuntu8.8) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-66-generic
Errors were encountered while processing:
 linux-image-4.4.0-22-generic
 plymouth-theme-ubuntu-gnome-logo
 grub-pc
 linux-image-4.4.0-66-generic
 linux-image-generic
 linux-image-4.4.0-64-generic
 linux-image-extra-4.4.0-22-generic
 linux-image-extra-4.4.0-64-generic
 linux-image-extra-4.4.0-66-generic
 linux-generic
 linux-generic-lts-vivid


```

As for df -ihT

```

$ df -ihT
Filesystem     Type     Inodes IUsed IFree IUse% Mounted on
udev           devtmpfs   3.0M   756  3.0M    1% /dev
tmpfs          tmpfs      3.0M  1.3K  3.0M    1% /run
/dev/sdd1      ext4        58M  1.7M   57M    3% /
tmpfs          tmpfs      3.0M    13  3.0M    1% /dev/shm
tmpfs          tmpfs      3.0M     9  3.0M    1% /run/lock
tmpfs          tmpfs      3.0M    18  3.0M    1% /sys/fs/cgroup
cgmfs          tmpfs      3.0M    14  3.0M    1% /run/cgmanager/fs
tmpfs          tmpfs      3.0M    13  3.0M    1% /run/user/125
tmpfs          tmpfs      3.0M    21  3.0M    1% /run/user/1000
/dev/sde1      ext4       175M  238K  175M    1% /1st-3T-DATA-INFO
/dev/sdc1      vfat          0     0     0     - /media/SURVIVORUSB


```

---

### Post by crazybear on 2017-03-18
> **mus1cfreak said:**
> what shows:
cat /etc/apt/sources.list

$ cat /etc/apt/sources.list 
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial main universe restricted multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) xenial-security main universe multiverse restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates main universe multiverse restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports main universe multiverse restricted

---

### Post by crazybear on 2017-03-19
Is there a greater possibility to fully install/remove these things using a live CD? My system seems to be stuck at a point where I can't do anything much. :confused:
According to what I see on the Grub screen, I am booting into Linux 4.4.0-22. Would something done in recovery mode be helpful?!
Thanks.

---

### Post by dragonfly41 on 2017-03-19
One suggestion .. install grub-customizer .. to get more visibility in GUI
about Grub settings.   You can view each setting via highlight > right click > edit.
But I would not suggest actually editing and changing before first asking in this forum.

---

### Post by crazybear on 2017-03-19
I have and use grub-customizer....but this is not my problem. Getting rid of the 'stuck' un-removable linux-images is....

---

### Post by Bashing-om on 2017-03-19
crazybear; Hello again .

Mind if I poke my nose into this, as you do not seem to be making much headway ?

Appears that the ONLY kernel fully installed is :
> 
ii  linux-image-4.4.0-21-generic 

And it is tough to say presently on a best procedure . However, I do know that we must get linux-firmware, linux-generic, linux-headers-generic, and linux-image-generic fully installed. Whatever that may take.

I do suggest that to start this process that you clean out the trash:
While there is no built in way to remove all of your configuration information from your removed packages you can remove all configuration data from every removed package. To purge all removed but not yet purged packages, where The state is rc, the package is removed, but the config files are not removed....with the following command.
```

dpkg -l | awk '/^rc/{print $2}' | xargs sudo dpkg -P

```
Now show me what we are working with in a format I am accustomed to .
```

dpkg -l | grep linux-
ls -al /boot/
lsb_release -a
uname -r

```
Try and rebuild as clean as possible, knowing, however, we may have to get real dirty to make things right in the end. This could be a long hard process .

Clear away the clutter and get a better view of what we have to do.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by Impavidus on 2017-03-19
Do you mind if I poke my nose in too?

> **crazybear said:**
> 
```
:~$ sudo apt-get dist-upgrade
...
Removing linux-image-3.13.0-54-generic (3.13.0-54.91) ...
Examining /etc/kernel/postrm.d . (...)
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-54-generic /boot/vmlinuz-3.13.0-54-generic
Generating grub configuration file ...
**/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_GFXPAYLOAD_LINUX=None'.**
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 64
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.13.0-54-generic.postrm line 328.
dpkg: error processing package linux-image-3.13.0-54-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
...

```

> **crazybear said:**
> 
```

$ sudo dpkg --configure -a
...
Setting up linux-image-4.4.0-22-generic (4.4.0-22.40) ... (...)
Examining /etc/kernel/postinst.d. (...)
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-22-generic /boot/vmlinuz-4.4.0-22-generic
Generating grub configuration file ...
**/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_GFXPAYLOAD_LINUX=None'.**
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 64
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-4.4.0-22-generic.postinst line 1052.
dpkg: error processing package linux-image-4.4.0-22-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
...
Setting up grub-pc (2.02~beta2-36ubuntu3.8) ...
Installing for i386-pc platform.
Installation finished. No error reported.
Installing for i386-pc platform.
grub-install: warning: File system `ext2' doesn't support embedding.
grub-install: warning: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
Installation finished. No error reported.
Generating grub configuration file ...
**/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_GFXPAYLOAD_LINUX=None'.**
No path or device is specified.
Usage: grub-probe [OPTION...] [OPTION]... [PATH|DEVICE]
Try 'grub-probe --help' or 'grub-probe --usage' for more information.
dpkg: error processing package grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 64

```

Every time the same error. Whenever a kernel gets installed or uninstalled, or when grub is installed, the grub configuration file gets updated. Here something goes wrong:```
/usr/sbin/grub-probe: error: failed to get canonical path of `/boot/grub/unicode.pf2GRUB_GFXPAYLOAD_LINUX=None'
```which shows a strange concatenation of a file name and some option from a config file. The error is in the grub update code, nothing specific with the kernels or the package manager. I don't know how to solve this. Maybe reinstalling grup-common and other grub-related packages helps. Or replacing /etc/default/grub with a clean copy. I don't know.

I have to say though that this isn't the first strange error in updating the boot loader on systems with grub customizer I have seen: [https://ubuntuforums.org/showthread.php?t=2353152](https://ubuntuforums.org/showthread.php?t=2353152). It seems grub customizer may encourage messing up grub...

---

### Post by ajgreeny on 2017-03-19
Interesting find Impavidus, and you may be right.

@crazybear
I wonder if it is worth using command ```
sudo apt-get purge grub*
``` then reinstalling all the packages that are removed when running that command, probably 5 or 6 of them but it will depend on whether you have UEFI or BIOS as to which are removed and then reinstalled.

I have never used grub-customiser as all it can do is also possible without it, so I have no idea about its abilities nor how likely it is to affect the situation as suggested by Impavidus.

---

### Post by crazybear on 2017-03-21
> **Bashing-om said:**
> crazybear; Hello again .

Mind if I poke my nose into this, as you do not seem to be making much headway ?

Appears that the ONLY kernel fully installed is :

And it is tough to say presently on a best procedure . However, I do know that we must get linux-firmware, linux-generic, linux-headers-generic, and linux-image-generic fully installed. Whatever that may take.

I do suggest that to start this process that you clean out the trash:
While there is no built in way to remove all of your configuration information from your removed packages you can remove all configuration data from every removed package. To purge all removed but not yet purged packages, where The state is rc, the package is removed, but the config files are not removed....with the following command.
```

dpkg -l | awk '/^rc/{print $2}' | xargs sudo dpkg -P

```
Now show me what we are working with in a format I am accustomed to .
```

dpkg -l | grep linux-
ls -al /boot/
lsb_release -a
uname -r

```
Try and rebuild as clean as possible, knowing, however, we may have to get real dirty to make things right in the end. This could be a long hard process .

Clear away the clutter and get a better view of what we have to do.
[INDENT][INDENT]ain't nothing but a thing
[/INDENT]
[/INDENT]


Well, that is a handy-dandy little bit o' code! It certainly removed a LOT of things...I just hope it didn't remove anything I NEED! [or that I'd have to re-install now before I log out to ever log back in...!]

I usually get logged in to 4.4.0-22, but because I was told that the only one that seemed to be fully installed was 4.4.0-21, I purposely logged in with that now.

```

Purging configuration files for brltty-x11 (5.0-2ubuntu2) ...
Removing browser-plugin-gnash (0.8.11~git20160109-1build1) ...
Purging configuration files for browser-plugin-gnash (0.8.11~git20160109-1build1) ...
Removing debian-mate-default-settings (1.12.2-1) ...
Purging configuration files for debian-mate-default-settings (1.12.2-1) ...
Removing f-spot (0.8.2-5.1ubuntu1) ...
Purging configuration files for f-spot (0.8.2-5.1ubuntu1) ...
Removing flashplugin-installer (11.2.202.621ubuntu0.16.04.1) ...
Purging configuration files for flashplugin-installer (11.2.202.621ubuntu0.16.04.1) ...
Removing galculator (2.1.4-1) ...
Purging configuration files for galculator (2.1.4-1) ...
Removing gnash (0.8.11~git20160109-1build1) ...
Purging configuration files for gnash (0.8.11~git20160109-1build1) ...
Removing kde-window-manager-common (4:4.11.11-0ubuntu0.2) ...
Purging configuration files for kde-window-manager-common (4:4.11.11-0ubuntu0.2) ...
Removing kodi (2:16.1~git20160424.1410-final-0trusty) ...
Purging configuration files for kodi (2:16.1~git20160424.1410-final-0trusty) ...
Removing libaccounts-qt1 (1.11+14.04.20140410.1-0ubuntu1) ...
Purging configuration files for libaccounts-qt1 (1.11+14.04.20140410.1-0ubuntu1) ...
Removing libafpclient0:amd64 (0.8.1-5ubuntu1) ...
Purging configuration files for libafpclient0:amd64 (0.8.1-5ubuntu1) ...
Removing libakonadi-socialutils4 (4:4.14.10-1ubuntu2) ...
Purging configuration files for libakonadi-socialutils4 (4:4.14.10-1ubuntu2) ...
Removing libapertium3-3.1-0 (3.1.0-2) ...
Purging configuration files for libapertium3-3.1-0 (3.1.0-2) ...
Removing libatkmm-1.6-1:amd64 (2.22.7-2ubuntu1) ...
Purging configuration files for libatkmm-1.6-1:amd64 (2.22.7-2ubuntu1) ...
Removing libavcodec54:amd64 (6:9.16-0ubuntu0.14.04.1) ...
Purging configuration files for libavcodec54:amd64 (6:9.16-0ubuntu0.14.04.1) ...
Removing libavfilter3:amd64 (6:9.18-0ubuntu0.14.04.1+fdkaac) ...
Purging configuration files for libavfilter3:amd64 (6:9.18-0ubuntu0.14.04.1+fdkaac) ...
Removing libavresample1:amd64 (6:9.18-0ubuntu0.14.04.1+fdkaac) ...
Purging configuration files for libavresample1:amd64 (6:9.18-0ubuntu0.14.04.1+fdkaac) ...
Removing libbaloopim4 (4:4.14.3-0ubuntu5) ...
Purging configuration files for libbaloopim4 (4:4.14.3-0ubuntu5) ...
Removing libbaloowidgets4 (4:4.13.3-0ubuntu0.1) ...
Purging configuration files for libbaloowidgets4 (4:4.13.3-0ubuntu0.1) ...
Removing libbasicusageenvironment0 (2014.01.13-1) ...
Purging configuration files for libbasicusageenvironment0 (2014.01.13-1) ...
Removing libboo2.0.9-cil (0.9.5~git20110729.r1.202a430-2) ...
Purging configuration files for libboo2.0.9-cil (0.9.5~git20110729.r1.202a430-2) ...
Removing libboost-atomic1.54.0:amd64 (1.54.0-4ubuntu3.1) ...
Purging configuration files for libboost-atomic1.54.0:amd64 (1.54.0-4ubuntu3.1) ...
Removing libboost-chrono1.54.0:amd64 (1.54.0-4ubuntu3.1) ...
Purging configuration files for libboost-chrono1.54.0:amd64 (1.54.0-4ubuntu3.1) ...
Removing libboost-context1.54.0:amd64 (1.54.0-4ubuntu3.1) ...
Purging configuration files for libboost-context1.54.0:amd64 (1.54.0-4ubuntu3.1) ...
Removing libboost-filesystem1.54.0:amd64 (1.54.0-4ubuntu3.1) ...
Purging configuration files for libboost-filesystem1.54.0:amd64 (1.54.0-4ubuntu3.1) ...
Removing libboost-graph-parallel1.54.0 (1.54.0-4ubuntu3.1) ...
Purging configuration files for libboost-graph-parallel1.54.0 (1.54.0-4ubuntu3.1) ...
Removing libboost-graph1.54.0:amd64 (1.54.0-4ubuntu3.1) ...
Purging configuration files for libboost-graph1.54.0:amd64 (1.54.0-4ubuntu3.1) ...
Removing libboost-iostreams1.54.0:amd64 (1.54.0-4ubuntu3.1) ...
Purging configuration files for libboost-iostreams1.54.0:amd64 (1.54.0-4ubuntu3.1) ...
Removing libboost-locale1.54.0:amd64 (1.54.0-4ubuntu3.1) ...
Purging configuration files for libboost-locale1.54.0:amd64 (1.54.0-4ubuntu3.1) ...
Removing libboost-log1.54.0 (1.54.0-4ubuntu3.1) ...
Purging configuration files for libboost-log1.54.0 (1.54.0-4ubuntu3.1) ...
Removing libboost-math1.54.0:amd64 (1.54.0-4ubuntu3.1) ...
Purging configuration files for libboost-math1.54.0:amd64 (1.54.0-4ubuntu3.1) ...
Removing libboost-mpi-python1.54.0 (1.54.0-4ubuntu3.1) ...
Purging configuration files for libboost-mpi-python1.54.0 (1.54.0-4ubuntu3.1) ...
Removing libboost-mpi1.54.0 (1.54.0-4ubuntu3.1) ...
Purging configuration files for libboost-mpi1.54.0 (1.54.0-4ubuntu3.1) ...
Removing libboost-program-options1.54.0:amd64 (1.54.0-4ubuntu3.1) ...
Purging configuration files for libboost-program-options1.54.0:amd64 (1.54.0-4ubuntu3.1) ...
Removing libboost-python1.54.0:amd64 (1.54.0-4ubuntu3.1) ...
Purging configuration files for libboost-python1.54.0:amd64 (1.54.0-4ubuntu3.1) ...
Removing libboost-python1.55.0 (1.55.0-1) ...
Purging configuration files for libboost-python1.55.0 (1.55.0-1) ...
Removing libboost-random1.54.0:amd64 (1.54.0-4ubuntu3.1) ...
Purging configuration files for libboost-random1.54.0:amd64 (1.54.0-4ubuntu3.1) ...
Removing libboost-regex1.54.0:amd64 (1.54.0-4ubuntu3.1) ...
Purging configuration files for libboost-regex1.54.0:amd64 (1.54.0-4ubuntu3.1) ...
Removing libboost-serialization1.54.0:amd64 (1.54.0-4ubuntu3.1) ...
Purging configuration files for libboost-serialization1.54.0:amd64 (1.54.0-4ubuntu3.1) ...
Removing libboost-signals1.54.0:amd64 (1.54.0-4ubuntu3.1) ...
Purging configuration files for libboost-signals1.54.0:amd64 (1.54.0-4ubuntu3.1) ...
Removing libboost-test1.54.0:amd64 (1.54.0-4ubuntu3.1) ...
Purging configuration files for libboost-test1.54.0:amd64 (1.54.0-4ubuntu3.1) ...
Removing libboost-thread1.54.0:amd64 (1.54.0-4ubuntu3.1) ...
Purging configuration files for libboost-thread1.54.0:amd64 (1.54.0-4ubuntu3.1) ...
Removing libboost-timer1.54.0:amd64 (1.54.0-4ubuntu3.1) ...
Purging configuration files for libboost-timer1.54.0:amd64 (1.54.0-4ubuntu3.1) ...
Removing libboost-wave1.54.0:amd64 (1.54.0-4ubuntu3.1) ...
Purging configuration files for libboost-wave1.54.0:amd64 (1.54.0-4ubuntu3.1) ...
Removing libcairomm-1.0-1:amd64 (1.10.0-1ubuntu3) ...
Purging configuration files for libcairomm-1.0-1:amd64 (1.10.0-1ubuntu3) ...
Removing libcalendarsupport4 (4:4.13.3-0ubuntu0.1) ...
Purging configuration files for libcalendarsupport4 (4:4.13.3-0ubuntu0.1) ...
Removing libcauchy0.0 (0.9.0-0ubuntu1) ...
Purging configuration files for libcauchy0.0 (0.9.0-0ubuntu1) ...
Removing libcec2:amd64 (2.2.0-2~trusty) ...
Purging configuration files for libcec2:amd64 (2.2.0-2~trusty) ...
Removing libcheese-gtk23:amd64 (3.10.2-0ubuntu2) ...
Purging configuration files for libcheese-gtk23:amd64 (3.10.2-0ubuntu2) ...
Removing libcheese7:amd64 (3.10.2-0ubuntu2) ...
Purging configuration files for libcheese7:amd64 (3.10.2-0ubuntu2) ...
Removing libclucene-contribs1:amd64 (2.3.3.4-4build1) ...
Purging configuration files for libclucene-contribs1:amd64 (2.3.3.4-4build1) ...
Removing libclucene-core1:amd64 (2.3.3.4-4build1) ...
Purging configuration files for libclucene-core1:amd64 (2.3.3.4-4build1) ...
Removing libclutter-gst-1.0-0:amd64 (1.6.0-2build1) ...
Purging configuration files for libclutter-gst-1.0-0:amd64 (1.6.0-2build1) ...
Removing libcogl-pango15:amd64 (1.16.2-1) ...
Purging configuration files for libcogl-pango15:amd64 (1.16.2-1) ...
Removing libcogl15:amd64 (1.16.2-1) ...
Purging configuration files for libcogl15:amd64 (1.16.2-1) ...
Removing libcolumbus1:amd64 (1.1.0+14.04.20140325.3-0ubuntu1) ...
Purging configuration files for libcolumbus1:amd64 (1.1.0+14.04.20140325.3-0ubuntu1) ...
Removing libconfig++9:amd64 (1.4.9-2) ...
Purging configuration files for libconfig++9:amd64 (1.4.9-2) ...
Removing libcr0 (0.8.5-2.2) ...
Purging configuration files for libcr0 (0.8.5-2.2) ...
Removing libcrypto++9 (5.6.1-6+deb8u1build0.14.04.1) ...
Purging configuration files for libcrypto++9 (5.6.1-6+deb8u1build0.14.04.1) ...
Removing libcwidget3 (0.5.16-3.5ubuntu1) ...
Purging configuration files for libcwidget3 (0.5.16-3.5ubuntu1) ...
Removing libdebconf-kde0 (0.3-1) ...
Purging configuration files for libdebconf-kde0 (0.3-1) ...
Removing libdvbpsi8:amd64 (1.0.0-3) ...
Purging configuration files for libdvbpsi8:amd64 (1.0.0-3) ...
Removing libebml4:amd64 (1.3.0-2+deb8u1build0.14.04.1) ...
Purging configuration files for libebml4:amd64 (1.3.0-2+deb8u1build0.14.04.1) ...
Removing libecal-1.2-16 (3.10.4-0ubuntu1.5) ...
Purging configuration files for libecal-1.2-16 (3.10.4-0ubuntu1.5) ...
Removing libechonest2.1:amd64 (2.1.0-2) ...
Purging configuration files for libechonest2.1:amd64 (2.1.0-2) ...
Removing libecryptfs0 (104-0ubuntu1.14.04.4) ...
Purging configuration files for libecryptfs0 (104-0ubuntu1.14.04.4) ...
Removing libedata-cal-1.2-23 (3.10.4-0ubuntu1.5) ...
Purging configuration files for libedata-cal-1.2-23 (3.10.4-0ubuntu1.5) ...
Removing libegl1-mesa-lts-vivid:amd64 (10.5.9-2ubuntu1~trusty2) ...
Purging configuration files for libegl1-mesa-lts-vivid:amd64 (10.5.9-2ubuntu1~trusty2) ...
Removing libept1.4.12:amd64 (1.0.12) ...
Purging configuration files for libept1.4.12:amd64 (1.0.12) ...
Removing libexosip2-10 (4.0.0-4ubuntu1) ...
Purging configuration files for libexosip2-10 (4.0.0-4ubuntu1) ...
Removing libfarstream-0.2-2:amd64 (0.2.3-1ubuntu2) ...
Purging configuration files for libfarstream-0.2-2:amd64 (0.2.3-1ubuntu2) ...
Removing libffmpegthumbnailer4 (2.0.8-2) ...
Purging configuration files for libffmpegthumbnailer4 (2.0.8-2) ...
Removing libflac++6:amd64 (1.3.0-2ubuntu0.14.04.1) ...
Purging configuration files for libflac++6:amd64 (1.3.0-2ubuntu0.14.04.1) ...
Removing libfreenect0.2:amd64 (1:0.2.0+dfsg-2) ...
Purging configuration files for libfreenect0.2:amd64 (1:0.2.0+dfsg-2) ...
Removing libfreerdp1:amd64 (1.0.2-2ubuntu1) ...
Purging configuration files for libfreerdp1:amd64 (1.0.2-2ubuntu1) ...
Removing libgbm1-lts-vivid:amd64 (10.5.9-2ubuntu1~trusty2) ...
Purging configuration files for libgbm1-lts-vivid:amd64 (10.5.9-2ubuntu1~trusty2) ...
Removing libgconfmm-2.6-1c2 (2.28.3-0ubuntu2) ...
Purging configuration files for libgconfmm-2.6-1c2 (2.28.3-0ubuntu2) ...
Removing libgcu0 (0.14.6-1ubuntu1) ...
Purging configuration files for libgcu0 (0.14.6-1ubuntu1) ...
Removing libgdome2-cpp-smart0c2a (0.2.6-6ubuntu1) ...
Purging configuration files for libgdome2-cpp-smart0c2a (0.2.6-6ubuntu1) ...
Removing libgif4:amd64 (4.1.6-11) ...
Purging configuration files for libgif4:amd64 (4.1.6-11) ...
Removing libgl1-mesa-dri-lts-vivid:amd64 (10.5.9-2ubuntu1~trusty2) ...
Purging configuration files for libgl1-mesa-dri-lts-vivid:amd64 (10.5.9-2ubuntu1~trusty2) ...
Removing libgl1-mesa-dri-lts-vivid:i386 (10.5.9-2ubuntu1~trusty2) ...
Purging configuration files for libgl1-mesa-dri-lts-vivid:i386 (10.5.9-2ubuntu1~trusty2) ...
Removing libgl1-mesa-glx-lts-vivid:amd64 (10.5.9-2ubuntu1~trusty2) ...
Purging configuration files for libgl1-mesa-glx-lts-vivid:amd64 (10.5.9-2ubuntu1~trusty2) ...
Removing libgl1-mesa-glx-lts-vivid:i386 (10.5.9-2ubuntu1~trusty2) ...
Purging configuration files for libgl1-mesa-glx-lts-vivid:i386 (10.5.9-2ubuntu1~trusty2) ...
Removing libglademm-2.4-1c2a (2.6.7-2ubuntu1) ...
Purging configuration files for libglademm-2.4-1c2a (2.6.7-2ubuntu1) ...
Removing libglapi-mesa-lts-vivid:amd64 (10.5.9-2ubuntu1~trusty2) ...
Purging configuration files for libglapi-mesa-lts-vivid:amd64 (10.5.9-2ubuntu1~trusty2) ...
Removing libglapi-mesa-lts-vivid:i386 (10.5.9-2ubuntu1~trusty2) ...
Purging configuration files for libglapi-mesa-lts-vivid:i386 (10.5.9-2ubuntu1~trusty2) ...
Removing libgle3 (3.1.0-7.1) ...
Purging configuration files for libgle3 (3.1.0-7.1) ...
Removing libgles1-mesa-lts-vivid:amd64 (10.5.9-2ubuntu1~trusty2) ...
Purging configuration files for libgles1-mesa-lts-vivid:amd64 (10.5.9-2ubuntu1~trusty2) ...
Removing libgles2-mesa-lts-vivid:amd64 (10.5.9-2ubuntu1~trusty2) ...
Purging configuration files for libgles2-mesa-lts-vivid:amd64 (10.5.9-2ubuntu1~trusty2) ...
Removing libglibmm-2.4-1c2a:amd64 (2.39.93-0ubuntu1) ...
Purging configuration files for libglibmm-2.4-1c2a:amd64 (2.39.93-0ubuntu1) ...
Removing libgnome-control-center1 (1:3.8.6-0ubuntu1~trusty2) ...
Purging configuration files for libgnome-control-center1 (1:3.8.6-0ubuntu1~trusty2) ...
Removing libgnustep-gui0.22 (0.22.0-1ubuntu2) ...
Purging configuration files for libgnustep-gui0.22 (0.22.0-1ubuntu2) ...
Removing libgnutls-deb0-28:amd64 (3.2.16-1u1~ppa2) ...
Purging configuration files for libgnutls-deb0-28:amd64 (3.2.16-1u1~ppa2) ...
Removing libgnutls-deb0-28:i386 (3.2.16-1u1~ppa2) ...
Purging configuration files for libgnutls-deb0-28:i386 (3.2.16-1u1~ppa2) ...
Removing libgnutls28:amd64 (3.2.11-2ubuntu1.1) ...
Purging configuration files for libgnutls28:amd64 (3.2.11-2ubuntu1.1) ...
Removing libgpac2:amd64 (0.5.0+svn4288~dfsg1-4ubuntu1) ...
Purging configuration files for libgpac2:amd64 (0.5.0+svn4288~dfsg1-4ubuntu1) ...
Removing libgpgme++2 (4:4.13.3-0ubuntu0.2) ...
Purging configuration files for libgpgme++2 (4:4.13.3-0ubuntu0.2) ...
Removing libgphoto2-port10:i386 (2.5.3.1-1ubuntu2.2) ...
Purging configuration files for libgphoto2-port10:i386 (2.5.3.1-1ubuntu2.2) ...
Removing libgroupsock1 (2014.01.13-1) ...
Purging configuration files for libgroupsock1 (2014.01.13-1) ...
Removing libgsl0ldbl (1.16+dfsg-1ubuntu1) ...
Purging configuration files for libgsl0ldbl (1.16+dfsg-1ubuntu1) ...
Removing libgsoap4:amd64 (2.8.16-2) ...
Purging configuration files for libgsoap4:amd64 (2.8.16-2) ...
Removing libgtkmm-2.4-1c2a:amd64 (1:2.24.4-1ubuntu1) ...
Purging configuration files for libgtkmm-2.4-1c2a:amd64 (1:2.24.4-1ubuntu1) ...
Removing libgtkmm-3.0-1:amd64 (3.10.1-0ubuntu2) ...
Purging configuration files for libgtkmm-3.0-1:amd64 (3.10.1-0ubuntu2) ...
Removing libhdf5-7:amd64 (1.8.11-5ubuntu7) ...
Purging configuration files for libhdf5-7:amd64 (1.8.11-5ubuntu7) ...
Removing libhogweed2:amd64 (2.7.1-1ubuntu0.1) ...
Purging configuration files for libhogweed2:amd64 (2.7.1-1ubuntu0.1) ...
Removing libhogweed2:i386 (2.7.1-1ubuntu0.1) ...
Purging configuration files for libhogweed2:i386 (2.7.1-1ubuntu0.1) ...
Removing libical1 (1.0-0ubuntu1) ...
Purging configuration files for libical1 (1.0-0ubuntu1) ...
Removing libicc2:amd64 (2.12+argyll1.5.1-5ubuntu1) ...
Purging configuration files for libicc2:amd64 (2.12+argyll1.5.1-5ubuntu1) ...
Removing libid3-3.8.3c2a (3.8.3-15) ...
Purging configuration files for libid3-3.8.3c2a (3.8.3-15) ...
Removing libidl0:amd64 (0.8.14-0.2ubuntu4) ...
Purging configuration files for libidl0:amd64 (0.8.14-0.2ubuntu4) ...
Removing libimdi0:amd64 (1.5.1-5ubuntu1) ...
Purging configuration files for libimdi0:amd64 (1.5.1-5ubuntu1) ...
Removing libincidenceeditorsng4 (4:4.13.3-0ubuntu0.1) ...
Purging configuration files for libincidenceeditorsng4 (4:4.13.3-0ubuntu0.1) ...
Removing libindi0c:amd64 (0.9.7-0ubuntu4) ...
Purging configuration files for libindi0c:amd64 (0.9.7-0ubuntu4) ...
Removing libkactivities-models1 (4:4.13.3-0ubuntu0.2) ...
Purging configuration files for libkactivities-models1 (4:4.13.3-0ubuntu0.2) ...
Removing libkarma0 (0.1.2-2.3) ...
Purging configuration files for libkarma0 (0.1.2-2.3) ...
Removing libkdb5-7:amd64 (1.12+dfsg-2ubuntu5.2) ...
Purging configuration files for libkdb5-7:amd64 (1.12+dfsg-2ubuntu5.2) ...
Removing libkdecorations4abi1 (4:4.11.11-0ubuntu0.2) ...
Purging configuration files for libkdecorations4abi1 (4:4.11.11-0ubuntu0.2) ...
Removing libkdepim4 (4:4.13.3-0ubuntu0.1) ...
Purging configuration files for libkdepim4 (4:4.13.3-0ubuntu0.1) ...
Removing libkdepimdbusinterfaces4 (4:4.13.3-0ubuntu0.1) ...
Purging configuration files for libkdepimdbusinterfaces4 (4:4.13.3-0ubuntu0.1) ...
Removing libkdgantt2-0 (4:4.13.3-0ubuntu0.1) ...
Purging configuration files for libkdgantt2-0 (4:4.13.3-0ubuntu0.1) ...
Removing libkexiv2-11 (4:4.13.0-0ubuntu1) ...
Purging configuration files for libkexiv2-11 (4:4.13.0-0ubuntu1) ...
Removing libkface2 (1.0~digikam3.5.0-0ubuntu10) ...
Purging configuration files for libkface2 (1.0~digikam3.5.0-0ubuntu10) ...
Removing libkfbapi1 (1.0-0ubuntu7) ...
Purging configuration files for libkfbapi1 (1.0-0ubuntu7) ...
Removing libkfilemetadata4 (4:4.14.2-0ubuntu2) ...
Purging configuration files for libkfilemetadata4 (4:4.14.2-0ubuntu2) ...
Removing libkgapi2-2:amd64 (2.1.0-0ubuntu1) ...
Purging configuration files for libkgapi2-2:amd64 (2.1.0-0ubuntu1) ...
Removing libkgeomap1 (1.0~digikam3.5.0-0ubuntu10) ...
Purging configuration files for libkgeomap1 (1.0~digikam3.5.0-0ubuntu10) ...
Removing libkleo4 (4:4.13.3-0ubuntu0.1) ...
Purging configuration files for libkleo4 (4:4.13.3-0ubuntu0.1) ...
Removing libkolab0 (0.5.0-0ubuntu4) ...
Purging configuration files for libkolab0 (0.5.0-0ubuntu4) ...
Removing libkolabxml1 (1.0.1-0ubuntu3) ...
Purging configuration files for libkolabxml1 (1.0.1-0ubuntu3) ...
Removing libkpgp4 (4:4.13.3-0ubuntu0.1) ...
Purging configuration files for libkpgp4 (4:4.13.3-0ubuntu0.1) ...
Removing libkscreen1 (1.0.5-0ubuntu1~ubuntu14.04) ...
Purging configuration files for libkscreen1 (1.0.5-0ubuntu1~ubuntu14.04) ...
Removing libktnef4 (4:4.14.10-1ubuntu2) ...
Purging configuration files for libktnef4 (4:4.14.10-1ubuntu2) ...
Removing libkubuntu0 (14.04ubuntu4) ...
Purging configuration files for libkubuntu0 (14.04ubuntu4) ...
Removing libkwineffects1abi4 (4:4.11.11-0ubuntu0.2) ...
Purging configuration files for libkwineffects1abi4 (4:4.11.11-0ubuntu0.2) ...
Removing libkwinglesutils1 (4:4.11.11-0ubuntu0.2) ...
Purging configuration files for libkwinglesutils1 (4:4.11.11-0ubuntu0.2) ...
Removing libkwinglutils1abi3 (4:4.11.11-0ubuntu0.2) ...
Purging configuration files for libkwinglutils1abi3 (4:4.11.11-0ubuntu0.2) ...
Removing libkworkspace4abi2 (4:4.11.11-0ubuntu0.2) ...
Purging configuration files for libkworkspace4abi2 (4:4.11.11-0ubuntu0.2) ...
Removing libkwwidgets1.0.1009 (1.0.0~cvs20100930-8) ...
Purging configuration files for libkwwidgets1.0.1009 (1.0.0~cvs20100930-8) ...
Removing liblept4 (1.70.1-1) ...
Purging configuration files for liblept4 (1.70.1-1) ...
Removing liblinear1 (1.8+dfsg-1ubuntu1) ...
Purging configuration files for liblinear1 (1.8+dfsg-1ubuntu1) ...
Removing liblivemedia23 (2014.01.13-1) ...
Purging configuration files for liblivemedia23 (2014.01.13-1) ...
Removing libllvm3.4:i386 (1:3.4-1ubuntu3) ...
Purging configuration files for libllvm3.4:i386 (1:3.4-1ubuntu3) ...
Removing libllvm3.6:amd64 (1:3.6-2ubuntu1~trusty1) ...
Purging configuration files for libllvm3.6:amd64 (1:3.6-2ubuntu1~trusty1) ...
Removing libllvm3.6:i386 (1:3.6-2ubuntu1~trusty1) ...
Purging configuration files for libllvm3.6:i386 (1:3.6-2ubuntu1~trusty1) ...
Removing liblsmash1 (1.9.1-1~trusty) ...
Purging configuration files for liblsmash1 (1.9.1-1~trusty) ...
Removing liblttoolbox3-3.1-0 (3.1.0-1.1ubuntu1) ...
Purging configuration files for liblttoolbox3-3.1-0 (3.1.0-1.1ubuntu1) ...
Removing libm2mml0.0 (0.9.0-0ubuntu1) ...
Purging configuration files for libm2mml0.0 (0.9.0-0ubuntu1) ...
Removing libmagick++5:amd64 (8:6.7.7.10-6ubuntu3) ...
Purging configuration files for libmagick++5:amd64 (8:6.7.7.10-6ubuntu3) ...
Removing libmagickcore5:amd64 (8:6.7.7.10-6ubuntu3) ...
Purging configuration files for libmagickcore5:amd64 (8:6.7.7.10-6ubuntu3) ...
Removing libmagickwand5:amd64 (8:6.7.7.10-6ubuntu3) ...
Purging configuration files for libmagickwand5:amd64 (8:6.7.7.10-6ubuntu3) ...
Removing libmailcommon4 (4:4.13.3-0ubuntu0.1) ...
Purging configuration files for libmailcommon4 (4:4.13.3-0ubuntu0.1) ...
Removing libmailimporter4 (4:4.13.3-0ubuntu0.1) ...
Purging configuration files for libmailimporter4 (4:4.13.3-0ubuntu0.1) ...
Removing libmarblewidget18 (4:4.13.3-0ubuntu0.1) ...
Purging configuration files for libmarblewidget18 (4:4.13.3-0ubuntu0.1) ...
Removing libmateweather-common (1.12.1-1) ...
Purging configuration files for libmateweather-common (1.12.1-1) ...
Removing libmatroska6:amd64 (1.4.1-2+deb8u1build0.14.04.1) ...
Purging configuration files for libmatroska6:amd64 (1.4.1-2+deb8u1build0.14.04.1) ...
Removing libmediaart-1.0-0:amd64 (0.4.0-1ubuntu1) ...
Purging configuration files for libmediaart-1.0-0:amd64 (0.4.0-1ubuntu1) ...
Removing libmediainfo0:amd64 (0.7.75-0ppa1~trusty) ...
Purging configuration files for libmediainfo0:amd64 (0.7.75-0ppa1~trusty) ...
Removing libmessagecomposer4 (4:4.13.3-0ubuntu0.1) ...
Purging configuration files for libmessagecomposer4 (4:4.13.3-0ubuntu0.1) ...
Removing libmessagecore4 (4:4.13.3-0ubuntu0.1) ...
Purging configuration files for libmessagecore4 (4:4.13.3-0ubuntu0.1) ...
Removing libmessageviewer4 (4:4.13.3-0ubuntu0.1) ...
Purging configuration files for libmessageviewer4 (4:4.13.3-0ubuntu0.1) ...
Removing libmetacity-private0a (1:2.34.13-0ubuntu4.1) ...
Purging configuration files for libmetacity-private0a (1:2.34.13-0ubuntu4.1) ...
Removing libmirclient7:amd64 (0.1.8+14.04.20140411-0ubuntu1) ...
Purging configuration files for libmirclient7:amd64 (0.1.8+14.04.20140411-0ubuntu1) ...
Removing libmirprotobuf0:amd64 (0.1.8+14.04.20140411-0ubuntu1) ...
Purging configuration files for libmirprotobuf0:amd64 (0.1.8+14.04.20140411-0ubuntu1) ...
Removing libmowgli-2-0:amd64 (2.0.0-1~webupd8~trusty) ...
Purging configuration files for libmowgli-2-0:amd64 (2.0.0-1~webupd8~trusty) ...
Removing libmozjs-24-0 (24.2.0-1) ...
Purging configuration files for libmozjs-24-0 (24.2.0-1) ...
Removing libmuonprivate2 (2.2.0-0ubuntu3.2) ...
Purging configuration files for libmuonprivate2 (2.2.0-0ubuntu3.2) ...
Removing libmuparser2:amd64 (2.2.3-3) ...
Purging configuration files for libmuparser2:amd64 (2.2.3-3) ...
Removing libmusicbrainz3-6 (3.0.2-2.1) ...
Purging configuration files for libmusicbrainz3-6 (3.0.2-2.1) ...
Removing libmutter0c (3.10.4-0ubuntu2.1) ...
Purging configuration files for libmutter0c (3.10.4-0ubuntu2.1) ...
Removing libmysqlclient18:amd64 (5.5.49-0ubuntu0.14.04.1) ...
Purging configuration files for libmysqlclient18:amd64 (5.5.49-0ubuntu0.14.04.1) ...
Removing libmysqlclient18:i386 (5.5.49-0ubuntu0.14.04.1) ...
Purging configuration files for libmysqlclient18:i386 (5.5.49-0ubuntu0.14.04.1) ...
Removing libnepomuk4 (4:4.13.3-0ubuntu0.2) ...
Purging configuration files for libnepomuk4 (4:4.13.3-0ubuntu0.2) ...
Removing libnepomukcleaner4 (4:4.13.3-0ubuntu0.2) ...
Purging configuration files for libnepomukcleaner4 (4:4.13.3-0ubuntu0.2) ...
Removing libnepomukcore4abi1 (4:4.13.3-0ubuntu0.2) ...
Purging configuration files for libnepomukcore4abi1 (4:4.13.3-0ubuntu0.2) ...
Removing libnepomukquery4a (4:4.13.3-0ubuntu0.2) ...
Purging configuration files for libnepomukquery4a (4:4.13.3-0ubuntu0.2) ...
Removing libnepomukutils4 (4:4.13.3-0ubuntu0.2) ...
Purging configuration files for libnepomukutils4 (4:4.13.3-0ubuntu0.2) ...
Removing libnetcdfc++4 (1:4.1.3-7ubuntu2) ...
Purging configuration files for libnetcdfc++4 (1:4.1.3-7ubuntu2) ...
Removing libnetcdfc7 (1:4.1.3-7ubuntu2) ...
Purging configuration files for libnetcdfc7 (1:4.1.3-7ubuntu2) ...
Removing libnettle4:amd64 (2.7.1-1ubuntu0.1) ...
Purging configuration files for libnettle4:amd64 (2.7.1-1ubuntu0.1) ...
Removing libnettle4:i386 (2.7.1-1ubuntu0.1) ...
Purging configuration files for libnettle4:i386 (2.7.1-1ubuntu0.1) ...
Removing libobrender29 (3.5.2-6) ...
Purging configuration files for libobrender29 (3.5.2-6) ...
Removing libodfgen-0.0-0 (0.0.2-1ubuntu1) ...
Purging configuration files for libodfgen-0.0-0 (0.0.2-1ubuntu1) ...
Removing libokularcore4 (4:4.13.3-0ubuntu0.1) ...
Purging configuration files for libokularcore4 (4:4.13.3-0ubuntu0.1) ...
Removing libopenbabel4 (2.3.2+dfsg-1.1) ...
Purging configuration files for libopenbabel4 (2.3.2+dfsg-1.1) ...
Removing libopencolorio1 (1.0.8+repack2~dfsg0-2.1ubuntu2) ...
Purging configuration files for libopencolorio1 (1.0.8+repack2~dfsg0-2.1ubuntu2) ...
Removing libopencv-calib3d2.4:amd64 (2.4.8+dfsg1-2ubuntu1) ...
Purging configuration files for libopencv-calib3d2.4:amd64 (2.4.8+dfsg1-2ubuntu1) ...
Removing libopencv-contrib2.4:amd64 (2.4.8+dfsg1-2ubuntu1) ...
Purging configuration files for libopencv-contrib2.4:amd64 (2.4.8+dfsg1-2ubuntu1) ...
Removing libopencv-core2.4:amd64 (2.4.8+dfsg1-2ubuntu1) ...
Purging configuration files for libopencv-core2.4:amd64 (2.4.8+dfsg1-2ubuntu1) ...
Removing libopencv-features2d2.4:amd64 (2.4.8+dfsg1-2ubuntu1) ...
Purging configuration files for libopencv-features2d2.4:amd64 (2.4.8+dfsg1-2ubuntu1) ...
Removing libopencv-flann2.4:amd64 (2.4.8+dfsg1-2ubuntu1) ...
Purging configuration files for libopencv-flann2.4:amd64 (2.4.8+dfsg1-2ubuntu1) ...
Removing libopencv-highgui2.4:amd64 (2.4.8+dfsg1-2ubuntu1) ...
Purging configuration files for libopencv-highgui2.4:amd64 (2.4.8+dfsg1-2ubuntu1) ...
Removing libopencv-imgproc2.4:amd64 (2.4.8+dfsg1-2ubuntu1) ...
Purging configuration files for libopencv-imgproc2.4:amd64 (2.4.8+dfsg1-2ubuntu1) ...
Removing libopencv-legacy2.4:amd64 (2.4.8+dfsg1-2ubuntu1) ...
Purging configuration files for libopencv-legacy2.4:amd64 (2.4.8+dfsg1-2ubuntu1) ...
Removing libopencv-ml2.4:amd64 (2.4.8+dfsg1-2ubuntu1) ...
Purging configuration files for libopencv-ml2.4:amd64 (2.4.8+dfsg1-2ubuntu1) ...
Removing libopencv-objdetect2.4:amd64 (2.4.8+dfsg1-2ubuntu1) ...
Purging configuration files for libopencv-objdetect2.4:amd64 (2.4.8+dfsg1-2ubuntu1) ...
Removing libopencv-video2.4:amd64 (2.4.8+dfsg1-2ubuntu1) ...
Purging configuration files for libopencv-video2.4:amd64 (2.4.8+dfsg1-2ubuntu1) ...
Removing libopenimageio1.3 (1.3.12~dfsg0-1ubuntu1) ...
Purging configuration files for libopenimageio1.3 (1.3.12~dfsg0-1ubuntu1) ...
Removing libopenmpi1.6 (1.6.5-8) ...
Purging configuration files for libopenmpi1.6 (1.6.5-8) ...
Removing libopenobex1 (1.5-2.1) ...
Purging configuration files for libopenobex1 (1.5-2.1) ...
Removing libopenraw1:amd64 (0.0.9-3.4ubuntu1) ...
Purging configuration files for libopenraw1:amd64 (0.0.9-3.4ubuntu1) ...
Removing libopenrawgnome1:amd64 (0.0.9-3.4ubuntu1) ...
Purging configuration files for libopenrawgnome1:amd64 (0.0.9-3.4ubuntu1) ...
Removing libopenvg1-mesa:amd64 (10.1.3-0ubuntu0.6) ...
Purging configuration files for libopenvg1-mesa:amd64 (10.1.3-0ubuntu0.6) ...
Removing libosip2-10:amd64 (4.0.0-3ubuntu2) ...
Purging configuration files for libosip2-10:amd64 (4.0.0-3ubuntu2) ...
Removing libpanel-applet-4-0 (1:3.8.0-1ubuntu12.2) ...
Purging configuration files for libpanel-applet-4-0 (1:3.8.0-1ubuntu12.2) ...
Removing libpangomm-1.4-1:amd64 (2.34.0-1ubuntu1) ...
Purging configuration files for libpangomm-1.4-1:amd64 (2.34.0-1ubuntu1) ...
Removing libpangox-1.0-0:i386 (0.0.2-5) ...
Purging configuration files for libpangox-1.0-0:i386 (0.0.2-5) ...
Removing libpcrecpp0:amd64 (1:8.31-2ubuntu2.3) ...
Purging configuration files for libpcrecpp0:amd64 (1:8.31-2ubuntu2.3) ...
Removing libpimcommon4 (4:4.13.3-0ubuntu0.1) ...
Purging configuration files for libpimcommon4 (4:4.13.3-0ubuntu0.1) ...
Removing libplatform1:amd64 (1.0.10-1~trusty) ...
Purging configuration files for libplatform1:amd64 (1.0.10-1~trusty) ...
Removing libportsmf0:amd64 (0.1~svn20101010-4) ...
Purging configuration files for libportsmf0:amd64 (0.1~svn20101010-4) ...
Removing libppl13:amd64 (1:1.1-1ubuntu1) ...
Purging configuration files for libppl13:amd64 (1:1.1-1ubuntu1) ...
Removing libprojectm2 (2.1.0+dfsg-1build2) ...
Purging configuration files for libprojectm2 (2.1.0+dfsg-1build2) ...
Removing libprotobuf-lite8:amd64 (2.5.0-9ubuntu1) ...
Purging configuration files for libprotobuf-lite8:amd64 (2.5.0-9ubuntu1) ...
Removing libprotoc8:amd64 (2.5.0-9ubuntu1) ...
Purging configuration files for libprotoc8:amd64 (2.5.0-9ubuntu1) ...
Removing libproxy1:amd64 (0.4.11-0ubuntu4) ...
Purging configuration files for libproxy1:amd64 (0.4.11-0ubuntu4) ...
Removing libproxy1:i386 (0.4.11-0ubuntu4) ...
Purging configuration files for libproxy1:i386 (0.4.11-0ubuntu4) ...
Removing libpt2.10.10 (2.10.10~dfsg-4) ...
Purging configuration files for libpt2.10.10 (2.10.10~dfsg-4) ...
Removing libpython3.4:amd64 (3.4.3-1ubuntu1~14.04.3) ...
Purging configuration files for libpython3.4:amd64 (3.4.3-1ubuntu1~14.04.3) ...
Removing libpython3.4-minimal:amd64 (3.4.3-1ubuntu1~14.04.3) ...
Purging configuration files for libpython3.4-minimal:amd64 (3.4.3-1ubuntu1~14.04.3) ...
Removing libpyzy-1.0-0 (1.0.1-4) ...
Purging configuration files for libpyzy-1.0-0 (1.0.1-4) ...
Removing libqapt2 (2.1.70-0ubuntu4.2) ...
Purging configuration files for libqapt2 (2.1.70-0ubuntu4.2) ...
Removing libqapt2-runtime (2.1.70-0ubuntu4.2) ...
Purging configuration files for libqapt2-runtime (2.1.70-0ubuntu4.2) ...
Removing libqextserialport1:amd64 (1.2.0~rc1+git7-g3be3fbf-1) ...
Purging configuration files for libqextserialport1:amd64 (1.2.0~rc1+git7-g3be3fbf-1) ...
Removing libqoauth1 (1.0.1-2ubuntu4) ...
Purging configuration files for libqoauth1 (1.0.1-2ubuntu4) ...
Removing libqtlocation1:amd64 (1.2.0-3ubuntu5) ...
Purging configuration files for libqtlocation1:amd64 (1.2.0-3ubuntu5) ...
Removing libquazip0:amd64 (0.6.2-0ubuntu1) ...
Purging configuration files for libquazip0:amd64 (0.6.2-0ubuntu1) ...
Removing librpmsign1 (4.11.1-3ubuntu0.1) ...
Purging configuration files for librpmsign1 (4.11.1-3ubuntu0.1) ...
Removing librygel-core-2.0-1 (0.20.3-1ubuntu2) ...
Purging configuration files for librygel-core-2.0-1 (0.20.3-1ubuntu2) ...
Removing librygel-renderer-2.0-1 (0.20.3-1ubuntu2) ...
Purging configuration files for librygel-renderer-2.0-1 (0.20.3-1ubuntu2) ...
Removing librygel-renderer-gst-2.0-1 (0.20.3-1ubuntu2) ...
Purging configuration files for librygel-renderer-gst-2.0-1 (0.20.3-1ubuntu2) ...
Removing librygel-server-2.0-1 (0.20.3-1ubuntu2) ...
Purging configuration files for librygel-server-2.0-1 (0.20.3-1ubuntu2) ...
Removing libsendlater4 (4:4.13.3-0ubuntu0.1) ...
Purging configuration files for libsendlater4 (4:4.13.3-0ubuntu0.1) ...
Removing libshp1:amd64 (1.2.10-7) ...
Purging configuration files for libshp1:amd64 (1.2.10-7) ...
Removing libsidplay1 (1.36.59-5ubuntu1) ...
Purging configuration files for libsidplay1 (1.36.59-5ubuntu1) ...
Removing libsidplay2 (2.1.1-14) ...
Purging configuration files for libsidplay2 (2.1.1-14) ...
Removing libsidplayfp:amd64 (1.2.2-1) ...
Purging configuration files for libsidplayfp:amd64 (1.2.2-1) ...
Removing libsigc++-2.0-0c2a:amd64 (2.2.10-0.2ubuntu2) ...
Purging configuration files for libsigc++-2.0-0c2a:amd64 (2.2.10-0.2ubuntu2) ...
Removing libsmokebase3 (4:4.13.0-0ubuntu1) ...
Purging configuration files for libsmokebase3 (4:4.13.0-0ubuntu1) ...
Removing libsmokenepomuk3 (4:4.13.0-0ubuntu1) ...
Purging configuration files for libsmokenepomuk3 (4:4.13.0-0ubuntu1) ...
Removing libstreamanalyzer0 (0.7.8-1ubuntu2) ...
Purging configuration files for libstreamanalyzer0 (0.7.8-1ubuntu2) ...
Removing libstreams0 (0.7.8-1ubuntu2) ...
Purging configuration files for libstreams0 (0.7.8-1ubuntu2) ...
Removing libswscale2:amd64 (6:9.18-0ubuntu0.14.04.1+fdkaac) ...
Purging configuration files for libswscale2:amd64 (6:9.18-0ubuntu0.14.04.1+fdkaac) ...
Removing libtag1-vanilla:amd64 (1.10-0ubuntu1~trusty0) ...
Purging configuration files for libtag1-vanilla:amd64 (1.10-0ubuntu1~trusty0) ...
Removing libtag1-vanilla:i386 (1.10-0ubuntu1~trusty0) ...
Purging configuration files for libtag1-vanilla:i386 (1.10-0ubuntu1~trusty0) ...
Removing libtar0 (1.2.20-4) ...
Purging configuration files for libtar0 (1.2.20-4) ...
Removing libtemplateparser4 (4:4.13.3-0ubuntu0.1) ...
Purging configuration files for libtemplateparser4 (4:4.13.3-0ubuntu0.1) ...
Removing libtinyxml2-0.0.0:amd64 (0~git20120518.1.a2ae54e-1) ...
Purging configuration files for libtinyxml2-0.0.0:amd64 (0~git20120518.1.a2ae54e-1) ...
Removing libtinyxml2-2v5:amd64 (2.2.0-1.1ubuntu1) ...
Purging configuration files for libtinyxml2-2v5:amd64 (2.2.0-1.1ubuntu1) ...
Removing libtinyxml2.6.2:amd64 (2.6.2-2) ...
Purging configuration files for libtinyxml2.6.2:amd64 (2.6.2-2) ...
Removing libtracker-extract-0.16-0 (0.16.5-0ubuntu0.1) ...
Purging configuration files for libtracker-extract-0.16-0 (0.16.5-0ubuntu0.1) ...
Removing libtracker-miner-0.16-0 (0.16.5-0ubuntu0.1) ...
Purging configuration files for libtracker-miner-0.16-0 (0.16.5-0ubuntu0.1) ...
Removing libtracker-sparql-0.16-0 (0.16.5-0ubuntu0.1) ...
Purging configuration files for libtracker-sparql-0.16-0 (0.16.5-0ubuntu0.1) ...
Removing libts-0.0-0:amd64 (1.0-12) ...
Purging configuration files for libts-0.0-0:amd64 (1.0-12) ...
Removing libusageenvironment1 (2014.01.13-1) ...
Purging configuration files for libusageenvironment1 (2014.01.13-1) ...
Removing libvala-0.20-0:amd64 (0.20.1-2ubuntu5) ...
Purging configuration files for libvala-0.20-0:amd64 (0.20.1-2ubuntu5) ...
Removing libvamp-hostsdk3:amd64 (2.5+repack0-2) ...
Purging configuration files for libvamp-hostsdk3:amd64 (2.5+repack0-2) ...
Removing libvigraimpex5 (1.10.0+dfsg-3ubuntu2) ...
Purging configuration files for libvigraimpex5 (1.10.0+dfsg-3ubuntu2) ...
Removing libvlccore7 (2.1.4+git20150124+r54591+19+11~ubuntu14.04.1) ...
Purging configuration files for libvlccore7 (2.1.4+git20150124+r54591+19+11~ubuntu14.04.1) ...
Removing libvncclient0:amd64 (0.9.9+dfsg-6~ubuntu14.04.1~ppa1) ...
Purging configuration files for libvncclient0:amd64 (0.9.9+dfsg-6~ubuntu14.04.1~ppa1) ...
Removing libvncserver0:amd64 (0.9.9+dfsg-6~ubuntu14.04.1~ppa1) ...
Purging configuration files for libvncserver0:amd64 (0.9.9+dfsg-6~ubuntu14.04.1~ppa1) ...
Removing libvpx1:i386 (1.3.0-3~trusty) ...
Purging configuration files for libvpx1:i386 (1.3.0-3~trusty) ...
Removing libvtk5.8 (5.8.0-14.1ubuntu3) ...
Purging configuration files for libvtk5.8 (5.8.0-14.1ubuntu3) ...
Removing libwayland-egl1-mesa-lts-vivid:amd64 (10.5.9-2ubuntu1~trusty2) ...
Purging configuration files for libwayland-egl1-mesa-lts-vivid:amd64 (10.5.9-2ubuntu1~trusty2) ...
Removing libwcs4:amd64 (4.20-2) ...
Purging configuration files for libwcs4:amd64 (4.20-2) ...
Removing libwxbase3.0-0:amd64 (3.0.2-1~ppa1) ...
Purging configuration files for libwxbase3.0-0:amd64 (3.0.2-1~ppa1) ...
Removing libwxgtk3.0-0:amd64 (3.0.2-1~ppa1) ...
Purging configuration files for libwxgtk3.0-0:amd64 (3.0.2-1~ppa1) ...
Removing libx265-40 (1.4+222+hg5f9f7194267b-1~trusty) ...
Purging configuration files for libx265-40 (1.4+222+hg5f9f7194267b-1~trusty) ...
Removing libx265-49:amd64 (1.5+370-1~trusty1.1) ...
Purging configuration files for libx265-49:amd64 (1.5+370-1~trusty1.1) ...
Removing libx265-59:amd64 (1.7-1~trusty) ...
Purging configuration files for libx265-59:amd64 (1.7-1~trusty) ...
Removing libxapian22 (1.2.16-2ubuntu1) ...
Purging configuration files for libxapian22 (1.2.16-2ubuntu1) ...
Removing libxatracker2:amd64 (10.1.3-0ubuntu0.4) ...
Purging configuration files for libxatracker2:amd64 (10.1.3-0ubuntu0.4) ...
Removing libxatracker2-lts-vivid:amd64 (10.5.9-2ubuntu1~trusty2) ...
Purging configuration files for libxatracker2-lts-vivid:amd64 (10.5.9-2ubuntu1~trusty2) ...
Removing libxen-4.4 (4.4.2-0ubuntu0.14.04.5) ...
Purging configuration files for libxen-4.4 (4.4.2-0ubuntu0.14.04.5) ...
Removing libxft2:i386 (2.3.2-1) ...
Purging configuration files for libxft2:i386 (2.3.2-1) ...
Removing libyaml-cpp0.3:amd64 (0.3.0-1.1) ...
Purging configuration files for libyaml-cpp0.3:amd64 (0.3.0-1.1) ...
Removing libzlcore0.12 (0.12.10dfsg-9) ...
Purging configuration files for libzlcore0.12 (0.12.10dfsg-9) ...
Removing libzltext0.12 (0.12.10dfsg-9) ...
Purging configuration files for libzltext0.12 (0.12.10dfsg-9) ...
Removing linux-image-3.13.0-52-generic (3.13.0-52.86) ...
Purging configuration files for linux-image-3.13.0-52-generic (3.13.0-52.86) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-52-generic /boot/vmlinuz-3.13.0-52-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-52-generic /boot/vmlinuz-3.13.0-52-generic
Removing linux-image-3.13.0-53-generic (3.13.0-53.89) ...
Purging configuration files for linux-image-3.13.0-53-generic (3.13.0-53.89) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-53-generic /boot/vmlinuz-3.13.0-53-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-53-generic /boot/vmlinuz-3.13.0-53-generic
Removing linux-image-3.13.0-55-generic (3.13.0-55.94) ...
Purging configuration files for linux-image-3.13.0-55-generic (3.13.0-55.94) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-55-generic /boot/vmlinuz-3.13.0-55-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-55-generic /boot/vmlinuz-3.13.0-55-generic
Removing linux-image-3.13.0-58-generic (3.13.0-58.97) ...
Purging configuration files for linux-image-3.13.0-58-generic (3.13.0-58.97) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-58-generic /boot/vmlinuz-3.13.0-58-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-58-generic /boot/vmlinuz-3.13.0-58-generic
Removing linux-image-3.13.0-61-generic (3.13.0-61.100) ...
Purging configuration files for linux-image-3.13.0-61-generic (3.13.0-61.100) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-61-generic /boot/vmlinuz-3.13.0-61-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-61-generic /boot/vmlinuz-3.13.0-61-generic
Removing linux-image-3.13.0-64-generic (3.13.0-64.104) ...
Purging configuration files for linux-image-3.13.0-64-generic (3.13.0-64.104) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-64-generic /boot/vmlinuz-3.13.0-64-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-64-generic /boot/vmlinuz-3.13.0-64-generic
Removing linux-image-3.13.0-65-generic (3.13.0-65.106) ...
Purging configuration files for linux-image-3.13.0-65-generic (3.13.0-65.106) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-65-generic /boot/vmlinuz-3.13.0-65-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-65-generic /boot/vmlinuz-3.13.0-65-generic
Removing linux-image-3.13.0-66-generic (3.13.0-66.108) ...
Purging configuration files for linux-image-3.13.0-66-generic (3.13.0-66.108) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-66-generic /boot/vmlinuz-3.13.0-66-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-66-generic /boot/vmlinuz-3.13.0-66-generic
Removing linux-image-3.13.0-67-generic (3.13.0-67.110) ...
Purging configuration files for linux-image-3.13.0-67-generic (3.13.0-67.110) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-67-generic /boot/vmlinuz-3.13.0-67-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-67-generic /boot/vmlinuz-3.13.0-67-generic
Removing linux-image-3.13.0-70-generic (3.13.0-70.113) ...
Purging configuration files for linux-image-3.13.0-70-generic (3.13.0-70.113) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-70-generic /boot/vmlinuz-3.13.0-70-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-70-generic /boot/vmlinuz-3.13.0-70-generic
Removing linux-image-3.13.0-72-generic (3.13.0-72.115) ...
Purging configuration files for linux-image-3.13.0-72-generic (3.13.0-72.115) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-72-generic /boot/vmlinuz-3.13.0-72-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-72-generic /boot/vmlinuz-3.13.0-72-generic
Removing linux-image-3.13.0-73-generic (3.13.0-73.116) ...
Purging configuration files for linux-image-3.13.0-73-generic (3.13.0-73.116) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-73-generic /boot/vmlinuz-3.13.0-73-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-73-generic /boot/vmlinuz-3.13.0-73-generic
Removing linux-image-3.13.0-74-generic (3.13.0-74.118) ...
Purging configuration files for linux-image-3.13.0-74-generic (3.13.0-74.118) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-74-generic /boot/vmlinuz-3.13.0-74-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-74-generic /boot/vmlinuz-3.13.0-74-generic
Removing linux-image-3.13.0-77-generic (3.13.0-77.121) ...
Purging configuration files for linux-image-3.13.0-77-generic (3.13.0-77.121) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-77-generic /boot/vmlinuz-3.13.0-77-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-77-generic /boot/vmlinuz-3.13.0-77-generic
Removing linux-image-3.13.0-83-generic (3.13.0-83.127) ...
Purging configuration files for linux-image-3.13.0-83-generic (3.13.0-83.127) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-83-generic /boot/vmlinuz-3.13.0-83-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-83-generic /boot/vmlinuz-3.13.0-83-generic
Removing linux-image-3.13.0-85-generic (3.13.0-85.129) ...
Purging configuration files for linux-image-3.13.0-85-generic (3.13.0-85.129) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-85-generic /boot/vmlinuz-3.13.0-85-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-85-generic /boot/vmlinuz-3.13.0-85-generic
Removing linux-image-3.19.0-29-generic (3.19.0-29.31~14.04.1) ...
Purging configuration files for linux-image-3.19.0-29-generic (3.19.0-29.31~14.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-29-generic /boot/vmlinuz-3.19.0-29-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-29-generic /boot/vmlinuz-3.19.0-29-generic
Removing linux-image-3.19.0-30-generic (3.19.0-30.34~14.04.1) ...
Purging configuration files for linux-image-3.19.0-30-generic (3.19.0-30.34~14.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-30-generic /boot/vmlinuz-3.19.0-30-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-30-generic /boot/vmlinuz-3.19.0-30-generic
Removing linux-image-3.19.0-31-generic (3.19.0-31.36~14.04.1) ...
Purging configuration files for linux-image-3.19.0-31-generic (3.19.0-31.36~14.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-31-generic /boot/vmlinuz-3.19.0-31-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-31-generic /boot/vmlinuz-3.19.0-31-generic
Removing linux-image-3.19.0-32-generic (3.19.0-32.37~14.04.1) ...
Purging configuration files for linux-image-3.19.0-32-generic (3.19.0-32.37~14.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-32-generic /boot/vmlinuz-3.19.0-32-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-32-generic /boot/vmlinuz-3.19.0-32-generic
Removing linux-image-3.19.0-36-generic (3.19.0-36.41~14.04.1) ...
Purging configuration files for linux-image-3.19.0-36-generic (3.19.0-36.41~14.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-36-generic /boot/vmlinuz-3.19.0-36-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-36-generic /boot/vmlinuz-3.19.0-36-generic
Removing linux-image-3.19.0-37-generic (3.19.0-37.42~14.04.1) ...
Purging configuration files for linux-image-3.19.0-37-generic (3.19.0-37.42~14.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-37-generic /boot/vmlinuz-3.19.0-37-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-37-generic /boot/vmlinuz-3.19.0-37-generic
Removing linux-image-3.19.0-39-generic (3.19.0-39.44~14.04.1) ...
Purging configuration files for linux-image-3.19.0-39-generic (3.19.0-39.44~14.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-39-generic /boot/vmlinuz-3.19.0-39-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-39-generic /boot/vmlinuz-3.19.0-39-generic
Removing linux-image-3.19.0-41-generic (3.19.0-41.46~14.04.2) ...
Purging configuration files for linux-image-3.19.0-41-generic (3.19.0-41.46~14.04.2) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-41-generic /boot/vmlinuz-3.19.0-41-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-41-generic /boot/vmlinuz-3.19.0-41-generic
Removing linux-image-3.19.0-42-generic (3.19.0-42.48~14.04.1) ...
Purging configuration files for linux-image-3.19.0-42-generic (3.19.0-42.48~14.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-42-generic /boot/vmlinuz-3.19.0-42-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-42-generic /boot/vmlinuz-3.19.0-42-generic
Removing linux-image-3.19.0-49-generic (3.19.0-49.55~14.04.1) ...
Purging configuration files for linux-image-3.19.0-49-generic (3.19.0-49.55~14.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-49-generic /boot/vmlinuz-3.19.0-49-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-49-generic /boot/vmlinuz-3.19.0-49-generic
Removing linux-image-3.19.0-56-generic (3.19.0-56.62~14.04.1) ...
Purging configuration files for linux-image-3.19.0-56-generic (3.19.0-56.62~14.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-56-generic /boot/vmlinuz-3.19.0-56-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-56-generic /boot/vmlinuz-3.19.0-56-generic
Removing linux-image-extra-3.13.0-52-generic (3.13.0-52.86) ...
Purging configuration files for linux-image-extra-3.13.0-52-generic (3.13.0-52.86) ...
Removing linux-image-extra-3.13.0-53-generic (3.13.0-53.89) ...
Purging configuration files for linux-image-extra-3.13.0-53-generic (3.13.0-53.89) ...
Removing linux-image-extra-3.13.0-54-generic (3.13.0-54.91) ...
Purging configuration files for linux-image-extra-3.13.0-54-generic (3.13.0-54.91) ...
Removing linux-image-extra-3.13.0-55-generic (3.13.0-55.94) ...
Purging configuration files for linux-image-extra-3.13.0-55-generic (3.13.0-55.94) ...
Removing linux-image-extra-3.13.0-58-generic (3.13.0-58.97) ...
Purging configuration files for linux-image-extra-3.13.0-58-generic (3.13.0-58.97) ...
Removing linux-image-extra-3.13.0-61-generic (3.13.0-61.100) ...
Purging configuration files for linux-image-extra-3.13.0-61-generic (3.13.0-61.100) ...
Removing linux-image-extra-3.13.0-64-generic (3.13.0-64.104) ...
Purging configuration files for linux-image-extra-3.13.0-64-generic (3.13.0-64.104) ...
Removing linux-image-extra-3.13.0-65-generic (3.13.0-65.106) ...
Purging configuration files for linux-image-extra-3.13.0-65-generic (3.13.0-65.106) ...
Removing linux-image-extra-3.13.0-66-generic (3.13.0-66.108) ...
Purging configuration files for linux-image-extra-3.13.0-66-generic (3.13.0-66.108) ...
Removing linux-image-extra-3.13.0-67-generic (3.13.0-67.110) ...
Purging configuration files for linux-image-extra-3.13.0-67-generic (3.13.0-67.110) ...
Removing linux-image-extra-3.13.0-70-generic (3.13.0-70.113) ...
Purging configuration files for linux-image-extra-3.13.0-70-generic (3.13.0-70.113) ...
Removing linux-image-extra-3.13.0-72-generic (3.13.0-72.115) ...
Purging configuration files for linux-image-extra-3.13.0-72-generic (3.13.0-72.115) ...
Removing linux-image-extra-3.13.0-73-generic (3.13.0-73.116) ...
Purging configuration files for linux-image-extra-3.13.0-73-generic (3.13.0-73.116) ...
Removing linux-image-extra-3.13.0-74-generic (3.13.0-74.118) ...
Purging configuration files for linux-image-extra-3.13.0-74-generic (3.13.0-74.118) ...
Removing linux-image-extra-3.13.0-77-generic (3.13.0-77.121) ...
Purging configuration files for linux-image-extra-3.13.0-77-generic (3.13.0-77.121) ...
Removing linux-image-extra-3.13.0-83-generic (3.13.0-83.127) ...
Purging configuration files for linux-image-extra-3.13.0-83-generic (3.13.0-83.127) ...
Removing linux-image-extra-3.13.0-85-generic (3.13.0-85.129) ...
Purging configuration files for linux-image-extra-3.13.0-85-generic (3.13.0-85.129) ...
Removing linux-image-extra-3.19.0-29-generic (3.19.0-29.31~14.04.1) ...
Purging configuration files for linux-image-extra-3.19.0-29-generic (3.19.0-29.31~14.04.1) ...
Removing linux-image-extra-3.19.0-30-generic (3.19.0-30.34~14.04.1) ...
Purging configuration files for linux-image-extra-3.19.0-30-generic (3.19.0-30.34~14.04.1) ...
Removing linux-image-extra-3.19.0-31-generic (3.19.0-31.36~14.04.1) ...
Purging configuration files for linux-image-extra-3.19.0-31-generic (3.19.0-31.36~14.04.1) ...
Removing linux-image-extra-3.19.0-32-generic (3.19.0-32.37~14.04.1) ...
Purging configuration files for linux-image-extra-3.19.0-32-generic (3.19.0-32.37~14.04.1) ...
Removing linux-image-extra-3.19.0-36-generic (3.19.0-36.41~14.04.1) ...
Purging configuration files for linux-image-extra-3.19.0-36-generic (3.19.0-36.41~14.04.1) ...
Removing linux-image-extra-3.19.0-37-generic (3.19.0-37.42~14.04.1) ...
Purging configuration files for linux-image-extra-3.19.0-37-generic (3.19.0-37.42~14.04.1) ...
Removing linux-image-extra-3.19.0-39-generic (3.19.0-39.44~14.04.1) ...
Purging configuration files for linux-image-extra-3.19.0-39-generic (3.19.0-39.44~14.04.1) ...
Removing linux-image-extra-3.19.0-41-generic (3.19.0-41.46~14.04.2) ...
Purging configuration files for linux-image-extra-3.19.0-41-generic (3.19.0-41.46~14.04.2) ...
Removing linux-image-extra-3.19.0-42-generic (3.19.0-42.48~14.04.1) ...
Purging configuration files for linux-image-extra-3.19.0-42-generic (3.19.0-42.48~14.04.1) ...
Removing linux-image-extra-3.19.0-49-generic (3.19.0-49.55~14.04.1) ...
Purging configuration files for linux-image-extra-3.19.0-49-generic (3.19.0-49.55~14.04.1) ...
Removing linux-image-extra-3.19.0-56-generic (3.19.0-56.62~14.04.1) ...
Purging configuration files for linux-image-extra-3.19.0-56-generic (3.19.0-56.62~14.04.1) ...
Removing luatex (0.76.0-3ubuntu1) ...
Purging configuration files for luatex (0.76.0-3ubuntu1) ...
Removing mate-applets (1.12.1-1) ...
Purging configuration files for mate-applets (1.12.1-1) ...
Removing mate-control-center (1.12.1-2) ...
Purging configuration files for mate-control-center (1.12.1-2) ...
Removing mate-icon-theme (1.12.0-1) ...
Purging configuration files for mate-icon-theme (1.12.0-1) ...
Removing mate-media-common (1.12.1-1) ...
Purging configuration files for mate-media-common (1.12.1-1) ...
Removing mate-menus (1.12.0-1) ...
Purging configuration files for mate-menus (1.12.0-1) ...
Removing mate-polkit-common (1.12.0-3) ...
Purging configuration files for mate-polkit-common (1.12.0-3) ...
Removing mate-power-manager (1.12.1-1) ...
Purging configuration files for mate-power-manager (1.12.1-1) ...
Removing mate-screensaver (1.12.0-1) ...
Purging configuration files for mate-screensaver (1.12.0-1) ...
Removing mate-screensaver-common (1.12.0-1) ...
Purging configuration files for mate-screensaver-common (1.12.0-1) ...
Removing mate-session-manager (1.12.2-1) ...
Purging configuration files for mate-session-manager (1.12.2-1) ...
Removing mate-settings-daemon (1.12.1-2build1) ...
Purging configuration files for mate-settings-daemon (1.12.1-2build1) ...
Removing mate-settings-daemon-common (1.12.1-2build1) ...
Purging configuration files for mate-settings-daemon-common (1.12.1-2build1) ...
Removing mate-themes (1.12.2+gtk3.18-1) ...
Purging configuration files for mate-themes (1.12.2+gtk3.18-1) ...
Removing menu-xdg (0.5) ...
Purging configuration files for menu-xdg (0.5) ...
Removing mysql-server-5.5 (5.5.49-0ubuntu0.14.04.1) ...
Purging configuration files for mysql-server-5.5 (5.5.49-0ubuntu0.14.04.1) ...
Removing nepomuk-core-data (4:4.13.3-0ubuntu0.2) ...
Purging configuration files for nepomuk-core-data (4:4.13.3-0ubuntu0.2) ...
Removing onboard (1.0.1-0ubuntu1) ...
Purging configuration files for onboard (1.0.1-0ubuntu1) ...
Removing openjdk-6-jre-headless:amd64 (6b38-1.13.10-0ubuntu0.14.04.1) ...
Purging configuration files for openjdk-6-jre-headless:amd64 (6b38-1.13.10-0ubuntu0.14.04.1) ...
Removing openjdk-7-jre-headless:amd64 (7u95-2.6.4-0ubuntu0.14.04.2) ...
Purging configuration files for openjdk-7-jre-headless:amd64 (7u95-2.6.4-0ubuntu0.14.04.2) ...
Removing overlay-scrollbar-gtk3:amd64 (0.2.16+r359+14.04.20131129-0ubuntu1) ...
Purging configuration files for overlay-scrollbar-gtk3:amd64 (0.2.16+r359+14.04.20131129-0ubuntu1) ...
Removing perl-modules (5.18.2-2ubuntu1.1) ...
Purging configuration files for perl-modules (5.18.2-2ubuntu1.1) ...
Removing php5-cli (5.5.9+dfsg-1ubuntu4.16) ...
Purging configuration files for php5-cli (5.5.9+dfsg-1ubuntu4.16) ...
Removing php5-readline (5.5.9+dfsg-1ubuntu4.16) ...
Purging configuration files for php5-readline (5.5.9+dfsg-1ubuntu4.16) ...
Removing python-cupshelpers (1.4.3+20140219-0ubuntu2.6) ...
Purging configuration files for python-cupshelpers (1.4.3+20140219-0ubuntu2.6) ...
Removing python-kwwidgets (1.0.0~cvs20100930-8) ...
Purging configuration files for python-kwwidgets (1.0.0~cvs20100930-8) ...
Removing python3.4 (3.4.3-1ubuntu1~14.04.3) ...
Purging configuration files for python3.4 (3.4.3-1ubuntu1~14.04.3) ...
Removing python3.4-minimal (3.4.3-1ubuntu1~14.04.3) ...
Purging configuration files for python3.4-minimal (3.4.3-1ubuntu1~14.04.3) ...
Removing rygel (0.28.3-1) ...
Purging configuration files for rygel (0.28.3-1) ...
Removing skype-wrapper (0ubuntu6.5.2~trusty0) ...
Purging configuration files for skype-wrapper (0ubuntu6.5.2~trusty0) ...
Removing systemd-services (204-5ubuntu20.19) ...
Purging configuration files for systemd-services (204-5ubuntu20.19) ...
Removing tracker-miner-fs (0.16.5-0ubuntu0.1) ...
Purging configuration files for tracker-miner-fs (0.16.5-0ubuntu0.1) ...
Removing tsconf (1.0-12) ...
Purging configuration files for tsconf (1.0-12) ...
Removing ttf-punjabi-fonts (1:0.5.14ubuntu1) ...
Purging configuration files for ttf-punjabi-fonts (1:0.5.14ubuntu1) ...
Removing ubuntu-core-launcher (2.22.3) ...
Purging configuration files for ubuntu-core-launcher (2.22.3) ...
Removing ubuntu-mate-default-settings (16.04.5) ...
Purging configuration files for ubuntu-mate-default-settings (16.04.5) ...
Removing webaccounts-extension-common (0.5-0ubuntu2.14.04.1) ...
Purging configuration files for webaccounts-extension-common (0.5-0ubuntu2.14.04.1) ...
Removing wine1.6 (1:1.6.2-0ubuntu14) ...
Purging configuration files for wine1.6 (1:1.6.2-0ubuntu14) ...
Removing wxmp3val (3.7~ppa1~trusty) ...
Purging configuration files for wxmp3val (3.7~ppa1~trusty) ...
Removing xchat (2.8.8-7.1ubuntu5.1) ...
Purging configuration files for xchat (2.8.8-7.1ubuntu5.1) ...
Removing xserver-xorg-core-lts-vivid (2:1.17.1-0ubuntu3.1~trusty1) ...
Purging configuration files for xserver-xorg-core-lts-vivid (2:1.17.1-0ubuntu3.1~trusty1) ...
Removing xserver-xorg-lts-vivid (1:7.7+7ubuntu3~trusty1) ...
Purging configuration files for xserver-xorg-lts-vivid (1:7.7+7ubuntu3~trusty1) ...
Removing xserver-xorg-video-intel-lts-vivid (2:2.99.917-1~exp1ubuntu2.2~trusty1) ...
Purging configuration files for xserver-xorg-video-intel-lts-vivid (2:2.99.917-1~exp1ubuntu2.2~trusty1) ...
Removing xserver-xorg-video-openchrome-lts-vivid (1:0.3.3-1ubuntu1~trusty1) ...
Purging configuration files for xserver-xorg-video-openchrome-lts-vivid (1:0.3.3-1ubuntu1~trusty1) ...
Removing xserver-xorg-video-vmware (1:13.0.2-2ubuntu1) ...
Purging configuration files for xserver-xorg-video-vmware (1:13.0.2-2ubuntu1) ...
Removing xserver-xorg-video-vmware-lts-vivid (1:13.1.0-0ubuntu1build1~trusty1) ...
Purging configuration files for xserver-xorg-video-vmware-lts-vivid (1:13.1.0-0ubuntu1build1~trusty1) ...
Processing triggers for menu (2.1.47ubuntu1) ...
Processing triggers for libc-bin (2.23-0ubuntu5) ...

:~$ dpkg -l | grep linux-
ii  ladspa-sdk                                                  1.13-2                                        amd64        sample tools for linux-audio-dev plugin architecture
ii  linux-base                                                  4.0ubuntu1                                    all          Linux image base package
ii  linux-firmware                                              1.157.8                                       all          Firmware for Linux kernel drivers
iU  linux-generic                                               4.4.0.66.70                                   amd64        Complete Generic Linux kernel and headers
iU  linux-generic-lts-vivid                                     4.4.0.66.70                                   amd64        Complete Generic Linux kernel and headers (dummy transitional package)
ii  linux-headers-3.13.0-54                                     3.13.0-54.91                                  all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-54-generic                             3.13.0-54.91                                  amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-57                                     3.13.0-57.95                                  all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-57-generic                             3.13.0-57.95                                  amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-59                                     3.13.0-59.98                                  all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-59-generic                             3.13.0-59.98                                  amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-62                                     3.13.0-62.102                                 all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-62-generic                             3.13.0-62.102                                 amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-63                                     3.13.0-63.103                                 all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-63-generic                             3.13.0-63.103                                 amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-79                                     3.13.0-79.123                                 all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-79-generic                             3.13.0-79.123                                 amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-51                                     3.19.0-51.58~14.04.1                          all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-51-generic                             3.19.0-51.58~14.04.1                          amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-21                                      4.4.0-21.37                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-21-generic                              4.4.0-21.37                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-22                                      4.4.0-22.40                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-22-generic                              4.4.0-22.40                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-64                                      4.4.0-64.85                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-64-generic                              4.4.0-64.85                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-66                                      4.4.0-66.87                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-66-generic                              4.4.0-66.87                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.6.0-040600                                  4.6.0-040600.201605151930                     all          Header files related to Linux kernel version 4.6.0
ii  linux-headers-4.6.0-040600rc3                               4.6.0-040600rc3.201604120934                  all          Header files related to Linux kernel version 4.6.0
ii  linux-headers-4.6.0-040600rc3-generic                       4.6.0-040600rc3.201604120934                  amd64        Linux kernel headers for version 4.6.0 on 64 bit x86 SMP
ii  linux-headers-generic                                       4.4.0.66.70                                   amd64        Generic Linux kernel headers
rH  linux-image-3.13.0-54-generic                               3.13.0-54.91                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rH  linux-image-3.13.0-57-generic                               3.13.0-57.95                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rH  linux-image-3.13.0-59-generic                               3.13.0-59.98                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rH  linux-image-3.13.0-62-generic                               3.13.0-62.102                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rH  linux-image-3.13.0-63-generic                               3.13.0-63.103                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rH  linux-image-3.13.0-79-generic                               3.13.0-79.123                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rH  linux-image-3.19.0-51-generic                               3.19.0-51.58~14.04.1                          amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rH  linux-image-3.19.0-58-generic                               3.19.0-58.64~14.04.1                          amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-21-generic                                4.4.0-21.37                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
iF  linux-image-4.4.0-22-generic                                4.4.0-22.40                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
iF  linux-image-4.4.0-64-generic                                4.4.0-64.85                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
iF  linux-image-4.4.0-66-generic                                4.4.0-66.87                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-4.6.0-040600-generic                            4.6.0-040600.201605151930                     amd64        Linux kernel image for version 4.6.0 on 64 bit x86 SMP
rH  linux-image-4.6.0-040600rc3-generic                         4.6.0-040600rc3.201604120934                  amd64        Linux kernel image for version 4.6.0 on 64 bit x86 SMP
rH  linux-image-extra-3.13.0-57-generic                         3.13.0-57.95                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rH  linux-image-extra-3.13.0-59-generic                         3.13.0-59.98                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rH  linux-image-extra-3.13.0-62-generic                         3.13.0-62.102                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rH  linux-image-extra-3.13.0-63-generic                         3.13.0-63.103                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rH  linux-image-extra-3.13.0-79-generic                         3.13.0-79.123                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rH  linux-image-extra-3.19.0-51-generic                         3.19.0-51.58~14.04.1                          amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rH  linux-image-extra-3.19.0-58-generic                         3.19.0-58.64~14.04.1                          amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-21-generic                          4.4.0-21.37                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-extra-4.4.0-22-generic                          4.4.0-22.40                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-extra-4.4.0-64-generic                          4.4.0-64.85                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-extra-4.4.0-66-generic                          4.4.0-66.87                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-generic                                         4.4.0.66.70                                   amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                        4.4.0-67.88                                   amd64        Linux Kernel Headers for development
ii  linux-lts-vivid-tools-common                                3.19.0-18.18~14.04.1                          all          Linux kernel version specific tools for version 3.19.0
ii  linux-sound-base                                            1.0.25+dfsg-0ubuntu5                          all          base package for ALSA and OSS sound systems
ii  syslinux-common                                             3:6.03+dfsg-11ubuntu1                         all          collection of bootloaders (common)
ii  syslinux-legacy                                             2:3.63+dfsg-2ubuntu8                          amd64        Bootloader for Linux/i386 using MS-DOS floppies

~$ ls -al /boot/
total 203852
drwxr-xr-x  4 root root    12288 Mar 18 16:30 .
drwxr-xr-x 26 root root     4096 Mar 18 16:30 ..
-rw-r--r--  1 root root  1239577 Apr 19  2016 abi-4.4.0-21-generic
-rw-r--r--  1 root root  1239612 May 13  2016 abi-4.4.0-22-generic
-rw-r--r--  1 root root  1245512 Feb 20 14:40 abi-4.4.0-64-generic
-rw-r--r--  1 root root  1245512 Mar  3 19:25 abi-4.4.0-66-generic
-rw-r--r--  1 root root   189412 Apr 19  2016 config-4.4.0-21-generic
-rw-r--r--  1 root root   189520 May 13  2016 config-4.4.0-22-generic
-rw-r--r--  1 root root   190247 Feb 20 14:40 config-4.4.0-64-generic
-rw-r--r--  1 root root   190247 Mar  3 19:25 config-4.4.0-66-generic
drwxr-xr-x  6 root root     4096 Mar 18 16:30 grub
drwxr-xr-x  5 root root     4096 May  9  2016 grub.bak
-rw-r--r--  1 root root 39406840 Feb 22 06:57 initrd.img-4.4.0-21-generic
-rw-r--r--  1 root root 39407057 Mar 18 16:30 initrd.img-4.4.0-22-generic
-rw-r--r--  1 root root 39943328 Mar 18 16:30 initrd.img-4.4.0-64-generic
-rw-r--r--  1 root root 39944648 Mar 18 16:30 initrd.img-4.4.0-66-generic
-rw-r--r--  1 root root   182704 Jan 28  2016 memtest86+.bin
-rw-r--r--  1 root root   184380 Jan 28  2016 memtest86+.elf
-rw-r--r--  1 root root   184840 Jan 28  2016 memtest86+_multiboot.bin
-rw-------  1 root root  3853719 Apr 19  2016 System.map-4.4.0-21-generic
-rw-------  1 root root  3855781 May 13  2016 System.map-4.4.0-22-generic
-rw-------  1 root root  3883990 Feb 20 14:40 System.map-4.4.0-64-generic
-rw-------  1 root root  3883990 Mar  3 19:25 System.map-4.4.0-66-generic
-rw-------  1 root root  7013968 Apr 19  2016 vmlinuz-4.4.0-21-generic
-rw-------  1 root root  7015440 May 13  2016 vmlinuz-4.4.0-22-generic
-rw-------  1 root root  7087152 Feb 20 14:40 vmlinuz-4.4.0-64-generic
-rw-------  1 root root  7087024 Mar  3 19:25 vmlinuz-4.4.0-66-generic

~$ lsb_release -a
LSB Version:    core-9.20160110ubuntu0.2-amd64:core-9.20160110ubuntu0.2-noarch:security-9.20160110ubuntu0.2-amd64:security-9.20160110ubuntu0.2-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:    16.04
Codename:    xenial

~$ uname -r
4.4.0-21-generic

```

---

### Post by crazybear on 2017-03-21
> **ajgreeny said:**
> Interesting find Impavidus, and you may be right.

@crazybear
I wonder if it is worth using command ```
sudo apt-get purge grub*
``` then reinstalling all the packages that are removed when running that command, probably 5 or 6 of them but it will depend on whether you have UEFI or BIOS as to which are removed and then reinstalled.

I have never used grub-customiser as all it can do is also possible without it, so I have no idea about its abilities nor how likely it is to affect the situation as suggested by Impavidus.

Ah, do I really want to remove grub? and whatever it will uninstall with it? Will I be able to just re-install each item removed without having to resort to a grub-rescue disk? I'll at least wait to see what damage, if any, I've done with the terminal 'move' posted above, before I try this. I had a LOT deleted and want to move slowly here, least I have to totally re-install 16.04 - which was not a lot of fun nor as simple as 'people say' by a LOOOOOOOONNNNG shot.

---

### Post by crazybear on 2017-03-21
I just ran 
sudo dpkg --configure -a

and I got [at the end]:

```


Errors were encountered while processing:
 linux-image-4.4.0-22-generic
 plymouth-theme-ubuntu-gnome-logo
 grub-pc
 linux-image-4.4.0-66-generic
 linux-image-generic
 linux-image-4.4.0-64-generic
 linux-image-extra-4.4.0-22-generic
 linux-image-extra-4.4.0-64-generic
 linux-image-extra-4.4.0-66-generic
 linux-generic
 linux-generic-lts-vivid

```

What to do now?!

---

### Post by crazybear on 2017-03-21
I tried in synaptic to re-install grub-pc, but it can not because of the 17(?) linux-images it can't uninstall that it says it needs to....I'm still at the initial problem....I can't do much because of the 'stuck' unremovable or partly-instlaled images.

---

### Post by Bashing-om on 2017-03-21
crazybear; Hey;

Looking much cleaner now ,
However we still have this sloppyation:
> 
iU  linux-generic
iU  linux-image-generic

where the 'iU' means : i is the desired state (installed) and U is unpacked but not configured . We must at some point get these fully installed.

And this has to go as it is End_Of_Life:
> 
iU  linux-generic-lts-[color=red]vivid[/color]

And requiring attention is all these files marked :
> 
rH  linux-image-3.13.0-54-generic 

where here the r is removed and the H means Half installed . need to get rid of all the old remnants - some how !

At this point may be easier to remove manually, breaking the package manager real bad . Once all kernel files are consistent we then have the package manager "heal it's self ' . Now that is my opinion !

Were me I would look at :
```

ls -al /usr/src/
ls -al /lib/modules/
ls -al /boot/
dpkg -l | grep linux

```
Make these directories all agree, re-install  linux-generic and inux-image-generic ( if we can at this point )  . Then heal the package manager .

[INDENT][INDENT]make sense ?
[/INDENT][/INDENT]

---

### Post by ajgreeny on 2017-03-21
> **crazybear said:**
> Ah, do I really want to remove grub? and whatever it will uninstall with it? Will I be able to just re-install each item removed without having to resort to a grub-rescue disk? I'll at least wait to see what damage, if any, I've done with the terminal 'move' posted above, before I try this. I had a LOT deleted and want to move slowly here, least I have to totally re-install 16.04 - which was not a lot of fun nor as simple as 'people say' by a LOOOOOOOONNNNG shot.
You will be fine if you make sure you first run the command to purge the grub packages in your system and then immediately, ie, without shutting down, (or you would be in trouble), install all the packages that you just removed.  The terminal will tell you the names of those removed so you can just copy those back into an install command.

What I am hoping will happen is that the purging command will remove all configurations that may be causing that error noticed by impavidus, and we can then reinstall all the grub packages with new configuration.

Keep your fingers crossed!
If none of this helps I am beginning to wonder if the easiest way out of your problem might be a reinstallation of the OS; it looks as if you may have updated distro version a couple of times already which may be why you appear to have so many errant and unwanted kernels, so a clean reinstallation my give you a clean start.

---

### Post by crazybear on 2017-03-23
> **Bashing-om said:**
> crazybear; Hey;

Looking much cleaner now ,
However we still have this sloppyation:

where the 'iU' means : i is the desired state (installed) and U is unpacked but not configured . We must at some point get these fully installed.

And this has to go as it is End_Of_Life:

And requiring attention is all these files marked :

where here the r is removed and the H means Half installed . need to get rid of all the old remnants - some how !

At this point may be easier to remove manually, breaking the package manager real bad . Once all kernel files are consistent we then have the package manager "heal it's self ' . Now that is my opinion !

Were me I would look at :
```

ls -al /usr/src/
ls -al /lib/modules/
ls -al /boot/
dpkg -l | grep linux

```
Make these directories all agree, re-install  linux-generic and inux-image-generic ( if we can at this point )  . Then heal the package manager .
[INDENT][INDENT]make sense ?
[/INDENT]
[/INDENT]


Yes, makes sense. To my untrained they don't agree. I still see iU and rH entries for the last query:

```

~$ ls -al /usr/src/
total 120
drwxr-xr-x 30 root root 4096 Mar 21 20:45 .
drwxr-xr-x 14 root root 4096 Apr 28  2016 ..
drwxr-xr-x  3 root root 4096 May 15  2016 libdvd-pkg
drwxr-xr-x 24 root root 4096 Jun  7  2015 linux-headers-3.13.0-54
drwxr-xr-x  7 root root 4096 Jun  7  2015 linux-headers-3.13.0-54-generic
drwxr-xr-x 24 root root 4096 Jun 25  2015 linux-headers-3.13.0-57
drwxr-xr-x  7 root root 4096 Jun 25  2015 linux-headers-3.13.0-57-generic
drwxr-xr-x 24 root root 4096 Jul 30  2015 linux-headers-3.13.0-59
drwxr-xr-x  7 root root 4096 Jul 30  2015 linux-headers-3.13.0-59-generic
drwxr-xr-x 24 root root 4096 Aug 13  2015 linux-headers-3.13.0-62
drwxr-xr-x  7 root root 4096 Aug 13  2015 linux-headers-3.13.0-62-generic
drwxr-xr-x 24 root root 4096 Aug 19  2015 linux-headers-3.13.0-63
drwxr-xr-x  7 root root 4096 Aug 19  2015 linux-headers-3.13.0-63-generic
drwxr-xr-x 24 root root 4096 Mar 11  2016 linux-headers-3.13.0-79
drwxr-xr-x  7 root root 4096 Mar 11  2016 linux-headers-3.13.0-79-generic
drwxr-xr-x 24 root root 4096 Mar 11  2016 linux-headers-3.19.0-51
drwxr-xr-x  7 root root 4096 Mar 11  2016 linux-headers-3.19.0-51-generic
drwxr-xr-x 27 root root 4096 Apr 28  2016 linux-headers-4.4.0-21
drwxr-xr-x  7 root root 4096 Apr 28  2016 linux-headers-4.4.0-21-generic
drwxr-xr-x 27 root root 4096 May 18  2016 linux-headers-4.4.0-22
drwxr-xr-x  7 root root 4096 May 18  2016 linux-headers-4.4.0-22-generic
drwxr-xr-x 27 root root 4096 Feb 22 06:42 linux-headers-4.4.0-64
drwxr-xr-x  7 root root 4096 Feb 22 06:42 linux-headers-4.4.0-64-generic
drwxr-xr-x 27 root root 4096 Mar 16 21:08 linux-headers-4.4.0-66
drwxr-xr-x  7 root root 4096 Mar 16 21:08 linux-headers-4.4.0-66-generic
drwxr-xr-x 24 root root 4096 May 26  2016 linux-headers-4.6.0-040600
drwxr-xr-x 24 root root 4096 May 26  2016 linux-headers-4.6.0-040600rc3
drwxr-xr-x  8 root root 4096 May 26  2016 linux-headers-4.6.0-040600rc3-generic
drwxr-xr-x  6 root root 4096 Mar 21 20:45 oem-audio-hda-daily-lts-xenial-0.201703210732~ubuntu16.04.1
drwxr-xr-x 12 root root 4096 Feb 22 06:45 virtualbox-5.0.32


:~$ ls -al /lib/modules/
total 56
drwxr-xr-x 14 root root 4096 Mar 16 21:08 .
drwxr-xr-x 30 root root 4096 Mar 21 20:44 ..
drwxr-xr-x  2 root root 4096 Mar 17 06:17 3.13.0-54-generic
drwxr-xr-x  3 root root 4096 Mar 17 15:17 3.13.0-57-generic
drwxr-xr-x  3 root root 4096 Mar 17 15:18 3.13.0-59-generic
drwxr-xr-x  3 root root 4096 Mar 17 15:18 3.13.0-62-generic
drwxr-xr-x  3 root root 4096 Mar 17 15:19 3.13.0-63-generic
drwxr-xr-x  3 root root 4096 Mar 17 15:20 3.13.0-79-generic
drwxr-xr-x  3 root root 4096 Mar 17 15:21 3.19.0-51-generic
drwxr-xr-x  6 root root 4096 Mar 21 20:47 4.4.0-21-generic
drwxr-xr-x  6 root root 4096 Mar 21 21:13 4.4.0-22-generic
drwxr-xr-x  6 root root 4096 Mar 21 21:13 4.4.0-64-generic
drwxr-xr-x  6 root root 4096 Mar 21 21:13 4.4.0-66-generic
drwxr-xr-x  2 root root 4096 Jun  8  2016 4.6.0-040600rc3-generic


:~$ ls -al /boot/
total 203860
drwxr-xr-x  4 root root    12288 Mar 21 21:14 .
drwxr-xr-x 26 root root     4096 Mar 21 21:13 ..
-rw-r--r--  1 root root  1239577 Apr 19  2016 abi-4.4.0-21-generic
-rw-r--r--  1 root root  1239612 May 13  2016 abi-4.4.0-22-generic
-rw-r--r--  1 root root  1245512 Feb 20 14:40 abi-4.4.0-64-generic
-rw-r--r--  1 root root  1245512 Mar  3 19:25 abi-4.4.0-66-generic
-rw-r--r--  1 root root   189412 Apr 19  2016 config-4.4.0-21-generic
-rw-r--r--  1 root root   189520 May 13  2016 config-4.4.0-22-generic
-rw-r--r--  1 root root   190247 Feb 20 14:40 config-4.4.0-64-generic
-rw-r--r--  1 root root   190247 Mar  3 19:25 config-4.4.0-66-generic
drwxr-xr-x  6 root root     4096 Mar 21 21:13 grub
drwxr-xr-x  5 root root     4096 May  9  2016 grub.bak
-rw-r--r--  1 root root 39406840 Feb 22 06:57 initrd.img-4.4.0-21-generic
-rw-r--r--  1 root root 39408251 Mar 21 21:13 initrd.img-4.4.0-22-generic
-rw-r--r--  1 root root 39945705 Mar 21 21:13 initrd.img-4.4.0-64-generic
-rw-r--r--  1 root root 39944727 Mar 21 21:14 initrd.img-4.4.0-66-generic
-rw-r--r--  1 root root   182704 Jan 28  2016 memtest86+.bin
-rw-r--r--  1 root root   184380 Jan 28  2016 memtest86+.elf
-rw-r--r--  1 root root   184840 Jan 28  2016 memtest86+_multiboot.bin
-rw-------  1 root root  3853719 Apr 19  2016 System.map-4.4.0-21-generic
-rw-------  1 root root  3855781 May 13  2016 System.map-4.4.0-22-generic
-rw-------  1 root root  3883990 Feb 20 14:40 System.map-4.4.0-64-generic
-rw-------  1 root root  3883990 Mar  3 19:25 System.map-4.4.0-66-generic
-rw-------  1 root root  7013968 Apr 19  2016 vmlinuz-4.4.0-21-generic
-rw-------  1 root root  7015440 May 13  2016 vmlinuz-4.4.0-22-generic
-rw-------  1 root root  7087152 Feb 20 14:40 vmlinuz-4.4.0-64-generic
-rw-------  1 root root  7087024 Mar  3 19:25 vmlinuz-4.4.0-66-generic

:~$ dpkg -l | grep linux
ii  bluez-tools                                                 0.2.0~20140808-5                              amd64        Set of tools to manage Bluetooth devices for linux
ii  console-setup-linux                                         1.108ubuntu15.3                               all          Linux specific part of console-setup
ii  fonts-linuxlibertine                                        5.3.0-2                                       all          Linux Libertine family of fonts
ii  ladspa-sdk                                                  1.13-2                                        amd64        sample tools for linux-audio-dev plugin architecture
ii  libselinux1:amd64                                           2.4-3build2                                   amd64        SELinux runtime shared libraries
ii  libselinux1:i386                                            2.4-3build2                                   i386         SELinux runtime shared libraries
ii  libv4l-0:amd64                                              1.10.0-1                                      amd64        Collection of video4linux support libraries
ii  libv4l-0:i386                                               1.10.0-1                                      i386         Collection of video4linux support libraries
ii  libv4lconvert0:amd64                                        1.10.0-1                                      amd64        Video4linux frame format conversion library
ii  libv4lconvert0:i386                                         1.10.0-1                                      i386         Video4linux frame format conversion library
ii  linux-base                                                  4.0ubuntu1                                    all          Linux image base package
ii  linux-firmware                                              1.157.8                                       all          Firmware for Linux kernel drivers
iU  linux-generic                                               4.4.0.66.70                                   amd64        Complete Generic Linux kernel and headers
iU  linux-generic-lts-vivid                                     4.4.0.66.70                                   amd64        Complete Generic Linux kernel and headers (dummy transitional package)
ii  linux-headers-3.13.0-54                                     3.13.0-54.91                                  all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-54-generic                             3.13.0-54.91                                  amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-57                                     3.13.0-57.95                                  all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-57-generic                             3.13.0-57.95                                  amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-59                                     3.13.0-59.98                                  all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-59-generic                             3.13.0-59.98                                  amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-62                                     3.13.0-62.102                                 all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-62-generic                             3.13.0-62.102                                 amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-63                                     3.13.0-63.103                                 all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-63-generic                             3.13.0-63.103                                 amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-79                                     3.13.0-79.123                                 all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-79-generic                             3.13.0-79.123                                 amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-51                                     3.19.0-51.58~14.04.1                          all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-51-generic                             3.19.0-51.58~14.04.1                          amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-21                                      4.4.0-21.37                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-21-generic                              4.4.0-21.37                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-22                                      4.4.0-22.40                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-22-generic                              4.4.0-22.40                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-64                                      4.4.0-64.85                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-64-generic                              4.4.0-64.85                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-66                                      4.4.0-66.87                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-66-generic                              4.4.0-66.87                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.6.0-040600                                  4.6.0-040600.201605151930                     all          Header files related to Linux kernel version 4.6.0
ii  linux-headers-4.6.0-040600rc3                               4.6.0-040600rc3.201604120934                  all          Header files related to Linux kernel version 4.6.0
ii  linux-headers-4.6.0-040600rc3-generic                       4.6.0-040600rc3.201604120934                  amd64        Linux kernel headers for version 4.6.0 on 64 bit x86 SMP
ii  linux-headers-generic                                       4.4.0.66.70                                   amd64        Generic Linux kernel headers
rH  linux-image-3.13.0-54-generic                               3.13.0-54.91                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rH  linux-image-3.13.0-57-generic                               3.13.0-57.95                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rH  linux-image-3.13.0-59-generic                               3.13.0-59.98                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rH  linux-image-3.13.0-62-generic                               3.13.0-62.102                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rH  linux-image-3.13.0-63-generic                               3.13.0-63.103                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rH  linux-image-3.13.0-79-generic                               3.13.0-79.123                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rH  linux-image-3.19.0-51-generic                               3.19.0-51.58~14.04.1                          amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rH  linux-image-3.19.0-58-generic                               3.19.0-58.64~14.04.1                          amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-21-generic                                4.4.0-21.37                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
iF  linux-image-4.4.0-22-generic                                4.4.0-22.40                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
iF  linux-image-4.4.0-64-generic                                4.4.0-64.85                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
iF  linux-image-4.4.0-66-generic                                4.4.0-66.87                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-4.6.0-040600-generic                            4.6.0-040600.201605151930                     amd64        Linux kernel image for version 4.6.0 on 64 bit x86 SMP
rH  linux-image-4.6.0-040600rc3-generic                         4.6.0-040600rc3.201604120934                  amd64        Linux kernel image for version 4.6.0 on 64 bit x86 SMP
rH  linux-image-extra-3.13.0-57-generic                         3.13.0-57.95                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rH  linux-image-extra-3.13.0-59-generic                         3.13.0-59.98                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rH  linux-image-extra-3.13.0-62-generic                         3.13.0-62.102                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rH  linux-image-extra-3.13.0-63-generic                         3.13.0-63.103                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rH  linux-image-extra-3.13.0-79-generic                         3.13.0-79.123                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rH  linux-image-extra-3.19.0-51-generic                         3.19.0-51.58~14.04.1                          amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rH  linux-image-extra-3.19.0-58-generic                         3.19.0-58.64~14.04.1                          amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-21-generic                          4.4.0-21.37                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-extra-4.4.0-22-generic                          4.4.0-22.40                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-extra-4.4.0-64-generic                          4.4.0-64.85                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-extra-4.4.0-66-generic                          4.4.0-66.87                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-generic                                         4.4.0.66.70                                   amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                        4.4.0-67.88                                   amd64        Linux Kernel Headers for development
ii  linux-lts-vivid-tools-common                                3.19.0-18.18~14.04.1                          all          Linux kernel version specific tools for version 3.19.0
ii  linux-sound-base                                            1.0.25+dfsg-0ubuntu5                          all          base package for ALSA and OSS sound systems
ii  linuxinfo                                                   2.2.3-1                                       amd64        Displays extended system information
ii  playonlinux                                                 4.2.10-2ubuntu0.1                             all          front-end for Wine
ii  pptp-linux                                                  1.8.0-1                                       amd64        Point-to-Point Tunneling Protocol (PPTP) Client
ii  syslinux                                                    3:6.03+dfsg-11ubuntu1                         amd64        collection of bootloaders (DOS FAT and NTFS bootloader)
ii  syslinux-common                                             3:6.03+dfsg-11ubuntu1                         all          collection of bootloaders (common)
ii  syslinux-legacy                                             2:3.63+dfsg-2ubuntu8                          amd64        Bootloader for Linux/i386 using MS-DOS floppies
ii  util-linux                                                  2.27.1-6ubuntu3.2                             amd64        miscellaneous system utilities
ii  v4l-conf                                                    3.103-3build1                                 amd64        tool to configure video4linux drivers

```

So, how to proceed? I have my butcher's knife sharpened, but don't know where or how to 'cut'.

---

### Post by Impavidus on 2017-03-23
> **ajgreeny said:**
> 
What I am hoping will happen is that the purging command will remove all configurations that may be causing that error noticed by impavidus, and we can then reinstall all the grub packages with new configuration.

I think that hope is reasonable. You can run```
dpkg --list | grep grub
```to get a list of currently installed grub packages.

---

### Post by crazybear on 2017-03-24
> **Impavidus said:**
> I think that hope is reasonable. You can run```
dpkg --list | grep grub
```to get a list of currently installed grub packages.

Here is the output:

```


$ dpkg --list | grep grub
ii  grub-common                                                 2.02~beta2-36ubuntu3.8                        amd64        GRand Unified Bootloader (common files)
ii  grub-customizer                                             5.0.6-0ubuntu1~ppa1x                          amd64        Grub Customizer - A graphical Grub2/BURG configuration application
ii  grub-gfxpayload-lists                                       0.7                                           amd64        GRUB gfxpayload blacklist
iF  grub-pc                                                     2.02~beta2-36ubuntu3.8                        amd64        GRand Unified Bootloader, version 2 (PC/BIOS version)
ii  grub-pc-bin                                                 2.02~beta2-36ubuntu3.8                        amd64        GRand Unified Bootloader, version 2 (PC/BIOS binaries)
ii  grub2-common                                                2.02~beta2-36ubuntu3.8                        amd64        GRand Unified Bootloader (common files for version 2)


```

---

### Post by ajgreeny on 2017-03-24
```
$ dpkg --list | grep grub
ii  grub-common                                                 2.02~beta2-36ubuntu3.8                        amd64        GRand Unified Bootloader (common files)
ii  grub-customizer                                             5.0.6-0ubuntu1~ppa1x                          amd64        Grub Customizer - A graphical Grub2/BURG configuration application
ii  grub-gfxpayload-lists                                       0.7                                           amd64        GRUB gfxpayload blacklist
[COLOR="#FF0000"]iF  grub-pc                                                     2.02~beta2-36ubuntu3.8                        amd64        GRand Unified Bootloader, version 2 (PC/BIOS version)[/COLOR]
ii  grub-pc-bin                                                 2.02~beta2-36ubuntu3.8                        amd64        GRand Unified Bootloader, version 2 (PC/BIOS binaries)
ii  grub2-common 
```
The line shown in red above is a bit of a worry as it means that grub-pc is only part configured, so I think a reinstall of at least that package is in order; it may be behind your difficulties.

Try command ```
sudo apt-get install --reinstall grub-pc
```

---

### Post by Impavidus on 2017-03-24
Reinstalling grub-pc may work, but configuration of this package failed for the same reason as for which (un-)installation of kernels failed. See the output of dpkg --reconfigure -a in post #10. The tool that gave the error message, /usr/sbin/grub-probe, is part of grub-common. So I suspect one of the other packages is broken and grub-pc failed configuration during install the last time it was upgraded.

So, if that doesn't work, purge and reinstall all grub* packages.

First purge them, to remove the packages including their configuration files:```
sudo apt-get purge grub-common grub-customizer grub-gfxpayload-lists grub-pc grub-pc-bin grub2-common
```This will make your computer unbootable. Then reinstall them to get them back with the default configuration files:```
sudo apt-get install grub-common grub-gfxpayload-lists grub-pc grub-pc-bin grub2-common
```I left out grub-customizer for reinstall, as that package is not vital. You can reinstall it later, but be careful as I suspect it may have contributed to your problem. If you made any changes to grub to support, for example, your graphics card, make those changes again. Make sure that not only the packages are reinstalled, but grub is also reinstalled to the MBR. I see you have the bios version of grub, so I assume you use MBR partitioning. If this all works, your computer should be bootable and it should be possible to uninstall the old kernels. If you end up with an unbootable system, reinstall.

**REALLY IMPORTANT:** First check you have a working live disk and good backups of your important files. Then nothing can go wrong.

---

### Post by crazybear on 2017-03-24
Well, I think I finally made progress.....without doing any damage. I did finally add in grub-customizer [I've not had any trouble with it in other [12.04; 14.04] and it seems to be working OK now too.

As for the linux-images, they seem to be installed OK now [and some new ones that couldn't be before]. I'll remove some of the old ones shortly, but what I have now is:

```

$ ls -al /usr/src/
total 120
drwxr-xr-x 30 root root 4096 Mar 24 18:44 .
drwxr-xr-x 14 root root 4096 Apr 28  2016 ..
drwxr-xr-x  3 root root 4096 May 15  2016 libdvd-pkg
drwxr-xr-x 24 root root 4096 Jun  7  2015 linux-headers-3.13.0-54
drwxr-xr-x  7 root root 4096 Jun  7  2015 linux-headers-3.13.0-54-generic
drwxr-xr-x 24 root root 4096 Jun 25  2015 linux-headers-3.13.0-57
drwxr-xr-x  7 root root 4096 Jun 25  2015 linux-headers-3.13.0-57-generic
drwxr-xr-x 24 root root 4096 Jul 30  2015 linux-headers-3.13.0-59
drwxr-xr-x  7 root root 4096 Jul 30  2015 linux-headers-3.13.0-59-generic
drwxr-xr-x 24 root root 4096 Aug 13  2015 linux-headers-3.13.0-62
drwxr-xr-x  7 root root 4096 Aug 13  2015 linux-headers-3.13.0-62-generic
drwxr-xr-x 24 root root 4096 Aug 19  2015 linux-headers-3.13.0-63
drwxr-xr-x  7 root root 4096 Aug 19  2015 linux-headers-3.13.0-63-generic
drwxr-xr-x 24 root root 4096 Mar 11  2016 linux-headers-3.13.0-79
drwxr-xr-x  7 root root 4096 Mar 11  2016 linux-headers-3.13.0-79-generic
drwxr-xr-x 24 root root 4096 Mar 11  2016 linux-headers-3.19.0-51
drwxr-xr-x  7 root root 4096 Mar 11  2016 linux-headers-3.19.0-51-generic
drwxr-xr-x 27 root root 4096 Apr 28  2016 linux-headers-4.4.0-21
drwxr-xr-x  7 root root 4096 Apr 28  2016 linux-headers-4.4.0-21-generic
drwxr-xr-x 27 root root 4096 May 18  2016 linux-headers-4.4.0-22
drwxr-xr-x  7 root root 4096 May 18  2016 linux-headers-4.4.0-22-generic
drwxr-xr-x 27 root root 4096 Feb 22 06:42 linux-headers-4.4.0-64
drwxr-xr-x  7 root root 4096 Feb 22 06:42 linux-headers-4.4.0-64-generic
drwxr-xr-x 27 root root 4096 Mar 16 21:08 linux-headers-4.4.0-66
drwxr-xr-x  7 root root 4096 Mar 16 21:08 linux-headers-4.4.0-66-generic
drwxr-xr-x 24 root root 4096 May 26  2016 linux-headers-4.6.0-040600
drwxr-xr-x 24 root root 4096 May 26  2016 linux-headers-4.6.0-040600rc3
drwxr-xr-x  8 root root 4096 May 26  2016 linux-headers-4.6.0-040600rc3-generic
drwxr-xr-x  6 root root 4096 Mar 24 18:44 oem-audio-hda-daily-lts-xenial-0.201703240731~ubuntu16.04.1
drwxr-xr-x 12 root root 4096 Feb 22 06:45 virtualbox-5.0.32


~$ ls -al /lib/modules/
total 56
drwxr-xr-x 14 root root 4096 Mar 16 21:08 .
drwxr-xr-x 30 root root 4096 Mar 24 18:43 ..
drwxr-xr-x  2 root root 4096 Mar 17 06:17 3.13.0-54-generic
drwxr-xr-x  3 root root 4096 Mar 17 15:17 3.13.0-57-generic
drwxr-xr-x  3 root root 4096 Mar 17 15:18 3.13.0-59-generic
drwxr-xr-x  3 root root 4096 Mar 17 15:18 3.13.0-62-generic
drwxr-xr-x  3 root root 4096 Mar 17 15:19 3.13.0-63-generic
drwxr-xr-x  3 root root 4096 Mar 17 15:20 3.13.0-79-generic
drwxr-xr-x  3 root root 4096 Mar 17 15:21 3.19.0-51-generic
drwxr-xr-x  6 root root 4096 Mar 24 18:45 4.4.0-21-generic
drwxr-xr-x  6 root root 4096 Mar 24 18:44 4.4.0-22-generic
drwxr-xr-x  6 root root 4096 Mar 24 18:44 4.4.0-64-generic
drwxr-xr-x  6 root root 4096 Mar 24 18:45 4.4.0-66-generic
drwxr-xr-x  2 root root 4096 Jun  8  2016 4.6.0-040600rc3-generic


~$ ls -al /boot/
total 203856
drwxr-xr-x  4 root root    12288 Mar 24 18:36 .
drwxr-xr-x 26 root root     4096 Mar 24 18:35 ..
-rw-r--r--  1 root root  1239577 Apr 19  2016 abi-4.4.0-21-generic
-rw-r--r--  1 root root  1239612 May 13  2016 abi-4.4.0-22-generic
-rw-r--r--  1 root root  1245512 Feb 20 14:40 abi-4.4.0-64-generic
-rw-r--r--  1 root root  1245512 Mar  3 19:25 abi-4.4.0-66-generic
-rw-r--r--  1 root root   189412 Apr 19  2016 config-4.4.0-21-generic
-rw-r--r--  1 root root   189520 May 13  2016 config-4.4.0-22-generic
-rw-r--r--  1 root root   190247 Feb 20 14:40 config-4.4.0-64-generic
-rw-r--r--  1 root root   190247 Mar  3 19:25 config-4.4.0-66-generic
drwxr-xr-x  6 root root     4096 Mar 24 19:00 grub
drwxr-xr-x  5 root root     4096 May  9  2016 grub.bak
-rw-r--r--  1 root root 39406840 Feb 22 06:57 initrd.img-4.4.0-21-generic
-rw-r--r--  1 root root 39409220 Mar 24 18:35 initrd.img-4.4.0-22-generic
-rw-r--r--  1 root root 39943738 Mar 24 18:35 initrd.img-4.4.0-64-generic
-rw-r--r--  1 root root 39944512 Mar 24 18:36 initrd.img-4.4.0-66-generic
-rw-r--r--  1 root root   182704 Jan 28  2016 memtest86+.bin
-rw-r--r--  1 root root   184380 Jan 28  2016 memtest86+.elf
-rw-r--r--  1 root root   184840 Jan 28  2016 memtest86+_multiboot.bin
-rw-------  1 root root  3853719 Apr 19  2016 System.map-4.4.0-21-generic
-rw-------  1 root root  3855781 May 13  2016 System.map-4.4.0-22-generic
-rw-------  1 root root  3883990 Feb 20 14:40 System.map-4.4.0-64-generic
-rw-------  1 root root  3883990 Mar  3 19:25 System.map-4.4.0-66-generic
-rw-------  1 root root  7013968 Apr 19  2016 vmlinuz-4.4.0-21-generic
-rw-------  1 root root  7015440 May 13  2016 vmlinuz-4.4.0-22-generic
-rw-------  1 root root  7087152 Feb 20 14:40 vmlinuz-4.4.0-64-generic
-rw-------  1 root root  7087024 Mar  3 19:25 vmlinuz-4.4.0-66-generic


~$ dpkg -l | grep linux
ii  bluez-tools                                                 0.2.0~20140808-5                              amd64        Set of tools to manage Bluetooth devices for linux
ii  console-setup-linux                                         1.108ubuntu15.3                               all          Linux specific part of console-setup
ii  fonts-linuxlibertine                                        5.3.0-2                                       all          Linux Libertine family of fonts
ii  ladspa-sdk                                                  1.13-2                                        amd64        sample tools for linux-audio-dev plugin architecture
ii  libselinux1:amd64                                           2.4-3build2                                   amd64        SELinux runtime shared libraries
ii  libselinux1:i386                                            2.4-3build2                                   i386         SELinux runtime shared libraries
ii  libv4l-0:amd64                                              1.10.0-1                                      amd64        Collection of video4linux support libraries
ii  libv4l-0:i386                                               1.10.0-1                                      i386         Collection of video4linux support libraries
ii  libv4lconvert0:amd64                                        1.10.0-1                                      amd64        Video4linux frame format conversion library
ii  libv4lconvert0:i386                                         1.10.0-1                                      i386         Video4linux frame format conversion library
ii  linux-base                                                  4.0ubuntu1                                    all          Linux image base package
ii  linux-firmware                                              1.157.8                                       all          Firmware for Linux kernel drivers
ii  linux-generic                                               4.4.0.66.70                                   amd64        Complete Generic Linux kernel and headers
ii  linux-generic-lts-vivid                                     4.4.0.66.70                                   amd64        Complete Generic Linux kernel and headers (dummy transitional package)
ii  linux-headers-3.13.0-54                                     3.13.0-54.91                                  all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-54-generic                             3.13.0-54.91                                  amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-57                                     3.13.0-57.95                                  all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-57-generic                             3.13.0-57.95                                  amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-59                                     3.13.0-59.98                                  all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-59-generic                             3.13.0-59.98                                  amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-62                                     3.13.0-62.102                                 all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-62-generic                             3.13.0-62.102                                 amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-63                                     3.13.0-63.103                                 all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-63-generic                             3.13.0-63.103                                 amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-79                                     3.13.0-79.123                                 all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-79-generic                             3.13.0-79.123                                 amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-51                                     3.19.0-51.58~14.04.1                          all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-51-generic                             3.19.0-51.58~14.04.1                          amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-21                                      4.4.0-21.37                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-21-generic                              4.4.0-21.37                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-22                                      4.4.0-22.40                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-22-generic                              4.4.0-22.40                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-64                                      4.4.0-64.85                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-64-generic                              4.4.0-64.85                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-66                                      4.4.0-66.87                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-66-generic                              4.4.0-66.87                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.6.0-040600                                  4.6.0-040600.201605151930                     all          Header files related to Linux kernel version 4.6.0
ii  linux-headers-4.6.0-040600rc3                               4.6.0-040600rc3.201604120934                  all          Header files related to Linux kernel version 4.6.0
ii  linux-headers-4.6.0-040600rc3-generic                       4.6.0-040600rc3.201604120934                  amd64        Linux kernel headers for version 4.6.0 on 64 bit x86 SMP
ii  linux-headers-generic                                       4.4.0.66.70                                   amd64        Generic Linux kernel headers
rc  linux-image-3.13.0-54-generic                               3.13.0-54.91                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-57-generic                               3.13.0-57.95                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-59-generic                               3.13.0-59.98                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-62-generic                               3.13.0-62.102                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-63-generic                               3.13.0-63.103                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-79-generic                               3.13.0-79.123                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-51-generic                               3.19.0-51.58~14.04.1                          amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-58-generic                               3.19.0-58.64~14.04.1                          amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-21-generic                                4.4.0-21.37                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-22-generic                                4.4.0-22.40                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-64-generic                                4.4.0-64.85                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-66-generic                                4.4.0-66.87                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.6.0-040600-generic                            4.6.0-040600.201605151930                     amd64        Linux kernel image for version 4.6.0 on 64 bit x86 SMP
rc  linux-image-4.6.0-040600rc3-generic                         4.6.0-040600rc3.201604120934                  amd64        Linux kernel image for version 4.6.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-57-generic                         3.13.0-57.95                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-59-generic                         3.13.0-59.98                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-62-generic                         3.13.0-62.102                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-63-generic                         3.13.0-63.103                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-79-generic                         3.13.0-79.123                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-51-generic                         3.19.0-51.58~14.04.1                          amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-58-generic                         3.19.0-58.64~14.04.1                          amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-21-generic                          4.4.0-21.37                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-22-generic                          4.4.0-22.40                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-64-generic                          4.4.0-64.85                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-66-generic                          4.4.0-66.87                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic                                         4.4.0.66.70                                   amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                        4.4.0-67.88                                   amd64        Linux Kernel Headers for development
ii  linux-lts-vivid-tools-common                                3.19.0-18.18~14.04.1                          all          Linux kernel version specific tools for version 3.19.0
ii  linux-sound-base                                            1.0.25+dfsg-0ubuntu5                          all          base package for ALSA and OSS sound systems
ii  linuxinfo                                                   2.2.3-1                                       amd64        Displays extended system information
ii  playonlinux                                                 4.2.10-2ubuntu0.1                             all          front-end for Wine
ii  pptp-linux                                                  1.8.0-1                                       amd64        Point-to-Point Tunneling Protocol (PPTP) Client
ii  syslinux                                                    3:6.03+dfsg-11ubuntu1                         amd64        collection of bootloaders (DOS FAT and NTFS bootloader)
ii  syslinux-common                                             3:6.03+dfsg-11ubuntu1                         all          collection of bootloaders (common)
ii  syslinux-legacy                                             2:3.63+dfsg-2ubuntu8                          amd64        Bootloader for Linux/i386 using MS-DOS floppies
ii  util-linux                                                  2.27.1-6ubuntu3.2                             amd64        miscellaneous system utilities
ii  v4l-conf                                                    3.103-3build1                                 amd64        tool to configure video4linux drivers


```

Thanks. I need to test it a bit before I declare this fixed. I did have some special code in the grub for the keyboard that now is gone and I need to check some other things before declaring victory, but so far thanks. How does it look from there?

---

### Post by crazybear on 2017-03-24
And for grub files:

```

$ dpkg --list | grep grub
ii  grub-common                                                 2.02~beta2-36ubuntu3.8                        amd64        GRand Unified Bootloader (common files)
ii  grub-customizer                                             5.0.6-0ubuntu1~ppa1x                          amd64        Grub Customizer - A graphical Grub2/BURG configuration application
ii  grub-gfxpayload-lists                                       0.7                                           amd64        GRUB gfxpayload blacklist
ii  grub-pc                                                     2.02~beta2-36ubuntu3.8                        amd64        GRand Unified Bootloader, version 2 (PC/BIOS version)
ii  grub-pc-bin                                                 2.02~beta2-36ubuntu3.8                        amd64        GRand Unified Bootloader, version 2 (PC/BIOS binaries)
ii  grub2-common                                                2.02~beta2-36ubuntu3.8                        amd64        GRand Unified Bootloader (common files for version 2)


```

---

### Post by Impavidus on 2017-03-24
OK, grub customizer fixed it. When you think about it, it's not really surprising grub customizer could fix it, as it may have caused the problem using a buggy setting and then just reversed it. That's what I think.

Just do some cleanup now, uninstalling old kernels, and you should be fine.

But don't forget to keep a live disk and backups at hand anyway. One day you'll need them.

---

### Post by ajgreeny on 2017-03-25
Great news! 
Please mark as SOLVED from the Thread Tools menu up-top if this really is now solved to your satisfaction, which appears to be the case.
It is a great help to users searching the forum for similar problems.

---

