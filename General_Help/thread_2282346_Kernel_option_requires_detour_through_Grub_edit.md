---
title: "Kernel option requires detour through Grub edit"
date: 2015-06-13
forum: General Help
---

### Post by pbwolf on 2015-06-13
Here is my procedure to boot up in XUbuntu 15.04. 

 1. hold Shift down to make Grub show the menu; 

 2. type 'e' to edit the first item, Ubuntu;

 3. type F10 to let it boot.

If I don't take that scenic detour, the boot procedure freezes before it prompts me for a username.  If that happens I can press Ctrl-Alt-Del and try again to engage the Grub menu.

To be clear -- I don't change anything in Edit.  

The live image suffered the same freeze until I figured out to choose "nomodeset" from the F6 menu.  The installer duly wrote "nomodeset" into /etc/default/grub (which I have not changed), and I see "nomodeset" in the incantations when I'm "editing" in Grub.  But if I let Grub boot without the detour through 'e' and F10, Ubuntu behaves as though "nomodeset" were not there.

??

---

### Post by QDR06VV9 on 2015-06-13
Hi pbwolf 
Can you paste back the results of the code below
```
gedit /etc/default/grub
```

---

### Post by pbwolf on 2015-06-13
```

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
GRUB_CMDLINE_LINUX="nomodeset"

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

---

### Post by QDR06VV9 on 2015-06-14
> **pbwolf said:**
> ```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
[COLOR=#ff0000]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"[/COLOR]
GRUB_CMDLINE_LINUX="nomodeset"

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
The line in red [COLOR=#ff0000]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

[/COLOR][COLOR=#000000]N[/COLOR]eeds to read as below[COLOR=#ff0000]
[/COLOR] [B]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
[/B]to edit that open a terminal```
gksudo gedit /etc/default/grub
```
The line that has [COLOR=#ff0000]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
[/COLOR]
Change to[COLOR=#ff0000]

[/COLOR]```
**GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"**
```
Then run 
```
sudo update-grub
```
should do the trick.
Regards

---

### Post by pbwolf on 2015-06-16
Thanks runrickus.  What a difference there is between GRUB_CMDLINE_LINUX_DEFAULT and GRUB_CMDLINE_LINUX!

---

