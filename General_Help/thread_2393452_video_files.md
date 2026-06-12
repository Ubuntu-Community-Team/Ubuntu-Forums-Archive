---
title: "video files"
date: 2018-06-03
forum: General Help
---

### Post by TheTinyt1 on 2018-06-03
Is there any way to convert video files to audio formats so that they can be listened to with out the video?

---

### Post by lisati on 2018-06-03
Check out [Audacity]("https://www.audacityteam.org/"). 

I believe there's an Ubuntu-friendly version available in the repos.

There is an feature called "Chains" on its File menu which comes with an option to convert multiple files to MP3 format, this should work  with video files as well as audio files.

---

### Post by Perfect Storm on 2018-06-04
A very easy app for that is soundconverter.

```
sudo apt install soundconverter
```

---

### Post by leunam12 on 2018-06-04
Winff

---

### Post by Yellow Pasque on 2018-06-04
If you would prefer not to convert, you can just use:
```
mpv --no-audio filename
```
I use this in the summertime when I want to go to sleep and listen to a video. It saves CPU and cuts down on heat/power.

---

### Post by kazakore on 2018-06-04
[FONT=arial]> **Temüjin said:**
> If you would prefer not to convert, you can just use:
```
mpv --no-audio filename
```
I use this in the summertime when I want to go to sleep and listen to a video. It saves CPU and cuts down on heat/power.


I can only assume you don't mean --no-audio as that seems rather strange an argument to keep audio only, but I don't use mpv so maybe it is correct.... (--no-video maybe?? Yeah manpage seems to say that would be right.)


As to how I'd do it:
If you do want to extract the files I know two ways to do this via demuxing, without actually changing the data and thus no loss of quality.

A. GUI method.
Use Kdenlive to Demux and save the audio.

B. CLI method
ffmpeg -i /path/to/video -vn -acodec copy /path/to/save/audio
There are various ways to find out what codec the audio was, to give the output file the right extension, it should say during the ffmpeg processing if you read the std output, or VLC can give you codec info.[SIZE=2]
[/SIZE][/FONT]

---

### Post by Yellow Pasque on 2018-06-04
Yes, sorry. It's "--no-video"

---

