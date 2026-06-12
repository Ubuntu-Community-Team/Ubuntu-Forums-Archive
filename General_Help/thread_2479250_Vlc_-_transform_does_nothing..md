---
title: "Vlc - transform does nothing."
date: 2022-09-19
forum: General Help
---

### Post by raleigh3 on 2022-09-19
VLC transform does nothing.

No matter what transform setting I pick, nothing happens.

---

### Post by #&amp;thj^% on 2022-09-19
Stab in the dark here: VLC -> Tools -> Preferences -> Input/Codecs -> Codecs.Hardware-accelerated decoding=Disable

---

### Post by raleigh3 on 2022-09-19
It did not help. Working at it from another angle.

I used

ffmpeg -i movie.mp4 -vf "transpose=1"  output-video.mp4

[https://ubuntuhandbook.org/index.php/2021/03/single-command-rotate-video-ubuntu-linux/?unapproved=3736511&moderation-hash=ed4fe896ade4e7cd8c5ecd72ff2acd7a#comment-3736511](https://ubuntuhandbook.org/index.php/2021/03/single-command-rotate-video-ubuntu-linux/?unapproved=3736511&moderation-hash=ed4fe896ade4e7cd8c5ecd72ff2acd7a#comment-3736511)

This works but loses a lot of resolution in the process.

Is there a way to keep the original resolution?

---

### Post by #&amp;thj^% on 2022-09-19
Good thinking, Aspect ratio is added to encoding options automatically if none is specified.
So example:
```

options = {:resolution => 320x180} # Will add -aspect 1.77777777777778 to ffmpeg
```

Preserve aspect ratio on width or height by using the **preserve_aspect_ratio transcoder option**.
More Here: [https://www.rubydoc.info/gems/streamio-ffmpeg/0.8.0](https://www.rubydoc.info/gems/streamio-ffmpeg/0.8.0)
To help maybe, I'll use this for most of my ffmpeg
```

ffmpeg -i "file".mp4 -vcodec mpeg2video -s 1920x1080 -q:v 1 -acodec copy -f mpegts "file".ts
```

---

### Post by raleigh3 on 2022-09-19
I tried it. Went from 85 mb to 210 mb. :-)

And it did not rotate the image as well. (That is what transpose does.)

---

### Post by #&amp;thj^% on 2022-09-19
> **raleigh3 said:**
> I tried it. Went from 85 mb to 210 mb. :-)

[s]Please explain??[/s] I see you edited your post.
should be in the same directory the terminal was located, /home/username

---

### Post by raleigh3 on 2022-09-19
```
should be in the same directory the terminal was located, /home/username
```

I do not understand this.

I ran it in the directory that contained the mp4.

I used 

```
ffmpeg -i /home/andy/Downloads/small.mp4 -vcodec mpeg2video -s 1024x640 -q:v 1 -acodec copy -f mpegts movie.ts
```

It works fine, but did not rotate it.

---

