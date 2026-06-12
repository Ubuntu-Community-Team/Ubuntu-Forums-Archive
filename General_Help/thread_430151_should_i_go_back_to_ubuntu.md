---
title: "should i go back to ubuntu?"
date: 2007-05-01
forum: General Help
---

### Post by atlfalcons866 on 2007-05-01
I am starting to miss ubuntu:( 
But there are certain things that are holding me back

1. There is no video encoder to convert flv to divx or wmv
2. Is there a free program to write software
3. i couldnt find a video editor.

---

### Post by musicinmybrain on 2007-05-01
> **atlfalcons866 said:**
> 3. i couldnt find a video editor.

Kino is designed specifically for editing movies from DV camcorders. Cinellera is huge, powerful, confusing, and buggy.

If you find a video editor that's actually useful, I'd like to know about it too!

---

### Post by musicinmybrain on 2007-05-01
> **atlfalcons866 said:**
> There is no video encoder to convert flv to divx or wmv.

[Here](http://youmakemedia.com/2006/10/13/converting-flv-to-mpeg-in-linux/) is one way to convert to mpg using ffmpeg. In case that page goes down, here's the recommended command-line: ```
ffmpeg -i video.flv -ab 56 -ar 22050 -b 500 -s 320x240 test.mpg
``` You might choose to tweak the parameters as you see fit. It's also possible to do this with mencoder.

I don't know if ffmpeg or mencoder can write wmv or not. Haven't tried it. I imagine one of them can at least write divx or xvid.

Edit: Wow, ffmpeg is smart. This should do it. ```
ffmpeg -i video.flv -ab 56 -ar 22050 -b 500 -s 320x240 test.wmv
``` Again, tweak to suit.

---

### Post by musicinmybrain on 2007-05-01
> **atlfalcons866 said:**
> 2. Is there a free program to write software

[http://ubuntuforums.org/showthread.php?t=430164](http://ubuntuforums.org/showthread.php?t=430164)

---

### Post by mjpatey on 2007-05-01
If you're looking for a good video editing package a la the entry-level version of Premiere, Vegas Movie Studio, iMovie, etc., check out kdenlive.  It's set up a lot like programs you've probably used in Windows and Mac OS, and the interface is very intuitive and pretty powerful.  It does rely on some KDE elements, but I believe kdenlive installs via Synaptic, and all dependencies are installed automatically.

I tried Kino, but couldn't make heads or tails of its UI.  As I understand it, Kino's main developer has gone on hiatus from the project, and in the meantime has very positive things to say about kdenlive.  :-)

-Mark

---

### Post by musicinmybrain on 2007-05-02
> **mjpatey said:**
> It does rely on some KDE elements, but I believe kdenlive installs via Synaptic, and all dependencies are installed automatically.

It's not in the repos, but it looks really intriguing. I'll have to compile it or grab a deb from the site when I get a chance.

---

