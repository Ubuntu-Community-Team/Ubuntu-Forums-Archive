---
title: "USB &quot;Achilles' heel&quot;"
date: 2007-12-28
forum: General Help
---

### Post by santuccie on 2007-12-28
Hi,

This problem may be a Linux or Unix-wide problem, but since Ubuntu and Mint (descendant of Ubuntu) are my choice distros, I figured I'd ask my questions here...

I was running Gutsy Gibbon (and have tried various other distros as well) on a Compaq Presario SR2150NX PC.  I use a USB keyboard, USB mouse, USB printer, and two or three USB storage devices at a time.  One of these devices, a 2 GB Kingston flashdrive, stores over 80 portable applications; making migration a thing of the past, and making backups as simple as copy-paste (I also use a lot of these for house calls).  Two of these apps, Thunderbird Portable and PStart (menu launcher for my portable apps), will run in Wine at all times during a session.  My preference appears to be one of Linux's weak points.

Windows does not have problems with the strain I put on USB, but every Linux distro I've used will suddenly stop responding to a USB mouse, and running portable apps will become unresponsive.  If I'm using my USB mouse when Linux decides to crash, it's gone; unplugging and plugging it back in changes nothing.  The machine will only respond to the keyboard at this point.  I reboot from the Ctrl + Alt + Del menu, leaving Linux to terminate all apps I had running when it crashed.  If I use a PS/2 mouse, I don't have any problems with the pointer.  But USB apps will still crash without warning, and the drive running them will become inaccessible until I reboot, or terminate everything and dismount/remount the device.  And if I do a hard shutdown, I lose data.:mad:

Can anyone tell me who maintains the Linux kernel itself, and/or how to get in touch with them?  And is there a patch or a workaround in the meantime?  I'd like to be able to put Linux back on my PC, and also on my new laptop; but I'm hesitant to do so until I know it can do what I need it to do (or how to make it do what I need it to do) without crashing.  Thanks in advance.

--santuccie

---

### Post by fimblo on 2007-12-28
The kernel is published over at [http://www.kernel.org](http://www.kernel.org). A little lower down on the page you'll find info on how to report a bug. And as to the question on who maintains the kernel? Its Linus Torvalds and his gang.

---

### Post by LaRoza on 2007-12-28
First, I would try to single out the problem.

Try running different devices and in different numbers and combinations. See if it is specific to a single device or situation. Try not running the portable apps, and as many devices as possible.

I have not had the same experiences as you (because I never tried to run that many devices, although I do have a USB Plasma Ball, USB Lava Lamp and a USB Aquarium, in addition to my drives and mouse)

---

