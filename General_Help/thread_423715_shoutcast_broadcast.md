---
title: "shoutcast broadcast?"
date: 2007-04-26
forum: General Help
---

### Post by SXR on 2007-04-26
I have a radio station allowing me to do a show online VIA shoutcast... I cannot figure out how to set up a broadcast from my ubuntu 7.04 box to their servers ?help please I am a little lost.

---

### Post by kerry_s on 2007-04-26
Did you try vlc?

---

### Post by SXR on 2007-04-28
I have VLC i didn't know you could broadcast from it 
can you explain how its done please ?:lolflag:

---

### Post by alchemist0 on 2008-07-17
Someone plz help with this one.....I want to know too.......:):biggrin: By the way....what happened to [www.xmms.org](www.xmms.org) :confused:??

---

### Post by atomkarinca on 2008-07-17
You can use [Internet DJ Console]("http://www.onlymeok.nildram.co.uk/") to broadcast to a shoutcast server.

```
sudo apt-get install idjc
```

---

### Post by alchemist0 on 2008-07-17
WOW!! LIGHT-SpEED FAST REPLY!!:lolflag: The thing is I have already tried it...However, im not sure about the settings....Im trying to broadcast to a specific server....does this have anything to do with that??\

Thanx in advance!

---

### Post by atomkarinca on 2008-07-17
You can see a brief description of how you can connect to a server [here]("http://www.onlymeok.nildram.co.uk/server.html").

---

### Post by alchemist0 on 2008-07-17
ok...now another question....idjc wont let me encode the stream to mp3...any ideas??

---

### Post by hellion0 on 2008-07-17
Ditto that. (Just saw the thread.) I saw options on how to set up the stream (type, host, port, etc.), but nothing for the encoder type/bitrate/frequency.

Running on Hardy, by the way. Grabbed the version from the repos.

---

### Post by alchemist0 on 2008-07-17
ok found the answer.....go here:

[http://www.onlymeok.nildram.co.uk/download.html](http://www.onlymeok.nildram.co.uk/download.html)

and download the package.
While running the

./configure 

command, u'll get some warnings concerning some missing packages.....use synaptic to install them, restart your system and cross ur fingers...Hopefully, this should do the trick. At least it worked for me.....:)

But now, another problem showed up....the sound of the audio broad casted is garbled...sounds like sh*t......HELP!!

---

### Post by alchemist0 on 2008-07-23
Forget idjc....thats the only way.....unfortunately......I tried Winamp via wine....works perfectly:guitar:

---

