---
title: "Not having a good Linux day ... :-("
date: 2008-05-26
forum: General Help
---

### Post by dbee on 2008-05-26
So basically, I have some fairly remedial tasks that I'd like to perform. Unfortunately, it seems like I might be using the wrong OS though. Don't get me wrong, i love ubuntu and all, but sometimes I wonder whether I can afford to 'spend/waste' the extra time it takes to do simple things ...

At the moment, all i want to do is open a .ai file and edit an mp4 video. I've been onto forums, irc, google, mailing lists and trawling through documentation about how to do this. Everyone seems to either think it either should work, or it won't work.

I've extended my repos, updated the system, pulled in packages from mediaubuntu, installed just about every video editor i can think of as well as some codecs and asked anyone and everyone who might be able to help. I'm going to have spent way more time trying to simply open these files, than I'm going to spend doing this project :-( 

Suffice it to say, that I'm not having a very good 'linux' day (actually, more like 3 days - and counting) :-(. I was wondering whether someone could help ?

Inkscape/GIMP/Evince won't open my .ai file. I can see the contents of the file on my Desktop thumbnail - so something must be able to open it. The file is stored in .ai pdf format. I've tried opening the file, importing the file, I've also downloaded a python script called ai2svg.py ( or something like that ), the script just hangs the system and i need to pkill it.

Most video editors encounter b-frame reference errors when trying to open the mp4 file. The only one that doesn't is avidemux, which is too simple for my needs. When i try to use FFMpeg to transfer the file from MP4 to AVI, all i get is ...
```

ffmpeg -i vid.mp4 -f avi file.avi
.....
Unsupported codec (id=86018) for input stream #0.0

```

I hope I'm not being too whiny here. Like I said, I like Linux. But I'm thinking to myself that if I was using Windows - I'd be finished by this stage. 

Thanks,

---

### Post by bmac on 2008-05-26
Then use windows... Ubuntu isn't for everyone and may not perform specific tasks as M$ does. You may also consider utilizing a dual boot system to accomplish all task while still enjoying the benefits of Ubuntu. Then again you may simply prefer M$ and wish Ubuntu would duplicate all the task similarly without any time investment.
Either way I don't believe your whining or trolling just frustrated.....
Good Luck with what ever decision you make and I really hope you find help with your problem here in the forum, as I'm not technically knowledgeable enough to assist with this particular problem...

But this will bump you post....

---

### Post by MrFSL on 2008-05-26
> At the moment, all i want to do is open a .ai file and edit an mp4 video. 

1) by ".ai" file I am assuming that you mean a Adobe Illustrator File. If so, if seems that acrobat reader will open it. 
[FOUND HERE!]("http://www.adobe.com/products/acrobat/readstep2_allversions.html")

2) Editing an mp4 video. Well Linux does leave much to be desired in terms of video editing; and you said that "avidemux, which is too simple for my needs" so I can assume you wish to do alot to it. Here I agree with **bmac** in saying that Linux might not be the way you want to go.

It sounds like this file if perhaps only using an mp4 container. To find out more details you can post the result of the following commands:

```
file /path/to/MP4_Movie.mp4
```
```
mplayer -frames 0 -identify /path/to/MP4_Movie.mp4
```

---

### Post by dbee on 2008-05-27
OK cheeers guys,

I grabbed acroread from media ubuntu and then I tried to open from the terminal instead of from GNOME ...
```

DISPLAY=:0 && inkscape merit.ai

```
That works :-) 

As for the mp4 file ...

It turns out that the mediaubuntu version of ffmpeg doesn't come with h264 support, which is strange i guess ( especially for universe ). The moral of the story i guess, is that when you're using ffmpeg, it's always better to grab the svn version and then configure it yourself. Even the latest repo packages seem to be out of date, or maybe have licensing issues ?

Anyway, this whole episode just serves to remind me, that one of the greatest benefits of using Ubuntu/Linux as an OS, is the great community that is built around it ...

Thanks guys :-)

---

