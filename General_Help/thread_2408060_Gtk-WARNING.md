---
title: "Gtk-WARNING"
date: 2018-12-13
forum: General Help
---

### Post by drumanart on 2018-12-13
Hello.

I have a new installed Ubuntu Studio 18.04

Opening any application using the terminal I get a warning:

> 
(gedit:8404): Gtk-WARNING **: 19:24:27.350: Theme parsing error: gtk.css:4549:12: Expected a string.


But if I do:
**GTK_THEME=Radiance** gedit // delcearing a theme the app, opens without warning.


Many thanks Martin

---

### Post by drumanart on 2018-12-17
hmm not even one view on my post.

Do I something wrong?



    Home
    Forum
    The Ubuntu Forum Community
    Ubuntu Official Flavours Support
    General Help
    [ubuntu] Gtk-WARNING

+ Reply to Thread
Results 1 to 1 of 1
Thread: Gtk-WARNING
my post.

---

### Post by coffeecat on 2018-12-17
The view counter is broken. In fact, nine people including yourself have viewed this thread.

You need to bump your thread every so often if you don't get a reply. Leaving it for four days almost guarantees that it will sink down too far for it to attract attention. Bump it after 12-24 hours if you get no reply.

---

### Post by deadflowr on 2018-12-17
> hmm not even one view on my post.

Do I something wrong?


As stated the view count is busted up.
But beyond that perhaps it's unclear what you're asking or if you're asking for anything.
I'm not sure anyone knows how to respond.

