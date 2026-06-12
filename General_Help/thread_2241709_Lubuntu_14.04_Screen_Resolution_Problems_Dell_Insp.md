---
title: "Lubuntu 14.04 Screen Resolution Problems Dell Inspiron 1100"
date: 2014-08-27
forum: General Help
---

### Post by csiebester on 2014-08-27
I installed Lubuntu on my Inspiron 1100 laptop which is apparently a laptop that hates linux because resolution problems occur in many Linux distros.  Everything is fine booting from CD but the computer will only allow 640x480 when booting from the hard drive.  There are a lot of very old solutions posted that are related to the xorg.conf file but that file no longer exists so I am wondering what to do.  There are people who have suggested copying the file when running the live CD which I do not know how to do, or writing my own file which I certainly don't know how to do.  Any help would be greatly appreciated.

---

### Post by sudodus on 2014-08-28
In another application I had a similar problem: The screen size was limited to 640x480 unless I activated

```
GRUB_TERMINAL=console
```

in the file **/etc/default/grub** and ran

```
sudo update-grub
```

Please come back if that quick solution does not work for you. In this case also post the output of this command, that should help identify the graphics chip or card

```
sudo lshw -C display
```

---

### Post by csiebester on 2014-08-28
Thanks so much Sudodus.  It works great now. 

For anyone else that stumbles across this problem I am posting my working /etc/default/grub file below.  I believe it has some other modifications though I've tried a bunch of things and I've lost track.  


# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
######GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.modeset=1"
GRUB_CMDLINE_LINUX_DEFAULT="vga=773 quiet nosplash" 
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
#GRUB_INIT_TUNE="480 440 1"

---

### Post by sudodus on 2014-08-29
Congratulations :KS

Please click on Thread Tools at the top of this page and mark this thread as SOLVED

---

