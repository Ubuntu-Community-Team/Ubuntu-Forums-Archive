---
title: "do i really need evolution on my system?"
date: 2017-06-08
forum: General Help
---

### Post by wyndlass on 2017-06-08
do i really need evolution on my system? i don't use it for anything(that i know of) and have been wanting to remove it. is evolution needed by the system for anything or is it safe to remove? i'm running xenial on a hp pavilion g7 6gb ram 650 gb hdd i3 dual core. thanx

---

### Post by deadflowr on 2017-06-08
What are you running? Ubuntu flavor-wise.

Ubuntu, itself, does not, currently, come with evolution.
However, Ubuntu does comes with the package evolution-data-server
It uses that package for the calendar in the panel.
So removing that will probably break the calendar.

But if you have just evolution for some reason, I see no reason as to why removing it should break anything.

---

### Post by &amp;KyT$0P# on 2017-06-08
If you use Synaptic package manager, it should tell you what else will be removed when you mark evolution for removal.

Otherwise, you can simulate removing evolution using this terminal command -
```
apt-get -s purge evolution
```
This won't actually change anything, but it will tell you what would happen if you were to remove evolution.

---

### Post by JonPaul on 2017-06-08
I did the following having found it on another forum.
sudo mv /usr/lib/evolution /usr/lib/evolution.bk
i use gnome and trying to 'apt remove/purge' wants to take out tons of stuff.
I have not noticed any problems resulting from this.
I don't use evolution or gnome calendar.

Cheers

---

### Post by wyndlass on 2017-06-11
i'm running regular ubuntu 16.04 lts. i do sometimes look at the calendar but i can get the gnome one. thanx.

---

