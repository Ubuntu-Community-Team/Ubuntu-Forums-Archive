---
title: "Synaptic Package Manger problems"
date: 2008-01-05
forum: General Help
---

### Post by souperdoo on 2008-01-05
OK, I know this has to be basic and I just don't get something.

I have Gutsy Gibbon installed.

When using Synaptic Package Manger, I select what I want to install, mark it, tell it to go ahead and install it. Synaptic shows it installed, but I can't find it in the menu anywhere.

I tried using the "Add/Remove" to find it, but no joy.

What the heck am I doing wrong?

Thanks,

Tom

---

### Post by taurus on 2008-01-05
What is the name of the app?  Not all programs have icons in the menu.

---

### Post by EYEdROP on 2008-01-05
> **taurus said:**
> What is the name of the app?  Not all programs have icons in the menu.

Which is kinda stupid IMO. Yeah, not all apps should be there, since *nix consists of many small programs. But the ones users installed should be in the list, even if its a terminal app.

---

### Post by souperdoo on 2008-01-06
> **taurus said:**
> What is the name of the app?  Not all programs have icons in the menu.

The app is "gpsman", which is a GPS (Global Positioning) manager. I was hoping to be able to get my ancient Garmin emap working.

Thanks,

Tom

---

### Post by erfahren on 2008-01-06
sometimes you just have to make your own entry - through the menu editor (alacarte) 

to get the command type in the name of it ("gpsman") to see if that launches it.

If it doesn't go back to Synaptic and to its Preferences and enable "Show pacakage properties in main window")

then under the "Installed files") tab in the package description window see if you can see the name of the excutable it put into /usr/bin (or whatever/bin ) and you should be able to launch it with that.

---

### Post by erfahren on 2008-01-06
> **EYEdROP said:**
> Which is kinda stupid IMO. Yeah, not all apps should be there, since *nix consists of many small programs. But the ones users installed should be in the list, even if its a terminal app.
it depends on the package and on *how* it was packaged. 

it really isn't that difficult to create entries once you know how, and since you can use .PNGs for icons it's not hard to find or create a suitable icon for it.

The Xfce4 menu (like in Xubuntu) is much more of a pain to deal with!

---

### Post by erfahren on 2008-01-06
oh, I forgot...
sometimes you just have to do "killall gnome-panel" and that will cause the panel to restart, refreshing the menu and the menu entry will appear

---

### Post by souperdoo on 2008-01-06
OK, I'll play with that, though I don't know about "alacarte".

It would be nice if they would add a smilie that was kinda like "Whoosh! That went right over my head!"

<pause>

I went to usr/bin and found "gpsman". it was labeled as "linked to a shell script". When I doubled clicked it, it launched.

I ought to be able to figure out a way to get it into a menu somewhere.

Thanks for your help!

Tom

---

### Post by erfahren on 2008-01-06
> **souperdoo said:**
> OK, I'll play with that, though I don't know about "alacarte".

It would be nice if they would add a smilie that was kinda like "Whoosh! That went right over my head!"

<pause>

I went to usr/bin and found "gpsman". it was labeled as "linked to a shell script". When I doubled clicked it, it launched.

I ought to be able to figure out a way to get it into a menu somewhere.

sorry, the actual name of the menu editor itself is called "alacarte" (you can type that to launch it).

(I knew of this tip - but had to go find it - I guess I should bookmark it)
[HOWTO: Add entries in your GNOME Menu](http://ubuntuforums.org/showthread.php?t=533265)

---

### Post by souperdoo on 2008-01-06
Ah! Thanks for that link - it shows me how to do what I gotta do.

I've book marked it.

Thanks again,

Tom

---

