---
title: "Keyboard backlight not working"
date: 2017-07-28
forum: General Help
---

### Post by deadmoon on 2017-07-28
Hello all,

I have a problem with my keyboard backlight. The laptop I'm using is a Sony Vaio SVE1711W1E. As usual, Sony does not provide any drivers for their laptops, but with Ubuntu 14.04 everything worked fine, without any interference. When I updated to 16.04, keyboard backlight stopped turning on (noted that I made a clean install). 

After a couple of searches over the forums, I figured out that I have to change /sys/devices/platform/sony-laptop/kbd_backlight to 1, using modprobe.

But there is a problem, there is no file kbd_backlight. What does this mean? Specific module disabled? Also, I tried to create this file but got the message 'permission denied'. After searching, I discovered that everything under /sys is kernel files and that's why I can't modify them.

Any help is appreciated. Thank you!

---

