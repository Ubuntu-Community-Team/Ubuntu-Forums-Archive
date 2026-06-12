---
title: "voltage control on fan header for leds"
date: 2021-09-20
forum: General Help
---

### Post by tominto on 2021-09-20
Hello everyone
I have a new motherboard(Asrock b450 itx) with a cpu header and several four pin pwm headers also usable as three pin headers.  
If I plug in a uv dimmable led strip into a fan header, I've found out I can change the header to use dc mode in Bios.  I can also change 'temperature' settings from 60 to 100, and this will dim or brighten the led strip.  
I can then boot into ubuntu with a set brightness to the led strip.  However, once I'm in ubuntu, I can't vary the brightness, in anyway I can see.  Is there a way to do this? 
 i'd like to have control over the led strip other than having it on or off.

---

### Post by tominto on 2021-12-05
bump

---

### Post by HermanAB on 2021-12-05
Well, you have to modify the fan control device driver.  It is possible to do that but it sure will take you a while to figure out how.

---

