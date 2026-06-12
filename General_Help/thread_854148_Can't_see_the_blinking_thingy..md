---
title: "Can't see the blinking thingy."
date: 2008-07-09
forum: General Help
---

### Post by animaniac on 2008-07-09
Can't see the whats its name, anyone have a clue how i can make it darker, the current pale blue color is almost impossible to make out. 

[http://img224.imageshack.us/img224/5673/screenshotfi5.png](http://img224.imageshack.us/img224/5673/screenshotfi5.png)

Really annoying.

edit: also i tried changing the pointer theme, didn't help.
also its only this color in some places, firefox address bar that also has a dark themed background and the cursor there is black.

---

### Post by Rhubarb on 2008-07-09
That's a cursor, I'm not too sure how to change it.  Perhaps someone else may have an idea?

---

### Post by sayakb on 2008-07-09
Is that KDE4?

---

### Post by animaniac on 2008-07-09
Gnome...
See the [ubuntu] prefix, 8.04.

---

### Post by sayakb on 2008-07-09
I saw the prefix :p
Plus, not sure that the color could be changed.. Im aware of changing terminal's cursor color but not this..
Btw, what theme is it? Looks kewl!

---

### Post by animaniac on 2008-07-09
@LinuxIsInnovation: 

#i took Sauna-Dark for the controls, 

#changed the input box colour background to #8F7D6A (easier to see the black text, but makes the cursor a pain)

#window borders are from the Chocolate V1.0 theme.

#background from tinypilot.com

#icons Human (appart from evolution icon, which i don't like the default of)and default pointer.

and heres a screen:)
[http://img98.imageshack.us/img98/7164/screenshot1hw8.png](http://img98.imageshack.us/img98/7164/screenshot1hw8.png)

Really nice combined.

---

### Post by sayakb on 2008-07-09
Looks great! :)

---

### Post by Neo_The_User on 2008-07-09
Go to system > Preferences > Appearance> Themes > Double click on Human and hit enter.

---

### Post by animaniac on 2008-07-10
> **Neo_The_User said:**
> Go to system > Preferences > Appearance> Themes > Double click on Human and hit enter.

any real solution would be welcome, i like my dark theme, default just doesn't do it for me.

---

### Post by Rhubarb on 2008-07-10
Just thinking out aloud, but it should be a setting somewhere in /usr/share/themes/
What step do you take when setting up your (very nice) theme do you find the cursor going for being black to pale blue?  If you know this, then you'll know more exactly where to look to fix up this problem.

If you're unsure, could you please post links of the themes / controls / how you changed the input box background colour - so I may repeat your process myself (I like your desktop a lot, and wouldn't mind a similar one)  This way I can help solve this mystery faster.

---

### Post by animaniac on 2008-07-10
Heres a link to the theme from which i used the controls:

[http://gnome-look.org/content/show.php/Sauna-Dark?content=80633](http://gnome-look.org/content/show.php/Sauna-Dark?content=80633)

The background color was changed System>Preferences>Appearance>[Customize...]>Colors(tab)>Input boxes, Background(click on the color>Color name: #8F7D6A

Unfortunately thats the first place i looked for a possibility to change the cursor.

---

### Post by Rhubarb on 2008-07-10
Aaaah, I think I know why this problem arises.
It seems to effect some applications (such as Evolution and OpenOffice.org)
Evolution and OpenOffice.org (but not other apps, such as gedit, pidgin or xchat) seem to choose a cursor colour that has the opposite hue (180°
), and a value that's symmetrically opposite 50.
What this means is, is that a poor contrasting cursor would arise from an input box background colour that has a low saturation and a value close to 50.

Now that I'm quite sure that this is the problem, I'm not sure exactly how this problem would be rectified / reported as a bug.  It may be a bug unique to Gnome, or gtk, or some libraries, or particular applications.
I may look into this further.

---

### Post by hihihi on 2008-10-25
hello there,
i am having exact the same problem.
i am writing a theme and on especially on some entry-boxes, Thunderbird, Evolution the blinker is not visible, due to lowlow contrast.

what you are saying seems right.
now, is there a way to make some hack in the gtkrc in order to give those entry-field a different look than the system-wide background-color?

---

