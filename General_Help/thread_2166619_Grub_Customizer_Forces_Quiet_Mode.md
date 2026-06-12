---
title: "Grub Customizer Forces Quiet Mode"
date: 2013-08-10
forum: General Help
---

### Post by mrcpuhead on 2013-08-10
I'm running Ubuntu 12.04 LTS and used Grub Customizer to set up my boot menu and options.  I've set a background picture and custom resolution and font settings.  Even though I didn't specify the 'quiet' kernel parameter, when I select ubuntu from the boot menu, the system leaves the background picture up and never displays startup messages - just goes directly into the desktop environment.  What gives?

Here's my grub file contents:

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT="3"
#GRUB_HIDDEN_TIMEOUT="0"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="noapic"
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
GRUB_GFXMODE="1024x768x24"

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID="true"

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
GRUB_INIT_TUNE="480 440 1"

export GRUB_MENU_PICTURE="/home/joe/installs/Mac-os-x-Wallpapers/Lion.png"
export GRUB_COLOR_NORMAL="white/black"
export GRUB_COLOR_HIGHLIGHT="light-magenta/black"
GRUB_SAVEDEFAULT="false"
GRUB_FONT="/boot/grub/unicode.pf2"

---

