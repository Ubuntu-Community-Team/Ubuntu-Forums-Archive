---
title: "Re-Encode Lots of MP3's to Ogg"
date: 2006-11-09
forum: General Help
---

### Post by darrenm on 2006-11-09
I have lots of music files in /home/darrenm/mymusic/{artistname}/{albumname} but they are all different types.

I have old MP3's, started ripping some in lossless Ogg until I saw the space they were using up then started ripping in lossy Ogg.

I now want to re-encode all of them in Ogg lossy but I don't want to spend all night going through all of them one by one.

Before I start building a script to do this for me can anyone suggest a program that will go through my collection and re-encode anything it finds as Ogg?

Ta

---

### Post by CatKiller on 2006-11-09
I think Sound Converter can do that conversion, and you can drag-n-drop a bunch and leave it on while you sleep.

---

### Post by darrenm on 2006-11-10
Thanks.

Borrowed a few lines from someone elses bash script and modified slightly so I do the following in this order:

```
sudo updatedb && locate flac | grep mymusic
cd (one of the dirs listed)
for i in *.flac; do mv "$i" `echo $i | tr ' ' '_'`; done
for file in `ls`; do oggenc "$file" ; done
rm *.flac
```

Suits my purposes nicely.

---

### Post by puppy on 2006-11-10
Check that you're happy with the quality of some sample output files before you go ahead and reencode your entire collection. Moving from one lossy format to another is bound to lower the quality of the files to some extent, and if they weren't encoded at a high bitrate in the first place you might begin to "hear" it...

---

### Post by darrenm on 2006-11-10
Going from FLACs mate (lossless) to ogg level 3 which is supposed to be pretty good. Doing it remotely at the moment but Ill check later thanks.

---

### Post by puppy on 2006-11-10
Oh, I got the idea from your initial post that a lot of your files were to be converted from MP3 - FLAC (as you say) is completely lossless (and thus produces huge file sizes) so enjoy converting the files :mrgreen:  I hope you have a portable music player you can use these .ogg files on :p

---

### Post by darrenm on 2006-11-10
Ah yes sorry. I have some MP3's and FLACs. I decided against converting from MP3 to OGG because of exactly the reason you said. I'll just stick with ogg from now on.

---

