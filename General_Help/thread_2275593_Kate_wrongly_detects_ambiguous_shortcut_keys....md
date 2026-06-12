---
title: "Kate wrongly detects ambiguous shortcut keys..."
date: 2015-04-27
forum: General Help
---

### Post by timgood on 2015-04-27
Ctrl+A and Ctrl+C for example are both detected as ambiguous despite being set correctly as default and only options. 

[ATTACH=CONFIG]261606[/ATTACH]

Only problematic in Kate, keys work as expected in LibreOffice etc. This seems to be a repeat of an earlier bug (2010) but has resurfaced in 15.04 for some reason. Ideas?

---

### Post by wd5gnr2 on 2015-09-20
I know this is an old thread but since no one answered and it may come up in search.

[COLOR=#333333][FONT=sans-serif]Open up[/FONT][/COLOR]
[FONT=sans-serif]~/.config/kdeglobals[/FONT]
[COLOR=#333333][FONT=sans-serif]There may be lines where a command is given the same shortcut multiple times like[/FONT][/COLOR]
[FONT=sans-serif]Copy=Ctrl+C; Ctrl+Ins; Ctrl+C; Ctrl+Ins; Ctrl+C...[/FONT]
[COLOR=#333333][FONT=sans-serif]Fix those lines (there will be many of them).[/FONT][/COLOR]

---

