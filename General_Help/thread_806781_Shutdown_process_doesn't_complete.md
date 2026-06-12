---
title: "Shutdown process doesn't complete"
date: 2008-05-25
forum: General Help
---

### Post by victor.zamanian on 2008-05-25
I have a Dell Dimension 9200 with an NVidia GeForce 7600 video card and restricted drivers enabled. I'm running 32-bit Ubuntu 8.04 with the latest updates including proposed updates (as of today, 2008-05-25); kernel version is 2.6.24-17-generic; GNOME version: 2.22.1.

It seems I can't shutdown Ubuntu without force-resetting it with the power button for a number of seconds. The shutdown process freezes when the Ubuntu splash screen's loading bar "depletes" at the very end of the process.

A bug very plausibly related to this one is the fact that when I installed Ubuntu (this happened two out of two times, installing 8.04), when it asks me to remove the CD and press enter to restart, it won't restart. I can remove the disk, and slide the CD slot in and out, but it never responds to my pressing enter.

I accidentally posted this as a comment on a bug on launchpad but it turns out my post was unrelated to the bug. However, one person suggested,

> i find it extremely unlikely that your problem is related, Victor. sounds like Ubuntu can't access your motherboard's ACPI functions properly, and that's nothing to do with this.

I have no idea what that entails, so any help is greatly appreciated since the power button on this machine is very stiff to hold in for any number of seconds (I kid you not), and I'd like to shutdown using the keyboard or mouse pointer like I'm supposed to be able to... :-)

Thanks,
Victor

PS.
Suspending the computer won't allow me to enter back into Ubuntu. The screen (yeah, the screen) is telling me that it is in power-saving mode when I start the computer back up. Just thought I'd mention in case someone knows if it's related or not. If not, just focus on the shutdown problem please. ;-)

---

### Post by diablo75 on 2008-05-25
ACPI is the feature of pretty much all newer computer that allows the Operating System to do things like go into hibernate or tell the system to shut down.  It's power management, in other words, and is a feature of your BIOS.  Two things you should check is the current version of your BIOS and compare it to the manufactures latest posted flash images online to see if you could use an upgrade, and you should also go into your BIOS settings to see if ACPI support simply needed to be enabled.

---

### Post by victor.zamanian on 2008-05-25
Thanks diablo75 for your incredibly quick, informative and well-written reply (haven't seen a lot of that on the Internet lately :)!

I recently flashed my BIOS, actually, but that's a good idea if this happens again.

However, just a few minutes ago, I wanted to show my family member my issue, and it turns out, the problem didn't occur! I tried again and it seems like the problem is resolved. I have no idea of why or how, which is sad because I'd love to tell you the solution to this problem! I'm going to have to assume that any software updates did not "sink in" until now and that those were the solution to the problem.

Thanks again, and happy computing!

---

### Post by victor.zamanian on 2008-05-26
Okay, so this problem isn't solved at all, it's just that I'm experiencing this bug: [https://bugs.launchpad.net/ubuntu/+bug/218357](https://bugs.launchpad.net/ubuntu/+bug/218357)

Ubuntu thinks that my hardware has disabled rebooting. The times I was demonstrating my problem, I chose to shutdown and not to reboot.

Marked this as unsolved.

---

### Post by Scunizi on 2008-05-26
Instead of using the power button to shut down try this instead for a clean shutdown.. no guarantees it will work on your machine.. but it does on mine.

CTRL+ALT+F2 (It will give you a large text screen with login prompt)
login using your normal uname and pass
sudo shutdown -P now <enter>

Your machine should now be shutting down.

---

### Post by victor.zamanian on 2008-05-28
> **Scunizi said:**
> Instead of using the power button to shut down try this instead for a clean shutdown.. no guarantees it will work on your machine.. but it does on mine.

CTRL+ALT+F2 (It will give you a large text screen with login prompt)
login using your normal uname and pass
sudo shutdown -P now <enter>

Your machine should now be shutting down.

My problem is not with halting/shutting down the computer--it is with rebooting. Read my previous post and take a look at the link to the bug report on launchpad.net I pasted in. I posted a comment to that bug report as well. This means that not even "sudo reboot" or "sudo shutdown -r now" works, even if gdm and X are killed (I've tried).

---

### Post by victor.zamanian on 2008-06-03
Alright. It seems that this issue is really resolved now, with the latest updates. I tried rebooting yesterday and it worked fine. And the white-screen problem when logging back in after switching users when using compiz with an nVidia card has also been fixed apparently!!! Psyked about that!

Thanks for the help, guys. Marking it as solved, yet again (reserving the annoying right to mark it as unsolved again later maybe >< ).

---

### Post by victor.zamanian on 2008-06-06
RIGHT. NOPE. Marking it as unsolved, and not touching it ever again! Power management is just not working for me at all (hibernate, suspend, reboot...).

So... still unsolved, don't know what the heck is going on. Is there ever going to be any light in the darkness of the linux power management? :-/

---

### Post by victor.zamanian on 2008-06-12
Okay... I'm almost ready to mark this as [SOLVED], because now rebooting works, and I even managed to resume from suspend today. So yeah. I'm going to do more testing to see if it works okay. I assume this has to do with my upgrading the kernel through the update manager since I've not altered any files anywhere, manually.

Alright, peace!

---

### Post by victor.zamanian on 2008-06-14
Wow, okay. Some more software updates came today, so I installed them, and tried rebooting and suspending. Rebooting doesn't work, but I can at least say I found a pattern regarding suspension.

Suspension works 1 time after a full shutdown + startup (I'm saying shutdown + startup since I'm not able to reboot). The second time, it fails to resume from suspension.

Does anybody have a clue to why this is happening? There was even an update to some... "hal"-software, that claimed it had fixed some "rebooting and suspending quirks", but I'm having the same problems as I've always had. Driving me crazy.

Anybody, any type of help, suggestions or directions would be greatly appreciated. I feel like I want to boot into my Windows partition until this is fixed just so I can suspend, because I use it so much (or I *would*, if it worked. I use it a lot with other computers).

---

