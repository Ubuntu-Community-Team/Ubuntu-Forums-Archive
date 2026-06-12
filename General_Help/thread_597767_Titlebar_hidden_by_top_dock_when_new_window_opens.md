---
title: "Titlebar hidden by top dock when new window opens"
date: 2007-10-30
forum: General Help
---

### Post by gazotem on 2007-10-30
Im not having trouble with the issue where beryl/compiz fusion window borders / decorations arent working, but when I open a new window the title bar is behind the top dock so that I must drag each window down about 25 pixels in order to access the title bar buttons (minimize, maximize, close).  It is an annoyance.  I just installed Avant Window Manager, could this be an issue related to that?  Let me know if you need any more info.

---

### Post by aidanr on 2007-10-30
It's probably the focus stealing prevention option, in compiz config settings manager it's:
General -> Focus & Raise Behaviour -> Focis Prevention Windows -> none
In beryl it's similarly titled in the general options, just set it to "none".

Also in the place plugin you can set the placement mode to "centered", that'll help for anything that doesn't open maximized if my first suggestion doesn't work.

---

### Post by gazotem on 2007-10-30
Made the change, but no luck.  Attached is an screen of what i'm talking about.

I'm going to disable compiz-fusion and test it out.

> **aidanr said:**
> It's probably the focus stealing prevention option, in compiz config settings manager it's:
General -> Focus & Raise Behaviour -> Focis Prevention Windows -> none
In beryl it's similarly titled in the general options, just set it to "none".

Also in the place plugin you can set the placement mode to "centered", that'll help for anything that doesn't open maximized if my first suggestion doesn't work.

---

### Post by gazotem on 2007-10-30
Alright fixed it up, went into the compizConfig manager, and enabled Place Windows option with the placement mode of Smart.

Thanks.

> **gazotem said:**
> Made the change, but no luck.  Attached is an screen of what i'm talking about.

I'm going to disable compiz-fusion and test it out.

---

