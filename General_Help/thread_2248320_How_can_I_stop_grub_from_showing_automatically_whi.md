---
title: "How can I stop grub from showing automatically while booting?"
date: 2014-10-14
forum: General Help
---

### Post by Jatin_kaushal on 2014-10-14
Hi. I installed ubuntu 12.04 alongside ubuntu 14.04 and I want to automatically boot using ubuntu 12.04 without showing the list of OSs automatically. I want to make it show only when I press SHIFT. here is my /etc/default/grub file:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT="0"
#GRUB_HIDDEN_TIMEOUT="0"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="persistent"

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL="console"

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE="640x480"

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID="true"

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

---

### Post by Cliff_Simonds on 2014-10-14
Change GRUB_TIMEOUT="10" to GRUB_TIMEOUT=0

---

### Post by Jatin_kaushal on 2014-10-14
do I update-grub too?

---

### Post by Impavidus on 2014-10-14
Yes. And you need root permissions, so make that sudo update-grub.

Keep in mind that you have to do this from your 12.04 system. This is all assuming 12.04 is in control of grub, which is usually the case if 12.04 was installed last

---

