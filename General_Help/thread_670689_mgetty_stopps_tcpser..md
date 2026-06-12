---
title: "mgetty stopps tcpser."
date: 2008-01-17
forum: General Help
---

### Post by Raymond Day on 2008-01-17
Hi all. I need help. Been working on this for hours! I have tcpser installed to do a modem though  /dev/ttyS1 it worked real good for about a year, but after I installed mgetty and rebooted it stopped. I un-installed mgetty but can't get tcpser to work now! It just comes back with "I/O possible" when I send any thing to it's /dev/ttyS1 or com port or RS232 port. I rebooted lots of times after I changed some things but I never get tcpser working again.

Any one know a fix?

My system is headless Ubuntu server:

# uname -a
Linux small 2.6.22-14-server #1 SMP Tue Dec 18 08:31:40 UTC 2007 i686 GNU/Linux

-Raymond Day

---

### Post by Raymond Day on 2008-01-17
I seen that /dev/ttyS0 and /dev/ttyS1 are both set for Group dialout now. I switch the group to root but that did not fix it.

I think some how mgetting is using the /dev/ttyS0 and /dev/ttyS1 so it will not let tcpser work right on them.

Any one know how to stop mgetting from using them to comports? I just want it to use the USB port /dev/ttyACM0 It does do caller ID from it good. It's Group is set for dialout.

-Raymond Day

---

### Post by Raymond Day on 2008-01-17
I think this my be the error. That there are 2 of each ttyS0 and ttyS1

# dmesg | grep tty
[   51.489227] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   51.490483] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   51.494751] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   51.496408] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   77.316702] cdc_acm 1-1:2.0: ttyACM0: USB ACM device
[   77.407249] cdc_acm 2-2:2.0: ttyACM1: USB ACM device

How do I delete the 2 with the 00:08 and 00:09? If that is what I need to do.

Or change them to ttyS2 and ttyS3 ?

-Raymond Day

---

### Post by Raymond Day on 2008-01-18
Worked on fixing this I guess about all added up 30 hours. I got to give up.

Looks like harly no one uses mgetty and tcpser together.

I can only guess mgetty used /dev/ttyS0 and /dev/ttyS1 some how that even when it's un-installed don't let tcpser work again.

-Raymond Day

---

### Post by Raymond Day on 2008-01-20
> **Raymond Day said:**
> I seen that /dev/ttyS0 and /dev/ttyS1 are both set for Group dialout now. I switch the group to root but that did not fix it.

I think some how mgetting is using the /dev/ttyS0 and /dev/ttyS1 so it will not let tcpser work right on them.

Any one know how to stop mgetting from using them to comports? I just want it to use the USB port /dev/ttyACM0 It does do caller ID from it good. It's Group is set for dialout.


Yesterday I seen that something, I guess mgetty renamed the /dev/ttyS0 and /dev/ttyS1 back to group dialout, and user root, when I had them both to tcpser.

So some place mgetty must of changed the user and group name back.

Why is it using /dev/ttyS0 and /dev/ttyS1 any way? I don't have it set to use them at all just /dev/ttyACM0

Looked on google for help on this now. It comes right to here! So this is a herd one that looks like no one else has asked or fixed!

---

### Post by Raymond Day on 2008-01-29
No one could help here. But I found Jim made a update all ready and you can get it at:

[http://www.jbrain.com/pub/linux/serial/tcpser-1.0rc12.tar.gz]("http://www.jbrain.com/pub/linux/serial/tcpser-1.0rc12.tar.gz")

It works. All he said in the CHANGES file is:

"1.0rc12
  Added code to hook SIG_IO to SIG_IGN.  Newer versions of Linux are terminating when IO arrives."

Newer versions of Linux. That must be Ubuntu 7.10

I never remember getting help on this Ubuntu message board. But with time I found out how to fix it and post it here so if others have the same to them they can fix it.

A big thank you to Jim for updateing the code. Now they just need to get it in the ```
apt-get install tcpser
```

-Raymond Day

---

