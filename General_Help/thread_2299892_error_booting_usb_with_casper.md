---
title: "error booting usb with casper"
date: 2015-10-22
forum: General Help
---

### Post by fdo2 on 2015-10-22
I make a bootable usb with ubuntu 14.04 LTS and unetbootin, with a persistent filesystem.
It worked well.
Then I updated the system (apt-get upgrade), and installed some stuff, until filesystem got full.
I realized that the problem was that the persistent filesystem was on a file casper-rw in the fat32 partition so I needed a real ext4 partition.
Following this link [[COLOR=#1155cc][FONT=Arial]_[http://askubuntu.com/questions/397481/how-to-make-a-persistent-live-ubuntu-usb-with-more-than-4gb](http://askubuntu.com/questions/397481/how-to-make-a-persistent-live-ubuntu-usb-with-more-than-4gb)_[/FONT][/COLOR]]("http://askubuntu.com/questions/397481/how-to-make-a-persistent-live-ubuntu-usb-with-more-than-4gb")  i tried to change it: I shrinked the first partition (sdb1), created a sdb2 with ext4 and deleted casper-rw file.
Booting I get a Busybox promt.

casper partition is mounted
```

#mount
rootfs on / type rootfs (rw,size=1269928k,nr_inodes=317482)
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,relatime,size=1269944k,nr_inodes=317486,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
/dev/sdb2 on /cow type ext4 (rw,noatime,data=ordered)
/dev/sdc1 on /pen type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)

```


This is casper.log
```

/init: line 3: can't open /dev/sr0: No medium found
/init: line 3: can't open /dev/sr0: No medium found
/init: line 3: can't open /dev/sr0: No medium found
/init: line 3: can't open /dev/sr0: No medium found
/init: line 3: can't open /dev/sr0: No medium found
chroot: can't execute 'mktemp': No such file or directory
cp: can't stat '/root/var/cache/debconf/config.dat': No such file or directory
cp: can't stat '/root/var/cache/debconf/passwords.dat': No such file or directory
sed: /root/etc/debconf.conf: No such file or directory
chroot: can't execute 'debconf-communicate': No such file or directory
mount: mounting /cdrom on /root/cdrom failed: Invalid argument
/scripts/casper-bottom/07remove_oem_config: .: line 20: can't open '/root/usr/share/debconf/confmodule'
/scripts/casper-bottom/12fstab: line 25: can't create /root/etc/fstab: nonexistent directory
/scripts/casper-bottom/13swap: line 44: can't create /root/etc/fstab: nonexistent directory
grep: /root/usr/share/i18n/SUPPORTED: No such file or directory
/scripts/casper-bottom/14locales: line 58: can't create /root/etc/default/locale: nonexistent directory
/scripts/casper-bottom/14locales: line 58: can't create /root/etc/locale.gen: nonexistent directory
chroot: can't execute '/usr/sbin/locale-gen': No such file or directory
/scripts/casper-bottom/18hostname: line 23: can't create /root/etc/hostname: nonexistent directory
/scripts/casper-bottom/18hostname: line 25: can't create /root/etc/hosts: nonexistent directory
cp: omitting directory '/root'
chroot: can't execute '/usr/sbin/install-keymap': No such file or directory
/bin/casper-preseed: .: line 13: can't open '/root/usr/share/debconf/confmodule'
cat: read error: Is a directory
cat: can't open '/tmp/keyboard.orig': No such file or directory
/scripts/casper-bottom/22sslcert: .: line 20: can't open '/root/usr/share/debconf/confmodule'
/scripts/casper-bottom/23networking: line 31: can't create /root/etc/network/interfaces: nonexistent directory
/scripts/casper-bottom/23networking: line 109: can't create /root/etc/network/interfaces: nonexistent directory
grep: /root/etc/network/interfaces: No such file or directory
/scripts/casper-bottom/23networking: line 122: can't create /root/etc/network/interfaces: nonexistent directory
/scripts/casper-bottom/24preseed: .: line 20: can't open '/root/usr/share/debconf/confmodule'
/scripts/casper-bottom/25adduser: .: line 20: can't open '/root/usr/share/debconf/confmodule'
sed: /root/etc/pam.d/login: No such file or directory
/scripts/casper-bottom/30accessibility: line 73: can't create /root/etc/xdg/autostart/screen-reader-profile.desktop: nonexistent directory
chroot: can't execute 'dpkg-divert': No such file or directory
ln: /root/usr/lib/update-notifier/apt-check: No such file or directory
chroot: can't execute 'dpkg-divert': No such file or directory
ln: /root/usr/lib/ubuntu-release-upgrader/check-new-release: No such file or directory
chroot: can't execute 'dpkg-divert': No such file or directory
ln: /root/usr/lib/ubuntu-release-upgrader/check-new-release-gtk: No such file or directory
/scripts/casper-bottom/32disable_hibernation: line 24: can't create /root/var/lib/polkit-1/localauthority/50-local.d/disable-hibernate.pkla: nonexistent directory
grep: /root/etc/default/apport: No such file or directory
chroot: can't execute 'dpkg-divert': No such file or directory
/scripts/casper-bottom/43disable_updateinitramfs: line 44: can't create /root/usr/sbin/update-initramfs: nonexistent directory
chmod: /root/usr/sbin/update-initramfs: No such file or directory
chroot: can't execute 'debconf-copydb': No such file or directory
chroot: can't execute 'debconf-copydb': No such file or directory

```


I guess the problem is about mounting /root
I have tried to modify syslinux.cfg in the fat32 partition, it was
```

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- persistent

```

trying with
```
label ubnentry6
menu label testing
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/dev/sdb1/preseed/ubuntu.seed boot=casper quiet splash -- persistent
```

but it didn't work.


what more can I try?


regards

---

### Post by sudodus on 2015-10-22
Welcome to the Ubuntu Forums :-)

I suggest that you try ***mkusb***. When you tell it to make a persistent live drive, it will make a casper-rw partition automatically (not a casper-rw file). I think it is much easier than to try to repair your current system. See the following links

[mkusb](https://help.ubuntu.com/community/mkusb)

[mkusb#Persistent_live_systems](https://help.ubuntu.com/community/mkusb#Persistent_live_systems)

-o-

If you have a very big drive (for example a USB HDD) or if you want to exchange data with Windows with an NTFS file system, you might want to try the 'bleeding edge' version from the unstable PPA, ppa:mkusb/ustable.

['bleeding edge' version from the unstable PPA](https://help.ubuntu.com/community/mkusb/gui)

Otherwise the mkusb version from the standard PPA, ppa:mkusb/ppa will be good.

---

