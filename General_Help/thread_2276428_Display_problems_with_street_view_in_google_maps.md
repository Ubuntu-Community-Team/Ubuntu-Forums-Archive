---
title: "Display problems with street view in google maps"
date: 2015-05-02
forum: General Help
---

### Post by Robbyx on 2015-05-02
My mouse moves but does nothing and the keyboard does not work other than using "Alt-Printscreen R" (which restarts the system)  when I go into the street view of google maps. Is there anything I can do about it?

Ram 4gb
Intel 2 core 
Card Nvidia G73 (GF7600 gs) 
Nouveau (driver currently running)

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
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=" 
# nomodeset noapic nolapic
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

### Post by tuxHulk on 2015-05-02
I personally have had issues using the Nouveau driver (I'm running a different card by the way GTX550 Ti), even with web pages occasionally. The only way I resolved my problem is using the NVIDIA binary driver (proprietary, tested) from 'Additional Drivers' in Software & Updates.

---

