---
title: "MX1000:  Just can't get it working :("
date: 2007-02-26
forum: General Help
---

### Post by Vivix729 on 2007-02-26
Ok, I looked at all the tutorials in the forum, and several other websites.  No matter what I do, X server won't start after a reboot.  It's like it goes in a loop...a black screen, some corrupted colors, black screen and so on.

I think the problem is in the following:

I have my MX1000 and the cradle, which are identified as Logitech USB Receiver.  But I also have a Logitech keyboard that uses a different receiver, and that one shows up twice (for the keyboard and the mouse that came with the keyboard which I'm not using, I assume), and they are ALSO identified as Logitech USB Receiver.  Now, how would I tell my xorg.conf to identify the right Logitech USB Receiver?

THANKS!

---

### Post by ububug on 2007-02-26
I had the exact same problem and I _think_ what was messing things up was some quotation mark or some other small error somewhere. 


[https://help.ubuntu.com/community/MX1000Mouse](https://help.ubuntu.com/community/MX1000Mouse)


Try following that guide and manually replacing all the " before saving xorg.conf, it's worth a shot.

---

### Post by Vivix729 on 2007-02-26
Do you have two Logitech USB Receiver devices too?

I also noticed this note:

We are only identifying the device using it's "Name". If this is a problem for you because other devices also identify themselves this way, post at the forum link found at the bottom of this page.

---

### Post by Vivix729 on 2007-02-27
I hate to be bumping my own thread, but I'm stuck on this issue for DAYS already.  I even tried creating a udev rule.  Still, no matter what, evdev keeps crashing X.  Any ideas at all?

---

### Post by ububug on 2007-02-28
No just one receiver.  Have you seen this thread: [http://blog.blackdown.de/2006/01/15/updated-logitech-mx1000-configuration/](http://blog.blackdown.de/2006/01/15/updated-logitech-mx1000-configuration/) ? The answer might be in the comments. Read them through and see if you find anything that helps you. I remember reading them but I'm not sure if that's where I found the answer.

---

