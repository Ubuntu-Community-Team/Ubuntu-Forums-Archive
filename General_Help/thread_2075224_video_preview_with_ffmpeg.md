---
title: "video preview with ffmpeg"
date: 2012-10-23
forum: General Help
---

### Post by sohlinux on 2012-10-23
How can I make a preview video using ffmpeg or similar from the command line?

for example I have a 1 hour avi video, I want to make a preview video by taking a 30 second section of the video every x minutes?

something like this
first part of video take 30 seconds
at 10 mins take 30 seconds
at 20 mins take 30 seconds
and so on until the end then join them all up?

thanks

---

### Post by lykeion on 2012-10-23
You can use the -ss seek parameter in combination with -t time parameter of ffmpeg to do this.

Get the first 30 secs:
```
avconv -i <inputvideo> -t 00:00:30.0 -vcodec copy -acodec copy <outputvideo>
```

seek 10 mins and get 30 secs:
```
avconv -i <inputvideo> -ss 00:10:0 -t 00:00:30.0 -vcodec copy -acodec copy <outputvideo>
```

You could just enter the commands manually and change the start time, or you could write a bash script to handle this automatically.

Note that I'm using avconv instead of ffmpeg (it's the old name)

---

### Post by FakeOutdoorsman on 2012-10-23
> **lykeion said:**
> Note that I'm using avconv instead of ffmpeg (it's the old name)

There is more of a difference between ffmpeg and avconv than just the name:

[Who can tell me the difference and relation between ffmpeg, libav, and avconv](http://stackoverflow.com/a/9477756/1109017)

---

### Post by sohlinux on 2012-10-23
> **lykeion said:**
> You can use the -ss seek parameter in combination with -t time parameter of ffmpeg to do this.

Get the first 30 secs:
```
avconv -i <inputvideo> -t 00:00:30.0 -vcodec copy -acodec copy <outputvideo>
```

seek 10 mins and get 30 secs:
```
avconv -i <inputvideo> -ss 00:10:0 -t 00:00:30.0 -vcodec copy -acodec copy <outputvideo>
```

You could just enter the commands manually and change the start time, or you could write a bash script to handle this automatically.

Note that I'm using avconv instead of ffmpeg (it's the old name)

thanks I will give that a try :)

---

