---
title: "Where desktop background info is stored..."
date: 2008-06-21
forum: General Help
---

### Post by Th3Professor on 2008-06-21
I noticed that when you select a background it sets it based on where the current file is located, so if you move it you lose it as a background - or maybe that's right - anyway, my question is about this...

When you right-click on the desktop, select "change desktop background", and see the various images that are reserved for backgrounds...

Is there a specific folder that stores all of those background images (or at least links to them)?

---

### Post by mc4man on 2008-06-21
/usr/share/backgrounds

---

### Post by Th3Professor on 2008-06-22
good to know... however... I only have 14 files listed there (default with the system). I have others that show up in the "change desktop background" window that are not present in that directory. (using ls -a (even with sudo, though no difference)). Any idea about the ones I've added?

---

### Post by mc4man on 2008-06-22
> I have others that show up in the "change desktop background" window no idea really though any image that can be found in that window should show path when moused over.

---

### Post by plucky on 2008-06-22
Open a terminal and input ```
locate backgrounds
```

I get > /usr/share/pixmaps/backgrounds/cosmos

also contains background images.

Good Luck

---

### Post by Th3Professor on 2008-06-22
Nope... still didn't do it... though the cosmos images are pretty neat lol. Still trying to find the big list.

---

### Post by him610 on 2008-06-22
> I only have 14 files listed there (default with the system). I have others that show up in the "change desktop background" window that are not present in that directory.

The system is probably showing other png or jpg files elsewhere in the file structure.

Any particular background not found in /usr/share/backgrounds that you would like to use and not lose can be copied to the /usr/share/backgrounds directory.

Cheers.

---

### Post by sdennie on 2008-06-22
They aren't stored in a specific directory.  They are stored in ~/.gnome2/backgrounds.xml.  However, you can find and change the current background using:

```

gconf-editor

```

Navigate to /desktop/gnome/background/picture_filename.  You can also change this value from the command line.  For example, to change it to /usr/share/backgrounds/space-01.jpg:

```

gconftool-2 --type string --set /desktop/gnome/background/picture_filename /usr/share/backgrounds/space-01.jpg

```

---

### Post by Th3Professor on 2008-06-22
cool!

---

