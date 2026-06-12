---
title: "After upgrading 12.10, s-video screen flickering"
date: 2013-01-19
forum: General Help
---

### Post by chiron80 on 2013-01-19
I have a computer hooked up to my old CRT TV using the s-video connection and running Mythbuntu. I do not have a monitor attached (just the TV), but I can SSH into the computer from my laptop.

It was working fine prior to my upgrade from 12.04 to 12.10. Since the upgrade, when the computer boots, it brings me to the log-in screen, but the screen is flickering as if the refresh rate or resolution is incorrect. I can just barely make out that my username is displayed on the screen, but everything on the screen is scrolling across the screen so fast that it is unusable. If I switch to a virtual console (ctrl+alt+F1) or shut down GDM (or lightdm) the virtual console is also flickering in the same way, so the problem isn't related to X.

I'm pretty sure I need to change something in the grub configuration (/etc/default/grub?) to fix this, but I'm not quite sure what.

I've already increased the time-out so that the grub menu is visible. When the computer boots, I can see the POST messages fine, I can see the grub count-down and hit "esc". I can see the grub-menu and choose advanced options, and that all displays just fine. Once I choose to boot Ubuntu, it says "Loading, please wait..." then the screen goes blank for a few seconds, then starts flickering.

Video card is an NVIDIA Corporation NV34 [GeForce FX 5200] (rev a1) (reported from lspci).

---

### Post by chiron80 on 2013-01-19
The current contents of my '/etc/default/grub' file.

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=20
GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_TIMEOUT=20
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

---

### Post by chiron80 on 2013-01-19
I was able to fix the problem by adding 'nomodeset' to the list of arguments after "GRUB_CMDLINE_LINUX_DEFAULT" in '/etc/default/grub'. My new '/etc/default/grub' file looks like this:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=5
GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_TIMEOUT=0
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

