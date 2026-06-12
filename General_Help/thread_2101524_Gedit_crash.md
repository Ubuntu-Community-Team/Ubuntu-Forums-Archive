---
title: "Gedit crash"
date: 2013-01-04
forum: General Help
---

### Post by cipherboy_loc on 2013-01-04
After having issues with gedit crashing on me, I modified the menu item in fluxbox to include automatic logging of gedit sessions. Attached below is one such report where it crashes. At the time, I was looking at a terminal window in front of the gedit session (last command at the time was a cd command followed by ls), when gedit disappeared from under it, crashing.

Load averages are1.41, 0.96, 0.62

uname -a
```

Linux ubuntu-basement 3.5.0-21-generic #32-Ubuntu SMP Tue Dec 11 18:52:46 UTC 2012 i686 athlon i686 GNU/Linux

```free -m
```

             total       used       free     shared    buffers     cached
Mem:          2903       1645       1257          0        224        573
-/+ buffers/cache:        846       2056
Swap:         4095          0       4095


```CPU hovers at ~30% all the time, though likely as I have the following applications open:
(conky on desktop, fluxbox window manager):
thunderbird (one email account, 20k emails, multiple news feeds)
pidgin (1 connected accounts)
firefox (4 tabs average)
gedit (4 files, all under 1k lines)
terminal (3 tabs)

Average CPU usage when none of the applications (except conky) are open is about 5%

Only thing that I could think of is that gedit had been open for 10 hours (current time is 8PM, launched at 10AM), however other times it has crashed being open for less than an hour. The error message at the end, upon a google search, has revealed nothing.

Applicable part of log when gedit crashes:
```

Launching gedit on 01-04-13 at 10:07:01

(gedit:4610): Gtk-CRITICAL **: gtk_list_store_set_column_types: assertion `priv->columns_dirty == 0' failed
Fontconfig warning: "/etc/fonts/conf.d/50-user.conf", line 9: reading configurations from ~/.fonts.conf is deprecated.

(gedit:4610): GtkSourceView-WARNING **: Could not find word to remove in buffer (username), this should not happen!

(gedit:4610): GtkSourceView-WARNING **: Could not find word to remove in buffer (success), this should not happen!

(gedit:4610): GtkSourceView-WARNING **: Could not find word to remove in buffer (checkBlacklist), this should not happen!
Fontconfig warning: "/etc/fonts/conf.d/50-user.conf", line 9: reading configurations from ~/.fonts.conf is deprecated.

(gedit:4610): Gtk-CRITICAL **: gtk_grid_set_column_spacing: assertion `GTK_IS_GRID (grid)' failed


```
Thanks,
Cipherboy

---

### Post by cipherboy_loc on 2013-02-08
Bump. Gedit is still occasionally crashing, attached are some more logs. 
 
```

Launching gedit on 02-07-13 at 15:43:59

(gedit:5260): Gtk-CRITICAL **: gtk_list_store_set_column_types: assertion `priv->columns_dirty == 0' failed
Fontconfig warning: "/etc/fonts/conf.d/50-user.conf", line 9: reading configurations from ~/.fonts.conf is deprecated.

(gedit:5260): GtkSourceView-WARNING **: Could not find word to remove in buffer (In), this should not happen!

[ Similar message repeats multiple times ]

** (gedit:5260): CRITICAL **: gedit_view_frame_get_view: assertion `GEDIT_IS_VIEW_FRAME (frame)' failed

** (gedit:5260): CRITICAL **: gedit_view_scroll_to_cursor: assertion `GEDIT_IS_VIEW (view)' failed

(gedit:5260): GtkSourceView-WARNING **: Could not find word to remove in buffer (Pro), this should not happen!

(gedit:5260): Gtk-CRITICAL **: gtk_text_buffer_remove_tag: assertion `tag->priv->table == buffer->priv->tag_table' failed

(gedit:5260): Gtk-CRITICAL **: gtk_text_tag_table_remove: assertion `tag->priv->table == table' failed

(gedit:5260): GtkSourceView-WARNING **: Could not find word to remove in buffer (thanks), this should not happen!

[ Similar message repeats multiple times] 

** (gedit:5260): CRITICAL **: gedit_view_frame_get_view: assertion `GEDIT_IS_VIEW_FRAME (frame)' failed

** (gedit:5260): CRITICAL **: gedit_view_scroll_to_cursor: assertion `GEDIT_IS_VIEW (view)' failed

** (gedit:5260): CRITICAL **: gedit_view_frame_get_view: assertion `GEDIT_IS_VIEW_FRAME (frame)' failed

** (gedit:5260): CRITICAL **: gedit_view_scroll_to_cursor: assertion `GEDIT_IS_VIEW (view)' failed

``````

Launching gedit on 02-08-13 at 09:14:28

(gedit:7088): Gtk-CRITICAL **: gtk_list_store_set_column_types: assertion `priv->columns_dirty == 0' failed
Fontconfig warning: "/etc/fonts/conf.d/50-user.conf", line 9: reading configurations from ~/.fonts.conf is deprecated.

```Any ideas as to what is causing this? The logs don't seem to reveal anything.

Side note, it seems to happen more when I am switching between applications (specifically gedit and the terminal), or when switching tabs in gedit (Alt+<number>). 

As like before, I have plenty of RAM available and CPU does not spike; gedit is perfectly responsive; it just crashes/disappears immediately. ps aux | grep gedit reveals that gedit is not running after such a crash, and launching it again is just fine. Also, these past two times have been without any other applications open, just gedit and the terminal.

Excerpt from ~/.xsession-errors:
```

/usr/local/bin/gedit.sh: line 11:  4194 Segmentation fault      (core dumped) bash -c /usr/bin/gedit >> $HOME/.logs/gedit/log.$date.txt 2>&1
/usr/local/bin/gedit.sh: line 11:  4213 Segmentation fault      (core dumped) bash -c /usr/bin/gedit >> $HOME/.logs/gedit/log.$date.txt 2>&1

```

It appears gedit is segfaulting... ...but why?

Thanks,
Cipherboy

---

### Post by cipherboy_loc on 2013-02-10
Bump. Again applied updates today, still no resolution, though Gedit did not get updated.

---

### Post by Bufeu on 2013-02-10
Why not send a crash report using Apport?

---

