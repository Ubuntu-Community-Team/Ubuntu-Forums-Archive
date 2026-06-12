---
title: "Where are the icons stored that are used on panel window list?"
date: 2008-06-27
forum: General Help
---

### Post by dwasifar on 2008-06-27
When I change the icon set in Appearance, the application icons change in the menus, on the desktop, and in AWN, but not in the panel window list items or on the title bar.  

So for example, if I load the Oxygen icon set, the menus and AWN show this icon for Firefox:

[IMG]http://www.dwasifar.com/icon2.jpg[/IMG]

But I still see this icon in the panel:

[IMG]http://www.dwasifar.com/icon1.jpg[/IMG]

If I knew where the panel and title bar icons were coming from, maybe I could sync these up so I see the Oxygen icon in the panel and in the window title bar...?

---

### Post by rubicon on 2008-06-27
Usually in /usr/share/icons/

Packaged icons would be in /usr/lib/appname/... for example /usr/lib/firefox-3.0/icons/mozicon128.png

---

### Post by chmacka on 2009-05-31
I found some icons in /usr/share/pixmaps.

---

### Post by UKBB on 2009-06-10
> **chmacka said:**
> I found some icons in /usr/share/pixmaps.

Thanks! That got it.

---

