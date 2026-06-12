---
title: "Anjuta Crash"
date: 2007-09-28
forum: General Help
---

### Post by Freiburg05 on 2007-09-28
Hi there!

        I'm trying to use Anjuta as my c++ development IDE. I've installed version 2.2.1 from repositories (I've had to add the repository they provide in the homepage). My problem is the following. When I try to view the "help display" view (It's connected to Devhelp plugin, which I already have installed.) Anjuta automatically crashes, just when cliking the "help display" tab.  This is the terminal what the terminal says:


inaki@inaki:~/Azerhitz$ anjuta

(anjuta:12817): Gdl-WARNING **: Unable to load stock icon /usr/share/gdl/images/stock-close-12.png

(anjuta:12817): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(anjuta:12817): Gdl-WARNING **: Unable to load stock icon /usr/share/gdl/images/stock-menu-left-12.png

(anjuta:12817): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(anjuta:12817): Gdl-WARNING **: Unable to load stock icon /usr/share/gdl/images/stock-menu-right-12.png

(anjuta:12817): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
** Message: Spawning script
Segmentation fault (core dumped)


Any idea?

---

### Post by Slaines73 on 2007-09-28
Hi there,

I'am also looking for a C++ IDE on linux and I think that Anjuta could be something for me.
But I get the exact same error as you did, found any solution yet?

Best Regards

---

### Post by Freiburg05 on 2007-10-05
Hi there,

     I'm a bit late, sorry. I found no solution for my anjuta problem, so I tried the new eclipse 3.3 which comes with cdt 4 for C/C++. I'm starting with C++ (I've worked mostly in JAVA until now, and I use Eclipse for a long time), and I think the new Eclipse is the best option for me. 

    You just need sun java (Eclipse 3.3 it's not tested with gcj yet), and unzip the Eclipse package for C/C++ development ([http://www.eclipse.org/downloads/download.php?file=/technology/epp/downloads/release/20070927/eclipse-cpp-europa-fall-linux-gtk.tar.gz]("http://www.eclipse.org/downloads/download.php?file=/technology/epp/downloads/release/20070927/eclipse-cpp-europa-fall-linux-gtk.tar.gz")).

    Hope it helps If you didn't found any solution yet.  
    
    Best regards

---

