---
title: "Video Lost Sound. Can It Be Fixed?"
date: 2019-08-29
forum: General Help
---

### Post by Smallwheels on 2019-08-29
I have a movie file that lost sound. Can it be fixed? How would I do it. I've played other videos and they have audio. I've played this movie in the past and the audio was good. I tried using VLC first and then GNOME MPV. No success with either player. It's a .mp4 file. I tried changing suffixes to .avi and .mkv with no success. 

Thank you for your input.

---

### Post by SeijiSensei on 2019-08-29
Install SMPlayer which will use mpv, then look at Options > Preferences > Audio and see if changing the audio driver, or any of the other settings, helps.

View > Information and properties will tell you if it sees the audio track and what was used to encode it.

---

### Post by ajgreeny on 2019-08-29
Install ***mediainfo*** package then run command ```
mediainfo /path/to/file.mp4
``` which will give you all the details of the problem file, including the sound codecs etc etc.

---

### Post by Smallwheels on 2019-08-29
I downloaded SMPlayer and tried different settings in the General tab at the top. The choices were mpv, mplayer, and other. Which had a box with mpv in it. I went to the View tab and got the information about the video. At the "Initial Audio Stream" section the part that said "Selected codec:" had nothing listed. Above this section there is a tab called Audio codec. Clicking it opens a page with what looks like more than a hundred possible codecs. I tried selecting many and clicking apply. Nothing changed. There was a little circular loading wheel that appeared for a second every time I pressed apply. At the same time it said Subtitles applied, or something like that. 

Under the video codec it is listed as h264 - H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10. 

How would I install the mediainfo package? How would I use it with this video to learn what is happening? 

Thanks for helping.

---

### Post by ajgreeny on 2019-08-30
The command ```
sudo apt install mediainfo 
```will install the utility just as the ***apt install*** command installs anything else in the repos.

However, it may not be shown in the ubuntu-software, or whatever it's now called, which I never use, but it will be in ***synaptic*** which is definitely worth installing, in my opinion if you want to use a GUI for package management.

---

### Post by SeijiSensei on 2019-08-30
> At the "Initial Audio Stream" section the part that said "Selected codec:" had nothing listed.
Hmm, that sounds like there's no audio stream in the file at all.  You should have seen something like:

Format: ac3
Bitrate: 319 kbps
Rate: 44100 Hz
Channels: 2
Selected codec: ac3

Other possibilities might have been AAC, FLAC, or even MP3.  

You say you have played this file before, and it had sound. Was it converted in some fashion like with ffmpeg? If so, do you still have the original?

mpv can detect and play pretty much anything thrown at it, so I doubt the file is using a codec mpv doesn't recognize.

---

