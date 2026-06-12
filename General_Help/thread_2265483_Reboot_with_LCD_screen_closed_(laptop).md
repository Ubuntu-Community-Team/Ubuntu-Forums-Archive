---
title: "Reboot with LCD screen closed (laptop)"
date: 2015-02-15
forum: General Help
---

### Post by rafaelsartori on 2015-02-15
have a way to reboot the system when LCD closed?

i saw this thread: [http://ubuntuforums.org/showthread.php?t=2149751](http://ubuntuforums.org/showthread.php?t=2149751)

it seems to be the same problem, or much closer of it. any solution?

** if i reboot with open lcd, all goes ok.

---

### Post by rafaelsartori on 2015-02-15
i  have solved this issue adding acpi=off and pci=noacpi at grub conf, the best is that i dindt lost my others acpi functions, like vol+/vol- etc...
its now like this:

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="acpi=off pci=noacpi"


# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"
...

---

### Post by buzzingrobot on 2015-02-15
If the machine vents through the keyboard, keeping the lid closed after it has booted might not be the wisest thing to do.

---

