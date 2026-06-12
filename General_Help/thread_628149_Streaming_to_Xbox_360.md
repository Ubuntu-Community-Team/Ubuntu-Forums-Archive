---
title: "Streaming to Xbox 360"
date: 2007-11-30
forum: General Help
---

### Post by illbashu on 2007-11-30
i looked in all the threads i could find and none of them had an answer, is there any native gusty software that will stream to an xbox 360? i am useing 32bit version of ubuntu..

---

### Post by illbashu on 2007-12-01
bump! anyone!

---

### Post by soniclava on 2007-12-03
Bump! Bump!

---

### Post by Schalken on 2007-12-03
AFAIK microsoft uses some locked down proprietary protocol to stream to the xbox 360. i haven't heard of anyone bothering to reverse engineer it.

---

### Post by soniclava on 2007-12-03
I am looking into a program called fuppes which looks like it can stream and transcode to windows media format.  I'll let you know if I get it working.

---

### Post by mozetti on 2007-12-03
Since this hasn't gotten alot of attention, I'll just pipe up with my own setup. I installed Virtualbox and made an XP virtual machine. I used a tutorial here for installing VirtualBox and getting the XP VM fully integrated into Gutsy/Compiz, including having my video, audio, and photo partitions accessible to the XP VM.

I then installed Tversity, a Windows media server program that works with a large number of devices, including the Xbox360. Whenever I want to stream anything to my Xbox360, I just fire up the VirtualBox XP VM, run Tversity (actually, it's run on startup), and then watch my videos.

I do notice a performance hit when trying to use the PC while the XP VM is running and streaming to the Xbox360 but it doesn't render the computer unusable, just slower.

Specs:
P4 2.8 Ghz
3 GB DDR 3200 (400 Mhz) dual-channel RAM (also ran it with 1 GB and it ran fine)
Ubuntu 7.10 Gutsy
VirtualBox (latest from site)
Tversity (latest from site)
PC & Xbox360 both hard-wired to Linksys WRT54G v1.1 WiFi router(though I've used Wireless before and it worked fine).

I just found this was easier than dual-booting and having to restart every time I wanted to start & stop streaming to the Xbox360.

---

### Post by BENdage on 2007-12-03
> **soniclava said:**
> I am looking into a program called fuppes which looks like it can stream and transcode to windows media format.  I'll let you know if I get it working.

If you get fuppes working can you try and let me know how you did it. I've followed every set of instructions I can find and I cant get my xbox to see it, I know the server is running cos I can log onto it from other computers, but my 360 cant see it and I dont know if it'll transcode properly. Its probebly just cos I'm a complete n00b and I've done something wrong lol ...

---

### Post by soniclava on 2007-12-05
People are able to get it to work through the methods on this page:
[http://ubuntuforums.org/showthread.php?t=592757](http://ubuntuforums.org/showthread.php?t=592757)

I wasn't able with either of the instructions.  I keep getting an error that looks like this:
> lib/Transcoding/ffmpeg/ffmpeg.cpp: In member function 'void CFFmpeg::new_video_stream(AVFormatContext*)':
lib/Transcoding/ffmpeg/ffmpeg.cpp:1943: warning: converting to 'int' from 'float'
lib/Transcoding/ffmpeg/ffmpeg.cpp: In member function 'void CFFmpeg::new_audio_stream(AVFormatContext*)':
lib/Transcoding/ffmpeg/ffmpeg.cpp:2053: warning: converting to 'int' from 'float'
make[2]: *** [ffmpeg.lo] Error 1
make[2]: Leaving directory `/usr/src/fuppes/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/usr/src/fuppes/src'
make: *** [all-recursive] Error 1

Anyone have an idea?

---

### Post by blackoper on 2007-12-05
check out ushare I'm pretty sure it will do it

[http://ushare.geexbox.org/]("http://ushare.geexbox.org/")

confirmed:
[http://linux.vanvalkinburgh.org/2007/05/25/stream-videos-to-xbox-360-with-patched-ushare/]("http://linux.vanvalkinburgh.org/2007/05/25/stream-videos-to-xbox-360-with-patched-ushare/")

---

### Post by blackoper on 2007-12-05
looks like you'll need to rename your files to mov or other supported extensions for the time being until ushare gets updated to allow all the new supported extensions to your xbox

---

### Post by soniclava on 2007-12-05
I just got Ushare running but my Xbox isn't seeing it.  I tried getting fuppes to work trying everything I could but I still couldn't make the deb package for ffmpeg.  At least Ushare is running but its still not working.  :mad:

Going to mess with this tomorrow

---

### Post by bitshifter1001 on 2007-12-06
If you want to use uShare check out the following links.

A decent HowTo:
[http://ubuntuforums.org/showthread.php?t=632428](http://ubuntuforums.org/showthread.php?t=632428)

Lost of questions and answers:
[http://ubuntuforums.org/showthread.php?t=631213](http://ubuntuforums.org/showthread.php?t=631213)

---

### Post by kajillin on 2007-12-07
this is a dumb idea (streaming music off your pc to an xbox i mean), Why? well because if u always rely on streaming to play your media it limits when you can do so, because i dont think anyone in thier right mind would stream while playing on live which is pretty much the only time you want to listen to music(unless you dont like the stories in singleplayer mode, which i highly doubt).  here is a legal non warranty-breaking mod available to help.

[http://www.llamma.com/xbox360/mods/USB%20Hard%20Drive%20Mod.htm](http://www.llamma.com/xbox360/mods/USB%20Hard%20Drive%20Mod.htm)

this is just hooking a hdd up to your xbox as a portable drive very easy and very inexpensive, unless you dont have a spare drive. even so a ten or twenty gig hdd will only run u ten bucks.

as for video streaming is still the only way to do it without voiding the warranty, 

There are mods out to run and store video files off of a portable device, But these void the warranty so im not going to mention them. Unless you know of one that doesnt then by all means please mention it.

---

### Post by bitshifter1001 on 2007-12-07
> **kajillin said:**
> this is a dumb idea (streaming music off your pc to an xbox i mean), Why? well because if u always rely on streaming to play your media it limits when you can do so, because i dont think anyone in thier right mind would stream while playing on live which is pretty much the only time you want to listen to music(unless you dont like the stories in singleplayer mode, which i highly doubt).

Dumb? That is your opinion. I stream music all the time while playing games and yes, they are games on Live. Halo 3 is a perfect example.


> here is a legal non warranty-breaking mod available to help.

How is streaming content illegal? Since the 360 was released you could always stream music to it from Windows Media Center, and with the Spring Update of 06 video and pictures were available.


> as for video streaming is still the only way to do it without voiding the warranty, 

Wrong again. Windows Media Center uses the uPnP protocol. You can use many products both commercial or Open Source Software to accomplish this. And NO, it does not void your warranty. Have you seen the latest features release with the Fall Update? Check them out. [[COLOR="Red"]Fall Update[/COLOR]]("http://www.xbox.com/en-US/support/systemupdates/20071204-features.htm"). All pertaining to streaming media to the 360. 

As you can see, "Added support for Mpeg-4 part 2 video files in AVI containers" which means DivX / Xvid. This update makes the 360 what it has always meant to be a device which plays all your digital content. With [[COLOR="Red"]IPTV[/COLOR]]("http://www.microsoft.com/presspass/press/2007/jan07/01-08IPTVXboxPR.mspx") coming soon it just makes me question, why wouldn't you stream media to your 360?

---

### Post by Ramorous on 2007-12-07
I've used Twonky Media successfully and find it better than uShare (personal opinion).

I haven't tried it on the Fall Update however but will try soon.

---

### Post by gigaferz on 2007-12-08
[http://sourceforge.net/project/showfiles.php?group_id=159861](http://sourceforge.net/project/showfiles.php?group_id=159861)

itried that program , so far the xbox 360 can see the files on the ubuntu feisty computer, however, when we tried to play an ogg file, we only heard static noise.

---

### Post by illbashu on 2007-12-09
is there anything that can stream movies to the xbox?

edit! i installed ushare and typed in ```
ushare -n Galactica -c'/home/raza/Music' -c '/home/raza/Videos' -x -i eth1
``` in terminal and i got this message 
```
 uShare (version 1.1), a lightweight UPnP Media Server.
Benjamin Zores (C) 2005-2007, for GeeXboX Team.
See http://ushare.geexbox.org/ for updates.
bind: Address already in use
```

the xbox is seeing ushare but there is no files being displayed how do i add files to ushare server?

---

### Post by illbashu on 2007-12-09
bump! can someone help me! plz!

---

### Post by paladin677 on 2007-12-10
> **illbashu said:**
> bump! can someone help me! plz!

My guess is either you have another ushare process running or more likely the kernel has already randomly used the TCP port ushare is trying to use.  Try using the -p argument with a port between 49152 and 65535.

---

### Post by bitshifter1001 on 2008-01-09
> **illbashu said:**
> is there anything that can stream movies to the xbox?

```
 uShare (version 1.1), a lightweight UPnP Media Server.
Benjamin Zores (C) 2005-2007, for GeeXboX Team.
See http://ushare.geexbox.org/ for updates.
bind: Address already in use
```

the xbox is seeing ushare but there is no files being displayed how do i add files to ushare server?

I agree with paladin677. Are you running uShare as a daemon (did you start it from the init script)? If so, stop the service. 

```

sudo /etc/init.d/ushare stop

```

To find all uShare processes
```

sudo ps ax | grep -i ushare

```

This will return the process id's for you. From there you can kill the processes.
```

sudo kill -9 334455 <-- insert process id

```

Hope this helps.

---

### Post by fenrir12 on 2008-04-30
Has anyone experimented with the x360 media server? I am currently using twonkyvision,have used ushare, and am wondering if there are any advantages to ([http://sourceforge.net/projects/x360mediaserve/](http://sourceforge.net/projects/x360mediaserve/)).

---

### Post by Quicky on 2008-05-07
Yeah, I gave that a go before buying Twonky. It worked fine, and with minimal setup, but will only stream music if I remember rightly.

---

