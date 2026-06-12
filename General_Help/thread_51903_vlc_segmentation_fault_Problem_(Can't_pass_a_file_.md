---
title: "vlc segmentation fault Problem (Can't pass a file to vlc)"
date: 2005-07-25
forum: General Help
---

### Post by esukf on 2005-07-25
After updating my system vlc 8.1 no longer loads properly when I double click a media file which has been set to load vlc as the default media player.

Whenever i double click a media file vlc loads and immediately quits.

When i execute vlc in a terminal and passing a file to it, I get a Segmentation Fault error.

esukf@esukfpc:~$ vlc test.avi
VLC media player 0.8.1 Janus
Segmentation fault
esukf@esukfpc:~$

vlc works fine if i just type vlc in terminal or start it from the application menu and then drag and drop media files to it.  The Segmentation Fault only happens when passing a file to vlc.

Anyone know how to resolve the problem???

These are the programs that was upgraded that caused the problem to occur:-

Commit Log for Mon Jul 25 00:46:47 2005


Upgraded the following packages:
amule (2.0.0-1~5.04ubp1) to 2.0.3-1build1~5.04ubp1
dpkg (1.10.27ubuntu1) to 1.10.27ubuntu1.1
dpkg-dev (1.10.27ubuntu1) to 1.10.27ubuntu1.1
dselect (1.10.27ubuntu1) to 1.10.27ubuntu1.1
gaim (1:1.3.1~5.04ubp1) to 1:1.4.0-1ubuntu1~5.04ubp1
gaim-data (1:1.3.1~5.04ubp1) to 1:1.4.0-1ubuntu1~5.04ubp1
gimp (2.2.7-1~5.04ubp1) to 2.2.8-1ubuntu1~5.04ubp1
gimp-data (2.2.7-1~5.04ubp1) to 2.2.8-1ubuntu1~5.04ubp1
gimp-python (2.2.7-1~5.04ubp1) to 2.2.8-1ubuntu1~5.04ubp1
gtk2-engines-clearlooks (0.5-0ubuntu1) to 0.6.2-1~5.04ubp1
k3b (0.11.23-0ubuntu3) to 0.11.24-0ubuntu1~5.04ubp2
k3blibs (0.11.23-0ubuntu3) to 0.11.24-0ubuntu1~5.04ubp2
kdelibs-bin (4:3.4.0-0ubuntu3.2) to 4:3.4.0-0ubuntu3.3
kdelibs-data (4:3.4.0-0ubuntu3.2) to 4:3.4.0-0ubuntu3.3
kdelibs4 (4:3.4.0-0ubuntu3.2) to 4:3.4.0-0ubuntu3.3
libgimp2.0 (2.2.7-1~5.04ubp1) to 2.2.8-1ubuntu1~5.04ubp1
libldap2 (2.1.30-3ubuntu3) to 2.1.30-3ubuntu3.1
libmysqlclient14 (4.1.10a-2) to 4.1.10a-2ubuntu0.1
powernowd (0.90-3ubuntu14) to 0.96-1ubuntu1~5.04ubp1
smeg (0.7.4-0ubuntu1~5.04ubp1) to 0.7.5-0ubuntu1~5.04ubp1
sun-j2re1.5 (1.5.0+update02) to 1.5.0+update04
zlib1g (1:1.2.2-4ubuntu1) to 1:1.2.2-4ubuntu1.2

---

### Post by esukf on 2005-07-26
Found out what was causing the segmentation fault. It was the upgrade of  gtk2-engines-clearlooks (0.5-0ubuntu1) to 0.6.2-1~5.04ubp1 which is causing the problem.

Downgrading back to 0.5-0ubuntu1 or changing themes fixed it.

---

### Post by the real alien on 2005-07-26
Hi,
I hava the same problem. How did you do that? I managed to remove de newest version, but how can I tell him to take the older version?

Thanx

---

### Post by esukf on 2005-07-28
Download the gtk2-engines-clearlooks deb package from here [http://packages.ubuntu.com/hoary/gnome/gtk2-engines-clearlooks](http://packages.ubuntu.com/hoary/gnome/gtk2-engines-clearlooks) then install it with ```
sudo dpkg -i gtk2-engines-clearlooks_0.5-0ubuntu1_i386.deb
```

Hope it helps!

---

### Post by tedddee on 2005-11-09
didnt help :(

here's what im getting 

> GLib-WARNING **: g_main_iterate(): main loop already active in another thread

                                                                GLib-WARNING **: g_main_iterate(): main loop already active in another thread

                                                             GLib-WARNING **: g_main_iterate(): main loop already active in another thread

                                                          GLib-WARNING **: g_main_iterate(): main loop already active in another thread

                                                       GLib-WARNING **: g_main_iterate(): main loop already active in another thread

                                                    GLib-WARNING **: g_main_run(): called recursively from within a source's check() or prepare() member or from a second thread, iteration not possible

                                        Gdk-CRITICAL **: file gdkgc.c: line 289 (gdk_gc_unref): assertion `private->ref_count > 0' failed.
                                                          Segmentation fault


---

