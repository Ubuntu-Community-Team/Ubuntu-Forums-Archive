---
title: "Firefox - Switch Page Direction"
date: 2007-11-21
forum: General Help
---

### Post by kgw on 2007-11-21
When I right click in Firefox, there is a "Switch Page Direction" Option. This has to be the mostly useless option I have ever scene and quite troublesome.

If I am at the bottom of the page and right click, My pages reverses.
Is there a way to disable or completely remove it from the right click menu?

---

### Post by kgw on 2007-11-22
Sorry KGW, we have no clue as to why "Switch Page Direction" on Firefox would show up on a Linux/Ubuntu System and not needed on a windows system.

I know this doesn't help but *AT LEAST* you got an answer!

---

### Post by TrOjAnUK on 2007-11-22
Its for left handed people or people that prefer the scroll bar on the left..

TrOjAn

---

### Post by kgw on 2007-11-22
Well it moves WAY more than just the scroll bar. It messes up web page looks to. Espiciallyanything that has to do with CMS'S an blocks

---

### Post by kgw on 2007-11-25
Seems ubuntu installed UBUFOX extension. Upon disabling this I managed to kill it!

---

### Post by ekravche on 2007-11-25
I think it's there in order to support languages that are written from right to left?

---

### Post by bowmanjj on 2007-12-01
> **kgw said:**
> When I right click in Firefox, there is a "Switch Page Direction" Option. This has to be the mostly useless option I have ever scene and quite troublesome.

If I am at the bottom of the page and right click, My pages reverses.
Is there a way to disable or completely remove it from the right click menu?

Yeah, it looks useless at first, but ekravche has it right:

> **ekravche said:**
> I think it's there in order to support languages that are written from right to left?

It seems Ubuntu goes a bit overboard in its internationalization and enables support for R-to-L languages whether you want it or not.  I found a [page about Firefox configuration](http://kb.mozillazine.org/About:config_entries) that helped me disable this.  The relevant section is Bidi.*, which deals with bidirectional text.

I was able to disable the "switch page direction" menu entry by doing the following:

1) Type "about:config" into the address bar.
2) In the "Filter:" text box, type "bidi"
3) The "bidi.browser.ui" entry was set to "true" in the "value" column.  To change it to "false", right-click on this entry and select "Toggle".
4) Restart Firefox.

After doing all this, the "Switch page direction" context-menu entry disappeared.  Hope this helps.

---

