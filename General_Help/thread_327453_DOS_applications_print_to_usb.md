---
title: "DOS applications print to usb"
date: 2006-12-29
forum: General Help
---

### Post by daller on 2006-12-29
Hi There,

I'm running a financial DOS application (Concorde) - Which is running great with dosbox.

My problem is that I can't get it to print, due to the applications parallel printer "lock-in"

Can I somehow make prints from that specific application point to my usb printer?

---

### Post by rogblake on 2006-12-29
> **daller said:**
> Hi There,
I'm running a financial DOS application (Concorde) - Which is running great with dosbox.
My problem is that I can't get it to print, due to the applications parallel printer "lock-in"
Can I somehow make prints from that specific application point to my usb printer?

I have not used dosbox, but have run into similar situations with DOS programs running under Windows with USB printers. Does dosbox support networking, something like the MS-DOS "NET USE" command?  What I've done under Windows is to share the USB printer out as a network printer, and capture the LPT1 port to that shared printer.  (On Windows 2000 and XP you can do this even if the DOS program and printer are running on the same computer.) Then the DOS program just prints to LPT1 and the networking subsystem does the rest. If dosbox can connect to Samba shared printers you might give this a try.

---

