---
title: "looking for an app to record my screen to a video file"
date: 2022-07-09
forum: General Help
---

### Post by Skaperen on 2022-07-09
i would like to record my own screen to a video file.  capturing to a directory of image files, one per frame, might be a suitable alternative (i've tried this with image capture, but nothing gets even close to fast enough).  any standard video format supported by *ffmpeg* input is usable.  i am wanting to record my typing speed so i want to get 60 fps.  also, i don't want a GUI or any other window popping up (it would mess up things i want to record).  so it needs to be command line started and stopped (maybe stopped with a single keystroke like ESC or Ctrl-C or a signal).  i can create an icon to have it started in the background.

please don't suggest *possibilities*.  if you have tried it on Ubuntu 20.04 or earlier and got it to work for you, then you *know* it works and can tell others your wisdom.

---

### Post by &amp;KyT$0P# on 2022-07-09
Have you tried ffmpeg?  I have done screen recording with ffmpeg in 20.04, starting & stopping it at command line, and it worked for me.

---

### Post by HermanAB on 2022-07-09
There is a program called istanbul which works well, but I would simply use ffmpeg - a one liner.

---

### Post by Skaperen on 2022-07-10
i did find a command line (all the options) online and tried it.  what it wrote to the file was useless.  it had 1 video stream that was all black and 1 audio stream that was dead silence.  there was no clear and obvious way to stop the recording and i think a sudden kill left the file in a corrupt state.

if it actually works for you, can you post your exact command line arguments and options and what signal makes it correctly end?  ffmpeg tends to be overly complex and hard to learn everything in it.

---

### Post by dragonfly41 on 2022-07-11
Try FlameShot instead.

P.S. Might there be easier ways to test typing speed?

[https://www.ubuntupit.com/best-typing-tutor-software-for-linux-to-increase-your-typing-skill/](https://www.ubuntupit.com/best-typing-tutor-software-for-linux-to-increase-your-typing-skill/)

---

### Post by #&amp;thj^% on 2022-07-11
> **Skaperen said:**
> 
if it actually works for you, can you post your exact command line arguments and options and what signal makes it correctly end?  ffmpeg tends to be overly complex and hard to learn everything in it.
The line I use most often is:
```
ffmpeg -f x11grab -y -r 60 -s 1920x1080 -i :0.0 -vcodec huffyuv out.avi

```
You specified 60fps and that's my liking as well.
I'll also make a directory before hand:
```
mkdir -p ~/Videos/ffmpeg-capture/
```
and cd to that directory before I start any recordings.
**To quit the ffmpeg window use keys <q> or <Ctrl+z>**
I'll go a bit overkill as well, recording my camera along with screen, but I warn you will get a small window that pops up.
open a terminal window and enter the following:
```
ffplay -f video4linux2 -i /dev/video0 -video_size 320x240 -fflags nobuffer
```
Be careful not to increase resolution than the device can handle or things will break.

While the first terminal is open, your webcam will be displayed on the desktop. (I know you asked for NO GUI's)
Now open a second terminal to start the recording:
```
cd ~/Videos/ffmpeg-capture/

ffmpeg -f x11grab -r 60 -s cif -i :0.0 capture.mp4
```
As long as these two terminal windows are open, you&#8217;ll be recording the desktop at 60 FPS, and displaying a webcam.

---

### Post by &amp;KyT$0P# on 2022-07-11
> **Skaperen said:**
> if it actually works for you, can you post your exact command line arguments and options 

Sure, try this -
```
ffmpeg -framerate 60 -f x11grab -video_size [COLOR="#FF0000"]WIDTH[/COLOR]x[COLOR="#FF0000"]HEIGHT[/COLOR] -i "${DISPLAY}+0,0" -an ./test.mkv
```
Replace [COLOR="#FF0000"]WIDTH[/COLOR] and [COLOR="#FF0000"]HEIGHT[/COLOR] with the actual numbers for your screen resolution.

> and what signal makes it correctly end? 

Either pressing q or Ctrl-C/SIGINT

---

### Post by Skaperen on 2022-07-12
> **1fallen said:**
> The line I use most often is:
```
ffmpeg -f x11grab -y -r 60 -s 1920x1080 -i :0.0 -vcodec huffyuv out.avi

```

i got this error message:
```

[x11grab @ 0x55e9333ad700] Stream #0: not enough frames to estimate rate; consider increasing probesize

```
:-({|=

but it still recorded a working video.  i stopped it and tried to play it with *mplayer* and got all the same text output, or so i thought.  it was just playing the video that had the text recorded in it.  as soon as i saw the cursor move, then i realized that it had worked.:redface:

so now i'll put that in a script with a few seconds delay so i can switch to the desired workspace (i keep terminals in their own workspaces so i can have them large even with large fonts).:cool:

then i'll play around converting them to *webm* format (*vp9* seems to be much better compression).\\:D/

thank you for working details):P

---

### Post by Skaperen on 2022-07-12
> **halogen2 said:**
> Sure, try this -
```
ffmpeg -framerate 60 -f x11grab -video_size [COLOR=#FF0000]WIDTH[/COLOR]x[COLOR=#FF0000]HEIGHT[/COLOR] -i "${DISPLAY}+0,0" -an ./test.mkv
```
Replace [COLOR=#FF0000]WIDTH[/COLOR] and [COLOR=#FF0000]HEIGHT[/COLOR] with the actual numbers for your screen resolution.



Either pressing q or Ctrl-C/SIGINT

this works for me, too.  played a recording back.  well, i only tried 'q' to quit.

---

### Post by #&amp;thj^% on 2022-07-14
> **Skaperen said:**
> i got this error message:

How odd, on debian-rolling I get:
```
Stream #0:0: Video: rawvideo (BGR[0] / 0x524742), bgr0, 1920x1080, 3981312 kb/s, 60 fps, 1000k tbr, 1000k tbn
Stream mapping:
  Stream #0:0 -> #0:0 (rawvideo (native) -> huffyuv (native))
Press [q] to stop, [?] for help
[huffyuv @ 0x5642d2c57d00] using huffyuv 2.2.0 or newer interlacing flag
[huffyuv @ 0x5642d2c60e40] using huffyuv 2.2.0 or newer interlacing flag
[huffyuv @ 0x5642d2c58b00] using huffyuv 2.2.0 or newer interlacing flag
[huffyuv @ 0x5642d2c598c0] using huffyuv 2.2.0 or newer interlacing flag
[huffyuv @ 0x5642d2c6c500] using huffyuv 2.2.0 or newer interlacing flag
[huffyuv @ 0x5642d2c7e380] using huffyuv 2.2.0 or newer interlacing flag
[huffyuv @ 0x5642d2c84900] using huffyuv 2.2.0 or newer interlacing flag
[huffyuv @ 0x5642d2c8b200] using huffyuv 2.2.0 or newer interlacing flag
[huffyuv @ 0x5642d2c91b80] using huffyuv 2.2.0 or newer interlacing flag
[huffyuv @ 0x5642d2c98600] using huffyuv 2.2.0 or newer interlacing flag
[huffyuv @ 0x5642d2c9f080] using huffyuv 2.2.0 or newer interlacing flag
[huffyuv @ 0x5642d2ca5b00] using huffyuv 2.2.0 or newer interlacing flag
[huffyuv @ 0x5642d2a52e80] using huffyuv 2.2.0 or newer interlacing flag
Output #0, avi, to 'out.avi':
  Metadata:
    ISFT            : Lavf59.16.100


```
But I'm happy to hear you have a good solution. :)

---

### Post by Skaperen on 2022-07-14
i see messages like that, too.  but i do get a recording though it is not very well compressed, if at all.  the recording does play.

now, i'd like to get sound added.  i'd like to be able to choose between a microphone (maybe a specific one if i get another) and whatever sound is playing on the speakers (without having to shut up and pick up speaker sound on the microphone, since it is often noisy around here, cats barking, fish squealing. squirrels chattering, etc.)  being able to mix (with headphones replacing speakers) would be a plus.

i need to see what better compression i can get at record time.  i don't think i have the CPU power for webm (vp9).  so webm will be post processing.

---

### Post by #&amp;thj^% on 2022-07-14
Try this one, it has no sound, but check if compression and quality is good enough.
```
ffmpeg -video_size 1920x1080 -framerate 30 -f x11grab -i :0.0 -c:v libx264rgb -crf 0 -preset ultrafast -color_range 2 output.mkv
```

---

