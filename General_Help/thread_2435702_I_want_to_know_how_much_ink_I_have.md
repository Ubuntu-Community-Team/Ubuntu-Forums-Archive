---
title: "I want to know how much ink I have"
date: 2020-01-24
forum: General Help
---

### Post by logie on 2020-01-24
Since  I gave up Windows around 2005 I have missed only one thing.  I used to have a program that showed me how much ink was left in my printer cartridges.  Is there any way to check that with Ubuntu 18.04?

---

### Post by CatKiller on 2020-01-24
It depends on the printer. HP printers will show that information in HPLIP.

---

### Post by HermanAB on 2020-01-24
A real geek, would put a webcam on the printer...
;)

---

### Post by logie on 2020-01-24
> **CatKiller said:**
> It depends on the printer. HP printers will show that information in HPLIP.

Thanks. I have HP.  How do I do it? (Please excuse ignorance!)

---

### Post by CatKiller on 2020-01-24
It's in the repositories; you'd install it the same as any other software. Then, when you run it, it has a tab called "Supplies" that shows ink levels. You can also do the normal print job stuff in an interface that you might think is prettier than the CUPS one.

---

### Post by coffeecat on 2020-01-24
Point of information: if you want a pretty GUI app, you would need the package hplip-gui. hplip provides all the backend stuff and is a dependency of hplip-gui, but it's the gui package that I think the OP would want. 

I'm fairly sure that hplip comes as default in Ubuntu, but that you need to install hplip-gui if you want it. The module for monitoring ink levels (and other stuff) is called HP Toolbox.

---

### Post by CelticWarrior on 2020-01-24
> **coffeecat said:**
> Point of information: if you want a pretty GUI app, you would need the package hplip-gui. 

+1

Last time I use a HP printer was some years ago. I vaguely remember search for and installing it with the software center.

But now (19.10) there's only 'hplip-printer-application' (snap) and an alternative menu as a Gnome extension.

---

### Post by kurt18947 on 2020-01-24
I installed refillable cartridges in my inkjet printer. They're translucent so I can see at a glimpse. They also hold a lot more ink than 'normal' cartridges - no sponges - so i don't have to refill them very often. I'm lucky that my printer is old enough to not have chipped ink cartridges which makes things simpler.

---

### Post by logie on 2020-01-30
> **kurt18947 said:**
> I installed refillable cartridges in my inkjet printer. They're translucent so I can see at a glimpse. They also hold a lot more ink than 'normal' cartridges - no sponges - so i don't have to refill them very often. I'm lucky that my printer is old enough to not have chipped ink cartridges which makes things simpler.

I would like to do the same.  How do I go about it?      LOGIE

---

### Post by ajgreeny on 2020-01-30
> **logie said:**
> I would like to do the same.  How do I go about it?      LOGIE

Just do a web search for ***compatible cartridges "printer-make/model"***  You will probably get many links to look at and research a bit further.  I have been using compatible cartridges for many years here in the UK with no problems, but I suggest you look for reviews of the cartridges before purchase.

---

### Post by CelticWarrior on 2020-01-30
> **ajgreeny said:**
> Just do a web search for ***compatible cartridges "printer-make/model"***  You will probably get many links to look at and research a bit further.  I have been using compatible cartridges for many years here in the UK with no problems, but I suggest you look for reviews of the cartridges before purchase.

+1

But also check, if applicable, your warranty status and conditions.

In EU (including UK) we're safe, manufacturers can't void the warranty if the alternative cartridges are used as long as they're "fir to the purpose" but many manufacturers tried many times to pass such warranty terms in other regions of the world.

---

