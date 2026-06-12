---
title: "Display problems still"
date: 2008-02-25
forum: General Help
---

### Post by Dracar on 2008-02-25
Hey, sorry If I am not aloud to start another post about the same issue, the last was never resolved and I don't want to bump it again cause idk if bumping is aloud.

I've ran sudo dpkg-reconfigure -phigh xserver-xorg  a few times, It says its configured wrong, and wont do anything. on boot it tells me that on a blue box screen then goes to terminal. I selected vesa each time Like I used to, I even tried restoring a working backup of xorg, but it won't let me rename the backup to remove the date and time from it.  I really want to get ubuntu fixed so I can switch over to it again.

---

### Post by uberlube on 2008-02-25
Did you install your graphics driver?

---

### Post by Dracar on 2008-02-25
It was working before, then one day i just went to get on and it would not load. So I tried that command and then I got xorg or w/e is not configured right. If it helps I have a stock dell inspiron b130

---

### Post by uberlube on 2008-02-25
try:

sudo dpkg -phigh xserver-xorg

or:

sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by Dracar on 2008-02-25
ive ran the second one multiple times to no avail, im on the pc in windows now, so I will try the first one in a minute when i switch over

yea didnt work

---

### Post by Dracar on 2008-02-25
Ok, have to bump, don't want to start another new topic with this, i need help. Ubuntu has like 90% of my hard drive and my windows partition is full up, keylogged, and glitched. I need to get ubnutu working.

---

