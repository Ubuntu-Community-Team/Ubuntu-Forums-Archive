---
title: "How do I assign certain programs to file extensions?"
date: 2007-12-12
forum: General Help
---

### Post by pijiu on 2007-12-12
This might be a silly question but how do I assign file types to programs? For example in Firefox I want to set .torrent to KTorrent but I don't know where to find KTorrent in ubuntu, where are applications stored?

---

### Post by Steveway on 2007-12-12
Right-click a torrent-file on your PC > Choose Open with > look for Ktorrent/ if it isn't there then choose user-definied-command and type ktorrent in it.
Done.
The names of some of the buttons could vary because I don't have an english Ubuntu here.
Also if you want to open it with ktorrent everytime then put that checkmark there (Dunno how to translate what it says).

---

### Post by pijiu on 2007-12-12
Sure i've managed that but more specifically Firefox keeps trying to open .torrent files to the default bittorent client, when I go to assign it to ktorrent I can't find where Ktorrent is lol

---

### Post by Steveway on 2007-12-12
Try looking in /usr/bin or /usr/sbin.
Wait, a quick "locate ktorrent" in the terminal gave me this: /usr/bin/ktorrent
I almost forgot locate.
Just type in locate <filename> and it will spit out everything with that name.

---

