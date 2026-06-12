---
title: "convert xvid to DVD?"
date: 2007-01-08
forum: General Help
---

### Post by bone2006 on 2007-01-08
I'm slowly moving over to linux from windows, but currently when ever I have an xvid video file that I want to burn to DVD, I end up moving the file over to my NTFS partition and rebooting and using ConvertXtoDVD software.  I like the software, because I only have to click file add and then click one button and put a black DVDR inside and 45 minutes later it has a perfect DVD for me.

Is there any linux software out there that's remotely close to this?

---

### Post by linuchsan on 2007-01-08
Did you search the forum, cause your question is already answered

---

### Post by bone2006 on 2007-01-08
yeah, I searched and only saw that it works with wine.  I'd prefer to try and not use wine, unless there was not other alternative.  If that's the answer then I guess I could do that instead of booting up XP each time.  I'd just figure there's better software for linux.  

I guess it's that even in windows I've seen directions that take 200 steps and then the DVD burns, while the software I mentioned was only one or two steps.  I wouldn't mind doing a few steps in linux and I'd rather use free software and support linux based software instead of windows software using wine.

---

### Post by DarthMandeep on 2007-01-08
I think Avidemux will do this easily, but I haven't used it for that just yet.

I actually just installed it earlier today when I needed to burn a DVD, though I didn't have to transcode anything.  It has what looks like a one-click transcode option, just open your video file, select "Auto" and click the DVD option.

---

### Post by bone2006 on 2007-01-08
thank you so much
i'll give it a try

---

### Post by tagra123 on 2007-01-08
I use tovid often -- it might also work.

---

### Post by bone2006 on 2007-01-08
thank you both, seems as if there's not a one step as what I was completely looking for, but
with Avidemux I opened up my xvid file and pressed ok a few times, on the top I clicked auto to change it to DVD and then I clicked saved, which is taking about 45 minutes.

From this mpeg I hopefully can use the software mandvd, which looks promising to get it on a DVDR.  

I don't mind using two programs, I just didn't want to use 6 programs and spend an hour as i've seen instructions for windows utilities in the past.
Thanks again

---

### Post by binks on 2007-01-11
ok m8 just follow the thread in my signature and this will let you input 1 xvid and convert to a dvd with a simple menu screen all in a very easy wizard format 
binks

---

### Post by bone2006 on 2007-01-11
thanks mate
I'll try it as soon as I get home.  I tried a few days ago using Avidemux and then using dvdman and tovid, but both produced errors, when I tried to burn.  It didn't make it to the burning process.  I'll go through your post.

appreciate your help and all the other help
love how helpful the people on this board truly are :)

---

### Post by bone2006 on 2007-01-11
I ran into a little error, I went through the instructions and came up with this:

command: tovid

Found 3 installations of tovid on your system!
I won't run until there is only one of me :)
Installed versions:
   /usr/local/bin/tovid
   /usr/bin/tovid
   /usr/bin/X11/tovid
Exiting...

How do I go about removing other installations?

---

### Post by majoridiot on 2007-01-11
i prefer convertxtodvd and run it in wine.  other than being a little slower to load, it runs just as
well as it did in XP.  i didn't need to do anything special to get it to run in wine.  just installed
it by double-clicking on the windows install.exe

---

### Post by bone2006 on 2007-01-11
I do like convertxtodvd , but I like supporting free software.  If it wasn't for this software many people might have trouble moving over to linux.  The software convertxtodvd isn't free and a lot of people might not pay for it who use it, but I'd prefer to send a donation and support free software that is helping the linux community than purchase software that only runs on linux.  Just as now I'm only going to purchase hardware that makes an effort to be linux compatible.

---

### Post by tanman on 2007-01-12
I actually use DeeVeeDee that is located in the add remove programs. It works excellent and you can control audio and video bitrate. It even gives you the option of a Mpeg video, video ts, and a iso image which I burn with GnomeBaker. I find it will do any avi file.
Just a suggestion

---

### Post by bone2006 on 2007-01-12
I just tried the software devede and it's already loaded with ubuntu it seems, so I didn't even have to search for it.  It was so much easier than I thought.  I just loaded the xvid, then told it that it's only going to be one file and I created an ISO file, then after the file was created on my desktop I clicked write ISO file to disk.
It seems that devede does all the hardwork that it's surprising that the software won't actually burn the ISO file, at least not that I'm aware of.

I was really impressed with devede and how easy it was.  thanks for the recommendation

---

### Post by tagra123 on 2007-01-12
You could try apt-get remove tovid to remove .

I'm not sure how three got installed?

you might also try running by typing th complete path and see if it still complains

/usr/bin/tovid

---

### Post by binks on 2007-01-13
sudo rm -r /usr/local/bin/tovid
sudo rm -r /usr/bin/tovid
sudo rm -r /usr/bin/X11/tovid
then rerun script
binks

---

### Post by fakie_flip on 2007-05-17
I have a similar problem. I installed tovidgui from getdeb.net. When I installed from that deb, it began downloading something. Maybe I shouldn't trust debs from that website. Now I get this error.

```
Found 2 installations of tovid on your system!
I won't run until there is only one of me :)
Installed versions:
   /usr/bin/tovid
   /usr/bin/X11/tovid
Exiting...
```

Did the other person get tovid from getdeb.net?

---

### Post by A_POET on 2007-06-04
which one of these apps have "auto chapters" this IS the feature that makes me use convertXtodvd


does DeeVeedee do this???

---

### Post by funkb4u on 2007-08-19
This isn't actually multiple installations.  This is a byproduct of X11R6 being a symlink to /usr/local.  There's a patch:  see [http://www.nabble.com/multimedia-tovid-fails-to-start-t4256661.html](http://www.nabble.com/multimedia-tovid-fails-to-start-t4256661.html)

H.

---

