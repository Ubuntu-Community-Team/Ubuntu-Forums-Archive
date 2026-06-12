---
title: "Any good transparent themes for gnome?"
date: 2007-01-13
forum: General Help
---

### Post by raul_ on 2007-01-13
So i took a look at Sabayon Linux and found it really cool :mrgreen: and i wanted to make my panels transparent. I tried to use "solid color -> transparent" in the panel properties but it failed miserably (see attachment). 
Has anyone been able to find a theme for gnome/beryl that makes panels go transparent? I know there's the option of creating custom transparent images and overwriting the ones in the theme's folder but....i really wanted a native theme that did the trick.

---

### Post by Bigbluecat on 2007-01-13
Move you cursor over an unoccupied space in the panel. Right click and select properties.

Select background.

Find the style slider and slide left/right till you get the transparent mix you want.

Is this what you were trying to achieve?

---

### Post by raul_ on 2007-01-13
That's what i did :P i have posted solutions in other threads but i really want a transparent theme. I've been searching but i'm aware that there are a lot of other users here that know more themes than i do so...

---

### Post by PriceChild on 2007-01-13
Sabyon uses Beryl by default doesn't it....?

---

### Post by raul_ on 2007-01-13
Yes, but it also uses KDE by default (i hate KDE, no flaming intention)

---

### Post by Bigbluecat on 2007-01-13
OK.

I'm using the visa_smoked_aero_glass theme which can be found in the emerald theme manager. This may be close to what you saw in Sabayon.

Well. I would be using it when I fix Beryl after the recent upgrades :rolleyes:

---

### Post by raul_ on 2007-01-13
What about the Metacity theme? Which one are u using?

---

### Post by Bigbluecat on 2007-01-13
It's a combination of things.

Control is E17-GTK-Blue

Borders are Mozilla modern

Icons are Glossy Glass

Then themed Firefox with Metal Lion Ice

---

### Post by ~LoKe on 2007-01-13
Couldn't you just use your wallpaper as the background image?

---

### Post by raul_ on 2007-01-13
The problem is not the background. Some themes even support "fully" transparent panels. The thing is that when a window is selected, it turns gray or another color, that kinda screws up the whole feeling =\

---

### Post by Bigbluecat on 2007-01-13
Not tried this and can't until I fix Beryl but in the Beryl Settings Manager you can select "Set Windows Attributes by various criteria" under the Window Management tab.

Seems to have some way of setting window opacity. Not sure how it works though. You may get some help on the Beryl forums.

I'll have a play with this when I'm up and running again.

---

### Post by ~LoKe on 2007-01-13
> **Bigbluecat said:**
> Not tried this and can't until I fix Beryl but in the Beryl Settings Manager you can select "Set Windows Attributes by various criteria" under the Window Management tab.

Seems to have some way of setting window opacity. Not sure how it works though. You may get some help on the Beryl forums.

I'll have a play with this when I'm up and running again.
```
w:DOCK:50
```

---

### Post by Bigbluecat on 2007-01-13
Well I fixed Beryl and got it working again.

Tried w:DOCK:50 - seemed to turn down the brightness of the panels. 

I think what our friend is after is that minimised windows are semi transparent when on the panel. 

I'll keep looking.

---

### Post by raul_ on 2007-01-13
Here is a screenshot so you guys see what i'm talking about. This is the "Clearlooks theme". See how the panel and windows are transparent? but See how the window that is selected (Swiftfox) isn't transparent at all, and notice the ugly white separator. This messes the whole feeling

---

### Post by ~LoKe on 2007-01-13
> **raul_ said:**
> Here is a screenshot so you guys see what i'm talking about. This is the "Clearlooks theme". See how the panel and windows are transparent? but See how the window that is selected (Swiftfox) isn't transparent at all, and notice the ugly white separator. This messes the whole feeling

I don't think you can have any control over that without using beryl to make it transparent, which also makes the text and menu's transparent as well.

---

### Post by strabes on 2007-01-13
Themes in gnome don't control panel transparency. You could make your own semi-transparent .png and it would work I guess. Keep in mind that things like the window list cannot be transparent for some reason.

---

### Post by raul_ on 2007-01-13
Weel, i (kinda) did the trick with the Human theme by not using fully transparent, but only half transparent panel. It bugs me that the panels with the Human theme can't be smaller than 23 pixels but what the heck. Here are some screenshots:

[http://www.ubuntuforums.org/showpost.php?p=2008509&postcount=321]("http://www.ubuntuforums.org/showpost.php?p=2008509&postcount=321")

Still looking for a good Beryl theme thar goes with it though

EDIT: I did it...i just did what i said in the first post and replaced the images in the "panel" folder for transparent ones

[http://www.ubuntuforums.org/showpost.php?p=2009825&postcount=324]("http://www.ubuntuforums.org/showpost.php?p=2009825&postcount=324")

---

