---
title: "CD ripping &amp; music collection"
date: 2005-08-19
forum: General Help
---

### Post by mariuss on 2005-08-19
Hi all,

I am thinking to rip all my CDs and eventually move them to a MythTV like system. I am fairly new to ripping and Linux in general. I will use the ogg format.

What ripper should I use so files are properly tagged? Sound Juicer adds a limitted number of tags (no year for example).

Is there a standard way to associate images with albums (album covers)?

Any other advice?

Thanks,
Marius

---

### Post by buldir on 2005-08-19
I use grip to rip CDs to mp3s.  Here's the code for the rip to mp3 setting in grip:

```
/usr/bin/lame
-q 2 -b 128 --cbr --nohist --tt %n --ta %A --tl %d --ty %y --tn %t --tg %G %w %m
```
I'm not sure about the album cover thing.

---

### Post by kamiccolo on 2005-08-21
I also wanted to use grip to rip all my CDs. It works good with lame as the encoder, but ripping itself is so slow (only 1,2x). As I used Fedora, ripping was at least 7x or faster. What can I do to accelerate it?

---

### Post by RicgorE on 2005-08-21
you may need to enable dma for your cdrom drives , look here [http://ubuntuguide.org/#speedupcddvdrom ](http://ubuntuguide.org/#speedupcddvdrom ) 

If dma is enabled than maybe cdparanoia is having difficulty with the source disk. Try reducing cdparanoia's settings from within grip. under the config/ rip/ ripper tab. I loosened up the settings here and I now rip cd's at amazing speeds.

---

### Post by kamiccolo on 2005-08-21
This speeds up ripping to only 4x whils others rip at about 30x.
Could it be that's the wrong ripper?
Btw: DMA is enabled for all drives.

---

### Post by skoal on 2005-08-21
Whoa! Talk about your timely chances to post a reply.  Why I'm currently ripping a collection of Czech Polka CD(s), even as I type...

What am I using? KAudioCreator
What format? Ogg, of course...
Alternatives? Sure. But you want something fast and sleek, right?  Why push a Lexus when you can drive a vette?  You feelin' me?

Checkity check 'dis out...

1. Install KAudioCreator (if you don't have KDE) and libvorbis-tools
2. Under settings > configure KAudioCreator > Encoder, select oggEnc > Configure...
3. configure 'oggenc' to use the various quality settings with the -q CLI switch.  I use 6 instead of the default 3 (~128kbps).  My command line is pretty much the same as default:

oggenc -q 6 -o %o --artist %{artist} [...]

* check man pages for more 411...

4. and start ripping those CD(s) another ogg donut hole...

\\//_

---

### Post by kamiccolo on 2005-08-22
Grip is good an I also wanted to use it in the future. With ripper I meant the module thats listed in the configuration. It's split up there in "rip" and "encode". Encoding is very fast, but ripping is very slow with max. 4x on a 50x-drive.
In the tab "rip" in the configurations menu you can choose cdparanoia (default) and cdda2wav. In former times with Fedora cdparanoia worked very fast, so I think it must be a problem with the settings.

---

### Post by Jenda on 2005-08-23
Hmmm. I think I'll give KAudio **K**rrrrrrrrrreator a try.

Enjoy the Czech Polka, mon. I myself am not a big fan of Czech Music. I did, though, just buy a very Czech tenor saxophone (Amati, Kraslice) - although to play american music, Jazz.

-Jenda, Prague, Czech Republic

---

