---
title: "Stopmotion cannot create video - No such file or directory"
date: 2013-09-01
forum: General Help
---

### Post by Dragonbite on 2013-09-01
I am running Ubuntu 12.04 and my sone was whosing his younger sister how to make a stop motion movie when we go this mesage:
> 
ffmpeg version 0.8.6-4:0.8.6-0ubuntu0.12.04.1, Copyright (c) 2000-2013 the Libav developers
  built on Apr  2 2013 17:02:36 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
/home/drew/.stopmotion/packer/walking project/images/%06d.jpg: No such file or directory


I went into "configure Stopmotion" and added a line using avconv instead of ffmpeg (but left all of the other settings) so it includes ```
avconv -r 10 -b 1800 -i "$IMAGEPATH/%06d.jpg" "$VIDEOFILE"
```When I try and run an export the message changes slightly > avconv version 0.8.6-4:0.8.6-0ubuntu0.12.04.1, Copyright (c) 2000-2013 the Libav developers
  built on Apr  2 2013 17:02:36 with gcc 4.6.3
/home/drew/.stopmotion/packer/walking/images/%06d.jpg: No such file or directory

What do I need to do or change?  I don't understand where this error is coming from.

---

