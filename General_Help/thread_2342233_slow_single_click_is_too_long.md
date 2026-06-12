---
title: "slow single click is too long"
date: 2016-11-04
forum: General Help
---

### Post by courtens on 2016-11-04
I am a slow clicker...

Most of the time my clicks are too slow to register as a single click. In other words, my single-click are too long. I think right now my clicks are being interpreted as click and hold and release --- not just a single click. This makes using the main menu bare unresponsive and unusable. One could almost say it's a bug.

How, and where can I extend that setting? 

Thanks

---

### Post by CantankRus on 2016-11-05
You may have to practice tapping instead of pressing or if you have trouble doing this 
try hover click in "universal access".
You can also access global menu items by pressing alt and typing.

---

### Post by CantankRus on 2016-11-05
After another look it seems you can adjust this in dconf.
Run this terminal command...
```
gsettings set com.canonical.Unity.Decorations grab-wait **500**
```

Means you can hold down mouse1 longer before the cursor grabs the titlebar.
The default is 175 and can be set to a max of 1000 millisecs.

If still not enough try (or whatever you like between 0 and 1000)...
```
gsettings set com.canonical.Unity.Decorations grab-wait **750**
```

To set back to default...
```
gsettings reset com.canonical.Unity.Decorations grab-wait
```

---

### Post by courtens on 2016-11-05
500 is perfect. :D

Thank you so much! This really makes all the difference. **I hope someone will take the time to report this as a [COLOR=#b22222]mini-bug[/COLOR].** It is very aggravating when the menu is not popping up, and one have no idea why not. It took me some searching to just find out what it actually happening. If you want to experience my experience set it to 50 and try to click on the menu. :-?

---

### Post by mc4man on 2016-11-22
> **CantankRus said:**
> After another look it seems you can adjust this in dconf.
Run this terminal command...
```
gsettings set com.canonical.Unity.Decorations grab-wait **500**
```

Means you can hold down mouse1 longer before the cursor grabs the titlebar.
The default is 175 and can be set to a max of 1000 millisecs.

If still not enough try (or whatever you like between 0 and 1000)...
```
gsettings set com.canonical.Unity.Decorations grab-wait **750**
```

To set back to default...
```
gsettings reset com.canonical.Unity.Decorations grab-wait
```

This does appear to be the issue, filed bug,
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1643713](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1643713)

---

### Post by CantankRus on 2016-11-22
Yes, the default for mouse double click time is 400ms which seems more realistic for the grab-wait time as well. (Added "me too")

---

