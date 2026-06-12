---
title: "Deluge Will Not Start!"
date: 2008-05-05
forum: General Help
---

### Post by Sohn_of_a_Gunn on 2008-05-05
Deluge will not start for me, I click the icon, acts like it will start up, and nothing starts at all. I get this error when I run it in a terminal:
Traceback (most recent call last):
File "/usr/bin/deluge", line 145, in <module>
start_deluge()
File "/usr/bin/deluge", line 128, in start_deluge
interface = deluge.interface.DelugeGTK()
File "/var/lib/python-support/python2.5/deluge/interface.py", line 54, in __init__
common.CONFIG_DIR)
File "/var/lib/python-support/python2.5/deluge/core.py", line 202, in __init__
self.config = pref.Preferences(os.path.join(self.base_dir, PREFS_FILENAME))
File "/var/lib/python-support/python2.5/deluge/pref.py", line 291, in __init__
self.load(self.config_file)
File "/var/lib/python-support/python2.5/deluge/pref.py", line 336, in load
self.dump = pickle.load(pkl_file)
cPickle.UnpicklingError: invalid load key, '9'

Any help please?

---

### Post by agim on 2008-05-05
I would try removing and reinstalling it.

sudo apt-get remove deluge-torrent
sudo apt-get install deluge-torrent

This solution will keep your configuration files, so you won't need to redo them.

Or if you prefer, you can just find the package in synaptic (deluge-torrent) and reinstall.

---

### Post by Sohn_of_a_Gunn on 2008-05-06
> **agim said:**
> I would try removing and reinstalling it.

sudo apt-get remove deluge-torrent
sudo apt-get install deluge-torrent

This solution will keep your configuration files, so you won't need to redo them.

Or if you prefer, you can just find the package in synaptic (deluge-torrent) and reinstall.

I did that and no luck.

---

### Post by s_spiff on 2008-05-08
Try this :  rm ~/.config/deluge/persistent.state
Dunno what it exactly does, but found it on another thread, and worked for me.

---

### Post by 944jon on 2009-02-28
> **s_spiff said:**
> Try this :  rm ~/.config/deluge/persistent.state
Dunno what it exactly does, but found it on another thread, and worked for me.

This worked for me. I'm running 8.10, and Deluge 0.5.9.3

I had to add all my torrents over again though, and it loses them when I restart deluge.

---

### Post by Hobbymaster on 2009-07-24
> **Sohn_of_a_Gunn said:**
> I did that and no luck.
I have similar problem but I think the reason mine will not start is because I set the download to goto a removable drive which died during a thunderstorm power out. Even if I reinstall it gives this error in terminal 


no existing Deluge session
Starting new Deluge session...
Traceback (most recent call last):
  File "/usr/bin/deluge", line 133, in <module>
    start_deluge()
  File "/usr/bin/deluge", line 116, in start_deluge
    interface = deluge.interface.DelugeGTK()
  File "/var/lib/python-support/python2.5/deluge/interface.py", line 54, in __init__
    common.CONFIG_DIR)
  File "/var/lib/python-support/python2.5/deluge/core.py", line 208, in __init__
    os.mkdir(TORRENTS_SUBDIR)
OSError: [Errno 13] Permission denied: '/media/149GB_STO_'

I tried to use a other drive with the same volume name but still not working.

I liked this program, I am using Ktorrent but I like to use different torrent programs and Deluge became a favorite of mine because it was so close to Utorrent.

---

### Post by Bigtime_Scrub on 2009-07-24
You need to get rid of the settings you had before and reinstall. Please do not use any {rm} command until you know what you are doing as that can cause some serious damage to your system.

Anyhow, try this

```
sudo apt-get purge deluge
```
```
sudo apt-get autoremove
```

then finally run 

```
sudo aptitude install deluge
```

Then restart deluge.

---

### Post by Hobbymaster on 2009-07-25
> **Bigtime_Scrub said:**
> You need to get rid of the settings you had before and reinstall. Please do not use any {rm} command until you know what you are doing as that can cause some serious damage to your system.

Anyhow, try this

```
sudo apt-get purge deluge
``````
sudo apt-get autoremove
```then finally run 

```
sudo aptitude install deluge
```Then restart deluge.


Wish I could say that worked but it still looks for the broken drive.
Any how I put a different drive on and called it the same volume it was looking for and the program began to work. I guess I fooled the program into thinking it had the old drive.
Whew!! I changed the settings and should not have any problems. I had the same problem with transmission as well and fixed it with the drive. I do not know why they keep there settings when you do a reinstall. You think you would want to fresh new version with the default settings. Lesson here do not dump files to removable drive just move them there yourself. But I really like to thank you for the help.

---

### Post by Hobbymaster on 2009-07-25
opps spoke too soon now it does not load again
Starting new Deluge session...
deluge_core; using libtorrent 0.13.0.0. Compiled with NDEBUG.
Applying preferences
save uploaded memory
Pickling state...
Scanning plugin dir /usr/share/deluge/plugins
Initialising plugin MoveTorrent
Initialising plugin TorrentNotification
Initialising plugin Scheduler
Initialising plugin TorrentFiles
Initialising plugin FlexRSS
Initialising plugin WebUi
Initialising plugin WebSeed
Initialising plugin TorrentPeers
Initialising plugin BlocklistImport
Initialising plugin DesiredRatio
Initialising plugin NetworkGraph
Initialising plugin SpeedLimiter
Initialising plugin EventLogging
Initialising plugin TorrentCreator
Initialising plugin NetworkHealth
Initialising plugin Search
Applying preferences
Starting DHT...
Showing window
terminate called after throwing an instance of 'libtorrent::invalid_torrent_file'
  what():  invalid torrent file
