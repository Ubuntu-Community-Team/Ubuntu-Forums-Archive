---
title: "Monitor &quot;Out of Frequency&quot; during boot"
date: 2007-11-24
forum: General Help
---

### Post by Unicycle on 2007-11-24
Hi folks.  I recently did a clean install of Gutsy after hosing things with the ATI driver crap.  Anyway, on this new install, my monitor reports "Out of Frequency" during what I assume is the Ubuntu splash screen. Once it gets to the login screen, everything is fine.

My frequency is set at 76 Hz, and if I remember right, it was at 60 Hz for my last install.  How would I change this (76 Hz is the only option in the "Screens and Graphics" menu)?  Would reconfiguring xorg.conf do the trick?

Thanks. \\:D/

---

### Post by rune0077 on 2007-11-24
Try System > Preferences > Screen Resolution

---

### Post by chrisccoulson on 2007-11-24
What sort of monitor is it? What are the supported resolutions?

---

### Post by Unicycle on 2007-11-24
> **chrisccoulson said:**
> What sort of monitor is it? What are the supported resolutions?

It's a 15 inch LCD (or is it plasma?  Anyway, the older not-glassy kind).  It's at 1024 x 768 now, and that's what I've set xorg.conf to support.  I don't see a section of xorg.conf to edit the Hz, though.

---

### Post by martinoco on 2007-11-25
hey I'm havin the same problem here :(

i was able to adjust the screen frequency and can use ubuntu normally, but I haven't been able to fix the splash screen. Hopefully someone can help

---

### Post by namanbagga on 2007-11-25
[This]("http://www.namanb.com/2007/11/ubuntu-710-bootup-resolution-problem.html") is the solution to your problem:popcorn:

---

### Post by martinoco on 2007-11-25
> **namanbagga said:**
> [This]("http://www.namanb.com/2007/11/ubuntu-710-bootup-resolution-problem.html") is the solution to your problem:popcorn:

thanks! that worked great :)

---

