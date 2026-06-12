---
title: "your thoughts on having HOME on seperate partition?"
date: 2006-10-28
forum: General Help
---

### Post by syxbit on 2006-10-28
i tried it, but whenever i'd reformat (leaving home untouched) it would keep lots of settings (often the setting that were messed up that were making me format in the first place) also, all the shortcuts i had were now to programs  i didn't have installed.
all in all, a bit of a pain.

instead this time i just left a 75GB partition blank, and then mounted it.
i plan on using this kind of like my home dir, only it's just files :)
your thoughts on pro's con's ?

---

### Post by Aerandir on 2006-10-28
At least theoretically, a seperate /home partition makes distribution upgrades easier.  But on the other hand, it is more convenient if everything is on one big partition and config files don't get messed up.

---

### Post by taurus on 2006-10-28
Easy to reinstall if you somewhere trash your system since you can keep all your personal settings in /home untouch!!!  I don't see any con in having a seperate /home at all...

---

### Post by syxbit on 2006-10-28
but are all settings to all programs kept here?

---

### Post by taurus on 2006-10-28
For your account, yes.

---

### Post by ~LoKe on 2006-10-28
> **syxbit said:**
> but are all settings to all programs kept here?

If that's really a problem for you...
```
sudo rm -Rf .*
```

---

### Post by syxbit on 2006-10-28
so that will delete all hidden folders, when i reinstall, will ubuntu recognize i don't have settings and put the default stuff back in ?

---

### Post by ~LoKe on 2006-10-28
> **syxbit said:**
> so that will delete all hidden folders, when i reinstall, will ubuntu recognize i don't have settings and put the default stuff back in ?

I haven't reinstalled with my home folder on a separate partition yet, but logically, yes, that would happen.

---

### Post by taurus on 2006-10-28
> **syxbit said:**
> so that will delete all hidden folders, when i reinstall, will ubuntu recognize i don't have settings and put the default stuff back in ?
Yes, it would, assuming you mount that partition to /home during the installing process...

---

### Post by Christopher on 2006-10-29
Is there a link for a "HOW TO" on this. Thank you in advanced.  :D

---

### Post by taurus on 2006-10-29
> **Christopher said:**
> Is there a link for a "HOW TO" on this. Thank you in advanced.  :D
Is this what you are having in mind?  Otherwise, just make a new thread for your question!

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by ~LoKe on 2006-10-29
> **Christopher said:**
> Is there a link for a "HOW TO" on this. Thank you in advanced.  :D

[Text](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/).  Only one I know of.

---

### Post by Christopher on 2006-10-29
Both of those links are great, thank you. :D

---

### Post by aysiu on 2006-10-29
Just so people know, I created the first tutorial posted **based on** the second one posted. I just added some more explanation and a few screenshots.

---

