---
title: "Why is /etc/rc0.d empty?"
date: 2007-12-30
forum: General Help
---

### Post by kvonb on 2007-12-30
-

---

### Post by .nedberg on 2007-12-30
Here is mine:

```

lrwxrwxrwx 1 root root  13 2007-10-18 19:07 K01kdm -> ../init.d/kdm
lrwxrwxrwx 1 root root  17 2007-10-18 19:07 K01usplash -> ../init.d/usplash
lrwxrwxrwx 1 root root  22 2007-10-18 19:07 K16avahi-daemon -> ../init.d/avahi-daemon
lrwxrwxrwx 1 root root  16 2007-10-18 19:07 K16dhcdbd -> ../init.d/dhcdbd
lrwxrwxrwx 1 root root  16 2007-10-18 19:07 K20apport -> ../init.d/apport
lrwxrwxrwx 1 root root  18 2007-10-23 18:41 K20keytouch -> ../init.d/keytouch
lrwxrwxrwx 1 root root  20 2007-10-19 19:31 K20nfs-common -> ../init.d/nfs-common
lrwxrwxrwx 1 root root  20 2007-10-18 19:07 K25hwclock.sh -> ../init.d/hwclock.sh
lrwxrwxrwx 1 root root  20 2007-10-18 19:07 K50alsa-utils -> ../init.d/alsa-utils
lrwxrwxrwx 1 root root  14 2007-10-22 20:01 K51lirc -> ../init.d/lirc
lrwxrwxrwx 1 root root  26 2007-10-18 19:07 K59mountoverflowtmp -> ../init.d/mountoverflowtmp
lrwxrwxrwx 1 root root  17 2007-11-03 16:45 K80openvpn -> ../init.d/openvpn
lrwxrwxrwx 1 root root  21 2007-10-18 19:07 K99laptop-mode -> ../init.d/laptop-mode
-rw-r--r-- 1 root root 355 2007-10-04 12:17 README
lrwxrwxrwx 1 root root  41 2007-10-18 19:07 S01linux-restricted-modules-common -> ../init.d/linux-restricted-modules-common
lrwxrwxrwx 1 root root  22 2007-10-18 19:07 S15wpa-ifupdown -> ../init.d/wpa-ifupdown
lrwxrwxrwx 1 root root  18 2007-10-18 19:07 S20sendsigs -> ../init.d/sendsigs
lrwxrwxrwx 1 root root  17 2007-10-18 19:07 S30urandom -> ../init.d/urandom
lrwxrwxrwx 1 root root  22 2007-10-18 19:07 S31umountnfs.sh -> ../init.d/umountnfs.sh
lrwxrwxrwx 1 root root  17 2007-10-19 19:31 S32portmap -> ../init.d/portmap
lrwxrwxrwx 1 root root  18 2007-10-18 19:07 S40umountfs -> ../init.d/umountfs
lrwxrwxrwx 1 root root  20 2007-10-18 19:07 S60umountroot -> ../init.d/umountroot
lrwxrwxrwx 1 root root  14 2007-10-18 19:07 S90halt -> ../init.d/halt


```

---

### Post by kvonb on 2007-12-30
-

---

