---
title: "Cleaning up Home Directory"
date: 2007-10-06
forum: General Help
---

### Post by Bluecube on 2007-10-06
I'm trying to clean up my Home directory as I'm getting loads of "Out of Disk Space" messages. I've cleaned out the Trash which was a whopping 12Gb but am still getting the out of space messages. I'm at a loss what I can do next as cleaning out the trash should have made a difference! /home is on a separate partition if this makes any difference.

TIA for any advice.

---

### Post by taurus on 2007-10-06
What's the output of this command from a terminal then?

```
sudo du -h /home
```

---

### Post by Gillingham on 2007-10-06
Are you sure that the out of disk space messages are about the home directory?  The root partition can also get full.
In the past to get an idea of what file space is used I have used the system monitor under Systems > Administration, And the file systems tab.

---

### Post by Bluecube on 2007-10-06
12K     /home/craig/.openoffice.org2/user/registry/data/org/openoffice/Office/UI
96K     /home/craig/.openoffice.org2/user/registry/data/org/openoffice/Office
104K    /home/craig/.openoffice.org2/user/registry/data/org/openoffice
108K    /home/craig/.openoffice.org2/user/registry/data/org
112K    /home/craig/.openoffice.org2/user/registry/data
1008K   /home/craig/.openoffice.org2/user/registry/cache
1.1M    /home/craig/.openoffice.org2/user/registry
2.6M    /home/craig/.openoffice.org2/user
2.6M    /home/craig/.openoffice.org2
20K     /home/craig/.icons/Neu/extra/128x128/apps
24K     /home/craig/.icons/Neu/extra/128x128
8.0K    /home/craig/.icons/Neu/extra/24x24/apps
12K     /home/craig/.icons/Neu/extra/24x24
96K     /home/craig/.icons/Neu/extra/scalable/actions
16K     /home/craig/.icons/Neu/extra/scalable/apps
116K    /home/craig/.icons/Neu/extra/scalable
8.0K    /home/craig/.icons/Neu/extra/48x48/apps
12K     /home/craig/.icons/Neu/extra/48x48
16K     /home/craig/.icons/Neu/extra/22x22/apps/SVGs
24K     /home/craig/.icons/Neu/extra/22x22/apps
28K     /home/craig/.icons/Neu/extra/22x22
196K    /home/craig/.icons/Neu/extra
36K     /home/craig/.icons/Neu/deprecated/actions
40K     /home/craig/.icons/Neu/deprecated
88K     /home/craig/.icons/Neu/128x128/emblems
640K    /home/craig/.icons/Neu/128x128/actions
108K    /home/craig/.icons/Neu/128x128/places
180K    /home/craig/.icons/Neu/128x128/devices
424K    /home/craig/.icons/Neu/128x128/apps
172K    /home/craig/.icons/Neu/128x128/categories
184K    /home/craig/.icons/Neu/128x128/mimetypes
272K    /home/craig/.icons/Neu/128x128/status
2.1M    /home/craig/.icons/Neu/128x128
252K    /home/craig/.icons/Neu/24x24/actions
40K     /home/craig/.icons/Neu/24x24/places
64K     /home/craig/.icons/Neu/24x24/devices
132K    /home/craig/.icons/Neu/24x24/apps
52K     /home/craig/.icons/Neu/24x24/categories
76K     /home/craig/.icons/Neu/24x24/mimetypes
100K    /home/craig/.icons/Neu/24x24/status
720K    /home/craig/.icons/Neu/24x24
128K    /home/craig/.icons/Neu/scalable/emblems
872K    /home/craig/.icons/Neu/scalable/actions
188K    /home/craig/.icons/Neu/scalable/places
276K    /home/craig/.icons/Neu/scalable/devices
784K    /home/craig/.icons/Neu/scalable/apps
216K    /home/craig/.icons/Neu/scalable/categories
356K    /home/craig/.icons/Neu/scalable/mimetypes
436K    /home/craig/.icons/Neu/scalable/status
3.2M    /home/craig/.icons/Neu/scalable
32K     /home/craig/.icons/Neu/48x48/emblems
264K    /home/craig/.icons/Neu/48x48/actions
40K     /home/craig/.icons/Neu/48x48/places
64K     /home/craig/.icons/Neu/48x48/devices
152K    /home/craig/.icons/Neu/48x48/apps
56K     /home/craig/.icons/Neu/48x48/categories
80K     /home/craig/.icons/Neu/48x48/mimetypes
100K    /home/craig/.icons/Neu/48x48/status
792K    /home/craig/.icons/Neu/48x48
40K     /home/craig/.icons/Neu/22x22/emblems/SVGs
60K     /home/craig/.icons/Neu/22x22/emblems
888K    /home/craig/.icons/Neu/22x22/actions/SVGs
1.2M    /home/craig/.icons/Neu/22x22/actions
188K    /home/craig/.icons/Neu/22x22/places/SVGs
228K    /home/craig/.icons/Neu/22x22/places
272K    /home/craig/.icons/Neu/22x22/devices/SVGs
336K    /home/craig/.icons/Neu/22x22/devices
656K    /home/craig/.icons/Neu/22x22/apps/SVGs
784K    /home/craig/.icons/Neu/22x22/apps
216K    /home/craig/.icons/Neu/22x22/categories/SVGs
268K    /home/craig/.icons/Neu/22x22/categories
364K    /home/craig/.icons/Neu/22x22/mimetypes/SVGs
440K    /home/craig/.icons/Neu/22x22/mimetypes
436K    /home/craig/.icons/Neu/22x22/status/SVGs
536K    /home/craig/.icons/Neu/22x22/status
3.8M    /home/craig/.icons/Neu/22x22
24M     /home/craig/.icons/Neu
24M     /home/craig/.icons
4.0K    /home/craig/.gnome2/glchess/logs
12K     /home/craig/.gnome2/glchess
208K    /home/craig/.gnome2/yelp.d
16K     /home/craig/.gnome2/evince
4.0K    /home/craig/.gnome2/gnometris.d
4.0K    /home/craig/.gnome2/deskbar-applet/modules-2.20-compatible
12K     /home/craig/.gnome2/deskbar-applet
8.0K    /home/craig/.gnome2/Totem
4.0K    /home/craig/.gnome2/file-roller
44K     /home/craig/.gnome2/panel2.d/default/launchers
48K     /home/craig/.gnome2/panel2.d/default
52K     /home/craig/.gnome2/panel2.d
4.0K    /home/craig/.gnome2/gthumb/remote_cache
4.0K    /home/craig/.gnome2/gthumb/comments
4.0K    /home/craig/.gnome2/gthumb/collections
20K     /home/craig/.gnome2/gthumb
4.0K    /home/craig/.gnome2/eog
8.0K    /home/craig/.gnome2/f-spot/addins
16K     /home/craig/.gnome2/f-spot/addin-db-000/addin-data
12K     /home/craig/.gnome2/f-spot/addin-db-000/addin-dir-data
36K     /home/craig/.gnome2/f-spot/addin-db-000
4.0K    /home/craig/.gnome2/f-spot/repository-cache
332K    /home/craig/.gnome2/f-spot
8.0K    /home/craig/.gnome2/keyrings
76K     /home/craig/.gnome2/accels
8.0K    /home/craig/.gnome2/share/fonts
8.0K    /home/craig/.gnome2/share/cursor-fonts
20K     /home/craig/.gnome2/share
152K    /home/craig/.gnome2/rhythmbox/covers
2.5M    /home/craig/.gnome2/rhythmbox
28K     /home/craig/.gnome2/gnome-btdownload/cache
32K     /home/craig/.gnome2/gnome-btdownload
4.0K    /home/craig/.gnome2/nautilus-scripts
3.4M    /home/craig/.gnome2
4.0K    /home/craig/Public
8.0K    /home/craig/.gnome/gnome-vfs
12K     /home/craig/.gnome
12K     /home/craig/.defcon
36K     /home/craig/.wapi
116K    /home/craig/.bluefish
4.0K    /home/craig/.gimp-2.4/themes
4.0K    /home/craig/.gimp-2.4/curves
4.0K    /home/craig/.gimp-2.4/levels
4.0K    /home/craig/.gimp-2.4/patterns
4.0K    /home/craig/.gimp-2.4/scripts
4.0K    /home/craig/.gimp-2.4/modules
4.0K    /home/craig/.gimp-2.4/gimpressionist
4.0K    /home/craig/.gimp-2.4/plug-ins
4.0K    /home/craig/.gimp-2.4/environ
4.0K    /home/craig/.gimp-2.4/fonts
4.0K    /home/craig/.gimp-2.4/fractalexplorer
4.0K    /home/craig/.gimp-2.4/palettes
4.0K    /home/craig/.gimp-2.4/gflare
4.0K    /home/craig/.gimp-2.4/tmp
4.0K    /home/craig/.gimp-2.4/gfig
4.0K    /home/craig/.gimp-2.4/brushes
4.0K    /home/craig/.gimp-2.4/gradients
4.0K    /home/craig/.gimp-2.4/templates
460K    /home/craig/.gimp-2.4
416K    /home/craig/.thumbnails/fail/gnome-thumbnail-factory
420K    /home/craig/.thumbnails/fail
199M    /home/craig/.thumbnails/large
25M     /home/craig/.thumbnails/normal
223M    /home/craig/.thumbnails
26M     /home/craig/.cache/tracker
26M     /home/craig/.cache
488K    /home/craig/.galeon/mozilla/galeon/Cache
12K     /home/craig/.galeon/mozilla/galeon/chrome
624K    /home/craig/.galeon/mozilla/galeon
628K    /home/craig/.galeon/mozilla
8.0K    /home/craig/.galeon/favicon_cache
780K    /home/craig/.galeon
12K     /home/craig/.Trash
4.0K    /home/craig/.scribus/scrapbook/main
8.0K    /home/craig/.scribus/scrapbook
140K    /home/craig/.scribus
28K     /home/craig/.xine
4.0K    /home/craig/.beagle/config
12K     /home/craig/.beagle/ToIndex
2.1M    /home/craig/.beagle/Log
8.0K    /home/craig/.beagle/Indexes/KonversationIndex/SecondaryIndex
8.0K    /home/craig/.beagle/Indexes/KonversationIndex/PrimaryIndex
4.0K    /home/craig/.beagle/Indexes/KonversationIndex/Locks
32K     /home/craig/.beagle/Indexes/KonversationIndex
88K     /home/craig/.beagle/Indexes/FileSystemIndex/SecondaryIndex
240K    /home/craig/.beagle/Indexes/FileSystemIndex/PrimaryIndex
4.0K    /home/craig/.beagle/Indexes/FileSystemIndex/Locks
464K    /home/craig/.beagle/Indexes/FileSystemIndex
8.0K    /home/craig/.beagle/Indexes/LabyrinthIndex/SecondaryIndex
8.0K    /home/craig/.beagle/Indexes/LabyrinthIndex/PrimaryIndex
4.0K    /home/craig/.beagle/Indexes/LabyrinthIndex/Locks
32K     /home/craig/.beagle/Indexes/LabyrinthIndex
8.0K    /home/craig/.beagle/Indexes/KAddressBookIndex/SecondaryIndex
8.0K    /home/craig/.beagle/Indexes/KAddressBookIndex/PrimaryIndex
4.0K    /home/craig/.beagle/Indexes/KAddressBookIndex/Locks
40K     /home/craig/.beagle/Indexes/KAddressBookIndex
8.0K    /home/craig/.beagle/Indexes/IndexingServiceIndex/SecondaryIndex
3.6M    /home/craig/.beagle/Indexes/IndexingServiceIndex/PrimaryIndex
4.0K    /home/craig/.beagle/Indexes/IndexingServiceIndex/Locks
3.6M    /home/craig/.beagle/Indexes/IndexingServiceIndex
8.0K    /home/craig/.beagle/Indexes/ThunderbirdIndex/SecondaryIndex
8.0K    /home/craig/.beagle/Indexes/ThunderbirdIndex/PrimaryIndex
4.0K    /home/craig/.beagle/Indexes/ThunderbirdIndex/Locks
32K     /home/craig/.beagle/Indexes/ThunderbirdIndex
8.0K    /home/craig/.beagle/Indexes/KonqBookmarkIndex/SecondaryIndex
8.0K    /home/craig/.beagle/Indexes/KonqBookmarkIndex/PrimaryIndex
4.0K    /home/craig/.beagle/Indexes/KonqBookmarkIndex/Locks
40K     /home/craig/.beagle/Indexes/KonqBookmarkIndex
8.0K    /home/craig/.beagle/Indexes/BlamIndex/SecondaryIndex
8.0K    /home/craig/.beagle/Indexes/BlamIndex/PrimaryIndex
4.0K    /home/craig/.beagle/Indexes/BlamIndex/Locks
32K     /home/craig/.beagle/Indexes/BlamIndex
8.0K    /home/craig/.beagle/Indexes/KOrganizerIndex/SecondaryIndex
8.0K    /home/craig/.beagle/Indexes/KOrganizerIndex/PrimaryIndex
4.0K    /home/craig/.beagle/Indexes/KOrganizerIndex/Locks
32K     /home/craig/.beagle/Indexes/KOrganizerIndex
8.0K    /home/craig/.beagle/Indexes/KNotesIndex/SecondaryIndex
8.0K    /home/craig/.beagle/Indexes/KNotesIndex/PrimaryIndex
4.0K    /home/craig/.beagle/Indexes/KNotesIndex/Locks
32K     /home/craig/.beagle/Indexes/KNotesIndex
8.0K    /home/craig/.beagle/Indexes/KopeteIndex/SecondaryIndex
8.0K    /home/craig/.beagle/Indexes/KopeteIndex/PrimaryIndex
4.0K    /home/craig/.beagle/Indexes/KopeteIndex/Locks
32K     /home/craig/.beagle/Indexes/KopeteIndex
8.0K    /home/craig/.beagle/Indexes/AkregatorIndex/SecondaryIndex
8.0K    /home/craig/.beagle/Indexes/AkregatorIndex/PrimaryIndex
4.0K    /home/craig/.beagle/Indexes/AkregatorIndex/Locks
32K     /home/craig/.beagle/Indexes/AkregatorIndex
96K     /home/craig/.beagle/Indexes/EvolutionMailIndex/SecondaryIndex
1.4M    /home/craig/.beagle/Indexes/EvolutionMailIndex/PrimaryIndex
4.0K    /home/craig/.beagle/Indexes/EvolutionMailIndex/Locks
1.5M    /home/craig/.beagle/Indexes/EvolutionMailIndex
8.0K    /home/craig/.beagle/Indexes/LifereaIndex/SecondaryIndex
8.0K    /home/craig/.beagle/Indexes/LifereaIndex/PrimaryIndex
4.0K    /home/craig/.beagle/Indexes/LifereaIndex/Locks
32K     /home/craig/.beagle/Indexes/LifereaIndex
8.0K    /home/craig/.beagle/Indexes/KMailIndex/SecondaryIndex
8.0K    /home/craig/.beagle/Indexes/KMailIndex/PrimaryIndex
4.0K    /home/craig/.beagle/Indexes/KMailIndex/Locks
32K     /home/craig/.beagle/Indexes/KMailIndex
8.0K    /home/craig/.beagle/Indexes/EvolutionDataServerIndex/SecondaryIndex
88K     /home/craig/.beagle/Indexes/EvolutionDataServerIndex/PrimaryIndex
4.0K    /home/craig/.beagle/Indexes/EvolutionDataServerIndex/Locks
4.0K    /home/craig/.beagle/Indexes/EvolutionDataServerIndex/Photos
116K    /home/craig/.beagle/Indexes/EvolutionDataServerIndex
8.0K    /home/craig/.beagle/Indexes/GaimLogIndex/SecondaryIndex
8.0K    /home/craig/.beagle/Indexes/GaimLogIndex/PrimaryIndex
4.0K    /home/craig/.beagle/Indexes/GaimLogIndex/Locks
32K     /home/craig/.beagle/Indexes/GaimLogIndex
8.0K    /home/craig/.beagle/Indexes/TomboyIndex/SecondaryIndex
16K     /home/craig/.beagle/Indexes/TomboyIndex/PrimaryIndex
4.0K    /home/craig/.beagle/Indexes/TomboyIndex/Locks
48K     /home/craig/.beagle/Indexes/TomboyIndex
8.0K    /home/craig/.beagle/Indexes/KonqHistoryIndex/SecondaryIndex
128K    /home/craig/.beagle/Indexes/KonqHistoryIndex/PrimaryIndex
4.0K    /home/craig/.beagle/Indexes/KonqHistoryIndex/Locks
272K    /home/craig/.beagle/Indexes/KonqHistoryIndex
6.3M    /home/craig/.beagle/Indexes
24K     /home/craig/.beagle/TextCache/b3
8.0K    /home/craig/.beagle/TextCache/2a
8.0K    /home/craig/.beagle/TextCache/c2
28K     /home/craig/.beagle/TextCache/a5
88K     /home/craig/.beagle/TextCache/93
16K     /home/craig/.beagle/TextCache/7f
64K     /home/craig/.beagle/TextCache/1f
20K     /home/craig/.beagle/TextCache/8c
20K     /home/craig/.beagle/TextCache/9d
24K     /home/craig/.beagle/TextCache/51
16K     /home/craig/.beagle/TextCache/f8
20K     /home/craig/.beagle/TextCache/cc
20K     /home/craig/.beagle/TextCache/0e
8.0K    /home/craig/.beagle/TextCache/11
28K     /home/craig/.beagle/TextCache/21
12K     /home/craig/.beagle/TextCache/b8
20K     /home/craig/.beagle/TextCache/bd
16K     /home/craig/.beagle/TextCache/c6
4.0K    /home/craig/.beagle/TextCache/be
36K     /home/craig/.beagle/TextCache/78
12K     /home/craig/.beagle/TextCache/ff
36K     /home/craig/.beagle/TextCache/f5
8.0K    /home/craig/.beagle/TextCache/5f
20K     /home/craig/.beagle/TextCache/c0
16K     /home/craig/.beagle/TextCache/6f
4.0K    /home/craig/.beagle/TextCache/c9
20K     /home/craig/.beagle/TextCache/1d
28K     /home/craig/.beagle/TextCache/99
40K     /home/craig/.beagle/TextCache/1b
24K     /home/craig/.beagle/TextCache/70
16K     /home/craig/.beagle/TextCache/bb
24K     /home/craig/.beagle/TextCache/ac
20K     /home/craig/.beagle/TextCache/3f
16K     /home/craig/.beagle/TextCache/dc
8.0K    /home/craig/.beagle/TextCache/b1
12K     /home/craig/.beagle/TextCache/e3
16K     /home/craig/.beagle/TextCache/88
32K     /home/craig/.beagle/TextCache/63
52K     /home/craig/.beagle/TextCache/36
28K     /home/craig/.beagle/TextCache/44
20K     /home/craig/.beagle/TextCache/03
24K     /home/craig/.beagle/TextCache/17
48K     /home/craig/.beagle/TextCache/aa
32K     /home/craig/.beagle/TextCache/bc
12K     /home/craig/.beagle/TextCache/b2
8.0K    /home/craig/.beagle/TextCache/0d
8.0K    /home/craig/.beagle/TextCache/95
16K     /home/craig/.beagle/TextCache/c8
40K     /home/craig/.beagle/TextCache/0b
16K     /home/craig/.beagle/TextCache/04
4.0K    /home/craig/.beagle/TextCache/ce
12K     /home/craig/.beagle/TextCache/f6
28K     /home/craig/.beagle/TextCache/37
16K     /home/craig/.beagle/TextCache/86
28K     /home/craig/.beagle/TextCache/c7
12K     /home/craig/.beagle/TextCache/4d
20K     /home/craig/.beagle/TextCache/e5
16K     /home/craig/.beagle/TextCache/42
8.0K    /home/craig/.beagle/TextCache/90
32K     /home/craig/.beagle/TextCache/af
32K     /home/craig/.beagle/TextCache/9e
20K     /home/craig/.beagle/TextCache/94
12K     /home/craig/.beagle/TextCache/8b
40K     /home/craig/.beagle/TextCache/cd
16K     /home/craig/.beagle/TextCache/c1
28K     /home/craig/.beagle/TextCache/71
16K     /home/craig/.beagle/TextCache/a3
28K     /home/craig/.beagle/TextCache/d2
12K     /home/craig/.beagle/TextCache/e2
16K     /home/craig/.beagle/TextCache/73
8.0K    /home/craig/.beagle/TextCache/4a
56K     /home/craig/.beagle/TextCache/23
16K     /home/craig/.beagle/TextCache/2c
40K     /home/craig/.beagle/TextCache/34
8.0K    /home/craig/.beagle/TextCache/55
20K     /home/craig/.beagle/TextCache/83
20K     /home/craig/.beagle/TextCache/12
36K     /home/craig/.beagle/TextCache/6d
20K     /home/craig/.beagle/TextCache/13
12K     /home/craig/.beagle/TextCache/27
36K     /home/craig/.beagle/TextCache/26
36K     /home/craig/.beagle/TextCache/df
8.0K    /home/craig/.beagle/TextCache/ee
20K     /home/craig/.beagle/TextCache/2d
20K     /home/craig/.beagle/TextCache/79
20K     /home/craig/.beagle/TextCache/85
12K     /home/craig/.beagle/TextCache/e8
28K     /home/craig/.beagle/TextCache/48
48K     /home/craig/.beagle/TextCache/e1
16K     /home/craig/.beagle/TextCache/76
8.0K    /home/craig/.beagle/TextCache/eb
12K     /home/craig/.beagle/TextCache/56
12K     /home/craig/.beagle/TextCache/5e
40K     /home/craig/.beagle/TextCache/30
12K     /home/craig/.beagle/TextCache/1a
12K     /home/craig/.beagle/TextCache/89
4.0K    /home/craig/.beagle/TextCache/31
24K     /home/craig/.beagle/TextCache/00
4.0K    /home/craig/.beagle/TextCache/d6
20K     /home/craig/.beagle/TextCache/92
8.0K    /home/craig/.beagle/TextCache/60
20K     /home/craig/.beagle/TextCache/ae
8.0K    /home/craig/.beagle/TextCache/7d
20K     /home/craig/.beagle/TextCache/52
24K     /home/craig/.beagle/TextCache/e4
20K     /home/craig/.beagle/TextCache/4f
24K     /home/craig/.beagle/TextCache/a9
24K     /home/craig/.beagle/TextCache/a0
28K     /home/craig/.beagle/TextCache/6e
32K     /home/craig/.beagle/TextCache/49
12K     /home/craig/.beagle/TextCache/b7
16K     /home/craig/.beagle/TextCache/fd
24K     /home/craig/.beagle/TextCache/c5
12K     /home/craig/.beagle/TextCache/2b
12K     /home/craig/.beagle/TextCache/9f
32K     /home/craig/.beagle/TextCache/01
24K     /home/craig/.beagle/TextCache/5a
20K     /home/craig/.beagle/TextCache/25
12K     /home/craig/.beagle/TextCache/0f
40K     /home/craig/.beagle/TextCache/6b
48K     /home/craig/.beagle/TextCache/84
4.0K    /home/craig/.beagle/TextCache/e6
20K     /home/craig/.beagle/TextCache/96
4.0K    /home/craig/.beagle/TextCache/a6
60K     /home/craig/.beagle/TextCache/c4
12K     /home/craig/.beagle/TextCache/14
40K     /home/craig/.beagle/TextCache/69
8.0K    /home/craig/.beagle/TextCache/05
20K     /home/craig/.beagle/TextCache/4e
12K     /home/craig/.beagle/TextCache/77
8.0K    /home/craig/.beagle/TextCache/65
20K     /home/craig/.beagle/TextCache/98
32K     /home/craig/.beagle/TextCache/ea
40K     /home/craig/.beagle/TextCache/8a
8.0K    /home/craig/.beagle/TextCache/59
36K     /home/craig/.beagle/TextCache/32
28K     /home/craig/.beagle/TextCache/3b
16K     /home/craig/.beagle/TextCache/d9
20K     /home/craig/.beagle/TextCache/24
12K     /home/craig/.beagle/TextCache/db
20K     /home/craig/.beagle/TextCache/bf
20K     /home/craig/.beagle/TextCache/9c
28K     /home/craig/.beagle/TextCache/40
20K     /home/craig/.beagle/TextCache/64
12K     /home/craig/.beagle/TextCache/ef
20K     /home/craig/.beagle/TextCache/53
16K     /home/craig/.beagle/TextCache/19
24K     /home/craig/.beagle/TextCache/0c
24K     /home/craig/.beagle/TextCache/08
32K     /home/craig/.beagle/TextCache/02
24K     /home/craig/.beagle/TextCache/29
36K     /home/craig/.beagle/TextCache/7b
12K     /home/craig/.beagle/TextCache/43
12K     /home/craig/.beagle/TextCache/b5
44K     /home/craig/.beagle/TextCache/d1
20K     /home/craig/.beagle/TextCache/62
20K     /home/craig/.beagle/TextCache/d7
36K     /home/craig/.beagle/TextCache/15
24K     /home/craig/.beagle/TextCache/fe
12K     /home/craig/.beagle/TextCache/67
24K     /home/craig/.beagle/TextCache/ab
12K     /home/craig/.beagle/TextCache/28
28K     /home/craig/.beagle/TextCache/0a
36K     /home/craig/.beagle/TextCache/9b
24K     /home/craig/.beagle/TextCache/fc
12K     /home/craig/.beagle/TextCache/a4
28K     /home/craig/.beagle/TextCache/c3
20K     /home/craig/.beagle/TextCache/45
24K     /home/craig/.beagle/TextCache/4c
24K     /home/craig/.beagle/TextCache/a1
40K     /home/craig/.beagle/TextCache/b6
40K     /home/craig/.beagle/TextCache/fb
12K     /home/craig/.beagle/TextCache/22
20K     /home/craig/.beagle/TextCache/ad
8.0K    /home/craig/.beagle/TextCache/7c
12K     /home/craig/.beagle/TextCache/97
28K     /home/craig/.beagle/TextCache/18
8.0K    /home/craig/.beagle/TextCache/1c
36K     /home/craig/.beagle/TextCache/57
16K     /home/craig/.beagle/TextCache/16
24K     /home/craig/.beagle/TextCache/3c
20K     /home/craig/.beagle/TextCache/3e
28K     /home/craig/.beagle/TextCache/2f
28K     /home/craig/.beagle/TextCache/d5
16K     /home/craig/.beagle/TextCache/66
20K     /home/craig/.beagle/TextCache/fa
28K     /home/craig/.beagle/TextCache/cf
16K     /home/craig/.beagle/TextCache/8d
28K     /home/craig/.beagle/TextCache/f9
20K     /home/craig/.beagle/TextCache/80
28K     /home/craig/.beagle/TextCache/68
44K     /home/craig/.beagle/TextCache/ba
32K     /home/craig/.beagle/TextCache/f7
24K     /home/craig/.beagle/TextCache/f4
32K     /home/craig/.beagle/TextCache/07
28K     /home/craig/.beagle/TextCache/9a
36K     /home/craig/.beagle/TextCache/50
44K     /home/craig/.beagle/TextCache/1e
28K     /home/craig/.beagle/TextCache/38
12K     /home/craig/.beagle/TextCache/7e
12K     /home/craig/.beagle/TextCache/5c
16K     /home/craig/.beagle/TextCache/39
28K     /home/craig/.beagle/TextCache/33
28K     /home/craig/.beagle/TextCache/d3
24K     /home/craig/.beagle/TextCache/82
4.0K    /home/craig/.beagle/TextCache/d0
28K     /home/craig/.beagle/TextCache/d4
12K     /home/craig/.beagle/TextCache/ed
24K     /home/craig/.beagle/TextCache/da
20K     /home/craig/.beagle/TextCache/3a
20K     /home/craig/.beagle/TextCache/61
8.0K    /home/craig/.beagle/TextCache/8e
28K     /home/craig/.beagle/TextCache/ec
48K     /home/craig/.beagle/TextCache/3d
36K     /home/craig/.beagle/TextCache/46
24K     /home/craig/.beagle/TextCache/10
20K     /home/craig/.beagle/TextCache/58
12K     /home/craig/.beagle/TextCache/72
24K     /home/craig/.beagle/TextCache/74
12K     /home/craig/.beagle/TextCache/4b
56K     /home/craig/.beagle/TextCache/a8
44K     /home/craig/.beagle/TextCache/35
32K     /home/craig/.beagle/TextCache/09
12K     /home/craig/.beagle/TextCache/e7
32K     /home/craig/.beagle/TextCache/e9
24K     /home/craig/.beagle/TextCache/75
12K     /home/craig/.beagle/TextCache/20
20K     /home/craig/.beagle/TextCache/91
16K     /home/craig/.beagle/TextCache/a7
20K     /home/craig/.beagle/TextCache/b4
28K     /home/craig/.beagle/TextCache/a2
20K     /home/craig/.beagle/TextCache/b9
28K     /home/craig/.beagle/TextCache/f3
36K     /home/craig/.beagle/TextCache/f0
16K     /home/craig/.beagle/TextCache/41
12K     /home/craig/.beagle/TextCache/6a
28K     /home/craig/.beagle/TextCache/d8
4.0K    /home/craig/.beagle/TextCache/2e
20K     /home/craig/.beagle/TextCache/de
32K     /home/craig/.beagle/TextCache/54
24K     /home/craig/.beagle/TextCache/5d
12K     /home/craig/.beagle/TextCache/47
24K     /home/craig/.beagle/TextCache/87
24K     /home/craig/.beagle/TextCache/f2
8.0K    /home/craig/.beagle/TextCache/f1
16K     /home/craig/.beagle/TextCache/6c
16K     /home/craig/.beagle/TextCache/cb
12K     /home/craig/.beagle/TextCache/81
24K     /home/craig/.beagle/TextCache/ca
20K     /home/craig/.beagle/TextCache/5b
8.0K    /home/craig/.beagle/TextCache/dd
12K     /home/craig/.beagle/TextCache/8f
8.0K    /home/craig/.beagle/TextCache/7a
28K     /home/craig/.beagle/TextCache/06
24K     /home/craig/.beagle/TextCache/e0
12K     /home/craig/.beagle/TextCache/b0
6.4M    /home/craig/.beagle/TextCache
15M     /home/craig/.beagle
100K    /home/craig/.nautilus/metafiles
1.1M    /home/craig/.nautilus
8.0K    /home/craig/.ggz
13G     /home/craig
13G     /home

