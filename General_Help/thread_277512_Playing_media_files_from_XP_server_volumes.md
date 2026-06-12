---
title: "Playing media files from XP server volumes?"
date: 2006-10-14
forum: General Help
---

### Post by Tamed_G on 2006-10-14
Hello all,

Well I'm loving Ubuntu so far although it's all a little unfamiliar (and my ATi x64 drivers are giving me hell).

I have a server running XP Pro sharing 5 hard drives where I store all of my media. I'd like to be able to play my files across the network in my media players in Ubuntu but they don't seem to like mounted volumes.

How can I acheive this?

Many thanks

G

---

### Post by taurus on 2006-10-14
Why don't you mount those harddrives/volumes using samba so you can access them from your Ubuntu machine!

---

### Post by finalbeta on 2006-10-14
Actually, totem, the default media player in ubuntu no longer plays files from samba shares. This is the case for edgy. Someone reported this for dapper 2.

I've created a bug report in launchpad and have taken it upstream : [http://bugzilla.gnome.org/show_bug.cgi?id=359133](http://bugzilla.gnome.org/show_bug.cgi?id=359133)
Let's hope this one get's fixed soon, so we can play our media from our media servers again.

---

### Post by taurus on 2006-10-14
Sorry but I never like totem!!!  I use xmms for my mp3s and mplayer for all my videos...

---

### Post by Tamed_G on 2006-10-15
All of the tutorials I seem to look at are referring to using Linux as the server and setting up Windows Clients - they also lose me about 99% of the time with the things they talk about.

I have the 5 hard drives setup as shared drives on the network on the XP machine, so anyone with network access can see them without needing user accounts to access them.

I can mount them through Gnome just fine on my desktop, but many applications refuse to look at network drives so I can't use them to play my media.

Can anyone give an example (or point me to one) for the absolute most basic setup to make them permanent mounts in the /mnt folder (or am I trying to do the wrong thing altogether?)

G

---

