---
title: "Need some help"
date: 2008-02-11
forum: General Help
---

### Post by watsgoodg on 2008-02-11
can you guys help me fix this error i get it when im trying to update.  I just came from windows so im alittle in the dark here. 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by jan quark on 2008-02-11
what happens if you run this in terminal
post any error messages you get

```
sudo dpkg --configure -a
```

---

### Post by watsgoodg on 2008-02-11
Setting up python-bittorrent (3.4.2-11ubuntu3~7.10) ...

Setting up language-pack-en (1:7.10+20071120) ...
Setting up apturl (0.1ubuntu2) ...

Setting up capplets-data (1:2.20.1-0ubuntu1) ...

Setting up libssl0.9.8 (0.9.8e-5ubuntu3.1) ...

Setting up avahi-autoipd (0.6.20-2ubuntu3.2) ...

Setting up bittorrent (3.4.2-11ubuntu3~7.10) ...

Setting up linux-image-2.6.22-14-generic (2.6.22-14.51) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.22-14.46 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.22-14.46 was configured last, according to dpkg)
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.22-14-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done


Setting up app-install-data-commercial (8.4) ...
Caching application data...
Skipped k3dsurf.desktop: does not include a menu name
Generating mime/codec maps...

Setting up libperl5.8 (5.8.8-7ubuntu3.1) ...

Setting up libdb4.4 (4.4.20-8.1ubuntu3.1) ...
Setting up libavahi-common-data (0.6.20-2ubuntu3.2) ...
Setting up libavahi-common3 (0.6.20-2ubuntu3.2) ...

Setting up libisc32 (1:9.4.1-P1-3ubuntu1) ...

Setting up libisccc30 (1:9.4.1-P1-3ubuntu1) ...

Setting up libc6-i686 (2.6.1-1ubuntu10) ...

Setting up language-pack-gnome-en (1:7.10+20071120) ...
Setting up libdns32 (1:9.4.1-P1-3ubuntu1) ...

Setting up openssh-client (1:4.6p1-5ubuntu0.1) ...

dpkg: error processing libpng12-0 (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Setting up libisccfg30 (1:9.4.1-P1-3ubuntu1) ...

Setting up liblwres30 (1:9.4.1-P1-3ubuntu1) ...

Setting up libbind9-30 (1:9.4.1-P1-3ubuntu1) ...

Setting up libavahi-core5 (0.6.20-2ubuntu3.2) ...

Setting up avahi-daemon (0.6.20-2ubuntu3.2) ...
 * Reloading system message bus config...                                [ OK ] 
 * Starting Avahi mDNS/DNS-SD Daemon avahi-daemon                        [ OK ] 

Setting up bind9-host (1:9.4.1-P1-3ubuntu1) ...
Setting up dnsutils (1:9.4.1-P1-3ubuntu1) ...

Setting up perl-modules (5.8.8-7ubuntu3.1) ...
Setting up perl (5.8.8-7ubuntu3.1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 libpng12-0

thats what happend?

---

