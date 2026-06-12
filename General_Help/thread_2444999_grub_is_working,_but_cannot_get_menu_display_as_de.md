---
title: "grub is working, but cannot get menu display as default"
date: 2020-06-07
forum: General Help
---

### Post by tonystark on 2020-06-07
grub was working just fine on my system until yesterday.  I would boot, the EUFI splash would come up, then the grub menu.
Today, grub is still working, but the menu does not appear unless I hold down the shift key just after the EUFI splash.  If I do hold down the shift key, it works just fine.
This change happened after a software update, including new kernels in Ubuntu 18.04

Here is my /etc/default/grub file:
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

#GRUB_DEFAULT=4
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE='menu'
GRUB_HIDDEN_TIMEOUT=5
#GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=20
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
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
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
GRUB_INIT_TUNE="480 440 1"


I did check my /boot/grub/grub.cfg file (I know you're not supposed to edit it, I was just looking at it...) and it includes the following:
terminal_input console
terminal_output console
if [ "${recordfail}" = 1 ] ; then
  set timeout=30
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=menu
    set timeout=20
  # Fallback normal timeout code in case the timeout_style feature is
  # unavailable.
  else
    set timeout=20
  fi
fi


Note that it does say "set timeout_style=menu"

---

