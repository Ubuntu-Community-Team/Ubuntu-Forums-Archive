---
title: "&quot;Switch User&quot; freeze system"
date: 2007-12-14
forum: General Help
---

### Post by BjoeHrn on 2007-12-14
Hi!

I hope this is the right subforum :-).

I've installed Gutsy on my 32bit mashine. Make the updates and installed the fglrx driver with the ubuntu system tool.
Every time when I click on the "Switch user" button I get a blank screen and my system freeze. Also STRG+ALT+Backward and STRG+ALT+ENFT has no function after the freeze.

When I disable fglrx and use the radeon driver I can switch the user without a freeze.

I use a Radeon 9600 graphikcard and the fglrx version 7.1.0-8-37+2.6.22.4-14.10.

Can anyone help me?

Thanks a lot!

Regards
Bjoern

---

### Post by SunnyRabbiera on 2007-12-14
the switch user applet is buggy admittedly, it does have some things that I dont like

---

### Post by Ber P on 2007-12-14
I think it is a known bug with the fglrx driver. Same thing happens on my machine. I can, however, logoff and then login as a new user. Not very smart though.

---

### Post by BjoeHrn on 2007-12-14
Hey!

Thanks for your replies! 
I hope in near future there will be a fix for this bug. So long I use the method from Ber P and log out completly and login with the new user.

If someone has a fix for this bug, please contact me :)!

Thanks a lot!

Edit: Can I fix the bug, when I install a fever version of GDM? Or use a other login manager?
Edit 2: I found this bug report it is the same problem than I have but without a fix :/ ([https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/107115](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/107115))

Regards
Bjoern

---

