---
title: "How to play videos in Ubuntu?"
date: 2005-04-10
forum: General Help
---

### Post by maxsideburn on 2005-04-10
I just switched from Mandrake Linux 10.1 Official to Ubuntu "Hoary Hedgehog". The only thing I've noticed majorly different so far is that Ubuntu will not play any of my videos no matter the format with Totem Movie Player, how would I go about installing XINE or MPLAYER? In Mandrake I would just go to "Install Programs" (the RPM manager) and I could download these packages. How would I do something like this in Ubuntu?

---

### Post by heimo on 2005-04-10
I hate to reply with a link, but this is really, really good source of information for your problem. What you need is:

[http://www.ubuntuguide.org/#generalnotes](http://www.ubuntuguide.org/#generalnotes)

and:

[http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/)

You need something like:
```
deb http://backports.ubuntuforums.org/backports hoary-backports main universe multiverse restricted
deb http://backports.ubuntuforums.org/backports hoary-extras main universe multiverse restricted

```
in /etc/apt/sources.list and

```

sudo apt-get update
sudo apt-get install w32codecs
```

for more information, read the UbuntuGuide - it's great.

---

### Post by maxsideburn on 2005-04-11
[[IMG]http://img220.echo.cx/img220/9581/screenshot8eb.th.png[/IMG]](http://img220.echo.cx/my.php?image=screenshot8eb.png)

That's what happens when I try to play anything except an MPG. When I play an MPG it just freezes up. What am I doing wrong? I mean I did everything you said to do, it installed the W32 codecs.......Ubuntu looks great, but it's so different from Mandrake.

---

### Post by heimo on 2005-04-11
[QUOTE=maxsideburn]I just switched from Mandrake Linux 10.1 Official to Ubuntu "Hoary Hedgehog". The only thing I've noticed majorly different so far is that Ubuntu will not play any of my videos no matter the format with Totem Movie Player, how would I go about installing XINE or MPLAYER? In Mandrake I would just go to "Install Programs" (the RPM manager) and I could download these packages. How would I do something like this in Ubuntu?[/QUOTE]

I'm not at my Linux box at the moment - sorry for inaccurate instructions - but look in Gnomes menus for Add Remove Programs or Synaptic. You could also use apt-get on terminal.

Also try:
```
sudo apt-get install gstreamer0.8-plugins
```

And look at the Applications->Sound & Video-> xine. I don't like totem, so I have installed vlc and I occasionally use xine. You could probably install vlc by entering:

```
sudo apt-get install vlc
```

To search for packets using apt-get, use apt-cache for example like this:
```
sudo apt-cache search video
```

---

### Post by strawberry on 2005-04-11
I insist on playing video files with the 'default' Totem Movie Player. I think it is not a mistake developers put totem-gstreamer package in ubuntu. But I haven't read a word that anyone managed to play video with Totem. Maybe it's my fault  :roll: 
I installed the w32codecs pack but Totem still can't play any media file.
Thnx any help in advance.

---

### Post by fsman on 2005-04-11
go into synaptic and select totem-xine. it will prompt to remove totem-gstreamer - say yes.
I had to do this to get totem to play video without stuttering.
PS I too had mdk10.1 and only just moved to ubuntu and its playing the same as mdk.

---

### Post by heimo on 2005-04-11
fsman advice is good, Totem can use gstreamer or xine-lib, so you can try to install the totem-xine package (which will remove totem-gstreamer). Or you can try to install gstreamer0.8* stuff and use gstreamer.

```

 But I haven't read a word that anyone managed to play video with Totem. 
```
I'm playing videos with totem at this very moment, using totem-gstreamer.

Hope you can get it fixed.

Cheers! :)

---

### Post by strawberry on 2005-04-12
fsman:
I did the same after I had installed warty: w32codecs and xine worked well together. 
Now I upgrade to hoary and I can't believe the 'default' ubuntu movie player (the gstreamer version) does not work.

heimo:
Thanks, installing the gstreamer0.8-plugins (and its dependencies) was the clue. Though the divx and SVCD files remain unplayable.
Should I change to totem-xine after all?  :roll:

---

### Post by heimo on 2005-04-13
[QUOTE=strawberry]fsman:
heimo:
Thanks, installing the gstreamer0.8-plugins (and its dependencies) was the clue. Though the divx and SVCD files remain unplayable.
Should I change to totem-xine after all?  :roll:[/QUOTE]

Well, why not? It's still Ubuntu, it's still totem. What ever works for you is good and after all it's also about the freedom of choice. :)

---

### Post by Poyayan on 2005-04-13
for divx and stuff you need the gstreamer-ffmpeg package.  However even with this file totem-gstreamer is slower than totem-xine when playing most files that use formats such as divx.  Your choice really.  If gstreamer-ffmpeg works fine use it if it does use totem-xine or vice versa

---

### Post by strawberry on 2005-04-13
Poyayan, heimo:
Installing gstreamer-ffmpeg solved my trouble. Totem can play the divx files but the sound is broken and quality of picture is low.

I'll go and change gstreamer to xine. Ubuntu should come with xine by default.

I see totem-xine is in universe group. I think that's reason.
Thnx for your help anyway :)

