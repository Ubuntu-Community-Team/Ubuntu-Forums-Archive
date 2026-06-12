---
title: "How To Use The Buttons Of Your Trackball In Linux"
date: 2007-11-20
forum: General Help
---

### Post by calande on 2007-11-20
Hi, I was able to use the four buttons of my Kensington Turbo Mouse PRO, and I wrote a tutorial for the community. Hope this helps: [http://linux-trackball.dreamhosters.com/](http://linux-trackball.dreamhosters.com/)

:)

---

### Post by ADH on 2007-12-09
How can I set the upper buttons as held down for drag and drop?

---

### Post by calande on 2007-12-09
How will you perform the drag and drop? (Here I hold down the left-click and move the marble)

---

### Post by ADH on 2007-12-27
I want the top buttons to be interpreted as being held down when clicked, which is how they're set in OS/2 and Windows.  Top left button is locked left, top right is locked right.

---

### Post by calande on 2007-12-27
Ok, assuming your button is #8, you would just execute:

```
"echo 'ButtonRelease 1 ButtonPress 1' | xmacroplay :0"
b:8
```

This should work. Not sure why you need the button to be held down when clicked though :)

---

### Post by ADH on 2007-12-27
I'm disabled, and can't hold the buttons down and move the ball at the same time .  That's why I need to set the top two buttons as locked down.

Another question - is there a utility that allows the mouse pointer to pass through the screen edges and reappear on the other side?  I have such for OS/2 and Windows.

Thanks,

---

### Post by calande on 2008-01-11
Ah, I see. Did my code help somehow to drag and drop?

---

### Post by ADH on 2008-01-28
I haven't been able to install it yet, to set the upper buttons as held down. 

If Kensington would release a Linux driver for the Expert Mouse, life would be much simpleer.

---

### Post by calande on 2008-01-28
Actually, you mean a front-end to the driver :)

---

