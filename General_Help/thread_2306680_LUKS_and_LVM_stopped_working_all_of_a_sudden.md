---
title: "LUKS and LVM stopped working all of a sudden"
date: 2015-12-17
forum: General Help
---

### Post by arieunier on 2015-12-17
Hi there,
This morning, my laptop decided to stop booting. I'm using Ubuntu 14.04.

I got stuck after grub, and it complained about strange errors.
After a few researches on the internet, i found someone having the same error here => [http://ubuntuforums.org/showthread.php?t=2286393](http://ubuntuforums.org/showthread.php?t=2286393)

I decided to redo the entire LVM/LUKS configuration i have but i still can't boot ..
Here are the steps i did, can you help finding what's wrong ?


1/ on another ubuntu installation :
```
cryptsetup luksOpen /dev/sda5 encrypted
lvmdiskscan
vgchange -ay
lvscan
mount /dev/ubuntu-vg/root /mnt/external
mount /dev/sda1 /mnt/external/boot
mount --bind /dev /mnt/external/dev
mount --bind /proc /mnt/external/proc
mount --bind /sys /mnt/external/sys
chroot /mnt/external
```

2/ then :
```
apt-get purge grub-pc
apt-get autoremove
apt-get install grub-pc
grub-install /dev/sda
```

3/ blkid :
```
/dev/sda1: UUID="24d786e2-87e2-4975-b5ba-401ac5fe0fe3" TYPE="ext2"
/dev/sda5: UUID="1f9250f2-9289-486c-a28b-f2e6085b66e4" TYPE="crypto_LUKS"
/dev/sdb1: UUID="96686987-f467-4e73-80dd-69779d9c9cf3" TYPE="ext4"
/dev/sdb5: UUID="ac48ba8d-27cd-41b7-8929-15ce7e06eebf" TYPE="swap"
/dev/mapper/encrypted: UUID="o6DWUB-fdZt-Uzxg-y3gT-cm4W-Oj4l-igftMK" TYPE="LVM2_member"
/dev/mapper/ubuntu--vg-root: UUID="ae5df6a7-2bb3-4437-874d-9703ec24bbac" TYPE="ext4"
/dev/mapper/ubuntu--vg-swap_1: UUID="0163699c-f93b-4295-b1ed-46b8a0b20f77" TYPE="swap" 
```

4/ lucks access defined in /etc/crypttab
```
ubuntu--vg-root UUID=1f9250f2-9289-486c-a28b-f2e6085b66e4 none luks
```

5/ modify fstab
```
#LVM
/dev/mapper/ubuntu--vg-root /               ext4    errors=remount-ro 0       1
/dev/mapper/ubuntu--vg-swap_1 none            swap    sw              0       0
#BOOT : /dev/sda1
UUID=24d786e2-87e2-4975-b5ba-401ac5fe0fe3    /boot    ext2    defaults    0    2
```

6/ update initramfs
```
update-initramfs -k all -c -v
```

7/ reboot

It shows me the password screen , and then fails, and roll backs to a screen with busy box and initramfs prompt ..

Any idea ??

---

### Post by deepakdeshp on 2015-12-17
Go to the recovery boot option in GRUB , try file system check through that. You can repair file system too.
Grub also give memtest to test your RAM

If there is a hardware disk  error you can test it using following process. 
[https://help.ubuntu.com/stable/ubuntu-help/disk-check.html](https://help.ubuntu.com/stable/ubuntu-help/disk-check.html)

---

### Post by arieunier on 2015-12-18
The file system is mounted properly and works fine on another system thanks to the commands i wrote
RAM is fine as well

I think it's more related to a grub - luks - lvm chain issue ;/

---

### Post by arieunier on 2015-12-23
I was able to make it work
What I did is to install a new virtual image with luks and lvm, and check all settings generated

The main issue i found was the name I gave when I manually decrypted the encrypted disk (replaced 'encrypted' by 'sda5_crypted' and used it everywhere in configuration files)

---

