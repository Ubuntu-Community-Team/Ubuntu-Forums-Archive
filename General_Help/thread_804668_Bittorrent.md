---
title: "Bittorrent"
date: 2008-05-23
forum: General Help
---

### Post by jtlharrison on 2008-05-23
Before anyone claims i'm doing anything illegal, i'd like to reassure I need to know this info to update a game.

I'm on a university network and bittorrent downloads are blocked, I wonder if there is a way in ubuntu to trick the network into not noticing the download?

---

### Post by metallicamaster3 on 2008-05-23
try using a really high, random port, something about 40107. Also force encryption and don't allow legacy connections. Assuming you're using uTorrent or Transmission.

---

### Post by Rinzwind on 2008-05-23
It is impossible to answer without knowledge on how your university set up internet access.

IF they correctly log traffic and block access they will always know you are trying to download (be it torrents or other downloads). All you can do is try to use other ports/random ports but if the person that blocked access is worth his money you'll never get away with it. 

Oh and ... you should be busy with learning things you are suppose to learn. :lolflag:

---

### Post by jtlharrison on 2008-05-23
It recognises when programs load up and blocks internet access for 2 minutes, or at least I know that's the case in windows, transmission however doesn't result in the connection being cut. Also it recognises the connections and blocks.

---

### Post by jtlharrison on 2008-05-23
it also recognises when i download .torrent files

---

### Post by danwood76 on 2008-05-23
You could try using an SSH tunnel.
This is bound to work through their network (if they allow SSH) and is encrypted so they cant listen to it.

On my uni network a couple of years ago I used to be able to get bit torrent to work by using encryption and really good private tracker.
It worked because although they would attempt to block my TCP connections they only seemed to be able to stop me opening new ones and so I could still get data from the good seeds I was connected to.
I eventually used an SSH tunnel which just worked perfectly.

---

### Post by jtlharrison on 2008-05-23
how do i use an ssh tunnel?

---

### Post by danwood76 on 2008-05-23
Well you setup an SSH tunnel and send your bittorrent through it.

You need to have an SSH server, or an account with one to make it work, I used to use Disflux but I just had a look and they dont seem to exist anymore.
Google SSH tunnel and you should get some info, it is a little tricky to setup but once its going you will be able to use torrents.

It might be easier if you are just downloading game updates to talk to your network administartor about it, he/she may be able to open a port up for your game updates.

---

### Post by jtlharrison on 2008-05-23
I'd already asked them, the music/film companies must have really scared the uni, because they won't even allow legal bittorent downloads.

---

