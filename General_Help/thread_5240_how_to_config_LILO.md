---
title: "how to config LILO ?"
date: 2004-11-16
forum: General Help
---

### Post by kixvn on 2004-11-16
i chose JFS in the installation of Hoary array 1 (just want to try something new .. also, because i use IBM laptop, so just want to try IBM filesystem),
but it can't install GRUB, LILO can
so i go with LILO

the problem is, no matter how i config the file at /etc/lilo.conf , when i reboot it always boot into ubuntu

i attach here my lilo.conf so can someone give me some hint ? :)

another thing is that it takes some really long time to check the BIOS, how can i disable it ?

tks

> 
# /etc/lilo.conf - See: `lilo(8)' and `lilo.conf(5)',
# ---------------       `install-mbr(8)', `/usr/share/doc/lilo/',
#                       and `/usr/share/doc/mbr/'.

# +---------------------------------------------------------------+
# |                        !! Reminder !!                         |
# |                                                               |
# | Don't forget to run `lilo' after you make changes to this     |
# | conffile, `/boot/bootmess.txt' (if you have created it), or   |
# | install a new kernel.  The computer will most likely fail to  |
# | boot if a kernel-image post-install script or you don't       |
# | remember to run `lilo'.                                       |
# |                                                               |
# +---------------------------------------------------------------+

# Specifies the boot device.  This is where Lilo installs its boot
# block.  It can be either a partition, or the raw device, in which
# case it installs in the MBR, and will overwrite the current MBR.
#
boot=/dev/hda

# Specifies the device that should be mounted as root. (`/')
#
root=/dev/hda8

# Enable map compaction:
# Tries to merge read requests for adjacent sectors into a single
# read request. This drastically reduces load time and keeps the
# map smaller.  Using `compact' is especially recommended when
# booting from a floppy disk.  It is disabled here by default
# because it doesn't always work.
#
compact

# Installs the specified file as the new boot sector
# You have the choice between: text, bmp, and menu
# Look in lilo.conf(5) manpage for details
#
install=menu

# Specifies the location of the map file
#
map=/boot/map

# You can set a password here, and uncomment the `restricted' lines
# in the image definitions below to make it so that a password must
# be typed to boot anything but a default configuration.  If a
# command line is given, other than one specified by an `append'
# statement in `lilo.conf', the password will be required, but a
# standard default boot will not require one.
#
# This will, for instance, prevent anyone with access to the
# console from booting with something like `Linux init=/bin/sh',
# and thus becoming `root' without proper authorization.
#
# Note that if you really need this type of security, you will
# likely also want to use `install-mbr' to reconfigure the MBR
# program, as well as set up your BIOS to disallow booting from
# removable disk or CD-ROM, then put a password on getting into the
# BIOS configuration as well.  Please RTFM `install-mbr(8)'.
#
# password=tatercounter2000

# Specifies the number of deciseconds (0.1 seconds) LILO should
# wait before booting the first image.
#
delay=3

# You can put a customized boot message up if you like.  If you use
# `prompt', and this computer may need to reboot unattended, you
# must specify a `timeout', or it will sit there forever waiting
# for a keypress.  `single-key' goes with the `alias' lines in the
# `image' configurations below.  eg: You can press `1' to boot
# `Linux', `2' to boot `LinuxOLD', if you uncomment the `alias'.
#
message=/boot/bootmess.txt
	prompt
	delay=100
	timeout=100

# Specifies the VGA text mode at boot time. (normal, extended, ask, <mode>)
#
# vga=ask
# vga=9
#
vga=normal

# Kernel command line options that apply to all installed images go
# here.  See: The `boot-prompt-HOWTO' and `kernel-parameters.txt' in
# the Linux kernel `Documentation' directory.
#
# append=""
 
# If you used a serial console to install Ubuntu, this option should be
# enabled by default.
# serial=

#
# Boot up Linux by default.
#
default=Linux

image=/vmlinuz
	label=Linux
	read-only
#	restricted
#	alias=1

	initrd=/initrd.img

# If you have another OS on this machine to boot, you can uncomment the
# following lines, changing the device name on the `other' line to
# where your other OS' partition is.
#
# other=/dev/hda4
#	label=HURD
#	restricted
#	alias=3
other=/dev/hda1
	label=Windows
#	restricted
#	alias=2



---

### Post by TravisNewman on 2004-11-16
Did you follow the instructions at the top of the file and run lilo after making changes?

---

### Post by pgoya on 2004-11-16
Try to [COLOR=Red]eneable[/COLOR] the [COLOR=Red]LBA mode[/COLOR] in the HD config at setup of your laptop. If it is "AUTO", change to "LBA".

---

### Post by nkdb on 2004-11-17
You must run cmd >lilo after llilo.conf file modifications.

>lilo write on MBR (Master Boot Record) new instructions. Without that, modifications are not tke into account ... ;)

---

### Post by kixvn on 2004-11-17
[QUOTE=nkdb]You must run cmd >lilo after llilo.conf file modifications.

>lilo write on MBR (Master Boot Record) new instructions. Without that, modifications are not tke into account ... ;)[/QUOTE]
 ya, it works
(i thought i did it but may be i didn't :D )
just a side question, how can I configure GRUB to work with JFS ? (since i can't do that in the installation stage)
tks all :)

---

