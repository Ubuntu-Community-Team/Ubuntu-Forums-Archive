---
title: "ffmpeg, remove parts of file."
date: 2013-03-06
forum: General Help
---

### Post by spiritech on 2013-03-06
i would like to use ffmpeg to cut out sections of a mp4 file. i understand how to do it if it is at the beginning or end of the film using the start time or duration options, how can i cut out a section that is in the middle of the film?

spiritech

---

### Post by Mr. Shannon on 2013-03-06
After doing some searching it seems the way to do this is to extract the beginning and end and then join the files.  However, as mentioned here [http://stackoverflow.com/questions/7567713/combining-two-video-from-ffmpeg](http://stackoverflow.com/questions/7567713/combining-two-video-from-ffmpeg), .mp4 cant be joined with the cat command.  Therefore, you need to convert to .mpg during the extraction of the two halves of the video, as .mpg video can be joined with the cat command according to the above link.  NOTE: All this was found with a few minutes of searching.

---

### Post by FakeOutdoorsman on 2013-03-07
> **Mr. Shannon said:**
> After doing some searching it seems the way to do this is to extract the beginning and end and then join the files.  However, as mentioned here [http://stackoverflow.com/questions/7567713/combining-two-video-from-ffmpeg](http://stackoverflow.com/questions/7567713/combining-two-video-from-ffmpeg), .mp4 cant be joined with the cat command.  Therefore, you need to convert to .mpg during the extraction of the two halves of the video, as .mpg video can be joined with the cat command according to the above link.  NOTE: All this was found with a few minutes of searching.

That StackOverflow answer is outdated. The method of converting to mpeg-2 video and using cat is no longer required now that there is the concat [demuxer](http://ffmpeg.org/ffmpeg-formats.html#concat), [protocol](http://ffmpeg.org/ffmpeg-protocols.html#concat), and [filter](http://ffmpeg.org/ffmpeg-filters.html#concat). You can create the segments that you want to join:

```
ffmpeg -i input.mp4 -ss 10 -t 5 -c copy -map 0 output1.mp4
ffmpeg -i input.mp4 -ss 120 -t 12 -c copy -map 0 output2.mp4
```

And then join them with the [concat demuxer](http://ffmpeg.org/ffmpeg-formats.html#concat) as shown in [How to concatenate (join, merge) media files](https://ffmpeg.org/trac/ffmpeg/wiki/How%20to%20concatenate%20%28join%2C%20merge%29%20media%20files).

I don't think the fake "ffmpeg" from libav in the repo can do this, so you'll have to get a recent real ffmpeg. Static builds are easy to use: [example instructions](http://ubuntuforums.org/showthread.php?t=2121268&p=12536453&viewfull=1#post12536453).

---

### Post by spiritech on 2013-03-07
i will give the concat demuxer a go, seems like the simplest option.

---

