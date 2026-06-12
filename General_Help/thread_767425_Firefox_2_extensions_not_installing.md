---
title: "Firefox 2 extensions not installing"
date: 2008-04-25
forum: General Help
---

### Post by BWF89 on 2008-04-25
I'm using Kubuntu 8.10 KDE4 Remix and whenever I go to install extensions for Firefox 2 I always get:
```
Could not install file to <address to firefox directory which I'm not going to type up>
because: unexpected instllation error
Review the error consol for more defails.
-203
```

What exactly is happening? I've tried restarting firefox, logging out of KDE, and even restarting the computer. But nothing seems to be working.

---

### Post by lancern on 2008-04-25
Are you using firefox 3 beta 5?..if so alot of the extensions may not yet work with FF3..

---

### Post by BWF89 on 2008-04-25
> **lancern said:**
> Are you using firefox 3 beta 5?..if so alot of the extensions may not yet work with FF3..

No, I'm using the package from the repos called "Firefox 2". I originally just installed the regular "Firefox" meta package but than I realized that the Firefox beta was installed along with that. So I immediately uninstalled it and installed Firefox 2.

---

### Post by rignes on 2008-04-25
I'm having the exact same problem here too.  :(

---

### Post by calibre97 on 2008-04-26
Same here. I fixed it under Kubuntu 8.04 RC but now I'm running the release version of Ubuntu and I can't seem to get it to work. Uninstalling Firefox 3 doesn't do the whole thing. I had to remove some add-on or extension directory and then install Firefox 2 and then it worked but that doesn't seem to be happening now. I'll try uninstalling 2 again and then SUDO removing Firefox items from a terminal and then installing Firefox 2 again and see what happens.

---

### Post by rignes on 2008-04-26
I fixed it last night.  All I had to do was to remove my .mozilla directory which contains firefox's profiles.  I imagine I could have just deleted the actual profile directoery in .mozilla/firefox.  Once I did that and re-ran firefox-2 it worked normally.  Zero problems installing extensions.

I'm guessing the problem was caused by the fact that I ran Firefox 3.0b5 first before installing firefox-2.  It seems the profile created by 3.0b5 is not compatible with 2.x.x.x.

Anyway, that worked for me.  Maybe it'll work for someone else.

---

### Post by ACMiller on 2008-04-26
If you rename or delete .mozilla/firefox/profile.ini in your home directory, while firefox is closed, firefox then creates a new default profile the next time you open it (i.e. a firefox 2 profile, to replace the incompatible firefox 3 one). This worked for me, although you then need to start from scratch with your bookmarks etc.

Hope it works for you

---

### Post by BWF89 on 2008-04-27
Thanks for the help. But I coudln't put up with KDE4's antics anylonger. I downgraded to 3.5.

---

