---
title: "Fluxbox Help Needed"
date: 2006-12-23
forum: General Help
---

### Post by playmobiel on 2006-12-23
Hi , i recently installed fluxbox. Please look at the attacment, i wan't to know how to remove these ugly things. I've seen screenshots without them , so i know its possible :)

Thanks

---

### Post by lucia_engel on 2006-12-23
I just installed fluxbox as well and still learning. Those 'ugly' things are call tabs and allows you to group your windows together (like a web browser).
[Fluxbox Feature: Tabs]("http://fluxbox.sourceforge.net/features/tabs.php")

Here's the official guide on how to configure and turn off the tabs:
[http://fluxbox.sourceforge.net/docbook/en/html/x234.html]("http://fluxbox.sourceforge.net/docbook/en/html/x234.html")

```
sudo gedit ~/.fluxbox/init
```

Find the line
```
session.tabs:	true
```
and change it to
```
session.tabs:	false
```

---

### Post by kerry_s on 2006-12-23
Right click> configuration>tab options> tabs in title bar

You should learn to use the tabs it comes in very handy. Middle click a window  & drag & drop it on another window. see pic three in tab form->

---

