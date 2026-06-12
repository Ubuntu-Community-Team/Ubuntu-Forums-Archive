---
title: "video convertion"
date: 2007-07-20
forum: General Help
---

### Post by RDUBBALO on 2007-07-20
I need to find a way to convert my video files for use with my blackberry pearl 8100. I need a good way to do this I dont know if I have the avidemux figured out if anyone knows how that works. just change the format and save?

---

### Post by brent113 on 2007-07-21
You'll need a program to do this:

[http://blogs.zdnet.com/blackberry/?p=117]("http://blogs.zdnet.com/blackberry/?p=117") is somehwere to start.  I just googled "convert video blackberry".

It looks like your linux options are prety limited, so I would consider looking into getting wine to run the windows software in linux.

---

### Post by tbroderick on 2007-07-21
Mencoder will do it.
```

mencoder -vf scale=240:-10 <input.file> -o <output.file> -of avi -ofps 15 -ovc lavc -oac lavc -lavcopts vcodec=mpeg4:vbitrate=230:acodec=mp3:abitrate=64
```

Taken from [here]("http://www.the8thsign.com/2006/11/22/encode-video-for-the-blackberry-pearl-8100-mac-edition/")

---

### Post by slamgauge on 2007-11-18
I have the new sprint blackberry 8830 and I have been pulling out my hair trying to find a way to transcode video for my phone.  No one on the forums has had a solution that worked for me up to this point.  I finally figured it out though.

I found MediaCoder [URL="http://mediacoder.sourceforge.net/index.htm"] and it runs great.
They have a wine guide up on the wiki and there are plug-ins for phones and other hand held 
devices.  So far this is the only solution I have found that works for my 8830. 
This should work for the pearl as well, you can even rotate the image when transcoding.

I hope this helps.

---

### Post by atlfalcons866 on 2007-11-18
try this
[http://ubuntuforums.org/showthread.php?t=567016](http://ubuntuforums.org/showthread.php?t=567016)

convert it is a GUI

---

### Post by 43moon on 2007-11-23
RDUBBALO,

I have an 8130 and it took a while to find something that worked right for me.  Avidemux does the trick.  

I open the original video file and use these settings to convert it to a format that works on my Pearl:

Video: Mpeg4(lavc)
Configure: (keep default)
Video Filters: Transform / Resize / Configure / Width: 240 Height: 180

Audio: FAAC
Configure: Bitrate 64kbits
Filters: (keep default)

Format: MP4

Hit the save button and let Avidmux run.

Enjoy,
43moon

---

