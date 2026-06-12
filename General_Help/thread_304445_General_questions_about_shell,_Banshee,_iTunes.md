---
title: "General questions about shell, Banshee, iTunes"
date: 2006-11-21
forum: General Help
---

### Post by newagelink on 2006-11-21
Why is Banshee Music Player an unsupported application in the Add/Remove Applications manager? I thought it was a better choice for gnome than amaroK (which is for KDE?)

[quote="http://www.banshee-project.org/Faq"]**Q: Why do I get the error don't know how to handle application/x-id3?**

and/or

**Q: My MP3 files will not play?**

A: This is caused by not having MP3 support in your version of gstreamer. For Ubuntu Dapper, ```
sudo apt-get install gstreamer0.10-fluendo-mp3
``` should do it. [/quote]

I got that error message when I tried doubleclicking on a song in my library (only playlist) in Banshee. So I tried it:
```
daniel@daniel-laptop:~$ sudo apt-get install gstreamer0.10-fluendo-mp3
Password:
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  gstreamer0.10-fluendo-mp3
0 upgraded, 1 newly installed, 0 to remove and 4 not upgraded.
Need to get 52.9kB of archives.
After unpacking 201kB of additional disk space will be used.
Err http://us.archive.ubuntu.com dapper/universe gstreamer0.10-fluendo-mp3 0.10. 2.debian-1
  Could not connect to us.archive.ubuntu.com:80 (146.137.96.7), connection timed  out
Get:1 http://archive.ubuntu.com dapper/universe gstreamer0.10-fluendo-mp3 0.10.2 .debian-1 [52.9kB]
Fetched 52.9kB in 4m20s (203B/s)
Selecting previously deselected package gstreamer0.10-fluendo-mp3.
(Reading database ... 94836 files and directories currently installed.)
Unpacking gstreamer0.10-fluendo-mp3 (from .../gstreamer0.10-fluendo-mp3_0.10.2.d ebian-1_i386.deb) ...
Setting up gstreamer0.10-fluendo-mp3 (0.10.2.debian-1) ...
daniel@daniel-laptop:~$
```
Erm ... so does that mean it couldn't connect, tried again, and successfully installed the thing? (And what "thing" did it install?)

Also, does iTunes (in Windows) encode the My Ratings into the song itself? If so, are there any linux apps that will use that rating, so I don't have to rate every one of my 15000 songs over again?

---

### Post by GStubbs43 on 2006-11-21
> **newagelink said:**
> 
Erm ... so does that mean it couldn't connect, tried again, and successfully installed the thing? (And what "thing" did it install?)

No, it couldn't connect to [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com), so it connected to [http://archive.ubuntu.com](http://archive.ubuntu.com).
It installed codecs so that Ubuntu can encode mp3 files and play them.

> **newagelink said:**
> 
Also, does iTunes (in Windows) encode the My Ratings into the song itself? If so, are there any linux apps that will use that rating, so I don't have to rate every one of my 15000 songs over again?


No, it saves it into iTunes itself, not the song. ;)

Hope this helps at all. :-D

---

### Post by newagelink on 2006-11-21
It does, thanks...

Why is Banshee Music Player an unsupported application in the Add/Remove Applications manager?

What are the most popular music playing softwares for Linux? (I'll search threads for opinions, as I know this has been asked.) I'm trying to listen to music from /media/DanielDrive/Music (my external hard drive) and I've decided to make the switch from iTunes in Windows to something in Linux.

edit: Screw amaroK. Can't figure out how to add the music from my hard drive to any sort of playlist -- go figure, you'd think it would be "add media", or "new playlist", or something simple. Nope.
And then it crashes. ```
(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1232419136 (LWP 28366)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[KCrash handler]
#6  0xb670673f in KAudioManagerPlay::KAudioManagerPlay ()
   from /usr/lib/libartskde.so.1
#7  0xb679c0cd in KNotify::restartedArtsd () from /usr/lib/kde3/knotify.so
#8  0xb679c350 in KNotify::KNotify () from /usr/lib/kde3/knotify.so
#9  0xb679c82a in kdemain () from /usr/lib/kde3/knotify.so
#10 0x0804e063 in ?? ()
#11 0x00000001 in ?? ()
#12 0x08141748 in ?? ()
#13 0x00000001 in ?? ()
#14 0x00000000 in ?? ()

```What a terrible program.

---

### Post by aysiu on 2006-11-21
Banshee isn't the official music player of Ubuntu, whereas AmaroK *is* the official music player of Kubuntu.

Banshee is in the Universe repositories, which means it's community maintained. You have to enable extra repositories in order to install it.

If you have no idea what I'm talking about, read this link:
[http://www.ubuntu.com/ubuntu/components](http://www.ubuntu.com/ubuntu/components)

By the way, I voted *Other*, as I use Rhythmbox.

---

### Post by newagelink on 2006-11-21
I'll try Rhythmbox again. I'm disappointed with AmaroK, and don't know why I'm having the trouble with it that I am. For some reason I'm having technical troubles, and the design is counter-intuitive to me.

Thanks for the URL -- URI ?? -- I will read. I should be [doing homework]("http://mtsu.edu/~phys2110/Homework/homework.html"), but I'm having trouble focusing; guess I'm a little depressed.

---

### Post by newagelink on 2006-11-21
Everything sounds good with Rhythmbox, except my computer -- or that program -- is lagging for some reason. The display is randomly freezing up momentarily. :(

It also does not seem to be reporting [my Recent Tracks on last.fm]("http://www.last.fm/user/newagelink/charts/?charttype=recenttracks"), unless it is the website is lagging. (I'm listening to 10000 Days right now, and none of the tracks are there.)

Edit > Preferences > Audioscrobbler is enabled and info is typed in ... I alt+tabbed back and forth between Firefox and Rhythmbox just then while typing this, and now the display is freezing up again.

Maybe I just need to restart my computer? (Or is that just a Windows solution from the kernel "leaking memory" or whatever?)

(edit: I restarted my computer, and now it seems to be logging the tracks. Peculiar...?)

[quote="http://www.ubuntu.com/ubuntu/components"]You can enable the universe component by editing the file "/etc/apt/sources.list" after installing Ubuntu.[/quote]What do 'etc' and 'apt' stand for?

-------------

I restarted my laptop; it seemed to be getting low on resources. Now that I did, Rhythmbox is working great -- almost a replica of iTunes, except I can't right click on the taskbar icon to rate music, which sucks, but oh well. :)

Now to ... rate 10420 songs.

edit: The other thing I'm lacking is a Comments thing, for me to jot down where profanity occurs (so I'll remember not to play that song for [my radio show]("http://wmts.danielbridges.info/joomla/").)

---

### Post by strabes on 2007-06-22
You can import ratings from itunes using this amarok script: [http://muro.bryvecer.sk/itunesratings/](http://muro.bryvecer.sk/itunesratings/)

---

