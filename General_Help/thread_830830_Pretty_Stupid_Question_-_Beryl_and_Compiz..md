---
title: "Pretty Stupid Question - Beryl and Compiz."
date: 2008-06-16
forum: General Help
---

### Post by ForksHolder on 2008-06-16
Hello,
I remember that long time ago i used beryl until the compiz fusion came.
Well, ofcourse compiz is much better (fester, stable, and so on), but there is a small thing i miss in Beryl.

You remember Beryl's logo? This small red diamond who appeared in the panel?
This is what i miss!

My question is:

Is there any way to put a red diamond in the panel? It makes me feel powerful :)

Thanks,
ForksHolder.

---

### Post by angry_johnnie on 2008-06-16
There's **fusion-icon**. (in hardy repos)

It does pretty much the same as beryl-manager, although it's not a diamond, just a little blue cube. :-)

---

### Post by ForksHolder on 2008-06-16
Aha.. :P

And is there any way i can change the picture?

---

### Post by angry_johnnie on 2008-06-16
hahaha you really want that diamond?

I guess (i'm really guessing :-)) you could edit the .desktop file.

It's located in **/usr/share/applications/fusion-icon.desktop**

I used cat to see what's in it, and it says **Icon=fusion-icon**.

You could try this in terminal:

```
sudo nano /usr/share/applications/fusion-icon.desktop
```

find the Icon line

and replace fusion-icon with any other icon you want (with a full path).

Then you can just save the changes (ctrl + o, and then enter), and exit (ctrl + x).

Edit:  you know what's **a lot** easier?  You could just get the diamond icon, put it in /usr/share/pixmaps and rename it to fusion-icon.  It should do it. :-)

---

### Post by ForksHolder on 2008-06-16
Bah, It doesn't work. It shows the same logo.

Although, when i run it through Alt+F2 it shows the beryl logo.. but not in the panel.

Idea?

---

### Post by angry_johnnie on 2008-06-16
> **ForksHolder said:**
> Idea?


Actually... yes :p

First of all, the icon you want (the beryl diamond) has to be in xpm format, and located at /usr/share/pixmaps.

I think you can convert it with the gimp.
I know you can convert it with imagemagick.

If you have imagemagick, do:
```

convert /original/image.png /new/image.xpm
```

given the original image is a .png... otherwise, just replace that.

Once it's xpm, put it in /usr/share/pixmaps.

Now, open a terminal and type:
```

gksu gedit /usr/lib/python2.4/site-packages/FusionIcon/interface_gtk/main.py
```

somewhere near the end of that text file, you'll see this:

```
icon = gtk.status_icon_new_from_icon_name('fusion-icon')
```

replace ('fusion-icon') with ('your-new-icon').

I was curious and wanted to be sure, so I went and replaced it with the gambas2 icon.  And it worked. :-) (i got a fish in the system tray).

You must really like that diamond, huh? :-)

---

### Post by ForksHolder on 2008-06-16
> gksu gedit /usr/lib/python2.4/site-packages/FusionIcon/interface_gtk/main.py

There is no such file... Are you sure this is it?

> You must really like that diamond, huh? :)

Yup, I do. ^^

---

### Post by angry_johnnie on 2008-06-18
:o I'm very sure that's the one.  I just double checked it, thinking it might have been a typo, but no... That's the one...  Maybe you just have a different version of fusion-icon... or a different version of python, maybe?

Try replacing **python2.4** with **python2.5** or **python2.3**.

I'm pretty certain you must have at least one of those, otherwise fusion-icon wouldn't even work... It depends on python, and other python-related stuff.  :-)

---

### Post by ForksHolder on 2008-06-30
Thanks, Sloved ^^

---

