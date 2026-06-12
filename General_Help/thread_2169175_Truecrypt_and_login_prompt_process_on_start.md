---
title: "Truecrypt and login prompt process on start"
date: 2013-08-20
forum: General Help
---

### Post by ShadowMonster on 2013-08-20
Hi 

I need some suggestions and/or help to make solution with I need. 
Everywhere I can read about it how to auto-mount some encrypted HD on bot or start. Well I'm looking some little opposite. 

I would like that ubuntu will normally start from non-encrypted volume etc. and in some point he will execute script to mount one encrypted drive before login screen. But **I want it to prompt for password** and wait to put password by me. Until it will not be correct password it will prompt it all time. When correct it will go to login screen. I know bash little but I'm not sure when and how correctly put that script into ubuntu start process.

Any help/suggestion appreciate.

Regards

---

### Post by David_Pecot on 2013-08-29
Hi,
There's no reason to mount an encrypted drive when no one is logged in.  Why would you need to do this?

---

### Post by ShadowMonster on 2013-09-16
I keep on USB some important stuff like ssh keys VPN keys ad some important docs etc. I would like system to prompt for it first to mount this usb and then start work because whatever I need mount it manually later when I log to ubuntu - I think also to make log into ubuntu base on keys but everywhere in internet is about how make it auto-mout and auto-login on USB but I don't want auto-mount I want it to prompt for ex. ssh key password.

Thanks for interest.

---

