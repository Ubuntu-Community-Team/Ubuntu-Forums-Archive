---
title: "Ctrl-S and Ctrl-Q keys don't work on autostarted rtorrent"
date: 2007-05-28
forum: General Help
---

### Post by Nakkis on 2007-05-28
I followed the tutorial [here](http://libtorrent.rakshasa.no/wiki/RTorrentCommonTasks) to start an rtorrent + screen session with a init.d script. It works all fine but the keys used to quit and start torrents (Ctrl+S and Ctrl+Q) don't work. (maybe others too?). If I kill the init.d started rtorrent and start another manually the keys work fine. 

Any ideas?

---

### Post by konsole on 2007-05-31
did you read this? [http://libtorrent.rakshasa.no/wiki/RTorrentUserGuide#Addingandremovingtorrents](http://libtorrent.rakshasa.no/wiki/RTorrentUserGuide#Addingandremovingtorrents)

try to undefine these terminal mappings prior to executing screen & rtorrent in your init script.

good luck.

---

### Post by p-stone on 2007-08-24
konsole - 
I put in 

stty stop undef
stty start undef

in my script but it still doesn't work. If I manually run the commands and then resume my screen it works like a charm, but it'd be much nicer to have it part of the script. I've tried putting the commands before and after the line that executes rtorrent, it doesn't seem to make a difference, any suggestions?

---

### Post by loire280 on 2008-03-08
I'm a little late to this thread, but I'll post for Googlers like me...

If you hit Control-A followed by Control-F until "-flow" appears at the bottom left corner, the commands should work.  These are the flow control commands for screen.

I found this at the rtorrent user guide at the link posted below.

---

