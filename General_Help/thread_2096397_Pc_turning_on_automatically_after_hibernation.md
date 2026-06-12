---
title: "Pc turning on automatically after hibernation"
date: 2012-12-19
forum: General Help
---

### Post by terrax81 on 2012-12-19
When I send Ubuntu enter in hibernation, it works as intended, it enter hibernation and resumes after starting off again, the problem is that about four seconds after the pc turn off, it automatically turn on again, forcing me to power off it in the button if I wish to use hibernation. 

What can be?

I am using Lucid Lynx (10.04) in a pc with a Thinkcentre a51 8138d motherboard that uses the i915g igp

---

### Post by Mark Phelps on 2012-12-20
Had similar problem.  Found that if I disabled the "wake on USB" option in the BIOS, the problem stopped.  But then, can't wake up the PC using the mouse or keyboard.

---

### Post by terrax81 on 2012-12-21
I think I don't have this option on my bios

---

### Post by cwsnyder on 2012-12-21
You may instead have a Wake-On-Lan setting, again in your BIOS, which would wake your PC on any LAN activity.

---

### Post by terrax81 on 2012-12-21
I did but it didn't work.

---

