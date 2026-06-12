---
title: "USB Problem 'usb 2-4: device descriptor read/64, error -110'"
date: 2015-08-26
forum: General Help
---

### Post by James Wilde on 2015-08-26
Asus laptop running 14:04

I first got the above message (several times) when starting a gparted live cd.  Now I have seen it when I started Ubuntu today.  I copied the messages from dmesg.  The whole relevant bit is as follows:

```
[FONT=Helvetica][   64.280078] usb 2-4: device descriptor read/64, error -110[/FONT]
[FONT=Helvetica][   64.496129] usb 2-4: new high-speed USB device number 6 using ehci-pci[/FONT]
[FONT=Helvetica][   69.516399] usb 2-4: device descriptor read/8, error -110[/FONT]
[FONT=Helvetica][   74.636277] usb 2-4: device descriptor read/8, error -110[/FONT]
[FONT=Helvetica][   74.852304] usb 2-4: new high-speed USB device number 7 using ehci-pci[/FONT]
[FONT=Helvetica][   79.872297] usb 2-4: device descriptor read/8, error -110[/FONT]
[FONT=Helvetica]
[/FONT]
[FONT=Helvetica][   84.992319] usb 2-4: device descriptor read/8, error -110[/FONT]
[FONT=Helvetica][   85.096176] hub 2-0:1.0: unable to enumerate USB device on port 4[/FONT]

```
The reason for the gap before the last two lines was that there was a good deal of other text there, and then the two lines showed up again.

I have seen a number of questions, mostly with error -71, but none with error -110.  The machine in question has a keyboard, a roller ball, a 2 TB hard disk, a card reader for logging in to the bank, and a Brother printer connected via usb.

I'd really appreciate it if someone can give me a pointer to what I should be looking at or for.

---

### Post by pauljw on 2015-08-26
Found this from a web search (Google is your friend.)  It's an older post but is your very error message.  Might be the solution for you too.

[http://www.linuxquestions.org/questions/linux-hardware-18/usb-error-usb-2-4-device-descriptor-read-64-error-71-a-643022-print/](http://www.linuxquestions.org/questions/linux-hardware-18/usb-error-usb-2-4-device-descriptor-read-64-error-71-a-643022-print/)

---

### Post by James Wilde on 2015-08-27
Thanks, Paul.  It's not actually the same error.  Mine is -110.  But I'll give this a try.  I have actually seen indications that it is a group of errors with a common solution.

---

