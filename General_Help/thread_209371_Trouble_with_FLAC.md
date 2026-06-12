---
title: "Trouble with FLAC"
date: 2006-07-05
forum: General Help
---

### Post by grte on 2006-07-05
I've been going through various music players, trying to decide what I like.  I'm currently using Rhythmbox, not because I like it best, but because it's one of two programs that will display id3 tags attached to flac files.

The other player that works is XMMS.  I've tried listen, exaile, muine, amarok, quod libet, and a couple others, and they all refuse to arrange my flac files into my media library according to the tags.

But like I said, both rhythmbox and xmms display them fine.  Does anyone know what may be causing this?

---

### Post by hugmenot on 2006-07-05
Could be that you&#8217;re not confused about having ID3 tags on your FLAC files but really have them, which would be silly because what belongs into FLAC for tagging really are Vorbis tags, not ID3.
Did you use proven software for tagging the flacs?

---

### Post by grte on 2006-07-05
[QUOTE=hugmenot]Could be that you’re not confused about having ID3 tags on your FLAC files but really have them, which would be silly because what belongs into FLAC for tagging really are Vorbis tags, not ID3.
Did you use proven software for tagging the flacs?[/QUOTE]

Is easytag proven?

---

### Post by hugmenot on 2006-07-05
Hm, I don&#8217;t know. What is shown when you look at what mutagen-inspect shows for a .flac file? (use it on the command line.)

---

### Post by grte on 2006-07-05
```
1_Prowler.flac
-- 01_Prowler.flac
- APEv2 tags
No APE tag found
- MP3 tags
MPEG 1 layer 1, 448000 bps, 44100 Hz, 537.08 seconds
TENC=[[Dr. Device]]
TIT2=Prowler
TRCK=01/09
TLEN=236000
TPE1=Iron Maiden
TALB=Iron Maiden
TCON=Metal
- FLAC tags
'01_Prowler.flac' is not a valid FLAC file

```

---

### Post by grte on 2006-07-05
I've got it figured out, now.  It seems easytag had an option enabled that was trying to write id3 tags to flacs instead of flac tags.  I disabled it, resaved all the tags, and it's now being detected in other programs.

Thanks for the help.

---

### Post by hugmenot on 2006-07-05
[QUOTE=grte]I've got it figured out, now.  It seems easytag had an option enabled that was trying to write id3 tags to flacs instead of flac tags. [/QUOTE]

Which gives a compelling resolution to the question, &#8216;Is easytag a proven software&#8217;, doesn&#8217;t it?

I recommend you to take one look at the tagger in Quod Libet.


EDIT: Oh, and it is also telling that Rhythmbox and XMMS support this insanity.

---

### Post by grte on 2006-07-05
[QUOTE=hugmenot]Which gives a compelling resolution to the question, ‘Is easytag a proven software’, doesn’t it?

I recommend you to take one look at the tagger in Quod Libet.


EDIT: Oh, and it is also telling that Rhythmbox and XMMS support this insanity.[/QUOTE]

Well, it *is* an option that can be turned on or off, and when turned off, it seems to work perfectly, so I won't hold it against them too badly.

---

### Post by hugmenot on 2006-07-05
[QUOTE=grte]Well, it *is* an option that can be turned on or off, and when turned off, it seems to work perfectly, so I won't hold it against them too badly.[/QUOTE]

Sure, and tomorrow it writes EXIF tags to MP3 and HTML doctypes to Vorbis files, optional mind you.

---

### Post by jak-_- on 2006-08-29
Sorry for the terrible bump, but I have the same problem... here's a mutegen-inspect output.

```
-- 02 - Starlight.flac
- APEv2 tags
No APE tag found
- MP3 tags
MPEG 2 layer 3, 32000 bps, 22050 Hz, 7353.50 seconds
TDRC=2006
TIT2=Starlight
COMM==eng=Track 2
TENC=Exact Audio Copy   (Secure mode)
TRCK=02
TPE1=Muse
TALB=Black Holes And Revelations
TCON=Alternative
- FLAC tags
'02 - Starlight.flac' is not a valid FLAC file
```

Like this for all... but uhh... is there a quick/easy way to fix this? They are my own rips, but I don't have all the CD's available... and I wanna play my music in Quod Libet (rythmbox sucks) easily :(...

Ideas?

---

### Post by grte on 2006-08-29
> **jak-_- said:**
> Sorry for the terrible bump, but I have the same problem... here's a mutegen-inspect output.

```
-- 02 - Starlight.flac
- APEv2 tags
No APE tag found
- MP3 tags
MPEG 2 layer 3, 32000 bps, 22050 Hz, 7353.50 seconds
TDRC=2006
TIT2=Starlight
COMM==eng=Track 2
TENC=Exact Audio Copy   (Secure mode)
TRCK=02
TPE1=Muse
TALB=Black Holes And Revelations
TCON=Alternative
- FLAC tags
'02 - Starlight.flac' is not a valid FLAC file
```

Like this for all... but uhh... is there a quick/easy way to fix this? They are my own rips, but I don't have all the CD's available... and I wanna play my music in Quod Libet (rythmbox sucks) easily :(...

Ideas?

Well, like I mentioned earlier, easytag was what did this to me.  If it's the same for you, what I did to fix it was to strip the tags, then (in easytag), open Settings > Preferences > ID3 Tag Settings, and make sure 'Write Id3 tags in Flac files with Flac Tags' was unchecked, then retag.

I wouldn't recommend that second bit, anymore, though.  I found another tagging program that I prefer, Audio Tag Tool, which is in the repos.  Just strip, then retag, and everything should work well again.

What might also work is to make sure the Id3 Flac tag option is unchecked, then forcing a resave on all you rfiles.  That might fix things, though I have doubts.

---

### Post by hugmenot on 2006-08-29
Same issue as above, some program of yours wrote MP3 tags into the file.
Deactivate this deviant behaviour and rewrite the tags (ask grte if you need to know how).

---

### Post by hugmenot on 2006-08-29
Oh, there you go ..

---

### Post by grte on 2006-08-29
Creeeepy...

I mean...What're the chances we'd both come back to this thread within a couple minutes of each other?

---

### Post by hugmenot on 2006-08-29
Very low, considering that I&#8217;m in CEST and it&#8217;s 5:49.
I really need to get my circadian rhythm in order until vacation runs out ...

---

### Post by meastp on 2007-09-05
> **grte said:**
> Well, like I mentioned earlier, easytag was what did this to me.  If it's the same for you, what I did to fix it was to strip the tags, then (in easytag), open Settings > Preferences > ID3 Tag Settings, and make sure 'Write Id3 tags in Flac files with Flac Tags' was unchecked, then retag.

I wouldn't recommend that second bit, anymore, though.  **I found another tagging program that I prefer, Audio Tag Tool, which is in the repos**.  Just strip, then retag, and everything should work well again.

What might also work is to make sure the Id3 Flac tag option is unchecked, then forcing a resave on all you rfiles.  That might fix things, though I have doubts.

I can't get Audio Tag Tool to recognise .flac... Is this possible?

---

