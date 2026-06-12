---
title: "Kubuntu Compiz Desktop Effects"
date: 2008-06-01
forum: General Help
---

### Post by Vietzomb on 2008-06-01
Hey all! i just installed Kubuntu 8.04 Hardy Heron and went to the compiz desktop effects but it told me that i could not use until i install it. So i hit the install button but i keep getting a message stating the package compiz-kde could not be found. I am new to linux but would LOVE to have compiz running. Can someone please help me out. thanks

---

### Post by Forlong on 2008-06-02
Sounds like you don't have the **universe** repository enabled.
Go to *System &#8594; Administration &#8594; Software Sources* and make sure it's checked.

edit: ah, silly me... you're on KDE. Show us your **/etc/apt/sources.list** then -- and use the forum's [noparse][CODE][/noparse] tag please (# button)

---

### Post by Zorael on 2008-06-02
Or open up Adept Manager, then Adept -> Manage Repositories -> tag Community-maintained Open Source software (universe). And any others you might like while you're at it.

The packages you want are **compiz**, **compiz-kde** and **compizconfig-settings-manager**. Also, get rid of **compiz-gnome**. Just installing **compiz-kde** won't get you Compiz Fusion plugins, though if that's what you want, go ahead.

Terminal way:
```
$ sudo aptitude install compiz compiz-kde compiz-gnome_
```

---

