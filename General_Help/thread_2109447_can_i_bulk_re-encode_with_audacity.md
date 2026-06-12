---
title: "can i bulk re-encode with audacity"
date: 2013-01-27
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2013-01-27
I want to re-encode all my music (mp3 format) using audacity, i am tring to get the file sizes down so everything will fit on my 1gb ipod shuffle
i know there are several 4.5-7MB files that could have a MB or more shaved off the file size, going though 220 files one by one is a PITA

i have tried using sound converter, but i have had it make file larger than audacity and loose some sound data on some high frequencies sections of songs

if this is just a settings difference i would like to know how to set the sound converter to write mp3s the same as audacity exports them

---

### Post by tgalati4 on 2013-01-27
I would use sox for such a batch conversion.  Sound converter will work, but it requires you defining the exact mp3 settings as a profile, otherwise you will get default settings--which may result in larger files.

The other way to do it is some music player applications have a mode to transcribe on-the-fly for designated mp3, hardware devices.  This requires some setup, but since it works on the fly, you don't have to reencode your entire collection.

---

### Post by HiImTye on 2013-01-27
you could probably do it with ffmpeg/avconv, but you'd need to write a quick script to catch all your files (likely with find) and then pipe them to ffmpeg. something like:
```

cd /path/to/music/folder/
while read -r f; do
  F=${f##*/}
  P=$(echo $f | sed 's|.*/||')
  ffmpeg -i $f <ffmpeg options> $P/.$F
  mv $P/.$F $f
done < <(find . -iname *.mp3)

```

---

