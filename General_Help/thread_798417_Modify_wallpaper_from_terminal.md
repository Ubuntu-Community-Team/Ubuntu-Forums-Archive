---
title: "Modify wallpaper from terminal"
date: 2008-05-18
forum: General Help
---

### Post by Tux.Ice on 2008-05-18
like the title says

---

### Post by barbedsaber on 2008-05-18
I guess you want to know how to do it?

---

### Post by Tux.Ice on 2008-05-18
yes.

---

### Post by Christmas on 2008-05-18
From LinuxJournal, a while ago
> 
Create logos using CLI:

convert -size 800x120 xc:white -font Times-Roman -pointsize 100 -fill gray -annotate +20+80 'Linux is cool!' -fill black -annotate +23+83 'Linux is cool!' -trim +repage logo.png

```

man convert - convert between image formats as well as resize an image, blur, crop, despeckle, dither, draw on, flip, join, re-sam&#8208;
       ple, and much more

```

---

### Post by barbedsaber on 2008-05-18
its not for pictures, but still

Background images

In a simplified graphical environment, you might find yourself relying on an external program to set the background image -- the wallpaper.

As an alternative, you might consider the primitive but omnipresent xsetroot command, which can set the "wallpaper" to a flat color, like this:

xsetroot -solid blue

You can use any HTML color name there you like, or the value code preceded by a hash mark and enclosed in quotes (example: "#3465a4"). Add that same line to your .xinitrc file and you'll have a decent, if somewhat monotonous, background at every start. And it's lightweight as well.

---

### Post by K.Mandla on 2008-05-18
Moved to Desktop Effects and Customization.

---

