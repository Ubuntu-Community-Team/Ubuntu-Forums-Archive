---
title: "Minor Xgl/Beryl Issues"
date: 2006-10-26
forum: General Help
---

### Post by serion on 2006-10-26
So I made the switch to Edgy yesterday night, and tried getting Beryl running on it today.  Everything is working out great, but I have a few little things that are bugging me:

1)  The center-of-the-screen windows overview that shows all open windows when I zoom out.  It works great, but I am running dual monitors, and I would very much like to have it display on one monitor or the other, instead of having a big black bar through my windows.

2)  I have a panel at both the bottom and top of my screen, and when maximized, windows correctly stick to the top panel and both sides of the monitor, but get in behind my lower panel.  Is there a way to fix this besides setting the bottom panel to autohide?  It worked fine before Beryl.

3)  I used to be able to have windows stick to each other's sides and the borders of the desktop.  Now, though, the "snap" seems to be gone, and windows will go all over the place.  They no longer even stick to the side of the screen or the panels, and I would really like to have this functionality back.


I am running Edgy, in Gnome, on an nvidia card.  Thanks a lot, guys.

---

### Post by PriceChild on 2006-10-26
> **serion said:**
> 1)  The center-of-the-screen windows overview that shows all open windows when I zoom out.  It works great, but I am running dual monitors, and I would very much like to have it display on one monitor or the other, instead of having a big black bar through my windows.I'm sorry... but that's one of the disadvantages of using both right now...> 2)  I have a panel at both the bottom and top of my screen, and when maximized, windows correctly stick to the top panel and both sides of the monitor, but get in behind my lower panel.  Is there a way to fix this besides setting the bottom panel to autohide?  It worked fine before Beryl.not sure why this is happenning, i regularly have to alt+move because windows are behind my top panel. Search the beryl bug tracker maybe.> 3)  I used to be able to have windows stick to each other's sides and the borders of the desktop.  Now, though, the "snap" seems to be gone, and windows will go all over the place.  They no longer even stick to the side of the screen or the panels, and I would really like to have this functionality back.that's what you pay for wobblyness ;)

---

### Post by theslut on 2006-10-26
i also have problems with 2 & 3 since going to edgy.

---

### Post by serion on 2006-10-26
I'm finding that one is not really too huge an issue, because I can still see it, and when there's an even number of things on the screen they end up on opposite monitors and not in the middle anyway.

What's with the bottom panel though?  Its properties are almost identical to the tops, and yet it behaves very differently

---

### Post by theslut on 2006-10-26
ive only got a top panel and now everytime i open an app the top bar starts behind the panel requiring me to press ALT to move it. very annoying.

---

### Post by WorLord on 2006-10-26
1) Can't help you there.

2) I haven't seen this happen here, so I can only speculate.

3) Hold down shift while dragging.  The sensitivity is less than Metacity's in Edgy, but I actually prefer Beryl's setting.

---

### Post by VR6Pete on 2006-10-27
I've had the same issues as described in point 2. 

it only happens on twin view I've noticed.....

Post a bug report on the beryl bug tracker.

---

### Post by beerorkid on 2006-10-27
2) try this:  beryl-manager --> beryl settings manager --> move window --> check all three options

3) beryl-manager --> beryl settings manager --> wobbly windows --> check default snapping to on

not completely positive cuz I am not on edgy yet, but worth a try ;)

---

### Post by hellblade on 2006-10-27
Thanks mate. I can confirm that the snapping option works great!

---

### Post by aqwabawks on 2006-11-01
I too and am having some minor XGL/Beryl issues, albeitly slightly different to the original poster.

Mine relates to the wave-like effect that is on by default in Beryl.  The feature I am referring to is that when you select a menu from the menu bar the menu that appears kind of ripples/shakes.  I was wondering how to turn it off via the Beryl Settings Manager?

The other curious problem I have is when my mouse hovers over either the uppermost or lowermost corners of my screen.  When this happens the Linux version of expose appears with all the applications I am running laid out.  Now, don't get me wrong, I love this feature, but it gets annoying when it always pops up when I have my mouse in a corner of my screen.  Any way to disable that ability (that it will only appear when I press F8)?

---

### Post by beerorkid on 2006-11-01
gonna split it up into your two issues

1) beryl settings manager --> animations --> create effect 2
you can change what it affects, change the animation, or turn it off

2. beryl settings manager --> scale --> right most tab screen edges and corners
Set accordingly or uncheck/disable

---

### Post by aqwabawks on 2006-11-02
Thanks, that helped a lot, it wish it was a bit more clear (the options and what not), as some of them kinda confuse me... :)

---

### Post by desimo on 2006-12-30
In beryl version 1.4, the problem of windows opening behind panels can be solved by  turning on "intelligent placement" mode.  That worked for me.

---

