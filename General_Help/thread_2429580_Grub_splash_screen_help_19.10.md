---
title: "Grub splash screen help 19.10"
date: 2019-10-20
forum: General Help
---

### Post by michaels24082 on 2019-10-20
Hello,

Would appreciate some help with grub, grub menu, and splash screen. I am currently running and recently upgraded to Ubuntu desktop 19.10 from 19.04. I wish to hide the grub boot screen and modify the splash screen to look like Fedora 30's splash screen. 



My goal is to have the grub boot menu hidden, spinner imposed on the bios boot screen with Ubuntu logo at the bottom, just like fedora has done. I have searched and made some modifications to grub. 
installed plymouth
```

sudo apt install plymouth-themes

```

All I have managed to do is make my grub menu black and white instead of magenta/purple and white, and complete remove the Ubuntu splash screen:


I have reset my grub config file to default as it is on install:
```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL="console"

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE="1024x768x16"

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID="true"

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```
```

sudo updage-grub

```

and still cannot get back to an out of the box fresh install experience. So, I need some help. First and foremost I wish to get back to the default grub menu and splash screen. Then I wish to learn how to modify the grub correclty so I can hide the grub menu unless invoked with key strokes at boot, and have a modified splash screen as mentioned above.

Any help will be greatly appreciated.

Thanks,
MIke

---

