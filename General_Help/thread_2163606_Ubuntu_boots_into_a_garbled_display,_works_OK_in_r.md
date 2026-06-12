---
title: "Ubuntu boots into a garbled display, works OK in recovery mode, but resolution suffer"
date: 2013-07-19
forum: General Help
---

### Post by nipunreddevil on 2013-07-19
Hi,

I am using Ubuntu 12.10 64 bit. Recently after updating my system, normal boot takes me to a garbled screen, hardly anything is visible. I think that boot is working fine, just that the display would have some issues.
If i start in recovery mode and then resume, display is OK, but with a much reduced resolution.

The following is the graphics card installed obtained via lspci command.

```
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Thames XT/GL [Radeon HD 7600M Series]

```

Following shows the installed kernel

Currently ```
uname -r
3.5.0-36-generic

```

Following are the contents of /etc/default/grub
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
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
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

---

### Post by elliotn on 2013-07-19
did u restart your machine?

---

### Post by nipunreddevil on 2013-07-19
This is not a single time problem. Out of 10 odd restarts, display would work fine in 1 or so. Otherwise i have to resort to recovery mode.

---