I did find this similar bug report:
[https://bugs.launchpad.net/ubuntu/+source/apport/+bug/1713749]("https://bugs.launchpad.net/ubuntu/+source/apport/+bug/1713749")
But again, not sure if it's something or not.

---

### Post by #&amp;thj^% on 2018-12-17
The views are broken as far as views. (Ninja'd by coffeecat and deadflowr)
Bug found here: [https://bugs.launchpad.net/ubuntu/+source/ubuntu-themes/+bug/1773045](https://bugs.launchpad.net/ubuntu/+source/ubuntu-themes/+bug/1773045)

have you tried>>remove the line (73) in /usr/share/themes/Radiance/gtk-3.20/gtk-main

---

### Post by drumanart on 2018-12-18
the file @import url("apps/gnome-builder.css"); in /usr/share/themes/Radiance/gtk-3.20/gtk-main.css doesn't exist.

It happens on all themes not only on Radiance, and not only opening gedit o evince.

Here is the output when running gedit:

```

(gedit:3598): Gtk-WARNING **: 18:40:05.621: Theme parsing error: gtk.css:2286:8: not a number

(gedit:3598): Gtk-WARNING **: 18:40:05.621: Theme parsing error: gtk.css:2286:18: Using Pango syntax for the font: style property is deprecated; please use CSS syntax

(gedit:3598): Gtk-WARNING **: 18:40:05.621: Theme parsing error: gtk.css:2291:8: not a number

(gedit:3598): Gtk-WARNING **: 18:40:05.621: Theme parsing error: gtk.css:2291:18: Using Pango syntax for the font: style property is deprecated; please use CSS syntax

(gedit:3598): Gtk-WARNING **: 18:40:05.626: Theme parsing error: gtk.css:4357:14: not a number

(gedit:3598): Gtk-WARNING **: 18:40:05.626: Theme parsing error: gtk.css:4357:14: Expected a string.

(gedit:3598): Gtk-WARNING **: 18:40:05.626: Theme parsing error: gtk.css:4419:12: not a number

(gedit:3598): Gtk-WARNING **: 18:40:05.626: Theme parsing error: gtk.css:4419:12: Expected a string.

(gedit:3598): Gtk-WARNING **: 18:40:05.626: Theme parsing error: gtk.css:4428:16: not a number

(gedit:3598): Gtk-WARNING **: 18:40:05.626: Theme parsing error: gtk.css:4428:16: Expected a string.

(gedit:3598): Gtk-WARNING **: 18:40:05.626: Theme parsing error: gtk.css:4443:22: not a number

(gedit:3598): Gtk-WARNING **: 18:40:05.626: Theme parsing error: gtk.css:4443:22: Expected a string.

(gedit:3598): Gtk-WARNING **: 18:40:05.627: Theme parsing error: gtk.css:4499:12: Expected a string.

(gedit:3598): Gtk-WARNING **: 18:40:05.627: Theme parsing error: gtk.css:4501:16: not a number

(gedit:3598): Gtk-WARNING **: 18:40:05.627: Theme parsing error: gtk.css:4501:16: Expected a string.

(gedit:3598): Gtk-WARNING **: 18:40:05.627: Theme parsing error: gtk.css:4549:12: not a number

(gedit:3598): Gtk-WARNING **: 18:40:05.627: Theme parsing error: gtk.css:4549:12: Expected a string.

(gedit:3598): Gtk-WARNING **: 18:40:05.696: Attempting to read the recently used resources file at '/home/martin/.local/share/recently-used.xbel', but the parser failed: Failed to open file “/home/martin/.local/share/recently-used.xbel”: Permission denied.
martin@drumanart:~$ clear

martin@drumanart:~$ gedit

(gedit:3605): Gtk-WARNING **: 18:40:14.887: Theme parsing error: gtk.css:597:14: not a number

(gedit:3605): Gtk-WARNING **: 18:40:14.887: Theme parsing error: gtk.css:597:14: Expected a string.

(gedit:3605): Gtk-WARNING **: 18:40:14.887: Theme parsing error: gtk.css:600:17: Expected a string.

(gedit:3605): Gtk-WARNING **: 18:40:14.888: Theme parsing error: gtk.css:784:14: not a number

(gedit:3605): Gtk-WARNING **: 18:40:14.888: Theme parsing error: gtk.css:784:14: Expected a string.

(gedit:3605): Gtk-WARNING **: 18:40:14.888: Theme parsing error: gtk.css:787:17: Expected a string.

(gedit:3605): Gtk-WARNING **: 18:40:14.889: Theme parsing error: gtk.css:1096:14: not a number

(gedit:3605): Gtk-WARNING **: 18:40:14.889: Theme parsing error: gtk.css:1096:14: Expected a string.

(gedit:3605): Gtk-WARNING **: 18:40:14.889: Theme parsing error: gtk.css:1099:17: Expected a string.

(gedit:3605): Gtk-WARNING **: 18:40:14.893: Theme parsing error: gtk.css:2286:8: not a number

(gedit:3605): Gtk-WARNING **: 18:40:14.893: Theme parsing error: gtk.css:2286:18: Using Pango syntax for the font: style property is deprecated; please use CSS syntax

(gedit:3605): Gtk-WARNING **: 18:40:14.893: Theme parsing error: gtk.css:2291:8: not a number

(gedit:3605): Gtk-WARNING **: 18:40:14.893: Theme parsing error: gtk.css:2291:18: Using Pango syntax for the font: style property is deprecated; please use CSS syntax

(gedit:3605): Gtk-WARNING **: 18:40:14.898: Theme parsing error: gtk.css:4357:14: not a number

(gedit:3605): Gtk-WARNING **: 18:40:14.898: Theme parsing error: gtk.css:4357:14: Expected a string.

(gedit:3605): Gtk-WARNING **: 18:40:14.898: Theme parsing error: gtk.css:4419:12: not a number

(gedit:3605): Gtk-WARNING **: 18:40:14.898: Theme parsing error: gtk.css:4419:12: Expected a string.

(gedit:3605): Gtk-WARNING **: 18:40:14.898: Theme parsing error: gtk.css:4428:16: not a number

(gedit:3605): Gtk-WARNING **: 18:40:14.898: Theme parsing error: gtk.css:4428:16: Expected a string.

(gedit:3605): Gtk-WARNING **: 18:40:14.899: Theme parsing error: gtk.css:4443:22: not a number

(gedit:3605): Gtk-WARNING **: 18:40:14.899: Theme parsing error: gtk.css:4443:22: Expected a string.

(gedit:3605): Gtk-WARNING **: 18:40:14.899: Theme parsing error: gtk.css:4499:12: Expected a string.

(gedit:3605): Gtk-WARNING **: 18:40:14.899: Theme parsing error: gtk.css:4501:16: not a number

(gedit:3605): Gtk-WARNING **: 18:40:14.899: Theme parsing error: gtk.css:4501:16: Expected a string.

(gedit:3605): Gtk-WARNING **: 18:40:14.899: Theme parsing error: gtk.css:4549:12: not a number

(gedit:3605): Gtk-WARNING **: 18:40:14.899: Theme parsing error: gtk.css:4549:12: Expected a string.



```

---

### Post by drumanart on 2018-12-20
It seems to be that nobody has had the same problem.
I googled without any success until now.

As it says it is a  Gtk-WARNING not an error, but great would be to get reed of this messages.

Help please Martin

---

### Post by drumanart on 2018-12-21
In the folder **/usr/share/themes/NumixBlue/** I have **gtk-2.0, gtk-3.0 & gtk-3.20**

After changing names of gtk-3.0 & gtk-3.20 the nasty Gtk-WARNING disappeard.

Why is another question.

---

