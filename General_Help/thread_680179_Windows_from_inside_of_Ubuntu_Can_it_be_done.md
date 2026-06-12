---
title: "Windows from inside of Ubuntu: Can it be done?"
date: 2008-01-27
forum: General Help
---

### Post by recursive on 2008-01-27
Alright, I just moved on to the successful phase of my switch away from windows (after pitched combat against my Netgear adapter), and I am just starting to realize that it's not going to be as easy as I thought. I still need to use windows for a wide variety of tasks, but can't stand the fact that it gives you so little control, and as such am trying to minimize usage.

What I'd like to know is if it's possible to "boot" a pre-existing windows partition from within Ubuntu? Here's kinda the image I have in my mind. You boot Ubuntu, log in, and have an icon on your desktop "Start Windows XP". You click on this, and Ubuntu goes more or less dormant, Windows goes through its boot sequence like normal. You do the stuff in windows. Then you go to shut down, and instead of turning off the computer, it just shuts down windows, and you're back in Ubuntu.

Virtual Machines aren't really an option simply because I'd have to clone my entire 150 gb hard drive for it to work, and I just don't want to devour my secondary like that.

Any insight would be greatly appreciated.

---

### Post by Martin Witte on 2008-01-27
youu can go virtual with vmware, see eg. [http://ubuntuforums.org/showthread.php?t=183209](http://ubuntuforums.org/showthread.php?t=183209)

---

### Post by tempril on 2008-01-27
Vmware is good for running an existing install of windows, but as I found out, ALWAYS....ALWAYS shut down your windows before running your windows from the Grub menu.
I have posted a help after doing this, because the system files change from the open suspended windows then running windows from boot up causes big problems.

(big booming voice) BE WARNED!!!!  (/big booming voice)

---

