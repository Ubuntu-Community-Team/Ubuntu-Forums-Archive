---
title: "canera/guvcview problems"
date: 2019-08-30
forum: General Help
---

### Post by jgw on 2019-08-30
I am having a problem with my usb camera (Logitech, Inc. Webcam Pro 9000) and Guvcview version 2.0.6.   With my camera pointed at me I run guvcview.  I can see myself but I am frozen.  I then go into video settings and change the video control resolution to something else and I get movement.  I can then return to the original frozen resolution and things are still fine.  Its all strange.  I never used to have a problem and now I do.  I have no idea what I might have done to screw things up.  The only thing I actually use this camera for is when running google hangouts which is also screwed up now.  

Here is what I get when I start guvcview (I have deleted a lot of duplicate lines):
```

greg@gregdown:~$ sudo guvcview -d /dev/video0
[sudo] password for greg: 
GUVCVIEW: version 2.0.6
V4L2_CORE: (UVCIOC_CTRL_MAP) Error: No such file or directory
V4L2_CORE: (UVCIOC_CTRL_MAP) Error: No such file or directory
V4L2_CORE: (UVCIOC_CTRL_MAP) Error: No such file or directory
V4L2_CORE: (UVCIOC_CTRL_MAP) Error: No such file or directory
V4L2_CORE: (UVCIOC_CTRL_MAP) Error: File exists
V4L2_CORE: (UVCIOC_CTRL_MAP) Error: File exists
V4L2_CORE: (UVCIOC_CTRL_MAP) Error: File exists
V4L2_CORE: (UVCIOC_CTRL_MAP) Error: File exists
V4L2_CORE: (UVCIOC_CTRL_MAP) Error: File exists
Home directory not accessible: Permission denied
ALSA lib pcm_dmix.c:1052:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm.c:2495:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear
ALSA lib pcm.c:2495:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
ALSA lib pcm.c:2495:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
ALSA lib pcm_route.c:867:(find_matching_chmap) Found no matching channel map
Home directory not accessible: Permission denied
ALSA lib pulse.c:243:(pulse_connect) PulseAudio: Unable to connect: Connection refused

Home directory not accessible: Permission denied
ALSA lib pulse.c:243:(pulse_connect) PulseAudio: Unable to connect: Connection refused

ALSA lib pcm_dmix.c:1052:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1052:(snd_pcm_dmix_open) unable to open slave
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
V4L2_CORE: Could not grab image (select timeout): Resource temporarily unavailable
V4L2_CORE: ioctl (-1067952623) retried 4 times - giving up: Resource temporarily unavailable)
V4L2_CORE: (VIDIOC_DQBUF) Unable to dequeue buffer: Resource temporarily unavailable
V4L2_CORE: ioctl (-1067952623) retried 4 times - giving up: Resource temporarily unavailable)
V4L2_CORE: (VIDIOC_DQBUF) Unable to dequeue buffer: Resource temporarily unavailable
GUVCVIEW: error setting spin value
V4L2_CORE: ioctl (-1067952623) retried 4 times - giving up: Resource temporarily unavailable)
V4L2_CORE: (VIDIOC_DQBUF) Unable to dequeue buffer: Resource temporarily unavailable
V4L2_CORE: ioctl (-1067952623) retried 4 times - giving up: Resource temporarily unavailable)
V4L2_CORE: (VIDIOC_DQBUF) Unable to dequeue buffer: Resource temporarily unavailable
V4L2_CORE: ioctl (-1067952623) retried 4 times - giving up: Resource temporarily unavailable)
V4L2_CORE: (VIDIOC_DQBUF) Unable to dequeue buffer: Resource temporarily unavailable
V4L2_CORE: ioctl (-1067952623) retried 4 times - giving up: Resource temporarily unavailable)
V4L2_CORE: (VIDIOC_DQBUF) Unable to dequeue buffer: Resource temporarily unavailable
GUVCVIEW: error setting spin value
V4L2_CORE: ioctl (-1067952623) retried 4 times - giving up: Resource temporarily unavailable)
V4L2_CORE: (VIDIOC_DQBUF) Unable to dequeue buffer: Resource temporarily unavailable
V4L2_CORE: ioctl (-1067952623) retried 4 times - giving up: Resource temporarily unavailable)
V4L2_CORE: (VIDIOC_DQBUF) Unable to dequeue buffer: Resource temporarily unavailable
V4L2_CORE: ioctl (-1067952623) retried 4 times - giving up: Resource temporarily unavailable)
V4L2_CORE: (VIDIOC_DQBUF) Unable to dequeue buffer: Resource temporarily unavailable
V4L2_CORE: ioctl (-1067952623) retried 4 times - giving up: Resource temporarily unavailable)
V4L2_CORE: (VIDIOC_DQBUF) Unable to dequeue buffer: Resource temporarily unavailable
greg@gregdown:~$ 

```

