---
title: "Set Resolution in tty for nvidia"
date: 2012-11-24
forum: General Help
---

### Post by tornadof3 on 2012-11-24
Hello

I have the proprietary nvidia driver for a GeForce 210 correctly installed and running great for my desktop @ 1920x1080. However, if I cntrl-alt-F{1-8} for a tty, the resolution is very low, as indeed it is whilst booting, which makes a terminal session difficult. How can I change this eg to 1920x1080 or anything better than what it currently is (maybe 640x480).

Many thanks

---

### Post by ranger1021994 on 2012-11-24
> **tornadof3 said:**
> Hello

I have the proprietary nvidia driver for a GeForce 210 correctly installed and running great for my desktop @ 1920x1080. However, if I cntrl-alt-F{1-8} for a tty, the resolution is very low, as indeed it is whilst booting, which makes a terminal session difficult. How can I change this eg to 1920x1080 or anything better than what it currently is (maybe 640x480).

Many thanks

Type :
```
sudo gedit /etc/default/grub
```

Search for :
```
GRUB_GFXMODE
```

Replace it with : 
```
GRUB_GFXMODE="1920x1080"
```

Then run :
```
sudo update-grub
```

Hope it helps :)

---

### Post by tornadof3 on 2012-11-24
Thank you for your reply!

So I edited the grub file and ran sudo update-grub. Tried both with " " marks and without and rebooted twice etc. No errors, but it didn't change the tty resolution?

/etc/default/grub:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nmi_watchdog=0 nowatchdog"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE="1920x1080"

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

---

### Post by Anaximander Thales on 2012-11-24
You'll need to set the gfxpayload in /etc/grub.d/00_header.

I would also set:
GRUB_GFXMODE=auto

This sets the terminal to use what ever grub is using.  This way, you don't have to figure out which one works.

edit /etc/grub.d/00_header 
search for: set gfxmode=${GRUB_GFXMODE} on the next line 
insert: set gfxpayload=keep 

verify that the new line is before insmod gfxterm

then: update-grub

[Source]("http://wiki.debian.org/GrubTransition#Grub2andtheVGAparameter")

If you have issues, here's mine (there is a slight difference from what has been shown here).

```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
#GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=auto

[COLOR="Red"]# Uncomment to allow the kernel to use the same resolution by grub
GRUB_GFXPAYLOAD_LINUX=keep[/COLOR]

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

---

### Post by tornadof3 on 2012-11-25
Thanks for the suggestion. I made the changes but it caused problems. My graphical session was still fine, but ctrl-alt-F1 just didn't work, but it did put odd black pixel locks onto my graphical session. I had to undo the "keep" statement and the =auto statements. I can confirm that I did edit the 00_headers file and update-grub, as well as trying several different combinations. Not to worry, perhaps it just isn't to be!

---

### Post by dentex on 2013-05-29
> **Anaximander Thales said:**
> 
[COLOR=Red]# Uncomment to allow the kernel to use the same resolution by grub
GRUB_GFXPAYLOAD_LINUX=keep[/COLOR]


Thank you very much.
This is the only working solution I found all over the whole internet (at least for me).
Don't know why many people used:
```
GRUB_GFXPAYLOAD=keep

```instead of
```
GRUB_GFXPAYLOAD_LINUX=keep
```
into /etc/default/grub.

Then, I have also there:
```
GRUB_GFXMODE=1680x1050  # not "auto"
GRUB_GFXPAYLOAD_LINUX=keep
```

and, into /etc/grub.d/00_header, some modified lines, as:
```
if [ "x${GRUB_GFXMODE}" = "x" ] ; then GRUB_GFXMODE=1680x1050 ; fi
```
and, below, the block:
```
  set gfxmode=${GRUB_GFXMODE}
  set gfxpayload=keep
  load_video
  insmod gfxterm
```

My system:
```
$ lsb_release -a
No LSB modules are available.
Distributor ID:    LinuxMint
Description:    Linux Mint 15 Olivia
Release:    15
Codename:    olivia

$ uname -rvmos
Linux 3.8.0-22-generic #33-Ubuntu SMP Thu May 16 15:17:14 UTC 2013 x86_64 GNU/Linux
```

video card:
```
  Vendor: pci 0x10de "nVidia Corporation"
  Device: pci 0x0622 "G94 [GeForce 9600 GT]"
```

---

