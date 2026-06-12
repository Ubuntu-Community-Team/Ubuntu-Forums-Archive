---
title: "No sound on Ubuntu 7.10"
date: 2008-04-21
forum: General Help
---

### Post by yaaman on 2008-04-21
Hello Everyone,

I am new to Linux and when I say new I mean I do not know anything about linux. A friend of mine installed Ubuntu on my Gateway 4530GZ Laptop. Now I can not hear any sound or hear some sound that I can barely hear it at all. But I can see videos. I have checked that nothing is muted. I believe I have a Intel 82801DB-ICH4 (Alsa mixer), from the Sound Preferences window. I have my ubuntu updated. Any help would be appreciated.

Thank You,
-yaaman:)

EDIT:Never mind I fixed the problem, my external amp was checked in volume settings

---

### Post by marufaberlin on 2008-04-21
I have the same problem, and on my system it was due to some randomly running pulseaudio processes.

run (in a terminal):
```

ps -aux (pipe sign, I'm on a mac) grep pulseaudio

```

if that comes up with results, run 
```

sudo kill PID

```
and replace PID with the number in the beginning of the upper line (should be long, 'bout 4 to 5digits).

---

### Post by ScorpKing on 2008-04-21
Maybe this will help - [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