I also created a guvcview profile:
```
#V4L2/CTRL/0.0.2
APP{"guvcview 2.0.6"}
# control data
#Brightness
ID{0x00980900};CHK{0:255:1:128}=VAL{128}
#Contrast
ID{0x00980901};CHK{0:255:1:32}=VAL{32}
#Saturation
ID{0x00980902};CHK{0:255:1:28}=VAL{28}
#White Balance Temperature, Auto
ID{0x0098090c};CHK{0:1:1:1}=VAL{1}
#Gain
ID{0x00980913};CHK{0:255:1:0}=VAL{82}
#Power Line Frequency
ID{0x00980918};CHK{0:2:1:2}=VAL{2}
#White Balance Temperature
ID{0x0098091a};CHK{0:10000:10:4000}=VAL{3070}
#Sharpness
ID{0x0098091b};CHK{0:255:1:191}=VAL{191}
#Backlight Compensation
ID{0x0098091c};CHK{0:1:1:1}=VAL{1}
#Exposure, Auto
ID{0x009a0901};CHK{0:3:1:3}=VAL{3}
#Exposure (Absolute)
ID{0x009a0902};CHK{1:10000:1:166}=VAL{305}
#Exposure, Auto Priority
ID{0x009a0903};CHK{0:1:1:0}=VAL{0}
#Pan (Absolute)
ID{0x009a0908};CHK{-36000:36000:3600:0}=VAL{0}
#Tilt (Absolute)
ID{0x009a0909};CHK{-36000:36000:3600:0}=VAL{0}
#Focus
ID{0x009a090a};CHK{0:255:1:0}=VAL{0}
#LED1 Mode
ID{0x0a046d05};CHK{0:3:1:3}=VAL{3}
#LED1 Frequency
ID{0x0a046d06};CHK{0:255:1:0}=VAL{0}
#Disable video processing
ID{0x0a046d71};CHK{0:1:1:0}=VAL{0}
#Raw bits per pixel
ID{0x0a046d72};CHK{0:1:1:0}=VAL{0}
```

Here is my camera:
```

greg@gregdown:~$ v4l2-ctl --list-devices
UVC Camera (046d:0809) (usb-0000:00:12.0-3.2):
	/dev/video0
	/dev/video1
greg@gregdown:~$ lsusb -s 003:005
Bus 003 Device 005: ID 046d:0809 Logitech, Inc. Webcam Pro 9000
greg@gregdown:~$ ls -ltrh /dev/video*
crw-rw----+ 1 root video 81, 1 Aug 28 09:16 /dev/video1
crw-rw----+ 1 root video 81, 0 Aug 28 09:16 /dev/video0

```

Any thoughts would be appreciated - thank you....................

---

### Post by jgw on 2019-09-28
guess there are no answers on this one  so I will mark it solved................................

---

### Post by coffeecat on 2019-09-28
Please do not mark a thread as solved if it is not solved. That is a disservice and a discourtesy to people searching for answers, who would be misled into coming to a thread wrongly marked solved.

There is a gap of over 4 weeks between your first post in this thread and your latest. Not once in that time did you bump the thread. It is unreasonable therefore to assume that there are no answers. Perhaps no one here can help, but it is wrong to assume that is the case if you do not bump the thread occasionally. 

I will remove your solved tag as soon as I have posted.

---

### Post by jgw on 2019-09-28
How odd, I am not trying to get into anything here.  Its odd because I have been told, more than once, that when a folder is done, replies or not, to mark it as solved.  I have, over the years, tried to get another options (something like "unsolved but old" would do it).  I have bumped before with no luck.  I can do that and see what happens but, in the end .......................

---

### Post by jgw on 2019-09-28
bump

---

