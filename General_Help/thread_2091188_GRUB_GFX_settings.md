---
title: "GRUB GFX settings"
date: 2012-12-04
forum: General Help
---

### Post by cecilieaux on 2012-12-04
Problem: In the course of trying to fix the initial display so that it is the standard terminal menu (and large enough for my eyes) I have used both the configurator and gedit and, while the display is fine, I keep getting a GFX related error of one kind or another no matter what I do. I'm also getting a screen dump of Linux setting up until the black Ubuntu screen with the dots.

How do I get back to the standard terminal menu WITHOUT the subsequent error upon choosing Ubuntu and WITHOUT the scrolling dumps of very techie stuff before the  Ubuntu screen with the dots?

My System: a Dell with 3GB RAM, plenty of storage, dual-booting Windows XP (need it for some work stuff) and Ubuntu 12.04 LTS. GRUB 1.99.

Thanks in advance!

---

### Post by oldfred on 2012-12-05
The quiet splash settings normally hide the loading process. Did you remove one or the other in grub?
And do you perhaps have some error in grub.

Post this from terminal:
 cat /etc/default/grub

default for this line from mine:
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

---

### Post by cecilieaux on 2012-12-06
> **oldfred said:**
> The quiet splash settings normally hide the loading process. Did you remove one or the other in grub?
And do you perhaps have some error in grub.

Post this from terminal:
 cat /etc/default/grub

default for this line from mine:
OK, here's the listing (cat /etc/default/grub) from terminal:

> # If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT="saved"
#GRUB_HIDDEN_TIMEOUT="0"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="splash"
#GRUB_CMDLINE_LINUX="vga=800x600"
GRUB_SAVEDEFAULT="true"

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
GRUB_TERMINAL="console"

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
# GRUB_GFXMODE="800x600x8"
# GRUB_GFXPAYLOAD="0x0x0x0,0x0"
GRUB_GFXMODE="auto"

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID="true"

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

#UNNAMED_OPTION=""


---

### Post by oldfred on 2012-12-06
If you do not want to see the boot process add quiet next to splash like mine posted above.

I have not seen auto, does that work?
GRUB_GFXMODE="auto"
Most have just inserted the exact settings which it looks like you experimented with.
The the grub setting is just for grub, not a parameter passed to the kernel.

Some Intel need the size passed and vga= settings are obsolete. Change to your exact screen size settings, frame rate, & freq This goes next to quiet splash:
       Force Intel Video mode as boot parameter in grub menu for newer systems
video=1280x1024-24@60
and if that doesn't work you can try
video=VGA-1:1280x1024-24@60
    

       Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)


[LIST]
[*]Older Intel video card: i915.modeset=1 or i915.modeset=0 newer:  i915.i915_enable_rc6=1
[*]nVidia: nomodeset
[*]Generic: xforcevesa or nouveau.modeset=0
[*]Radeon: radeon.modeset=0
[/LIST]

---

### Post by cecilieaux on 2012-12-15
Still get "unknown command: gfxmode" and The Matrix-like startup for a while. Sigh!

Here's the grub file

> # If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT="saved"
#GRUB_HIDDEN_TIMEOUT="0"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="splash quiet"
#GRUB_CMDLINE_LINUX="vga=800x600"
GRUB_SAVEDEFAULT="true"

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
GRUB_TERMINAL="console"

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
# GRUB_GFXMODE="800x600x8"
# GRUB_GFXPAYLOAD="0x0x0x0,0x0"
GRUB_GFXMODE="1280x1024x24"

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID="true"

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

#UNNAMED_OPTION=""


---

### Post by oldfred on 2012-12-15
You have disabled graphical terminal, so do you get a command line boot?

What does recovery mode give, same errors?

You may need other boot parameters.

---

### Post by cecilieaux on 2012-12-17
I changed GRUB_CMDLINE_LINUX_DEFAULT="splash quiet" to GRUB_CMDLINE_LINUX_DEFAULT="splash" and the Matrix-like scrolling (command line boot, I guess) stopped. Now it goes straight to the dark screen with Ubuntu and the dots, while the system is loading. 

One problem solved. Yayy!!!

It still says "command unknown GFXMODE" and asks to press to continue, I don't know if this is GRUB or Ubuntu. I'll try the recovery mode, although that worries me.

---

### Post by cecilieaux on 2012-12-17
> **oldfred said:**
> You have disabled graphical terminal, so do you get a command line boot?

What does recovery mode give, same errors?

You may need other boot parameters.
The recovery mode does not give the same errors. I mean, obviously it doesn't do the splash screen, but no unknown comman, either.

I'm gonna try disabling GRUB_GFXMODE="1280x1024x24"

---

### Post by steeldriver on 2012-12-17
did you actually run 'vbeinfo' at the grub prompt to check it supports 1280x1024x24? when I do that on my box I see only 1280x1024x16 or 1280x1024x32

---

### Post by cecilieaux on 2012-12-17
will try

(disabling did nothing, BTW)

---

### Post by cecilieaux on 2012-12-17
> **steeldriver said:**
> did you actually run 'vbeinfo' at the grub prompt to check it supports 1280x1024x24? when I do that on my box I see only 1280x1024x16 or 1280x1024x32
I did vbeinfo (is there something to stop the scolling screen?). I saw 1280x1024x32 and at the end Preferred Mode: 1280x1024.

---

### Post by cecilieaux on 2012-12-17
In the course of all this I pressed 'e' for edit at the grub prompt and got an edit screen with a list of commands, including

> gfxmode $linux_gfx_mode

Presumably, this is the culprit? But I didn't know what I had found so I left it.

I'm going to try restoring GRUB_GFXMODE=

but with 1280x1024x32

---

### Post by cecilieaux on 2012-12-17
Nope!

I even tried erasing the strange gfxmode $linux_gfx_mode line.

Nuthin'

OK. I gotta get stuff done, so if anyone has a brilliant idea, I'll try it.

---

### Post by cecilieaux on 2013-01-08
SOLUTION !!!!!!!!!!!!!!!!!!!!

Found at [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

They mentioned an application called Boot-Repair, it's a GUI to install, reinstall GRUB.

Instructions here: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

I reinstalled and the problem is gone. ):P

---

