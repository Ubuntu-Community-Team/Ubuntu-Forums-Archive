---
title: "&quot;select desktop environment&quot; out of display"
date: 2012-10-23
forum: General Help
---

### Post by masuch on 2012-10-23
Hi,

In 12.10 ubuntu:

On login screen when click on "select desktop environment"
it is going to roll down and some items are out of display.
I do not know how to get on item (keyboard does not work, only mouse) (like xubuntu, and those on the alphabetic end) and choose that desktop environment.

Is there any workaround how to click on it ?
Or how to display it in the middle of the display as it was in 12.04 ?
I cannot even change desktop because I do not see "ok" button and cannot get on it by keyboard.

see attached picture. In 12.04 it was ok.

please any help. where is located config file or anything ?
thank you,
kind regards,
M.

---

### Post by dino99 on 2012-10-23
check both :
- display settings, into System Settings
- xorg.conf (/etc/X11/xorg.conf: maybe you need to remove it, now the kernel dont need it)

---

### Post by masuch on 2012-10-23
> **dino99 said:**
> check both :
- display settings, into System Settings
- xorg.conf (/etc/X11/xorg.conf: maybe you need to remove it, now the kernel dont need it)

Thanks for it but did not help.

I do not have display settings. I have "display" - there is only resolution,refresh rate,rotation,reflection.
or "monitor settings" - only resolution and refresh rate - it is application from lxde.

(I am not using unity - I tried it more than year ago so maybe something is missing , I did not even log in within unity desktop environment? I am using ubuntu with xfce 4.10 desktop.) 
What should I check in display settings ?

(Is it possible to use terminal - I am not using desktop configuration software many times ?)

---

