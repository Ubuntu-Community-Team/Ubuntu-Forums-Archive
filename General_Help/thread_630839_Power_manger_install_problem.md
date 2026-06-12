---
title: "Power manger install problem"
date: 2007-12-03
forum: General Help
---

### Post by prow on 2007-12-03
i recently updated with update manager and now everytime GNOME loads i get a pop up window that says:

Install Problem!

The configuration defaults for GNOME Power Manager have not been installed correctly.  Please contact your computer administrator.

and all my settings are gone or messed up in some way.  Its really irritating.

Please help

---

### Post by Jeff_From_VA on 2007-12-04
I am right there with you.  I did a fresh install of gutsy the other day and got this same error at boot, then re-installed gutsy and all was fine for a day, and now right back to it.   

Gutsy is officially completely and totally  useless, I was stable with feisty for a very long time, then my dumbass just had to upgrade, it's been nothing but problems since. 

Gutsy stability is somewhere between Windows ME, and Vista, closer to ME then Vista..... Shittiest Linux distro out yet.... I spend more time fixing it then when I ran gentoo.....

I am hoping I can keep this box up long enough to burn a feisty cd, so I can "upgrade" back to feisty.

---

### Post by VHans on 2007-12-07
Since a few days I am having the same problem. Don't know where it comes from.

---

### Post by LiquidSam on 2008-01-08
I just installed Gutsy on an HP Pavilion 7935 and after updating with the Package Manager I receive this error as well. Can anyone shed light on this issue?

---

### Post by backwardselvis on 2008-01-12
Same Here! AMD64 7.10

---

### Post by scotboi on 2008-02-28
I too have this problem - decided to upgrade to gutsy today from feiesty - even though not much used to UBUNTU - but was sick of it not having software need so thought that this would have been sorted to extent in 7.10. Now get message gnome power manager did not install properly" and I can not switch off- it always seems to just want to reboot - and seems to be due to prob with gnome power manager - according to Bugzilla. Do not know what to do and how to fix this problem? Each time turn off now have to hit the mains supply to turn of before reboots.

See no one has answered this problem here but lots of us have this problem. Can anyone out there who has any idea what we can do please tell us - as getting on my nerves now

---

### Post by russellnation on 2008-03-15
try 
sudo dpkg --configure  -a
sudo apt-get -f install

seems to have worked for me....

---

