---
title: "masses of folder icons on de PLUS extra &quot;default&quot; apps"
date: 2013-07-09
forum: General Help
---

### Post by DouglasAdams on 2013-07-09
i installed ubuntu on a friends machine then added the xfce desktop using:
```

sudo apt-get install xfce4

```
as he wanted all the ubuntu apps but with a simple(r) de.

we now have two problems:

1)
just about every sub in his home folder has an icon on the de which i can't find a setting to remove - HELP please!

2)
the ubuntu default apps have changed.
i don't mind most of them (i actually prefer xfburn!) but i really don't like the default file mangers for Xubuntu (& Lubuntu too)
- give me Nautilus every time.

i was thinking, if i had installed Xubuntu (or Lubuntu) and then added the Ubuntu desktop
 (with, i guess:

```

sudo apt-get install ubuntu-desktop)

```

would i have been closer to what i actually wanted, i.e. the heavier Ubuntu apps but the light desktop?

many thanks

---

### Post by duanedesign on 2013-07-09
Changing your folder icons:

Right-click on the icon and select properties.
Under the basic tab click on the icon.
A window will open and navigate to  /usr/share/icons.
Here you can navigate all the icons installed.  (I found my default folder icon at /usr/share/icons/Humanity/places/48/folder.svg



Using Nautilus with XFCE (I found  a couple solutions. I apologize I could not test thesse and post the one that I found works best.):

Sol1: This thread assumes you did not start with Ubuntu so some of these packages you will not need to install. Which ones should be obvious)[ http://ubuntuforums.org/showthread.php?t=1854209]("http://ubuntuforums.org/showthread.php?t=1854209")

Sol2: Well, it might be considered a dirty hack but it has worked for me in gnome before so it should also work in xfce.  Just edit the thunar.desktop file in /usr/share/applications and replace the Exec=thunar to Exec=nautilus --no-desktop and save the file.  Then any time thunar is launched, nautilus will be launched instead.

Sol3: Otherwise, you can edit the menu with the menu editor and change the File manager command and do the same in the panel icon properties.

---

