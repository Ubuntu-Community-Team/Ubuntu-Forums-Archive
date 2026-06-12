---
title: "Keyboard Layouts allow no options"
date: 2007-05-08
forum: General Help
---

### Post by raggacore on 2007-05-08
First, I apologize for any bad spelling I may subject you to, but I generally type on a dvorak keyboard. Earlier today I booted my feisty box up, and, out of nowhere, I can't set the layout to dvorak anymore.

The login screen allows me to type in dvorak and xorg is still configured properly. I don't know what is going on, if it is an xkb or gnome thing, nut not being able to type is making this incredibly frustrating to figure out. 

The Layouts tab of "keyboard preferences" allows me to select ONLY 'Generic Keyboard' for the model (just found out the computer is treating caps lock as nothing more than a shift key, I had to hold it down for that entire word). When I try to change the layout, I get a list of different stuff, but it looks different from the list I started out with. There are very few layout choices, and dvorak is not one of them. I also seem to recall that the options were grouped by language previously, now they are not. There is no dvorak option, and thus I can't even really work effectively at fixing this. Is some library magically missing or something... this makes no sense. (On a side note, I let my girlfriend use this computer for the first time today... maybe there is something simple that she accidentally did that can fix this and I am just unaware of. That would really be nice.)

Does anyone know what the issue is? Please help.

---

### Post by Simon Bridge on 2007-05-08
> **raggacore said:**
> First, I apologize for any bad spelling I may subject you to, but I generally type on a dvorak keyboard. Earlier today I booted my feisty box up, and, out of nowhere, I can't set the layout to dvorak anymore.

[snip]

Does anyone know what the issue is? Please help.
Sounds bad - which keyboard is this?

I am using dvorak in fiesty right now.
Not many locales had the dvorak option.
I am using us layout, which shows options for classic as well as modern dvorak

---

### Post by raggacore on 2007-05-08
That's the thing, I don't even have the option to set up the locale anymore. It's just like all the options to configure the keyboard disappeared. It was set up as US dvorak 3 days ago when I installed feisty and was working fine up until yesterday... but now that isn't even an option. 

What "available layouts" the computer still recognizes:

US 101'key keyboard
US 105-key keyboard
etc. (none of which are grouped by locale as I think they were previously)

Also, if this helps anyone figure out what is going on, under "layout options," I forgot how many options htere used to be, but currently I only get "Layout shift behavior." 

Just to reiterate, xorg.conf is absolutely fine.

Since I just upgraded... maybe it's worth a fresh install just to save time and effort.

---

### Post by Simon Bridge on 2007-05-08
> **raggacore said:**
> That's the thing, I don't even have the option to set up the locale anymore. It's just like all the options to configure the keyboard disappeared. It was set up as US dvorak 3 days ago when I installed feisty and was working fine up until yesterday... but now that isn't even an option. 

What "available layouts" the computer still recognizes:

US 101'key keyboard
US 105-key keyboard
etc. (none of which are grouped by locale as I think they were previously)

Also, if this helps anyone figure out what is going on, under "layout options," I forgot how many options htere used to be, but currently I only get "Layout shift behavior." 

Just to reiterate, xorg.conf is absolutely fine.

Since I just upgraded... maybe it's worth a fresh install just to save time and effort.

dpkg-reconfigure xserver-xorg

---

