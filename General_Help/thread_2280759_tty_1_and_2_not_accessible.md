---
title: "tty 1 and 2 not accessible"
date: 2015-06-02
forum: General Help
---

### Post by maxinstuff2 on 2015-06-02
tty 1 and 2 (via Alt+Ctrl+F1/2) seem to be running, but the keyboard shortcuts don't seem to work anymore.

tty 3 - 6 work fine and I can switch instantly between them. 1 and 2 SOMETIMES work, but very inconsistently. If I rapidly switch between tty's I can get to them sometimes.

I am running Kubuntu 14.04,2, and using lightdm.override to boot into terminal 1 (the only way I can consistently get there). Then using startx to get into KDE. Logging out in KDE gets me back to tty1.

F1 key is definitely working, if I press it with dolphin open it pops help files every time. 

I have messed with grub settings a bit (before finding out about lightdm.override), but I'm pretty sure I have it back to "defaults". /etc/default/grub looks like this:
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=1
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=0
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
#GRUB_GFXMODE=auto

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"


```

---

### Post by maxinstuff2 on 2016-01-16
This is old but I eventually figured out that I have to use the RIGHT Ctrl and Alt keys to get to tty1-3 and left Ctrl and Alt keys to get to tty4-7. 

Maybe this is a Kubuntu specific quirk..... In any case I'm marking this solved as I can reliably get to tty1 now.

---

