---
title: "changed grub settings"
date: 2019-08-21
forum: General Help
---

### Post by jgw on 2019-08-21
I just changed my grub file settings (/etc/default/grub/)  My goal was to get to the grub menu.  the 2 settings I changed now look like:
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10

It worked fine and I was able to get to the menu.
I then updated grub, checked the file system and re-booted.
I then got an error box telling me:
xrandr failed to get size of gamma output
xrandr failed to find output vga0

I then went to the settings to check my resolution and there was no resolution.

I then read further and it said that the resolution might be screwed up and to re-boot and things will be dandy.
I rebooted and things are now dandy.

I have no idea what happened but I thought I would post this in case I really screwed it up and need to fix something.

Thank you..................

---

### Post by #&amp;thj^% on 2019-08-21
It would be helpful if you add:
```
cat /etc/default/grub
```
Sample of mine &&***** Do Not Copy Mine*****: (This is an Arch Config)
```
# GRUB boot loader configuration

GRUB_DEFAULT=0
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR="Arch"
GRUB_CMDLINE_LINUX_DEFAULT='resume=/dev/sda3 apparmor=1 security=apparmor ipv6.disable=1'
GRUB_CMDLINE_LINUX="scsi_mod.use_blk_mq=1 quiet"

# Preload both GPT and MBR modules so that they are not missed
GRUB_PRELOAD_MODULES="part_gpt part_msdos"

# Uncomment to enable booting from LUKS encrypted devices
#GRUB_ENABLE_CRYPTODISK=y

# Uncomment to enable Hidden Menu, and optionally hide the timeout count
#GRUB_HIDDEN_TIMEOUT=5
#GRUB_HIDDEN_TIMEOUT_QUIET=true

# Uncomment to use basic console
GRUB_TERMINAL_INPUT=console

# Uncomment to disable graphical terminal
#GRUB_TERMINAL_OUTPUT=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via 

# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=auto

# Uncomment to allow the kernel use the same resolution used by grub
GRUB_GFXPAYLOAD_LINUX=keep

# Uncomment if you want GRUB to pass to the Linux kernel the old 

# format "root=/dev/xxx" instead of "root=/dev/disk/by-uuid/xxx"
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
GRUB_DISABLE_RECOVERY=true

# Uncomment and set to the desired menu colors.  Used by normal and 

# modes only.  Entries specified as foreground/background.
#GRUB_COLOR_NORMAL="light-blue/black"
#GRUB_COLOR_HIGHLIGHT="light-cyan/blue"

# Uncomment one of them for the gfx desired, a image background or a 

GRUB_BACKGROUND="/home/me/Pictures/bluedandelion.jpg"
#GRUB_THEME="/path/to/gfxtheme"

# Uncomment to get a beep at GRUB start
#GRUB_INIT_TUNE="480 440 1"

# Uncomment to make GRUB remember the last selection. This requires to
# set 'GRUB_DEFAULT=saved' above.
#GRUB_SAVEDEFAULT="true"

```
You should see a line with>:
```
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=auto

# Uncomment to allow the kernel use the same resolution used by grub
GRUB_GFXPAYLOAD_LINUX=keep

```

---

### Post by jgw on 2019-08-22
Thank you for the reply.

I am a genuine neophyte about grub so I will, until I learn more, just leave it alone.  

I have, incidentally, noticed that when I first boot in the morning the 'ubuntu', in the middle of the screen will start to blink and the screen blank.  when this starts it means that its never going to boot.  The answer seems to be to restart and the second time around it works just fine.  Strange but probably easier to live with than trying to fix it and screw it up (I seem to be a real expert at that! <G>)

---

### Post by jgw on 2019-08-28
Here is my grub file:

greg@gregdown:~$ cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
# GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT_STYLE=menu
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
greg@gregdown:~$

---