Having looked at the sytem monitor info I'm seeing that the /home directory is still 100% full... I don't understand why though!

---

### Post by taurus on 2007-10-06
Looks like /home/craig/.thumbnails is taking up a lot of space.  

What's the output of this command from a terminal?

```
df -h
```

---

### Post by Bluecube on 2007-10-06
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              80G  5.8G   70G   8% /
varrun               1014M  104K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
udev                 1014M  160K 1013M   1% /dev
devshm               1014M     0 1014M   0% /dev/shm
lrm                  1014M   34M  980M   4% /lib/modules/2.6.22-13-generic/volatile
/dev/sda1              28G   27G     0 100% /home
/dev/hdb5              68G   17G   48G  27% /media/GeneralFiles
/dev/hdb1              67G   18G   46G  29% /media/Music
/dev/hdb6              43G   13G   29G  31% /media/Video
/dev/hdb7              10G  2.0G  7.5G  21% /media/Pictures

This pretty much backs up what I've been saying. However I don't know what's taking up all the space. The thumbnails are way less than a Gb.

---

### Post by thirddeep on 2007-10-06
Do :
```
cd ~
du -hsx *
```
Then you will know where your filling up ...

Thd.

---

### Post by taurus on 2007-10-06
How about

```
ls -la ~
du -h ~/.Trash
```

