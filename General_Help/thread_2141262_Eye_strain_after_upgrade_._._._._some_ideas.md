---
title: "Eye strain after upgrade . . . . some ideas?"
date: 2013-05-02
forum: General Help
---

### Post by edcv on 2013-05-02
Hi all,

I have Ubuntu 13.04 and a problem with my screen after installing gnome 3.8.

I started by installing the gnome-shell and everything was fine. 
Then after I installed :ubuntu-gnome-desktop

I noticed immediately that the font in the top bar was much sharper than usually in both gnome 3.8 and unity. 
Now when I run gnome or unity I get terrible eye strain. 
A pic, but maybe it is hard to see from it.
I[ATTACH=CONFIG]242078[/ATTACH]

IS there someone else that has had this problem?

My dpi settings
xrdb -query | grep dpi
Xft.dpi:    96
xdpyinfo | grep dots
  resolution:    90x88 dots per inch

I have modified the xdpyinfo using xorg.conf to 120x120 but that has no effect on the font
size in gnome.

I have basically tried everything (I think) , except from reinstalling ubuntu. 
Tried nvidia drivers from 3.04, 3.10 and 3.13. Uninstalling gnome 3.8 has no effect. This is probably some setting somewhere but I'm out of ideas.

It is hard to describe this but I get tired after only 30 min of using the computer vs whole day before.

Some ideas?

---

### Post by edcv on 2013-05-02
The fonts are actually quite okay when at the login screen.
After I log in I see the fonts changing and becoming extremely sharp.

---

### Post by pootan on 2013-05-02
Have you tried changing the font setting in gnome tweak tool?

---

### Post by edcv on 2013-05-02
Yes I have, but not sure what to modify there. The fonts are the same as I have at home and it works fine there, so I think the problem is with something else. 

Currently I have 
Text scaling factor 1.0
Hinting: slight
Antialiasing Rgba

Default font: Ubuntu 11
Document font Sans 11
Monospace font Ubuntu Mono 13
Window title font Ubuntu Medium 11

---

### Post by pootan on 2013-05-02
The **Hinting** setting is usally one of the first I change to 'full' on any Ubuntu based install and has a big effect on system fonts. Since you mention sharpness maybe this will have some effect. If not, I wish you luck to fix your problem.

---

### Post by edcv on 2013-05-02
It becomes a little bit better by modifying the hinting but does not fix it. 
The fonts in the top bar are still much sharper and smaller than before :(

---

### Post by sgage on 2013-05-02
> **edcv said:**
> Yes I have, but not sure what to modify there. The fonts are the same as I have at home and it works fine there, so I think the problem is with something else. 

Currently I have 
Text scaling factor 1.0
Hinting: slight
Antialiasing Rgba

Default font: Ubuntu 11
Document font Sans 11
Monospace font Ubuntu Mono 13
Window title font Ubuntu Medium 11

Try grayscale antialiasing - it is better than RGB on my rig.

---

### Post by edcv on 2013-05-02
Thanks for the tip!
I tried that for and after a while I noticed my emails where not as easy to read. So Rgba worked better. But a nice suggestion.

I removed /usr/share/gnome-shell/theme/gnome-shell.css and installed gnome-shell again.
That increased the size of some of the text. 

Also by adding ubuntu to 
stage {
    font-family: ubuntu, cantarell, sans-serif;
    font-size: 11pt;
    color: white;
}
in gnome-shell.css the text became more consistent and the notification text at the bottom became larger but the text showing the software on the left, when hovering over the buttons became smaller again.

There seems to be something in the .css files for the gnome shell.

---

### Post by edcv on 2013-05-03
Doesn't seem to be the .css file. I took the gnome-shell.css file I have at home. I have a screen there with the same resolution / inch and it looks much better there. Something else that is messing with my screen and fonts.

---

