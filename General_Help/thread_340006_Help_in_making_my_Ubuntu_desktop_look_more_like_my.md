---
title: "Help in making my Ubuntu desktop look more like my Xp one!"
date: 2007-01-16
forum: General Help
---

### Post by PRGUY85 on 2007-01-16
Hey there:

I love Ubuntu, yet maybe it is because I have been using Windows XP for a longer period of time that my XP desktop looks better than my Ubuntu one.  Here is a pic of my current Xp desktop:

[IMG]http://img522.imageshack.us/img522/3263/windowsxpwv3.jpg[/IMG]

I want to know how to add cool widgets like the ones I use with the Yahoo Widgets (Konfabulator) program as well as adding that glossy black taskbar which I cant find a proper gif image to use for it.

By the way my current Ubuntu desktop looks like this:

[IMG]http://img361.imageshack.us/img361/7338/desktopro0.png[/IMG]

---

### Post by PRGUY85 on 2007-01-16
Darn, sorry about the large pics...

---

### Post by ardchoille42 on 2007-01-16
Your Windows desktop looks quite nice. Here's some info about how to get started making your Ubuntu desktop look like that:

1) I would recommend installing and using superkaramba.. it's in the universe repo so you should be able to enable universe and do: "sudo apt-get install superkaramba" to get it. Superkaramba provides widgets for the dekstop and there are some outstanding ones. More info about enabling repos can be found [here]("https://help.ubuntu.com/community/Repositories").

2) There are lots of cool gnome themes at: [Gnome Look]("http://gnome-look.org") and [Gnome Art]("http://art.gnome.org").

3) You could use KDE as I think the KDE desktop has more eye candy and better themes, but others may feel differently :)

Some GTK2 (gnome) themes are [here]("http://www.gnome-look.org/index.php?xcontentmode=100")

Hope this helps you on your way.

---

### Post by PRGUY85 on 2007-01-16
Any idea on the glossy taskbar with black? or maybe dark grey or something?  Its just the Xp desktop looks so darn glossy haha

---

### Post by ardchoille42 on 2007-01-16
> **PRGUY85 said:**
> Any idea on the glossy taskbar with black? or maybe dark grey or something?  Its just the Xp desktop looks so darn glossy haha

Your panels (the taskbar at the top and bottom) are taken care of by the GTK2 themes, of which I supplied a link in my earlier post. The window borders in your windows are taken care of by Metacity themes. Metacity is the default window manager in gnome.

Search these two pages to find some themes that suit you:

[GTK2 themes]("http://www.gnome-look.org/index.php?xcontentmode=100")

[Metacity themes]("http://www.gnome-look.org/index.php?xcontentmode=101").

The best way to install new themes is to unpack them and copy them to the following loactions:

~/.themes - themes for your user only
/usr/share/themes - themes for all users (system-wide)

It doesn't matter where you copy them to, but keep in mind that the gnome-theme-manager installer has problems with multi-theme tarballs, so I recommend to install them manually.

---

### Post by PRGUY85 on 2007-01-16
I have my borders done by Beryl so I am good with that.

---

### Post by ardchoille42 on 2007-01-16
How about these?: 
[http://www.gnome-look.org/content/show.php?content=49179](http://www.gnome-look.org/content/show.php?content=49179)
[http://www.gnome-look.org/content/show.php?content=46153](http://www.gnome-look.org/content/show.php?content=46153)
[http://www.gnome-look.org/content/show.php?content=45829](http://www.gnome-look.org/content/show.php?content=45829)
[http://www.gnome-look.org/content/show.php?content=44925](http://www.gnome-look.org/content/show.php?content=44925)

---

### Post by rsh67 on 2007-12-12
fellas just check out Ubuntu Studio, you can install the theme without reloading the OS to get it.
[http://ubuntustudio.org/screenshots](http://ubuntustudio.org/screenshots)
here is a link to the process (simple really)
[http://yogharp.wordpress.com/2007/05/11/ubuntu-studio-theme-black-sexy/](http://yogharp.wordpress.com/2007/05/11/ubuntu-studio-theme-black-sexy/)
follow the instructions, if you are running Gutsy, just find/replace the Feisty with Gutsy

you will then need to go to system-preferences-appearence to select the studio theme, by the way be sure to go into the login screen while you are tinkering with it and select the studio login theme, its so much better than the "Human orange, tannish brown" theme 

its the best theme I have seen for Ubuntu

][v][rCl3an
~out

---

