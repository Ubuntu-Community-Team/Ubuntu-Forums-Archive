---
title: "Possible to make rtorrent the default .torrent application?"
date: 2007-05-10
forum: General Help
---

### Post by Meese on 2007-05-10
Direct to the question:  Is it possible to launch rtorrent as the default application for downloading .torrents?  Specifically, say when clicked from a weblink etc.

I am relatively new to the Ubuntu desktop, but Im quickly becoming a convert and Im trying to absorb every bit I can.  Ive used many different Torrent clients (Azureus, uTorrent/Wine, Deluge, Ktorrent, etc etc) and I keep coming back to rtorrent.  I would like, if possible, to be able to click a .torrent link from my favorite tracker site and have rTorrent automatically start in a term window with the .torrent file queued up.

Im perfectly happy with rTorrent as is, and will continue to use it both on my all my machines desktops or no.  Im just trying to streamline just a bit more.  I know Im only saving a couple 'clicks' beeing able to start it directly versus "copy link location" and pasteing.

---

### Post by last1 on 2007-05-10
I have my browser save all files to a particular directory, and the rtorrent application scans that directory for any torrents. Any saved files that are torrents get automatically loaded into rtorrent's queue and begin downloading. Pretty much the same thing, but you'd already have to have rtorrent running.

There's a part in your .rtorrent.rc file, located in your home directory, that looks like this
```
# Watch a directory for new torrents, restart torrents that have been
# copied back and stop those that have been deleted.

#schedule = watch_directory,10,10,load_start=~/Download/watch/*.torrent
```
It's probably just commented out, so uncomment that line and make the directory it checks be the directory firefox saves torrents to.

---

### Post by vascot on 2008-02-05
I use the following script. I set firefox to open the file with this script (application)

It uses screen, so you can close (per accident) your terminal window it yust runs, beside of that you can view it from another computer.

I user Eterm, because I love it, but you can use any other terminal (maybe you have to change some switches).

O, I set rtorrent so it use ~/watch as watch dir ;)
```

#!/bin/bash
if [ -n "$1" ]
then
    mv $1 ~/watch/
fi

Eterm -g 150x40 --buttonbar 0 --scrollbar-width 1 -e screen -d -R -S bt rtorrent

```

---

