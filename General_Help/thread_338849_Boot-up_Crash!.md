---
title: "Boot-up Crash!"
date: 2007-01-15
forum: General Help
---

### Post by Leonaken on 2007-01-15
This is the strangest (and scariest) problem I've yet faced, on any platform. Here are the details:

I have an HP Compaq nc8230 laptop, 2.0GHz Pentium M, 1GB RAM, and a 64MB ATi Radeon Mobility X600, dual-booting Ubuntu 6.10 and Windows XP. Right now, when I boot-up my laptop and select any of the Ubuntu options (Ubuntu kernel version yada, Ubuntu recovery mode, memtest) the screen reads "Starting up...", waits one second, screen turns off, and the system shuts off. If I boot into Windows, boots fine.

Has anybody else experienced this?

---

### Post by riven0 on 2007-01-15
I haven't heard about this one before, but it'll be hard to tell where the problem is related to if you don't have an error message.

So, to find out exactly where it is shutting down do this: when you get to GRUB, hit **e**. Then go down to the line that looks like this and hit **e** again:

> kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet single 

Delete the **quiet** from the line, then hit enter and then **b** to bootup. Now you'll be able to tell exactly what is happening before it shuts down. Post the last few lines of the bootup here. Hopefully, it's something simple.

---

### Post by John Doe on 2007-01-15
I bet getting an error message from an issue like this would be rather difficult if the system shuts off 1 second into booting even when "quiet" is removed from the kernel command line.

---

### Post by Leonaken on 2007-01-15
John called it. In fact, the first time I tried editing the command line, the system shut off. After successfully editing the line (second try), and booted it up, I got no error message, just "Starting up..." and a subsequent blackout.

---

### Post by John Doe on 2007-01-20
On the same kernel line that riven0 mentioned, try booting with one of the following boot options added to it and see if the system boots:

[LIST]
[*]noacpi
[*]noapic nolapic
[/LIST]

---

### Post by Leonaken on 2007-01-21
I´ve actually found a work-around to the boot-up crash. If I take out the AC cable during boot-up, the system boots fine. Therefore, this is not related to Linux or GRUB in any way, this is a hardware problem. I´m just going to have to send my laptop in for servicing.

---

