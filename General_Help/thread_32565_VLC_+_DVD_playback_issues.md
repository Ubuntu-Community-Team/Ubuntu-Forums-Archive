---
title: "VLC + DVD playback issues"
date: 2005-05-08
forum: General Help
---

### Post by gazzie on 2005-05-08
Hi there!

Just installed Ubuntu on Friday, it's my first ever Linux install. I'm using the Hoary AMD64 kernel.

I got hold of VLC from multiverse and it plays all my AVIs etc without problem. However when I try to do Open disc -> DVD I have a couple of problems:

1) When I choose DVD (menus) (dvd:///), after I press OK, I briefly see the default VLC panel and then it closes itself.

2) If I choose DVD (dvdsimple:///), I get no control over episode selection (so it's useless for a 24 disc for example) and the sound doesn't work. Any ideas?

I also have no VLC icon - what's up with that ?;)

---

### Post by cdhotfire on 2005-05-08
```

$ sudo apt-get install libdvdcss2

```
any use?

and for vlc icon, restart gnome and you should have it back.:)

---

### Post by gazzie on 2005-05-08
```
libdvdcss2 is already the newest version.
```

---

### Post by gazzie on 2005-05-08
[QUOTE=gazzie]```
libdvdcss2 is already the newest version.
```[/QUOTE]
 I restarted GNOME and my VLC icon is a traffic cone... is that right? :P

---

### Post by Maestro23 on 2005-05-08
[QUOTE=gazzie]I restarted GNOME and my VLC icon is a traffic cone... is that right? :P[/QUOTE]

Yes, correct icon.  If you don't believe me, check their site:  [http://www.videolan.org/](http://www.videolan.org/)  ;-) 

Good program by the way, I use it also.

---

### Post by gazzie on 2005-05-08
[QUOTE=Maestro23]Yes, correct icon.  If you don't believe me, check their site:  [http://www.videolan.org/](http://www.videolan.org/)  ;-) 

Good program by the way, I use it also.[/QUOTE]
 Another VLC issue... when I right-click a video file and go to open-with, when I select VLC, it spouts back with "Cannot add application to application database". If I want to open files I have to go to file -> open in VLC itself. A bit annoying!

---

### Post by gazzie on 2005-05-08
No ideas?

---

### Post by bored2k on 2005-05-08
[QUOTE=gazzie]No ideas?[/QUOTE]
 Just click properties > open with > add > custom command > vlc. This will make vlc default.

---

### Post by bored2k on 2005-05-08
[QUOTE=gazzie]I restarted GNOME and my VLC icon is a traffic cone... is that right? :P[/QUOTE]
 You dont have to restart gnome to see panel changes. Just type [in a terminal]
killall gnome-panel
They will go away and restart with the new changes.

---

### Post by gazzie on 2005-05-08
[QUOTE=bored2k]Just click properties > open with > add > custom command > vlc. This will make vlc default.[/QUOTE]
 Awesome, that's worked.

Just the DVD issue to fix now... no ideas? ;/

---

### Post by bored2k on 2005-05-08
[QUOTE=gazzie]Awesome, that's worked.

Just the DVD issue to fix now... no ideas? ;/[/QUOTE]
 It's no vlc fix. But did you try running the dvd with mplayer, totem-xine or ogle-gui ?

---

### Post by bored2k on 2005-05-08
> Just installed Ubuntu on Friday, it's my first ever Linux install. I'm using the Hoary AMD64 kernel.

In just 2 linux days this is your small problem? Your a fast learner dude :-P
Pretty amazed you got as far as adding repositories to install vlc :roll:

---

### Post by darkoptix on 2005-05-08
Well, you did get the vlc esd plugin and set the sound to go though esd, did you not?

---

### Post by bored2k on 2005-05-08
[QUOTE=darkoptix]Well, you did get the vlc esd plugin and set the sound to go though esd, did you not?[/QUOTE]
 What does that have to do with a problem opening a dvdisc? :?

---

### Post by bored2k on 2005-05-08
[QUOTE=darkoptix]Well, you did get the vlc esd plugin and set the sound to go though esd, did you not?[/QUOTE]
 I don't think that's relevant to his dvdisc problem.. :\ :?

