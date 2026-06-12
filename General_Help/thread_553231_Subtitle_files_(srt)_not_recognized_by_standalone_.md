---
title: "Subtitle files (srt) not recognized by standalone DVD-player"
date: 2007-09-17
forum: General Help
---

### Post by webaake on 2007-09-17
Just tried burning some avi's to data dvd with repectively K3B, Gnomebaker, Brasero for playing on my standalone Philps DVP 630/642. I used to burn in Nero/windows without any problems - subtitles playing just fine.

Now my standalone will not recognize the srt-files. They have a red question mark as icon.

What I've tried so far:
Joilet (of course)
Allowing almost everything in K3B's advanced settings.
Renaming both the avi file and the srt file to 8+3 chars.



The DVD's and subtitles work perfectly on Ubuntu and Windows, and in VLC on both platforms.

Can it be something wrong with the mime type in Ubuntu? It's application/x-srt, wich is supposed to be a subset of text/plain.

Or is just not possible?

---

### Post by chrome307 on 2007-09-17
Standalone players need VOB subs for playback. **( *.sub & *.idx )**

If you want to create an DVD from an AVI file with SRT files, you could use ConvertXtoDVD or WinAVI.  Both should allow you to load up the subtitle files along with with movie which will give you a DVD you can burn. (Windows)

Not sure if Linux/Ubuntu has an equivalent.

---

### Post by webaake on 2007-09-17
The Philips DVP 630/642 plays Divx/Xvid just fine, and .srt/.sub files as specifications.

The problem seems to be the way Ubuntu handles the .srt files......


Found a link here:

[http://ubuntuforums.org/archive/index.php/t-204426.html](http://ubuntuforums.org/archive/index.php/t-204426.html)

That might solve my problem.

---

### Post by perdubug on 2008-03-18
You can create an DVD from an AVI file with SRT files on Ubuntu by using DeVeDe. It works fine on my Philips  CVP 3000K DVD player.

---

### Post by webaake on 2008-03-18
My solution was to buy NeroLinux. It works very well when burning avi-files and .srt/.sub files to a data dvd.

---

