---
title: "Resizing/presizing nautilus excuted through SSH."
date: 2014-04-17
forum: General Help
---

### Post by zemega on 2014-04-17
Hi.

Usually when you use ssh, you dont usually open nautilus. I know this. But I just want to know this. When you run nautilus in shh, it will create an X windows of nautilus on the entire screen. How can I run nautilus through ssh and resize the nautilus or the X window so that it doesnt create a X windows on the whole screen. I just want a rectangular smaller X window of nautilus.

---

### Post by HermanAB on 2014-04-17
Experiment with the -g parameter.

$ man nautilus

---

### Post by zemega on 2014-04-17
No, the g parameter is not what I want, it open up a nautilus inside a x-nautilus-desktop. What I want is to resize the x-nautilus-desktop part, or start it at a smaller size.

---

### Post by steeldriver on 2014-04-17
Try

```

nautilus **--no-desktop**

```

---

### Post by zemega on 2014-04-17
Well, that removes the whole desktop and only launch nautilus folder, but I don't want that. I like the nautilus with desktop, but not the size of it.

---

