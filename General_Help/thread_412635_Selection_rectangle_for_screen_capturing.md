---
title: "Selection rectangle for screen capturing"
date: 2007-04-18
forum: General Help
---

### Post by geokker on 2007-04-18
I've recently returned to Linux land from a short stint as a reasonably happy Mac user. With Eft and compiz, I've  got most of the features I've become accustomed to. One time saver I'm still missing however is the ability to draw a selection box around a region of the desktop to capture as a picture (preferably a .png). On a Mac, the options for screen capture are:

[LIST]
[*]entire screen
[*]window
[*]selectable region
[/LIST]

All to a file or the clipboard.

I've figured out the first 2, but how to capture a region baffles me. If this isn't a Gnome feature, is there a program to allow me to do this?

As it is, I'm having to crop captures in Gimp, which is needlessly (I hope) time consuming.

---

### Post by beerorkid on 2007-04-18
[imagemagick]("http://www.imagemagick.org/script/index.php") would do this for you no problem.  I use it for that reason all the time.

```
sudo apt-get install imagemagick
```

then to use open up a console / terminal and type:

```
import filename.extentionyouwant
``` example ```
import puppy.png
```

makes your cursor into a + sign which will let you crop out what you want.

I really enjoy it cuz it makes no difference what you want to capture.  I have used it on flash vids, remote desktop connections, basically anything on the screen.

The import command is just one of the many other options imagemagick can do.  Great for resizing bunches of pictures at once.

---

### Post by geokker on 2007-04-18
AWESOME! That's actually exceeded my best expectation - thanks muchly!

---

