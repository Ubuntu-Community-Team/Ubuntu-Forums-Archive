---
title: "Automatic logout when running Wine application."
date: 2007-01-11
forum: General Help
---

### Post by mmcmonster on 2007-01-11
Hi.
  I had everything setup and working perfectly in wine (was using DVDShrink and DVDDecrypter, amongst other applications).  When I ran one of these apps earlier today, the whole screen became garbage for a second, then black, and then I was presented with my standard GDM login screen.  It looks like I was forcibly logged out.

  I renamed my ~/.wine folder and then ran winecfg, and the same thing happened.

  I'm running Dapper with the latest wine release from their repositories.  I also made sure I'm not running any wine processes (ie:wineserver) when I try winecfg.

  Any suggestions?

---

### Post by mmcmonster on 2007-01-11
Also, I did an "apt-get remove --purge wine", and subsequently reinstalled it, and had the same problem.

---

### Post by mmcmonster on 2007-01-13
Apparently my problem wasn't with wine, but with nvidia.  Apparently while my desktop appeared stable, it would log me out if I tried any opengl applications.  Somehow I installed differing versions of the nvidia drivers. :-(

Anyone happen to have tips about troubleshooting the nvidia driver versions?

---

### Post by zorkerz on 2007-12-23
could you explain more about what drivers/packages you actually changed. I am having the same problem. There are a number of people who have had this with nvidia cards but i have an intel x3100 and did not think I would have any similar drivers.
thanks

---

