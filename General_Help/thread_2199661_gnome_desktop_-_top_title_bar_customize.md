---
title: "gnome desktop - top title bar customize"
date: 2014-01-15
forum: General Help
---

### Post by mrkaplan on 2014-01-15
i use gnome desktop under ubuntu 12.04 . 
i cannot seem to find how to customize the top desktop title bar :  where you have , on a black bg : activities on left ,  calendar in center  ,  system options on the right .
this is by default black bg and bigger font. 
 i find black to be too high contrast , id prefer to switch to grey or else.  and id like the font to be same size as others .  
can this be done ?
so far  tried ubuntu tweak and gnome tweak tool , didnt see an option to control this .

---

### Post by buzzingrobot on 2014-01-15
I believe this can only be done by changing themes or by editing the CSS/Javascript of the default theme.

---

### Post by deadflowr on 2014-01-15
Open a terminal and run
```
gksu gedit /usr/share/gnome-shell/theme/gnome-shell.css
```
When it opens go to the section Panel.
Use the search for text feature the section will look like this

```
/* Panel */

#panel {
    background-color: black;
    font-weight: bold;
    height: 1.86em;
```
Change the color here for the panel.
If you want to change further settings, like the various colors, look further down.
There are several places that you can change the color for.
When done save, and to see the effects logout of gnome and then log back in.

I don't know about changing fonts size in this panel, though.
Never thought about it. I find the fonts in gnome's panel to be just fine.

As an added bonus, to make the panel transparent add this line to the section of the background in the panel section
```
background-color: rgba(0,0,0,0.0);
```
adjusting the alpha channel to your liking (that's the 0.0 section the numbers go 0(red,0(green),0(blue),0.0(alpha channel)

If you want to do some really heavy handed lifting, look into the various .js files in 
/usr/share/gnome-shell/js/ui folder.

don't know how much this'll help, but it's a place to look at.
Have fun.

---

