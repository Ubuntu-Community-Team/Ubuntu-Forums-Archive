---
title: "How to set the same theme on Ubuntu 20.04 like it was on Ubuntu 18.04?"
date: 2020-08-14
forum: General Help
---

### Post by abcuser on 2020-08-14
Today I have upgraded Ubuntu 18.04 to Ubuntu 20.04. One of the first things I really don't like is the theme. I would like to have the same!!! theme like it was in Ubuntu 18.04.

I know I can change theme in Settings application in Appearance and then Light/Standard/Dark, I don't like non of them. I also installed Tweaks application and in Appearance there are different themes but non of them I like.

I really loved the theme in Ubuntu 18.04, combination of purple and grey.

1. The first thing I don't like now is boot splash menu is now black, but it was beautiful purple before.
2. I don't like title bar black - I liked dark grey one.
3. I don't like black in menus bar.
4. I don't like terminal background color.

I have learned I can change colour settings in file: ~/.config/gtk-3.0/gtk.css but this is not simple to change, because I don't know the settings names and values.

So in short, how to get the theme colours in Ubuntu 20.04 the same as they were in Ubuntu 18.04?
Regards

---

### Post by Dennis N on 2020-08-14
_Terminal Background:_

Options Button > Preferences > Click on current profile (probably called 'unnamed;') > uncheck: 'use colors from system theme'

Then you are free to pick your own colors from the numerous options below that. (see attachment)

Window Title Bar is determined by Application Theme.

It's unclear what is meant by:
boot splash menu
menus bar

---

### Post by abcuser on 2020-08-14
Dennis N,
- boot splash menu. Better wording: GRUB menu is now black background, it was purple backgroud
- menus bar, see picture:
[IMG]https://i.imgur.com/CV6W1Bu.png[/IMG]

---

### Post by Dennis N on 2020-08-15
The Firefox title bar is determined by your application theme. Use the same theme as your previous Ubuntu, or try another theme. 

The Firefox menu bar appearance is part of the Firefox theme. To see all Firefox themes, go here:
 
[https://addons.mozilla.org/en-US/firefox/themes/](https://addons.mozilla.org/en-US/firefox/themes/)

The grub menu default background is indeed black but was purple in 19.10. At the moment, I'm not sure where that color is set. Another way to get a solid color background for grub menu is to create a .png image of the solid color you want, copy it into /boot/grub, and run** sudo update-grub** in your terminal.

---

