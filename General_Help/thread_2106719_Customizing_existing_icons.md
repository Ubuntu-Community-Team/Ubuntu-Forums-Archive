---
title: "Customizing existing icons"
date: 2013-01-19
forum: General Help
---

### Post by jrogge on 2013-01-19
I'm running Ubuntu 12.04 with gnome 3 shell. I'm currently using the icon theme Ubuntu mono-dark and I like it but there are just a few icons I want to change. I imagine changing those icons would just be going to some directory and replacing the images, so I looked at /usr/share/icons/ubuntu-mono-dark/ but I'm not sure where to go from there. There are 3 folders there, 16, 22, and 24. In 22 and 24, there are icons that say "audio-volume-low-panel.png" "audio-volume-low.png" etc but none of them are the ones that contain the images that appear when I change the volume through fn-f11 or other fn hotkeys. I looked but I can't find a tutorial for editing an existing icon theme in 12.04, but if there is one please post the link.
Any help is much appreciated.

---

### Post by Frogs Hair on 2013-01-19
Not all icon themes are set up the same way. I have changed images in other sets but not Ubuntu defaults.

Ask Ubuntu may another place to seek an answer. I don't think the Ubuntu sets work independently of each other and that is why you can't locate the identical images. Keep in mind some icons have many images to create an animation. Volume and battery status would be examples of that.

---

### Post by jrogge on 2013-01-19
> **Frogs Hair said:**
> Not all icon themes are set up the same way. I have changed images in other sets but not Ubuntu defaults.

Ask Ubuntu may another place to seek an answer. I don't think the Ubuntu sets work independently of each other and that is why you can't locate the identical images. Keep in mind some icons have many images to create an animation. Volume and battery status would be examples of that.
Alright, I'll make a post over at Ask Ubuntu, thanks.

---

