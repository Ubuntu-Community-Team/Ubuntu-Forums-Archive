---
title: "MP3/Xine problem in Dapper"
date: 2006-12-10
forum: General Help
---

### Post by izalac on 2006-12-10
I have a rather fresh install of Dapper. I turned on my computer today, picked up updates (only Automatix got updated), went to play some MP3s and got badly surprized when Amarok didn't work for me today.

Especially as it worked yesterday flawlessly.

When I tried to play files that were already in the playlist it said something about missing demux plugin. When I tried to make a new playlist, it claimed that I don't have MP3 support installed and offered to install it, crashing when I pressed yes.

I checked that I have all required packages installed manually, and I do. I tried to reboot computer, remove packages, install packages manually, re-run automatix, checked my sources.list, removed every package again, reinstalled it again, removed it again, reinstalled it etc... and nothing helped.

I tried Rhytmbox and my MP3s played as normal. I concluded that there's probably some problem in the Xine engine.

As I have totem-xine, I tried playing a MP3 file in Totem. It plays a first second of music and then stops with the following error message:

Totem could not play <filename>
There is no plugin to handle this movie.

If I try to open it in xine, it produces the following message output:

xine: found demuxer plugin: Elementary MPEG stream demux plugin
xine: found input plugin  : file input plugin
xine: couldn't find demux for >filename<
xine: found input plugin  : file input plugin
xine: found demuxer plugin: Elementary MPEG stream demux plugin
xine: found input plugin  : file input plugin

Now, the funniest part is, all movies I have play fine and with no sound problems, in both totem and xine...

Rhytmbox still works as it's based on gstreamer, I believe, but all xine-based apps just refuse to work with any MP3s I throw at them.

I'd appreciate any help... Amarok just got me spoiled and I'd like to get it running again.

---

