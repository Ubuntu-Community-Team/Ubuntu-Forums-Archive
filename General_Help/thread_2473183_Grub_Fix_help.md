---
title: "Grub Fix help"
date: 2022-03-26
forum: General Help
---

### Post by steve-moser on 2022-03-26
[SIZE=2][FONT=arial]I have had windows on normal HDD and I installed a PCIe based ssd for 2nd hdd with ubuntu 18.
ssd is an lvm encrypted drive
[/FONT][/SIZE]
[SIZE=2][FONT=arial][SIZE=2][FONT=arial]It worked fine for like 2+ years.[/FONT][/SIZE]
Windows had an upgrade or something and it broke the boot to ubuntu. [/FONT][/SIZE]

[SIZE=2][FONT=arial]Now when I choose to boot to ubuntu it would go to a grub prompt
[/FONT][/SIZE]
[SIZE=2][FONT=arial]
[/FONT][/SIZE]
[SIZE=2][FONT=arial]So I boot to ubuntu usb and "Try ubuntu"[/FONT][/SIZE]

[SIZE=2][FONT=arial]
[/FONT][/SIZE]
[SIZE=2][FONT=arial]from fdisk -l  my two drives are:[/FONT][/SIZE]

[SIZE=2][FONT=arial]
[/FONT][/SIZE]
[SIZE=2][FONT=arial]Ubuntu[/FONT][/SIZE]

[SIZE=2][FONT=arial]Disk /dev/nvme0n1: 953.9 GiB, 1024209543168 bytes, 2000409264 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
[/FONT][/SIZE][SIZE=2][FONT=arial]Disk identifier: 275*******[/FONT][/SIZE]

[SIZE=2][FONT=arial]
[/FONT][/SIZE]
[SIZE=2][FONT=arial]Device           Start        End    Sectors   Size Type
/dev/nvme0n1p1    2048    1050623    1048576   512M EFI System
/dev/nvme0n1p2 1050624    2549759    1499136   732M Linux filesystem
/dev/nvme0n1p3 2549760 2000408575 1997858816 952.7G Linux filesystem

[/FONT][/SIZE]

[SIZE=2][FONT=arial]Windows:[/FONT][/SIZE]

[SIZE=2][FONT=arial]Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: CF2*********

Device         Start       End   Sectors   Size Type
/dev/sda1       2048    534527    532480   260M EFI System
/dev/sda2     534528    567295     32768    16M Microsoft reserved
/dev/sda3     567296 974725119 974157824 464.5G Microsoft basic data
/dev/sda4  974725120 976773119   2048000  1000M Windows recovery environment

[/FONT][/SIZE]
[SIZE=2][FONT=arial]
[/FONT][/SIZE]

[SIZE=2][FONT=arial]I tried following the instructions in this post below as  it seemed like the exact or very very similar problem.[/FONT][/SIZE]