---

### Post by Bluecube on 2007-10-06
Ouput as per Thirddeep's suggestion -
65M     Desktop
4.0K    Documents
151M    Downloads
4.0K    edid.bin
0       Examples
4.0K    games
4.0K    Music
264K    nautilus-debug-log.txt
176K    PB_UploaderApplet.log
0       Photos
16K     PicasaDocuments
4.0K    Pictures
4.0K    Public
4.0K    Templates
4.0K    Videos
5.2M    Wallpapers

Output as per Taurus -
65M     Desktop
4.0K    Documents
151M    Downloads
4.0K    edid.bin
0       Examples
4.0K    games
4.0K    Music
264K    nautilus-debug-log.txt
176K    PB_UploaderApplet.log
0       Photos
16K     PicasaDocuments
4.0K    Pictures
4.0K    Public
4.0K    Templates
4.0K    Videos
5.2M    Wallpapers
craig@Winter:~$ ls -la ~
total 928
drwxr-xr-x 72 craig craig   4096 2007-10-06 20:57 .
drwxr-xr-x  6 root  root    4096 2007-10-06 17:41 ..
-rw-------  1 craig craig   5875 2007-10-06 17:52 .bash_history
-rw-r--r--  1 craig craig    220 2007-07-18 18:46 .bash_logout
-rw-r--r--  1 craig craig   2298 2007-07-18 18:46 .bashrc
drwx------  7 craig users   4096 2007-10-06 20:33 .beagle
drwxr-xr-x  2 craig users   4096 2007-09-01 18:26 .bluefish
drwx------  2 craig users   4096 2007-09-22 17:50 .btanks
drwxr-xr-x  3 craig users   4096 2007-09-06 09:26 .cache
drwxr-xr-x  2 craig craig   4096 2007-07-18 19:42 .compizconfig
drwx------  7 craig craig   4096 2007-08-31 21:19 .config
drwx------  2 craig users   4096 2007-07-21 09:17 .cups
drwx------  3 craig users   4096 2007-08-15 22:15 .dbus
drwx------  2 craig users   4096 2007-10-04 15:12 .dbus-keyrings
drwxr-x---  2 craig users   4096 2007-10-04 15:22 .defcon
drwxr-xr-x  4 craig craig   4096 2007-10-06 12:50 Desktop
-rw-------  1 craig users     25 2007-10-06 20:31 .dmrc
drwxr-xr-x  2 craig users   4096 2007-09-06 18:22 Documents
drwxr-xr-x  4 craig users   4096 2007-09-05 22:04 Downloads
-rw-r-----  1 craig craig    256 2007-07-18 19:45 edid.bin
drwxr-xr-x  4 craig users   4096 2007-09-08 08:53 .emerald
-rw-------  1 craig craig     16 2007-07-18 19:03 .esd_auth
drwx------  8 craig craig   4096 2007-10-06 20:39 .evolution
drwxr-xr-x  5 craig users   4096 2007-07-26 15:53 .exaile
lrwxrwxrwx  1 craig craig     26 2007-07-18 18:46 Examples -> /usr/share/example-content
drwxr-xr-x  2 craig craig   4096 2007-09-21 22:40 .fontconfig
-rw-r--r--  1 craig users    514 2007-09-25 22:46 .fonts.conf
drwxr-xr-x  4 craig users   4096 2007-09-15 15:53 .galeon
drwxr-xr-x  2 craig users   4096 2007-09-01 18:34 games
drwx------  6 craig craig   4096 2007-10-06 20:31 .gconf
drwx------  2 craig craig   4096 2007-10-06 20:34 .gconfd
drwxr-xr-x  8 craig users   4096 2007-09-16 15:09 .gdesklets
drwx------  2 craig users   4096 2007-09-21 22:51 .ggz
drwxr-xr-x 21 craig users   4096 2007-08-21 20:23 .gimp-2.2
drwxr-xr-x 20 craig users   4096 2007-09-06 18:56 .gimp-2.3
drwxr-xr-x 20 craig users   4096 2007-09-23 17:44 .gimp-2.4
-rw-r-----  1 craig craig      0 2007-10-06 17:50 .gksu.lock
drwxr-xr-x  3 craig craig   4096 2007-07-18 19:03 .gnome
drwx------ 19 craig craig   4096 2007-10-06 17:56 .gnome2
drwx------  2 craig craig   4096 2007-07-19 20:32 .gnome2_private
drwx------  2 craig craig   4096 2007-07-18 19:06 .gnupg
drwxr-xr-x  2 craig craig   4096 2007-10-06 12:42 .gstreamer-0.10
-rw-r--r--  1 craig users     56 2007-10-06 20:31 .gtk-bookmarks
-rw-r--r--  1 craig craig     87 2007-07-18 19:03 .gtkrc-1.2-gnome2
-rw-------  1 craig users    159 2007-10-06 20:31 .ICEauthority
drwxr-xr-x  3 craig craig   4096 2007-09-16 12:08 .icons
drwxr-xr-x  3 craig users   4096 2007-09-09 10:56 .java
drwxr-xr-x  2 craig users   4096 2007-09-04 19:55 .kchmviewer
drwx------  4 craig users   4096 2007-08-15 22:16 .kde
-rw-------  1 craig users    154 2007-09-25 22:46 .kderc
drwx------  3 craig users   4096 2007-07-22 18:14 .local
drwx------  3 craig users   4096 2007-08-03 22:14 .loki
drwxr-xr-x  6 craig users   4096 2007-07-26 22:26 .lyrics
drwx------  3 craig craig   4096 2007-07-19 20:38 .macromedia
drwxr-xr-x  3 craig users   4096 2007-08-14 17:52 .mcop
-rw-------  1 craig users     31 2007-09-01 10:19 .mcoprc
drwx------  3 craig craig   4096 2007-07-18 19:03 .metacity
drwx------  4 craig craig   4096 2007-08-12 15:01 .mozilla
drwxr-xr-x  2 craig users   4096 2007-08-31 21:19 Music
drwxr-xr-x  3 craig craig  12288 2007-10-06 17:56 .nautilus
-rw-r--r--  1 craig users 266240 2007-09-19 18:20 nautilus-debug-log.txt
-rw-r--r--  1 craig craig   1044 2007-08-23 09:40 .nvidia-settings-rc
drwx------  3 craig users   4096 2007-10-04 16:05 .openoffice.org2
-rw-r--r--  1 craig users 176005 2007-10-02 23:43 PB_UploaderApplet.log
lrwxrwxrwx  1 craig users     15 2007-09-16 21:17 Photos -> /media/Pictures
drwxr-xr-x  4 craig users   4096 2007-09-16 22:16 .picasa
drwxr-xr-x  5 craig users   4096 2007-09-16 22:11 PicasaDocuments
drwxr-xr-x  2 craig users   4096 2007-08-31 21:19 Pictures
-rw-r--r--  1 craig craig    566 2007-07-18 18:46 .profile
drwxr-xr-x  2 craig users   4096 2007-08-31 21:19 Public
-rw-------  1 craig users    256 2007-10-04 12:50 .pulse-cookie
drwx------  3 craig users   4096 2007-09-02 21:52 .purple
drwxr-xr-x  2 craig craig   4096 2007-10-02 22:09 .qt
-rw-------  1 craig users  14755 2007-10-04 15:55 .recently-used
-rw-r--r--  1 craig users  67939 2007-10-06 17:56 .recently-used.xbel
drwxr-xr-x  3 craig users   4096 2007-09-02 22:31 .scribus
drwx------  2 craig users   4096 2007-10-06 20:33 .spamassassin
-rw-r--r--  1 craig craig      0 2007-07-18 19:03 .sudo_as_admin_successful
drwxr-xr-x  2 craig users   4096 2007-08-31 21:19 Templates
drwxr-xr-x  3 craig craig   4096 2007-09-16 12:20 .themes
drwx------  5 craig craig   4096 2007-07-26 15:35 .thumbnails
drwxr-xr-x  4 craig users   4096 2007-10-01 21:53 .tomboy
-rw-r--r--  1 craig users   5083 2007-10-01 22:24 .tomboy.log
drwx------  2 craig craig  12288 2007-10-06 17:41 .Trash
drwxr-xr-x  3 craig users   4096 2007-08-03 22:15 .tremulous
-rw-r--r--  1 craig users    721 2007-08-05 22:27 .ufrawrc
drwxr-xr-x  2 craig craig   4096 2007-07-18 19:54 .update-manager-core
drwx------  2 craig craig   4096 2007-07-20 20:11 .update-notifier
drwxr-xr-x  2 craig users   4096 2007-08-31 21:19 Videos
drwxr-xr-x  4 craig craig   4096 2007-09-04 18:37 .VirtualBox
drwxr-xr-x  3 craig users   4096 2007-07-22 18:14 .vlc
drwxr-xr-x  2 craig users   4096 2007-08-23 09:56 .vmware
drwx------  2 craig users   4096 2007-09-01 18:31 .w3m
drwx------  2 craig craig   4096 2007-09-02 15:35 Wallpapers
drwxr-xr-x  2 craig users   4096 2007-10-06 20:31 .wapi
drwxr-xr-x  4 craig users   4096 2007-09-30 15:03 .wine
-rw-------  1 craig users    117 2007-10-06 20:31 .Xauthority
drwxr-xr-x  2 craig users   4096 2007-08-14 16:44 .xine
-rw-r--r--  1 craig users  16384 2007-10-06 21:00 .xsession-errors

