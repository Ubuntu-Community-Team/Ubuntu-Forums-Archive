---
title: "Recording video streams from the internet with ubuntu...."
date: 2007-06-01
forum: General Help
---

### Post by Danwright on 2007-06-01
i was wondering if there is a way of capturing the audio and video from an internet stream using ubuntu? i have searched the forums and not been able to find anything and google only comes up with streamripper which cannot record video streams.

Thanks

Dan

---

### Post by faceoftheearth on 2007-06-01
I have a hankering for some Korean TV but I'm ever so lazy so I wrote a script that will download a stream. It uses VLC. I think you just need the basic command or you can go through the graphical interface. This dumps it to the hard drive in raw stream format. You're supposed to be able to encode it to an actual video format too, but I was getting caught in encoder hell so I just gave up. 

```
vlc mms://whatever --demux=dump --demuxdump-file="whateveryourfilepathis"
```

If you want the script just pm me. All it does is that but it names the file with the current date and has a little bit of facility for checking if there's already one for the current date and adding a number to the filename if there is.

---

### Post by khughitt on 2007-06-01
Anyone have any luck doing this with a realplayer (rtsp) stream? For some reason VLC will not play real player streams- I have to use realplay or realplayer instead.

Any ideas?

Thanks

---

### Post by david_2001 on 2007-06-01
> **pwnedd said:**
> Anyone have any luck doing this with a realplayer (rtsp) stream? For some reason VLC will not play real player streams- I have to use realplay or realplayer instead.

Any ideas?

Thanks
The real codecs are proprietary.  Mplayer and xine will play real audio/video with the w32codecs package installed (add the [COLOR="SandyBrown"][Medibuntu]("http://medibuntu.sos-sts.com/")[/COLOR] repository to your sources.list to get w32codecs).

---

### Post by khughitt on 2007-06-03
Okay, I followed instructions on [another post]("http://ubuntuforums.org/showthread.php?t=418785") and am able to rip the streams to .rm files using mplayer just fine now, although still no luck with VLC:

```

$ **vlc rtsp://169.229.131.16:554//bibs/s2006/group1/phys10/20060119.rm?start=4:29&end=1:22:58 --demux=dump --demuxdump-file="test.rm"**
[1] 19460
VLC media player 0.8.6 Janus
Usage: command-not-found [options] <command-name>

command-not-found: error: no such option: --demux
bash: --demux=dump: command not found
$ Sending request: OPTIONS rtsp://169.229.131.16:554//bibs/s2006/group1/phys10/20060119.rm?start=4:29 RTSP/1.0
CSeq: 1
User-Agent: VLC media player (LIVE555 Streaming Media v2006.03.16)
.
.
.
[00000298] live555 demuxer: real codec detected, using real-RTSP instead
[00000298] live555 demuxer error: Nothing to play for rtsp://169.229.131.16:554//bibs/s2006/group1/phys10/20060119.rm?start=4:29
[00000296] main input error: no suitable access module for `rtsp://169.229.131.16:554//bibs/s2006/group1/phys10/20060119.rm?start=4:29'
[00000287] main playlist: nothing to play
[00000287] main playlist: stopping playback


```

I'm fining grabbing the streams with VLC, but would be curious to know why VLC is not having any luck.

---

### Post by faceoftheearth on 2007-06-04
I would too. I'd rather not have all my files in stream format. As far as I know I have all the proper codecs but I get all sorts of errors when I try to stream to particular file type instead of just dumping the raw stream.

---

### Post by Danwright on 2007-06-06
hey, this is the stream i am wanting to record [http://downloadfestival.co.uk/webcast/]("http://downloadfestival.co.uk/webcast/") do you think this method will work on this stream?

---

### Post by Danwright on 2007-06-08
anyone? i would like to save the stream on sunday evening anyone have an idea?

---

