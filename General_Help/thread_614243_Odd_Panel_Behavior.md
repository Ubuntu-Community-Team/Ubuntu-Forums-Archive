---
title: "Odd Panel Behavior"
date: 2007-11-15
forum: General Help
---

### Post by wallish on 2007-11-15
Okay, this isn't a big issue but it is a little strange:  When logging into Gnome (Gutsy), I sometimes (not always) find my panel icons rearranged.  The panels themselves do not change position as it is with some other people, just the icons. Also, sometimes they are just removed altogether... This occurs independent of whether they are locked or not.  

Also, custom launchers have a disturbing tendency to reset themselves to blank launchers.  The icons that are being moved include the system monitor, volume icon, the notification area, and a few other non-standard program icons.  The icons that are removed completely are usually icons that were only placed in the panel during my last session... apparently if an icon lives through the first logout it'll make it through the rest.

---

### Post by FearNoIdea on 2007-11-16
I have been having a similar issue. Posted about it a while ago, no resolve... Do you have Avant Window Navigator installed?  I have noticed that most who are having this issue have AWN installed. Another possibly related issue that I have encountered is that at times my background would not load.  Upon opening Appearance Preferences the background would decide to show up.

---

### Post by wallish on 2007-11-16
No, no compositing at all. Also, this first happened within the first three or so log-ins, so it was before I installed any non-repository software (or really hardly any software at all).  I've never had the background problem, though.

---

### Post by zvacet on 2007-11-16
Are the icons locked on panel?If they are 

```
gconf-editor
```


**apps>nautilus>panel>notification area>tick locked**

---

### Post by wallish on 2007-11-16
Yes, everything that needs to be locked down is, including notification area, system monitor, volume, clock, workspace switcher, and logout button (everything that is on the right of my top panel).  Besides, even if they were not locked down why should they move, apparently at random, when I log in?

---

