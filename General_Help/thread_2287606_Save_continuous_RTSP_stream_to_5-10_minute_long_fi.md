---
title: "Save continuous RTSP stream to 5-10 minute long files"
date: 2015-07-20
forum: General Help
---

### Post by bmather9 on 2015-07-20
I've attempted to use what I found here: [http://stackoverflow.com/questions/10459338/save-continuous-rtsp-stream-to-5-10-minute-long-mp4-files](http://stackoverflow.com/questions/10459338/save-continuous-rtsp-stream-to-5-10-minute-long-mp4-files)

Instead I am writing to a .mkv file with the following command: 

```
avconv -i rtsp://admin:password@192.168.1.105/profile4/media.smp -c copy -map 0 -f segment -segment_time 60 "/rpool/files/media/recording/capture-%03d.mkv" 
```

This seems to work just how I'd like it, except that only one empty file appears in the ../capture directory until I press Ctrl+C to end the capture.  At that point all the video files that I'd expect appear.  I'm looking to use this for recording of multiple IP cameras around my house, so I'd plan to have about 6 streams like this running (at some lower framerate etc) and I'd like to be able to view the files that have been recorded so far.  _**How do I get those files to show up as they're written?**_



I'd also need it to begin overwriting files once I have about 7 days or so recorded, but I think I could build a script to take care of this.  Eventually I'd like some of the camera's to stop recording when my cell phone connects to my home Wifi, so that I can walk around in my underwear etc... without being recorded.  I also think I can script this somehow, or may end up trying some home automation software such as [Home Assisstant]("https://home-assistant.io/").   

I know software such as ZoneMinder could accomplish all this for me, but right now I have another thread where I am attempting to get this software working.  I figure this could be a more simple solution for what I want to accomplish anyway.  

Thanks for any help in advance.

---

### Post by bmather9 on 2015-07-23
No ideas for this one?

---

### Post by Lars Noodén on 2015-07-24
Just a wild guess but would using [timeout](http://manpages.ubuntu.com/manpages/trusty/en/man1/timeout.1.html) cause avconv to save the file on time?  You could run it in a loop so it keeps creating new files.

---

### Post by bmather9 on 2015-07-25
> **Lars Noodén said:**
> Just a wild guess but would using [timeout]("http://manpages.ubuntu.com/manpages/trusty/en/man1/timeout.1.html") cause avconv to save the file on time?  You could run it in a loop so it keeps creating new files.

I'm fairly confident that this would work, but I've read other who have done this and found that the stop and restart causes them to lose roughly 10 secs of recorded video.  It seems like there should be some way to make the -segment option perform this for me.

---

