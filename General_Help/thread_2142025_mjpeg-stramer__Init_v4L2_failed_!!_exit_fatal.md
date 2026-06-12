---
title: "mjpeg-stramer  Init v4L2 failed !! exit fatal"
date: 2013-05-04
forum: General Help
---

### Post by iconso on 2013-05-04
Hi everybody, 
I-m trying to stream a webcam with mjpg-streamer and ubuntu 12.04 with this command:
```
/mjpg-streamer/mjpg-streamer$ ./mjpg_streamer -i "./input_uvc.so -f 15 -r 640x480" -o "./output_http.so -w ./www"

```

This is my output:
```
MJPG Streamer Version: svn rev: 3:172
 i: Using V4L2 device.: /dev/video0
 i: Desired Resolution: 640 x 480
 i: Frames Per Second.: 15
 i: Format............: MJPEG
Unable to set format: 1196444237 res: 640x480
 Init v4L2 failed !! exit fatal 
 i: init_VideoIn failed


```
Do you have any idea or suggestion to solve this problem?

Thanks for help, 
Nicco.

---

