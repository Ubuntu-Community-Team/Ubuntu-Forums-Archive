---
title: "Ubuntu 6.10 keeps crashing randomly"
date: 2007-03-11
forum: General Help
---

### Post by Dexterp37 on 2007-03-11
Hi!

I really hope I'm posting to the right forum! I really need help :|

My ubuntu machine keeps crashing frequently, just after few minutes! It never happened before, I'm using Edgy since it got out and kept it up to date. I'm on a Pentium D machine with 1Gb of DDR2 ram (ATI video card X1300).

I just made synaptic update system software, and not installed anything but Anjuta and Inkscape.

That problem is getting very frustrating, It took me 4 crashes to write this post :confused: 

Is that any log I can take a look at to see what was going on?

Thanks in advance

---

### Post by wj32 on 2007-03-11
What happens when it crashes? Does the whole machine go down (as in it reboots) or is it just X? Or does it hang?

---

### Post by Dexterp37 on 2007-03-11
It hangs, freezes :) Mouse cursor stops, computer doesn't respond to any input and doesn't reboot, just freezes. Reset is the only way to get system back.

---

### Post by cowlip on 2007-03-11
are you using the ATI binary drivers?  I don't think the X1300 is supported by the open source ones..

---

### Post by Dexterp37 on 2007-03-11
Sure, I'm using drivers from the ATI web site, which worked/work like a charme until now!  My Ubuntu workstation worked like a charme for months, I just can't explaine why it started crashing now :| It looks like it happens more frequently (but not exclusively) when I'm listening to music (XMMS, MPlayer or Xine).

My MP3 are on a NTFS partition mounted using NTFS-3G

---

### Post by bapoumba on 2007-03-11
@ Dexterp37: just moved your thread to "General Help".
When your system is freezing, do you still have access to non graphical sessions ?
Hit: **CTRL-ALT-F2** for ex, login and run **top**, to see if any application is using all of your ressources. Depending on which one, you can kill it (**kill -9 <pid of application>** or **killall <application>**) and go back to your graphic session with **CTRL-ALT-F7**.

---

### Post by Dexterp37 on 2007-03-11
Yes, I tried that already, but it looks like the whole system is locked up and doesn't allow me to do anything.

---

### Post by bapoumba on 2007-03-11
may be have a look at this then:
[http://www.debianadmin.com/how-to-reboot-your-debianubuntu-system-only-if-all-else-fails.html]("http://www.debianadmin.com/how-to-reboot-your-debianubuntu-system-only-if-all-else-fails.html")

---

### Post by Dexterp37 on 2007-03-11
Thank you, at least now I that I can avoid the reset pain (I'll check).

But the problem isn't solved yet, any help?

---

