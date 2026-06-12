---
title: "libusb error when using lsusb in Ubuntu 22.04"
date: 2024-08-13
forum: General Help
---

### Post by dhpanchaai on 2024-08-13
I'm receiving the following error when using the command lsusb:
~$ lsusb
lsusb: symbol lookup error: lsusb: undefined symbol: libusb_get_port_numbers

I tried uninstalling and re-installing usbutils and libusb-1.0-0 with no luck.
~$ sudo apt-get install usbutils libusb-1.0-0
[sudo] password for my_machine: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
usbutils is already the newest version (1:014-1build1).
libusb-1.0-0 is already the newest version (2:1.0.25-1ubuntu2).
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.

Any idea what could be the issue or what I can try?

---

### Post by #&amp;thj^% on 2024-08-13
No idea yet, please show us this:
```
cd /etc/ld.so.conf.d && ls

```

---

### Post by idris2003 on 2024-09-12
> **#&thj^% said:**
> No idea yet, please show us this:
```
cd /etc/ld.so.conf.d && ls

```

Hijacking this thread. I am having the same error and the output I get is the following:
** libc.conf  x86_64-linux-gnu.conf**

This is what happens when I run cat for each of this conf files.

```
# libc default configuration
/usr/local/lib
```

```
/usr/local/lib/x86_64-linux-gnu
/lib/x86_64-linux-gnu
/usr/lib/x86_64-linux-gnu

```

---

### Post by dhpanchaai on 2024-10-07
Sorry for the late reply. Here is what I'm getting:

"$ cd /etc/ld.so.conf.d && ls
fakeroot-x86_64-linux-gnu.conf  x86_64-linux-gnu.conf
libc.conf                       zz_i386-biarch-compat.conf"

Also:

"/etc/ld.so.conf.d$ ldconfig -p | grep libusb
	libusbmuxd-2.0.so.6 (libc6,x86-64) => /lib/x86_64-linux-gnu/libusbmuxd-2.0.so.6
	libusb-1.0.so.0 (libc6,x86-64) => /lib/x86_64-linux-gnu/libusb-1.0.so.0
	libusb-0.1.so.4 (libc6,x86-64) => /lib/x86_64-linux-gnu/libusb-0.1.so.4
	libhidapi-libusb.so.0 (libc6,x86-64) => /lib/x86_64-linux-gnu/libhidapi-libusb.so.0"

---

### Post by &amp;KyT$0P# on 2024-10-07
> **dhpanchaai said:**
> "/etc/ld.so.conf.d$ ldconfig -p | grep libusb
	libusbmuxd-2.0.so.6 (libc6,x86-64) => /lib/x86_64-linux-gnu/libusbmuxd-2.0.so.6
	libusb-1.0.so.0 (libc6,x86-64) => /lib/x86_64-linux-gnu/libusb-1.0.so.0
	libusb-0.1.so.4 (libc6,x86-64) => /lib/x86_64-linux-gnu/libusb-0.1.so.4
	libhidapi-libusb.so.0 (libc6,x86-64) => /lib/x86_64-linux-gnu/libhidapi-libusb.so.0"

Please post the output from running this command in Terminal -
```
dpkg-query -S {/usr,}/lib/x86_64-linux-gnu/libusb-0.1.so.4
```

---

