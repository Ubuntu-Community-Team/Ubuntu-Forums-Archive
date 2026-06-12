---
title: "Teamspeak &quot;blocking my soundcard&quot;"
date: 2006-12-03
forum: General Help
---

### Post by Smokeymcpawt on 2006-12-03
Ok, i have teamspeak 2 Open and im connected to a server, i try to open xmms to listen to some music but i get an error stating:

> Please check that:
Your soundcard is configured properly
You have no correct output plugin selected
No other program is blocking your soundcard


When im already listening to music in xmms and i open teamspeak, i can't hear anything in teamspeak.

Is there a way to fix this, or am i left to choose one or the other?

My soundcard is a SoundMAX Digital Audio.

Thanks.

---

### Post by Smokeymcpawt on 2006-12-03
eh sorry, but bump.

---

### Post by strabes on 2006-12-03
I assume you're using alsa as your driver? You need to install alsa-oss: ```
sudo apt-get install alsa-oss
```

Then when you need to run more than one program with sound you just run it with "aoss" in front of the command: ```
aoss firefox
```

This prevents one certain program from monopolizing your sound card.

Hope this helps,
Alex

---

### Post by Smokeymcpawt on 2006-12-03
This works, but now my sound quality is terrible. There are snaps, crackles and pops (:)) all the time.


EDIT:

Only teamspeak has bad quality, i guess i can deal.

Thanks Alex, 

Jared

---

### Post by Smokeymcpawt on 2006-12-03
Ok, another problem:

Enemy territory sound dosnt work with aoss, any way to fix that?

---

### Post by robinl on 2006-12-03
For the sound quality issue you can experiment with alsamixer in terminal and lowering everything into green level.

PS: do you get muted microphone in TeamSpeak when you use aoss? I get that and I have no idea how to fix it

---

### Post by Smokeymcpawt on 2006-12-04
> **robinl said:**
> For the sound quality issue you can experiment with alsamixer in terminal and lowering everything into green level.

PS: do you get muted microphone in TeamSpeak when you use aoss? I get that and I have no idea how to fix it


No i don't, and thanks for the quality tip.

---

