---
title: "Update-initramfs hangs"
date: 2012-11-11
forum: General Help
---

### Post by whatthefunk on 2012-11-11
Ive reinstalled three times in the past two weeks and each time I eventually run into this same problem.  When installing something (this time the nvidia driver) that requires update-initramfs to be run, it stalls and hangs.
```
$ sudo update-initramfs -u
update-initramfs: Generating /boot/initrd.img-3.5.0-17-generic
```

I let it sit like this for near an hour once and it did nothing.  This is the tail end of my dpkg log:
```
2012-11-11 17:59:57 trigproc initramfs-tools:all 0.103ubuntu0.2 <none>
2012-11-11 17:59:57 status half-configured initramfs-tools:all 0.103ubuntu0.2
2012-11-11 18:05:04 startup packages configure
2012-11-11 18:05:04 configure initramfs-tools:all 0.103ubuntu0.2 <none>
2012-11-11 18:05:04 status half-configured initramfs-tools:all 0.103ubuntu0.2
2012-11-11 18:05:04 status installed initramfs-tools:all 0.103ubuntu0.2
2012-11-11 18:05:04 status triggers-pending initramfs-tools:all 0.103ubuntu0.2
2012-11-11 18:05:04 trigproc initramfs-tools:all 0.103ubuntu0.2 <none>
2012-11-11 18:05:04 status half-configured initramfs-tools:all 0.103ubuntu0.2
```

Ive tried the following:
```
sudo dpkg --configure -a
```
It tries to complete the update-initramfs command with the same result as above.

```
sudo update-initramfs -u
```
Same as above.

```
sudo apt-get install -f
```
And I get this error:
```
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
```

No luck.  Ive spent 6 hours googling this and have found hundreds of people with the same problem but no working solution.  I would really appreciate some help with this.

---

### Post by x15 on 2012-11-11
I have a same problem. Intel i7 and nVidia VGA card.

#update-initramfs -u -v hangs *after* this line:

Adding module /lib/modules/3.5.0-17-generic/kernel/drivers/gpu/drm/vmwgfx/vmwgfx.ko

I found several forum topics like this and every posts say similar problems, however not the same line - but nearby.

#ps fax shows this:
\_ aptitude
_\_ /usr/bin/dpkg --status-fd 120 --configure initramfs-tools:all linux-image-3.5.0-18-generic:amd64 linux-image-extra
__\_ /usr/bin/perl /var/lib/dpkg/info/linux-image-3.5.0-18-generic.postinst configure 
___\_ run-parts --verbose --exit-on-error --arg=3.5.0-18-generic --arg=/boot/vmlinuz-3.5.0-18-generic /etc/kerne
____\_ /bin/sh -e /etc/kernel/postinst.d/initramfs-tools 3.5.0-18-generic /boot/vmlinuz-3.5.0-18-generic
_____\_ /bin/sh /usr/sbin/update-initramfs -c -t -k 3.5.0-18-generic -b /boot
______\_ /bin/sh /usr/sbin/update-initramfs.initramfs-tools -c -t -k 3.5.0-18-generic -b /boot
_______\_ /bin/sh /usr/sbin/mkinitramfs -o /boot/initrd.img-3.5.0-18-generic.new 3.5.0-18-generic
________\_ /bin/sh /usr/share/initramfs-tools/hooks/framebuffer
_________\_ /bin/sh /usr/share/initramfs-tools/hooks/framebuffer
__________\_ modprobe --set-version=3.5.0-18-generic --ignore-install --quiet --show-depend
___________\_ awk /^insmod/ { print $2 }

---

### Post by whatthefunk on 2012-11-11
I got it working, but Im not sure exactly what did it.  In /etc/initramfs-tools/initramfs.conf change the line
```
MODULES=most
```
to
```
MODULES=dep
```

Then reboot.

---

### Post by x15 on 2012-11-17
Thanks whatthefunk!

It helped :)

But I worry a little bit what will happen when I'll change my motherboard...

How can I upgrade my servers to 12.10 remotely? :confused:

---

### Post by dino99 on 2012-11-17
please, add your comments and select "affect me too" to get devs attention; really need an upgrade.

[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/1079605](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/1079605)

---

