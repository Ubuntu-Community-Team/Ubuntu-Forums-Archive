---
title: "Limiting the sensitivity of the double click (a required time between double clicks)"
date: 2014-02-06
forum: General Help
---

### Post by cgshirley on 2014-02-06
Hello!

I have a mouse that on occasion it double clicks when I single click.  This is annoying when I place an order for something and I get 2 of them because the computer registered a single click as a double click (just happened with a google express order, ugh, actually not the end of the world to double my smoked oyster and herring purchasing, but none the less want it to be intentional).

So I've been looking into dconfig to see if I can set a required duration between clicks to register it as a double click, and have found none.  Don't confuse this question with speed of double click timing, but rather that I'm trying to eliminate these spontaneous double clicks, so I'm looking to adjust it to require more time between double clicks.  This might end up looking like, if a rapid double click occurs, register it as a single click.

Any suggestions would be great!

---

### Post by varunendra on 2014-02-07
Hello cgshirley !

I don't know if what you want is possible or not (all the options I know of facilitate 'Faster Tapping', not 'Ignoring' it), but the problem you described is a physical wear & tear problem of mouse or any kind of switch with physical contacts.

The common fix is to simply replace the mouse with a better quality one that lasts longer.

Otherwise, if you can do a little geeky housekeeping work, fixing the current mouse will take a small screw-driver, a needle, tweezers and a pointed knife. Open up the mouse > Open up the tiny switch (carefully) > clean all the carbon from the brass plate and all the contact pins/holding-slots. I keep doing that and is fun. :)

---

### Post by The Cog on 2014-02-07
The process of treating a very rapid series of changes as a single change is known as de-bouncing. It is often needed on electronics behind mechanical switches when the contacts can literally bounce for a short while as they come together. I've also been looking for a setting for the de-bounce time as my mouse is starting to do the same thing. Can't find any such setting. 

Maybe it's assumed that the de-bouncing is built into the mouse, which is probably the most senible place to do it, and as such the computer need not ever have to try to do it. So I suspect that there is no such timer in the computer, nothing to adjust.

---

### Post by Keith_Beef on 2014-02-07
> **cgshirley said:**
> Hello!

I have a mouse that on occasion it double clicks when I single click.  This is annoying when I place an order for something and I get 2 of them because the computer registered a single click as a double click (just happened with a google express order, ugh, actually not the end of the world to double my smoked oyster and herring purchasing, but none the less want it to be intentional).

Hmm! Smoked oysters! Yummy.

> **cgshirley said:**
> So I've been looking into dconfig to see if I can set a required duration between clicks to register it as a double click, and have found none.  Don't confuse this question with speed of double click timing, but rather that I'm trying to eliminate these spontaneous double clicks, so I'm looking to adjust it to require more time between double clicks.  This might end up looking like, if a rapid double click occurs, register it as a single click.

Any suggestions would be great!

Open the Dash home, type "System" and then select "System Settings".

In the dialog that appears, select "Mouse and Touchpad".

For me, the last parameter is called "Double-Click Timeout". This sets the **maximum** time allowed between two mouse clicks in order to register as a double-click. But you need to increase the **minimum** time allowed…   

I had a look in Gnome-conf Editor to see what was being changed by the slider in the "Mouse and Touchpad" dialog: it's the [FONT=Fixedsys]/desktop/gnome/peripherals/mouse/double_click[/FONT] key. I can't see any key that would have the effect you're looking for, so I think that the only solution is to repair your mouse or buy a new one (try not to buy two of them).

---

### Post by Keith_Beef on 2014-02-07
> **The Cog said:**
> The process of treating a very rapid series of changes as a single change is known as de-bouncing. It is often needed on electronics behind mechanical switches when the contacts can literally bounce for a short while as they come together. I've also been looking for a setting for the de-bounce time as my mouse is starting to do the same thing. Can't find any such setting. 

Maybe it's assumed that the de-bouncing is built into the mouse, which is probably the most senible place to do it, and as such the computer need not ever have to try to do it. So I suspect that there is no such timer in the computer, nothing to adjust.

There are de-bounce settings for the keyboard in Gnome-conf editor , but not for the mouse.

I couldn't se a good reason for assuming that a mouse should take care of bounce (therefore not handle it in the computer), but a keyboard should not (therefore handle it in the computer).

However, I found a few keys that handle bounce in the accesibility sections.
[LIST]
[*]/desktop/gnome/accessibility/keyboard/bouncekeys_delay
[*]/desktop/gnome/accessibility/keyboard/bouncekeys_enable
[*]/desktop/gnome/accessibility/keyboard/bouncekeys_beep_reject
[*]/schemas/desktop/gnome/accessibility/keyboard/bouncekeys_beep_reject
[*]/schemas/desktop/gnome/accessibility/keyboard/bouncekeys_delay
[*]/schemas/desktop/gnome/accessibility/keyboard/bouncekeys_enable
[/LIST]

So it looks like the Gnome team has anticipated "shaky hands" being a possible cause of unintended double keypresses, but has not forseen that the same problem could cause unintended double mouse clicks.

Maybe this could be put as a request to the developers…

---

