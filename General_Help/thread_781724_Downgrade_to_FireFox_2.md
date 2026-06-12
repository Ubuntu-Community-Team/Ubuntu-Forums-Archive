---
title: "Downgrade to FireFox 2"
date: 2008-05-04
forum: General Help
---

### Post by nami on 2008-05-04
I am trying to downgrade, but can't seem to get firefox to work properly after downgrading.  For example, after downgrading, I am unable to install any add-ons.

How to I remove FireFox 3 completely and get a fully working version of FireFox 2?

Please help.

---

### Post by aysiu on 2008-05-04
Can you explain what steps you took to downgrade?

---

### Post by nami on 2008-05-04
Yep,

Using synaptics, I unticked most stuff which said firefox, then ticked firefox 2.

thats it...

And it was the wrong thing to do, as I found out the hard way.

---

### Post by pressed on 2008-05-04
I hope you're not having to access the net through another computer?

try this:

sudo apt-get remove firefox-3.0
sudo apt-get install firefox-2

and if that doesn't work, and you're still stuck on another machine, you might want to install *opera* for now.

---

### Post by Zorael on 2008-05-04
I did this, basically equavilent of what pressed suggested.
```
$ sudo aptitude purge ~nfirefox-3.0 firefox-2+
```

---

### Post by nami on 2008-05-06
Thanks

All sorted.

---

