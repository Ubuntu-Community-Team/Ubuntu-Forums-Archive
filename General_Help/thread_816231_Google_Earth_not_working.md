---
title: "Google Earth not working"
date: 2008-06-02
forum: General Help
---

### Post by ekmon1582 on 2008-06-02
I just got Google Earth to work, but now when I start it, all I see is stars. No picture, nothing. It tells me it's my video card, but I don't see how that can be, because I can run Google Earth fine in Windows. I'm running Ubuntu 8.04 on VMware server, with Windows XP as the host. If anyone has some advice, that'd be great.

---

### Post by Sub101 on 2008-06-02
Mite not be the same for you but i have to run google earth as root. If i dont i just get a black box with no planet etc.

---

### Post by BlueSkyNIS on 2008-06-02
No need to run it as root, just remove the following directories:

~/.config/Google
~/.googleearth

Into terminal type:

```
sudo rm -rf ~/.config/Google
sudo rm -rf ~/.googleearth
```

and run it as normal user.

---

### Post by ekmon1582 on 2008-06-02
Awesome, it works, thank you!

---

### Post by Younio on 2010-05-08
Works in ubuntu 10.04 too. Thank you :)

---

### Post by abdusamed on 2010-08-04
gigapixel, youtube, user uploaded pictures doesn't work! If I click on the empty picture window all I can do is drag the invisible picture! Basically only google earth works, not the stuff on googel earth... any fix?

See attachement

---

### Post by pbhill on 2010-08-08
Thanks! It works in 10.04.
After about a year of doing without Google Earth I am so glad to have found your post!
Why is this happening?

---

### Post by abdusamed on 2010-08-13
`bump..still not working for me.. i get those blank windows mentioned in the previous post of mine

---

