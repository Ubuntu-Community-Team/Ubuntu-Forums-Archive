---
title: "resolution problem......plz help"
date: 2008-02-15
forum: General Help
---

### Post by chaitanya.iit on 2008-02-15
hi guys!

i am having problem with my [SIZE="5"]screen resolution[/SIZE] in gusty.
when the comp is booting a screen pops up saying

[SIZE="5"]"Not Optimim Mode -Recommended mode 1024*768 60hz."[/SIZE]

And after few minutes it is going into command mode with [SIZE="5"](initramfs)[/SIZE].

i typed following command[SIZE="5"] "(initramfs):dpkg-reconfigure xserver -xorg"[/SIZE].

Then it is saying[SIZE="5"](initramfs):/bin/sh: dpkg-reconfigure command not found[/SIZE]

And the [SIZE="5"]comp is finally failing to start[/SIZE]...even the sudo command returned the same result --not found

plzz help ..........

and by the way i am using [SIZE="5"]D102[/SIZE] motherboard which has [SIZE="5"] ATI[/SIZE] inbuilt graphics card

---

### Post by mbsullivan on 2008-02-15
Hi chaitanya.iit,

When you're booting up, try entering recovery mode. To do this, press escape when Grub is counting down from 5...0 before loading your kernel. The recovery mode should be labeled, and will probably be the second option on the list.

In recovery mode, X will not be started, so hopefully you will not get your error, and you can freely work with all available files on your harddrive.

As for your problem... reconfiguring xserver-xorg seems as good of a start as any. Have you made any changes recently (like getting a new monitor, etc)? I've experienced similar error messages before, but they didn't bomb everything like you're describing, so there may be an underlying problem.

Hope this helps! Let me know what you find in recovery mode.
Mike

---