---

### Post by cdhotfire on 2005-05-08
[QUOTE=bored2k]In just 2 linux days this is your small problem? Your a fast learner dude :-P
Pretty amazed you got as far as adding repositories to install vlc :roll:[/QUOTE]

Ya thats quite amazing, i remember my second day in linux, i was like what im i suppose to type into this little black box?:-?

---

### Post by bored2k on 2005-05-08
[QUOTE=cdhotfire]Ya thats quite amazing, i remember my second day in linux, i was like what im i suppose to type into this little black box?:-?[/QUOTE]
 I think my second day with linux.. I would probably be typing DOS commands lol
```
dir
dir/w
deltree
``` :-s

I also remember "Ok I downloaded application X. What now.. how the heck do I install this? *reads README* Oh i need to compile.. *40 minutes later* Oh i need to compile.."

I didn't even think of asking around, it was just me and my curiosity :(

---

### Post by gazzie on 2005-05-08
[QUOTE=bored2k]It's no vlc fix. But did you try running the dvd with mplayer, totem-xine or ogle-gui ?[/QUOTE]
 [[IMG]http://img85.echo.cx/img85/9264/mplayer9ms.th.png[/IMG]](http://img85.echo.cx/my.php?image=mplayer9ms.png)

It then gave me an "mplayer has crashed" message.

---

### Post by bored2k on 2005-05-08
[QUOTE=gazzie][[IMG]http://img85.echo.cx/img85/9264/mplayer9ms.th.png[/IMG]](http://img85.echo.cx/my.php?image=mplayer9ms.png)

It then gave me an "mplayer has crashed" message.[/QUOTE]
 Easy on the images.

Ok, go to preferences > audio and make mplayer/vlc use esd then retry.

---

### Post by gazzie on 2005-05-08
Crashed again.

---

### Post by gazzie on 2005-05-08
If I do applications -> run application ->

mplayer -nosound dvd://1

then I get a picture

Some sound issue it seems?

---

### Post by cdhotfire on 2005-05-08
do 
```

$ vlc

```

open your dvd, and tell us what comes out in the terminal, must be some error, thats closing ur vlc.:???:

---

### Post by gazzie on 2005-05-08
```
gareth@pogo:~$ vlc
VLC media player 0.8.1 Janus
libdvdnav: Using dvdnav version 0.1.9 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.8 for DVD access
libdvdnav: DVD Title: PHOENIX_NIGHTS
libdvdnav: DVD Serial Number: 2d17b941
libdvdnav: DVD Title (Alternative):
libdvdnav: Unable to find map file '/home/gareth/.dvdnav/PHOENIX_NIGHTS.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fd0000. Regions: 2

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00000144
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x00002686
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x00023c46
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x002e6894
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x003542a8
libdvdread: Elapsed time 0
libdvdread: Found 4 VTS's
libdvdread: Elapsed time 0
Segmentation fault
```

---

### Post by gazzie on 2005-05-09
May or may not be related: my DVD drive now won't eject!

---

### Post by cdhotfire on 2005-05-09
lol, you just keep having more and more problems.  Try
```

$ sudo unmount /media/cdrom0

```

cdrom0 if its the first one 1 for second.

if that doesnt work, then reset your comp, works for me all the time. If that still doesnt work, then you having dvd problems.:???:

---

### Post by gazzie on 2005-05-09
The drive works perfectly in Win XP :P

[http://www.ubuntuforums.org/showthread.php?t=29132&highlight=DVD+playback](http://www.ubuntuforums.org/showthread.php?t=29132&highlight=DVD+playback)
[http://www.ubuntuforums.org/showthread.php?t=28484&highlight=signal+11+decode_audio](http://www.ubuntuforums.org/showthread.php?t=28484&highlight=signal+11+decode_audio)

Similar problems... got a few things to try when I get home from work :)

---

### Post by AndreAPL on 2005-05-09
hi there. i have a similiar problem. what graphic card do you have ? :-?

---

### Post by gazzie on 2005-05-09
Radeon 9700 Pro

---

### Post by gazzie on 2005-05-09
```
totem dvd://
```

that works  \\:D/

---

