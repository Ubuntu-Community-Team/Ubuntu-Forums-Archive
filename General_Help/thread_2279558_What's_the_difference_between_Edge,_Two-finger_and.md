---
title: "What's the difference between Edge, Two-finger and Circular scrolling?"
date: 2015-05-24
forum: General Help
---

### Post by Rytron on 2015-05-24
Hi UF.

What's the difference between Edge, Two-finger and Circular scrolling?

Also, I just saw the option 'horizontal scrolling' in the MATE control panel. What's that?

Thanks.

---

### Post by mc4man on 2015-05-24
edge is  vertical scrolling, typically in far right side of touchpad
2 finger is vertical scrolling anywhere on touchpad with 2 finger contact
circular is scroll up with one circular dir., scroll down opposite circular dir.

horizontal is left <> right scroll when avail in window, typically very bottom of touchpad 1 finger or also in some setups can be set to 2 finger anywhere in tp

edit: while I generally just use a wireless mouse here scr. is my tp setup
(natural reverses the scroll up/down relative to dir. on tp

---

### Post by monkeybrain20122 on 2015-05-24
Why is that in settings I can only choose edge or two finger but Ubuntu actually supports both? I have to use a  startup script to have both working together.

---

### Post by mc4man on 2015-05-24
> **monkeybrain20122 said:**
> Why is that in settings I can only choose edge or two finger but my touchpad actually supports both? I have to use a  startup script to have both working together.
If I enable both in the tp indicator app then both work for vertical, 1 finger in edge area,  2 finger everywhere. Maybe in the system settings one only figures one or the other?

---

### Post by monkeybrain20122 on 2015-05-24
I run this script at start up and both work

```
synclient VertTwoFingerScroll=1
synclient HorizTwoFingerScroll=1
synclient EmulateTwoFingerMinW=5
synclient EmulateTwoFingerMinZ=48
```

Wonder why system settings only allow one.

---

### Post by mc4man on 2015-05-24
> **monkeybrain20122 said:**
> 

Wonder why system settings only allow one.
Could be the way the panel was designed, enabling one disables the other.
Ot, -  in my unity (14.04) install there is no edge choice, & in dconf-editor (org.gnome.settings-daemon.peripherals.touchpad ) the scroll-method only allows picking a string, not entering one or more.., so at least in Gnome they decided,  'pick one or the other'

---

### Post by Rytron on 2015-05-24
> **mc4man said:**
> edge is  vertical scrolling, typically in far right side of touchpad
2 finger is vertical scrolling anywhere on touchpad with 2 finger contact
circular is scroll up with one circular dir., scroll down opposite circular dir.

horizontal is left <> right scroll when avail in window, typically very bottom of touchpad 1 finger or also in some setups can be set to 2 finger anywhere in tp

edit: while I generally just use a wireless mouse here scr. is my tp setup
(natural reverses the scroll up/down relative to dir. on tp

Hi mc4man. Thanks for that informative explanation.

Circular scrolling seems odd. I think it's the default setting in MX Linux for some reason.

From your screenshot - natural scrolling? What's that?

---

### Post by mc4man on 2015-05-24
Natural is the opposite of what you have now. It's like you are scrolling on the screen itself (or like a tablet/touch screen
so - 
push/scroll up > page down, pull/scroll down > page up

For the touchpad I prefer the default which is the same in a way to my mouse scroll wheel, ie.
wheel towards me > page down, wheel away > page up so that translates to touchpad as pull/scroll down > page down push/scroll up page up

---

### Post by PhilGil on 2015-05-24
> **Rytron said:**
> Hi mc4man. Thanks for that informative explanation.

Circular scrolling seems odd. I think it's the default setting in MX Linux for some reason.

From your screenshot - natural scrolling? What's that?

Circular scrolling was a common option on older laptops before multi-touch touchpads became common. It's been mostly superseded by two finger scrolling.

---

### Post by Rytron on 2015-05-24
Thanks Phil.

---