### Post by jrogge on 2013-01-19
[http://askubuntu.com/questions/245222/creating-icon-themes-gnome-3](http://askubuntu.com/questions/245222/creating-icon-themes-gnome-3)
The ask ubuntu thread, posted for reference.

---

### Post by mcduck on 2013-01-20
> **jrogge said:**
> I'm running Ubuntu 12.04 with gnome 3 shell. I'm currently using the icon theme Ubuntu mono-dark and I like it but there are just a few icons I want to change. I imagine changing those icons would just be going to some directory and replacing the images, so I looked at /usr/share/icons/ubuntu-mono-dark/ but I'm not sure where to go from there. There are 3 folders there, 16, 22, and 24. In 22 and 24, there are icons that say "audio-volume-low-panel.png" "audio-volume-low.png" etc but none of them are the ones that contain the images that appear when I change the volume through fn-f11 or other fn hotkeys. I looked but I can't find a tutorial for editing an existing icon theme in 12.04, but if there is one please post the link.
Any help is much appreciated.
Icon theme doesn't always have to have it's own images for every icon needed, the themes can also define another theme to inherit from, and then all the missing icons will be pulled form that theme instead. Which is most likely what you are seeing here.

To find the original icon youa re looking for, take a look at the theme's index.theme -file. In the beginning you'll find a line like this:

```
Inherits=Humanity-Dark,gnome,hicolor
```
This means that if an icon isn't found from ubuntu-mono-dark, the system should look if one is available in Humanity-Dark. And if not there, then gnome, and finally hicolor.

This also means that once you have found the correct icon and it's name, you *don't* have to edit any other theme, as soon as you create the icon in the theme you are editing the system will start using it instead of inheriting it from some other theme. (And also you don't actually need to edit an existing theme to change a few icons, you can instead make a new theme of your own, just add the icons you wish to change and then set the theme to inherit from ubuntu-mono-dark ;))

---

### Post by vasa1 on 2013-01-20
> **mcduck said:**
> ... take a look at the theme's index.theme -file. In the beginning you'll find a line like this:

```
Inherits=Humanity-Dark,gnome,hicolor
```
This means that if an icon isn't found from ubuntu-mono-dark, the system should look if one is available in Humanity-Dark. And if not there, then gnome, and finally hicolor.
...
Very helpful ... Thanks!

---

### Post by jrogge on 2013-01-20
> **mcduck said:**
> Icon theme doesn't always have to have it's own images for every icon needed, the themes can also define another theme to inherit from, and then all the missing icons will be pulled form that theme instead. Which is most likely what you are seeing here.

To find the original icon youa re looking for, take a look at the theme's index.theme -file. In the beginning you'll find a line like this:

```
Inherits=Humanity-Dark,gnome,hicolor
```This means that if an icon isn't found from ubuntu-mono-dark, the system should look if one is available in Humanity-Dark. And if not there, then gnome, and finally hicolor.

This also means that once you have found the correct icon and it's name, you *don't* have to edit any other theme, as soon as you create the icon in the theme you are editing the system will start using it instead of inheriting it from some other theme. (And also you don't actually need to edit an existing theme to change a few icons, you can instead make a new theme of your own, just add the icons you wish to change and then set the theme to inherit from ubuntu-mono-dark ;))
I'm confused, which theme should I replace the image in? Should I just dig around in the folders until I find the images?

EDIT: Nevermind, I must have missed the part where you said the order of inheritance. Thank you so much, I'll post the results later today.

---

### Post by dragonfly41 on 2013-01-20
I had a similar problem which I posted here .. if it helps ..

[http://ubuntuforums.org/showthread.php?t=2104483](http://ubuntuforums.org/showthread.php?t=2104483)

---

### Post by jrogge on 2013-01-20
I switched the audio-volume-high.png file in every place Ubuntu-mono-dark inherits but it still is showing the original image? How can I find out where the theme is getting the image so I can change that>

---

### Post by mcduck on 2013-01-20
> **jrogge said:**
> I'm confused, which theme should I replace the image in? Should I just dig around in the folders until I find the images?

EDIT: Nevermind, I must have missed the part where you said the order of inheritance. Thank you so much, I'll post the results later today.

You only should change it in the theme you are editing. The inheritance is used only if an icon doesn't exist in a theme. (This way the theme creators don't need to duplicate every singe image file to create a small variation of a theme, for example a different versions for light and dark panels.)

---

### Post by jrogge on 2013-01-20
> **mcduck said:**
> You only should change it in the theme you are editing. The inheritance is used only if an icon doesn't exist in a theme. (This way the theme creators don't need to duplicate every singe image file to create a small variation of a theme, for example a different versions for light and dark panels.)
I added an image "audio-volume-high.png" to Ubuntu-mono-dark/status/24 but it didn't effect anything. Sorry, I'm pretty new at this stuff, so I'm probably making some obvious mistake.

---

### Post by mcduck on 2013-01-21
> **jrogge said:**
> I added an image "audio-volume-high.png" to Ubuntu-mono-dark/status/24 but it didn't effect anything. Sorry, I'm pretty new at this stuff, so I'm probably making some obvious mistake.

Did you log out & back after changing the icon? Some programs load the icons etc when they are started, and don't detect if you change to a different theme (or edit the theme) after that unless you restart the program. (And logging out and back is the easiest way to do that for all programs).

---

### Post by jrogge on 2013-01-21
> **mcduck said:**
> Did you log out & back after changing the icon? Some programs load the icons etc when they are started, and don't detect if you change to a different theme (or edit the theme) after that unless you restart the program. (And logging out and back is the easiest way to do that for all programs).
I hadn't, but I just did with no change.
Does the size of the image matter? It isn't 24x24, and being in the 24x24 folder might mess it up? I'll try changing the size.

---

### Post by jrogge on 2013-01-21
It still didn't work. :(

---

### Post by dragonfly41 on 2013-01-21
In my earlier post I pointed you to a thread ..

you might have missed this link in the thread

[http://rafalcieslak.wordpress.com/2012/04/21/changing-new-message-indicator-color/](http://rafalcieslak.wordpress.com/2012/04/21/changing-new-message-indicator-color/)

it explains how to edit **[COLOR=DarkRed]*.svg[/COLOR]** format icons using an svg editor Inkscape

gksudo inkscape /usr/share/icons/ubuntu-mono-light/status/22/indicator-messages-new.svg

Does this answer your  question?

---

### Post by jrogge on 2013-01-21
> **dragonfly41 said:**
> In my earlier post I pointed you to a thread ..

you might have missed this link in the thread

[http://rafalcieslak.wordpress.com/2012/04/21/changing-new-message-indicator-color/](http://rafalcieslak.wordpress.com/2012/04/21/changing-new-message-indicator-color/)

it explains how to edit **[COLOR=DarkRed]*.svg[/COLOR]** format icons using an svg editor Inkscape

gksudo inkscape /usr/share/icons/ubuntu-mono-light/status/22/indicator-messages-new.svg

Does this answer your  question?
Oh, the images need to be .svg 's? I was using .png's because I saw them in other themes. Thank you, I'll try this.

---

### Post by jrogge on 2013-01-21
It didn't work, so I'm going to post exactly what I did.
1. I created a 16x16 image in inkscape and named it audio-volume-high.
2. Imoved it into /usr/share/icons/ubuntu-mono-dark/status/16 relogged in, then tried changing the volume through fn-f12
3. It didn't work, so I put audio-volume-high.svg in .../status/22 and .../status/24 too, relogged in, and tried again. It still didn't work.

Do I need to put the audio-volume-high in the themes ubuntu-mono-dark inherits from as well?

---

### Post by mc4man on 2013-01-21
> **jrogge said:**
> I'm running Ubuntu 12.04 with **gnome 3 shell**.

I don't have 12.04 but at least in 13.04 gnome-shell does not use  Ubuntu mono-dark icons in it's **panel**
So you may need to find out where Gs gets it's icons for the panel
(could be built-in??, no clue

---

### Post by jrogge on 2013-01-21
> **mc4man said:**
> I don't have 12.04 but at least in 13.04 gnome-shell does not use  Ubuntu mono-dark icons in it's **panel**
So you may need to find out where Gs gets it's icons for the panel
(could be built-in??, no clue
I'm not trying to change the panel icons, though. I'm trying to change the image that pious up when I change the volume or screen brightness through fn keys.

---

### Post by mcduck on 2013-01-21
> **jrogge said:**
> It didn't work, so I'm going to post exactly what I did.
1. I created a 16x16 image in inkscape and named it audio-volume-high.
2. Imoved it into /usr/share/icons/ubuntu-mono-dark/status/16 relogged in, then tried changing the volume through fn-f12
3. It didn't work, so I put audio-volume-high.svg in .../status/22 and .../status/24 too, relogged in, and tried again. It still didn't work.

Do I need to put the audio-volume-high in the themes ubuntu-mono-dark inherits from as well?
no, definitely not. You never need to change any of the inherited themes. That would be the exact opposite of what the  inheritance is used for. :D Like I've already said, the inheritance is only used if the theme itself doesn't have a particular icon.

Anyway, I think your problem is that you are using wrong icon name & location. After taking a look through some icon themes, I'm quite sure the names used for the volume notification popups are "status/scalable/notification-audio-volume-high", "status/scalable/notification-audio-volume-low" and so on. (I might be wrong, though, finding out the correct name each application uses for it's icons can be quite tricky. As you have probably noticed most themes have quite many copies of each icon linked to different names ;))

---

### Post by mc4man on 2013-01-21
> **jrogge said:**
> I'm not trying to change the panel icons, though. I'm trying to change the image that pious up when I change the volume or screen brightness through fn keys.If what was mentioned in previous post proves unfruitful then for a Gs session you may want to take a look in /usr/share/icons/gnome/scalable/status

*though at least here on a more recent Gs both the panel & respective notification are using the same icon(s)

---

### Post by jrogge on 2013-01-21
Ubuntu-mono-dark doesn't have a scalable folder in status, so I created one put notification-audio-volume-high.svg in it, relogged, and it still didn't work. Do I need to have the full icon set, like for low, medum, and muted as well?

---

### Post by jrogge on 2013-01-21
The only thing bothering me was this:
[http://i.imgur.com/OaJYndv.png](http://i.imgur.com/OaJYndv.png)
which I can just deal with, since it seems nothing is working.

---

### Post by mcduck on 2013-01-22
> **jrogge said:**
> Ubuntu-mono-dark doesn't have a scalable folder in status, so I created one put notification-audio-volume-high.svg in it, relogged, and it still didn't work. Do I need to have the full icon set, like for low, medum, and muted as well?

JUst having one icon with correct name, size & location should be enough, at least you'd be able to confirm that the name is correct and then add the other icons.

When you created the "scalable"-directory, did you add it to the index.theme file?

---

### Post by jrogge on 2013-01-22
No, I had not. To do that, I just add "status/scalable" to the variable directories?

---

