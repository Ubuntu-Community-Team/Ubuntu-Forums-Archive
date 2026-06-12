---
title: "Can't make dvd iso"
date: 2006-10-18
forum: General Help
---

### Post by hanzomon4 on 2006-10-18
mkisofs -dvd-video gives this error ```
INFO:   UTF-8 character encoding detected by locale settings.
        Assuming UTF-8 encoded filenames on source filesystem,
        use -input-charset to override.
```

I can't figure it out, any ideas?

---

### Post by bswilson on 2006-10-18
You can try this command:

```
$ mkisofs -dvd-video -input-charset default
```

...or you can read the man page for mkisofs which has pages and pages of information, including a special section (see line 930) about character sets.

---

### Post by hanzomon4 on 2006-10-19
Thanks I had messed around with "-input-charset" option, Never tried "default". It worked thanks

---

### Post by hanzomon4 on 2006-10-20
Well it works kinda, I can make an iso but I cant make dvd-video iso heres the output.

```
mkisofs 2.01.01a03-unofficial-iconv (i686-pc-linux-gnu)
Scanning /media/cdrom/
Scanning /media/cdrom/audio_ts
Scanning /media/cdrom/video_ts
mkisofs: Unable to make a DVD-Video image
```

And how do I pass the **[COLOR="Red"]-input-charset default[/COLOR]** option on to gnomebaker. I know I could make an alies but is something "meaux better" then that.

---

### Post by Hugo Galvão on 2007-11-08
You need to have AUDIO_TS and VIDEO_TS, not audio_ts and video_ts, and every file inside VIDEO_TS must have a name all in upper case too, it's all explained in the manual, right after the -dvd-video option

---

