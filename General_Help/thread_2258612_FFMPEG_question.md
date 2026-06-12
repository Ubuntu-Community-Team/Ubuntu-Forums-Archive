---
title: "FFMPEG question"
date: 2014-12-29
forum: General Help
---

### Post by asai on 2014-12-29
Hi,

I have written a small script to take snapshots from a webcamera.
The snapshots from a hole day are then used to make a timelapse movie.

Hopefully there is someone here that can help me with a small issue with my script.
The problem is that sometimes during the day the snapshot get fuzzy. This results in a flickering movie.

ffmpeg command:
```
ffmpeg -i rtsp://192.168.1.65:554/live.sdp -y -f image2 -t 5 /media/shared/snapshots/nordvest.jpg
```

ffmpeg command for timelapse movie:
```
ffmpeg -r 6 -qscale 2  -i /media/shared/converted/%05d.jpg /media/shared/$DATE.mp4
```

Here is an example of a snapshot with error:
[Snapshot]("http://81.166.3.217/download/nordvest.jpg")

The command for movie is OK, but the one for snapshots is not.
Does anyone have an idea what could br wrong?

---

### Post by hal8000b on 2014-12-29
> **asai said:**
> Hi,

I have written a small script to take snapshots from a webcamera.
The snapshots from a hole day are then used to make a timelapse movie.

Hopefully there is someone here that can help me with a small issue with my script.
The problem is that [COLOR=#ff0000]sometimes[/COLOR] during the day the snapshot get fuzzy. This results in a flickering movie.

ffmpeg command:
```
ffmpeg -i rtsp://192.168.1.65:554/live.sdp -y -f image2 -t 5 /media/shared/snapshots/nordvest.jpg
```

ffmpeg command for timelapse movie:
```
ffmpeg -r 6 -qscale 2  -i /media/shared/converted/%05d.jpg /media/shared/$DATE.mp4
```

Here is an example of a snapshot with error:
[Snapshot]("http://81.166.3.217/download/nordvest.jpg")

The command for movie is OK, but the one for snapshots is not.
Does anyone have an idea what could br wrong?


Can you define "sometimes" ?
is the web camera mounted indoors or outdoors?
The lower half of the image looks distorted, the kind of distortion when a camera is not held steady.
As the script works, I would say the problem is physical (movement, vibration, etc) and not software.
hope that helps.

---

### Post by Holger_Gehrke on 2014-12-29
Are my eyes going bad or is the lowest quarter of the image just the same line of pixel repeated again and again ? If that's the case and it's the problem you mean, a 'bad' file should be **a lot** smaller than a good one. Have your script check the file's size and retake the picture if it's too small to be good.

---

### Post by FakeOutdoorsman on 2014-12-29
> **asai said:**
> ```
ffmpeg -i rtsp://192.168.1.65:554/live.sdp -y -f image2 -t 5 /media/shared/snapshots/nordvest.jpg
```
Please include the complete ffmpeg console output from this command.
 
> **asai said:**
> ```
ffmpeg -r 6 -qscale 2  -i /media/shared/converted/%05d.jpg /media/shared/$DATE.mp4
```
-qscale 2 should be an output option, not an input option. However, if your default encoder for MP4 is libx264 then it will get ignored anyway and the default of -crf 23 will be used instead. See [FFmpeg H.264 Video Encoding Guide](https://trac.ffmpeg.org/wiki/Encode/H.264).

 > **asai said:**
> Here is an example of a snapshot with error:
[Snapshot]("http://81.166.3.217/download/nordvest.jpg")
Try playing the input with ffplay or VLC. Does it show the same issue?
```
ffplay -i rtsp://192.168.1.65:554/live.sdp
```

---

### Post by asai on 2014-12-30
Hi,

Thanks for replys.
I have searched round a bit and I found that this URL:
```
http://192.168.1.65/cgi-bin/viewer/video.jpg?streamid=0
```
Gets a snapshot from the cameras own software.
Is there a command to save this snapshot?

---

### Post by asai on 2014-12-30
Problem solved!

```
wget -P /media/shared "http://192.168.1.65/cgi-bin/viewer/video.jpg
```

Very nice picture.
Can be viewed here:
[Northwest]("http://www.veret-aalgaard.com/nordvest.jpg")

---

### Post by sitmex on 2015-01-24
Where can I see the script to make the pictures from? I'm trying to do the same, for a Home project.

---

### Post by asai on 2015-01-25
I have done it like this:
```

#!/bin/sh
export DATETIME=`date +%d%m%Y%H%M`

wget -P /media/shared "http://192.168.1.65/cgi-bin/viewer/video.jpg"

cp /media/shared/video.jpg /media/shared/snapshots/$DATETIME.jpg

```

This depends on the webcam to be able to take snapshots, I am not using ffmpeg.

---

