---
title: "Trying to rip from CD to MONO mp3 in SoundKonverter"
date: 2007-05-04
forum: General Help
---

### Post by mjpatey on 2007-05-04
Hi, folks-

I'm using SoundKonverter in Feisty to rip my pastor's sermons from CD to mp3 format to post on our church's Web site. In the past (before I switched to Ubuntu), the software I used gave me a lot of easily-accessible control over the exact parameters of the conversion.

Right now, in SoundKonverter, I've hit a little speed bump. I'm trying to rip audio from the CD (recorded in mono, but of course, ripping from CD results in a stereo file regardless), and go directly to a 64Kbps mono mp3 file. I'm able to set it to 64Kbps, but the program assumes stereo, since that's what it sees is coming in. There appears to be an option to set it to mono in SoundKonverter, but that is grayed out (though strangely enough, it says mono in its grayed-out state).

When I run the conversion, the resulting stereo mp3, of course, is at half the sound quality because at 64 Kbps, it uses 32 Kbps for each channel, rather than the whole 64Kbps for a single channel.

The only clue I have is under "Advanced Options", it has a field for "Command", which currently displays:

> /usr/bin/ffmpeg %p -i %i %o

It gives me the option to type into this field; is there some magic command I can insert into that text that would specify a mono mp3?

Sorry if my post is confusing, and thanks for any help you may be able to provide!

-Mark

---

### Post by FluffyElmo on 2007-05-04
I don't use that program myself but the command line switch to output mono via ffmpeg is *-ac 1* which is short for one audio channel. So my best guess at a command string would be:
```
/usr/bin/ffmpeg %p -i %i -ac 1 %o
```

If that doesn't work, this page has more detail on ffmpeg options...
[http://howto-pages.org/ffmpeg/]("http://howto-pages.org/ffmpeg/")

Good Luck, and let us know if you're successful...

---

### Post by mjpatey on 2007-05-04
Elmo,

Thank you!  That was perfect!  I spent some time scrolling through the ffmpeg man pages, and under "Audio Options" somehow didn't find the -ac switch until after you mentioned it.  That was the missing link.  My audio has gone from CD-R to 64 kbps mono mp3 in one step.  :-)

Thanks again!

-Mark

---

### Post by mjpatey on 2007-05-04
Elmo,

By the way, is there another program you'd recommend?  I'm working with SoundKonverter because it lets me specify the exact bitrate rather than just "very high, high, low, very low," etc.  But I'd be open to anything else if it does the job better or more simply.

Thanks!

---

