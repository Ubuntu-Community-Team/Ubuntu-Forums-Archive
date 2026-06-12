---
title: "Change decoration of windows"
date: 2008-06-29
forum: General Help
---

### Post by koper1805 on 2008-06-29
Hi all,
I'm new in this Forum so please excuse me if I did something wrong :/
In addition to this I'm German not English so I hope you can understand my bad english...

I want to change the look of my windows decoration so that the Closebutton is in the left corner not in the right (as it usual is). I'm using:
Ubuntu 8.04
Gnome 2.22.2
And I think there is Compiz installed..

Ok, hope I didn't forget to give you any information..

Regards,
Christoph

---

### Post by Forlong on 2008-06-29
Go to [http://gnome-look.org](http://gnome-look.org) and look for (Metacity) themes, that have this setup.

Additionally, if you (want to) use [Emerald]("apt://emerald"), you will be able to configure this yourself via Emerald Theme Manager.

Viel Spaß. :)


edit:
Actually, this seems to be configurable with Metacity themes as well.
Run ```
gconf-editor
```
There's a key called **button_layout** under /apps/metacity/general/ that seems to be there to set just that.

---

### Post by koper1805 on 2008-06-29
Thanks that did it :)

Regards,
Christoph

---

