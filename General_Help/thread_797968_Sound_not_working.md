---
title: "Sound not working"
date: 2008-05-17
forum: General Help
---

### Post by Johnson on 2008-05-17
When I enter Ubuntu I hear the normal intro sound, right.

But when I try listen to the music on YouTube, the sound of the clips.
When I try to install World of Warcraft, no sound from the installation either, you always here some music from that, but no.

What is wrong here?

---

### Post by windoze87 on 2008-05-17
If you're having problems with Flash playing sound, try this...

```
sudo apt-get install alsa-oss
```

then, log into terminal (with firefox closed) and type

```
aoss firefox
```

thanks to BitTorrentBuddha for figuring this one out, you rock my socks :guitar: if you dont want to type that in every time you want to watch a Flash video, and you have a panel launcher for Firefox, you can do this. Right click your Firefox icon, click Properties. Beside "Command" you should see "firefox %u", just insert "aoss" before firefox. As for you WoW problem... idk... i have sound problems with Wine too lol so you can mark me as wanting to know the answer to that one too. Good luck!

---

### Post by Johnson on 2008-05-17
Did not work.

Hm, but is there another way to play WoW then using Wine?
I can't change any graphic without getting error and I see alot of graphic error, can't do anything. It's just so buggy.

---

### Post by windoze87 on 2008-05-17
hmm... do you have the latest version of Java installed? I believe it's version 6 (at least that's what I have). Check that, and if you have an earlier version, install 6 through Synaptic Package Manager. As far as WoW is concerned... as far as I know, WoW's designed to run on Windows or Mac only, and therefore to use it on GNU/Linux systems you need a compatibility engine like Wine. You could always try VMWare, but you have to pay for that, i believe. Maybe someone else more knowledgeable will come along, I only know basics plus a little when it comes to Linux, i'm still learning myself. Sorry i couldn't help :(

---

