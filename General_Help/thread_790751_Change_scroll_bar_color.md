---
title: "Change scroll bar color?"
date: 2008-05-11
forum: General Help
---

### Post by wiseguyxp on 2008-05-11
I set up a new look for my Ubuntu 8.04 and I don't like the orange scroll bar still haunting me.  Is there a way that I can change it?

---

### Post by wiseguyxp on 2008-05-11
bump?

---

### Post by wiseguyxp on 2008-05-11
last bump

---

### Post by naptastic on 2011-10-17
Add these lines to ~/.gtkrc-2.0:

  style "gnome-color-chooser-scrollbar"
  {
    bg[NORMAL] = "#F07746"
    bg[PRELIGHT] = "#D76A3E"
    bg[ACTIVE] = "#BD5D37"
  }
  widget_class "*Scrollbar" style "gnome-color-chooser-scrollbar"

Change the hex color values to what you like. Prelight is the color while the mouse is hovering over the scrollbar, and active is the color while it's being held down.

---

### Post by Meelad on 2011-10-17
> **naptastic said:**
> Add these lines to ~/.gtkrc-2.0:

  style "gnome-color-chooser-scrollbar"
  {
    bg[NORMAL] = "#F07746"
    bg[PRELIGHT] = "#D76A3E"
    bg[ACTIVE] = "#BD5D37"
  }
  widget_class "*Scrollbar" style "gnome-color-chooser-scrollbar"

Change the hex color values to what you like. Prelight is the color while the mouse is hovering over the scrollbar, and active is the color while it's being held down.

:lolflag:

Finally he gets his answer!

---

### Post by fixerdave on 2011-10-17
> **Meelad said:**
> :lolflag:

Finally he gets his answer!

Yeah... took me a minute to figure out why there were suddenly 3 different posts from different people all asking the same question, and not one of them complaining about 11.10 ;)
Naptastic must have done a search :)

---

### Post by Meelad on 2011-10-17
> **fixerdave said:**
> Yeah... took me a minute to figure out why there were suddenly 3 different posts from different people all asking the same question, and not one of them complaining about 11.10 ;)
Naptastic must have done a search :)

Yeah, it looks to me like he did it in a reverse way.. He had the answer first, and then searched for the questions! :D

---

### Post by fixerdave on 2011-10-17
> **Meelad said:**
> Yeah, it looks to me like he did it in a reverse way.. He had the answer first, and then searched for the questions! :D


Well, if you struggle with something and find an answer, getting it in the forums to be search-able for the next guy is a nice thing to do.  Going back to 2008 might be pushing it a little, 3 times in as many minutes is a little excessive, but I'll give the guy credit.  It's better than not letting anyone know.

Slightly off-topic, I was surprised when I did a Google search for something and came up with a forum post from here that was only a few minutes old, right at the top of the list.  If you want to plaster some solution where it will be found... here's a good place.

---

### Post by Meelad on 2011-10-17
Yeah sure, I totally agree. It was nice of him to do that.. I just found it a bit funny..

This place is always placed very high in Google search results especially if you include Ubuntu in your search.. The high traffic on this site surely helps pushing it further up in the list..

---

