---
title: "Palm TX with Linux"
date: 2007-07-21
forum: General Help
---

### Post by sevenseeker on 2007-07-21
I have a Palm TX and would like to use it with Linux.  I am getting nowhere fast and would appreciate advice on how to proceed.  I am using Feitsy Kubuntu.

So far I have not found a way to sync the Palm with using J-Pilot or KPilot.  In fact, KPilot freezes everytime.

J-Pilot complains of a missing /dev/pilot.  Furthermore, the posts talking about /dev/tty/ttyUSB* leave me confused because there are no such devices present on my system.

lsusb shows the device but I do not know where in /dev it is.

---

### Post by Steve1961 on 2007-07-21
> **sevenseeker said:**
> I have a Palm TX and would like to use it with Linux.  I am getting nowhere fast and would appreciate advice on how to proceed.  I am using Feitsy Kubuntu.

So far I have not found a way to sync the Palm with using J-Pilot or KPilot.  In fact, KPilot freezes everytime.

J-Pilot complains of a missing /dev/pilot.  Furthermore, the posts talking about /dev/tty/ttyUSB* leave me confused because there are no such devices present on my system.

lsusb shows the device but I do not know where in /dev it is.

I'm using Ubuntu rather than Kubuntu so can't comment about J-pilot or KPilot.  However, my TX 'just works' when syncing with Evolution using the gnome-pilot applet.  Perhaps you need to create a udev rule so that the /dev/pilot node is created when you plug in your TX.  Something like:

KERNEL="ttyUSB[13579]*", NAME="pilot", GROUP="usb", MODE="0660"

in /etc/udev/rules.d/10-udev.rules

Note: I haven't written a udev rule since Dapper so the syntax might need updating.  This link might be useful:

[https://bugs.launchpad.net/ubuntu/+source/kdepim/+bug/75149](https://bugs.launchpad.net/ubuntu/+source/kdepim/+bug/75149)

Better still, found a recent post that might help:

[http://ubuntuforums.org/showthread.php?p=2706859](http://ubuntuforums.org/showthread.php?p=2706859)

---

### Post by Happypony on 2007-08-11
**This post could be related to an Ubuntu bug filed at**: [https://launchpad.net/gnome-pilot-conduits/](https://launchpad.net/gnome-pilot-conduits/) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Say how do you get the TX to sync its email with evolution, every thing else syncs nicely except the Versamail ?

---

### Post by Steve1961 on 2007-08-11
I only sync my calender and contacts so can't help, sorry.

---

### Post by isolatedvertex on 2007-09-03
Is there a way to do this using bluetooth?

---

