---
title: "How to set a custom formula calc script ?"
date: 2018-12-30
forum: General Help
---

### Post by dino99 on 2018-12-30
I am using Calc 6.0 with a gnome-shell session on 18.10

With a spreadsheet, i would like to ease the reading of complex and long formulas:
By default, inside the formula bar, all of the commands, cells reference, commas, brackets, are written with the font/size/black color.
I would like to set a custom format with : be able to tweak font/size used, custom colors to differentiate command/cell/bracket.

I've found an extension: [https://extensions.libreoffice.org/extensions/formatting-of-all-math-formulas](https://extensions.libreoffice.org/extensions/formatting-of-all-math-formulas) (aka FAF) that should do some changes.
But after installing that extension and restarted calc, the addon is listed and its dialog display as expected; selecting a cell with a formula, and testing a change via FAF ends up to a "Property or method not found" about getviewcursor (basic runtime error).
Digging the net does not resolve that issue. I have no idea about the package that is required to satisfy that extension; maybe some of you could suggest some usefull ideas. :P

Hope to see such features built inside Libreoffice.

---

### Post by Holger_Gehrke on 2018-12-30
That extension is meant for LO Math formulas, the kind you can put into LO with Insert->Object->Formula, not for Calc computations. It does work, at least on my machine (LO 6.0.7.3, XUbuntu 18.04), but it's not what you want. What you're looking for would be syntax highlighting for LO Calc formulas during entry. The only workaround for this missing capability in LO I've found while searching was the suggestion to create highlighting rules for your favourite editor and copy and paste the formulas back and forth between editor and Calc.

Holger

---

### Post by dino99 on 2018-12-30
Thanks Holger
that confirm my failing search sadly.

Get a happy new year ):P

---

