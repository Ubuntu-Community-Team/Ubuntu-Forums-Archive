---
title: "Sound Juicer clipping waveform of songs"
date: 2008-04-21
forum: General Help
---

### Post by ricardisimo on 2008-04-21
I'm trying to rip one of my CDs that used to play just fine, but now the audio is so blown out it's pretty much worthless [see attached waveform]. Is there any way for me to adjust the size of the waveform with which Sound Juicer works so as to allow me to start with an unclipped track, even if it is over-the-top-loud? Loud I can adjust; clipped is lost forever. Thanks in advance.

P.S. - There's probably something wrong with the disc - it's not scratched, but most of the tracks won't play in the car any longer. Any ideas what might cause this?

---

### Post by TeoBigusGeekus on 2008-04-21
I have no idea of what you are talking about, but if there is something that Sound Juicer can't do, I'm pretty sure Cinelerra can.
[http://cinelerra.org/getting_cinelerra.php]("http://cinelerra.org/getting_cinelerra.php")
It's a professional package for editting video and audio, the equivalent of Adobe Premiere.
I've always been to the opinion that if you're gonna use a piece of software, use the best...

---

### Post by ricardisimo on 2008-04-21
Cinelerra appears to be an ex post facto editor, and I'm sure it's very good. But unless it can replace missing information from an audio track, I don't see it being the right tool here. I need to change the way a given CD ripper grabs tracks from my CD, so that then I can edit the resulting file... with Cinelerra, for example. Anyhow, Audacity is also wonderful.

---

### Post by vanadium on 2008-04-21
When ripping, the digital audio data are read as recorded on CD, unless you use some kind of a "normalize" option. However, a normalize option at most adjusts the audio to make the peak amplitude 0 dB, and thus should not introduce clipping. I am not sure how and if you could use normalize with Sound juicer, so I am pretty convinced that the wav you have is the audo as it exists on the CD. Many modern pop CDs are badly mastered to sound as loud as possible. Perhaps the clipping you hear is just because your volume settings oversaturate the sound card.

To tell wether a wav form is really clipped, you must zoom in and examine individual peaks. If the peaks are "shaved off", this is where there has been clipping. Again, many modern recordings actually have some clipping on the original CD.

---

### Post by FluffyElmo on 2008-04-21
Just a quick thought but what format are you ripping to? If you are ripping to a lossy format like MP3 then some clipping is pretty much inevitable. Check *Edit->Preferences* to see what format is set as the default. There are ways to add more options to the Format using GStreamer but I don't know how offhand. Search for something like "ripping MP3 with sound juicer" to turn up some how-tos.

Also note that "Voice, Lossless" probably applies a filter to enhance spoken word. Try Lossless FLAC instead to see what you get.

---

### Post by ricardisimo on 2008-04-21
I tried ogg first, then flac, with identical results both times. The cause of the problem is physical, not programming. I was hoping that there would be a programming fix for this, however, or perhaps a home remedy (I don't know... spreading peanut butter on the back of the disc or some such thing). The disc played perfectly not much more than a year ago. It's a world music album, not metal or punk or the like, so the clipping is not by design.

The only other observation I can make is that to my (very) untrained eye, the disc itself looks slightly more transparent than normal, when I hold it up to the monitor or another light source. Anything to this? Thanks.

---

### Post by FluffyElmo on 2008-04-21
Maybe try another CD to confirm that the problem is physical. If it is the CD I'd suggest investigating other CD ripping libraries like cdparanoia ([http://www.xiph.org/paranoia/]("http://www.xiph.org/paranoia/"), apt-get install cdparanoia) which have error correction and let you change more options from the command line than Sound Juicer allows from the gui.

A few thoughts from the past when I've had problems with scratched CDs...
1. Try ripping at lower speeds like 1x or 2x instead of full speed.
2. In some cases you can increase the number of tries that the error correction makes, you can set it to read the disk multiple times and average the results.
3. If other hardware is available I recall getting much better results ripping with a CD-RW drive vs a DVD-ROM/RW, the firmware is probably more optimized?

Other than that, a friend who used to work at a used CD store recommended toothpaste to try and repair scratches on disks. You may also want to check your local video stores as some have a machine that will repair the surface of CDs. They usually charge for it but if it's a rare CD it could be worth it to you.

Good Luck!

---

### Post by stchman on 2008-04-21
> **ricardisimo said:**
> I'm trying to rip one of my CDs that used to play just fine, but now the audio is so blown out it's pretty much worthless [see attached waveform]. Is there any way for me to adjust the size of the waveform with which Sound Juicer works so as to allow me to start with an unclipped track, even if it is over-the-top-loud? Loud I can adjust; clipped is lost forever. Thanks in advance.

P.S. - There's probably something wrong with the disc - it's not scratched, but most of the tracks won't play in the car any longer. Any ideas what might cause this?

What CODEC are you using for ripping MP3, OGG, FLAC?  If MP3 I have a tutorial to rip CDs to MP3s easilt and they sound great.

[http://www.stchman.com/cd_rip.html](http://www.stchman.com/cd_rip.html)

Hope this helps.

---

