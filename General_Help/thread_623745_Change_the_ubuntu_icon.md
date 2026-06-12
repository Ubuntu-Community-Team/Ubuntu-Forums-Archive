---
title: "Change the ubuntu icon"
date: 2007-11-26
forum: General Help
---

### Post by hraposo on 2007-11-26
How I change the icon of gnome-satat-menu?
I want change the ubuntu icon for another.
How I change this???

This link shows what I mean

[http://hldraposo.no-ip.org/Semtítulo2.png]("http://hldraposo.no-ip.org/Semtítulo2.png")

---

### Post by WinterWeaver on 2007-11-26
?? what link?

---

### Post by hraposo on 2007-11-26
The link is there now!

---

### Post by WinterWeaver on 2007-11-26
unfortunately, I'm at work, and I'm unable to view that link (prob due to firewalls and stuff).

However, I believe I know what you want to change.

I can guide you halfway there, but I'm not completely sure where to do this.
first you have to open the gconf-editor

hit Alt+F2 and type the following:
```
gconf-editor
```

when this opens, navigate down the tree as follows:
```
apps >> panel >> objects
```

Once there, you have to try find the object for your main menu, and set the Custom Icon Property.

---

### Post by WinterWeaver on 2007-11-26
Yup... it works :) ... I just changed the icon here at work ^_^

---

