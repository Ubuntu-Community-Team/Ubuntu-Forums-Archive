---
title: "peerguardian errors with Ubuntu 14.04"
date: 2014-04-30
forum: General Help
---

### Post by macstl on 2014-04-30
I installed peer guardian on ubuntu 14.04 and get error message when I start it. Removed and reinstalled= same thing. I previously installed it on ubuntu 12.04 with no problem. Is this a known issue?

error-- could not use kdesu(do) or gksu(do) to execute the command requested.

---

### Post by macstl on 2014-05-01
I loaded afresh install of Ubuntu 12.04 and I installed pglgui ok and it works without error. I think I am going to stay here.....

---

### Post by jre on 2014-05-20
For future reference:
pglgui requires root privileges for some commands. The helper program for this is configurable in pglgui (Options- Settings - Sudo front-end). If you can't start pglgui edit in ~/.config/pgl/pglgui.conf the entry [paths]. In Gnome environments I recommend to use gksu:
```
[paths]
super_user=/usr/bin/gksu
```

In the long run we will replace this by using policykit. Help welcome.

---

### Post by macstl on 2014-05-20
JRE:
I installed pglgui using the instructions at : [http://sourceforge.net/p/peerguardian/wiki/pgl-Install-DebianUbuntu/](http://sourceforge.net/p/peerguardian/wiki/pgl-Install-DebianUbuntu/)
It installs a gui I put In my unity launcher . It only has two tabs= control and configure . In configure tab there is no options- settings-sudo front-end. 
When I start and stop the program it pops up a request to put in sudo password.  All installs and works fine in 12.04 only not in 14.04 
I still don't understand....

---

### Post by jre on 2014-05-20
The menu item "Options" is above the two tabs that you see. I guess in Unity this is on the top left of your display. (it should be where other programs have menu items like "File" and "Edit", ...).

Otherwise you still can edit ~/.config/pgl/pglgui.conf (see above).

---

### Post by macstl on 2014-05-20
I found it thanks!  it is set for = /usr/bin/gksudo
So do you mean that when I install it in 14.04 this is probably not set right?

---

### Post by jre on 2014-05-20
yes, gksudo is broken. Use 
/usr/bin/gksu
instead

---

### Post by macstl on 2014-05-22
I tried doing a complete new install on another computer of 14.04 and it hangs up ="configuring bcmwl-kernal-source(amd64)  I tried both dvd and usb install
I do skip and get error that acpi is unsupported. It is a gateway 64 bit amd64. I guess it does not like it cause it is not intel.  Centos 6.4 loads fine on it. I just don't seem to be having any luck with ubuntu 14.04
I got dual boot on intel thinkpad = win 8.1 and ubuntu 12.04  I don't know if I want to add a triboot of 14.04

---

### Post by macstl on 2014-05-22
oops!
I guess I need to try the ubuntu 14.04 mac amd64 verslion on the Gateway turion 64 amd computer....

---

### Post by macstl on 2014-05-24
On this 64 bit amd turion gatway computer i have tried to load 14.04 64 bit and also the amd 64 version and the 32bit version. I tried loading 12.04 64 bit and 32bit. The only thing that loads is 12.04  32 bit.  This doesn't make any sense to me .This is a 64 bit machine.
 I will keep 12.04 until they at least get to a point update on 14.04 .
I don't understand why gksudo is broken in 14.04 and not in 12.04

---