Aborted

Ok it works again 
if has a bad or invalid torrent file it will not load.
I deleted bad torrent file.
I post as info only hope it help someone.

---

### Post by abdusamed on 2009-11-09
on crunch bang linux 

```

rm ~/.config/deluge/persistent.state

```would not work i get this 
```
 
smallubuntu@smallubuntu-desktop:~$ rm ~/.config/deluge/persistent.state
rm: cannot remove `/home/smallubuntu/.config/deluge/persistent.state': No such file or directory

```it would start but wouldn't finish loading.. ANNOYIN..HELP PLZ!

this is what i get if i type in deluge in the terminal
```

smallubuntu@smallubuntu-desktop:~$ deluge
1.1.6
/var/lib/python-support/python2.6/deluge/ui/gtkui/mainwindow.py:63: GtkWarning: gtk_toolbar_set_icon_size: assertion `icon_size != GTK_ICON_SIZE_INVALID' failed
  "glade/main_window.glade"))
Exception in thread Thread-1:
Traceback (most recent call last):
  File "/usr/lib/python2.6/threading.py", line 525, in __bootstrap_inner
    self.run()
  File "/var/lib/python-support/python2.6/deluge/core/preferencesmanager.py", line 451, in run
    + "&plugins=" + quote_plus(self.config["enabled_plugins"])
  File "/usr/lib/python2.6/urllib.py", line 1228, in quote_plus
    return quote(s, safe)
  File "/usr/lib/python2.6/urllib.py", line 1220, in quote
    res = map(safe_map.__getitem__, s)
KeyError: 'Blocklist'

/var/lib/python-support/python2.6/deluge/ui/tracker_icons.py:70: DeprecationWarning: BaseException.message has been deprecated as of Python 2.6
  log.debug("%s %s %s" % (url, e, e.message))
^C^C/var/lib/python-support/python2.6/deluge/ui/gtkui/filtertreeview.py:202: GtkWarning: gtk_tree_store_set_value: assertion `VALID_ITER (iter, tree_store)' failed
  self.treestore.set_value(row, 3, count)
/var/lib/python-support/python2.6/deluge/ui/gtkui/filtertreeview.py:214: GtkWarning: gtk_tree_store_set_value: assertion `VALID_ITER (iter, tree_store)' failed
  self.treestore.set_value(row, FILTER_COLUMN, True)
/var/lib/python-support/python2.6/deluge/ui/gtkui/filtertreeview.py:183: GtkWarning: gtk_tree_store_set_value: assertion `VALID_ITER (iter, tree_store)' failed
  self.treestore.set_value(self.cat_nodes[cat], FILTER_COLUMN, True)
/var/lib/python-support/python2.6/deluge/ui/gtkui/filtertreeview.py:190: GtkWarning: gtk_tree_store_set_value: assertion `VALID_ITER (iter, tree_store)' failed
  self.treestore.set_value(self.filters[f], FILTER_COLUMN, False)

```

---

### Post by Pramod_rt on 2009-12-31
Maybe I have found a solution:

You just need to delete the file ~/.config/deluge/torrentview.state and relaunch deluge.

---

### Post by Chatoan on 2010-01-22
> **Sohn_of_a_Gunn said:**
> Deluge will not start for me, I click the icon, acts like it will start up, and nothing starts at all. I get this error when I run it in a terminal:
Traceback (most recent call last):
File "/usr/bin/deluge", line 145, in <module>
start_deluge()
File "/usr/bin/deluge", line 128, in start_deluge
interface = deluge.interface.DelugeGTK()
File "/var/lib/python-support/python2.5/deluge/interface.py", line 54, in __init__
common.CONFIG_DIR)
File "/var/lib/python-support/python2.5/deluge/core.py", line 202, in __init__
self.config = pref.Preferences(os.path.join(self.base_dir, PREFS_FILENAME))
File "/var/lib/python-support/python2.5/deluge/pref.py", line 291, in __init__
self.load(self.config_file)
File "/var/lib/python-support/python2.5/deluge/pref.py", line 336, in load
self.dump = pickle.load(pkl_file)
cPickle.UnpicklingError: invalid load key, '9'

Any help please?


i found a very easy way to solve the problem :close deluge from file menue or ctrl+Q hope it will work for you

---

### Post by ponq on 2010-05-11
I just ran into this problem. 
Removed and reinstalled Deluge. No go.

Finally I tried from the terminal: sudo deluge.

It works, so it seems I have to run it as root.

Now I have made a starter: gksudo deluge-gtk this one works for me.

Hope this helps.

---

### Post by vinayg18 on 2011-10-10
Thanks Pramod_rt, deleting torrentview.state worked for me.

---

### Post by Pramod_rt on 2011-10-11
> **vinayg18 said:**
> Thanks Pramod_rt, deleting torrentview.state worked for me.
Welcome :)

---

### Post by Devr0n on 2013-02-15
I have removed all .state files. This helps for me and all my old files were back online.

---

