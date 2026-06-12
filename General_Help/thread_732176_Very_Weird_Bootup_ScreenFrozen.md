---
title: "Very Weird Bootup Screen/Frozen"
date: 2008-03-22
forum: General Help
---

### Post by DJAKO on 2008-03-22
I installed a clean copy of ubuntu yesterday on an older dell computer I have. Pentium 4 with 1GB of RAM. Everything worked fine yesterday and when I turned it on today it locked up with a weird frozen screen which had rainbow like colors.

I have attached a screen shot

Any ideas on what the hell this is or how to fix it?

---

### Post by dcstar on 2008-03-23
> **DJAKO said:**
> I installed a clean copy of ubuntu yesterday on an older dell computer I have. Pentium 4 with 1GB of RAM. Everything worked fine yesterday and when I turned it on today it locked up with a weird frozen screen which had rainbow like colors.

I have attached a screen shot

Any ideas on what the hell this is or how to fix it?

Change your /etc/X11/xorg.conf file to use the **vesa** driver, and then reboot.

Search out posts on reconfiguring your X server settings once you get going again.

---

### Post by DJAKO on 2008-03-23
> **dcstar said:**
> Change your /etc/X11/xorg.conf file to use the **vesa** driver, and then reboot.

Search out posts on reconfiguring your X server settings once you get going again.

Where in the .conf file do I edit this? Like what lines? Sorry for the stupid questions.

Is this the other command I will have to run after?

> sudo dpkg-reconfigure xserver-xorg

---

### Post by DJAKO on 2008-03-23
Can anyone help me with this? This screen locking up is getting annoying lol

---

### Post by DJAKO on 2008-03-24
...anyone

---

