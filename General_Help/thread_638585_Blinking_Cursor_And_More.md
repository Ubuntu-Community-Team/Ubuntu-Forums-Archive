---
title: "Blinking Cursor And More"
date: 2007-12-12
forum: General Help
---

### Post by audiofreq on 2007-12-12
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/61711](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/61711) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi,

I've been using linux on and off for a few years and it's the only OS i use at uni. Before i'd been using Windows at home mainly but have tried a few linux installs and always gone back to windows on my main pc. However, recently i got ubuntu (i actually tried it a couple of years ago but on an older machine that couldn't really handle it...) and have pretty much switched to it. I have been using it for a couple of months now and never actually used windows in the time..

Anyway so the only niggling problem i have is fairly significant. I am aware of the blinking cursor at boot up bug...which is what i seem to have...and now i really need a solution or a work around because long boot times are getting really frustrating...and like i said...i like ubuntu so changing distro isn't really an option i want to consider right now.

I will post the information i know but if you need anything else just ask.

[Click Here For A Spec Of My PC]("http://www.measham.force9.co.uk/advent/pc/3512.htm")
Version: 7.10

As you can see i have the nVidia GForce and i use restricted drivers which came with ubuntu...

Ubuntu is installed on an external hard drive (which i presume is partially the cause)
Using the drive as an internal drive is not an option as it has a case with TV Out slots and it's my only hard drive and the moment...and i really still need the portability for now.

I have installed Ubuntu on the drive using it as an internal drive and encountered no problems. Performance when external hasn't changed much.

Right so the problem is when i boot up grub loads and then I am presented with a blinking cursor which remains for 2 minutes or so i think (i always leave the room when booting to avoid frustration of waiting!!).

Then i get the no splash problem where the splash isn't loading and even when changing the boot options i still just get a blank screen with sounds from the hard drive telling me it's booting...
CTR+ALT+F1 does nothing...

Then once it's all settled and sounds like it's booted my problem differs from the described bug. So at this stage i think Ubuntu has booted but the screen is blank. No keys or combination of keys do anything apart from CTR+ALT+DEL (as in reboot!). 

Buuuut it doesn't reboot! Sure enough the nVidia graphic comes up then i get gdm...

/etc/initramfs-tools/initramfs.conf 
```
WAIT=12
#
# initramfs.conf
# Configuration file for mkinitramfs(8). See initramfs.conf(5).
#

#
# MODULES: [ most | netboot | dep | list ]
#
# most - Add all framebuffer, acpi, filesystem, and harddrive drivers.
#
# dep - Try and guess which modules to load.
#
# netboot - Add the base modules, network modules, but skip block devices.
#
# list - Only include modules from the 'additional modules' list
#

MODULES=most

# BUSYBOX: [ y | n ]
#
# Use busybox if available.
#

BUSYBOX=y

#
# NFS Section of the config.
#

#
# BOOT: [ local | nfs ]
#
# local - Boot off of local media (harddrive, USB stick).
#
# nfs - Boot using an NFS drive as the root of the drive.
#

BOOT=local

#
# DEVICE: ...
#
# Specify the network interface, like eth0
#

DEVICE=eth0

#
# NFSROOT: [ auto | HOST:MOUNT ]
#

NFSROOT=auto

```

/etc/initramfs-tools/modules
```

ehci-hcd
uhci-hcd
usb-storage
usbcore
usbhid
scsi_mod
sd_mod

```

```

jon@legend:~$ fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1246d611

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          19      152586   83  Linux
/dev/sda2              20       38316   307620652+  83  Linux
/dev/sda3           38317       38913     4795402+  82  Linux swap / Solaris

```

/var/boot is empty.

Thanks in advance for any help.

---

### Post by audiofreq on 2007-12-12
bump

---

### Post by audiofreq on 2007-12-13
Bump...again. 

Really...if you even the slightest idea where i should be looking then that would be great!!

---

### Post by audiofreq on 2007-12-18
Last shameless bump.

---

