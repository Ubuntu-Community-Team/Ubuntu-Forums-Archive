---
title: "Menu icons disappeared in OpenOffice"
date: 2007-06-07
forum: General Help
---

### Post by devilears on 2007-06-07
When I opened OpenOffice Word Processor today (after not having opened it for a while), I realized that all the "menu icons", eg New, Copy, Paste, Print have disappeared! All I have left are the Text items. Can anyone help with this. I'm running kubuntu 7.04 (fully updated) and OpenOffice.org 2.2.0. Thanks.

---

### Post by steeleyuk on 2007-06-07
You haven't changed you icon set or theme have you since you last opened it? I changed my icons the other day and OOo decided to only display icons in text... until I reverted back or changed to a different set again.

Alternatively the setting could have been changed. To check it go to:

Tools > Options > View > Show icons in menus

---

### Post by devilears on 2007-06-07
Nope, it's not that, I checked. See screenshot attached:

---

### Post by steeleyuk on 2007-06-07
Thats definitely the same problem I had. This should fix it.

Tools > Options > View

You need to select an icon theme that OOo supports, Human is the default...

PS. If that doesnt work I don't know the problem.
PPS. The problem happens when the icon theme doesnt have the necessary icons for OOo (as far as I know)

---

### Post by devilears on 2007-06-07
you might be right, because i cannot select ANY theme, as there seems to be no themes available when i calick the down-arrow....

---

### Post by julianmag on 2008-04-03
I had the same problem.
You can fix it by selectin Tools -> Options, and then View. And then select an Icon set that you have installed.

In my case I've Crystal. You can download Crystal Icon set with apt-get using:

sudo apt-get install openoffice.org-style-crystal

Good luck.

WebLatam
[http://weblatam.com]("http://weblatam.com")

---

