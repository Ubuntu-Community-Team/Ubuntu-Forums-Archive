---
title: "Fonts"
date: 2007-04-14
forum: General Help
---

### Post by gunthermeyer on 2007-04-14
Does any one know where I can find some fonts that I can install into the word processor like Old English or fancy scriptive type fonts? I tried the synaptic package manager but no such luck. Is there any other place that I can look at? Thanks

---

### Post by iXneonXi on 2007-04-14
Try adding repositories like medibuntu or other repositories with fonts.

---

### Post by x1a4 on 2007-04-14
Hi, 

Check your _/etc/X11/xorg.conf_ file.  On my computer the FontPath paths were incorrectly configured.  

As the super user, open _/etc/X11/xorg.conf_ and check to see if the files in  section "Files" are correct.  

I had to change mine from _/usr/share/**X11/fonts/**_ to _/usr/share/**fonts/X11/**_.  Once I did that, I got a ton of new fonts.

---

### Post by gunthermeyer on 2007-04-15
Thanks x1a4 for the information and I will get right on it.

---

### Post by x1a4 on 2007-04-15
> **gunthermeyer said:**
> Thanks x1a4 for the information and I will get right on it.

This will not guarantee you'll get new fonts--you still have to download them--and /usr/share/X11/fonts/ is also a valid font location.  An alternative method might be to create symlinks in it to /usr/share/fonts/X11/<font-type>/

---

### Post by FalconP on 2007-04-16
More than 6700 free fonts available[ here]("http://thelinuxbox.org/").  Have fun.

---

