---
title: "Kernel Panic on Reboot/Shutdown"
date: 2008-06-24
forum: General Help
---

### Post by terminator14 on 2008-06-24
I'm running Ubuntu 8.04 (2.6.24-19), and I seem to be having some difficulties with restarting my computer or shutting it off. Every once in a while (not every time), when I restart my computer, and shut it down, I get a kernel panic. This isn't too inconvenient for now, seeing as how I'm able to hit the reset button on my computer if I was restarting it, or hold down the power button to shut it off, but soon I will be needing to access the computer from a remote location (I'm setting up Wake on LAN and autologin with SSH server so I can login from anywhere securely), and if it freezes, I won't be able to just reset it. Is this a know bug, or something just happening to me, and how can I fix it?

BTW my OS install is basically fresh (a few days old), and this problem has occurred in previous versions of the kernel (I only got 2.6.24-19 from an auto update - I believe the version that comes on the CD I use is 2.6.24-16). Also, I don't think anything I do really triggers the kernel panic since last time it happened, all I did was start my computer, edit my Grub's menu.lst with the command "sudo gedit /boot/grub/menu.lst", change the name of the kernel as it appeared in the grub menu (name only, I touched nothing else), and after saving typed "sudo reboot" after which it froze. All this too under 2 minutes, and I doubt any of that could have triggered it.

I have supplied 2 different photos of the kernel panic, since I couldn't really take a screenshot of it.

---

### Post by terminator14 on 2008-06-25
I have had this problem for a few months now, but haven't really had the time to follow up on it. Now that it's summer and I have some time, I would really like to get to the bottom of this problem. Anyone know or have an idea as to the cause of this?

---

