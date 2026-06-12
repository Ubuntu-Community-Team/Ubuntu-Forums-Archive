---
title: "seamonkey mouse auto scrolling posible?"
date: 2007-09-08
forum: General Help
---

### Post by sdowney717 on 2007-09-08
in firefox, when you press the center wheel button, you can scroll the page up and down by moving the mouse.
I looked for this in seamonkey and cant find it, does anyone have any ideas? 
In my seamonkey, when i push the center wheel, it goes to a google search page

---

### Post by kerry_s on 2007-09-08
yes, type 
```
about:config
```

in the address bar and hit enter, type> general <in the filter
change general.autoScroll to true by double clicking on it.

the scroll thing is ugly but it works. i usually just left-click+hold on the scrollbar and move the mouse up or down.

---

### Post by sdowney717 on 2007-09-09
It still did not change anything?
not sure why. I also went into edit preferences and that did not make it work either.
I did close and reopen seamonkey

I found this so apparently my seamonky is not working like it is supposed to be working

[http://seamonkey.ilias.ca/generalfaq/#noAutoScroll](http://seamonkey.ilias.ca/generalfaq/#noAutoScroll)

---

### Post by kerry_s on 2007-09-09
okay you also need>
middlemouse.contentLoadURL
false

that should give you the ugly scroll

---

### Post by sdowney717 on 2007-09-09
yes, that finally got it.
why is it ugly?
On mine the picture icon is round just like firefox.
I tried to show a screen shot but it goes away when I try to take the screen shot.

It is very practical to use the feature.

can you change the icon picture?

---

### Post by kerry_s on 2007-09-09
yours don't have that ugly square around it?

---

### Post by sdowney717 on 2007-09-10
No, I have a round icon

How do you take a picture of it, it vanishes if I click somewhere else on the screen with the mouse.

---

### Post by kerry_s on 2007-09-10
you've got to delay the screen shot. i use scrot> scrot -d 5 1.jpg

---

### Post by kerry_s on 2007-09-10
well anyway's anything else you need with seamonkey, i'm done playing with it, might get rid of it soon. :)

---

