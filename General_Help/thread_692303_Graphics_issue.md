---
title: "Graphics issue"
date: 2008-02-09
forum: General Help
---

### Post by Fistols on 2008-02-09
Hi, Im relatively new to Ubuntu. I am running Gutsy Gibbon, and my screen is messed up. Nothing serious I think, but the log in screen does not take up my whole screen. It takes up the top left side and then is surrounded by a different color beige background. Then when I log in my top tool bar does not go all the way across the top of the screen(It is expanded). When I open a program for the first time in full expansion it only takes up the space from the top tool bar down. I'll include a screenshot. Please let me know.

-Derek

---

### Post by src2206 on 2008-02-11
Hello Derek, welcome to the Community :)

Did you try changing the Display Options?

---

### Post by Fistols on 2008-02-11
Thank you for the welcoming. I tried to change my resolution and it crashed on me. Is there something else I should be doing?

---

### Post by src2206 on 2008-02-11
Which video driver are you using Derek? :?:

---

### Post by Fistols on 2008-02-12
no idea, how would I check?

---

### Post by apetresc on 2008-02-12
> **Fistols said:**
> no idea, how would I check?

It's in your /etc/X11/xorg.conf file. Do you know what model of video card you own? NVidia? ATi? A particular make?

---

### Post by Fistols on 2008-02-13
its an integrated card.
Section "Device"
	Identifier	"Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"

---

