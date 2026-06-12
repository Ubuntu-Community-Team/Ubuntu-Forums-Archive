---
title: "Captain, this is illogical!"
date: 2006-11-06
forum: General Help
---

### Post by unbreakable on 2006-11-06
Hello, newbie here asking a simple and logical question...

I have downloaded the DVD edition of kubuntu 6.10
and installed it... I was expecting more applications to be installed with the dvd edition... but it was the same thing as with the cd edition....

reading about this, some said that the dvd should have been added automatically in the repository list.. so that you could install from the dvd... well guys its not there.. I see only sites and ftp stuff... 

So how do I add it??? And it you tell me how, how then can I see whats available on the dvd only?

Thanks

---

### Post by taurus on 2006-11-06
If you want to add CD/DVD to your repos list, open a terminal and type

```
sudo apt-cdrom add
sudo aptitude update
```
Now, install it away.  If it can't find the program on your DVD, it will try the net.

---

### Post by Sethro on 2006-11-06
funny title man

---

### Post by Mr. Picklesworth on 2006-11-09
Should be possible to insert the DVD and have Gnome detect it as a software source and offer to open Synaptic. That happened for me a while ago with Dapper, anyway. It was very exciting :)

---

