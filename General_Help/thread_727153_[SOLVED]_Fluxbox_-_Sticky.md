---
title: "[SOLVED] Fluxbox - Sticky"
date: 2008-03-17
forum: General Help
---

### Post by The Avatar of Time on 2008-03-17
Hello I have a rather simple/dumb question here. I use Fluxbox, and I am setting up multiple workspaces. I have a few apps that I want to be sticky so that they appear on all workspaces, however when I do this it makes the nice pretty blue square that I click to make it sticky turn to an ugly grey. My question is is there a way to make an app sticky without changing the color of the square on the window border? Thanks for any help.

---

### Post by bodhi.zazen on 2008-03-17
I think the has more to do with the theme then Fluxbox.

---

### Post by p_quarles on 2008-03-17
Yes, that's a theme attribute, and is specifically set by this:
```
window.stuck.pressed.pixmap: 
```
If left blank, the default (grey) button will be used.

---

### Post by The Avatar of Time on 2008-03-17
I see. Thanks for the advice. So if I just copy the button I want to appear in place of the default it should then work fine?

---

### Post by jviscosi on 2008-03-18
> **The Avatar of Time said:**
> I see. Thanks for the advice. So if I just copy the button I want to appear in place of the default it should then work fine?

There are actually a bunch of buttons and button states in the newer versions of Fluxbox, some of which are likely to be missing pixmaps if you're using an older theme.  p_quarles already mentioned **pressed**, which IIRC is what you see while you're actually holding the mouse button down over a button.  Other states are **unfocus** and just the regular (focused) state, which doesn't have a qualifier. "Stuck" is the button that's displayed after you make a window sticky; "Stick" is the button that's displayed when a window is not currently sticky.  "Shade" and "Unshade" are similar toggles.  I believe "Unshade" is relatively new as it's frequently missing from themes.  (I probably spend way too much time tweaking old Fluxbox themes to make the buttons look like I want them.)

Tenr has a [tutorial on theming]("http://tenr.de/howtos/style_fbox/style_fbox.html") Fluxbox.  Not sure how up to date it is but here's the section about buttons:

> 
furthermore another important thing is: in a classic style all buttons are defined through **window.button.***. in a pixmap style you CAN make a image for each button and their states (focused, unfocused, pressed). you don't have to but you can. to give an example of the buttons you can style look at this: 

window.shade.pixmap:    shadefcs.xpm
window.shade.unfocus.pixmap: shadeufcs.xpm
window.shade.pressed.pixmap: shadepr.xpm

 window.unshade.pixmap: unshadefcs.xpm
window.unshade.unfocus.pixmap: unshadeufcs.xpm
window.unshade.pressed.pixmap: unshadepr.xpm

 window.menuicon.pixmap:    menuiconfcs.xpm
window.menuicon.unfocus.pixmap: menuiconufcs.xpm
window.menuicon.pressed.pixmap: menuiconpr.xpm

 window.close.pixmap:    closefcs.xpm
window.close.unfocus.pixmap: closeufcs.xpm
window.close.pressed.pixmap: closepr.xpm

 window.iconify.pixmap: minfcs.xpm
window.iconify.unfocus.pixmap: minufcs.xpm
window.iconify.pressed.pixmap: minpr.xpm

 window.maximize.pixmap:    maxfcs.xpm
window.maximize.unfocus.pixmap: maxufcs.xpm
window.maximize.pressed.pixmap: maxpr.xpm

 window.stick.pixmap:    stickufcs.xpm
window.stick.unfocus.pixmap: stickufcs.xpm
window.stick.pressed.pixmap: stickpr.xpm

 window.stuck.pixmap: stuckfcs.xpm
window.stuck.unfocus.pixmap: stuckufcs.xpm
window.stuck.pressed.pixmap: stuckufcs.xpm

 the syntax differs a little bit from the other parts, but again it's really simple to understand. look at [the little screenshot]("http://tenr.de/howtos/style_fbox/style_fbox.html#styleparts_classic") to get a clue what the buttons are.

**window.*.pixmap** are the pixmaps you see on a focused window.

**window.*.unfocus.pixmap** are the pixmaps you see on an unfocused window.

**window.*.pressed.pixmap** are the images you see when you click the button.

**window.stuck.*** is the activated state of the stick buttton.



---

### Post by The Avatar of Time on 2008-03-19
Thanks to all, I have it solved now. The entire window.stuck.__.pixmap: section was left out of my style, so I added it and copied in the normal pixmaps and it looks much better now. Thanks for the help!

---

### Post by RedSquirrel on 2008-03-19
Just for future reference, the fluxstyle man page is helpful for style information:

```
man fluxstyle
```

---

