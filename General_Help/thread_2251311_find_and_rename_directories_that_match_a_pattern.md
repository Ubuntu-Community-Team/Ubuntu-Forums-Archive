---
title: "find and rename directories that match a pattern"
date: 2014-11-03
forum: General Help
---

### Post by splintr on 2014-11-03
Hi,

i'm having trouble with finding a solution, because its to complex for my mind al that regex stuff. Hope somebody can help me who dreams regexp for fun :)
The Situation:
I have a movies directory "/storage/Moviez" in that directory there are several movies directories (Movie.1.720P , Movie.2.1080P) in those directories there are directories with extras (New.Extras.720, Removes.Scenes.Extras.1080p)

Structure:
/storage/Moviez
```

**Movie.1.720p**
-_Movie.1.Extras.DTS_
--Movie.x.Extras.DTS.mkv
--Movie.y.Extras.DTS.mkv
--Movie.s.Extras.DTS.mkv
--Movie.f.Extras.DTS.mkv
-Movie.1.720p.DTS.MKV
**Movie.New.Scene.1080P**
--_Movie.New.EXTRAS.1080P_
--Movie.New.EXTRAS.1080P.1.mkv
--Movie.New.EXTRAS.1080P.2.mkv
--Movie.New.EXTRAS.1080P.3.mkv
--Movie.New.EXTRAS.1080P.4.mkv
--Movie.New.EXTRAS.1080P.5Subbed.mkv
-Movie.New.Scene.1080P.DTS.MKV
etc...

```
The directories in Bold are the main directories, inside the main directory there is another directory with some text and inside the text the word 'Extras' in it.
I want to rename the the *blabla.Extras.blabla* directories to Extras.

I thought about using find /storage/Moviez -type d -name "*Extras*" > filelist.txt command but i don't know how to go further. Because the Extras inside the extra directory also have the word Extras in it. Next thing i tried was using some regexp stuff, i came to a point where it searched for Extras but i don't know how to rename the directory where the files that are matched are in.

Hope someone can help me.

---

### Post by Vaphell on 2014-11-03
```
while read -rd $'\0' d; do mv "$d" "${d%/*}/Extras"; done < <( find /storage/Moviez -iname "*Extras*" -type d -print0 )
```

---

### Post by splintr on 2014-11-03
> **Vaphell said:**
> ```
while read -rd $'\0' d; do mv "$d" "${d%/*}/Extras"; done < <( find /storage/Moviez -iname "*Extras*" -type d -print0 )
```

ooohh men, you are the best !
Thanks

---

