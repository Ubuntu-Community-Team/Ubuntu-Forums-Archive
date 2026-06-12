---
title: "ubuntu screensaver lock dialog"
date: 2005-04-04
forum: General Help
---

### Post by rocco on 2005-04-04
Hi all,

I need to change the ubuntu image on the xscreensaver lock dialog.
It's amazing, but in my company my boss want's our logo.

Can anyone help me?
(Ps. sorry about my poor english.)

Marcos Antonio Dellazari
[www.psl-trinacional.org](www.psl-trinacional.org)
Brazil

---

### Post by ksaling on 2005-05-11
I need to do the same thing.  Has anyone figured this out?

---

### Post by lt_kije on 2005-05-11
You could try changing the program that's run when xscreensaver itself starts up. This link [http://www.jwz.org/xscreensaver/faq.html#slideshow](http://www.jwz.org/xscreensaver/faq.html#slideshow) should help you. Basically, you need to edit ~/.xscreensaver, add a line in the "Programs" directive, and you're done.

HTH,

lt_kije

---

### Post by ksaling on 2005-05-16
Following up with the solution...

Oliver Grawert [1] is the author of the Ubuntu xscreensaver hack.  He gave me this clue...

"grab the source and look at the theme.h and lock.c files for the file logo.xpm, after a recompile you will see your new logo... but beware, the windowborder may need adjustments..."

Thanks Oliver!  Hope that helps someone else.

[1] [http://www.ubuntulinux.org/wiki/OliverGrawert](http://www.ubuntulinux.org/wiki/OliverGrawert)

---

### Post by ksaling on 2005-05-16
Maybe I am doing something wrong, but I grabbed the original source, plus the diff file.

[http://archive.ubuntu.com/ubuntu/pool/main/x/xscreensaver/xscreensaver_4.16.orig.tar.gz](http://archive.ubuntu.com/ubuntu/pool/main/x/xscreensaver/xscreensaver_4.16.orig.tar.gz)
[http://archive.ubuntu.com/ubuntu/pool/main/x/xscreensaver/xscreensaver_4.16-1ubuntu11.diff.gz](http://archive.ubuntu.com/ubuntu/pool/main/x/xscreensaver/xscreensaver_4.16-1ubuntu11.diff.gz)

I unzipped the diff file. I untarred the original and cd'd into that directory.  

I applied the diff with:
  patch -p1 -i ../xscreensaver_4.16-1ubuntu11.diff

I see ./driver/lock.c, which has this reference:
  #include "theme_logo.xpm"

I also see ./driver/theme.h but it has no reference to "theme_logo.xpm".

So, as a test, I created a .xpm graphic file exactly the same size as the existing "theme_logo.xpm" (221x51 pixels).  I overwrote the existing theme_logo.xpm with my new one.

Now, I did `./configure` then `make`.  Neither generated any serious errors.  So, I did `make install` which also ran without errors.

When I launch xscreensaver, then lock the screen it works, but when I move the mouse to get the unlock dialog, xscreensaver crashes without a helpful error message.

Here's an example:
$ xscreensaver
xscreensaver: 12:02:40: 0: child pid 8234 (<unknown>) exited abnormally (code 0).
Aborted
$

Hmmm, do I need to make additional changes somewhere?  I am doing something wrong?

---

### Post by AndThenWhat on 2008-07-22
Dunno if anyone wants this in Hardy but to change the picture in Hardy Heron using gnome-screensaver:

- Open the "/usr/share/gnome-screensaver/lock-dialog-default.glade" file in a text editor.

- Look for the section <widget class="GtkImage" id="ubuntu-logo"> if it doesn't exist create it like so:

```
<widget class="GtkImage" id="ubuntu-logo">
                            <property name="visible">True</property>
                            <property name="events">GDK_POINTER_MOTION_MASK | GDK_POINTER_MOTION_HINT_MASK | GDK_BUTTON_PRESS_MASK | GDK_BUTTON_RELEASE_MASK</property>
                            <property name="pixbuf">ubuntu-whatever.png</property>
                          </widget>
```

- Otherwise in that section add a new property like so containing your image:

<property name="pixbuf">ubuntu-whatever.png</property>

:guitar:

---

