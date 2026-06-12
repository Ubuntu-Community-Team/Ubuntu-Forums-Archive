---
title: "rename command"
date: 2012-12-19
forum: General Help
---

### Post by amir705 on 2012-12-19
I am not sure if I am in the right section.

I have a hard time renaming my music files.

> BreakOut -pWzx4kjQnow.aac
Ever Blazin' -kPsBxf0TWTw.aac
Eye Deh a Mi Knee -7s5Upro5cNM.aac
Fire Links (Intro) -3w1cTe7kgTo.aac
Give It Up to Me -7lwr-pKRyKY.aac
Got 2 Luv U Ft. Alexis Jordan.mp3
Head in the Zone -vdejLiMFkB0.aac
Head to Toe -JQ_NdiIPdug.aac
I'll Take You There -LI-FKVp8yPU.aac
Looga Man. Kid Kurup & jigzagula - Change The Game -t9iPpf1C_d4.aac
Never Gonna Be the Same -88XdrSasrO8.aac
Nina Sky - Connection -yLhZZW6NXpI.aac
Send It On -snmvVWRGrA0.aac
Straight Up -I2l9W4hGfnQ.aac
Tami Chynn - All on Me -1fEvNDmbfhc.aac
Temperature -l2Gf3ZbuKjs.aac
The Trinity -rRfnPaIyrco.aac
Wayne Marshall - Yardie Bone -mQ9geNBO9o0.aac
We Be Burnin' -6Exq3AbaYTY.aac
weiop@weiop:~/Music/sean_paul$ 


How can I rename them to the songs name only?
I gave up trying with the rename command

Thanks ahead :)

---

### Post by hwttdz on 2012-12-19
Take a look at easytag and picard.  Both are programs designed to help in tagging/organizing/naming music files.  Not sure if they play well with aac files.

---

### Post by cwsnyder on 2012-12-19
On looking at your song list, I can see why you are having troubles.  There _is_ no regular expression which can describe the difference between the names of the songs and the additions after the name.  I think you may have to bite the bullet and manually rename each song.

---

### Post by 1clue on 2012-12-19
Sure there is.  Zap everything between the - and the .

Frankly though there are music apps out there (banshee I think, comes to mind) that can rename your files based on anything you want, and put them into folders based on band or whatever too.

---

### Post by sisco311 on 2012-12-19
Thread moved to **General Help**.

---

### Post by sisco311 on 2012-12-19
Try:
```
rename **-n** 's/(.*) -.*\.(\.*)/$1.$2/' ./*
```

Used with the **-n** option, (p)rename will only print the name of each file that would be renamed. If everything looks good, run the command without the **-n** option.

If you are looking for a GUI application, then check out:
[list]
[*]**gprename** 
[*]thunar (file manager)
[*]gnome-commander (file manager)
[*]purrr 
[*]pyrenamer 
[*]gwenrename 
[*]**krename** (KDE) 
[/list]

---

### Post by cwsnyder on 2012-12-19
Hey guys who answered after me. Did you actually look at his names?  Some of them have 2 or 3 dashes in the names.  Your solutions will zap half of the name on those file names.

---

### Post by sisco311 on 2012-12-19
> **cwsnyder said:**
> Hey guys who answered after me. Did you actually look at his names?  Some of them have 2 or 3 dashes in the names.  Your solutions will zap half of the name on those file names.

I tested the command on the file names posted by the OP and as far as I can tell it works.

(Most/All ???) [Regular expressions]("http://mywiki.wooledge.org/RegularExpression") are by default greedy. ;)

[http://en.wikipedia.org/wiki/Regular_expression#Lazy_quantification](http://en.wikipedia.org/wiki/Regular_expression#Lazy_quantification)

---

### Post by 1clue on 2012-12-19
But if you match only on the last - then it works.

```

rename -n 's/(.*) -[^-]*\.(\.*)/$1.$2/' ./*

```

Didn't test that, but basically modified the regex supplied by sisco311.  Looks like it should work.

---

