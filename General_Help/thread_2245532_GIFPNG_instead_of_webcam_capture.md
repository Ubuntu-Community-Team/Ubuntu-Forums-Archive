---
title: "GIF/PNG instead of webcam capture"
date: 2014-09-24
forum: General Help
---

### Post by 700 on 2014-09-24
What could I do to show *.gif or *.png files instead of my webcam capture on Ubuntu?

Webcam Studio is not working well on my machine and there are no effects like that available on Cheese.

---

### Post by SeijiSensei on 2014-09-24
Do you want to take a video file and convert the frames to a series of still images?  You can do that from the command line with mplayer using the command:
```
mplayer -ao null -vo png /path/to/video/file
```
That will convert all the frames to PNG.  If you're interested in just a segment of the video, you can add the "-ss hh:mm:ss" parameter to specify a start time and the "-endpos n" parameter to specify the duration of the segment to be captured.

---

### Post by 700 on 2014-09-25
> Do you want to take a video file and convert the frames to a series of still images?

No. I want to stream *.gif (*.png, *.avi or any other image source) instead of my webcam capture.

---

