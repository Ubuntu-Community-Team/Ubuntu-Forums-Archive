---
title: "GRUB on second monitor"
date: 2022-09-06
forum: General Help
---

### Post by Olivares on 2022-09-06
I didn't know whether to post this one in general help or in installations & upgrades. I have just completed a fresh installation of Ubuntu 22.04 and Windows 10. Refer my thread 'no EFI partition was found.' Post installation I now find that the GRUB menu pops up on my second monitor, my TV, and not on the PC's monitor. I looked around on the internet for a solution; one answer I saw was to uncomment the GRUB line 'GRUB_GFXMODE=640x480.' I tried this but it didn't work. At present the only solution I have is to unplug the second monitor. I see I posted a request for the same problem back in June 2020 but didn't get a response. Obviously I fixed the problem back then, but I can't now remember what I did.

FYI the resolution on the first monitor Samsung 19" is 1600 x 900, on the Sony TV it is 1920 x 1080. The Samsung has a DVI cable, while the Sony is connected with an HDMI cable. Here is my GRUB script:

```
# If you change this file, run 'update-grub' afterwards to update# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
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
# GRUB_GFXMODE=640x480


# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true


# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"


# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

Thanks in advance.

---

### Post by MAFoElffen on 2022-09-06
Grub does not do dual monitors at different resolutions. At that stage of the boot process, your only get the primary monitor, then kernel boot... then graphics layer...

With Dual Monitors it will depend on the graphics GPU, which graphics engine you are using, and if you do mirroring or different desktops for each (left, right) in how you go about configuring those... There are multiple ways of doing that , based on those choices.

---

