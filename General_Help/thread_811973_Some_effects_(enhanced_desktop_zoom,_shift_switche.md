---
title: "Some effects (enhanced desktop zoom, shift switcher) not working in Hardy"
date: 2008-05-29
forum: General Help
---

### Post by wild_oscar on 2008-05-29
I've just upgraded from Gutsy to Hardy.

I have an Nvidia GTS 8600 and compiz Desktop Effects were working perfectly in Gutsy.

However, after upgrading to Hardy, some of the effects don't work:

1) Enhanced desktop zoom

Doesn't zoom (Super+ mouse button 1/2, super + keyboard 1/2/3). Super + R does move the mouse, though.


2) shift switcher
Doesn't work. All it does is fade to desktop and show a grayed desktop while I'm pressing the shortcut buttons, but the mini-windows  switcher doesn't show.

If anyone has had this problem and/or knows how to solve it, I'd be very thankful!

---

### Post by soreau on 2008-05-29
> **wild_oscar said:**
> 
1) Enhanced desktop zoom

Doesn't zoom (Super+ mouse button 1/2, super + keyboard 1/2/3). Super + R does move the mouse, though.


2) shift switcher
Doesn't work. All it does is fade to desktop and show a grayed desktop while I'm pressing the shortcut buttons, but the mini-windows  switcher doesn't show.

Have you tried setting the keybinding to something other than the default?

---

### Post by wild_oscar on 2008-05-29
> **soreau said:**
> Have you tried setting the keybinding to something other than the default?

Yes, I have - doesn't work.

And in the case of the shift switcher, the effect is partially present - the desktop is shown and the image is grayed. It's just the windows that don't appear.

---

### Post by wild_oscar on 2008-05-30
This a video of how the shift switcher is seen on my computer:

[http://www.youtube.com/watch?v=LF5tkQQv39o]("http://www.youtube.com/watch?v=LF5tkQQv39o")
Notice how the effect fades the windows, but fails to show the window switcher.

---

### Post by Onedinkenedi on 2009-10-30
You can set the keybindings by running **gconf-editor** (I do it from Alt-F2), then you find the compiz zoom settings (and so much else) under **apps**/**compiz**/**plugins**/**ezoom**/**allscreens**/**options**.

Cheers.

---

### Post by overdrank on 2009-10-30
> **Onedinkenedi said:**
> You can set the keybindings by running **gconf-editor** (I do it from Alt-F2), then you find the compiz zoom settings (and so much else) under **apps**/**compiz**/**plugins**/**ezoom**/**allscreens**/**options**.

Cheers.

Hi and thanks for the info but did you notice the date on the thread 
May 29th, 2008 :)

---

