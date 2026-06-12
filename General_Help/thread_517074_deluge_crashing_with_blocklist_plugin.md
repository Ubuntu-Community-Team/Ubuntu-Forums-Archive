---
title: "deluge crashing with blocklist plugin"
date: 2007-08-04
forum: General Help
---

### Post by jackmc on 2007-08-04
Here is the terminal output of what happens when I run deluge:

```

$ deluge
no existing Deluge session
Starting new Deluge session...
deluge_core; using libtorrent 0.13.0.0. Compiled with NDEBUG.
Applying preferences
Pickling state...
Scanning plugin dir /usr/share/deluge/plugins
Initialising plugin TorrentNotification
Initialising plugin TorrentSearch
Initialising plugin BlocklistImport
Initialising plugin DesiredRatio
Initialising plugin RSS
Initialising plugin NetworkGraph
Initialising plugin NetworkHealth
Initialising plugin TorrentCreator
Applying preferences
Starting DHT...
Showing window
Loading blocklist plugin ...
Fetching http://www.bluetack.co.uk/config/nipfilter.dat.gz
importing with gzmule
GZMuleReader loading /home/jack/.config/deluge/blocklist.cache
MuleReader loading
TextBase loading
Starting import
Traceback (most recent call last):
  File "/usr/bin/deluge", line 140, in <module>
    start_deluge()
  File "/usr/bin/deluge", line 129, in start_deluge
    interface.start(options.tray, get_cmd_line_torrents())
  File "/var/lib/python-support/python2.5/deluge/interface.py", line 794, in start
    self.load_plugins()
  File "/var/lib/python-support/python2.5/deluge/interface.py", line 810, in load_plugins
    self.plugins.enable_plugin(plugin)
  File "/var/lib/python-support/python2.5/deluge/plugins.py", line 75, in enable_plugin
    self.enabled_plugins[name] = plugin.enable(self.core, self.interface)
  File "/usr/share/deluge/plugins/BlocklistImport/__init__.py", line 29, in enable
    return BlocklistImport(path, core, interface)
  File "/usr/share/deluge/plugins/BlocklistImport/__init__.py", line 71, in __init__
    self.loadlist(fetch=self.config.get('load_on_start'))
  File "/usr/share/deluge/plugins/BlocklistImport/__init__.py", line 108, in loadlist
    ips = reader.next()
  File "/usr/share/deluge/plugins/BlocklistImport/text.py", line 31, in next
    txt = self.fd.readline()
  File "/usr/lib/python2.5/gzip.py", line 399, in readline
    c = self.read(readsize)
  File "/usr/lib/python2.5/gzip.py", line 227, in read
    self._read(readsize)
  File "/usr/lib/python2.5/gzip.py", line 263, in _read
    self._read_gzip_header()
  File "/usr/lib/python2.5/gzip.py", line 164, in _read_gzip_header
    raise IOError, 'Not a gzipped file'
IOError: Not a gzipped file

```

I figured out how to disable the plugin, but does anyone know how to fix the problem?

---

### Post by ptelder on 2007-10-14
Just in case you're still wondering... That traceback is complaining that the downloaded blocklist is not a gzipped file.

Either the people you get your blocklist from changed formats, or more likely, stopped hosting the file. Deluge was probably downloading a 404 error page instead of a blocklist.

You can probably fix it by giving it a new address to use. As to where to get that address, I have no clue. I landed here while doing a Google search to try to figure out how to set it up myself...

---

### Post by Hemmer on 2007-10-16
you could manually download the blocklist zip/tar to your home directory (home/*username*) and link to that. It wont have any trouble loading it locally.

---

### Post by splint-84 on 2007-11-28
I just had the same problem. Fixed it by going into my home folder, /.config/deluge/ and opening blocklist.conf and changing from:

(dp0
S'listtype'
p1
S'pgtext'
p2
sS'url'
p3
S'http://peerguardian.sourceforge.net/lists'
p4
sS'load_on_start'
p5
I01
s.

to:

(dp0
S'listtype'
p1
S'pgtext'
p2
sS'url'
p3
S''
p4
sS'load_on_start'
p5
I01
s.

then Deluge started with and error complaining about the URL missing (as it should), but at least it started so you can change things graphically again. :)

---

### Post by nuchdog on 2007-12-09
Try this: Check the site for links and the correct format to specify:

[http://dev.deluge-torrent.org/wiki/BlocklistPlugin]("http://dev.deluge-torrent.org/wiki/BlocklistPlugin")

---

### Post by H3retic on 2008-02-10
I had this problem, and this totally cleared things up.  Thanks!

---

