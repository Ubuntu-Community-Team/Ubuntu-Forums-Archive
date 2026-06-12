---
title: "how to auto hibernate"
date: 2008-05-02
forum: General Help
---

### Post by afreet5 on 2008-05-02
how could i customize my ubuntu gnome to hibernate (or shut down) automatically when the system is unused for specific time

---

### Post by RealPSL on 2008-05-04
Assuming that your hibernation is already working this is not difficult. I actually use System > Preferences > Power Management to achieve what you describe.

On the On AC Power tab (assuming you are using AC power) I just adjust the "Put computer to sleep when inactive" slider to the desired time and it handles the job great.

---

### Post by afreet5 on 2008-05-13
it puts computer in sleep mode isn't it .... i want it to hibernate or completely turn off

---

### Post by prvteprts on 2009-05-31
> **afreet5 said:**
> it puts computer in sleep mode isn't it .... i want it to hibernate or completely turn off

I agree. This is what I need Ubuntu to do as well. Any suggestions?

---

### Post by TimBilly on 2009-12-02
I'm looking for the same thing. I need a "Put the computer into Hibernation" option rather than "put the computer to Sleep." Any solutions out there?

---

### Post by amokoura on 2009-12-16
+1 for auto-hibernate.

---

### Post by Cuco3 on 2009-12-16
Try this, type in terminal:

```
gconf-editor
```then go to Apps > Gnome Power Management > Actions

then double click the value of "Sleep Type AC" and enter "hibernate"

For future reference, go to "Bookmarks > Add Bookmark" so it saves that tree directory for you.

**Sleep Type AC** is described as: "The type of sleeping that should be performed when the computer is inactive. Possible values are "hibernate", "suspend" and "nothing"

Sounds like that should fix your problems.

---

