---
title: "GUI too big for screen, unable to reach &quot;continue&quot; on install"
date: 2007-05-27
forum: General Help
---

### Post by stabu on 2007-05-27
Has anybody got a cure for a small screen problem where Feisty loads properly, but when you go through the install sequence in the Gnome GUI, you are unable to see and, consequently, bring your mouse down to the "continue" button?

There are some options in the initial screen for varying the screen res, but they have zero effect. Gnome itself allows you to vary the screenres, and I have tried it, but there is only one option allowed ... the one I'm usiing!

For some reason Feisty has decided what my screenres is, and offers me no ther options. Any help for this one?

It may be my screen of course, it's telling the wrong things to the CPU ...  I admit it's an old one ...

---

### Post by allwin on 2007-05-27
> **stabu said:**
> Has anybody got a cure for a small screen problem where Feisty loads properly, but when you go through the install sequence in the Gnome GUI, you are unable to see and, consequently, bring your mouse down to the "continue" button?

There are some options in the initial screen for varying the screen res, but they have zero effect. Gnome itself allows you to vary the screenres, and I have tried it, but there is only one option allowed ... the one I'm usiing!

For some reason Feisty has decided what my screenres is, and offers me no ther options. Any help for this one?

It may be my screen of course, it's telling the wrong things to the CPU ...  I admit it's an old one ...

I ran into the same situation here because I use a monitor switch (KVM switch).  I found that by altering the xorg.conf file and making the correct invocation to turn EDID off (varies with your video driver!) and set the res to 96DPI in that conf file, things got better.  Sometimes it's "Option UseEDID False" and sometimes "Option IgnoreEDID", case sensitive of course.  Plus you have to be able to make the edit outside of the GUI entirely.  You will have to do a google on EDID to find out what the proper syntax is for your particular video card.  Hope that clue sets you straight.[http://en.wikipedia.org/wiki/EDID]("http://en.wikipedia.org/wiki/EDID")

---

