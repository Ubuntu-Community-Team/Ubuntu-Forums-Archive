---
title: "Online Videos not working"
date: 2008-07-08
forum: General Help
---

### Post by Micronic on 2008-07-08
Youtube, Ubuntube, and other video sites are not working..

[www.cioko.com/Screenshot.png](www.cioko.com/Screenshot.png)
[www.cioko.com/Screenshot-1.png](www.cioko.com/Screenshot-1.png)

I don't know what is wrong.. any ideas?

---

### Post by nikgare on 2008-07-08
Do you have the Flash plugin installed?
You can go to synaptic and look for **flashplugin-nonfree**

---

### Post by Micronic on 2008-07-08
yes i just reinstalled it and nothing :(

[www.cioko.com/Screenshot-2.png](www.cioko.com/Screenshot-2.png)
plugins

---

### Post by nikgare on 2008-07-09
not that one, the other one!
ie: you have Gnash flash player installed, not the "real" adobe flash player.
Remove Gnash flash player(the one you have installed now) and install Shockwave Flash 9.0 r124 (the one underneath Gnash)

---

### Post by Tomatz on 2008-07-09
Try this:

**Close firefox**

Then open a terminal and type:

```
sudo apt-get remove --purge gnash* 
```

Then 

```
sudo apt-get install flashplugin-nonfree
```


Now try ;)

---

### Post by Micronic on 2008-07-10
yes!!!! thank you!

---

