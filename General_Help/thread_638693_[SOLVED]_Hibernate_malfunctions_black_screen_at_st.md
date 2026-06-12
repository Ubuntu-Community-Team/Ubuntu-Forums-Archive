---
title: "[SOLVED] Hibernate malfunctions: black screen at startup"
date: 2007-12-12
forum: General Help
---

### Post by KenBW2 on 2007-12-12
I recently installed Ubuntu 7.10 (after playing with other versions), and now use it as my primary OS. 
But I'm having problems with Hibernate. When I go to the Power button > Hibernate it goes through the motions, goes to some black and white text. Just before "Power down..." is printed on the screen it says something about USB 5 or something (I don't know if that's normal).
When I turn it back on afterwards I get something about USB again, it shows the Ubuntu splash screen with the orange bar, then nothing. Just a black screen. As far as I can tell nothing responds except the Num Lock light on my keyboard which is already on. All that fixes it is pulling the plug out.

Any ideas?

---

### Post by tgalati4 on 2007-12-12
Check your BIOS and under power management, make sure you have "Allow USB to wake", also check for any other power options that may be helpful.

How large is your RAM versus your swap drive?  If your swap is too small (to hold a compressed image of RAM) then you will get similar symptoms.

Hibernate is tricky to troubleshoot and get working correctly.  It takes some patience and digging.

---

### Post by KenBW2 on 2007-12-12
Went into BIOS > Power Management and there's nothing there about USBs.
Oh yea, meant to say about Swap:
1GB RAM
1.5GB Swap
Was advised that would be sufficient

---

### Post by roachk71 on 2007-12-12
Of course, there remains the one vexing problem regarding hibernation support: Hibernation states and techniques often vary not only between manufacturers, but in many cases, between models. What works on one computer won't necessarily work properly on another, etc.

I had a mind-numbingly hard time trying to get this feature working correctly on my (now dead) Pavilion xt125 notebook: No matter which distro or version I tried, it simply wouldn't work. And even if it does, if you don't have Network-Manager and its taskbar applet installed, you'll likely lose your network connection on resume (trying to restore the connection by disabling and re-enabling it is pointless; only a reboot seems to fix it.)

Oh, and you have ample swap space for hibernation.

Another problem is SoftwareSuspend's reliability: It tends to corrupt the resume image from time to time, so you may want to think carefully about its use to begin with. This is especially true if some of your swap is already in use.

---

### Post by KenBW2 on 2008-05-13
For anyone with this problem: I found my solution today:

[https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend](https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend)

---

