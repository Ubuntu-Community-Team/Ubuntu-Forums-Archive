---
title: "ffmpeg xvid edgy"
date: 2006-12-12
forum: General Help
---

### Post by daveyiv on 2006-12-12
Are there any good guides for compiling ffmpeg from source to include xvid support? I have been trying to find something, but the ones I have found seem to be for older versions of ubuntu.

---

### Post by RAOF on 2006-12-12
Are you aware that you don't need to?  Xvid is just a particular MPEG4 encoder, and FFmpeg can already encode to MPEG4.  If you want the resulting file to look like xvid to apps, you can use the "-vtag XVID" to mark the stream as XVID.

---

### Post by daveyiv on 2006-12-12
Well, I was trying to use nuvexport for mythtv to export to mpg4 or xvid. But these are my options:

```
Using ffmpeg for exporting.
What would you like to do?

  1. Export to XviD (disabled)
  2. Export to SVCD
  3. Export to VCD
  4. Export to DVCD (VCD with 48kHz audio for making DVDs)
  5. Export to DVD
  6. Export to DivX
  7. Export to ASF
  8. Export to MP3
  9. Export to PSP (disabled)
 10. Export to MP4 (iPod) (disabled)
 11. Export to .nuv and .sql

  q. Quit

Choose a function:  

```

---

### Post by RAOF on 2006-12-12
Oh, ok.  So the script is broken :(.

I don't know of any good guides.  Although you could add a src-deb line to one of my repositories - they contain AMD64 packages, but you could run
```
apt-get build-dep ffmpeg
apt-get -b source ffmpeg
```
to get all the build-dependencies and then build an ffmpeg package.

Alternatively, get the build-deps and then get ffmpeg's source from SVN.

---