---

### Post by gunnyman on 2005-04-13
I can't play WMV files in totem-Xine.  The audio cuts out and chirps.
Mplayer works great.
This problem isn't  evident  using mozplugger, only in files I have downloaded.
totem-gstreamer won't play at all. It gives codec error.

---

### Post by mike998 on 2005-04-13
[QUOTE=gunnyman]I can't play WMV files in totem-Xine.  The audio cuts out and chirps.
Mplayer works great.
This problem isn't  evident  using mozplugger, only in files I have downloaded.
totem-gstreamer won't play at all. It gives codec error.[/QUOTE]

I've had a bit of a problem with wmv files.  Other than that Xine (not totem-xine) is my player of choice...

---

### Post by strawberry on 2005-04-14
Totem-xine works fine. 
I haven't tried any wmv file yet. 
gunnyman said he prefered mplayer. I haven't found it in the deb packages so I think it have to compile from source. Is it difficult? (silly question) I'll try it later  ;-)

---

### Post by heimo on 2005-04-14
mplayer is available in marillat repository - or of course you can compile it from source too :)
[http://www.ubuntuguide.org/#mplayer]("http://www.ubuntuguide.org/#mplayer")

And it actually seems to be in multiverse, too.

---

### Post by strawberry on 2005-04-15
heimo:
I visited the mplayer home page ([www.mplayerhq.hu](www.mplayerhq.hu)) where I found the requirements/hardware recommendations and it seems I should upgrade my video card for proper performance...  :?:  So I'll stay for awhile at totem-xine. I'm new in linux so I'll find lot of other things to learn. 8)

---

### Post by Stormy Eyes on 2005-04-15
I use and recommend VLC.

---

### Post by gratefulfrog on 2005-04-28
I've tried absolutely all the above players on Hoary 64bit and find that none are really working great; Totem is the worst, only playing audio part of any video.

I'm wondering if the binary ati drivers will improve the video playback capability of my ATI 9250 card...

Anyone have any info on the impact of using the binary drivers for video playback?

I have heard that it is irrelevent? what do y'all think?

---

### Post by stevenyu on 2005-04-28
I have install w32codecs and well as all the gstreamer plugin, however when I go to the Quicktime webpage to watch quicktime movie trailer, i just get a black windows with no picture in there.

And some MPEG files can't be played at all ](*,)

---

### Post by mrbass on 2005-04-28
yeah apple.com/trailers you need to
killall -9 esd
and then mplayer will play them in firefox

for a permanent fix
check out [http://ubuntuguide.org](http://ubuntuguide.org) for the "How to fix sound in GNOME"

---

