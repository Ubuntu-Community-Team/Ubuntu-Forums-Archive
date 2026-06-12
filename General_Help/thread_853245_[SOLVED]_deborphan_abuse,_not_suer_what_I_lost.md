---
title: "[SOLVED] deborphan abuse, not suer what I lost"
date: 2008-07-08
forum: General Help
---

### Post by leetrefz on 2008-07-08
I took too much out with deborphan and now I only boot to command line. Don't remember what. Would be nice if there was one metapackage that gave me everything in the original install. even a list of packages in 8.04 would be nice, assuming if I put the right thing back it should work again just like that. 

Thanks for any help!

---

### Post by Elfy on 2008-07-08
Are not *buntu-desktop's the meta package?
 Try installing your version eg

sudo aptitude install ubuntu-desktop

or xubuntu, kubuntu

Didn't think that deborphan took anything that was required though tbh.

---

### Post by leetrefz on 2008-07-08
I did that, didn't work. Is there no meta package for the whole OS? I think I removed something required to use C language, which for some reason didn't show anything depending on it. I only remember things like avahli, atapi, bc & dc among what I removed. If I want to start the gui from command line what do I type? maybe it'll either work or give out a useful error message.

---

### Post by kdorf on 2008-07-08
You could try "startx". Or you could try "sudo /etc/init.d/gdm start" if you're using gnome or xfce, or "sudo /etc/init.d/kdm start" if you're using KDE.

---

### Post by leetrefz on 2008-07-08
pretend this post isn't here.

---

### Post by leetrefz on 2008-07-17
when i did startx it said it couldn't find vesa. i guess I took it out with deborphan. but when i went sudo apt-get install vesa it said it couldn't find module. Oh woe.

---

### Post by Elfy on 2008-07-18
Try using aptitude - or see if you can see what it needs from synaptic. But without knowing what you uninstalled it's a bit needle in a haystack.

---

### Post by leetrefz on 2008-08-04
turned out to be xorg-video-vesa or whatever. ok now

---

### Post by Elfy on 2008-08-04
Glad you got it sorted - I hadn't forgotten this thread - but couldn't help anymore lol

---

