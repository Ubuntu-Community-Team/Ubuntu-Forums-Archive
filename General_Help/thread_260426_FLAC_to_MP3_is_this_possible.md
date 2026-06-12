---
title: "FLAC to MP3 is this possible?"
date: 2006-09-18
forum: General Help
---

### Post by johnbl on 2006-09-18
Ripped some of my cds using a lossless FLAC format. Would like to convert them to a high bit rate mp3 but for the life of me I can't seemt to find any way.

Any help most appreciated.

John:confused:

---

### Post by bigaltx on 2006-09-18
Do a google search for Audio Convert. If I remember correctly it will flac to mp3, and is available as a deb package

---

### Post by croak77 on 2006-09-18
You can also install soundconverter which is a GNOME program that uses gstreamer as a backend.

---

### Post by skymt on 2006-09-18
Googling something as general as "audio convert" is never a good idea. So, here's the [Freshmeat entry](http://freshmeat.net/projects/audio-convert/), [homepage](https://savannah.nongnu.org/projects/audio-convert), and [direct .deb](http://download.savannah.nongnu.org/releases/audio-convert/audio-convert_0.3.1.1-0ubuntu1_all.deb).

---

### Post by skymt on 2006-09-18
> **croak77 said:**
> You can also install soundconverter which is a GNOME program that uses gstreamer as a backend.

SoundConverter requires GStreamer 0.8. Ubuntu is up to 0.10.
EDIT: The Ubuntu package is out of date. [SoundConverter](http://soundconverter.berlios.de/) has been updated to 0.10, but you have to install it yourself.

---

### Post by croak77 on 2006-09-18
You can have gstreamer 0.8 and 0.10 installed together. Nothing bad will happen. Gnomebaker uses gstreamer 0.8 too. BTW, audio-convert is in the repo's, its called nautilus-script-audio-convert.

---

### Post by INMCM on 2006-09-20
ok, that audio convert is not completly straight forward. Once you install the deb, you still have to run a script to install it.

```
audio-convert-install
```

Also, if you want to do FLAC --> MP3 you need to do 

```
sudo apt-get install flac lame
```


But it works like a charm now!!

---

### Post by johnbl on 2006-09-20
Ah, now I see. Did the install part, and no sign of Audio Converter. 
Will do the flac lame part first chance.

Had tried to use Audacity, interesting result, takes wma files and compresses them to a less than second of play time. Play results in a kind of zeeepp! WIll do the FLAC conversion but not batch system that I can see.

Anyway, clearly more to these file formats than I'm understanding at this point of time.

On the XP machines I use MusicMatch Juke box app [ registered / paid money ] that does a nice job. That which I have tried in Ubuntu appears to only touch mp3 vs MusicMatch that will play most anything.

Tried to use it via wine, but dll problem that have been unable to resolve. Complains about an old version that when updated fails to register...

Still will keep working at it, Ubuntu / linux are simply too good IMOP to give up on.

Thanks for the help
John

---

### Post by jocheem67 on 2006-09-20
Well, in windows there's EAC, Cdex, audiograbber that are completely free of charge and all use the great LAME mp3 encoder. My advice is not paying for encoding software ( movies and music ). There are just too many great app's around...
In linux they are all free, ofcourse......;)

---

### Post by johnbl on 2006-09-21
OK have unpacked the deb
run the install
run the lame command

Works like a treat, thanks again.
John

---

### Post by Zimmer on 2006-10-10
> **johnbl said:**
> Ripped some of my cds using a lossless FLAC format. Would like to convert them to a high bit rate mp3 but for the life of me I can't seemt to find any way.

Any help most appreciated.

John:confused:

I use GRip and use the Lame encoder and it rips straight to mp3  :)

---

### Post by alynx on 2006-11-03
> **skymt said:**
> Googling something as general as "audio convert" is never a good idea. So, here's the [Freshmeat entry](http://freshmeat.net/projects/audio-convert/), [homepage](https://savannah.nongnu.org/projects/audio-convert), and [direct .deb](http://download.savannah.nongnu.org/releases/audio-convert/audio-convert_0.3.1.1-0ubuntu1_all.deb).

Thanks a million , saved my day :) i was gonna go on a trip and wanted to get my flac files into mp3.  /bow

---

### Post by slapys on 2006-11-13
Ubuntu is so amazing.
It truly won't be long before it is "ready for the desktop" (i.e., my mom).

---

### Post by altonbr on 2006-12-02
So wait, how do you get nautilus-script-audio-convert to work? I don't see it in the Nautilus menus or the Applications/Places/System menu. Since it says Nautilus, I'm assuming it's not supposed to run in the terminal.

