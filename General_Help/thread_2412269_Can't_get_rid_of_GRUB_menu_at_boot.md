---
title: "Can't get rid of GRUB menu at boot"
date: 2019-02-10
forum: General Help
---

### Post by laserburn2 on 2019-02-10
Ubuntu 18.04 after some update all of a sudden started showing Grub menu with 30 seconds timer. I installed Grub Customizer and unchecked 'show menu' and 'look for other operating systems' to get rid of Grub screen, as I don't have other operating systems, but no luck, menu still comes up at boot. Took a look at grub.cfg to try to understand what could be wrong, but booting in Ubuntu is getting more and more complicated, I can't parse this thing any more (file attached with extension change).

Can anyone tell me what could be wrong and how to get rid of the GRUB menu?

---

### Post by yancek on 2019-02-10
The changes needed to be made are not in the grub.cfg file but rather in the /etc/default/grub file.  Take a look at the link below, the first method at the top of the page to try to make the change.  According to the site, using Grub Customizer the way you did is supposed to work.  Check this file to see if it shows as explained at the link below.

[http://ubuntuhandbook.org/index.php/2014/06/ubuntu-1404-hide-grub-menu/](http://ubuntuhandbook.org/index.php/2014/06/ubuntu-1404-hide-grub-menu/)

Another link with the info.

[https://linoxide.com/linux-how-to/hide-grub-boot-linux/](https://linoxide.com/linux-how-to/hide-grub-boot-linux/)

---

### Post by laserburn2 on 2019-02-10
Checked /etc/default/grub, it was already set up correctly. I added a line GRUB_HIDDEN_TIMEOUT_QUIET="true" just in case it makes some difference, but it doesn't. It's like  /etc/default/grub is not even consulted, no change I make there is applied to boot. Currently it's like this:

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT="0"
GRUB_TIMEOUT_STYLE="hidden"

GRUB_HIDDEN_TIMEOUT="0"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_DISABLE_OS_PROBER="true"

GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
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
#GRUB_GFXMODE="640x480"

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID="true"

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

---

### Post by CatKiller on 2019-02-10
> **laserburn2 said:**
> Checked /etc/default/grub, it was already set up correctly. I added a line GRUB_HIDDEN_TIMEOUT_QUIET="true" just in case it makes some difference, but it doesn't. It's like  /etc/default/grub is not even consulted, no change I make there is applied to boot.

You need to run update-grub for changes there to take effect.

---

### Post by dmnur on 2019-02-10
See this thread: [https://ubuntuforums.org/showthread.php?t=2412153](https://ubuntuforums.org/showthread.php?t=2412153)
There was a regression in new GRUB packages, should be fixed now. You probably just need to upgrade your system.

---

### Post by laserburn2 on 2019-02-10
> **dmnur said:**
> See this thread: [https://ubuntuforums.org/showthread.php?t=2412153](https://ubuntuforums.org/showthread.php?t=2412153)
There was a regression in new GRUB packages, should be fixed now. You probably just need to upgrade your system.

Yes, that was it. Upgraded and it works now. Thank you.

---

