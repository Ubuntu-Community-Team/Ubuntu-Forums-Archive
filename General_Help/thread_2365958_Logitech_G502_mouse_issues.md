---
title: "Logitech G502 mouse issues"
date: 2017-07-12
forum: General Help
---

### Post by cruz12141214 on 2017-07-12
Hey guys,

I have a Logitech G502 mouse, and it randomly stops  working whether Im using it or not, and for some reason both my keyboard  and the mouse become un responsive and the only thing i can do is use  the touch pad to reboot any help  please....


Yes I have tried different Ubuntu releases 16.04 and 16.10 and the same thing happens, so far it only happens with this mouse... I have tried a different generic mouse but it is not comfortable so i cant use it, but it works

Asus G752VL
Ubuntu 17.04

---

### Post by cruz12141214 on 2017-07-13
anyone know what i can do?

---

### Post by efflandt on 2017-07-13
The only time I had an issue where keyboard and mouse buttons randomly stopped responding (while mouse cursor usually still moved) was when I had a failing graphics card. That became more evident when I started getting graphic glitches during boot and nvidia driver while booting said hardware not responding. Never had that problem again using major brand graphics cards. But I guess it could be any number of issues from incompatible RAM to something overheating. Check /var/log/syslog from just before you had to reboot to see if that reveals anything. You could install psensor which can keep track of min/max and current temperatures of cpu, gpu, drives, and fan speeds and optionally plot graphs or log data.

The mice I currently use are all wireless Logitech models that use Unifying USB receiver with no glitches: MX Master (rechargeable li-ion), Anywhere MX (any surface, best used with rechargeable ni-mh batteries), and small M185 laptop mouse. The only one that gave me any trouble was that M1 button on Anywhere MX stopped working after much gaming, but disassembly and contact cleaner resolved that (still original switch).

---

### Post by cruz12141214 on 2017-07-13
see thats the thing, I cant check logs or anything liek that, as both the mouse and keyboard become unusable if i use this mouse for too long, this only happens with this mouse, even if Ubuntu is a clean install, or with all current released updates, As for GPU/CPU I know its not failing, no other mouse gives me this issue, and the issue wont appear if I just use the touch pad which is not Ideal..... I thought it might be the device goes to sleep, but why does it take the labtop keyboard with it? and I dont have labtop settings installed...

---

### Post by cruz12141214 on 2017-07-21
does anyone know what i can do?

---

