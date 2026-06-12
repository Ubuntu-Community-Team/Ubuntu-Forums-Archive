---
title: "No consoles (CTRL+F[1-7]) on Ubuntu"
date: 2013-03-26
forum: General Help
---

### Post by Pixman on 2013-03-26
Hi folks,

I have the strangest problem. I have no /etc/inittab either. I heard recently, that with upstart, it's obsolete.
But I just can't find out how to get to the console / bash with CTRL+F[1-7] and I need this often, for example when restarting the X-Server.

Thanks for any help!

Sincerely,
Pix

[B]&#8364;dit: I just tested it blind. The consoles ARE being started. But I get no visuals, no text, my monitor goes to stand by.
[/B]

---

### Post by Pixman on 2013-03-26
Ok, I now see text when booting
> # If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT="0"
#GRUB_HIDDEN_TIMEOUT="0"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX="quiet splash"

# Uncomment to enable BadRAM filteing, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE="1680x1050"

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID="true"

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"


This is my configuration so far.
But as soon X starts, the consoles don't work anymore.

a "ps ax | grep tty" gives me this:
>  1519 tty4     Ss+    0:00 /sbin/getty -8 38400 tty4
 1527 tty5     Ss+    0:00 /sbin/getty -8 38400 tty5
 1540 tty2     Ss+    0:00 /sbin/getty -8 38400 tty2
 1542 tty3     Ss+    0:00 /sbin/getty -8 38400 tty3
 1552 tty6     Ss+    0:00 /sbin/getty -8 38400 tty6
 2599 tty1     Ss+    0:00 /sbin/getty --noclear -8 38400 tty1
 2717 tty7     Ss+    0:07 /usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch


So the consoles seem to run.

---

### Post by Impavidus on 2013-03-26
On my computer it's ctrl+**alt**+F[1-7]

---

### Post by schragge on 2013-03-26
+1 to what **Impavidus** said.
You can change from one text console to another with **Ctrl**+**F**[1-7] only when you already _are_ in a text console. To get a text console from an X session **Ctrl**+**Alt**+**F**[1-7] shortcuts must be used.

---

