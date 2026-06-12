---
title: "USB Failure after using Ubuntu for awhile"
date: 2008-06-07
forum: General Help
---

### Post by dapps2k on 2008-06-07
I've posted this on the hardware support forums, but I only got people telling me that they have the same problems.  This is the issue:

Whenever I'm on Ubuntu for awhile, the mouse stops working. Clicking gets no response and it doesn't move whatsoever. Replugging it doesn't do anything either. At this point, all my other USB devices are still working, but eventually they'll stop working. I noticed that once replugging in the USB devices, they don't receive any power from the port and typing in lsusb in the terminal results in the terminal window hanging. Attempting to reboot or restart X would only cause Ubuntu to hang as well. I can only turn off the computer with hard shut downs.

Usually this happens when my CPU fan works at 100% before dropping down its speed when the CPU cooled down enough. I'm currently using a Acer Aspire E360 desktop. I've already tried updating the BIOS and adding acpi=force and irqpoll into the kernel boot options for grub and neither of them solved the problem.  I'm also highly certain it's not due to faulty hardware or else Windows would've been showing some problems as well.  I'm planning to try an upgrade to 8.04 from 7.10 to see if the problem remains.

This problem is really preventing me from doing any good work on Ubuntu.  I really want to enjoy the OS, but problems like these are really frustrating.

---

### Post by cariboo on 2008-06-07
You might want to check your power supply, especially if you are powering your usb devices. Some manufactureers use a fairly low quality power supply.

Jim

---

### Post by dapps2k on 2008-06-08
What would a bad power supply actually do?  It doesn't make sense to me that it would only cut power off to the mouse.  Even if I switch to a different slot, the mouse is always the first USB device to go off.  Again, if the power supply was bad, wouldn't there have been problems in Windows as well?

---

### Post by bingoUV on 2008-06-08
I think cariboo907 meant power supply to the USB device. If you were not aware, some devices need power from the mains (usually through an adaptor). The little power coming from USB slot is not enough for them.

---

### Post by tom66 on 2008-06-08
If you can, acquire a cheap, powered USB hub, and see if it does the same thing. Also, if you have one of the USB keyboard torch things or the USB keyboard fans try seeing if they stop. 

Have you contacted Acer support or is it out of warranty?

---

### Post by m4fia on 2008-06-08
A lot of the time, after I restart Ubuntu, the computer wont read my USB mouse, though this also happens with XP, and im using USB 1.0. Do you know if you are using USB 1.0 or 2.0?

---

### Post by chinocracy on 2008-06-08
I've had the same problem before when I had a Celeron 1.2 system. Now I've recently upgraded to a an Athlon X2 4400, had to reinstall Windows. But I haven't tried Ubuntu again. So it's an inherent bug in the hardware most of the time? Hope so. Celerons always sucked. I have yet to try it in my new system though.

---

### Post by dapps2k on 2008-06-08
> **chinocracy said:**
> I've had the same problem before when I had a Celeron 1.2 system. Now I've recently upgraded to a an Athlon X2 4400, had to reinstall Windows. But I haven't tried Ubuntu again. So it's an inherent bug in the hardware most of the time? Hope so. Celerons always sucked. I have yet to try it in my new system though.

I have an Athlon X2 4200+, so I guess it's easy to say I don't have a Celeron. :P

> A lot of the time, after I restart Ubuntu, the computer wont read my USB mouse, though this also happens with XP, and im using USB 1.0. Do you know if you are using USB 1.0 or 2.0?

I'm definitely sure I'm using USB 2.0. Again, it's a relatively new computer, only a year old.

> If you can, acquire a cheap, powered USB hub, and see if it does the same thing. Also, if you have one of the USB keyboard torch things or the USB keyboard fans try seeing if they stop.

Have you contacted Acer support or is it out of warranty?

It's unfortunately out of warranty and I'm not sure if Acer support would give me help on Ubuntu since I have no idea if they officially support Ubuntu.

> I think cariboo907 meant power supply to the USB device. If you were not aware, some devices need power from the mains (usually through an adaptor). The little power coming from USB slot is not enough for them.

I was aware, though I should check if it's using an adaptor for power.  As of now, I'm trying to not spend any money on the issue since I don't exactly have much cash to spend.  I'm hoping there's some update or a hack I can do to fix the problem.

---

