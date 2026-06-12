---
title: "Hardy Heron ... Keyboard Vs nvidia-xconfig"
date: 2008-05-06
forum: General Help
---

### Post by JoaquimPosses on 2008-05-06
I'm having a serious problem which is keeping me trapped in Window$...

I have a nvidia MX400 graphic card and put it running smoothly enough without even using gnome-terminal (the "path" was admninistration > hardware drives or something like it...)
with it I was able to choose a usable screen resolution (the "real" resolution of my monitor is 800X600, which is far beyond crap...)

The problem is that once I got the screen resolution I want, my keyboard layout changes... it ends up being something different than what I use most (abnt2 - the standard layout for brazilian keyboards...) ... so, after walking around forums, I edited the xorg.conf (the new lines are at the end of this post...) to put the keyboard working... Then I restart and strange things happen: 1. the nvidia logo doesn't shows; 2. I get a messagen saying "something went wrong" with graphics; 3. my layout is correct, but the screen resolutions is wrong.

I figured out that nvidia-settings only "accepts" the xorg.conf that it creates... even when I change only the lines of Section Input Device Identifier (the keyboard) it doesn't works properly and when I create a new xorg.conf as nvidia X configuration asks I end up with the wrong layout...

Anyone can help? please? I REALLY won't go back to feisty and windows is not my idea of efficiency and ease of use...

The lines of xorg.conf which makes my keyboard works...
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "abnt2"

---

### Post by jimv on 2008-05-06
Have you tried configuring hte keyboard layout in System>Preferences>Keyboard?

---

### Post by JoaquimPosses on 2008-05-08
Yes, I did.
But when I have xorg.conf wrote by nvidia-settings, my layout (generic/ant2/brazilian) doesn't show up. What I find in the GUI (system>preferences>keyboard layout) is Generic/USA...

Then, when I manually edit the xorg.conf, making the screen resolution drop back to 800X600, my correct option of layout is automatically chosen when I take a look in the keyboard layout.

off-topic: how can I activate automatic e-mails for responses on my threads? I thought it was on in my User CP...

---

### Post by JoaquimPosses on 2008-05-08
Fixed. I tried again with system>preferences>keyboard layout. Added a new standard and deleted the USA, so ending up with only one (the one I need...) and it worked... reboot and login and both screen resolution and keyboard layout come right... thanks for the tip

---

