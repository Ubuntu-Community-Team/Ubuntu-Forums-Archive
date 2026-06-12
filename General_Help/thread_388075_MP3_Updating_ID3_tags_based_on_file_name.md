---
title: "MP3: Updating ID3 tags based on file name"
date: 2007-03-19
forum: General Help
---

### Post by kpkeerthi on 2007-03-19
A few of my mp3 collection is currently organized as below:
```

album-title.mp3

```
Can someone please provide me a script/command that extracts the album name and title name from the mp3 filename?

---

### Post by paper0k on 2007-03-19
Try to use mp3info:
```
sudo apt-get install mp3info
```
and now:
```
mp3info filename.mp3
```
for a complete list of options use:
```
man mp3info
```

---

### Post by paper0k on 2007-03-19
But, if you need extract album and title only by filename, probably you need a script like this:
```
#! /bin/bash

for F in *.mp3
do
   Album=$(echo $F|sed "s/^\([^-]*\)-\([^\.]*\)\..*/\1/g"|tr " " "_"|sed "s/_*$//g")
   Title=$(echo $F|sed "s/^\([^-]*\)-\([^\.]*\)\..*/\2/g"|tr " " "_"|sed "s/^_*//g")
   echo "Album: ${Album}"
   echo "Title: ${Title}"

done

```;)

---

### Post by kpkeerthi on 2007-03-20
Thanks... With a bit of tweaking I was able to update the ID3 tags... I used id3v2 tool though...

---

### Post by dysolve on 2007-11-16
I know this is an old thread but after i moved all my mp3´s from my ntfs drive to my linux drive some how i lost about 3000 id3 tags, Did you update the tags from the filenames? if so could you please show me how you did it. 
thanks
David!

---

### Post by por100pre1 on 2007-11-16
> **dysolve said:**
> I know this is an old thread but after i moved all my mp3´s from my ntfs drive to my linux drive some how i lost about 3000 id3 tags, Did you update the tags from the filenames? if so could you please show me how you did it. 
thanks
David!

I think [Audio Tag Tool]("http://pwp.netcabo.pt/paol/tagtool/") can help you do that easily:

```
sudo aptitude install tagtool
```

---

### Post by dysolve on 2007-11-16
thanks for that... now thats great program... simple idea but AWESOME!

---

### Post by wootah on 2007-12-24
Had a similar issue where I needed to rename based on tag information. GREAT program to do so!

Will also go the other direction and set ID3 based on filename.

---

