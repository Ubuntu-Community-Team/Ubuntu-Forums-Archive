---
title: "Batch convertion of videos from camera"
date: 2016-05-30
forum: General Help
---

### Post by alain.roger on 2016-05-30
Hi,

i have several MTS files from my camera and i would like to convert them to mkv files. I know how to do it using ffmpeg and in command line. My question is how to do a batch inline to be sure each MTS will be converted to mkv.

i tried:
for i in ls *.MTS; do ffmpeg -i ${i} -vcodec libx264 -preset medium -crf 18 -vf scale=1280:720 -threads 0 -acodec copy ${i%%.*}-1.mkv; done

it seems the first file it tries to convert is "ls" :(
why?

thx

---

### Post by mc4man on 2016-05-30
cd to folder holding. then - 
```
for f in *.MTS; do ffmpeg -i "$f" -vcodec libx264 -preset medium -crf 18 -vf scale=1280:720 -threads 0 -acodec copy "${f%.MTS}.mkv"; done
```
or a bit shorter plus I believe you can lose the -threads 0
```
for f in *.MTS; do ffmpeg -i "$f" -c:v libx264 -preset medium -crf 18 -vf scale=1280:720  -c:a copy "${f%.MTS}.mkv"; done
```

(- assumes files end with .MTS vs. .mts

---

### Post by alain.roger on 2016-05-30
thx for info.

files are really MTS and not mts :( thx panasonic camera :D

---

