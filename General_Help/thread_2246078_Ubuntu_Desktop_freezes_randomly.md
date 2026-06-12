---
title: "Ubuntu Desktop freezes randomly"
date: 2014-09-28
forum: General Help
---

### Post by sleik on 2014-09-28
My Ubuntu Desktop ( Ubuntu 14.04) freezes shortly after the login, no matter what programms I use. When I use strg+alt+fx to switch to a console and then switch back to the desktop, it starts working for while, until it freezes again.

My Ubuntu runs on an Lenovo Z50-Notebook, with an Intel HD-Graphics integrated and an Nvidia graphics card. Are they any logs which I could check or any other possibilities which could solve the problem? I am using Gnome instead of unity.

Thank you in advance
Sleik

---

### Post by yancek on 2014-09-28
> My Ubuntu Desktop ( Ubuntu 14.04) freezes shortly after the login, no matter what programms I use

That's a classic sign of processor overheating so the first thing to try is cleaning it out and maybe checking the processor and applying thermal paste.  Can't tell if you are having the problem on a Desktop or Notebook?  It could be a number of other things but cleaning would be the first thing to try.

---

### Post by sleik on 2014-09-28
> **yancek said:**
> That's a classic sign of processor overheating[...]

I thought that too, but on same Laptop Windows 8 runs perfectly fine, so I figured that the hardware is sane.. Could it also be a software Problem?
Before I had Problems with the UI freezing, the Desktop did not show up at all. I ran: 

```
sudo apt-get remove --purge nvidia-*
``` and reininstalled the driver. But since then, the UI freezes. The Console is running perfectly fine though. 

I'm sorry, I should've said that before..

---

