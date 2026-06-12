---
title: "Low memory error with Ubuntu 16.04"
date: 2016-05-26
forum: General Help
---

### Post by lads on 2016-05-26
Dear all,

A few days ago I upgraded my laptop from 14.04 to 16.04. This morning it started booting into emergency mode claiming low memory corruption. This particular laptop is 7 years old, perhaps the hardware is really giving up the ghost...

However, I still have Ubuntu 14.04 installed on a USB drive and decided to give it a go. Surprisingly, it runs perfectly well, no warnings of low memory corruption whatsoever.

What is going one here? Is there really an hardware issue? Or could it be something else?

I would appreciate any ideas. Thank you.

---

### Post by mörgæs on 2016-05-26
If you want 16.04 then try a fresh install. Upgrades often cause trouble. 

I see no sign of hardware errors.

---

### Post by lads on 2016-05-26
> **mörgæs said:**
> If you want 16.04 then try a fresh install. Upgrades often cause trouble. 

Before going down that route I would like to understand what kind of "trouble" is this.

Thank you.

---

### Post by mörgæs on 2016-05-26
It's not about one kind of trouble, it's about a broad selection of small and big errors. I have stopped upgrading many years ago and only do fresh installs.

You could also try 16.04 in a live boot before deciding.

---

### Post by lads on 2016-05-26
> **mörgæs said:**
> You could also try 16.04 in a live boot before deciding.

A live Ubuntu 16.04 USB also failed to boot, but with a different error. For now only the 14.04 USB is able to boot.

Trying different things, I experimented booting from other kernels installed. It turns out it boots perfectly well if I select Upstart instead of SystemD. Go figure.

---

### Post by ajgreeny on 2016-05-26
It might help if you told us what hardware you have; just saying it's a 7 year old laptop is not at all helpful.

If you're not sure run terminal command```
sudo lshw > hardware.txt
``` which will make a hardware.txt file in your home, and then attach that txt file to an answer back here. It may give us some clues about what is going on.

If, however, you are happy with how things are now running just mark this thread as SOLVED from the Thread Tools menu up-top.

---

### Post by grahammechanical on 2016-05-26
The Ubuntu live session uses the open source video driver. When you upgraded did you revert to using the open source video driver before running the upgrade? Upgrading  whilst using a proprietary video driver often (in my opinion) causes problems.

If you can get to a working desktop go to Additional Drivers and change to the open source video driver. You may need to select at the Grub menu Advance options for Ubuntu and then load a recovery kernel and at the recovery menu select resume to get to a useful desktop.

Regards.

---

