---
title: "A couple Konqueror questions."
date: 2006-11-15
forum: General Help
---

### Post by Cable on 2006-11-15
I'm trying out KDE just for the fun of it.  Still getting used to things.  Anyway, I'm using the "Detailed List" view in Konqueror, and I'm wondering how I can get it to alternate the color of each row in the file list.  Also, how can I configure the middle mouse button to close a tab?  Right now it's not doing what I want it to do.

---

### Post by aysiu on 2006-11-15
That's odd. My Detailed List view defaults to alternating colors for each row. Maybe that has something to do with the color scheme you're using?

Try Alt-F2 ```
kcontrol
``` and go to Appearance > Colors

As for the "middle-click to close tab" feature, I don't think that's part of Konqueror. Maybe you should use Firefox instead?

---

### Post by dargaud on 2006-12-03
May I add another question ?

When using Konqueror for file browsing, how can I keep the file list (right) and the folder list (left) synchronized. In other words, how can I make it behave just like Windows Explorer ?

---

### Post by mexlinux on 2006-12-03
mmmh, mine i ssynchorined by default in both ways tree<->files...

---

### Post by dargaud on 2006-12-12
Well, sometimes it does but there are plenty of circumstances where it doesn't. For instance select the [Home folder] view in the left column. Then navigate somwhere else with the right file list or the url bar, and nothing will update the folder structure anymore.

---

### Post by Rashid584 on 2006-12-26
you can close tabs with middle click. you need to edit your konquerorrc

```
[FMSettings]
AlwaysTabbedMode=false
**MouseMiddleClickClosesTab=true**
PermanentCloseButton=false
TabCloseActivatePrevious=false
UnderlineLinks=false

```

Hope that helps someone... :)

-Rashid

---

