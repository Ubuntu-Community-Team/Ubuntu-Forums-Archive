---
title: "System suddenly stops booting up, and no boot log"
date: 2013-05-11
forum: General Help
---

### Post by Ranko Kohime on 2013-05-11
I'm fighting an issue with one of the family computers I administer that suddenly decided not to boot up today.  It goes about twelve seconds in according to the dmesg puke on the screen, and just, stops.  Not late enough in the boot cycle for me to grab access to a TTY.  It does respond to Ctrl+Alt+Del, spewing several lines too fast to read before rebooting.

It's also not writing anything to /var/log/boot or /var/log/dmesg, despite my setting BOOTLOGD_ENABLE to yes in /etc/default/bootlogd.

The available log on the screen provides me no useful clues as to why it's stopping, so, any suggestions?

Update: I've just been informed that a software update came up this morning, and was installed, and then the machine was shutdown.  This is on 12.10, BTW.

---

### Post by tgalati4 on 2013-05-11
Try booting a Live DVD or USB stick.  If this is a desktop computer did you clean it out and reseat all of the internal connections?  I would suspect a bad power supply.  How old is the machine?

If the power supply is weak, unplug the disk drive and just try booting into a Live session.

---

### Post by Ranko Kohime on 2013-05-11
It's a laptop, and it boots from the Live just fine.  Power is not an issue, I spent two hours troubleshooting it on battery, without a hiccup using my Live USB.

And I forgot to mention in my first post, I also tried booting up with the previous kernels, (there was a kernel update in the updates that installed this morning) and all 3 installed kernels, 3.8.0-19-generic, 3.5.0-22-generic, and 3.5.0-17-generic all failed to boot, stopping at the same place.

---

### Post by itchyLawn on 2013-05-11
Does the system boots and works before you installed the new kernel updates? Try to reinstall Ubuntu, then install all the updates **except** for the kernel ones. (still not sure though.. :p)

---

### Post by Ranko Kohime on 2013-05-12
Working on reinstalling right now.  Without any boot logs to know what's wrong, I have little other recourse.

Also, upon reinstalling, it asks if I want to install along side 13.04?  Apparently the updater snuck a distro upgrade in there.  Thought I had that disabled.  O_o

---

### Post by Ranko Kohime on 2013-06-06
Solving this, only because I figured out how, if not why.

The issue occurred at the first reboot after a distro upgrade.  I haven't figured out why that happened, but it did.

---

