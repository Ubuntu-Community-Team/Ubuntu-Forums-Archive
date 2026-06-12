---
title: "usb ethernet adapter"
date: 2024-07-04
forum: General Help
---

### Post by jhoni146 on 2024-07-04
Hello,

I have problems on Ubuntu 24 with a USB ethernet adapter, the problem is that it suddenly disappears and stops working, to make it work again I have to remove the USB and put it back in, how can I solve this?

---

### Post by TheFu on 2024-07-06
Have you tried a different USB port? Could be the port you use is loose.  The more a USB port is used (insert cycles), the more likely that connection is to fail.  I've had some USB storage devices disappear from my desktops.  Those connects were seldom removed/re-inserted, so I'm guessing it is just the slight vibration from the fans and other moving HDDs in the system.  Something to consider.

Sometimes USB devices die.  I'd get a new device and see if that fixes it.  I had a GigE-to-USB3 adapter about 10 yrs ago that lasted 3 years before dying.  Got a replacement, carefully searching the sellers and reviews for "Linux supported" and spent my $20. It has been working nearly 10 yrs now.  I've been lucky.

Electronic devices fail. Sometimes they fail a little. Sometimes they fail always.

---

### Post by jhoni146 on 2024-07-06
First of all, thank you for your response and your interest, the adapter is new and the laptop is 2 months old, in Windows it works fine, I am 100% sure it is a Ubuntu thing, sometimes it goes for many hours without disconnecting and sometimes less.

---

### Post by #&amp;thj^% on 2024-07-06
If you can, disable "IPV6" for a few days to see if that helps.

If you are uncertain on how to do that just ask.

---

### Post by TheFu on 2024-07-06
Also, disable power management, don't let the system sleep or hibernate.  

Sometimes it is necessary to create some custom sleep/unsleep commands for 1-off hardware.  I had to do this with my USB2-to-GigE adapter.  That was long ago on 16.04, so I don't recall exactly what or where to do it.  For my hardware, newer releases handled the sleep/unsleep without any custom scripts.

---

### Post by jhoni146 on 2024-07-06
IPv6 is disabled, I have also disabled power saving, turning off the screen and suspending, I will check anyway.

---

### Post by jhoni146 on 2024-07-08
Hi,

It just failed me right now and I have been able to see the following in the crash log:

r8152-cfgselector 2-4: device not accepting address 3, error -62
r8152 2-4:1.0 enx00e04c681463: Get ether addr fail
r8152-cfgselector 2-4: USB disconnect, device number 3

---

### Post by TheFu on 2024-07-08
I'm back to this as the cause .... 

> **TheFu said:**
> Have you tried a different USB port? Could be the port you use is loose.  The more a USB port is used (insert cycles), the more likely that connection is to fail. 

based on that error message.

---

### Post by jhoni146 on 2024-07-09
I'm going to try changing the port and I'll tell you, anyway it seems strange to me that a USB port on a new computer is broken and that in Windows it never fails... the adapter is something very strange.

---

### Post by TheFu on 2024-07-09
> **jhoni146 said:**
> I'm going to try changing the port and I'll tell you, anyway it seems strange to me that a USB port on a new computer is broken and that in Windows it never fails... the adapter is something very strange.

Not all chips are supported as well under Linux. Often, the vendor takes the "proof of concept" driver and posts it to the internet for Linux users, then says they are done.

You are right, if the USB ethernet adapter never fails under Windows using the same port, that means it isn't a vibration issue.  Not all USB ports are fully compatible with Linux. I had an early USB3 PCIe card that mostly worked, except when it didn't. About 2 yrs after I got it, the kernel got an update that made it work flawlessly.  Before that time, it was slow and would disconnect randomly.  I wasn't using it for wifi, just storage and USB printer connections.  At the time, motherboard buses weren't nearly as fast as they are today, so it was possible for that USB3 card to flood the entire motherboard bus.  In just 2 yrs, all motherboards included USB3 onboard and had massively more bandwidth on their buses to support multiple USB3 devices working concurrently at full speed.

Looks like that specific Realtek chip is well known for disconnects under different linux systems.  
See: 
[https://bbs.archlinux.org/viewtopic.php?id=284914](https://bbs.archlinux.org/viewtopic.php?id=284914)  
 and
[https://bugzilla.kernel.org/show_bug.cgi?id=198931](https://bugzilla.kernel.org/show_bug.cgi?id=198931)

Both links have things to try and workarounds. I didn't read every post.  Looking at the last few posts, seems that even today, there isn't a definitive fix after 6+ months of the kernel team trying to figure out the issue.  If it were me, I'd just buy a new adapter that is known to work well with Linux and be done with it.  To me, 1 day of not working is worth many hundreds of $$$, so if the fix is $20, that's not really a question.

---

### Post by jhoni146 on 2024-07-09
I'm going to review and continue testing, thanks for your answers and help.

---

