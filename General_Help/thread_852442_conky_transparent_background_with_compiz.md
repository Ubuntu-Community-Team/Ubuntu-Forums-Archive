---
title: "conky transparent background with compiz"
date: 2008-07-07
forum: General Help
---

### Post by pompeyjohn on 2008-07-07
Right, well I'm stumped.

I have gnome [hardy] running compiz. As I want the cube with different wallpapers on each face I have stopped nautilus from drawing the desktop. 

Each face of the cube has a wallpaper as set within Compiz. I can see at install time that these are drawn ontop of whatever is set in gnome.

.... and now whenever I run a conky script I can see it on every face of the cube, but the background of conky is the underlying brown default of gnome.

The same thing happens when trying to set the transparency of the main gnome menu panel.

Can this be overcome?

I have seen youtube videos of wonderful conky/compiz integration with gnome taskbars and different wallpapers. I have emailed the creators but heard nothing.

many thanks in advance,
John

---

### Post by easybake on 2008-07-07
a way you could try to go around it is to launch 4 seperate un-sticky conkys. have them sleep for different times. after the first launches rotate the cube. after the 2nd launches rotate cube. etc...

its not really a sophisticated way to do it but it should work.

---

### Post by Locutus_of_Borg on 2008-07-08
I accomplished this by setting ```
own_window yes
own_window_type normal
own_window_transparent no
own_window_hints undecorated

``` in .conkyrc

then in compiz, set class=Conky as a widget, and under window opacities in general settings, set class=Conky opacity to 33, in Window Rules I set the same class=Conky on everything but "above", "fullscreen", and "no ARGB visuals", and finally gave class=Conky a fixed window placement

this resulted in four different wallpapers, each with conky displayed on the right side, with an invisible background

attached is how it turned out

---

### Post by pompeyjohn on 2008-07-08
ok, I have tried that 

(all but the fixed window placement bit because I am not sure how to do that yet)

and running conky from the command line, it doesnt show in the desktop.

However, if you then hit F9, it fades the previously active windows and conky appears - on all sides of the cube. As soon as I click on anything but conky, it vanishes.

Thanks again in advance for the help
John

---

### Post by pompeyjohn on 2008-07-08
I can confirm that swearing at the screen and shaking my fist in a menacing fashion, does'nt make it work.

---

### Post by nkri on 2008-07-08
> **pompeyjohn said:**
> i Can Confirm That Swearing At The Screen And Shaking My Fist In A Menacing Fashion, Does'nt Make It Work.

+1

---

### Post by Maybelline on 2008-07-16
> **pompeyjohn said:**
> However, if you then hit F9, it fades the previously active windows and conky appears - on all sides of the cube. As soon as I click on anything but conky, it vanishes.

Sounds like you have it listed as a widget in CCSM.  I think that, if you turn off the Widget Layer plugin, it won't vanish when you click on other things.  Or, you could remove conky from the "Widget Windows" entry on the Behavior tab.  I can't say for sure -- I don't use the widget plugin.

HTH

---

### Post by Maybelline on 2008-07-16
> **Locutus_of_Borg said:**
> I accomplished this by setting ```
own_window yes
own_window_type normal
own_window_transparent no
own_window_hints undecorated

``` in .conkyrc

then in compiz, set class=Conky as a widget, and under window opacities in general settings, set class=Conky opacity to 33, in Window Rules I set the same class=Conky on everything but "above", "fullscreen", and "no ARGB visuals", and finally gave class=Conky a fixed window placement

this resulted in four different wallpapers, each with conky displayed on the right side, with an invisible background

I am using some similar settings, but I don't use dark backgrounds all 4 sides, so decreasing the opacity just won't work 100% of the time.

But, keep your eyes on [**this thread**]("http://forum.compiz-fusion.org/showthread.php?t=7753"), which sounds like it should work similar to [**this old Beryl plugin**]("http://www.youtube.com/watch?v=FESBa3qjZ20").

With this plugin, you could set your conky window to be ```
own_window_colour hotpink
``` and then tell this plugin that for conky windows, make hotpink = transparent.  That's my hope, anyway.

---

### Post by soul710 on 2009-01-19
> **Locutus_of_Borg said:**
> I accomplished this by setting ```
own_window yes
own_window_type normal
own_window_transparent no
own_window_hints undecorated

``` in .conkyrc

then in compiz, set class=Conky as a widget, and under window opacities in general settings, set class=Conky opacity to 33, in Window Rules I set the same class=Conky on everything but "above", "fullscreen", and "no ARGB visuals", and finally gave class=Conky a fixed window placement

this resulted in four different wallpapers, each with conky displayed on the right side, with an invisible background

attached is how it turned out


Hey, whats this mac-like bar on the bottom on your screenshot? :]

---

### Post by soul710 on 2009-01-20
> **soul710 said:**
> Hey, whats this mac-like bar on the bottom on your screenshot? :]

Anyone?

---

### Post by mithbuntu on 2009-04-15
It's Awn Window Manager (awn for short).  Very customizable and very cool.

---

### Post by Randomperson_1000 on 2009-05-10
Thanks every1 got it working 

one problem though when i click the minimise button conky also minimises! 

conky was appealing to me because it was intergrated into the desktop

has any1 been able to find a solution to this

I would normally of changed the conkyrc file to own_window no but then it doesnt appear on my desktop

any1 with any ideas?

n.b when i 1st turned the wallpaper plugin on it actually worked conky worked liked it should without the tweaks but when i restarted wouldnt show without the tweaks suggested here

---

### Post by Wollombi on 2009-11-01
Change own_window_type from normal to override.

---

