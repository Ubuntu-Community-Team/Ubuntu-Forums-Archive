---
title: "3 webcams in guvcview SOLVED"
date: 2022-07-12
forum: General Help
---

### Post by tampepper on 2022-07-12
I can manually add cameras to guvcview by adding a new window
Guvcview displays my three connected webcams perfectly
However, is there anyway I can save the settings allowing guvcview to start with the three cameras next time its started.
I tried saving the profile but this just saves the one camera.
Any help appreciated

---

### Post by mIk3_08 on 2022-07-12
> **tampepper said:**
> I can manually add cameras to guvcview by adding a new window
Guvcview displays my three connected webcams perfectly
However, is there anyway I can save the settings allowing guvcview to start with the three cameras next time its started.
I tried saving the profile but this just saves the one camera.
Any help appreciated
Please run the command below and post the result here in this thread. Regards and cheers.
```
hostnamectl status
```

---

### Post by tampepper on 2022-07-12
Static hostname: DarthVader
       Icon name: computer-desktop
         Chassis: desktop
      Machine ID: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
         Boot ID: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
Operating System: Ubuntu 22.04 LTS
          Kernel: Linux 5.15.0-41-generic
    Architecture: x86-64
 Hardware Vendor: Gigabyte Technology Co., Ltd.
  Hardware Model: B550 AORUS PRO AC

---

### Post by #&amp;thj^% on 2022-07-12
It's been awhile since i have had need for this, but my memory is bit fuzzy.
I had Two cameras working with:
```
guvcview --device=/dev/video0 --format=mjpeg -x=640x480 && guvcview --device=/dev/video1 --format=mjpeg -x=640x480
```
You'll need to adjust my code to suit your wants and devices.

---

### Post by tampepper on 2022-07-12
Thanks for that.
Unfortunately it opens one camera at a time ie video0 opens, when I close it, video2 opens.
My cameras are 0, 2 and 4 but I am just trying two to start with.
The command that works is 
guvcview --device=/dev/video0 --format=mjpeg --resolution=1920x1080 && guvcview --device=/dev/video2 --format=mjpeg --resolution=1920x1080
Using the GUI It opens with video0 and I add new windows for video 2 and video 4.
It runs the 3 camera well but as I say, I would like to start it with 3 cameras active

---

### Post by #&amp;thj^% on 2022-07-12
The best I have had work is 2 cameras out of 5, I believe there other programs that work better, but I flat lost interest.
can you show this please:
```
v4l2-ctl -d /dev/video0 --list-formats-ext
```
and:
```
v4l2-ctl --list-devices
```
I'm going to play with ffmpeg, to see if i can help
EDIT: It might work at first look:
```
[video4linux2,v4l2 @ 0x55e5279021c0] Compressed:       mjpeg :          Motion-JPEG : 1280x720 320x180 320x240 352x288 424x240 640x360 640x480 848x480 960x540
[video4linux2,v4l2 @ 0x55e5279021c0] Raw       :     yuyv422 :           YUYV 4:2:2 : 1280x720 320x180 320x240 352x288 424x240 640x360 640x480 848x480 960x540

```
To see what the command was:
```
ffmpeg -f v4l2 -list_formats all -i /dev/video0
```

---

### Post by tampepper on 2022-07-12
Much appreciated, thanks
UVC Camera: UVC Camera (usb-0000:01:00.0-3.1.4):
    /dev/video2
    /dev/video3
    /dev/media1

USB 2.0 Camera: S200C (usb-0000:01:00.0-3.3.4.4):
    /dev/video4
    /dev/video5
    /dev/media2

GENERAL WEBCAM: GENERAL WEBCAM (usb-0000:0a:00.3-1.1):
    /dev/video0
    /dev/video1
    /dev/media0

