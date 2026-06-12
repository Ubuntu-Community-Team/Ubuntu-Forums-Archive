---
title: "utorrent error : access Denied"
date: 2007-02-26
forum: General Help
---

### Post by ost on 2007-02-26
I am running utorrent via wine in edgy. On most of my torrents after about three minutes of downloading the download stops and I get "error access denied" On the wiki it says something about google toolbar blocking it but I think that mainly applies to windows users.

Any Suggestions?

Thanks
Jonathan


EDIT: If you get this error make sure that the UPnP mapping is not enabled. Look in options>Preferences>connection.

---

### Post by ost on 2007-02-26
Bump... anyone?


Thanks:popcorn:

---

### Post by zanglang on 2007-02-27
That sounds like utorrent was trying to write into cache or something. Are you sure your .wine's Program Files directory is writable... or you didn't install it somewhere you don't have write access to without sudo?

---

### Post by ost on 2007-02-27
Sorry for the delay, but I have wine writing into my a folder in home.

For some reason some torrents can be written, but others can't so I don't believe it is a permissions issue

Thanks again

---

### Post by feight on 2007-04-25
I tried multiple times in multiple ways, force check, force start, deleting and starting from scratch, and I could never figure out if the error meant the torrent was on a closed tracker or what, then I noticed the download started, and I'd get great speeds... but nothing saved, always ended at 0% even with the small tracker txt files. Finally created a separate folder from my other torrent and now it works fine. Some kind of disk writing error related to linux or wine?

---

### Post by tkat on 2008-02-23
I had the same problem, then I thought about it. All my successful downloads were ones that weren't in folders. So I manually created the folder for the torrent I was downloading, and now it works. *shrug* Must be some permissions thing. I was also downloading to a folder in /home

Changing the DL folder permission of the user (2nd permissions, below Owner) from "Access Files" only to "Create and delete files" fixed the problem for me

---

