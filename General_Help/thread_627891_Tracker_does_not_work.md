---
title: "Tracker does not work"
date: 2007-11-30
forum: General Help
---

### Post by johann_p on 2007-11-30
Tracker does not seem to work at all for me. Although it has been "active" (trackerd running) since weeks now and although I have my directories added in the config GUI, I get no hits whatsoever.

When I tried to stop the trackerd process and run it with optionb -v 2 from the command line I get many messages of the form:

Watching directory ..... (total watches = nnnn)

but after a while I get only messages of the form:

ERROR: Inotify watch on <path> has failed

I have noticed that after startup, there is a message:
"Setting inotify watch limit to 8191."

Now, this is ridiculously small. I have at leas about 40.000 directories to index, and even if I manually remove all those that are not really that necessary (using the "privacy" list of Tracker) I will still have many more than 8191.

But I could not find any setting anywhere how to increase that number.

I am using Beagle so far and Beagle never had a problem with the number of directories I index and worked quite well so far.

---

### Post by rainwalker on 2007-11-30
I switched to Beagle as well, and I love it
The only problem is that the Deskbar applet crashes if I try to use it with Beagle instead of Tracker

---

### Post by johann_p on 2007-12-01
I have in the meantime got a response on the tracker mailing list:

> 
/etc/sysctl.conf:
fs.inotify.max_user_watches=16384

(increase this number appropriately)
/etc/init.d/procps restart


That did solve my problems so far.

There seem to be subtle differences between the way tracker and beagle index the files, and which files, and there are differences between how results are displayed in their own query GUIs. 

Both have severe limitations and bugs, and both have points in their favor.

Tracker does not index my web pages (Beagle does through my beagle firefox extension). Tracker does not index my Thunderbird emails, Beagle does.

On the other hand I like the way Tracker shows results better, though the GUI is buggy (e.g. I cannot skip to the second page of the results).

Both have *very* lacking documentation and help. It would be good to know and to find out through help in the GUI how to limit the query to only the name or the file type, for example.

I also hate the way how one has to scroll through only small result lists in a cumbersome way, which is definitely worse in Beagle.

---

### Post by dbera on 2007-12-01
rainwalker, you are probably facing [http://bugzilla.gnome.org/show_bug.cgi?id=479091](http://bugzilla.gnome.org/show_bug.cgi?id=479091) - the bug was fixed in deskbar 2.20.2 - please update to it if it is available in gutsy or otherwise ask gutsy to provide an update for deskbar.

johann_p: there are some documentation about beagle in [http://beagle-project.org](http://beagle-project.org) For searching in names or by file types, there is unfortunately no GUI but you can use a rich query syntax to specify your query. The syntax rules are again given in [http://beagle-project.org](http://beagle-project.org)

---

### Post by rainwalker on 2007-12-01
> **dbera said:**
> rainwalker, you are probably facing [http://bugzilla.gnome.org/show_bug.cgi?id=479091](http://bugzilla.gnome.org/show_bug.cgi?id=479091) - the bug was fixed in deskbar 2.20.2 - please update to it if it is available in gutsy or otherwise ask gutsy to provide an update for deskbar.]

How do I do that?

---

