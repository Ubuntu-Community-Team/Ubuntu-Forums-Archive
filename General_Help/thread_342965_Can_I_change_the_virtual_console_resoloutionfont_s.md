---
title: "Can I change the virtual console resoloution/font size"
date: 2007-01-20
forum: General Help
---

### Post by roger99 on 2007-01-20
Hi All,

When I switch to a virtual console on my laptop running edgy the font size is quite large and by the time I've changed through a couple of directories I can only get a few characters on the line before it wraps.

Although this isn't a major problem it does niggle me a little bit so I was wondering if it is possible to increase the resoloution or decrease the font size so that everything becomes a little easier to read and follow.

Cheers

---

### Post by Rippey on 2007-01-20
In the boot loader menu append the following to the kernel line:

vga=791

or

vga=788

The first one is 1024=768 and the second is 800x600.

---

### Post by roger99 on 2007-01-21
Thank you Rippey, thats exactly what I was looking for :D

---

