---
title: "Ubuntu and Palm T5, and filenames... and stuff..."
date: 2006-11-20
forum: General Help
---

### Post by Keith_Beef on 2006-11-20
Not sure where to post this, but I hope I'll get some answers.

I recentyl got hold of a Palm Tungsten T5 (see [this thread]("http://ubuntuforums.org/showthread.php?p=1779013")).

I've not yet got synchronisation with Evolution to work, but I have got somewhere. :)

I was looking forward to playing my OGG files on the Palm.

I found a program called Aeroplayer with a free trial download. I found that if I put the Palm into "Drive Mode", I could simply copy the .prc files into the Palm's internal memory (or disc, or whatever it is) and run the player. Yes, it will play OGG files. Great.

But I can't get the extra skins to work.

And I can't get Aeroplayer to show up in the list of applications... I run it by locating the .prc file (in INTERNAL/applications) and executing it.

Any ideas what I should do?

Also, when ripping a CD with Grip, what are the best options to check so that filenames will work without getting annoying messages like "Input is not proper UTF-8, indicate encoding !" in tagtool, and so that I can copy files to the VFAT filesystem used on the SD cards I plug into the Palm?

Oh, and one last question...

Before I ever thought about getting a portable player, I had started ripping my CDs at a nominal 128k bitrate.

To fit more songs on each SD card, I can use sox to downsample. But sox plays havoc with the ID3 tags.

For example, 
```
$ tagtool --dump 01_Sodade.ogg

File type: Ogg Vorbis

Physical stream contains 1 logical stream(s)

---- Logical Stream #1 ----

Serial number   : 0x36EF9CE3
Encoder version : 0
Encoder vendor  : Xiph.Org libVorbis I 20030909
Channels        : 2
Sample rate     : 44100 Hz
Nominal bit rate: 128000 bps
Average bit rate: 128365 bps
Playing time    : 293.307 s

User comments (raw):
title=Sodade
artist=Cesaria Evora
genre=Folklore
date=1992
album=Miss Perfumado
tracknumber=01

---- Processed Comments ----

title        "Sodade"
artist       "Cesaria Evora"
date         "1992"
genre        "Folklore"
album        "Miss Perfumado"
tracknumber  "01"

```

becomes
```
$ tagtool --dump 01_Sodade_8k.ogg

File type: Ogg Vorbis

Physical stream contains 1 logical stream(s)

---- Logical Stream #1 ----

Serial number   : 0x687FB6B2
Encoder version : 0
Encoder vendor  : Xiph.Org libVorbis I 20050304
Channels        : 2
Sample rate     : 8000 Hz
Nominal bit rate: 31800 bps
Average bit rate: 30159 bps
Playing time    : 293.307 s

User comments (raw):
title=Sodade
artist=Cesaria Evora
genre=Folklore
date=1992
album=Miss Perfumado
tracknumber=01

---- Processed Comments ----

title        "Sodade
artist=Cesaria Evora
genre=Folklore
date=1992
album=Miss Perfumado
tracknumber=01"

```
after sox has finished work.

This really messes up the display in Beep's playlist, and probably would do the same in Aeroplay.

Is there a way, from the command line, to re-write the tags in the sox-generated file using the correct data read from the first OGG file?

Beef.

---

### Post by mssever on 2006-11-20
> **Keith_Beef said:**
> Also, when ripping a CD with Grip, what are the best options to check so that filenames will work without getting annoying messages like "Input is not proper UTF-8, indicate encoding !" in tagtool, and so that I can copy files to the VFAT filesystem used on the SD cards I plug into the Palm?

Don't know about your other question, but I believe that Grip is a little out of date nowadays. I've used Sound Juicer successfully.

---

