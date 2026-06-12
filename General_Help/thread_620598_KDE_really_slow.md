---
title: "KDE really slow"
date: 2007-11-22
forum: General Help
---

### Post by mister_pink on 2007-11-22
I've been running ubuntu for a while now, and the other day decided to try kde. I did an apt-get install kubuntu-desktop, and all worked fine. However kde is completely unusable. Programs and that run fine, but if I click on the main menu at the bottom it takes an age to draw each item individually. It can take up to a minute for the menu to appear. The same happens if I right click the desktop or anywhere else on the panel. 

Also, this is unrelated but doesn't really warrant its own thread - on startup and shutdown I now get the kubuntu loading splash rather than ubuntu - how do I change it back?

---

### Post by mister_pink on 2007-11-23
I absolutely hate doing this, but, anyone? I don't think there's anything else helpful I can say but if the contents of some file or the output of something would be useful then I can do that. Nothing to do with the ATI restricted drivers maybe?

---

### Post by firedancer on 2007-11-23
try a clean install instead and see wether problem persist , i just did , 

i wanted try out xubuntu , but was getting some trouble and didn't really liked it i changed back to kde,



good luck

---

### Post by kellemes on 2007-11-23
> **mister_pink said:**
> I absolutely hate doing this, but, anyone? I don't think there's anything else helpful I can say but if the contents of some file or the output of something would be useful then I can do that. Nothing to do with the ATI restricted drivers maybe?

Do you get the same result when loading Gnome from the current install?
I remember having this when I load fglrx + xgl without a composite manager..
Maybe you can browse /var/log/Xorg.0.log for hints..

---

### Post by knutschr on 2007-11-23
```
sudo apt-get remove xserver-xgl
```

This often works :-)

---

### Post by mister_pink on 2007-11-24
Gnome runs just fine. I've tried xubuntu now and that works well too, although it wont let me change my keyboard layout! It keeps reverting to default for some reason.

Since I was just playing, I've decided I want to remove kde completely for now. Doing apt-get remove kubuntu-desktop doesn't remove all the other stuff that came with it. Is there an easy way to remove the whole lot?

Edit: I did the thing on the psychocats website. Scary stuff. Seems to have removed everything though.

---

### Post by mister_pink on 2007-11-24
One last thing please- it seems to have removed all my audio codecs! Rhythumbox won't play anything in any format! What package do I need to install?

---

