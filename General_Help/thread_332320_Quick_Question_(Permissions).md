---
title: "Quick Question (Permissions)"
date: 2007-01-05
forum: General Help
---

### Post by raveneffct on 2007-01-05
I have a question, I am trying to add a font. But my font folder wont allow me to add anything because I am not root. How can I add a font to ubuntu. Thanks:)

---

### Post by Cholito on 2007-01-05
```
sudo cp
```

---

### Post by raveneffct on 2007-01-05
Not very helpful....  directions please.

by the way the location of my font folder is usr/share/fonts

---

### Post by raveneffct on 2007-01-05
Anyone?](*,)

---

### Post by FryerFox on 2007-01-05
You use sudo to do something as root, which gives you the highest permissions, so as the previous poster alluded to:

> sudo cp filename /usr/share/fonts

or you could hit ALT-F2 and type:

> sudo nautilus

(I assume you are using Gnome, not KDE)
Then use CTRL-L to get to the location bar and type:

> /usr/share/fonts

Now, you can copy things into your fonts folder by dragging them to the root-user-nautilus.

BTW, Nautilus is the Gnome equivalent of Windows Explorer (just in case you didn't know).

---

