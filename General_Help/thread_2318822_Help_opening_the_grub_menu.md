---
title: "Help opening the grub menu"
date: 2016-03-29
forum: General Help
---

### Post by alexander-m-rankin on 2016-03-29
Ok, so I have ubuntu installed on one harddrive, and windows 10 on another. The only way for me to boot into windows (because I can't open the grub menu) is to unplug the ubuntu harddrive. When I press esc at boot, it shows the menu for a nano second then goes to the grub terminal. My grub config file is:
```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=3
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
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```
Thank you for the help [IMG]http://ubuntuforums.org/images/icons/icon12.png[/IMG]

---

### Post by oldfred on 2016-03-29
Newer UEFI system or older BIOS/MBR system?

       But may be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by alexander-m-rankin on 2016-03-29
Ok, here is the pastebin link to the summary:
[http://paste.ubuntu.com/15554398/](http://paste.ubuntu.com/15554398/)

---

### Post by oldfred on 2016-03-29
UEFI & BIOS are not really compatible.
Once you start booting in one mode you cannot switch. Or grub only boots other systems in same boot mode.

You have Windows in BIOS boot mode with MBR partitioning on sda.
And you have Ubuntu with UEFI boot mode on sdb.

And you still have Windows hibernated, or its fast start up.

---

### Post by alexander-m-rankin on 2016-03-31
Ok, Thank you!

---

