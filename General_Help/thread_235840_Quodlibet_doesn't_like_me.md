---
title: "Quodlibet doesn't like me"
date: 2006-08-13
forum: General Help
---

### Post by Wallakoala on 2006-08-13
I decided to try quodlibet out, and to my dismay, something is terribly wrong.

I can't really explain what the problem is, so I attached a screenshot.


It seems as if it doesn't read my tags correctly, but banshee reads them perfectly and I have no problems with it.

---

### Post by njzillest on 2006-08-14
sounds like a program bug. I suggest rythembox as an alternative music player.

---

### Post by Wallakoala on 2006-08-14
> **njzillest said:**
> sounds like a program bug. I suggest rythembox as an alternative music player.

I don't really like rhythmbox. I really want to fix this problem...

It seems as if it is reading the id3 tags incorrectly...maybe there is something wrong with my files?

---

### Post by skymt on 2006-08-14
> **Wallakoala said:**
> I don't really like rhythmbox. I really want to fix this problem...

It seems as if it is reading the id3 tags incorrectly...maybe there is something wrong with my files?

Yes, your files seem to be pretty messed up. What program did you use to rip them?

---

### Post by cptnapalm on 2006-08-15
I've bumped into stuff that displays like that.  Not sure what causes it, but I don't think it is the program itself.

1) Do the files play fine?
2) Were they perchance ripped under Windows?  I ask because of the id3 tag question.

---

### Post by SepheeBear on 2006-08-15
I remember having a similar looking display in apps while Dapper was in its early testing phase. I think it was a fontconfig issue IIRC and was cleaned up after a series of updates. The good thing is its only a cosmetic issue. Try an app like EasyTAG to clean up ID3 tags if you suspect that as the culprit.

---

### Post by hugmenot on 2006-08-17
You could also open a terminal shell and use the command mutagen-inspect on one of the files. It will print the tags so you can perhaps see how they look.

```
mutagen-inspect <path to your mp3>
```

---

### Post by jordilin on 2006-08-20
> **Wallakoala said:**
> I decided to try quodlibet out, and to my dismay, something is terribly wrong.

I can't really explain what the problem is, so I attached a screenshot.


It seems as if it doesn't read my tags correctly, but banshee reads them perfectly and I have no problems with it.

It can be a language charset problem. What language do you use to tag your music?

---

