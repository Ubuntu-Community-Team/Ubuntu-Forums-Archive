---
title: "Problem with bittorrent client?"
date: 2007-04-27
forum: General Help
---

### Post by ccw127 on 2007-04-27
This is perhaps one of those 'dumb' questions, and the solution is just alluding me (being simple and all...); I can't seem to start more than one bittorrent download at a time. Whenever I try to start another download after one is already running, I get the error:

Couldn't listen
98, 'Address already in use'

an issue with ports not open? What am I missing?

<*mutters at vague error messages....>

Chris

---

### Post by KrazyPenguin on 2007-04-27
What bittorrent client are you using???

I like azureus, just drag the torrent file onto it and drop, press ok and it starts.

---

### Post by CocoAUS on 2007-04-27
It sounds like you're using just the pre-installed Gnome BitTorrent client?

Try using an application such as Azureus, Deluge, or KTorrent to manage multiple torrents.  I don't know of a way to configure the pre-installed client to handle multiple downloads.

---

### Post by CocoAUS on 2007-04-27
Scratch that, found the answer:

Apparently the Gnome client defaults to using only one port.  One port means one download.  To set the client up to use multiple ports, launch gconf-editor, and in /apps/gnome-btdownload/settings/, change the max port to something larger (try 6888 or something).

---

### Post by ccw127 on 2007-04-27
I was thinking that it was port related but I just went ahead and got azureus anyway (I like the interface).
Thanks for the info,
Chris

---

### Post by thunderkyss on 2007-05-22
THis may sound silly, but how do you start the gnome client??

I clicked on a torrent, and it started automatically. I shutdown the machine, then when I started it back up, I can't figure out how to start it again.

---

### Post by CocoAUS on 2007-05-23
The Gnome client doesn't keep track of the torrents.  To start the program, you'll have to double-click each of your .torrent files again.  It'll then check your progress on the file and resume downloading/uploading.

---

