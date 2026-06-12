---
title: "Missing Recovery Mode"
date: 2012-11-30
forum: General Help
---

### Post by perilin on 2012-11-30
Whenever I go into the GRUB menu, there's no recovery mode, which is a problem because I need to access it.  I've looked around, but I can't find anything else that explains this problem.  Do I have to reinstall Ubuntu?

---

### Post by 2F4U on 2012-12-01
Are you saying that the method of pressing Shift to get into the grub menu, for example explained in this article, is not working for you?

[http://www.upubuntu.com/2012/09/how-to-install-nvidia-drivers-using.html](http://www.upubuntu.com/2012/09/how-to-install-nvidia-drivers-using.html)

---

### Post by perilin on 2012-12-01
No -- I can get to the GRUB menu, but Recovery Mode isn't there.

---

### Post by Wim Sturkenboom on 2012-12-01
Check the file _/etc/default/grub_

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
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
**[COLOR="Red"]#GRUB_DISABLE_RECOVERY="true"[/COLOR]**

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```
If the line in bold red does not have the '#' in front or is missing, modify or add it and save the file; note that you need root privileges to edit the file. Next run
```

sudo update-grub

```

---

### Post by perilin on 2012-12-01
No, wait, it didn't -- I didn't have my glasses on, I thought it did.

Recovery Mode is there now. :)

---

