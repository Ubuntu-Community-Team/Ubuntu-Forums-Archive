---
title: "MP4Box issue"
date: 2012-12-29
forum: General Help
---

### Post by taunnt on 2012-12-29
Hello I'm trying to join m4v files with ac3 audio track with MP4Box. What i do is this:

MP4Box -cat afcd1.m4v -cat afcd2.m4v -new afcd.m4v

and the video out is garbled video and the audio is fine. Is there a better program I should use, or do I need to install something to help MP4Box join m4v files?

Thanks

---

### Post by ron999 on 2012-12-29
> **taunnt said:**
> ... What i do is this:
MP4Box -cat afcd1.m4v -cat afcd2.m4v -new afcd.m4v

Hi
What about this command:-
```
MP4Box afcd1.m4v -cat afcd2.m4v -out afcd.m4v
```

---

### Post by taunnt on 2012-12-30
It's not the command that's doing it. I tried that and same kind of out put file. Garbled video and audio is fine. Don't know if Handbrake uses a weird codec to do the video, but for some odd reason MP4Box and Handbrake videos aren't agreeing.



> **ron999 said:**
> Hi
What about this command:-
```
MP4Box afcd1.m4v -cat afcd2.m4v -out afcd.m4v
```

---

