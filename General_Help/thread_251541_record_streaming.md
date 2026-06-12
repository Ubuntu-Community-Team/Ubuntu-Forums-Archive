---
title: "record streaming"
date: 2006-09-05
forum: General Help
---

### Post by evaristegalois on 2006-09-05
I am trying to record audio streaming.

Let's say the streaming site is mms://public-radio/stream

mplayer mms://public-radio/stream

will start the streaming, and

ffmpeg file.mp3

will record it.

MY PROBLEM is that it will also record input from the built-in microphone of my computer and thus significantly reduce the quality of the recording. I installed gnome-alsamixer to control different sound inputs but I can only check and uncheck "capture" to turn both mplayer's input and microphone input off.

I don't know much about the ins and outs of sound. A simple solution would be great.

--evaristegalois

---

### Post by evaristegalois on 2006-09-05
Ideally, of course, I wouldn't use mplayer at all and specify the stream as input for ffmpeg, but

ffmpeg -i mms://public-radio/stream sound-file.mp3

does not work.

--evaristegalois

---

### Post by master_b on 2006-09-06
I use StreamTuner for accessing/playing/recording online audio, usually Shoutcast, and have had no problems except for using too much disk space :-D 

Bill

---

### Post by RawSewage on 2006-11-05
mplayer YOURURL -ao pcm:file=YOURFILE.wav

---

