---
title: "Generate mkv: add subtitle to mp4"
date: 2019-08-14
forum: General Help
---

### Post by jfca283 on 2019-08-14
Hello,
I need to create a script in order to add subtitles in a mp4 file, with the final intention of getting a mkv file.
I don't want to touch the video nor audio, just incorporate the sort file.
The srt and mp4 files are on the same folder.
Thanks for your time and interest

---

### Post by uRock on 2019-08-14
Not sure if you're willing to use a terminal, but here's a link to what I'd use. [https://trac.ffmpeg.org/wiki/HowToBurnSubtitlesIntoVideo](https://trac.ffmpeg.org/wiki/HowToBurnSubtitlesIntoVideo)

---

### Post by jfca283 on 2019-08-14
> **uRock said:**
> Not sure if you're willing to use a terminal, but here's a link to what I'd use. [https://trac.ffmpeg.org/wiki/HowToBurnSubtitlesIntoVideo](https://trac.ffmpeg.org/wiki/HowToBurnSubtitlesIntoVideo)

Thanks, but that's not what I need. I don't want to burn the subtitles on the picture.

---

### Post by SeijiSensei on 2019-08-14
If you want to merge video, audio, and subtities into a Matroska container, ffmpeg will do that, too.

[https://stackoverflow.com/questions/8672809/use-ffmpeg-to-add-text-subtitles](https://stackoverflow.com/questions/8672809/use-ffmpeg-to-add-text-subtitles)

---

### Post by TheFu on 2019-08-14
Subtitles are different from captions in the SRT or ASS format

```
mkvmerge -o output.mkv  input.mp4 input.srt
```

Additional SRT captions can be appended after the .srt ....   I routinely append .en.srt and .es.srt captions.

That's it.  About as fast as a file copy.  If you want to label the specific language of the subtitle, there are options for that.

---

