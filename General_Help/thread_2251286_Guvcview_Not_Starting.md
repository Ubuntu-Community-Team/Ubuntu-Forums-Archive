---
title: "Guvcview Not Starting"
date: 2014-11-03
forum: General Help
---

### Post by echotech2 on 2014-11-03
Updated on-line from 14.04.x to 14.10.  In 14.04.x Guvcview worked fine. With 14.10 starting guvcview from the dash nothing happens, no display, no crash report.  Cheese works OK.  From the terminal I get a some Unable to open...., Connection refused..., ending in "segmentation fault (core dumped)"

```
~$ guvcview
guvcview 1.7.3
file guvcview_video.mkv has extension type 1
file guvcview_image.jpg has extension type 0
unexpected integer value (8388608) for stack_size
Strings must be quoted
unexpected integer value (0) for spinbehave
Strings must be quoted
file guvcview_image.jpg has extension type 0
Video file suffix detected: 0
Image file suffix detected: 0
ALSA lib pcm_dmix.c:1022:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear
ALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
ALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
ALSA lib pcm_route.c:947:(find_matching_chmap) Found no matching channel map
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
ALSA lib pcm_dmix.c:1022:(snd_pcm_dmix_open) unable to open slave
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
video device: /dev/video0 
vid:046d 
pid:0990 
driver:uvcvideo
device doesn't seem to support uvc H264 (0)
mapping control for Pan (relative)
UVCIOC_CTRL_MAP - Error: No such file or directory
mapping control for Tilt (relative)
UVCIOC_CTRL_MAP - Error: No such file or directory
mapping control for Pan Reset
UVCIOC_CTRL_MAP - Error: No such file or directory
mapping control for Tilt Reset
UVCIOC_CTRL_MAP - Error: No such file or directory
mapping control for Focus (absolute)
mapping control for LED1 Mode
UVCIOC_CTRL_MAP - Error: File exists
mapping control for LED1 Frequency
UVCIOC_CTRL_MAP - Error: File exists
mapping control for Disable video processing
UVCIOC_CTRL_MAP - Error: File exists
mapping control for Raw bits per pixel
UVCIOC_CTRL_MAP - Error: File exists
Init. UVC Camera (046d:0990) (location: usb-0000:00:1a.7-6)
{ pixelformat = 'MJPG', description = 'MJPEG' }
{ discrete: width = 160, height = 120 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 176, height = 144 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 320, height = 240 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 352, height = 288 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 640, height = 480 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 800, height = 600 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 960, height = 720 }
	Time interval between frame: 1/15, 1/10, 1/5, 
{ pixelformat = 'YUYV', description = 'YUV 4:2:2 (YUYV)' }
{ discrete: width = 160, height = 120 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 176, height = 144 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 320, height = 240 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 352, height = 288 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 640, height = 480 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 800, height = 600 }
	Time interval between frame: 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 960, height = 720 }
	Time interval between frame: 1/10, 1/5, 
{ discrete: width = 1600, height = 1200 }
	Time interval between frame: 1/5, 
{ pixelformat = 'RGB3', description = 'RGB3' }
{ discrete: width = 160, height = 120 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 176, height = 144 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 320, height = 240 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 352, height = 288 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 640, height = 480 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 800, height = 600 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 960, height = 720 }
	Time interval between frame: 1/15, 1/10, 1/5, 
{ discrete: width = 1600, height = 1200 }
	Time interval between frame: 1/5, 
{ pixelformat = 'BGR3', description = 'BGR3' }
{ discrete: width = 160, height = 120 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 176, height = 144 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 320, height = 240 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 352, height = 288 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 640, height = 480 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 800, height = 600 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 960, height = 720 }
	Time interval between frame: 1/15, 1/10, 1/5, 
{ discrete: width = 1600, height = 1200 }
	Time interval between frame: 1/5, 
{ pixelformat = 'YU12', description = 'YU12' }
{ discrete: width = 160, height = 120 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 176, height = 144 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 320, height = 240 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 352, height = 288 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 640, height = 480 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 800, height = 600 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 960, height = 720 }
	Time interval between frame: 1/15, 1/10, 1/5, 
{ discrete: width = 1600, height = 1200 }
	Time interval between frame: 1/5, 
{ pixelformat = 'YV12', description = 'YV12' }
{ discrete: width = 160, height = 120 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 176, height = 144 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 320, height = 240 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 352, height = 288 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 640, height = 480 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 800, height = 600 }
	Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 960, height = 720 }
	Time interval between frame: 1/15, 1/10, 1/5, 
{ discrete: width = 1600, height = 1200 }
	Time interval between frame: 1/5, 
checking muxed H264 format support
device doesn't seem to support uvc H264 (0)
checking format: MJPG
VIDIOC_G_COMP:: Inappropriate ioctl for device
fps is set to 1/30
drawing controls

Segmentation fault (core dumped)
```

