---
title: "how to display chinese/japanese characters?"
date: 2007-05-03
forum: General Help
---

### Post by live4nothing on 2007-05-03
I did a minimal install of the ubuntu using the server version. Then I apt-get x, xfce, and other components that i think i need. Everything works fine except firefox won't display Chinese and Japanese characters. Can any one please let me know which packages should i get so firefox can display chinese/japanese character? Thanks in advance

---

### Post by nebousuru on 2007-05-03
> **live4nothing said:**
> I did a minimal install of the ubuntu using the server version. Then I apt-get x, xfce, and other components that i think i need. Everything works fine except firefox won't display Chinese and Japanese characters. Can any one please let me know which packages should i get so firefox can display chinese/japanese character? Thanks in advance

If you are having trouble displaying characters on a particular site, try View -> Character Encoding ->More Encoding -> East Asian -> [then pick one for whatever language].  You may need to try each of the several different encodings for each language,   and also try UTF-8  (View -> Character Encoding ->More Encoding -> Unicode ->UTF-8 )


If you are running in graphical mode, try enabling support for the language in System -> Administration -> Language Support, and click the box coresponding to the language you want

A guide to type in japanese is at: [[COLOR="Blue"]Japanese Input and Fonts in Ubuntu 7.04[/COLOR]]("https://help.ubuntu.com/community/Japanese_Input_and_Fonts_in_Ubuntu_7%2e04"); it also adds fonts and such, might help too.  If you use this guide, note that you don't have to modify the ~/.font file like it says.  I didn't like the new default english font



This worked for me, but i used a full install of the normal Ubuntu desktop.  there might be something else you are missing

---

### Post by live4nothing on 2007-05-07
i installed iceWM instead of Gnome, so the menu item you mentioned isn't there. I tried to add more language in firefox, as well as install chinese language supports, chinese fonts for X. Still can't solve it. Anymore help? I really don't want to mess up anything because after days, i finally got everything setup the way i want, all except displaying asian characters. I would really appriciate any help. Thanks

---

### Post by maikunari on 2007-09-11
I have the exact same problem as live4nothing, I've installed icewm, got everything set up nicely, scim is installed and running, but can't display japanese fonts, all japanese appears as weird little blocks, when try to use scim as well.

Any help would be greatly appreciated.
Thanks,

maikunari

---

### Post by dividebyzero on 2007-09-14
Try the following:

System->Administration->language support

On the dialog box, check whatever language you want and make sure "Enable support to enter complex characters" is checked. (I usually check Chinese, Japanese and Korean). SCIM needs to be restarted to work.

---

### Post by leetrefz on 2007-09-15
I'm on Mint xfce and have the same problem. have checked & installed chinese, checked support for complex characters, have a input selector thing in the bar, but it only inputs unicode boxes instead of readable chinese. have tried default character encoding in firefox but no. 

if it's fonts i/we need how do i get them?

---

### Post by maikunari on 2007-09-16
Thanks for your reply dividebyzero, but under icewm the menus are quite different from under straight ubuntu with gnome, I installed Japanese support through the terminal but I am having the same problem as you leetrefz, the input selector bar thing works find, but it only makes unicode boxes.  I installed a bunch of fonts and rebuilt the font cache as per this tutorial: [https://help.ubuntu.com/community/Japanese_Input_and_Fonts_in_Ubuntu_7.04](https://help.ubuntu.com/community/Japanese_Input_and_Fonts_in_Ubuntu_7.04)
but still no luck.
Any ideas?

---

### Post by maikunari on 2007-09-17
Found a solution, simply install ttf-kochi-mincho package!

> apt-get install ttf-kochi-mincho 

---

### Post by leetrefz on 2007-09-17
That's cool. 

Personally I couldn't find any ttf- chinese fonts. I've synaptic'd all the fonts I can find, still getting boxes. inputing boxes. woo.

Restarting firefox got it working in Chinese, huzzah. right now I can input chinese sort of, but can't tell what I'll input because the selector is still in unicode. I guess a restart will fix that tho.

---

### Post by macjones on 2007-09-21
these chinese ttf fonts may work for you...

apt-get install ttf-arphic-uming

---

