---
title: "Shut down screen freezes"
date: 2019-08-06
forum: General Help
---

### Post by yneopany on 2019-08-06
I have 18.04 version of UBUNTU. My shot down screen freezes and I have to press the power button and force shut down.. it's been more than a month nothing has been resolved yet.. please help

---

### Post by #&amp;thj^% on 2019-08-06
Can you add this:
```
cat /etc/default/grub
```

---

### Post by yneopany on 2019-08-11
I tried but I got "no such file or directory"

---

### Post by howefield on 2019-08-11
> **yneopany said:**
> I tried but I got "no such file or directory"

Then it is likely that you have made a mistake in typing the instruction.

Try again and if the same results then copy/paste the terminal input/output back here.

---

### Post by yneopany on 2019-08-13
cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force"
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


This is the message i got

---

