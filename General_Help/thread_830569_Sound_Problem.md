---
title: "Sound Problem"
date: 2008-06-15
forum: General Help
---

### Post by brycegg on 2008-06-15
Hello, I have a bunch of sound related questions here. :(

In hope to play sounds, I use alsa and I've gotten it to work in most cases.. But in some other cases it doesn't want to cooperate, and most of the applications use JACK, and require me to open JACK.. But JACK never opens the server, maybe because of applications using sound etc..

I tried this with Ardour, and if I'm lucky I can even get into the main screen.. I tried testing sounds(metronome) and it played, but at the same time, stuff using my alsa like aMSN, or media players stop playing

(jack uses the alsa, but it should share..)

also I've recently been trying recordMyDesktop, but It wont record sound no matter what i put into device, and jack doesn't want to open a server.

second question

WINE:

Almost anything besides FL Studio works, my NDS Emulator works flawlessly, in fact, I'm enjoying myself with it. But I used to make music on Windows, and I used FL Studio, I heard it worked in WINE, but whenever I load up FL Studio, it plays no sound, and strangely, altering the buffer rate, just increases the speed of the program, besides of what the tempo is set at.

Somehow I've gotten it to work, but it doesn't work anymore, and all i know is that in audio settings(WINE), i put it in ALSA and OSS.

Please help me! I feel like installing Windows just to use FL Studio.

---

### Post by Vivaldi Gloria on 2008-06-16
I don't know much about jack and the programs you mention but let me point out a couple of guides to you:

[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

[http://ubuntuforums.org/showthread.php?t=776739](http://ubuntuforums.org/showthread.php?t=776739)

I used the second thread to fix all my sound issues but the first thread is newer. Now I can start an OSS application with

```
padsp <some-oss-program>
```

and it plays fine. In particular, i chose OSS in wine and i use this for wine apps.

Now all of the apps i have share sound.

---

