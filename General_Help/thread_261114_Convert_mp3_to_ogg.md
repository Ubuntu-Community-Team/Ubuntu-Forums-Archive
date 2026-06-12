---
title: "Convert mp3 to ogg"
date: 2006-09-19
forum: General Help
---

### Post by rekahsoft on 2006-09-19
How do i convert .mp3 files to .ogg? Is there an app to do it? Thanks

---

### Post by MetalMusicAddict on 2006-09-19
Yes there are but I cant remember them. I just wanted to chime in and say if you value sound quality please dont go from one lossy format to another. Do you have a reason?

---

### Post by rekahsoft on 2006-09-19
what? what is wrong with ogg? or mp3? What format do u recomend? I was going to switch formats because i want to use open source as much as possable because i HATE propriatary.

---

### Post by MetalMusicAddict on 2006-09-19
No. Nothings wrong with ogg. :) You can start to introduce things going from one lossy format to another. Its better to re-rip you CDs strait to ogg. Some portable players batteries dont like ogg though.

---

### Post by SoloSalsa on 2006-09-19
So use FLAC in an OGG!
I converted al my music in Windows to FLAC or Vorbis using DbPowerAmp music converter.

---

### Post by MetalMusicAddict on 2006-09-19
> **SoloSalsa said:**
> So use FLAC in an OGG!
I converted al my music in Windows to FLAC or Vorbis using DbPowerAmp music converter.

What format was it before it went to FLAC?

---

### Post by BoHu on 2006-09-19
> sudo apt-get install mp32ogg

once the program is installed move to your music directory. Mine is /home/bohu/music

> cd /home/bohu/music

Then run the program. If you want it to convert to ogg and then delete the old mp3...

> mp32ogg --delete *.mp3

If you want to convert to ogg and KEEP your mp3 files too, do this...

> mp32ogg *.mp3

Then go to work or to sleep or whatever cuz this takes a long time on big collections. The program works recursively so it will get all the subfolders, too.

---

### Post by rekahsoft on 2006-09-19
will i loose audio quality?

---

### Post by SoloSalsa on 2006-09-20
They were MP3's, 128k, say?  I changed them to FLAC on the highest compression, only about twice the size (As opposed to like fifty times, according to uncompressed approximate).  And my old laptop (500mhz) barely reaches 8% cpu to play them.

---

### Post by jocheem67 on 2006-09-20
I would like to use ogg more and more, but it's just not exportable to many players ( my car audio-system:(  ).

Again, it's already said, you will hear the decay in sound quality if you do a transcode ( from lossy to again lossy ).

Can't you just make your new files .ogg??

---

### Post by user1397 on 2006-09-20
there's also the program **soundconverter**

look for it in synaptic (system > administration > synaptic package manager)

it has a gui for simplicity

---

### Post by rekahsoft on 2006-09-20
When i convert the mp3's to ogg on the very high quiality setting it sounds just as good or even better...do i loose any sound quiality when i convert?

---

### Post by RAOF on 2006-09-21
> **rekahsoft said:**
> When i convert the mp3's to ogg on the very high quiality setting it sounds just as good or even better...do i loose any sound quiality when i convert?

Yes.  They're both lossy formats (they throw away information that they think you won't hear), so encoding to ogg will discard some information.

---

### Post by rekahsoft on 2006-09-21
so if i have mp3's that have a bitrate of 128kbs and i convert them to 256kps ogg files what do i loose? I did not hear any sound decrease when i tried.

---

### Post by rekahsoft on 2006-09-21
Also if i first convert the mp3 to a lossless codec (like FLAC) and then encode it to ogg/vorbis would that be better?

---

### Post by cronholio on 2006-09-21
It is all about loss of information. If you take audio, say, from a CD and convert it to FLAC, the information in the FLAC file will be exactly the same as on the CD, only compressed. Now if instead you convert it to OGG or MP3, the encoder decides which information you won't hear anway and leaves that out. The rules for deciding which information that is differ between the MP3 and OGG algorithms. That's why encoding in one lossy format first and into a second lossy format after will strip some information from the data twice, resulting in a higher loss of quality.

> Also if i first convert the mp3 to a lossless codec (like FLAC) and then encode it to ogg/vorbis would that be better?

And you can convert back to a lossless format like FLAC or WAV all you want, you will not be able to get back the discarded information. You will only increase the file size.

---

### Post by slimdog360 on 2006-09-21
> **rekahsoft said:**
> so if i have mp3's that have a bitrate of 128kbs and i convert them to 256kps ogg files what do i loose? I did not hear any sound decrease when i tried.

IMO you have to have a sensitive ear to notice the differences that everyone talks about but it is there. I notice it in some songs every now and again. 
Encoding from a lower bitrate to a higher wont do anything except for degrade it more (but not my much).
Id say if you already have a heap of music in mp3 keep it that way but you can convert new music from cd's into ogg.

---

### Post by rekahsoft on 2006-09-21
ok...i will keep my music in mp3 but from now on i use ogg.

---

### Post by TheRingmaster on 2006-12-20
why can't you just burn all of your music to a cd and then ripped those cds to flac and then to ogg vorbis?

---

### Post by rekahsoft on 2006-12-21
> **TheRingmaster said:**
> why can't you just burn all of your music to a cd and then ripped those cds to flac and then to ogg vorbis?

This will do nothing. Read higher up on this thread.

---

### Post by OttifantSir on 2006-12-31
The poster who alerted me to mp32ogg said/claimed it worked recursively/searched and converted all music in subfolders too. I have now spent near two days converting my music collection from mp3 to ogg (I know, don't, right? Well, I am not audiophile enough to hear the difference). But it did not convert the files in subfolders. This might have something to do with the fact that all my music is on a USB-connected (1.1 USB) Western Digital "My Book" external Harddrive, but I can't see why this should have anything to do with it. When I tried a smaller collection and deleted the mp3s, it worked, but not when I wished to keep the mp3s.

Also, is there any possibility to tell the program to convert the music and store the finished result in a different folder than the original? It would be easier to have the program moved to the folder I wish it to be in after it's done, than looking up all the files later and move them.

---

### Post by bmhm on 2007-01-02
[FONT="Verdana"]I think sth like this will work:

```
mp32ogg --q=4.5 -v ./ ./* *
```

dunno if you need to append sth like ./*/* and /*/*/* and so on to go deeper than one folder... really! don't ask me :)[/FONT]

---

