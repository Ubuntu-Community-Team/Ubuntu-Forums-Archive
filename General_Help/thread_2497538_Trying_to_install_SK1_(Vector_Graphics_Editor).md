---
title: "Trying to install SK1 (Vector Graphics Editor)"
date: 2024-05-09
forum: General Help
---

### Post by braznyc on 2024-05-09
When I try to install SK1 I get a dependency error. It says I need Python 2.7.
And that's an old version of Python.
Any suggestions?

---

### Post by dragonfly41 on 2024-05-09
Find an alternative.

[http://snapsvg.io/](http://snapsvg.io/)
BoxySVG
Inkscape
etc.

---

### Post by braznyc on 2024-05-09
I need SK1. It supports Xara files and I can use it to preview images in CMYK.

---

### Post by Holger_Gehrke on 2024-05-09
If you look at the github page of sk1, you'll find that there have been no contributions since the death of the primary author of the project of Covid-19 in 2021. There is a development branch named py3 in the github, but i don't think it ever got to the point where you could use it. My suggestion therefore would be to use something still in active development like Inkscape or the drawing component of Libre Office.

Holger

Edit: That's what I get for not refreshing the page after researching what's going on with sk1. One workaround I've found is to use the portable windows 32-bit version in wine; can't tell you whether it does everything you need, but it does start up and does offer xar-import. Alternatively you could try setting up an air-gapped machine or a VM running an older version of Ubuntu (18.04 ? 20.04 ?) and run the Linux version of sk1 on that.

---

### Post by braznyc on 2024-05-09
I hope the team can fix that issue.

---

### Post by braznyc on 2024-05-09
> **Holger_Gehrke said:**
> If you look at the github page of sk1, you'll find that there have been no contributions since the death of the primary author of the project of Covid-19 in 2021. There is a development branch named py3 in the github, but i don't think it ever got to the point where you could use it. My suggestion therefore would be to use something still in active development like Inkscape or the drawing component of Libre Office.

Holger

Edit: That's what I get for not refreshing the page after researching what's going on with sk1. One workaround I've found is to use the portable windows 32-bit version in wine; can't tell you whether it does everything you need, but it does start up and does offer xar-import. Alternatively you could try setting up an air-gapped machine or a VM running an older version of Ubuntu (18.04 ? 20.04 ?) and run the Linux version of sk1 on that.


[COLOR=#000000][INDENT]Thank you, my friend! That option to install the portable Windows version on Wine worked![/INDENT]


[/COLOR]
[COLOR=#000000][B][RIGHT][/RIGHT]
[/B][/COLOR]

---

