---
title: "Deluge crashes on start [Log of start included]"
date: 2007-10-09
forum: General Help
---

### Post by foundation on 2007-10-09
Okay, so Deluge worked fine for a few days (Probably my favourite torrent client on Linux now) but one day after getting home from work and turning the laptop on Deluge will no longer start and as far as I'm aware nothing had been modified.

Here's the log of what happens when I try to start it:
```
byrd@skylark:~$ deluge
no existing Deluge session
Starting new Deluge session...
deluge_core; using libtorrent 0.13.0.0. Compiled with NDEBUG.
Applying preferences
Pickling state...
Scanning plugin dir /usr/share/deluge/plugins
Initialising plugin BlocklistImport
Initialising plugin TorrentPeers
Initialising plugin MoveTorrent
Initialising plugin WebSeed
Initialising plugin TorrentSearch
Initialising plugin TorrentPieces
Initialising plugin NetworkGraph
Initialising plugin ExtraStats
Initialising plugin EventLogging
Initialising plugin SimpleRSS
Initialising plugin TorrentCreator
Initialising plugin TorrentFiles
Initialising plugin TorrentNotification
Initialising plugin SpeedLimiter
Initialising plugin Locations
Initialising plugin NetworkHealth
Initialising plugin DesiredRatio
Applying preferences
Starting DHT...
No DHT file to resume
Showing window
Loading TorrentPeers plugin...
Loading Move Torrent plugin...
Loading ExtraStats plugin...
Traceback (most recent call last):
  File "/usr/bin/deluge", line 121, in <module>
    start_deluge()
  File "/usr/bin/deluge", line 110, in start_deluge
    interface.start(get_cmd_line_torrents())
  File "/var/lib/python-support/python2.5/deluge/interface.py", line 918, in start
    self.load_plugins()
  File "/var/lib/python-support/python2.5/deluge/interface.py", line 939, in load_plugins
    self.plugins.enable_plugin(plugin)
  File "/var/lib/python-support/python2.5/deluge/plugins.py", line 75, in enable_plugin
    self.enabled_plugins[name] = plugin.enable(self.core, self.interface)
  File "/usr/share/deluge/plugins/ExtraStats/__init__.py", line 45, in enable
    return ExtraStats(path, core, interface)
  File "/usr/share/deluge/plugins/ExtraStats/__init__.py", line 88, in __init__
    self.prepare_stats()
  File "/usr/share/deluge/plugins/ExtraStats/__init__.py", line 112, in prepare_stats
    self.all_downloaded = long(readlines[0])
IndexError: list index out of range
```I had a read through but I'm not too sure what it's saying; is it a problem with the ExtraStats plugin? If so, how can I disable that plugin without going into Deluge. Edit: I could just go to */usr/share/deluge/plugins* and rename/delete that plugin, or something? Edit: I was unable to rename the folder in Nautilus or via the terminal. D:

Or.. what is the problem? Hah. :confused: Oh, and I really, really don't want to lose the current torrents I'm in the process of downloading and/or seeding. :x


[b]Edit: I just did *sudo rm -r ExtraStats* and Deluge is starting fine now and I haven't lost the current torrents or anything.

---

### Post by linuxcompulsive on 2007-12-12
Thanks a lot. I had the same problem and you helped me.
Good work.

Linuxcompulsive

---

