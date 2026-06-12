---
title: "change terminal resolution"
date: 2013-09-21
forum: General Help
---

### Post by fennectech2 on 2013-09-21
Okay i am trying to change the resolution of the linux command line at bootup.i want to use the native resolution of my laptops panel wich is 1024x768 i cant figure out how to do it so i thought id come here.
im useing lubuntu raring ringtail on a sony vaio pcg-993l
hers my
 /etc/default/grub file 
I have done update-grub as superuser

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="nosplash debug --verbose"
GRUB_CMDLINE_LINUX="video=VGA-1:1024x768" 

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1024x768
GRUB_GFXPAYLOAD_LINUX=keep
# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

GRUB_GFXPAYLOAD_LINUX=1024x768x32

---

