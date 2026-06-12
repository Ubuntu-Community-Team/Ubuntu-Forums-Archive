---
title: "E: dpkg was interrupted (hanging) [16.04]"
date: 2016-07-20
forum: General Help
---

### Post by kenetik on 2016-07-20
Box is running 16.04.

```

# lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04 LTS
Release:	16.04
Codename:	xenial

```

After performing a routine 'apt-get upgrade', I've started experiencing the following error:
```

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

```

When attempting to resolve the issue with the suggested command, dpkg hangs after the following:
```

# dpkg --configure -a
Setting up libnm-glib-vpn1:amd64 (1.2.0-0ubuntu0.16.04.3) ...
Setting up apache2-utils (2.4.18-2ubuntu3.1) ...
Setting up libpython3.5:amd64 (3.5.2-2~16.01) ...
Setting up libnm0:amd64 (1.2.0-0ubuntu0.16.04.3) ...
Setting up linux-image-4.4.0-31-generic (4.4.0-31.50) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
initrd.img(/boot/initrd.img-4.4.0-31-generic
) points to /boot/initrd.img-4.4.0-31-generic
 (/boot/initrd.img-4.4.0-31-generic) -- doing nothing at /var/lib/dpkg/info/linux-image-4.4.0-31-generic.postinst line 491.
vmlinuz(/boot/vmlinuz-4.4.0-31-generic
) points to /boot/vmlinuz-4.4.0-31-generic
 (/boot/vmlinuz-4.4.0-31-generic) -- doing nothing at /var/lib/dpkg/info/linux-image-4.4.0-31-generic.postinst line 491.
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-31-generic
cryptsetup: WARNING: failed to detect canonical device of /dev/sdb5
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.

```

Any suggestions?

---

### Post by Registered2read on 2016-08-01
I had the same problem on two servers. A reboot solved the issue for me.

---

