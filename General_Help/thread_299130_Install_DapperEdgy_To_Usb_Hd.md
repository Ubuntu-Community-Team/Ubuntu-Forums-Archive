---
title: "Install Dapper/Edgy To Usb Hd"
date: 2006-11-13
forum: General Help
---

### Post by Ben Cook2 on 2006-11-13
Hi,

Does Anyone Have Any Instructions For Installing Dapper/Edgy On To A Usb Hd? As I Can't Seem To Find Any Instructions For Dapper, Most Refer To Breezy/Hoary. ](*,) And When I Try To Do It Myself Without Anything Special GRUB Seems To Encounter Problems. I Am Trying To Install To A Seagate 160GB Usb2.0 Drive Partioned As Follows.

130GB Main FAT32
30GB Free Space

I Used The Graphical Installer As Part Of The Kubuntu CD But I Can Try The Ubuntu Cd & Eithers Alternates If Needed.

I Also Have A Internal Sata HD Which I Don't Want Touched. The System Doesn't Have To Be Portable But It Would Be Nice.

---

### Post by Ben Cook2 on 2006-11-13
I Found A Page That Has Instructions That Let You Use The Live CD. :D 
Heres The Link: [http://www.ubuntuforums.org/showthread.php?t=162709&highlight=Install+To+Usb+Hd]("http://www.ubuntuforums.org/showthread.php?t=162709&highlight=Install+To+Usb+Hd")
Its Near The Bottom. 8)

---

### Post by Ben Cook2 on 2006-11-13
Hi,

I Just Installed Kubuntu Using The Instructions Provided. [Make The Appropriate Alterations] But I Came Acroos A Problem That MKINITRAMFS Would Not Accept /media/sdc2/lib/modules/2.6.15-26-386 So I Used /lib/modules/2.6.15-26-386 Which Uses The Cd. So I Rebooted & GRUB Says Code 29 & Something About A Disk Write Error. What Could My Problem Be? I Have Posted My mkinitramfs.conf File & My modules File. I Can't Post My Initrd.img Because I Have Dialup But I Could Get You Sections Of Its Internal Code, If You Told Me How To. I Have Provided The Original Files In txt Format As Well.I Hoped This Was Going To Be Easy...

> WAIT=12
#
# initramfs.conf
#

# BUSYBOX: [ y | n ]
#
# Use busybox if available.  You MUST use the -static version
#

BUSYBOX=y

#
# BOOT: [ local | nfs ]
#
# local - Boot off of local media (harddrive, USB stick).
#
# nfs - Boot using an NFS drive as the root of the drive.
#

BOOT=local

#
# MODULES: [ most | netboot | dep | list ]
#
# most - Add all framebuffer, acpi, filesystem, and harddrive drivers.
#
# netboot - Add the base modules, network modules, but skip block devices.
#
# dep - Try and guess which modules to load.
#
# list - Only include modules from the 'additional modules' list
#

MODULES=most

#
# NFS Section of the config.
#

#
# DEVICE: ...
#
# Specify the network device, like eth0
#

DEVICE=eth0

#
# NFSROOT: [ auto | HOST:MOUNT ]
#

NFSROOT=auto

# Hardcode partition to resume from so it doesn't have to be specified
# on the command line.  If the initramfs-tools package installation was
# able to guess a reasonable default for this setting, you can find it
# configured in conf.d/resume.  Manually specifying "resume=" on your
# kernel command line will always override this setting.

#RESUME=

> # List of modules that you want to include in your initramfs.
#
# Syntax:  module_name [args ...]
#
#
# This might be good choices:
#
# raid1
# 
echi-hcd
usb-storage
scsi_mod
sd_mod

---

