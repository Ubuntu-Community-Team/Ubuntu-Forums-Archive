---
title: "No graphical LUKS password prompt with plymouth theme installed"
date: 2019-02-13
forum: General Help
---

### Post by toad007toad007 on 2019-02-13
So i got plymouth working so that it displays the theme upon entry of my disk encryption key code, however, I am only prompted for the keycode with a text prompt. Previously before plymouth install I had the ubuntu graphical display, but since then it only shows text. I messed around with grub config file a bunch to get the plymouth theme to display before I realized that my theme was from an older version of plymouth and had the wrong directory location in the .plymouth file, so once I edited that the theme does display after I enter my encryption key. Ideally, I would like the theme to display with the key prompt. Here is my grub file...

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=1
GRUB_RECORDFAILT_TIMEOUT=$GRUB_TIMEOUT
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
GRUB_GFXMODE=1920x1080x32
GRUB_GFXPAYLOAD_LINUX=wxh
GRUB_VIDEO_BACKEND="vbe"

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

Any ideas on where to start and where I might have mucked something up? Any help is appreciated! Thank you all in advance.

---

### Post by toad007toad007 on 2019-02-13
Got it working after deleting the addition I put into /etc/initramfs-tools/modules

Please delete thread...

---

