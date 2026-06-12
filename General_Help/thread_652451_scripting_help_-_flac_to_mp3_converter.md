---
title: "scripting help - flac to mp3 converter"
date: 2007-12-28
forum: General Help
---

### Post by bionnaki on 2007-12-28
so, I have this script that will convert .flac to .mp3 V0 --vbr-new and transfer the id3 tags to the output .mp3 files:

> 
for a in *

do
OUTF=`echo "$a" | sed s/\.flac/.mp3/g`

ARTIST=`metaflac "$a" --show-tag=ARTIST | sed s/.*=//g`
TITLE=`metaflac "$a" --show-tag=TITLE | sed s/.*=//g`
ALBUM=`metaflac "$a" --show-tag=ALBUM | sed s/.*=//g`
GENRE=`metaflac "$a" --show-tag=GENRE | sed s/.*=//g`
TRACKNUMBER=`metaflac "$a" --show-tag=TRACKNUMBER | sed s/.*=//g`
DATE=`metaflac "$a" --show-tag=DATE | sed s/.*=//g`

flac -c -d "$a" | lame -m j -q 0 --vbr-new -V 0 -s 44.1 - "$OUTF"
id3 -t "$TITLE" -T "${TRACKNUMBER:-0}" -a "$ARTIST" -A "$ALBUM" -y "$DATE" -g "${GENRE:-12}" "$OUTF"

done


the script works great except for one problem. if there any other files in the directory besides .flac, they will be overwritten. can anyone who knows how to script better than I do show me how to ignore all files that are not *.flac?

I appreciate your help.

---

### Post by Andrew Golightly on 2007-12-28
hey there. I'm pretty much a newbie with scripting too..

although from what I hear.. you just want to process *.flac files right?

It seems to me you just need to request that in your for loop...

so..

```
for a in *
```

becomes

```
for a in *.flac
```

---

### Post by Lostincyberspace on 2007-12-28
You could always just use soundconverter to convert multiple folders at once in gui. 
Soundconverter is in the repository so it should be a simple intsall.

---

### Post by bionnaki on 2007-12-29
I dont like soundkonverter/soundconverter - they are quite limited and cannot do a proper V0/V2 encode. I'd rather use the commandline - much easier in the terminal.

thanks andrew - that works great.

---

