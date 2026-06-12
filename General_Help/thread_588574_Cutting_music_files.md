---
title: "Cutting music files"
date: 2007-10-23
forum: General Help
---

### Post by Baby Boy on 2007-10-23
Hello,

What program can I use to cut out certain parts of mp3s and other music files? I also need to do the same thing for video files.

---

### Post by solar george on 2007-10-23
Audacity for the mp3s - try kdenlive for the videos.

---

### Post by Baby Boy on 2007-10-23
Thanks, I have installed Audacity. But I can't seem to figure out how to cut out a part of the song and save it as a separate music file. Guide at the audacity website doesn't help much. Can you please just help me here and explain how to do it because that's mostly what I plan to do in it?

---

### Post by solar george on 2007-10-23
Import the song into audacity,

Select the section with the selection tool (if you press play it will just play the current selection)

File > Export Selection

Make sure you have Lame installed if you want to export as an mp3.

---

### Post by Baby Boy on 2007-10-24
There is a problem. When I select a section and press *Play* I get the message

> Error while opening sound device. Please check the output device settings and the project sample rate.

And there is only the *Export* option under *File* menu (which exports the whole song), the *Export Selection* is greyed out.

I tried to post a screenshot so you can see if I have really selected anything, but when I try to take a screenshot, the selection dissapears.

---

### Post by Ek0nomik on 2007-10-24
> **Baby Boy said:**
> There is a problem. When I select a section and press *Play* I get the message



And there is only the *Export* option under *File* menu (which exports the whole song), the *Export Selection* is greyed out.

I tried to post a screenshot so you can see if I have really selected anything, but when I try to take a screenshot, the selection dissapears.

Have you installed mp3 support so you can listen to the file?  (Can you listen to *.mp3's?)

Make sure you actually have part of the song *selected* if you want to export selection.  Otherwise you could cut sound before and after the segment you want.

If you want to export to *.mp3, you need to get a lame file.

Run this:

```
sudo aptitude search liblame-dev
```

Paste your output or install the version that pops up.

---

### Post by Baby Boy on 2007-10-24
Yes, I do have mp3 support installed and can listen to mp3s. 

About the selection, yes, I select a section with a left-and-right-gray-arrow thingie on the line representing the song.

Here is the output:

> p   liblame-dev                     - LAME Ain't an MP3 Encoder                 

Doesn't look good :-k.

---

### Post by Ek0nomik on 2007-10-24
Well, to get the *.mp3 export working:

```
sudo apt-get install liblame-dev
```

I am looking into your error...

[http://audacityteam.org/forum/viewtopic.php?f=14&t=58&start=0](http://audacityteam.org/forum/viewtopic.php?f=14&t=58&start=0)
[http://audacityteam.org/wiki/index.php?title=Linux_Issues#Error_Initializing_or_Opening_Sound_Device](http://audacityteam.org/wiki/index.php?title=Linux_Issues#Error_Initializing_or_Opening_Sound_Device)
[http://sg.answers.yahoo.com/question/index?qid=20070627130701AAbCkKQ](http://sg.answers.yahoo.com/question/index?qid=20070627130701AAbCkKQ)

Hope some of these can help.  I have to go to lecture.  :/

---

### Post by Baby Boy on 2007-10-24
Well, I installed lame, and that last link you gave me to Yahoo! Answers helped. I configured the Audio Playback to default ALSA driver and Play button works now, but it doesn't play only the selection but the whole song. Also, Export selection is still greyed out :(. 

BTW, thanks, I can really tell you're trying to help, hope we'll come up with a solution.

---

### Post by FuturePilot on 2007-10-24
You need to highlight the part you want to export.

---

### Post by Baby Boy on 2007-10-24
How? I keep trying to do it with the selection tool (that gray thing with arrows on both end) but it doesn't seem to have any effect.

---

### Post by FuturePilot on 2007-10-24
Use the one that looks like a text selector. Should be the first one in the top row. Then click and drag to highlight the part you want.

---

### Post by Baby Boy on 2007-10-24
When I do that the music starts playing (the selected part) but all the *Export* options are greyed out, and when I stop the music, the selection dissapears.

I am starting to feel really stupid ](*,).

---

### Post by solar george on 2007-10-24
> Dell Inspiron 1501 **Turion64**x2 1.6GHz, 1.5GB DDR2, Ati Xpress 1150 256MB HyperMemory, 80GB HDD

Are you using 64bit ubuntu?

---

### Post by Baby Boy on 2007-10-24
> Dell Inspiron 1501 Turion64x2 1.6GHz, 1.5GB DDR2, Ati Xpress 1150 256MB HyperMemory, 80GB HDD
Ubuntu1501 blog | Why Linux is better? | Tux avatars
Registered Ubuntu user #18213 | Registered Linux user #456577 | [SIZE="2"]64-bit user[/SIZE]
Yep.

---

### Post by solar george on 2007-10-25
Well I don't have a 64bit computer so I can't test this - try installing the 32bit audacity packages.

---

### Post by Baby Boy on 2007-10-25
Problem solved. How? I installed the 1.2.6 stable version for Feisty instead of the 1.3.3 beta for Gutsy. Everything works like it was supposed to now, but I keep getting asked to update Audacity which is kind of annoying. Does this mean the beta version which is included in Gutsy doesn't work in 64-bit or is bugged? Is it working for anyone?

---

### Post by solar george on 2007-10-25
In synaptic you should be able to prevent it trying to upgrade - do a search for audacity, then click Package > Lock Version.

> oes this mean the beta version which is included in Gutsy doesn't work in 64-bit or is bugged?

You should file a bug against it in [launchpad]("https://launchpad.net/ubuntu/+source/audacity")

---

### Post by Baby Boy on 2007-10-26
Thanks for the synaptic tip, now it's locked and doesn't offer me to update anymore.

About the bug report, I wasn't really sure how to do this, so I sent an e-mail to one of the Bug contacts for audacity.

---

### Post by t2000kw on 2007-11-22
> **FuturePilot said:**
> You need to highlight the part you want to export.

I have tried that, selecting (highlighting) the part I want to export and it exports it all right, but the rest of the file also. If I cut the unwanted portion out, then export it, I get the part I want with the rest of the original time as silence. 

Is there a bug in 1.3.3?

That's what Synaptics installed, instead of the stable version. I thought it would only install stable versions.

---