[SIZE=2][FONT=arial][https://ubuntuforums.org/showthread.php?t=2349833&p=13602088#post13602088](https://ubuntuforums.org/showthread.php?t=2349833&p=13602088#post13602088)[SIZE=2][FONT=arial]
```
[SIZE=2][FONT=arial]
sudo -i                 *         (small I) -puts terminal into root where sudo will not be needed till closed.

apt-get update &&  apt-get install lvm2 cryptsetup                                * not needed-cryptsetup is already the newest version 
modprobe dm-crypt
cryptsetup luksOpen /dev/nvme0n1p3 crypt1                                *REQUESTS passphrase
vgscan
vgchange -ay
lvscan
(You now must mount ubuntu-vg to /mnt) 
mount /dev/ubuntu-vg/root /mnt                           *:does the output of lvscan have "/dev/ubuntu-vg/root" if not change to lvscan

mount /dev/nvme0n1p2 /mnt/boot
mount /dev/nvme0n1p1 /mnt/boot/efi
mount --bind /dev /mnt/dev 
mount --bind /dev/pts /mnt/dev/pts
mount --bind /proc /mnt/proc
mount --bind /sys /mnt/sys
cp /etc/resolv.conf /mnt/etc/
chroot /mnt
apt-get install --reinstall grub-efi-amd64
update-grub

umount /dev/nvme0n1p1
umount /dev/nvme0n1p2
umount /dev/ubuntu-vg/root                **(see note above for lvscan output)
vgchange -an  
cryptsetup luksClose crypt1[/FONT][/SIZE][SIZE=2][FONT=arial]
[/FONT][/SIZE]
```

From the terminal,  [/FONT][/SIZE][SIZE=2][FONT=arial]
Everything worked fine, following all the same commands 

until I got to the command:[/FONT][/SIZE]

apt-get install --reinstall grub-efi-amd64[SIZE=2][FONT=arial]

It gave the output below:
[/FONT][/SIZE][FONT=arial]
[/FONT][/FONT][/SIZE]```
[SIZE=2][FONT=arial][FONT=arial][SIZE=2][SIZE=2][FONT=arial][FONT=arial]
[/FONT][FONT=arial][SIZE=2][FONT=arial]
[FONT=arial]Installing for x86_64-efi platform.[/FONT]
[/FONT][/SIZE][SIZE=2][FONT=arial]Installation finished. No error reported.
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
  WARNING: Failed to connect to lvmetad. Falling back to device scanning.
  WARNING: Failed to connect to lvmetad. Falling back to device scanning.
Found linux image: /boot/vmlinuz-4.18.0-15-generic
Found initrd image: /boot/initrd.img-4.18.0-15-generic
  WARNING: Failed to connect to lvmetad. Falling back to device scanning.
  WARNING: Failed to connect to lvmetad. Falling back to device scanning.
Memtest86+ needs a 16-bit boot, that is not available on EFI, exiting
Warning: os-prober will not be executed to detect other bootable partitions.
Systems on them will not be added to the GRUB boot configuration.
Check GRUB_DISABLE_OS_PROBER documentation entry.
done
Processing triggers for shim-signed (1.37~18.04.3+15+1533136590.3beb971-0ubuntu1) ...
root@ubuntu:/#[/FONT][/SIZE][/FONT][/FONT][/SIZE][/SIZE][/FONT][/FONT][/SIZE]
```[SIZE=2][FONT=arial][FONT=arial][SIZE=2]
[/SIZE][/FONT][/FONT][/SIZE]
So that made a partial fix, when I try to boot to ubuntu, it does not stick in grub command line, looks like it is booting ubuntu, then the errors, 
it boots to 
BusyBox
(initramfs)

The errors prior:
AER: Corrected error received
PCIe Bus Error: severity=corrected
Volume group "ubuntu-vg" not found
Cannot process volume group ubuntu-vg
...
...
ALERT!  /dev/mapper/ubuntu--vg-root does not exist.

----------------

When I boot to the system from usb ubuntu and run the commands from above post it can find the ubuntu-vg/root

```
root@ubuntu:~# modprobe dm-crypt
root@ubuntu:~# cryptsetup luksOpen /dev/nvme0n1p3 crypt1 
Enter passphrase for /dev/nvme0n1p3: 
root@ubuntu:~# vgscan
  Found volume group "ubuntu-vg" using metadata type lvm2
root@ubuntu:~# vgchange -ay
  2 logical volume(s) in volume group "ubuntu-vg" now active
root@ubuntu:~# lvscan
  ACTIVE            '/dev/ubuntu-vg/root' [<930.37 GiB] inherit
  ACTIVE            '/dev/ubuntu-vg/swap_1' [976.00 MiB] inherit
root@ubuntu:~# 

```


Any ideas?  Thank You!

---

### Post by #&amp;thj^% on 2022-03-26
See if this might help: [https://askubuntu.com/questions/567730/gave-up-waiting-for-root-device-ubuntu-vg-root-doesnt-exist](https://askubuntu.com/questions/567730/gave-up-waiting-for-root-device-ubuntu-vg-root-doesnt-exist)
I've helped other with simply doing this:
The solution was to boot from a LiveCD, unlock the drive manually with cryptsetup, chroot into the root filesystem, reinstall cryptsetup and call update-initramfs.

---

### Post by steve-moser on 2022-03-27
Thank you.  only slight variations in your comman[FONT=arial]ds/instructions for me.  I am using a live usb, not cd.  and I am running ubuntu not xubuntu,  The drives are the exact same name, so I could execute the commands exactly the [/FONT][SIZE=2]same, except removing the x from xubuntu.

When I executed the command  [FONT=arial] apt install cryptsetup lvm2
there was an error with update-notifier-common
[/FONT][/SIZE]Here are all those details, I could not get that figured out.

```
root@ubuntu:/# apt install cryptsetup lvm2
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
cryptsetup is already the newest version (2:2.4.3-1ubuntu1).
lvm2 is already the newest version (2.03.11-2.1ubuntu4).
0 upgraded, 0 newly installed, 0 to remove and 292 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up update-notifier-common (3.192.30) ...
Traceback (most recent call last):
  File "/usr/lib/update-notifier/package-data-downloader", line 24, in <module>
    import debian.deb822
  File "/usr/lib/python3/dist-packages/debian/deb822.py", line 78, in <module>
    class TagSectionWrapper(collections.Mapping):
AttributeError: module 'collections' has no attribute 'Mapping'
dpkg: error processing package update-notifier-common (--configure):
 installed update-notifier-common package post-installation script subprocess re
turned error exit status 1
Errors were encountered while processing:
 update-notifier-common
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ubuntu:/# update-initramfs -u -k all
update-initramfs: Generating /boot/initrd.img-4.18.0-15-generic
root@ubuntu:/# 


```

All the commands after appeared to work correctly.

I hoped that update-notifier-common error did not matter, when I booted into ubuntu, it did not go to busybox (initramfs) 
but had the following error and locked up:

initramfs unpacking failed: junk in compressed archive
kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,)
. . . 
 . . .


Thanks!

---

### Post by steve-moser on 2022-03-28
Anyone have any ideas to try?  I am sure this is something soo simple.

---

### Post by #&amp;thj^% on 2022-03-28
Good timing I was about to go offline.
After the machine has *re-booted*  open a terminal or tty and enter "**sudo dpkg-reconfigure initramfs-tools**" without the quotation marks.

---

