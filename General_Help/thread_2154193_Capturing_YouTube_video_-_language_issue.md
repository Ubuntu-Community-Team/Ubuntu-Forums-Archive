---
title: "Capturing YouTube video - language issue"
date: 2013-06-13
forum: General Help
---

### Post by pwabrahams on 2013-06-13
I'm using the program youtube-dl to capture a YouTube video.  The video is in Hungarian.  When I display it in a browser (either reconq or Firefox), it has English subtitles.  The captured version doesn't have the subtitles but seems to be otherwise correct. The command-line dialog looks like this:

```
pwa@Morchella:~/.macromedia$ youtube-dl http://www.youtube.com/watch?v=h4QcVdtbK_w
[youtube] Setting language
[youtube] h4QcVdtbK_w: Downloading video webpage
[youtube] h4QcVdtbK_w: Downloading video info webpage
[youtube] h4QcVdtbK_w: Extracting video information
[download] Destination: h4QcVdtbK_w.flv
[download] 100.0% of 8.71M at   34.42k/s ETA 00:00

```
I imagine the "Setting language" line has something to do with the problem, but I can't find any options for youtube-dl that seem relevant.

---

### Post by carboi82 on 2013-06-13
Unless Im mistaken, youtubes subtitles are layered over the video, not integral to it in any way.
You may find these helpful...

--write-sub                                  write subtitle file (currently youtube only)
--only-sub                                   [deprecated] alias of --skip-download
--all-subs                                    downloads all the available subtitles of the                           video (currently youtube only)
--list-subs                                   lists all available subtitles for the video                           (currently youtube only)
--sub-format LANG                      subtitle format [srt/sbv] (default=srt)                           (currently youtube only)
--sub-lang LANG                          language of the subtitles to download (optional)                           use IETF language tags like 'en'

Taken from:  [https://github.com/rg3/youtube-dl/](https://github.com/rg3/youtube-dl/)

---

### Post by pwabrahams on 2013-06-13
I tried what you suggested and got a message to the effect that the video has no subtitles.  So it does seem that the language setting is the key.

---

