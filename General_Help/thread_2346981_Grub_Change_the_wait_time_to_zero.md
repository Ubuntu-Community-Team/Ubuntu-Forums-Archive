---
title: "Grub: Change the wait time to zero"
date: 2016-12-20
forum: General Help
---

### Post by lynx6 on 2016-12-20
Hello,

I'm having a problem with Grub do *Lubuntu 16.04.1*
Lubuntu is in dual boot with Windows, and I would like to leave the standby time as 0 (zero), I already edited the Grub file I was able to change to 1 (one) second, but for 0 (zero) I still could not.
When I set 0 (zero) to restart the standby time is in 10 (ten) seconds.
I edit the file again and put 1 (one) again and this time is right.

The line I change is this:
GRUB_TIMEOUT=1

Maybe I need to change some line, but I do not know which one.


Note: whenever I make any changes use the command:
[I]sudo update-grub

[/I]Thank You.

---

### Post by Keith_Helms on 2016-12-20
If you don't want the grub menu to display at all and you just want it to automatically boot the default os, uncomment the following line:
```
#GRUB_HIDDEN_TIMEOUT=0
```

---

### Post by lynx6 on 2016-12-21
Hello Keith_Helms,

I have already made this change but the Grub menu continues to appear.
Obs.: I put Windows as the default system to start.

---

### Post by lynx6 on 2016-12-21
The Grub file looks like this:

*# If you change this file, run 'update-grub' afterwards to update*
*# /boot/grub/grub.cfg.*
*# For full documentation of the options in this file, see:*
*#   info -f grub -n 'Simple configuration'*

*GRUB_DEFAULT=4*
*GRUB_HIDDEN_TIMEOUT=0*
*GRUB_HIDDEN_TIMEOUT_QUIET=true*
*GRUB_TIMEOUT=1*
*GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`*
*GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"*
*GRUB_CMDLINE_LINUX="locale=pt_BR"*

*# Uncomment to enable BadRAM filtering, modify to suit your needs*
*# This works with Linux (no patch required) and with any kernel that obtains*
*# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)*
*#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"*

*# Uncomment to disable graphical terminal (grub-pc only)*
*#GRUB_TERMINAL=console*

*# The resolution used on graphical terminal*
*# note that you can use only modes which your graphic card supports via VBE*
*# you can see them in real GRUB with the command `vbeinfo'*
*#GRUB_GFXMODE=640x480*

*# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux*
*#GRUB_DISABLE_LINUX_UUID=true*

[I]# Uncomment to disable generation of recovery mode menu entries

Obs.: [/I]I put Windows as a system to start.

---

### Post by Keith_Helms on 2016-12-22
The more I looked into this, the harder it appears to be to make grub do what you want - just boot into a default os without waiting or displaying a menu.  Options that supposedly do that seem to be either ignored or overridden.  I give up.  Maybe somebody else knows the trick.

---

### Post by lynx6 on 2017-01-13
Guys, I got it right by leaving it this way:

*GRUB_DEFAULT=4*
*GRUB_HIDDEN_TIMEOUT=1*
*GRUB_HIDDEN_TIMEOUT_QUIET=true*
[I]GRUB_TIMEOUT=.01

[/I]
Note: You can set a smaller delay using **.01**, or even **.001**, so fast that you probably will not notice the Grub options!
I hope you help other users

---

