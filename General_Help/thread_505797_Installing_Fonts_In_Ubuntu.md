---
title: "Installing Fonts In Ubuntu"
date: 2007-07-20
forum: General Help
---

### Post by The Wisedude on 2007-07-20
Hello.. 

Me and my friend are having a little bit of trouble, we both like to make stuff in GIMP..

But we are still curious on HOW do you install new fonts in Ubuntu?

Eg. Like a .ttf..

Thanks for all your help :),

---

### Post by yabbadabbadont on 2007-07-20
Open a terminal window and run:
```
mkdir .fonts
```
Note that it starts with a period.  This makes the directory hidden.  Copy your ttf fonts into this directory and they should then be available for use.  You may need to logout and back in for them to show up, but some people report that they show up immediately.

---

### Post by The Wisedude on 2007-07-20
Yes thank you very much!
Just one quick question..

If I make a "."fonts

directory, how in the world will I actually add fonts to it, because all folders that start with "." disappear :(.?

---

### Post by yabbadabbadont on 2007-07-20
In nautilus, View->Show hidden files.  (or hit Ctrl-H to toggle their visibility)  :D

---

### Post by The Wisedude on 2007-07-20
> **yabbadabbadont said:**
> In nautilus, View->Show hidden files.  (or hit Ctrl-H to toggle their visibility)  :D

Thank you very much!

---

### Post by midgetporn on 2007-08-11
In my home folder, I only have .fontconfig folder. If I wanted to install a .ttf font would this be the folder I would install it in? I also want to use this new font in the GIMP Image Editor.

---

### Post by Majorix on 2007-08-11
No you have to create a .font folder. Because as the name implies .fontconfig is more about the configuration.

---

### Post by yabbadabbadont on 2007-08-11
> **Majorix said:**
> No you have to create a .font folder. Because as the name implies .fontconfig is more about the configuration.

Actually, the name of the folder is ".font**s**".  Plural.  ;)

---

### Post by SaiGoN DraGoN on 2007-08-28
Thanks for the tip;
for all other newbies like myself that want to get more fonts in ubuntu check this page [http://1000fonts.com]("http://1000fonts.com")  download them, unzip them and cut, paste into the .fonts directory that you already created.
Or if you have a windows partition like i do, just browse through windows to the fonts folder, copy and paste the same way i already told you about.
Good luck !!!!  :)

---

