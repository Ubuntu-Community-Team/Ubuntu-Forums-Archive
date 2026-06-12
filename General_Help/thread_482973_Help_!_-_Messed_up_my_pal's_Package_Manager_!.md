---
title: "Help ! - Messed up my pal's Package Manager !"
date: 2007-06-24
forum: General Help
---

### Post by paddyboy on 2007-06-24
I've been using Ubuntu Feisty for a few months now and loving it. When a friend asked me for a way to escape from Windows I was only too keen to help and turned him on to Linux. 
I helped him install / partition etc and all was good. 
He wanted to run some windows games etc, so I suggested WINE. I could'nt  see it in his Synaptic package manager (?)so we googled it and found the WINEHQ website with instructions for installing it. I did the following :

wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -
then:
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list](http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/winehq.list

Now Synaptic did see it, so we downloaded. Its says it did it and installed it etc but it did not appear on the menu's and a search showed nothing. Curiously the version it said it downloaded was 0.9.39 but my system shows 0.9.33 as the latest. 

How do I get him back to a clean/base  Package management condition. Does it mean pasting in a new /etc/apt/source.list ? Was I very foolish to run those commands above ?

Any help would be VERY much appreciated. Thanks.

---

### Post by Ziox on 2007-06-24
Wine should be in the standard Ubuntu repositories, you just have to enable all of the multiverse and universe.

---

### Post by paddyboy on 2007-06-24
Thanks Ziox, If I just remove whatever version it copied down will those commands I issued have any lasting effect ?

---

### Post by Ziox on 2007-06-24
there shouldn't be any issue.  But to be sure, you should remove or comment out the Wine repository in the source file:

/etc/apt/sources.list.

---

### Post by paddyboy on 2007-06-24
Great. Will do. Many thanks.

---

