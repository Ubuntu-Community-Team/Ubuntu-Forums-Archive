---
title: "grub config"
date: 2013-01-22
forum: General Help
---

### Post by shawn on 2013-01-22
Hi, I would really like to see the text mode boot, without all the colours and graphics. I've looked through a few things on the net and managed to get it so that the menu and graphics don't show but the screen just goes purple(ish) and stays like that until the login screen shows.

/etc/default/grub :


```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT="0"
GRUB_HIDDEN_TIMEOUT="0"
GRUB_HIDDEN_TIMEOUT_QUIET="false"
GRUB_TIMEOUT="0"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT=
GRUB_CMDLINE_LINUX="text"
GRUB_GFXMODE="1280x1024x32"
GRUB_GFXPAYLOAD_LINUX="keep"
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

What am I doing wrong, or is it not possible to see the boot text like in the old days?

---

### Post by Bashing-om on 2013-01-22
shawn; Hi !

If what you want is to see the boot messages. Then edit /etc/default/grub line to be:
> GRUB_CMDLINE_LINUX_DEFAULT=""Some versions of ubuntu if one inserts the term text between the quote marks gets a terminal login.

 (In your output the line is duplicated and probably causing problems)

Following the directions within grub should also work:
> # Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=consoleWhich means if the "#' character is removed, the line will be parsed. Login then will be from terminal.

Good read on grub:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

