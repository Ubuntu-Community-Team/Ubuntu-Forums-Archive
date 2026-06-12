---
title: "Black/dark screen on every second boot..."
date: 2013-03-06
forum: General Help
---

### Post by malapradej on 2013-03-06
Hi,

I have just removed the proprietary fglrx driver on ubuntu 12.04 on my hp pavilion dv6 using the system settings > hardware > additional drivers method. When I reboot, ever second boot succeeds with the other going into a black screen, although I can hear that ubuntu has started and requesting a login in the background. Usual drum sound in the background.... I have searched on various forums but none describe my specific issue. I have tried several times and it is only every second boot. :confused:

Any advice will be greatly appreciated...

Jacques

---

### Post by dino99 on 2013-03-06
so you are using catalyst now or radeon ?

if you have an xorg.conf (which is not required) then delete it:

```
sudo rm /etc/X11/xorg.conf
```

---

### Post by malapradej on 2013-03-06
Thanks dino99 for the reply.

I am not sure what is the difference and to be honest I don't know which one is running. I have uninstalled the fglrx driver and from what I understand ubuntu would use it's own driver at next reboot. Please help me out here. I have just removed the xorg.conf file and will reboot. Will get back to you with results.

Cheers,

---

### Post by malapradej on 2013-03-06
That sorted it out. Thanks a million. Now all that remains is my overheating issue. But that is for another thread. Would still like to know how to find out what I am running. Catalyst or Radeon. As far as I understand it is an ATI radeon card...

---

### Post by bogan on 2013-03-06
Hi!, **malapradej.**

```
lspci -nnk | grep -iA3 vga
glxinfo | grep -i opengl
```Will tell you what video card you have and which drivers are available and in use.
```
/usr/lib/nux/unity_support_test -p
```Will show if it is 3d compatible.

Chao!, **bogan**.

---

