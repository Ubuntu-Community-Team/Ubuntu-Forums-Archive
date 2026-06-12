---
title: "Unable to get ncmpc and sonata to read my mpd library."
date: 2008-01-19
forum: General Help
---

### Post by Gigamo on 2008-01-19
Since I reinstalled ubuntu I have nothing but trouble with mpd.

However, I got it running now.

The problem that remains is that I don't see my library in ncmpc or sonata (and yes I've specified the library in sonata/updated it/restarted sonata etc).

typing "mpc update" does nothing (i recall doing that on my previous install). What did work was "mpd --create-db", that gave a visual output in terminal of it loading all my songs, but I still don't have anything in ncmpc or sonata.

The way I specified my music directory in /etc/mpd.conf is the default /var/lib/mpd/music, and inside that folder I made a symbolic link to my Music directory.

And I also created a ~/.mpdconf in my home folder, this one directly pointing at my music directory.

Help appreciated.

---

