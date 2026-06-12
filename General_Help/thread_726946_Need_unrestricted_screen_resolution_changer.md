---
title: "Need unrestricted screen resolution changer"
date: 2008-03-17
forum: General Help
---

### Post by steve196 on 2008-03-17
I need a piece of software, to change the resolution and refresh rate of my monitor, without being restricted by what my system thinks about the monitors capabilities.
Is there anything like that?

---

### Post by renzokuken on 2008-03-17
not sure, but you could edit your xorg.conf manually and add/force the resolutions that way, but you could do damage if you got it wrong.......

---

### Post by Tomatz on 2008-03-17
I had this problem also. As i use an nvidia card i just ran nvidia-settings changed the resolution from there and when it asked me if i wanted to write the changes to xorg.conf (which is not a good idea from nvidia settings) i just clicked read changes first then copyed and pasted the relevant "screen" section over my old "screen" section in /etc/X11/xorg.conf

Worked a treat and i have all resolutions/refresh rates supported in the ubuntu screen resolution app :)

---

### Post by steve196 on 2008-03-17
I should have said that: Editing xorg.conf was the first thing i thought about. But there is nothing wrong with it. It spells out the capabilities of my monitor correctly. It is just apparently not used by the system (dapper drake).

---

### Post by Tomatz on 2008-03-17
Weird??? Ill have a google about and get back later.

---

