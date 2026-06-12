---
title: "[SOLVED] Weird display after monitor upgrade"
date: 2008-02-04
forum: General Help
---

### Post by lsmobrian on 2008-02-04
Im running gutsy.  I had a 15"(1024x768) and upgraded to a 19"
I unplugged the 15 and plugged the 19 and the display looked fine, then i ran(& re-ran) dpkg-reconfigure xserve-xorg and restarted X

upon restart the gdm was at 600x480 res and the monitor was at 1280x1024, meaning that gdm only took up a quarter of the screen.  When i logged in, the desktop is at 600x480 as far as the panels go, but when I open an application it is at 1280x1024.  The color is also off (probably 16 instead of 24 bit)


When i goto any display conf GUIs they only list 600x480 @ 60  ... I think I have had this monitor at 70 before


emachine T6414
AMD Athlon 64 3200+
ati radeon xpress 200


Any ideas?  I can post any conf files if needed

---

### Post by lsmobrian on 2008-02-04
I looked up the technical specs for the monitor and the horiz&vert rates I had were off by 1 on the max.  The whole screen is now used for gdm and panels, but seems I'm stuck at 600x480@60 as that is still the only option in any GUI

Any things I can try?

---

### Post by lsmobrian on 2008-02-04
restricted driver manager turned off ati driver, fixed as soon as i checked and rebooted

---