ioctl: VIDIOC_ENUM_FMT
    Type: Video Capture

    [0]: 'MJPG' (Motion-JPEG, compressed)
        Size: Discrete 1920x1080
            Interval: Discrete 0.033s (30.000 fps)
            Interval: Discrete 0.033s (30.000 fps)
        Size: Discrete 2560x1440
            Interval: Discrete 0.033s (30.000 fps)
        Size: Discrete 1280x720
            Interval: Discrete 0.033s (30.000 fps)
        Size: Discrete 800x480
            Interval: Discrete 0.033s (30.000 fps)
        Size: Discrete 640x480
            Interval: Discrete 0.033s (30.000 fps)
        Size: Discrete 320x240
            Interval: Discrete 0.033s (30.000 fps)
        Size: Discrete 640x360
            Interval: Discrete 0.033s (30.000 fps)
        Size: Discrete 800x600
            Interval: Discrete 0.033s (30.000 fps)
        Size: Discrete 1920x1080
            Interval: Discrete 0.033s (30.000 fps)
            Interval: Discrete 0.033s (30.000 fps)
    [1]: 'YUYV' (YUYV 4:2:2)
        Size: Discrete 1280x720
            Interval: Discrete 0.033s (30.000 fps)
            Interval: Discrete 0.033s (30.000 fps)
        Size: Discrete 800x480
            Interval: Discrete 0.033s (30.000 fps)
        Size: Discrete 640x480
            Interval: Discrete 0.033s (30.000 fps)
        Size: Discrete 320x240
            Interval: Discrete 0.033s (30.000 fps)
        Size: Discrete 640x360
            Interval: Discrete 0.033s (30.000 fps)
        Size: Discrete 800x600
            Interval: Discrete 0.033s (30.000 fps)
        Size: Discrete 1280x720
            Interval: Discrete 0.033s (30.000 fps)
            Interval: Discrete 0.033s (30.000 fps)
    [2]: 'H264' (H.264, compressed)
        Size: Discrete 1920x1080
            Interval: Discrete 0.033s (30.000 fps)
            Interval: Discrete 0.033s (30.000 fps)
        Size: Discrete 1280x720
            Interval: Discrete 0.033s (30.000 fps)
        Size: Discrete 800x480
            Interval: Discrete 0.033s (30.000 fps)
        Size: Discrete 640x480
            Interval: Discrete 0.033s (30.000 fps)
        Size: Discrete 320x240
            Interval: Discrete 0.033s (30.000 fps)
        Size: Discrete 640x360
            Interval: Discrete 0.033s (30.000 fps)
        Size: Discrete 800x600
            Interval: Discrete 0.033s (30.000 fps)
        Size: Discrete 1920x1080
            Interval: Discrete 0.033s (30.000 fps)
            Interval: Discrete 0.033s (30.000 fps)

---

### Post by #&amp;thj^% on 2022-07-12
Try this please, it's just for 1 camera for now,.... and hows the quality?
```
ffmpeg -f v4l2 -i /dev/video0 -map 0 -c:v libx264 -f tee "output.mp4|[f=nut]pipe:" | ffplay pipe:
```

---

### Post by tampepper on 2022-07-12
That works and its good quality

---

### Post by tampepper on 2022-07-13
I incorporated this into a python script and run it using startup applications.
I works, so I now call 3 separate python scripts from startup application, and the 3 cameras work perfectly.
Rough and ready but it works.
I would be interested if someone could polish this up a bit

---

### Post by tampepper on 2022-07-13
I can of course do the same by substituting the guvcview command
#!/usr/bin/python3
import os
cmd='guvcview --device=/dev/video0 --format=mjpeg --resolution=1920x1080'
os.system(cmd)

---

### Post by #&amp;thj^% on 2022-07-13
> **tampepper said:**
> I incorporated this into a python script and run it using startup applications.
I works, so I now call 3 separate python scripts from startup application, and the 3 cameras work perfectly.
Rough and ready but it works.
**I would be interested if someone could polish this up a bit**

Good work, I had some work related things come up yesterday, so I had to drop everything and put out a couple of fires.
As far as polishing this up, what would you need?
Remember hardware capabilities  and software capabilities come in to play here as well.
Would you be kind enough to show your script/s, maybe we can enhance them. (No promises though)

---

### Post by tampepper on 2022-07-13
I have 3 python scripts. Cam1 Cam2 and Cam3. in a folder. Each opens 1 of 3 cameras.

#!/usr/bin/python3
import os
cmd='guvcview --device=/dev/video0 --format=mjpeg --resolution=1920x1080'
os.system(cmd)

So when ubuntu boots, the "Startup Applications" app runs each in turn
I chose the guvcview cmdline instead of the fmpeg line, as the guvcview is  easy to change the resolution if I want
I really appreciate your help and am happy to go with this procedure.

---

