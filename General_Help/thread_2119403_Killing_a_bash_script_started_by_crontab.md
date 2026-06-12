---
title: "Killing a bash script started by crontab"
date: 2013-02-23
forum: General Help
---

### Post by timsdeepsky on 2013-02-23
Hi....
I am not understanding something....I run this cronjob ```
0 17 * * * /home/tim/bin/sunsetscript.sh

```....This runs a bash script with this code ```
#!/bin/bash
/usr/local/bin/ffmpeg -r 25 -f video4linux2 -s 640x480 -i /dev/video2 -qscale 3 /home/tim/bin/sunset_cron.mpeg
```....This code grabs and records a video feed from my sunset cam at /dev/video/2,,and writes it to my hard drive....I have to manually kill the script after 3 hours by putting this in terminal```
 ps -ef | grep cron
```,,and then ```
sudo kill (cron#)
```....I am trying to automate stopping the script after 3 hours,,but i am only more confused now....Parent/child in cron,,Grep in a bash script to kill it,,pkill-process....I basically need to start my bash script and then kill it 3 hours later....Can anyone point me to a webpage that i can more easily understand this,,or help me understand the parent/child procedure in cron??....Thanks for any info....

---

### Post by schragge on 2013-02-23
```
#!/bin/bash
/usr/local/bin/ffmpeg \
  -r 25 -f video4linux2 -s 640x480 -i /dev/video2 \
  -qscale 3 /home/tim/bin/sunset_cron.mpeg[COLOR=red]&
sleep 3h
kill %
exit 0[/COLOR]

``` Besides, there's a special command for it in GNU coreutils: [timeout](http://manpages.ubuntu.com/manpages/precise/en/man1/timeout.1.html).

---

### Post by timsdeepsky on 2013-02-23
Thanks schragge,,
I am going to test it now....
I will let you know how it goes shortly....
Thanks again....

---

### Post by timsdeepsky on 2013-02-24
schragge,,,,
This worked perfect for me....Somehow i missed the forest for the trees....My first cronjob launches the bash script and ffmpeg catches 3 hours of the west sky and now auto stops....Then my second cronjob launches my second bash script and ffmpeg encodes the video for the web....Thanks for your help....I am marking this solved....

---

### Post by FakeOutdoorsman on 2013-02-25
Another method is to add "-t 03:00:00" as an output option for ffmpeg to get an exact 3 hour video duration. ffmpeg will then quit when it is done recording.

---

### Post by timsdeepsky on 2013-02-25
Where would be the best place to put the ```
-t 03:00:00
```..??..Like so..??..```
#!/bin/bash
/usr/local/bin/ffmpeg \
  -r 25 -f video4linux2 -t 03:00:00 -s 640x480 -i /dev/video2 \
  -qscale 3 /home/tim/bin/sunset_cron.mpeg
```....FakeOutdoorsman,,my quality is poor and i think i might get better quality if i copy from my video feed instead of encoding and then saving it using -vcodec copy,,and then encoding it for the web....Of course i guess this would be no different than capturing and then encoding on the fly i suppose....I am trying to find "holy grail" good quality-small size formula now....I am capturing at 320 by 240 now because the 640 by 480 size gets too huge for me....Can i copy the frames straight from my camera with the same quality as they are,,and then use my mp4 code on the video..??..```
ffmpeg -i /home/tim/bin/video.mpeg -acodec libfaac -aq 100 -vcodec libx264 -preset slow -crf 28 /home/tim/bin/video_mpeg_x264_code.mp4;qt-faststart /home/tim/bin/video_mpeg_x264_code.mp4 /home/tim/bin/video_mpeg_x264_code_mp4_qtfaststart.mp4
```....Thanks for your help....

---

### Post by FakeOutdoorsman on 2013-02-25
> **timsdeepsky said:**
> Where would be the best place to put the ```
-t 03:00:00
```..??..Like so..??..```
#!/bin/bash
/usr/local/bin/ffmpeg \
  -r 25 -f video4linux2 -t 03:00:00 -s 640x480 -i /dev/video2 \
  -qscale 3 /home/tim/bin/sunset_cron.mpeg
```
You're applying the option to the input. [Option placement](http://ffmpeg.org/ffmpeg.html#Synopsis) matters, and options before "-i" are applied to the input (usually the decoder), and options before the output are applied to the output (usually the encoder).

```
ffmpeg (global options) [input options] -i input [output options] output
```

> **timsdeepsky said:**
> my quality is poor and i think i might get better quality if i copy from my video feed instead of encoding and then saving it using -vcodec copy,,and then encoding it for the web....

Of course i guess this would be no different than capturing and then encoding on the fly i suppose

I recommend trying the "on-the-fly" method first:

```
ffmpeg -framerate 25 -f video4linux2 -video_size 640x480 -i /dev/video2 -t 03:00:00 -vcodec libx264 -preset slow -crf 28 -movflags faststart -acodec libfaac -aq 100 output.mp4
```

I changed -r to -framerate, and -s to -video_size. Probably makes no difference, but there are V4L2 private options (options that are specific to the V4L2 input device). I added "-movflags faststart" which does the same thing as qt-faststart (moves some info to the beginning of the file so it can begin playback before it is completely downloaded by the viewer).

If your computer can handle it then that's one less step and one less temporary file to deal with. If it can not then you can try using "-codec copy", and then re-encoding that for the web.

See the [FFmpeg and x264 Encoding Guide](https://ffmpeg.org/trac/ffmpeg/wiki/x264EncodingGuide) for more info on how to get a specific quality level...although it looks like you basically already did that.

---

### Post by timsdeepsky on 2013-02-25
Thanks for all the help....This is working perfect for me....This gave me better quality than i was getting before by far....```
ffmpeg -framerate 25 -f video4linux2 -video_size 640x480 -i /dev/video2 -t 03:00:00 -vcodec libx264 -preset slow -crf 28 -movflags faststart -acodec libfaac -aq 100 output.mp4
```....Thanks again FakeOutdoorsman and schragge for all the help....

---

