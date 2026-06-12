---
title: "How to create logs for video files playback?"
date: 2013-04-29
forum: General Help
---

### Post by c2tarun on 2013-04-29
Hi friends,Is there any way by which I can create a script which will log the opening and closing time of any video file on my machine?For example lets say I have a 2 hr long video. Somebody started to play video at 2 PM and closed video at 2:30 PMI wan't to log the time-stamps of opening and closing of videos? All I want is duration, so that I can find out that for how long my machine is used for watching videos, even if filenames are missing it'll be fine.

---

### Post by hnf a on 2013-04-29
maybe you can go here and edit it and echo the output you can get it : [http://www.thelinuxdaily.com/2012/03/simple-stopwatch-script/](http://www.thelinuxdaily.com/2012/03/simple-stopwatch-script/)

---

### Post by c2tarun on 2013-04-30
Okay I figured out a simple way but it solves only first half of the problem.
I can edit /usr/bin/vlc file and add a line that adds timestamp to a particular file. This way I'll be able to get when a video will start. Now can anyone please tell me how to make an entry on closing vlc (use vlc only for videos). 
Afterwards I can write a small code reads my log file and tell me the total time of video for the day.

---

