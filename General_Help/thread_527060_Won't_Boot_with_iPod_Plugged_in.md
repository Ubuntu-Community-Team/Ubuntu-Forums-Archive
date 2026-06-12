---
title: "Won't Boot with iPod Plugged in"
date: 2007-08-16
forum: General Help
---

### Post by HarryHaller on 2007-08-16
Hi

I can't get ubuntu to boot when I have my iPod plugged into the usb port - it just hangs on the "starting up..." screen with a flashing cursor.  It boots perfectly fine with the iPod disconnected.

I've really got no idea of where to start to fix this problem.  Any ideas?

---

### Post by AZzKikR on 2007-08-16
> **HarryHaller said:**
> Hi

I can't get ubuntu to boot when I have my iPod plugged into the usb port - it just hangs on the "starting up..." screen with a flashing cursor.  It boots perfectly fine with the iPod disconnected.

I've really got no idea of where to start to fix this problem.  Any ideas?

Does it happen at the booting of the Ubuntu Operating System, or before?

I knew that when I connected my cellphone to my USB port of my laptop (running WinXP), it wouldn't boot as well, because it tries to boot from that USB 'drive'. That is a setting in the computer's BIOS.

---

### Post by UK-Wobbie on 2007-08-16
> **HarryHaller said:**
> Hi

I can't get ubuntu to boot when I have my iPod plugged into the usb port - it just hangs on the "starting up..." screen with a flashing cursor.  It boots perfectly fine with the iPod disconnected.

I've really got no idea of where to start to fix this problem.  Any ideas?

So Ubuntu will not boot at all if you have got your iPod plugged in?
And if you unplug it it will boot ok? :)

---

### Post by UK-Wobbie on 2007-08-16
> **HarryHaller said:**
> Hi

I can't get ubuntu to boot when I have my iPod plugged into the usb port - it just hangs on the "starting up..." screen with a flashing cursor.  It boots perfectly fine with the iPod disconnected.

I've really got no idea of where to start to fix this problem.  Any ideas?

Have you had a go plugging it in when you on the desktop? It may Instill some plugging :)

---

### Post by pxwpxw on 2007-08-16
Try plugging in the ipod after  boot.
When it is pllugged in before boot, it can change the order of allocation of drive names, so ubuntu gets lost.
That happens with any external drive, which is what the ipod may appear, like a USB stick.

---

### Post by janarene on 2007-08-16
I run various OS's on several Compaq machines and have experienced the same problem.  All I get is a blinking cursor on a black screen.  Sometimes I can resolve the problem by plugging the device right into the computer, rather than into a hub - but in most cases I have to remove the device to boot.  It seems to be a hardware issue and not an OS issue.

---

### Post by HarryHaller on 2007-08-17
Thanks for the replies!

I can easily boot and then plug in the iPod.  The problem is that my computer is in a different part of my house to my keyboard/mouse/screen and I frequently change OSs.

The "hang" happens after selecting to boot Ubuntu from GRUB.  This indicates to me that at least the MBR points to the right boot drive/partition for GRUB.  That doesn't preclude GRUB/Ubuntu getting confused about from which drive to boot.  So maybe I can fix it by changing GRUB configuration...

But would the presence of the USB drive really change the values of the other disks in the disk array?

Also, this doesn't happen in the other OSs I use.

---

### Post by swordsmith on 2007-08-17
Hmmm...I have the exact same problem. Nothing works, even the GRUB doesnt show up when ipod's plugged in.

---

