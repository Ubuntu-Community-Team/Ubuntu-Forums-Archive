---
title: "ZFS boot volume lack of space, round two"
date: 2023-07-09
forum: General Help
---

### Post by laserburn2 on 2023-07-09
Those of us who were unlucky enough to try zfs file system on Ubuntu have faced the issue that Ubuntu installer by default makes a bpool zfs volume way too small, so it can easily overfill with automatic filesystem snapshots. I had asked for help with this already [https://ubuntuforums.org/showthread.php?t=2465671](https://ubuntuforums.org/showthread.php?t=2465671). I would manually clean some old snapshots, which would release the space and I would be able to keep updating the system normally. 

But now the problem has gotten worse, space on bpool is entirely gone even though I kept just two zfs snapshots:

zfs list -r -t snapshot -o name,used,referenced,creation bpool/BOOT
NAME                                       USED     REFER  CREATION
bpool/BOOT/ubuntu_r569du@autozsys_n7l9to    80K      888M  Wed Jun 28 18:17 2023
bpool/BOOT/ubuntu_r569du@autozsys_x8v1jo    80K      888M  Thu Jun 29 20:47 2023

zfs list
NAME                                               USED  AVAIL     REFER  MOUNTPOINT
bpool                                             1.73G  15.3M       96K  /boot
bpool/BOOT                                        1.73G  15.3M       96K  none
bpool/BOOT/ubuntu_r569du                           902M  15.3M      902M  /boot
bpool/BOOT/ubuntu_us9kn1                           872M  15.3M      888M  /boot

Needless to say, it isn't the files that are eating all the space on the volume, though there are now 4 kernels instead of the two when I opened the first thread, as Ubuntu now keeps two latest 5.15 and two latest 5.19 kernels. I tried removing one unneeded 5.15 kernel, but system just replaces it with a dummy package and no disk space is released on /boot. 

ls -lh /boot
total 902M
-rw-r--r-- 1 root root 256K May 15 16:10 config-5.15.0-73-generic
-rw-r--r-- 1 root root 256K Jun  7 01:50 config-5.15.0-75-generic
-rw-r--r-- 1 root root 264K May 19 17:45 config-5.19.0-43-generic
-rw-r--r-- 1 root root 264K Jun  7 17:23 config-5.19.0-45-generic
-rw-r--r-- 1 root root 264K Jun 21 17:38 config-5.19.0-46-generic
drwxr-xr-x 4 root root 4.0K Jan  1  1970 efi
drwxr-xr-x 5 root root 4.0K Jul  9 12:54 grub
lrwxrwxrwx 1 root root   28 Jul  9 12:55 initrd.img -> initrd.img-5.19.0-46-generic
-rw-r--r-- 1 root root 203M Jun  2 19:15 initrd.img-5.15.0-73-generic
-rw-r--r-- 1 root root 204M Jun 16 21:25 initrd.img-5.15.0-75-generic
-rw-r--r-- 1 root root 214M May 31 18:28 initrd.img-5.19.0-43-generic
-rw-r--r-- 1 root root 214M Jun 16 21:24 initrd.img-5.19.0-45-generic
lrwxrwxrwx 1 root root   28 Jul  9 12:55 initrd.img.old -> initrd.img-5.15.0-75-generic
-rw-r--r-- 1 root root 179K Feb  6  2022 memtest86+.bin
-rw-r--r-- 1 root root 181K Feb  6  2022 memtest86+.elf
-rw-r--r-- 1 root root 181K Feb  6  2022 memtest86+_multiboot.bin
-rw------- 1 root root 6.0M May 15 16:10 System.map-5.15.0-73-generic
-rw------- 1 root root 6.0M Jun  7 01:50 System.map-5.15.0-75-generic
-rw------- 1 root root 6.2M May 19 17:45 System.map-5.19.0-43-generic
-rw------- 1 root root 6.2M Jun  7 17:23 System.map-5.19.0-45-generic
-rw------- 1 root root 6.2M Jun 21 17:38 System.map-5.19.0-46-generic
lrwxrwxrwx 1 root root   25 Jul  9 12:55 vmlinuz -> vmlinuz-5.19.0-46-generic
-rw------- 1 root root  12M May 15 16:50 vmlinuz-5.15.0-73-generic
-rw------- 1 root root  12M Jun  7 01:52 vmlinuz-5.15.0-75-generic
-rw------- 1 root root  12M May 19 17:48 vmlinuz-5.19.0-43-generic
-rw------- 1 root root  12M Jun  7 17:23 vmlinuz-5.19.0-45-generic
-rw------- 1 root root  12M Jun 21 17:43 vmlinuz-5.19.0-46-generic
lrwxrwxrwx 1 root root   25 Jul  9 12:55 vmlinuz.old -> vmlinuz-5.15.0-75-generic

I have no idea what's going on and where is all my space getting lost. ZFS can't make snapshots when available space on bpool drops under 20%, which means I'm out of restore points in something goes wrong. And just last night something went wrong when update of nvidia packages caused a number or problems to the system and this morning I had to revert to my last available snapshot from June 29. 

I would highly appreciate any help on what's eating my bpool volume and how I could reclaim my free space. I was hoping I could keep my system running until a new LTS comes along.

---

### Post by laserburn2 on 2023-07-09
One thing I can't understand is why is there even two filesystems on bpool/BOOT. 

zfs list -rt all -o name,type,creation
NAME                                                              TYPE        CREATION
bpool                                                             filesystem  Mon May  4 19:25 2020
bpool/BOOT                                                        filesystem  Mon May  4 19:25 2020
bpool/BOOT/ubuntu_r569du                                          filesystem  Sun Jul  9 12:50 2023
bpool/BOOT/ubuntu_r569du@autozsys_n7l9to                          snapshot    Wed Jun 28 18:17 2023
bpool/BOOT/ubuntu_r569du@autozsys_x8v1jo                          snapshot    Thu Jun 29 20:47 2023
bpool/BOOT/ubuntu_us9kn1                                          filesystem  Sun Aug 15 15:50 2021

There is ubuntu_r569du that has creation date today, probably because I reverted to a snapshot today. My two existing snapshots are on it.

And then there is ubuntu_us9kn1 that shows creation date in 2021. The system is originally installed as Ubuntu 20.04 in 2020, then upgraded to 22.04. It's possible that it's showing the date of an earlier return to a snapshot, I remember that I had problems with the system that summer and had to revert. Perhaps a new filesystem was created when OS was upgraded? :confused: Could this be safe to destroy?

---

### Post by laserburn2 on 2023-07-09
[FONT=arial]Ok, so according to ChatGPT,  bpool/BOOT/ubuntu_r569du                                           filesystem was created for 5.19 kernel, while the old bpool/BOOT/ubuntu_us9kn1 served the old 5.15 kernel. Sounds plausible. Suggested solution is:[/FONT]
sudo zfs destroy -r bpool/BOOT/ubuntu_us9kn1

I really need the system to be working for the next few days, so I can't test what AI said, but if no one else suggests a solution, I'll make a backup and go with this.

Another suggestion it made is to install byobu package and run sudo purge-old-kernels command to get rid of old kernels.

---

### Post by #&amp;thj^% on 2023-07-09
Now I run a very inconstant amount of kernels for testing proposes only, but when I'm done I'll only want one to remain.
This command will remove all kernels except the current running kernel.
```

dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | xargs sudo apt-get -y purge
```
And to give you a glimpse of the action taken off my machine:
```
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages will be REMOVED:
  linux-headers-5.15.0-69* linux-headers-5.15.0-69-generic*
  linux-headers-5.15.0-76* linux-headers-5.15.0-76-generic*
  linux-image-5.15.0-69-generic* linux-image-5.15.0-76-generic*
  linux-modules-5.15.0-69-generic* linux-modules-5.15.0-76-generic*
  linux-modules-extra-5.15.0-69-generic*
  linux-modules-extra-5.15.0-76-generic*
0 upgraded, 0 newly installed, 10 to remove and 1 not upgraded.
After this operation, 1,192 MB disk space will be freed.
(Reading database ... 452233 files and directories currently installed.)
Removing linux-headers-5.15.0-69-generic (5.15.0-69.76) ...
Removing linux-headers-5.15.0-69 (5.15.0-69.76) ...
Removing linux-headers-5.15.0-76-generic (5.15.0-76.83) ...
Removing linux-headers-5.15.0-76 (5.15.0-76.83) ...
Removing linux-modules-extra-5.15.0-69-generic (5.15.0-69.76) ...
Removing linux-modules-extra-5.15.0-76-generic (5.15.0-76.83) ...
Removing linux-modules-5.15.0-69-generic (5.15.0-69.76) ...
Removing linux-modules-5.15.0-76-generic (5.15.0-76.83) ...
Removing linux-image-5.15.0-69-generic (5.15.0-69.76) ...
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-5.15.0-69-generic
/etc/kernel/postrm.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found background: /boot/grub_linux_lite.png
Found background image: /boot/grub_linux_lite.png
Found linux image: vmlinuz-6.2.0-24-generic in rpool/ROOT/ubuntu_d1lsb0
Found initrd image: initrd.img-6.2.0-24-generic in rpool/ROOT/ubuntu_d1lsb0
Found linux image: vmlinuz-5.15.0-76-generic in rpool/ROOT/ubuntu_d1lsb0
Found initrd image: initrd.img-5.15.0-76-generic in rpool/ROOT/ubuntu_d1lsb0
Found memtest86+ 64bit EFI image: /BOOT/ubuntu_d1lsb0@/memtest86+x64.efi
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
Found Linux Lite 6.2 (22.04) on /dev/sdc1
Found Linux Lite 6.4 (22.04) on /dev/mapper/vglinux-root
Adding boot menu entry for UEFI Firmware Settings ...
done
Removing linux-image-5.15.0-76-generic (5.15.0-76.83) ...
/etc/kernel/prerm.d/dkms:
dkms: removing: 8812au 5.6.4.2_35491.20191025 (5.15.0-76-generic) (x86_64)
Module 8812au-5.6.4.2_35491.20191025 for kernel 5.15.0-76-generic (x86_64).
Before uninstall, this module version was ACTIVE on this kernel.

88XXau.ko:
 - Uninstallation
   - Deleting from: /lib/modules/5.15.0-76-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.
depmod...
Deleting module 8812au-5.6.4.2_35491.20191025 completely from the DKMS tree.
dkms: removing: nvidia 535.54.03 (5.15.0-76-generic) (x86_64)
Module nvidia-535.54.03 for kernel 5.15.0-76-generic (x86_64).
Before uninstall, this module version was ACTIVE on this kernel.

nvidia.ko:
 - Uninstallation
   - Deleting from: /lib/modules/5.15.0-76-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

nvidia-modeset.ko:
 - Uninstallation
   - Deleting from: /lib/modules/5.15.0-76-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

nvidia-drm.ko:
 - Uninstallation
   - Deleting from: /lib/modules/5.15.0-76-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

nvidia-uvm.ko:
 - Uninstallation
   - Deleting from: /lib/modules/5.15.0-76-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

nvidia-peermem.ko:
 - Uninstallation
   - Deleting from: /lib/modules/5.15.0-76-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.
depmod...
I: /boot/vmlinuz.old is now a symlink to vmlinuz-6.2.0-24-generic
I: /boot/initrd.img.old is now a symlink to initrd.img-6.2.0-24-generic
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-5.15.0-76-generic
/etc/kernel/postrm.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found background: /boot/grub_linux_lite.png
Found background image: /boot/grub_linux_lite.png
Found linux image: vmlinuz-6.2.0-24-generic in rpool/ROOT/ubuntu_d1lsb0
Found initrd image: initrd.img-6.2.0-24-generic in rpool/ROOT/ubuntu_d1lsb0
Found memtest86+ 64bit EFI image: /BOOT/ubuntu_d1lsb0@/memtest86+x64.efi
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
File descriptor 10 (/var/lib/dpkg/triggers/linux-update-5.15.0-69-generic (deleted)) leaked on vgs invocation. Parent PID 617464: grub-probe
File descriptor 10 (/var/lib/dpkg/triggers/linux-update-5.15.0-69-generic (deleted)) leaked on vgs invocation. Parent PID 617464: grub-probe
Found Linux Lite 6.2 (22.04) on /dev/sdc1
File descriptor 10 (/var/lib/dpkg/triggers/linux-update-5.15.0-69-generic (deleted)) leaked on vgs invocation. Parent PID 617692: /usr/sbin/grub-probe
File descriptor 10 (/var/lib/dpkg/triggers/linux-update-5.15.0-69-generic (deleted)) leaked on vgs invocation. Parent PID 617692: /usr/sbin/grub-probe
Found Linux Lite 6.4 (22.04) on /dev/mapper/vglinux-root
File descriptor 10 (/var/lib/dpkg/triggers/linux-update-5.15.0-69-generic (deleted)) leaked on vgs invocation. Parent PID 618682: /usr/sbin/grub-probe
File descriptor 10 (/var/lib/dpkg/triggers/linux-update-5.15.0-69-generic (deleted)) leaked on vgs invocation. Parent PID 618682: /usr/sbin/grub-probe
File descriptor 10 (/var/lib/dpkg/triggers/linux-update-5.15.0-69-generic (deleted)) leaked on vgs invocation. Parent PID 618742: /usr/sbin/grub-probe
File descriptor 10 (/var/lib/dpkg/triggers/linux-update-5.15.0-69-generic (deleted)) leaked on vgs invocation. Parent PID 618742: /usr/sbin/grub-probe
File descriptor 10 (/var/lib/dpkg/triggers/linux-update-5.15.0-69-generic (deleted)) leaked on vgs invocation. Parent PID 618752: /usr/sbin/grub-probe
File descriptor 10 (/var/lib/dpkg/triggers/linux-update-5.15.0-69-generic (deleted)) leaked on vgs invocation. Parent PID 618752: /usr/sbin/grub-probe
File descriptor 10 (/var/lib/dpkg/triggers/linux-update-5.15.0-69-generic (deleted)) leaked on vgs invocation. Parent PID 618762: /usr/sbin/grub-probe
File descriptor 10 (/var/lib/dpkg/triggers/linux-update-5.15.0-69-generic (deleted)) leaked on vgs invocation. Parent PID 618762: /usr/sbin/grub-probe
Adding boot menu entry for UEFI Firmware Settings ...
done
(Reading database ... 381245 files and directories currently installed.)
Purging configuration files for linux-modules-extra-5.15.0-76-generic (5.15.0-76.83) ...
Purging configuration files for linux-modules-extra-5.15.0-69-generic (5.15.0-69.76) ...
Purging configuration files for linux-image-5.15.0-76-generic (5.15.0-76.83) ...
Purging configuration files for linux-modules-5.15.0-76-generic (5.15.0-76.83) ...
Purging configuration files for linux-modules-5.15.0-69-generic (5.15.0-69.76) ...
dpkg: warning: while removing linux-modules-5.15.0-69-generic, directory '/lib/modules/5.15.0-69-generic' not empty so not removed
Purging configuration files for linux-image-5.15.0-69-generic (5.15.0-69.7
```
**Please note I'm a very bold user, over the years Back-Ups are just as necessary as the air I breathe. (And your mileage may vary)
```
stat /boot
  File: /boot
  Size: 18        	Blocks: 17         IO Block: 2048   directory
Device: 0,54	Inode: 34          Links: 4
Access: (0755/drwxr-xr-x)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2023-07-09 13:47:36.061365581 -0600
Modify: 2023-07-09 13:47:33.753384274 -0600
Change: 2023-07-09 13:47:33.753384274 -0600
 Birth: 2023-07-07 15:18:23.125541678 -0600

```
```
zpool list | grep bpool
bpool  1.88G   247M  1.63G        -         -     0%    12%  1.00x    ONLINE  -

```
Or a nicer look:
```
zfs list | grep bpool
bpool                                              247M  1.51G       96K  /boot
bpool/BOOT                                         246M  1.51G       96K  none
bpool/BOOT/ubuntu_d1lsb0                           246M  1.51G      246M  /boot

```

---

### Post by MAFoElffen on 2023-07-09
I'm at work right now. The canned install script for that sets the partition for bpool which mounts at boot, at 2GB. Larger than any other install script... You just need to do maintenance, delete the old snapshots, and set the conf file for automatic snapshots at 10 or less. Default for that is 20. Since I'm on break and have limited time to answer this, search on my ID, where I've answered this many times. And I posted a script to automate that.

---

### Post by #&amp;thj^% on 2023-07-10
> **MAFoElffen said:**
> I'm at work right now. The canned install script for that sets the partition for bpool which mounts at boot, at 2GB. Larger than any other install script... You just need to do maintenance, delete the old snapshots, and set the conf file for automatic snapshots at 10 or less. Default for that is 20. Since I'm on break and have limited time to answer this, search on my ID, where I've answered this many times. And I posted a script to automate that.

+1 To the above...
I'm just trying to give the OP some headroom to work with first. ;)

---

### Post by MAFoElffen on 2023-07-10
Here you go... This thread: [https://ubuntuforums.org/showthread.php?t=2480236](https://ubuntuforums.org/showthread.php?t=2480236)

These two posts:
[https://ubuntuforums.org/showthread.php?t=2480236&p=14116787#post14116787](https://ubuntuforums.org/showthread.php?t=2480236&p=14116787#post14116787)
[https://ubuntuforums.org/showthread.php?t=2480236&p=14116790#post14116790](https://ubuntuforums.org/showthread.php?t=2480236&p=14116790#post14116790)

---

### Post by #&amp;thj^% on 2023-07-10
> **MAFoElffen said:**
> Here you go... This thread: [https://ubuntuforums.org/showthread.php?t=2480236](https://ubuntuforums.org/showthread.php?t=2480236)

These two posts:
[https://ubuntuforums.org/showthread.php?t=2480236&p=14116787#post14116787](https://ubuntuforums.org/showthread.php?t=2480236&p=14116787#post14116787)
[https://ubuntuforums.org/showthread.php?t=2480236&p=14116790#post14116790](https://ubuntuforums.org/showthread.php?t=2480236&p=14116790#post14116790)
OMG that thread was a nightmare on UF street.....:lolflag:

---

### Post by MAFoElffen on 2023-07-10
LOL. Yes it was. I think we both still have PTSD from that one. Please warn the OP not to destroy too many things at once. I don't want to relive that one again. LOL

---

### Post by MAFoElffen on 2023-07-10
Since then, I've come to the decision that I do not need more than 5 iterations of snapshots. The default in zsys in 20.04 was 20. ZSys isn't even installed in new 22.04... Maybe show him where to reset that in zsys.conf. So it rolls off the older ones. I am posting this from my phone at work, on break. LOL

---

### Post by #&amp;thj^% on 2023-07-10
> **MAFoElffen said:**
> LOL. Yes it was. I think we both still have PTSD from that one. Please warn the OP not to destroy too many things at once. I don't want to relive that one again. LOL
Now behave :guitar: my hands shake just thinking about that one.
> **MAFoElffen said:**
> Since then, I've come to the decision that I do not need more than 5 iterations of snapshots. The default in zsys in 20.04 was 20. ZSys isn't even installed in new 22.04... Maybe show him where to reset that in zsys.conf. So it rolls off the older ones. I am posting this from my phone at work, on break. LOL
Copy That!
I'll wait first to see how the kernel removals worked out first. ;)
BTW you know your always welcome in any threads I post in. JFR
[https://didrocks.fr/2020/06/04/zfs-focus-on-ubuntu-20.04-lts-zsys-state-collection/](https://didrocks.fr/2020/06/04/zfs-focus-on-ubuntu-20.04-lts-zsys-state-collection/)

---

### Post by aljames2 on 2023-07-10
LOL you two are hilarious!  I learn a lot reading from you all and TheFu, and others.  I’ll have to get a cup of coffee & read through that long zfs thread, I’m curious now, lol

Leaving you now to help the OP

---

### Post by #&amp;thj^% on 2023-07-11
I'm more of a create my own back-ups, after my first initial trial on ZFS, not so much of automated backups .
But while I fight for the space taken by a half dozen or more backups daily I came up with a one liner to remove those and free up space.
```
zfs list -r -t snapshot -S creation -Ho name bpool/BOOT | tail -n+2 | sed 's/.*@\(autozsys_\)\?//' | sudo xargs -i sh -c "echo removing {}...; zsysctl state remove {} --system --force || exit 255"

```
This command will remove all but two snapshots, so adjust>> " tail -n+2" to how many snapshots you want to keep.
And I suggest to limit timers ie:
ZSys automatically creates a snapshot of user data (your home directory) each hour. To disable these snapshots, run the following commands:

```
systemctl --user stop zsys-user-savestate.timer
systemctl --user disable zsys-user-savestate.timer
```
Check with:
```
systemctl --user status zsys-user-savestate.timer
&#9675; zsys-user-savestate.timer - Save current user state periodically
     Loaded: loaded (/usr/lib/systemd/user/zsys-user-savestate.timer; enabled; >
   **_  Active: inactive (dead) since Tue 2023-07-11 10:25:50 MDT; 18s ago_**
   Duration: 40min 39.414s
    Trigger: n/a
   Triggers: &#9679; zsys-user-savestate.service

Jul 11 09:45:10 zfs-me systemd[8808]: Started zsys-user-savestate.timer - Save >
Jul 11 10:25:50 zfs-me systemd[8808]: Stopped zsys-user-savestate.timer - Save
```
And second command:
```
systemctl --user status zsys-user-savestate.timer
&#9675; zsys-user-savestate.timer - Save current user state periodically
     Loaded: loaded (/usr/lib/systemd/user/zsys-user-savestate.timer; enabled; >
     Active: inactive (dead) since Tue 2023-07-11 10:25:50 MDT; 2min 9s ago
   Duration: 40min 39.414s
    Trigger: n/a
   Triggers: &#9679; zsys-user-savestate.service

Jul 11 09:45:10 zfs-me systemd[8808]: Started zsys-user-savestate.timer - Save >
Jul 11 10:25:50 zfs-me systemd[8808]: Stopped zsys-user-savestate.timer - Save
```
ZSys also automatically creates a snapshot of the system (packages, snaps, etc.) every time you install a package. To disable these snapshots, run the following command:

```
sudo mv /etc/apt/apt.conf.d/90_zsys_system_autosnapshot /etc/apt/apt.conf.d/90_zsys_system_autosnapshot.disabled
```
EDIT: I will post the reversal for the above.
To re-enable user snapshots, run the following command.

```
systemctl --user start zsys-user-savestate.timer
systemctl --user enable zsys-user-savestate.timer
```

To re-enable system snapshots, run the following command.

```
sudo mv /etc/apt/apt.conf.d/90_zsys_system_autosnapshot.disabled /etc/apt/apt.conf.d/
```

---

### Post by laserburn2 on 2023-07-11
I found time to deal with this again, so I removed the other filesystem on bpool and my space was back. Then I thought to install the updates that were piling up in the repos and after that my space is again gone! I have just two snapshots, the fine working system from 29/6 and today's, created automaticly by system update.

zfs list -r -t snapshot -o name,used,referenced,creation bpool/BOOT
NAME                                       USED     REFER  CREATION
bpool/BOOT/ubuntu_4tpy3j@autozsys_kpja70     8K      674M  Tue Jul 11 20:45 2023
bpool/BOOT/ubuntu_56jo89@autozsys_x8v1jo    80K      888M  Thu Jun 29 20:47 2023

This is what I get when I try to remove it:

sudo zfs destroy bpool/BOOT/ubuntu_4tpy3j@autozsys_kpja70
cannot destroy 'bpool/BOOT/ubuntu_4tpy3j@autozsys_kpja70': snapshot has dependent clones
use '-R' to destroy the following datasets:
bpool/BOOT/ubuntu_r569du

I don't understand this mess and how did it all suddenly came to be:

zfs list -rt all -o name,type,creation
NAME                                                              TYPE        CREATION
bpool                                                             filesystem  Mon May  4 19:25 2020
bpool/BOOT                                                        filesystem  Mon May  4 19:25 2020
bpool/BOOT/ubuntu_4tpy3j                                          filesystem  Tue Jul 11 21:04 2023
bpool/BOOT/ubuntu_4tpy3j@autozsys_kpja70                          snapshot    Tue Jul 11 20:45 2023
bpool/BOOT/ubuntu_56jo89                                          filesystem  Tue Jul 11 21:18 2023
bpool/BOOT/ubuntu_56jo89@autozsys_x8v1jo                          snapshot    Thu Jun 29 20:47 2023
bpool/BOOT/ubuntu_r569du                                          filesystem  Sun Jul  9 12:50 2023

Can someone help me here, because I'm really close to writing this whole mess off and installing a clean OS, far away from zfs that seems to have completely lost its mind.

---

### Post by #&amp;thj^% on 2023-07-11
> **laserburn2 said:**
> 
Can someone help me here, because I'm really close to writing this whole mess off and installing a clean OS, far away from zfs that seems to have completely lost its mind.
Did you have a chance to read Post #13 it has info to help you with that.
I will be the first to say zfs-root is a steep learning curve, and all the moving parts are still a work in progress especially for Zsys, and i'm not going to hang my hat on that part.
I'm just a manual snapshot type of user.
This is all I keep around as a rule:
```
zfs list -r -t snapshot -o name,used,referenced,creation bpool/BOOT
NAME                                       USED     REFER  CREATION
bpool/BOOT/ubuntu_d1lsb0@autozsys_quzoch     8K      246M  Mon Jul 10 20:32 2023
bpool/BOOT/ubuntu_d1lsb0@autozsys_rgoun5     0B      246M  Tue Jul 11  9:46 2023[
```

---

### Post by MAFoElffen on 2023-07-11
@1fallen --- LOL. I saw that link a few years ago. When my bpool filled up and I was looking for a way to adjust the settings of ZSys in Ubuntu 20.04..

I just noticed this post...
> **laserburn2 said:**
> [FONT=arial]Ok, so [COLOR=#ff0000]according to ChatGPT[/COLOR],  bpool/BOOT/ubuntu_r569du                                           filesystem was created for 5.19 kernel, while the old bpool/BOOT/ubuntu_us9kn1 served the old 5.15 kernel. Sounds plausible. Suggested solution is:[/FONT]
[COLOR=#ff0000]sudo zfs destroy -r bpool/BOOT/ubuntu_us9kn1[/COLOR]

I really need the system to be working for the next few days, so I can't test what AI said, but if no one else suggests a solution, I'll make a backup and go with this.

Another suggestion it made is to install byobu package and run sudo purge-old-kernels command to get rid of old kernels.
Stop quick and [COLOR=#ff0000]DO NOT DO THAT[/COLOR]!!!

ChatCPT lied to you in some sort of twisted, very dangerous joke, in so many ways! 

What you would end up doing if you did that, is deleting all of your /boot/partition and all it's sub-directories, including the EFI and grub directories mounted under that. 

You would end up having to either re-install, or to recreate your bpool/BOOT/ubuntu_UUID dataset and the /boot partition. The other part of that is that the name of the dataset, "ubuntu_UUID" as in yours is "[FONT=arial]ubuntu_r569du" is not unique to Ubuntu 22.04, nor 20.04, or any release. It is created in the scripts as a string "ubuntu-$UUID" where the variable UUID is created by a randomized string of alpha-numeric characters of 6 characters length... To try to create a UUID unique to your system. I know those scripts and where they came up with that logic. From the scripts at OpenZFS...

Now do you see how dangerous and wrong that AI generated answer was?[/FONT]

*** Correct would be to clean up your /boot partition. As 1 fallen stated by cleaning up some old kernels, and by moving old, outdated snapshots...

Or to temporarily give it more room. ZFS is a powerful and adaptable Volume Manager, that gives you so many possibilities if you learn how to use it.. If created a new partition, anywhere on your system, and gave it a partition type of be00 (Solaris Boot) and added it to pool 'bpool', it would immediately have room to work with...
```

sudo zpool get autoexpand  # Ensure that setting is set to off.
ls -lah /dev/disk/by-id/           # look for the small 2GB partition you created

# Lets say it came back with 
lrwxrwxrwx 1 root root   10 Jul  5 18:32 ata-Samsung_SSD_870_EVO_2TB_S6PNNS0W330507J-part4 -> ../../sde4

# Then add it to bpool
sudo zpool add bpool /dev/disk/by-id/ata-Samsung_SSD_870_EVO_2TB_S6PNNS0W330507J-part4

```
Instantly, if you checked your zpool status, and zfs list, bpool would be online with both vdevs, and be twice the size.

Afterwards, you could just remove that new vdev, or if it was larger than the orgianl bpool vdev, remove the original. ZFS will take care of mounting the vdev and the wiring in the background...

That fixes the room to move around to be able to fix your system... Where you need to keep up with some maintenance of your boot partition. This is not a Volume Manager problem. Nor is it just an Ubuntu problem. This is a LVM2, ZFS and LUKS systems use a separate boot partition. This creates a "fixed space" for that folder. You need to keep it clean and keep an eye on the space left i it.

Zsys takes snapshots automatcially when apt updates, then adds those snapshots to the Grub2 menu. During updates, you'll see a status message of it doing the snapshot, or warning you if the space used is above 80%.

It's default is to save 20 snapshots before it rolls off the older snapshots. the value to adjust in /etc/zsys.conf is "keeplast: n", where "n" is the number of current snapshots.

If the file /etc/zsys.conf does not exist, then the zsys daemon uses the number set inside it when it was compiled. Creating a zys.conf file is a way to override those settings. Here is mine:
```

history:
  # Keep at least n history entry per unit of time if enough of them are present
  # The order condition the bucket start and end dates (from most recent to oldest)

  # We also keep all previous state saves for the previous day.
  # gcstartafter: 1 (GC start after a whole day). Default is 1.
  # If you change this to 30, it will keep all snapshots for 30 days.
  gcstartafter: 1 

  # Minimum number of recent states to keep. Default is 20
  keeplast: 5

  #    - name:             Abitrary name of the bucket
  #      buckets:          Number of buckets over the interval
  #      bucketlength:     Length of each bucket in days
  #      samplesperbucket: Number of datasets to keep in each bucket
  
  gcrules:
    - name: PreviousDay
      buckets: 1
      bucketlength: 1
      samplesperbucket: 3
      #
      # For the previous Day (after on full day of retention of all
      # snapshots due to gcstartafter: 1), the rule PreviousDay
      # defines one bucket (buckets: 1) of size 1 day (bucketlength: 1),
      # where we keep 3 states. So basically, we keep 3 states on the
      # previous full day.
      #
    - name: PreviousWeek
      buckets: 5
      bucketlength: 1
      samplesperbucket: 1
      #
      # For the 5 days before (buckets: 5 of size 1 day (bucketlength: 1)),
      # we keep one state (samplesperbucket: 1).
      # It means thus that we keep one state per day for each of those 5 days.
      #
    - name: PreviousMonth
      buckets: 4
      bucketlength: 7
      samplesperbucket: 1
      #
      # We divide the previous month, in 4 buckets (buckets: 4) of
      # 7 days each (bucketlength: 7) and keep one state for each
      # (samplesperbucket: 1).
      # In English, this means that we try to keep one state save
      # per week over the previous month.
      #
general:
  # Minimal free space required before taking a snapshot
  minfreepoolspace: 20
  # Daemon timeout in seconds
  timeout: 60

```

---

### Post by MAFoElffen on 2023-07-11
LOL. Sniped...

---

### Post by laserburn2 on 2023-07-12
I removed[COLOR=#000000] bpool/BOOT/ubuntu_us9kn1 and nothing bad happened, so clearly it won't remove /boot. It was used for the old 5.15 kernel, which I don't need any more.

I can't remove old kernels, i tried that and Ubuntu replaces it with a dummy package and no space is saved. Seems Ubuntu insists on having two latest kernels no matter what. And if you have 5.15 and 5.19 like me, that means 4 kernels, two latest for each.

I'm just getting tired moving in circles. Whenever zfs does something, it swallows the entire space on the volume, I literally watch how space disappears before my eyes while system is doing nothing and I don't know why. I might try some more desperate steps and if it breaks, it breaks. I have no fight left in me and considering that zfs on Ubuntu is on its way out anyway, I see no reason to learn more about it. 
[/COLOR]

---

### Post by laserburn2 on 2023-07-12
Ok, so I whacked bpool/BOOT/ubuntu_r569du, that released space on bpool, so I could upgrade. This time I tried upgrading from tty, thinking that if it's indeed graphic driver problem, I might not lose picture on the screen. Picture again disappeared during kernel upgrade, but I just left it some time to finish blind and after restart, everything works. 

Of course, I again don't have space on bpool, but at least all the kernel updates were installed, so I won't have a problem updating until some package wants to write on /boot again. Then I can play whack a mole again, killing the zfs filesystem for 5.15 that keeps regenerating every time zfs creates snapshots. Crude and ugly workaround, but let's hope it keeps me going for a while, as I really don't know what I would install if I needed a new OS for my rig. 

Of course, permanently getting rid of 5.15 relict kernel that was inherited from Ubuntu 20.04 would (probably) be better, but the system just doesn't want to part with it.

---

### Post by aljames2 on 2023-07-12
In post #3 you talked about making backups of your data, not sure if you have done that yet...
As 1fallen & MAFoElffen have suggested, I join them in encouraging you to do this, like now, before you go whacking any more moles :).  Do an rsync or some other tool to backup to a USB attached storage drive or other internal disk you may have.  If you don't have one, get one.  Snapshots are not backups.  I leave further zfs instruction to these two pros.  I'm starting my zfs install for the first time tonight.  Don't give up, it's probably fixable.

---

### Post by MAFoElffen on 2023-07-13
+1 -- Always have a backup to fall back to before making changes.

Next, do 
```

apt list linux-image-generic* --installed

```
I think what you will find, is that "you" have both linux-image-generic and linux-image-gerneric-hwe-22.04 packages installed... Or in English, you have both the regular GA hardware stack, and the Hardware Enablement (HWE) stack installed, and that is why it is having at least one kernel there from each stack series...

RE: [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

There is no harm from that. But if you think that is a problem, then wanted to keep the newer series, just do
```

sudo apt remove --purge linux-image-generic

```
If you do not want it to do auto-snapshots on it's own, then follow the instructions from 1 fallen posted on that. That's what I ended up doing for that. I can do snapshots manually for what I feel I need.

---

### Post by laserburn2 on 2023-07-14
Yes, of course, I've made data backups, it's not a huge thing if everything breaks, I do have free time for a fresh install if it comes to worst.

Indeed, I do have regular and HWE stacks installed, so removing the former seems like a good idea. The problem is that this is what I get when I try to purge linux-image-generic:

The following packages will be REMOVED:
  linux-generic* linux-image-generic*
0 upgraded, 0 newly installed, 2 to remove and 11 not upgraded.
After this operation, 41.0 kB disk space will be freed.

This really looks to me like it's just removing two metapackages, while the actual files remain on the disk.

---

### Post by MAFoElffen on 2023-07-14
That does look like that...

How about if you remove, without purge... an do it with a "-s" option to do a dry run simulation of that? I do that when I have any question and want to see what it would do, without actually doing it. That way I don't wack my system accidentally.

---

### Post by laserburn2 on 2023-07-14
So, simulated removal:

The following packages will be REMOVED:
  linux-generic linux-image-generic
0 upgraded, 0 newly installed, 2 to remove and 11 not upgraded.
Remv linux-generic [5.15.0.76.74]
Remv linux-image-generic [5.15.0.76.74]

Yup, just removes two metapackages, not the kernels and the accessories. Haven't used 5.15 kernel in a long time, but the system insists I must have it apparently.

---

