---
title: "ubuntu edgy stuck in the boot proccess"
date: 2006-11-10
forum: General Help
---

### Post by nadavvin on 2006-11-10
Hello

Ububtu stuck in the boot proccess after the fsck check finished.

I can move to tty1 and perform "sudo init 5" and KDM load.

Why doesn't it work automatic???

---

### Post by nadavvin on 2006-11-11
What is the problem?????????

and how do I fix it??????

---

### Post by nadavvin on 2006-11-12
Why It's not go directly to init 5 and stuck in the boot sequence???

---

### Post by nadavvin on 2006-11-18
this is the init state:

It's all fine?
```

/etc/rc0.d
/etc/rc0.d/K01kdm
/etc/rc0.d/K01usplash
/etc/rc0.d/K25hwclock.sh
/etc/rc0.d/K05preload
/etc/rc0.d/K19cupsys
/etc/rc0.d/K19hpoj
/etc/rc0.d/K20dbus
/etc/rc0.d/K20laptop-mode
/etc/rc0.d/K21hplip
/etc/rc0.d/K25mdadm
/etc/rc0.d/K50alsa-utils
/etc/rc0.d/K86ppp
/etc/rc0.d/S15wpa-ifupdown
/etc/rc0.d/S01linux-restricted-modules-common
/etc/rc0.d/S20sendsigs
/etc/rc0.d/S30urandom
/etc/rc0.d/S31umountnfs.sh
/etc/rc0.d/S40umountfs
/etc/rc0.d/S49evms
/etc/rc0.d/S50lvm
/etc/rc0.d/S50mdadm-raid
/etc/rc0.d/S60umountroot
/etc/rc0.d/S90halt
/etc/rc0.d/K89resolvconf
/etc/rc0.d/K91apache2
/etc/rc0.d/K19mysql-ndb-mgm
/etc/rc0.d/K20mysql
/etc/rc0.d/K21mysql-ndb
/etc/rc0.d/K85bind9
/etc/rc0.d/K20firestarter
/etc/rc0.d/K20gpm
/etc/rc0.d/K20mzscheme
/etc/rc0.d/K01gdm
/etc/rc0.d/K20jabber
/etc/rc0.d/K20mono-xsp
/etc/rc0.d/K20mono-xsp2
/etc/rc0.d/K50apache2
/etc/rc0.d/K50mysql
/etc/rc0.d/README
/etc/rc1.d
/etc/rc1.d/K01kdm
/etc/rc1.d/K01usplash
/etc/rc1.d/K11anacron
/etc/rc1.d/K11atd
/etc/rc1.d/K11cron
/etc/rc1.d/K19cupsys
/etc/rc1.d/K20acpi-support
/etc/rc1.d/K20apmd
/etc/rc1.d/K20dbus
/etc/rc1.d/K20hotkey-setup
/etc/rc1.d/K20laptop-mode
/etc/rc1.d/K20makedev
/etc/rc1.d/K20nvidia-kernel
/etc/rc1.d/K20powernowd
/etc/rc1.d/K20rsync
/etc/rc1.d/K21acpid
/etc/rc1.d/K21hplip
/etc/rc1.d/K25mdadm
/etc/rc1.d/K74bluetooth
/etc/rc1.d/K86ppp
/etc/rc1.d/K89klogd
/etc/rc1.d/K90sysklogd
/etc/rc1.d/S30killprocs
/etc/rc1.d/K91apache2
/etc/rc1.d/K19mysql-ndb-mgm
/etc/rc1.d/K20mysql
/etc/rc1.d/K21mysql-ndb
/etc/rc1.d/K85bind9
/etc/rc1.d/K20vsftpd
/etc/rc1.d/K20firestarter
/etc/rc1.d/K20gpm
/etc/rc1.d/K20mzscheme
/etc/rc1.d/K01gdm
/etc/rc1.d/K20festival
/etc/rc1.d/K20jabber
/etc/rc1.d/K90binfmt-support
/etc/rc1.d/K20mono-xsp
/etc/rc1.d/K20mono-xsp2
/etc/rc1.d/K50apache2
/etc/rc1.d/K50mysql
/etc/rc1.d/S90single
/etc/rc1.d/README
/etc/rc1.d/K20apt-index-watcher
/etc/rc1.d/K20kde-guidance
/etc/rc1.d/K05preload
/etc/rc1.d/K19hpoj
/etc/rc2.d
/etc/rc2.d/S05vbesave
/etc/rc2.d/S10acpid
/etc/rc2.d/S10powernowd.early
/etc/rc2.d/S10sysklogd
/etc/rc2.d/S11klogd
/etc/rc2.d/S14ppp
/etc/rc2.d/S18hplip
/etc/rc2.d/S19cupsys
/etc/rc2.d/S20apmd
/etc/rc2.d/S20dbus
/etc/rc2.d/S20hotkey-setup
/etc/rc2.d/S20laptop-mode
/etc/rc2.d/S20makedev
/etc/rc2.d/S20nvidia-kernel
/etc/rc2.d/S20powernowd
/etc/rc2.d/S20rsync
/etc/rc2.d/S25bluetooth
/etc/rc2.d/S25mdadm
/etc/rc2.d/S89anacron
/etc/rc2.d/S89atd
/etc/rc2.d/S89cron
/etc/rc2.d/README
/etc/rc2.d/S99acpi-support
/etc/rc2.d/S50mysql
/etc/rc2.d/S99rc.local
/etc/rc2.d/S99rmnologin
/etc/rc2.d/S99stop-readahead
/etc/rc2.d/S20gpm
/etc/rc2.d/S19mysql-ndb-mgm
/etc/rc2.d/S13gdm
/etc/rc2.d/S21mysql-ndb
/etc/rc2.d/S20mzscheme
/etc/rc2.d/S20festival
/etc/rc2.d/S20jabber
/etc/rc2.d/S90binfmt-support
/etc/rc2.d/S20mono-xsp
/etc/rc2.d/S20mono-xsp2
/etc/rc2.d/S50apache2
/etc/rc2.d/S20apt-index-watcher
/etc/rc2.d/S20kde-guidance
/etc/rc2.d/S95preload
/etc/rc2.d/S19hpoj
/etc/rc3.d
/etc/rc3.d/S05vbesave
/etc/rc3.d/S10acpid
/etc/rc3.d/S10sysklogd
/etc/rc3.d/S11klogd
/etc/rc3.d/S14ppp
/etc/rc3.d/S18hplip
/etc/rc3.d/S19cupsys
/etc/rc3.d/S20apmd
/etc/rc3.d/S20dbus
/etc/rc3.d/S20hotkey-setup
/etc/rc3.d/S20laptop-mode
/etc/rc3.d/S20makedev
/etc/rc3.d/K99kdm
/etc/rc3.d/S20powernowd
/etc/rc3.d/S20rsync
/etc/rc3.d/S25bluetooth
/etc/rc3.d/S25mdadm
/etc/rc3.d/S89anacron
/etc/rc3.d/S89atd
/etc/rc3.d/S89cron
/etc/rc3.d/S98usplash
/etc/rc3.d/S99acpi-support
/etc/rc3.d/S19hpoj
/etc/rc3.d/S99rc.local
/etc/rc3.d/S99rmnologin
/etc/rc3.d/S91apache2
/etc/rc3.d/S19mysql-ndb-mgm
/etc/rc3.d/S20mysql
/etc/rc3.d/S21mysql-ndb
/etc/rc3.d/S15bind9
/etc/rc3.d/S20vsftpd
/etc/rc3.d/S20firestarter
/etc/rc3.d/S20gpm
/etc/rc3.d/S20mzscheme
/etc/rc3.d/S20festival
/etc/rc3.d/S20jabber
/etc/rc3.d/S90binfmt-support
/etc/rc3.d/S20mono-xsp
/etc/rc3.d/S20mono-xsp2
/etc/rc3.d/S20kde-guidance
/etc/rc3.d/README
/etc/rc3.d/S20apt-index-watcher
/etc/rc3.d/K13gdm
/etc/rc3.d/K20nvidia-kernel
/etc/rc3.d/S95preload
/etc/rc4.d
/etc/rc4.d/S05vbesave
/etc/rc4.d/S10acpid
/etc/rc4.d/S10sysklogd
/etc/rc4.d/S11klogd
/etc/rc4.d/S14ppp
/etc/rc4.d/S18hplip
/etc/rc4.d/S19cupsys
/etc/rc4.d/S20apmd
/etc/rc4.d/S20dbus
/etc/rc4.d/S20hotkey-setup
/etc/rc4.d/S20laptop-mode
/etc/rc4.d/S20makedev
/etc/rc4.d/S20nvidia-kernel
/etc/rc4.d/S20powernowd
/etc/rc4.d/S20rsync
/etc/rc4.d/S25bluetooth
/etc/rc4.d/S25mdadm
/etc/rc4.d/S89anacron
/etc/rc4.d/S89atd
/etc/rc4.d/S89cron
/etc/rc4.d/S98usplash
/etc/rc4.d/S99acpi-support
/etc/rc4.d/S99kdm
/etc/rc4.d/S99rc.local
/etc/rc4.d/S99rmnologin
/etc/rc4.d/S91apache2
/etc/rc4.d/S19mysql-ndb-mgm
/etc/rc4.d/S20mysql
/etc/rc4.d/S21mysql-ndb
/etc/rc4.d/S15bind9
/etc/rc4.d/S20vsftpd
/etc/rc4.d/S20firestarter
/etc/rc4.d/S20gpm
/etc/rc4.d/S20mzscheme
/etc/rc4.d/S19hpoj
/etc/rc4.d/S20festival
/etc/rc4.d/S20jabber
/etc/rc4.d/S90binfmt-support
/etc/rc4.d/S20mono-xsp
/etc/rc4.d/S20mono-xsp2
/etc/rc4.d/S20kde-guidance
/etc/rc4.d/README
/etc/rc4.d/S20apt-index-watcher
/etc/rc4.d/S95preload
/etc/rc4.d/K13gdm
/etc/rc5.d
/etc/rc5.d/S05vbesave
/etc/rc5.d/S10acpid
/etc/rc5.d/S10sysklogd
/etc/rc5.d/S11klogd
/etc/rc5.d/S14ppp
/etc/rc5.d/S18hplip
/etc/rc5.d/S19cupsys
/etc/rc5.d/S20apmd
/etc/rc5.d/S20dbus
/etc/rc5.d/S20hotkey-setup
/etc/rc5.d/S20laptop-mode
/etc/rc5.d/S20makedev
/etc/rc5.d/S20nvidia-kernel
/etc/rc5.d/S20powernowd
/etc/rc5.d/S20rsync
/etc/rc5.d/S25bluetooth
/etc/rc5.d/S25mdadm
/etc/rc5.d/S89anacron
/etc/rc5.d/S89atd
/etc/rc5.d/S89cron
/etc/rc5.d/S98usplash
/etc/rc5.d/S99acpi-support
/etc/rc5.d/S99kdm
/etc/rc5.d/S99rc.local
/etc/rc5.d/S99rmnologin
/etc/rc5.d/K20mysql
/etc/rc5.d/S19mysql-ndb-mgm
/etc/rc5.d/K13gdm
/etc/rc5.d/S21mysql-ndb
/etc/rc5.d/S15bind9
/etc/rc5.d/S20vsftpd
/etc/rc5.d/S20firestarter
/etc/rc5.d/S20gpm
/etc/rc5.d/S20mzscheme
/etc/rc5.d/S19hpoj
/etc/rc5.d/S20festival
/etc/rc5.d/S20jabber
/etc/rc5.d/S90binfmt-support
/etc/rc5.d/S20mono-xsp
/etc/rc5.d/S20mono-xsp2
/etc/rc5.d/S20kde-guidance
/etc/rc5.d/README
/etc/rc5.d/S20apt-index-watcher
/etc/rc5.d/K91apache2
/etc/rc5.d/S95preload
/etc/rc6.d
/etc/rc6.d/K01kdm
/etc/rc6.d/K01usplash
/etc/rc6.d/K25hwclock.sh
/etc/rc6.d/K05preload
/etc/rc6.d/K19cupsys
/etc/rc6.d/K19hpoj
/etc/rc6.d/K20dbus
/etc/rc6.d/K20laptop-mode
/etc/rc6.d/K21hplip
/etc/rc6.d/K25mdadm
/etc/rc6.d/K50alsa-utils
/etc/rc6.d/K86ppp
/etc/rc6.d/S15wpa-ifupdown
/etc/rc6.d/S01linux-restricted-modules-common
/etc/rc6.d/S20sendsigs
/etc/rc6.d/S30urandom
/etc/rc6.d/S31umountnfs.sh
/etc/rc6.d/S40umountfs
/etc/rc6.d/S49evms
/etc/rc6.d/S50lvm
/etc/rc6.d/S50mdadm-raid
/etc/rc6.d/S60umountroot
/etc/rc6.d/S90reboot
/etc/rc6.d/K89resolvconf
/etc/rc6.d/K91apache2
/etc/rc6.d/K19mysql-ndb-mgm
/etc/rc6.d/K20mysql
/etc/rc6.d/K21mysql-ndb
/etc/rc6.d/K85bind9
/etc/rc6.d/K20firestarter
/etc/rc6.d/K20gpm
/etc/rc6.d/K20mzscheme
/etc/rc6.d/K01gdm
/etc/rc6.d/K20jabber
/etc/rc6.d/K20mono-xsp
/etc/rc6.d/K20mono-xsp2
/etc/rc6.d/K50apache2
/etc/rc6.d/K50mysql
/etc/rc6.d/README
/etc/rcS.d
/etc/rcS.d/README
/etc/rcS.d/S50hwclock.sh
/etc/rcS.d/S01readahead
/etc/rcS.d/S02hostname.sh
/etc/rcS.d/S05keymap.sh
/etc/rcS.d/S07linux-restricted-modules-common
/etc/rcS.d/S08loopback
/etc/rcS.d/S10udev
/etc/rcS.d/S13pcmciautils
/etc/rcS.d/S15module-init-tools
/etc/rcS.d/S17procps.sh
/etc/rcS.d/S20checkroot.sh
/etc/rcS.d/S25brltty
/etc/rcS.d/S25mdadm-raid
/etc/rcS.d/S26lvm
/etc/rcS.d/S27evms
/etc/rcS.d/S30checkfs.sh
/etc/rcS.d/S35mountall.sh
/etc/rcS.d/S39readahead-desktop
/etc/rcS.d/S40networking
/etc/rcS.d/S40pcmcia
/etc/rcS.d/S45waitnfs.sh
/etc/rcS.d/S55dns-clean
/etc/rcS.d/S55pppd-dns
/etc/rcS.d/S60displayconfig-hwprobe.py
/etc/rcS.d/S70screen
/etc/rcS.d/S70x11-common
/etc/rcS.d/S80bootmisc.sh
/etc/rcS.d/S85urandom
/etc/rcS.d/S90console-screen.sh
/etc/rcS.d/S07resolvconf
/etc/rcS.d/S05initrd-tools.sh
/etc/rcS.d/S31hibernate
/etc/rcS.d/S65guarddog
/etc/rcS.d/S06keyboard-setup
/etc/rcS.d/S49console-setup
/etc/rcS.d/S01mountkernfs.sh
/etc/rcS.d/S11mountdevsubfs.sh
/etc/rcS.d/S22mtab.sh
/etc/rcS.d/S36mountall-bootclean.sh
/etc/rcS.d/S46mountnfs-bootclean.sh


```

---

### Post by angem1 on 2006-11-25
Try removing 'splash' from kernel arguments on boot. (look in /boot/grub/menu.lst for your kernel)

---

### Post by nadavvin on 2006-11-25
I reinstall edgy and now It's fine.

Nadav

---

