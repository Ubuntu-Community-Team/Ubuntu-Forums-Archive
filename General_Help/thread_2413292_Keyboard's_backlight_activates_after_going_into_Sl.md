---
title: "Keyboard's backlight activates after going into Sleep"
date: 2019-02-23
forum: General Help
---

### Post by SnuKies on 2019-02-23
I have a Sony Vaio SVE 

Whenever I boot up, my keyboard's backlight does not work. I've been looking up on the internet for solutions*, but still nothing.  However, if I put my laptop in sleep mode and then open it again, the backlight works as expected! 

My question is: what scripts are executed when awaking from sleep? Maybe I could solve my boot problem by taking a look at them    


** What I tried:*
[LIST]
[*]*editing /sys/devices/platform/sony-vaio; adding kbd_backlight here -> I get `access denied`*
[*]*adding to /etc/modprobe.d/sony-vaio.conf `options sony-laptop kbd_backlight=1` -> not working*
[/LIST]

---

