---
title: "Rhythmbox not loading with a GLib-GObject-ERROR"
date: 2008-05-06
forum: General Help
---

### Post by imperius1 on 2008-05-06
After recently installing Hardy, I'm running into intermittent problems with Rhythmbox. Running 'rhythmbox --debug' occasionally results in an error like this:

GLib-GObject-ERROR **: g_type_plugin_*() invalidly modified type `TotemPlParser'
aborting...
Aborted

Sometimes it will generate a similar Glib-GObject-ERROR followed by a 'Segmentation fault'. I was having the same issue with Firefox, so I followed a post that recommended purging libflashsupport. I am experiencing less 'Segmentation fault's but am still seeing issues with Rhythmbox. I'd appreciate any suggestions, please.

---

### Post by imperius1 on 2008-05-08
UPDATE: Today, I removed the .gnome2/rhythmbox directory, which also removed the music and podcasts from my library. I imported all of my music, but did not add the podcasts. Everything seems to be working fine and I haven't received another one of these messages yet. It would appear that one (or several) of the podcasts I had added was causing the error. I'm going to try to slowly add the podcasts and see if I can reproduce the error. I'll keep you updated...

---

### Post by imperius1 on 2008-05-09
Yesterday, I added the most essential podcast feeds...
[INDENT][/INDENT][http://www.thelinuxlink.net/tllts/tllts.rss](http://www.thelinuxlink.net/tllts/tllts.rss)
[INDENT][/INDENT][http://www.lugradio.org/episodes.rss](http://www.lugradio.org/episodes.rss)
[INDENT][/INDENT][http://lottalinuxlinks.com/podcast/rss.xml](http://lottalinuxlinks.com/podcast/rss.xml)
[INDENT][/INDENT][http://feeds.feedburner.com/TheLinuxActionShow](http://feeds.feedburner.com/TheLinuxActionShow)
[INDENT][/INDENT][http://feeds.feedburner.com/linuxbasement](http://feeds.feedburner.com/linuxbasement)
...and FAIL. Rhythmbox crashed four times as it was loading, this morning. I completely removed all of the podcasts and will see how it goes. I'll take any other suggestions...

---

