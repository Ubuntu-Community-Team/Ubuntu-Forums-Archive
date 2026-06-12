---
title: "Possible video driver problem? Reboot black screen, Multiple Reboot eventually login"
date: 2015-09-27
forum: General Help
---

### Post by Jdfskitz on 2015-09-27
So occasionally when I reboot I will constantly get a black screen, I will get to the grub loader, try multiple different states in the advanced options and I will still get a black screen.
but at random it will just decide to work.

I think it's a video driver problem because it will not detect my monitors on occasion.

Radeon HD 6800
Ubuntu Live Studio 15.04

Using Proprietary Drivers W/ Updates

---

### Post by Jdfskitz on 2015-09-27
possible motherboard issue?

---

### Post by DK1993 on 2015-09-27
Could you possibly give us more information regarding the computer and motherboard that it is using. It may be of some use to help troubleshoot the problem. If this problem is new (i.e it didn't happen when you first installed Ubuntu Studio), I'd concur with Jdfskitz in that it is a motherboard or graphics card issue. Do you happen to have a Live CD or USB laying around? If so, does it give you this problem when using the installation media?

---

### Post by Jdfskitz on 2015-09-27
64 bit Operating System. ASUS M5A97

It does not give me that problem.

I think it began shortly after using this script

#!/bin/bash
xrandr --output DFP4 --auto --output CRT1 --auto --right-of DFP4

to extend monitors as a launcher

---

### Post by Jdfskitz on 2015-09-28
bump

---

### Post by Jdfskitz on 2015-09-28
..bump..

---

### Post by Jdfskitz on 2015-10-06
Not resolved however.

--Work around--
Ubuntu Software Center -> Grub Customizer
General Settings Tab -> Show Menu (I also editted etc/grub.conf) [sudo gedit /etc/default/grub.cfg
added new line 
GRUB_HIDDEN_TIMEOUT_QUIET="false"

and of course use the grub customizer and make it pretty.

---