In both outputs there is nothing to suggest what is hogging all the space...

---

### Post by taurus on 2007-10-06
```
du -h ~/.VirtualBox ~/.vmware ~/.wine
```

---

### Post by Bluecube on 2007-10-06
Virtualbox output -

12G     /home/craig/.VirtualBox/VDI
108K    /home/craig/.VirtualBox/Machines/XP MCE/Logs
253M    /home/craig/.VirtualBox/Machines/XP MCE/Snapshots
253M    /home/craig/.VirtualBox/Machines/XP MCE
152K    /home/craig/.VirtualBox/Machines/Vista/Logs
4.0K    /home/craig/.VirtualBox/Machines/Vista/Snapshots
164K    /home/craig/.VirtualBox/Machines/Vista
253M    /home/craig/.VirtualBox/Machines
12G     /home/craig/.VirtualBox

Seems the VDI's are taking up a lot of space - a damn sight more than what I expected by a long shot!!

I'll look into this further as this seems to have the solution to my problem. Many thanks for narrowing this down for me.

---

### Post by taurus on 2007-10-06
> **Bluecube said:**
> Virtualbox output -

12G     /home/craig/.VirtualBox/VDI
108K    /home/craig/.VirtualBox/Machines/XP MCE/Logs
253M    /home/craig/.VirtualBox/Machines/XP MCE/Snapshots
253M    /home/craig/.VirtualBox/Machines/XP MCE
152K    /home/craig/.VirtualBox/Machines/Vista/Logs
4.0K    /home/craig/.VirtualBox/Machines/Vista/Snapshots
164K    /home/craig/.VirtualBox/Machines/Vista
253M    /home/craig/.VirtualBox/Machines
12G     /home/craig/.VirtualBox

Seems the VDI's are taking up a lot of space - a damn sight more than what I expected by a long shot!!

I'll look into this further as this seems to have the solution to my problem. Many thanks for narrowing this down for me.

Well, you have both XP and Vista running in VirtualBox so there goes the space!

---

### Post by Bluecube on 2007-10-06
Yup! Vista took up 7Gb!! Ouch.

---

