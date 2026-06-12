---
title: "[SOLVED] logon white screen"
date: 2007-07-31
forum: General Help
---

### Post by pretender? on 2007-07-31
Hello out there 
I recently had an issue where i would drop back to 64x480 res for no reason.  In an attempt to fix the problem i disabled redistrict drivers.  However this caused me to loose X upon reboot

i then did a sudo dpkg-reconfigure xserver-xorrg

This got X back but when loging in now i get a white screen BSOD 

I removed beryl but this did not fix the problem.  

How can i get X back

I am running a NVidea FX 5200 video card 

Regards
Pretender?

---

### Post by fistfullofroses on 2007-08-01
What GUI are you using?

---

### Post by Shib on 2007-08-01
it's not a white BSOD... it's beryl not working correctly.

try this out...

apt-get install xfce4

then change your session type at the logon prompt to xfce4... I'm guessing that gnome (or kde, whichever you installed beryl on top of) is autostarting beryl... or at least trying to.

---

### Post by nitro_n2o on 2007-08-01
did you try to enable restricted drivers back? why'd u disable restricted drivers anyways..

---

