---
title: "LightDM using 30mb for no good reason"
date: 2013-01-12
forum: General Help
---

### Post by jontheid on 2013-01-12
Hi - have just come back to Lubuntu after messing around with many other distros and it is good to be back. Installed 12.10 on my Toshiba L30 and it works well, but uses much more memory than 11.10 did. I could get 11.10 down to about 76mb idle and 12.10 was around 120mb! (This is why I gave up on Lubuntu and tried loads of other things . . . )

Finally found out what was eating up the extra ram - lightdm was using 30mb to do pretty much nothing. I've now gone back to using lxdm and I'm getting about 86mb total use at idle, and it looks better too.

I made the big mistake of removing the lightdm package which uninstalled loads of lubuntu stuff, when I reinstalled it, it installed loads of Unity stuff, has taken a good while to get everything back to normal.

Can anybody explain why lightdm was used in recent Lubuntu releases? LXDM seems so much better to me.

Cheers
Jon

---

### Post by 2F4U on 2013-01-13
You would need to ask the developers why they switched, but likely reasons are
- configurability
- standardization (many Ubuntu-based distros are using it)

---

