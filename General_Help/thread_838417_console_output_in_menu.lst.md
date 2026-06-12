---
title: "console output in menu.lst"
date: 2008-06-23
forum: General Help
---

### Post by pjkoczan on 2008-06-23
Hi all. I was wondering if/how I could get boot output to go to both serial console and a monitor, and if there are any potential issues in doing this (like what happens if a monitor isn't attached).

I manage a bunch of servers, and while it's nice to have output go to serial console for remote administration, it's frustrating for when I actually have to be in the server room for debugging, since that same output is not piped to the screen by default.

Here's an excerpt from the /boot/grub/menu.lst file, it's auto-generated so it might look a little different than a default.

```

default=0
timeout=10
serial --unit=0 --speed=9600
terminal --timeout=10 serial console
...
title Ubuntu Linux (2.6.24-18-generic)
    root (hd0,0)
    kernel /boot/vmlinuz-2.6.24-18-generic ro apm=off root=LABEL=/ console=ttyS0,9600n8
    initrd /boot/initrd-2.6.24-18-generic

```

---

### Post by pjkoczan on 2008-06-24
I have this halfway figured out. If I add the parameter "console=tty0" to the grub boot arguments, it works...sort of.

It displays all the output to the serial console, but it only displays the output to the monitor up through module loading and SELinux initialization.

Any output of service or network initialization, init scripts, or my configuration tool (you know, the stuff I really care about) doesn't get displayed to the monitor.

I think it has to do with virtual terminals being set up (and thus tty0 being supressed), but I don't really know how to diagnose or fix the problem.

Any help for this would be appreciated.

---

