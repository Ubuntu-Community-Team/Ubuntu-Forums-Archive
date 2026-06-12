---
title: "Monitor problems"
date: 2006-08-14
forum: General Help
---

### Post by Benzorro on 2006-08-14
I just bought a new monitor(Sceptre X20G) wide screen.  In XP it works fine(1280x720) but in Ubuntu all I get is vertical lines.  I used to have a CRT monitor before this and Ubuntu worked fine.  What do I have to do to get the screen to work in Ubuntu?

---

### Post by Dr. Nick on 2006-08-14
Edit your /etc/X11/xorg and try adding the 1280x720 res to it.

[http://www.geocities.com/aebcoat/index.html](http://www.geocities.com/aebcoat/index.html)

---

### Post by evergreen on 2006-08-15
> **Benzorro said:**
> I just bought a new monitor(Sceptre X20G) wide screen.  In XP it works fine(1280x720) but in Ubuntu all I get is vertical lines.  I used to have a CRT monitor before this and Ubuntu worked fine.  What do I have to do to get the screen to work in Ubuntu?

This is what I do. Find your mannel for the monitor find the Scanning Frequency something like

EXAMPLE Frequencys yours maynot be the same!

Scanning Frequency
Analog: 24-82 kHz (H), 50-75 Hz (V)
Digital: 31-80 kHz (H), 50-75 Hz (V)

Then do

dpkg-reconfigure -plow xserver-xorg 

work your way thought the tool and you will be able to set up your monitor.

This is what I was thinking of then I post It´s helped me in the past [https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

---

### Post by Benzorro on 2006-08-16
Thanks guys I am up and running.  So much to learn and so little time.

---

