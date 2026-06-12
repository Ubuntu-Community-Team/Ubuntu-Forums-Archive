---
title: "Terminal tool to change audio codec within video files"
date: 2015-03-16
forum: General Help
---

### Post by CaptainMark on 2015-03-16
I don't have much experience with multimedia management so I need some help with something. I'm just starting to rip my DVD collection to my computer. I'm about 20 discs in when I find out that Google Chromecast doesn't support AC3 audio codecs which whilst not a dealbreaker, would be nice to use occasionally. Is there a command line tool to take these video files .mkv and convert the audio codec currently AC3 and change it Vorbis, all whilst doing nothing to the video quality, it's very important that I don't lose video quality because I've ripped them in quite good quality and and don't want to lose that. 

If this can't be done easily, I may just leave them for now, and re-rip them as and when I find one that doesn't play, it's only 20 or so DVD's so it's not the end of the world but it would be nice to be able to play them anywhere.

Thanks for any help
Regards
Mark

EDIT: I'm assuming avconv looks like the tool I want but the man page just blew my mind, I couldn't get my head around it at all, help would be appreciated.

---

### Post by TheFu on 2015-03-16
Yes, avconv is one of the choices or ffmpeg or mencoder or handbrake.

Or you could just setup a media server that dynamically transcodes the audio based on the client requesting it - plex media server does that.

A sample command:```
ffmpeg -y -i input-file.mkv -vcodec copy -strict experimental  -c:a aac output-file.mkv
```

I suppose you could use vorbis for the audio, but AAC is really the standard for web-based video files and supported by chromecast.

Whenever I create media files now, I'll put as many audio tracks as possible into the output file - english 5.1 AC3, english 6-ch AAC, plus all the other languages that might be included.  The same applies for subtitles and captions - the mkv container can hold pretty much anything, so why not?  Of course, you need to select mkv as the output container. The input file type doesn't matter really ...

---

### Post by SeijiSensei on 2015-03-16
Transcoding is one of those things where a GUI can sometimes help manage the myriad of options available at the command line for programs like ffmpeg. Add [John Stebbins's PPA]("https://launchpad.net/~stebbins/+archive/ubuntu/handbrake-snapshots"), then install **handbrake-gtk**.  You'll see vorbis as an audio option, along with many, many others. You can use it to convert the audio stream in an existing file and rip DVDs into the format(s) of your choice.

---

