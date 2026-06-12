---
title: "Edgy nor Feisty working for me.."
date: 2007-02-08
forum: General Help
---

### Post by jimhaddon on 2007-02-08
Hi all,

Just thought you might like to know, I have been using Ubuntu dapper for some time now, and thought it might be time to upgrade to edgy. So, i tried to upgrade using the official method, but this failed leaving me with an unusable system.

Not a great problem, i thought I'll just do a fresh install. So  downloaded fesity just to try it out, and it installed up to 75% and then just froze. 

Next.. another download, this time Edgy. This would not even boot using normal or safe graphics mode. Just hangs part way through boot. Can't even use the LiveCD.

Next, I thought I'll try Kubuntu Edgy. Again, this was exactly the same, couldnt even get to the LiveCD using safe or normal modes.

This is on a P4 @ 3.98 Ghz, 2GB DDR2 Ram, ATI card. A-bit aa8xe mobo

---

### Post by compmodder26 on 2007-02-08
This was a problem I also had with Edgy (haven't tried Feisty).  I too have an ATI card.  With Dapper, it couldn't boot with the normal graphics mode but it could with safe graphics.  Edgy wouldn't work either way.  The best I can tell is that Edgy still wanted to use the "ati" driver in safe graphics mode instead of dropping to vesa.  My solution was to install Edgy with the alternate CD.  After it installed, I booted into recovery mode and set the driver to vesa.  Worked fine after that.

---

### Post by jimhaddon on 2007-02-08
thanks! I'll try that right now!

---

### Post by Surgeon General on 2007-02-08
FWIW, you might want to look at this:

[https://wiki.ubuntu.com/EdgyKnownIssues](https://wiki.ubuntu.com/EdgyKnownIssues)

it only takes some patience and time to read the docs I'm sure you'll be surfing in Edgy in no time. ;-)

---

### Post by jimhaddon on 2007-02-08
Ok, I just tried using the alternate CD using text install mode, and this failed. Error was 'Could not figure how to install base system, as no cd could be found'.

....Useless..

Next, I tried the normal CD with the options that you gave me there, (pressing F6 etc), and this failed also. Just hung on startup, didnt even get to the Live Desktop. 

Edgy seems pretty useless to me at the moment!

---