Grip doesn't allow you to convert a Flac to MP3... only CD to MP3 or CD to Flac

---

### Post by Zimmer on 2006-12-02
> **altonbr said:**
> ...

Grip doesn't allow you to convert a Flac to MP3... only CD to MP3 or CD to Flac

I am sorry if I implied that it did. I was only referencing my preferred method of encoding MP3s via ripping (as johnbl stated he ripped his own CDs I have to assume they are still in his poseession and available ).

I would have thought that encoding FLAC to  MP3 would involve compression and also some loss..  see, for example,
[http://pvanhoof.be/wiki/index.php/Converting_flac_to_mp3](http://pvanhoof.be/wiki/index.php/Converting_flac_to_mp3)
..hence my preference for ripping straight(well, via GRIP and the original wav, of course) to MP3 .

---

### Post by Scraplab on 2006-12-03
The Audio Convert script is already in the repositories as 'nautilus-script-audio-convert'. However, I had to run 'nautilus-script-manager enable ConvertAudioFile' before it would activate.

---

### Post by pasipasi on 2006-12-12
I've experienced with this a lot lately, because most of my music is in flac and my portable player eats mp3s. The fastest and easiest way to convert a flac file to mp3 is to use foobar2000 over wine. I can convert a flac album in about 5mins or less. Those scripts aren't as easy and take 20% more time for some reason (I think the windows lame is more optimized). I wish lame would accept a flac file as input file, like oggenc(2) does, thus making the whole script useless, if you want to spare the tags.

[QUOTE=Zimmer]I would have thought that encoding FLAC to MP3 would involve compression and also some loss.. see, for example,
[http://pvanhoof.be/wiki/index.php/Co...ng_flac_to_mp3](http://pvanhoof.be/wiki/index.php/Co...ng_flac_to_mp3)
..hence my preference for ripping straight(well, via GRIP and the original wav, of course) to MP3 .[/QUOTE]
Now that is not true at all. Flac is a lossless file format, just like a wav file. Converting a flac file to mp3 is just like ripping straight from the cd, except it won't take nearly as long.

Converting an mp3 file to mp3 however would involve some serious loss in the data and is not recommended.

---

### Post by HugoPalma on 2006-12-14
I'm using SoundConverter to encode my flac files to mp3 but i'm getting mp3s with a single channel even though my flac files have two channels.
Is this happening to anyone else ?

---

### Post by HugoPalma on 2006-12-14
> **HugoPalma said:**
> I'm using SoundConverter to encode my flac files to mp3 but i'm getting mp3s with a single channel even though my flac files have two channels.
Is this happening to anyone else ?

Nevermind, the convertion is working great..... sorry :???:

---

### Post by pg99 on 2006-12-14
might not be the first app you think of for this sort of thing, but K3B can convert between many audio formats.  there's some info here for starters
[http://k3b.plainblack.com/support/k3b-0.12-new-features](http://k3b.plainblack.com/support/k3b-0.12-new-features)

---

### Post by glabouni on 2007-02-03
> **Zimmer said:**
> I would have thought that encoding FLAC to  MP3 would involve compression and also some loss..  


you're right, encoding to mp3 involves data loss. that's what mp3 is: a lossy codec (not to mention it's so old it should be considered obsolete and avoided).
but this is no way related to FLAC aka Free Lossless Audio Codec.

> **Zimmer said:**
> ..hence my preference for ripping straight(well, via GRIP and the original wav, of course) to MP3 .

a flac file is like a zipped wav you can listen to without having tu unpack it (as long as your audio player has flac support).

---

### Post by thejart on 2007-02-07
anyone know why this isn't working for me?  

```
flac -d db2004-12-31d1t01.flac | lame -b 224 -h  --noreplaygain db2004-12-31d1t01.wav
```

i get this...Could not find "db2004-12-31d1t01.wav".  and then flac runs and creates the wav file.  how can i get lame to accept the what-i'm-intending-to-be-pipped wav file?

---

### Post by thejart on 2007-02-07
about 2 seconds after i posted i thought, "maybe i'm not being explicit enough."  so i tried this...

```
flac -d -o - db2004-12-31d1t01.flac|lame -b 224 -h  --noreplaygain - db2004-12-31d1t01.mp3
```

and it worked.  but now when i play the file amarok, thinks that this file is 3'20" long, when it's actually 9'05" long.  the weird thing is that the song plays all the way through.  

is this any issue of filesize vs. pipe buffersize?  should i do this another way?  i'm doing it this way b/c i intend to create a script for converting all of my flacs to mp3s so i can finally listen to them on my ipod...too much unlistened-to music, thankyou etree and archive.org.

---