---

### Post by vasa1 on 2014-11-04
You aren't alone.

[https://plus.google.com/u/0/108297487499542256860/posts/c1afg7Anoh8](https://plus.google.com/u/0/108297487499542256860/posts/c1afg7Anoh8)

---

### Post by echotech2 on 2014-11-04
Thanks for the info, vasa1.

---

### Post by clepsdyrae on 2014-11-04
Just stumbled upon this with my new webcam, and it looks like I'm not alone either. Logitech C615.

Exact same behavior. Camera works fine in skype.

```
$ guvcview --verbose
guvcview 1.7.3
file guvcview_video.mkv has extension type 1
file guvcview_image.jpg has extension type 0
file guvcview_image.jpg has extension type 0
Video file suffix detected: 0
Image file suffix detected: 0
video_device: /dev/video0
vid_sleep: 0
cap_meth: 1
resolution: 640 x 480
windowsize: 560 x 560
default action: 0
mode: mjpg
fps: 1/25
Display Fps: 0
bpp: 0
hwaccel: 1
vid_codec: 8
sound: 1
sound Device: 0
sound samp rate: 0
sound Channels: 0
Sound delay: 0 nanosec
Sound Format: 80 
Pan Step: 2 degrees
Tilt Step: 2 degrees
Video Filter Flags: 0
image inc: 1
profile(default):/home/casey/default.gpfl
starting portaudio...
ALSA lib pcm_dsnoop.c:618:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dmix.c:1022:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear
ALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
ALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
ALSA lib pcm_dmix.c:1022:(snd_pcm_dmix_open) unable to open slave
language catalog=> dir:/usr/share/locale type:UTF-8 lang:en cat:guvcview.mo
Screen resolution is (2560 x 2048)
mjpg: setting format to MJPG
capture method = 1
video device: /dev/video0 
Device Node Path: /dev/video0
  VID/PID: 046d 082c
  (null)
  HD Webcam C615
  serial: FC814150
  busnum: 3
  devnum: 8
vid:046d 
pid:082c 
driver:uvcvideo
device doesn't seem to support uvc H264 (0)
mapping control for Pan (relative)
UVCIOC_CTRL_MAP - Error: No such file or directory
mapping control for Tilt (relative)
UVCIOC_CTRL_MAP - Error: No such file or directory
mapping control for Pan Reset
UVCIOC_CTRL_MAP - Error: No such file or directory
mapping control for Tilt Reset
UVCIOC_CTRL_MAP - Error: No such file or directory
mapping control for Focus (absolute)
UVCIOC_CTRL_MAP - Error: No such file or directory
mapping control for LED1 Mode
UVCIOC_CTRL_MAP - Error: No such file or directory
mapping control for LED1 Frequency
UVCIOC_CTRL_MAP - Error: No such file or directory
mapping control for Disable video processing
UVCIOC_CTRL_MAP - Error: No such file or directory
mapping control for Raw bits per pixel
UVCIOC_CTRL_MAP - Error: No such file or directory
Init. HD Webcam C615 (location: usb-0000:00:14.0-11)
{ pixelformat = 'YUYV', description = 'YUV 4:2:2 (YUYV)' }
{ discrete: width = 640, height = 480 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 160, height = 120 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 176, height = 144 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 320, height = 240 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 432, height = 240 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 352, height = 288 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 640, height = 360 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 800, height = 448 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 864, height = 480 }
        Time interval between frame: 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 1024, height = 576 }
        Time interval between frame: 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 800, height = 600 }
        Time interval between frame: 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 960, height = 720 }
        Time interval between frame: 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 1280, height = 720 }
        Time interval between frame: 1/10, 2/15, 1/5, 
{ discrete: width = 1600, height = 896 }
        Time interval between frame: 2/15, 1/5, 
{ discrete: width = 1920, height = 1080 }
        Time interval between frame: 1/5, 
{ pixelformat = 'MJPG', description = 'MJPEG' }
{ discrete: width = 640, height = 480 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 160, height = 120 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 176, height = 144 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 320, height = 240 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 432, height = 240 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 352, height = 288 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 640, height = 360 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 800, height = 448 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 864, height = 480 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 1024, height = 576 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 800, height = 600 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 960, height = 720 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 1280, height = 720 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 1600, height = 896 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 1920, height = 1080 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ pixelformat = 'RGB3', description = 'RGB3' }
{ discrete: width = 640, height = 480 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 160, height = 120 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 176, height = 144 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 320, height = 240 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 432, height = 240 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 352, height = 288 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 640, height = 360 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 800, height = 448 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 864, height = 480 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 1024, height = 576 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 800, height = 600 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 960, height = 720 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 1280, height = 720 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 1600, height = 896 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 1920, height = 1080 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ pixelformat = 'BGR3', description = 'BGR3' }
{ discrete: width = 640, height = 480 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 160, height = 120 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 176, height = 144 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 320, height = 240 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 432, height = 240 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 352, height = 288 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 640, height = 360 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 800, height = 448 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 864, height = 480 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 1024, height = 576 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 800, height = 600 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 960, height = 720 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 1280, height = 720 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 1600, height = 896 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 1920, height = 1080 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ pixelformat = 'YU12', description = 'YU12' }
{ discrete: width = 640, height = 480 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 160, height = 120 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 176, height = 144 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 320, height = 240 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 432, height = 240 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 352, height = 288 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 640, height = 360 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 800, height = 448 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 864, height = 480 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 1024, height = 576 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 800, height = 600 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 960, height = 720 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 1280, height = 720 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 1600, height = 896 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 1920, height = 1080 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ pixelformat = 'YV12', description = 'YV12' }
{ discrete: width = 640, height = 480 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 160, height = 120 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 176, height = 144 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 320, height = 240 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 432, height = 240 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 352, height = 288 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 640, height = 360 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 800, height = 448 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 864, height = 480 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 1024, height = 576 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 800, height = 600 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 960, height = 720 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 1280, height = 720 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 1600, height = 896 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 1920, height = 1080 }
        Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
checking muxed H264 format support
device doesn't seem to support uvc H264 (0)
checking format: MJPG
VIDIOC_G_COMP:: Inappropriate ioctl for device
fps is set to 1/24
drawing controls

Segmentation fault (core dumped)

```

---

### Post by vasa1 on 2014-11-04
Please take a look at [https://bugs.launchpad.net/ubuntu/+source/guvcview/+bug/1373221](https://bugs.launchpad.net/ubuntu/+source/guvcview/+bug/1373221)

And the dev suggests using his testing ppa because the fix (whatever that is) may not be available until 15.04.

---

### Post by clepsdyrae on 2014-11-05
Thanks, yeah -- just came here to post that as well. Similar info here: [http://sourceforge.net/p/guvcview/tickets/13/](http://sourceforge.net/p/guvcview/tickets/13/)

The ppa is here: [https://launchpad.net/~pj-assis/+archive/ubuntu/ppa](https://launchpad.net/~pj-assis/+archive/ubuntu/ppa)

I uninstalled gucview, set up that repo, then installed guvcview (and the dependencies) and it works now. Video saving seems to generate corrupt files, but that may just be a separate issue.

---

### Post by mike260 on 2014-11-18
Hi guys,

I just wanted to chime in and say thank-you for the "fix". I added the ppa (**ppa:pj-assis/ppa) **and grabbed the latest version. Works great now. 

-Mike

---

### Post by Kapurush on 2015-01-15
PPA worked for me also. in 14.10.
 guvcview rocks.

---

### Post by vedavrata on 2015-01-20
The same problem. :-(

tosik@DELL-E6430:~$ uname -a
Linux DELL-E6430 3.16.0-30-generic #40-Ubuntu SMP Mon Jan 12 22:06:37 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Ubuntu 14.10 (Utopic Unicorn)


tosik@DELL-E6430:~$ guvcview 
guvcview 1.7.3
file guvcview_video.mkv has extension type 1
file guvcview_image.jpg has extension type 0

** (guvcview:24741): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-Grv3g4WwxK: Connection refused
file guvcview_image.jpg has extension type 0
Video file suffix detected: 0
Image file suffix detected: 0
ALSA lib pcm.c:2239; (snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear
ALSA lib pcm.c:2239; (snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
ALSA lib pcm.c:2239; (snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
ALSA lib pcm_route.c:947; (find_matching_chmap) Found no matching channel map
bt_audio_service_open: connect() failed: Connection refused (111)
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
checking format: JPEG
Format unavailable: JPEG
Init v4L2 failed !! 
Init video returned -2
trying minimum setup ...
    format: YUYV
    resolution: 640 x 480
    framerate: 1/30
video device: /dev/video0 
vid:046d 
pid:0825 
driver:uvcvideo
device doesn't seem to support uvc H264 (0)
mapping control for Pan (relative)
UVCIOC_CTRL_MAP - Error: No such file or directory
mapping control for Tilt (relative)
UVCIOC_CTRL_MAP - Error: No such file or directory
mapping control for Pan Reset
UVCIOC_CTRL_MAP - Error: No such file or directory
mapping control for Tilt Reset
UVCIOC_CTRL_MAP - Error: No such file or directory
mapping control for Focus (absolute)
UVCIOC_CTRL_MAP - Error: No such file or directory
mapping control for LED1 Mode
UVCIOC_CTRL_MAP - Error: No such file or directory
mapping control for LED1 Frequency
UVCIOC_CTRL_MAP - Error: No such file or directory
mapping control for Disable video processing
UVCIOC_CTRL_MAP - Error: No such file or directory
mapping control for Raw bits per pixel
UVCIOC_CTRL_MAP - Error: No such file or directory
Init. UVC Camera (046d:0825) (location: usb-0000:00:1d.0-1.7.2)
{ pixelformat = 'YUYV', description = 'YUV 4:2:2 (YUYV)' }
{ pixelformat = 'MJPG', description = 'MJPEG' }
{ pixelformat = 'RGB3', description = 'RGB3' }
{ pixelformat = 'BGR3', description = 'BGR3' }
{ pixelformat = 'YU12', description = 'YU12' }
{ pixelformat = 'YV12', description = 'YV12' }
checking muxed H264 format support
device doesn't seem to support uvc H264 (0)
checking format: YUYV
fps is set to 1/30
drawing controls

**Segmentation fault (core dumped)**

---

### Post by vedavrata on 2015-01-20
> **clepsdyrae said:**
> Thanks, yeah -- just came here to post that as well. Similar info here: [http://sourceforge.net/p/guvcview/tickets/13/](http://sourceforge.net/p/guvcview/tickets/13/)

The ppa is here: [https://launchpad.net/~pj-assis/+archive/ubuntu/ppa](https://launchpad.net/~pj-assis/+archive/ubuntu/ppa)

I uninstalled gucview, set up that repo, then installed guvcview (and the dependencies) and it works now. Video saving seems to generate corrupt files, but that may just be a separate issue.

This helped me!
Thank you very much!

By this, guvcveiw updates from version 1.7.3. to 2.0.1 and started to work:
Guvcview version 2.0.1



// Anton Kuznetsov (Vedavrat)
// [http://Vedavrat.org](http://Vedavrat.org)

---

### Post by nscbabu on 2015-07-09
Have you tried using QtCam?

---

