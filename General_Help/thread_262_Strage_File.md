---
title: "Strage File"
date: 2004-10-12
forum: General Help
---

### Post by cll2001 on 2004-10-12
:oops: What is the file dead.letter? It has a gnome foot for an icon and
 a red X in the reght corner. Any ideas? It's located in /. Not in a folder just in /.

---

### Post by flygmaskin on 2004-10-12
Seems to be some form of mail from debconf.

> To: root
Subject: Debconf: Configuring libusb-0.1-4 -- /proc/bus/usb must be mounted to use libusb

libusb uses a pseudo-filesystem known as 'usbdevfs` or 'usbfs` to access
the USB devices connected to your machine. This filesystem must be mounted
under /proc/bus/usb for libusb to work.

Currently, it is not mounted, hence this note.

Adding the line
     none /proc/bus/usb usbfs defaults 0 0
to your /etc/fstab file will mount the usbfs for you automatically at boot
time ; only root will be able to access the USB devices with this setup.

Several mount options are available, that allow you to set the permissions
on the files created under /proc/bus/usb so that non-root users can use
libusb applications. See /usr/share/doc/libusb-0.1-4/README.Debian for
more information.

--
Debconf, running at localhost.localdomain
[ Debconf was not configured to display this note, so it mailed it to you. ]
To: root
Subject: Debconf: Configuring hotplug -- USB keyboard configuration

If you're booting with a USB keyboard and/or mouse, and want to defend
against boot failures like missing modules, you should probably use static
linking for the "hid", "keybdev" (and/or "mousedev"), "input", "usbcore",
and USB Host Controller modules.

--
Debconf, running at localhost.localdomain
[ Debconf was not configured to display this note, so it mailed it to you. ]
To: root
Subject: Debconf: LVM -- LVM interaction with devfs

LVM does work with Linux 2.4 kernels that have devfs in them, however
there are some important things you need to know.

If devfs is compiled into the kernel then it MUST be mounted on /dev
otherwise LVM will not be able to locate your Physical Volumes. You must
also use the full devfs device names in LVM commands rather than the
shortened devfsd names.

This is particularly important because the default Debian 2.4 Linux
kernels are built in this way. So, if you plan to stick with a default
kernel and want to use lvm you should also install the devfsd package.

--Debconf, running at localhost.localdomain
[ Debconf was not configured to display this note, so it mailed it to you. ]
To: root
Subject: Debconf: Configuring udev -- udev has not been fully enabled yet.

You may be able to start udev without rebooting by running:

/etc/init.d/udev start

but this will break some things. If in doubt, please reboot your system as
soon as possible to activate udev.

--
Debconf, running at localhost.localdomain
[ Debconf was not configured to display this note, so it mailed it to you. ]

---

### Post by WW on 2004-10-14
I asked about this file on the IRC channel.  You can delete it.

---

