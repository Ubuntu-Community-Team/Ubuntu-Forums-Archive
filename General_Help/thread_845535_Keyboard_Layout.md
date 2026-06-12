---
title: "Keyboard Layout"
date: 2008-06-30
forum: General Help
---

### Post by connord94 on 2008-06-30
Changing Key Layout.

So, firstly I'd like to point out that I'm new to linux, and learning as I go, the 1 key on my laptop is awkward and not actually a physical key anymore, so I'd like to change the keyboard layout so my  `¬| key does a 1, 

My (failed) attempt :

In Terminal

Sudo -i
<My Root Password>
cd /usr/share/X11/xkb/symbols/
cp gb gb.old                         (gb is my keyboard layout)
gedit gb 

...
I then added the following line :
```

 key <TLDE> { [          1,  exclam                                  ] };
```
Then saved and exited.

Which should edit the <TLDE> key to do a one, as far as I know, but it just doesn't work, I've change my keyboard layout away from GB, then back to GB, in order to refresh it, but still no luck.

Any ideas on how I can do it?

Thanks in advance.
Connor

---

### Post by connord94 on 2008-07-02
I myself, hate bumping threads - but I'd rather bump than start a new thread.


Connor

---

