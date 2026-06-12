---
title: "Tracker not indexing"
date: 2007-08-08
forum: General Help
---

### Post by jackn on 2007-08-08
I've recently installed Tracker, the desktop search appliction.

At this point, it seems not to be indexing. I don't know why.

Here are some observations.

Tracker starts automatcally at startup, as it should:
```
~$ ps aux | grep trac
user     5733  0.0  0.6  24656  3220 ?        SNl  06:36   0:00 trackerd
user     8557  0.0  0.1   2888   772 pts/0    R+   07:24   0:00 grep trac

```

While Tracker has 0 entities indexed, however, it is instantly 'done'  indexing:
```
08 Aug 2007, 06:37:15:350 - Fetching index stats...
08 Aug 2007, 06:37:15:352 - Total entities indexed : 0
08 Aug 2007, 06:37:15:354 - -----------------------

08 Aug 2007, 06:37:18:217 - starting indexing...
08 Aug 2007, 06:37:18:326 - flushing all words
08 Aug 2007, 06:37:18:327 - Finished indexing. Waiting for new events...

```

Indeed, trivial searches yield no results.

Here are two relevant lines from my tracker.cfg file:
```
WatchDirectoryRoots=/home 
NoWatchDirectory=/bin;/dev;/proc;/sbin;/vmlinuz

```

(The /home value is temporary, while testing. What I mean to have eventually is simply /. That's why some directories outside /home are kept out)

I must be missing something. How can I get Tracker to start indexing?

jackn

---

### Post by tbroderick on 2007-08-08
Do you have the GUI installed? Try running tracker-preferences and make sure enable indexing and enable watching is checked.

---

### Post by jackn on 2007-08-08
I'm not sure what you mean by the "GUI", tbroderick. Is it gnome or does tracker have its own?

As to Gnome, yes, I'm working with a GUI, but I do like the command line, which is why I reported observations from the command line.
But your advice led me to think I was missing some tracker components, so I searched 

```
~$ apt-cache search tracker
```
and installed anything relevant.

This included:

libdeskbar-tracker - metadata database, indexer and search tool - deskbar-applet plugin
libtrackerclient0 - metadata database, indexer and search tool - library
tracker-search-tool - metadata database, indexer and search tool - Gnome frontend
tracker-utils - metadata database, indexer and search tool - commandline tools

(some of which I guess I had already had, but some which were definitely new).

I had already had 
tracker - metadata database, indexer and search tool.

I did not install libtrackerclient-dev - metadata database, indexer and search tool - development files.


I restarted gnome.

As before, when I run
```
tracker-preferences
```
I get
```
bash: tracker-preferences: command not found
```

And still, no indexing, same observation as reported in the first post - Tracker had no indexed files, yet thinks it's done as soon as it starts.

Thank you, tbroderick, for your attention.

What can be done now?
jackn

---

### Post by jackn on 2007-08-12
bump

---

### Post by jackn on 2007-08-13
OK, paydirt.

The issue, I hate to say, was the absence of a semicolon in the 'watch/nowatch' lists in the .cfg file - there must be a semicolon at the end of the list, too, it seems...


So, to properly tell Tracker what you want indexed, and what not:
```
gedit .Tracker/tracker.cfg
```
and, there:

# List of directory roots to index and watch seperated by semicolons
WatchDirectoryRoots=dir1;dir2;dir3;
# List of directory roots to not index and not watch seperated by semicolons
NoWatchDirectory=dir1;dir2;dir3;

Personally, I set Tracker to index the root directory. I'd like to be able to search within config files, etc, for troubleshooting and learning purposes. I also kept out an image format and all directories which seem to contain only binary files:

```

WatchDirectoryRoots=/;
NoWatchDirectory=/bin;/vimlinuz;/proc;/bin;/sbin;*png;/dev;/lib;/tmp;/vmlinuz.old

```

This could probably be improved.
What do you think?

My mistake, BTW, was staring me in the face in my very first post...

[INDENT]> Here are two relevant lines from my tracker.cfg file:
WatchDirectoryRoots=/home
NoWatchDirectory=/bin;/dev;
/proc;/sbin;/vmlinuz[/INDENT]



Heartful thanks to Jamie McCracken, author of Tracks, and to Tshepang, for their help on the mailing list. 

jackn

---

