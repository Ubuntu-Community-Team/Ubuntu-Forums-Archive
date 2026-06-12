---
title: "Howto capture good Videos of destop session?"
date: 2006-10-11
forum: General Help
---

### Post by Osvaldo on 2006-10-11
Hi.

Can anyone help. I'm trying to record gimp tutorials in video with Ubuntu. This tutorials will be seen in Windows with Realplayer/VNC.

1) Instanbul records the videos too fast. I've tried to change Frames per second with values like 25.0 and 10.0 but changing values do not seem to change anything (?). The only way to reproduce this videos at normal speed is playing them with mplayer, starting on the comand line. But this is not easy to do in Windows...

mplayer -fps 5 file.ogg

2) I coundn't install xvidcap. I've downloaded the .deb from the developer website, but it doesn't work. It's a Debian .deb, not a Ubuntu one

It gives me this message:
xvidcap: error while loading shared libraries: libpng.so.2: cannot open shared object file: No such file or directory

Where can I get libpng ?

So, please help me to spread the word about gimp.

Best regards

Osvaldo

---

### Post by Osvaldo on 2006-10-18
1) I have instaled libpng3
2) I have renamed the libpng.so.3 to libpng.so.2

It works great. I dont understand why xvidcap isn't better suported in Ubuntu (not even in the help foruns). It's a great app. Great to make tutorials, it doesn't has Istanbul related problems.

To use it type on a shell:

xvidcap --file name.mpg

I also recomend **ffmpeg2theora** to convert the videos.

ffmpeg2theora name.mpg will generate a name.ogg with theora codec

The vídeos are of much better quality than Istanbul.

[http://xvidcap.sourceforge.net/]("http://xvidcap.sourceforge.net/")

Best regards

Osvaldo

---

### Post by Osvaldo on 2006-10-30
Hi. 

On 30 October 2006 Xvidcap has launched a new .deb file.

xvidcap 1.1.4

It works very well on Ubuntu Edgy.

[http://sourceforge.net/project/showfiles.php?group_id=81535](http://sourceforge.net/project/showfiles.php?group_id=81535)

It's a great video tool for tutorials. Istanbul has still many problems.

Osvaldo

---

### Post by ~LoKe on 2006-10-30
> **Osvaldo said:**
> Hi. 

On 30 October 2006 Xvidcap has launched a new .deb file.

xvidcap 1.1.4

It works very well on Ubuntu Edgy.

[http://sourceforge.net/project/showfiles.php?group_id=81535](http://sourceforge.net/project/showfiles.php?group_id=81535)

It's a great video tool for tutorials. Istanbul has still many problems.

Osvaldo

For some reason it crashes when I try to record fullscreen.

---

### Post by Osvaldo on 2006-10-31
xvidcap wasn't made for full screen capture. You need to draw a window and put the bar on top of it. The program isn't perfect, but I couldn't work with Istanbul because it simply just don't work, so I guess this is the best app for the job :-| 

By the way you can make ogg theora films by converting them with ffmpeg2theora.

[http://packages.ubuntu.com/edgy/graphics/ffmpeg2theora](http://packages.ubuntu.com/edgy/graphics/ffmpeg2theora)

It would be nice some MOTU included this deb in the universe repository. Video is a great way to make tutorials for Ubuntu.

Osvaldo

---

