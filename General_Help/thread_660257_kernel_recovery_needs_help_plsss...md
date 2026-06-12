---
title: "kernel recovery needs help plsss.."
date: 2008-01-06
forum: General Help
---

### Post by halln on 2008-01-06
how can i move back to my previous kernel. My system is a bit unstable with the new latest kernel. Previously I'm using the latest 7.04 kernel and it seems my computer is happy using it on gutsy 7.10. I tried to upgrade totally to 7.10 with the latest kernel and thats the time I get in trouble, the system clock seems to be very fast than normal, effects, video etc.. Pls help

---

### Post by zvacet on 2008-01-06
When you start your comp you will see grub,and there you can choose wich kernel you want to use.Pick one you think it is better for you.

---

### Post by halln on 2008-01-06
> **zvacet said:**
> When you start your comp you will see grub,and there you can choose wich kernel you want to use.Pick one you think it is better for you.

I,m a newbie, I tried to do that but After logging in it wont give the normal display just that text thing.

---

### Post by zvacet on 2008-01-07
That text thing is your grub and top kernel number is new one and it has recovery mode(line below).Select one that comes after that and hit Enter.

---

### Post by halln on 2008-01-07
I did that already but after logging in and loads I end up with my root command line and I dont what code I have to write to show my display (wallpaper with icons stage).

---

### Post by danwood76 on 2008-01-07
It sounds like you are selecting the recovery mode option, that will give you the terminal you describe.

Choose one of the options without recovery mode that is below your current kernel.
It should load as before as when you upgrade it doesnt destroy the old kernel or modules so you can go back.

---

### Post by halln on 2008-01-07
Thanx for your reply. I'm using the generic main one not the recovery mode kernel. What it did is, it loadsand ask you of your username and password and it loads again and end up with your root command. All these in text mode not the usual splash display thing.

---

### Post by danwood76 on 2008-01-07
try running startx to load the xserver.
seems strange that it doesnt load x straight off and also leaves you with a root login.

---

