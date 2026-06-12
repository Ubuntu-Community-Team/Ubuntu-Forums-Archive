---
title: "Howto record audio and video from web cam with VLC?"
date: 2023-06-10
forum: General Help
---

### Post by Old Jimma on 2023-06-10
Hello Forum:

I need to record myself playing a tune with my guitar... and since VLC is installed, I think I should use VLC.

I've looked high an low on how to do this. While there seems to be help  here [HTML]https://www.vlchelp.com/how-to-record-webcam-video-using-vlc-media-player/[/HTML] and elsewhere, that advice does not work because there is no "Direct  Show" at Media > Open Capture Device > Capture Mode

Please either:
[LIST]
[*]describe how to use VLC to record myself playing guitar using VLC, or
[*]tell me about other software that works and is easy to use.
[*]
[/LIST]

Thanks,
Old

---

### Post by #&amp;thj^% on 2023-06-10
There he is>>Old Jmma.;)
 with audio and video:
```
vlc v4l2:// :input-slave=alsa:// :v4l-vdev="/dev/video0" :v4l-norm=3 :v4l-frequency=-1 :v4l-caching=300 :v4l-chroma="" :v4l-fps=-1.000000 :v4l-samplerate=44100 :v4l-channel=0 :v4l-tuner=-1 :v4l-audio=-1 :v4l-stereo :v4l-width=480 :v4l-height=360 :v4l-brightness=-1 :v4l-colour=-1 :v4l-hue=-1 :v4l-contrast=-1 :no-v4l-mjpeg :v4l-decimation=1 :v4l-quality=100 --sout="#transcode{vcodec=theo,vb=2000,fps=12,scale=0.67,acodec=vorb,ab=90,channels=1,samplerate=44100}:standard{access=file,mux=ogg,dst=output.ogg}"
```
Or even this:
```
vlc v4l2:// :v4l-vdev="/dev/video0" :v4l-adev="/dev/pcm" :v4l-norm=3 :v4l-frequency=-1 :v4l-caching=300 :v4l-chroma="" :v4l-fps=-1.000000 :v4l-samplerate=44100 :v4l-channel=0 :v4l-tuner=-1 :v4l-audio=-1 :v4l-stereo :v4l-width=480 :v4l-height=360 :v4l-brightness=-1 :v4l-colour=-1 :v4l-hue=-1 :v4l-contrast=-1 :no-v4l-mjpeg :v4l-decimation=1 :v4l-quality=100 --sout="#transcode{vcodec=theo,vb=2000,fps=12,scale=0.67,acodec=vorb,ab=90,channels=1,samplerate=44100}:standard{access=file,mux=ogg,dst=output.ogg}"
```
And as always your experience may vary, depending on your hardware.
And make sure audio source is the proper source.
```
v4l2-ctl --list-devices
Integrated Camera: Integrated C (usb-0000:05:00.3-3):
	/dev/video0
	/dev/video1
	/dev/media0

```
Important, Check the availible formats:
```
v4l2-ctl --list-formats-ext -d /dev/video0
ioctl: VIDIOC_ENUM_FMT
	Type: Video Capture

	[0]: 'MJPG' (Motion-JPEG, compressed)
		Size: Discrete 1280x720
			Interval: Discrete 0.033s (30.000 fps)
		Size: Discrete 320x180
			Interval: Discrete 0.033s (30.000 fps)
		Size: Discrete 320x240
			Interval: Discrete 0.033s (30.000 fps)
		Size: Discrete 352x288
			Interval: Discrete 0.033s (30.000 fps)
		Size: Discrete 424x240
			Interval: Discrete 0.033s (30.000 fps)
		Size: Discrete 640x360
			Interval: Discrete 0.033s (30.000 fps)
		Size: Discrete 640x480
			Interval: Discrete 0.033s (30.000 fps)
		Size: Discrete 848x480
			Interval: Discrete 0.033s (30.000 fps)
		Size: Discrete 960x540
			Interval: Discrete 0.033s (30.000 fps)
	[1]: 'YUYV' (YUYV 4:2:2)
		Size: Discrete 1280x720
			Interval: Discrete 0.100s (10.000 fps)
		Size: Discrete 320x180
			Interval: Discrete 0.033s (30.000 fps)
		Size: Discrete 320x240
			Interval: Discrete 0.033s (30.000 fps)
		Size: Discrete 352x288
			Interval: Discrete 0.033s (30.000 fps)
		Size: Discrete 424x240
			Interval: Discrete 0.033s (30.000 fps)
		Size: Discrete 640x360
			Interval: Discrete 0.033s (30.000 fps)
		Size: Discrete 640x480
			Interval: Discrete 0.033s (30.000 fps)wpctl status
PipeWire 'pipewire-0' [0.3.71, me@arch-me, cookie:4097745474]
 &#9492;&#9472; Clients:
        31. pipewire                            [0.3.71, me@arch-me, pid:897]
        32. xfwm4                               [0.3.71, me@arch-me, pid:875]
        34. WirePlumber                         [0.3.71, me@arch-me, pid:896]
        35. WirePlumber [export]                [0.3.71, me@arch-me, pid:896]
        41. xdg-desktop-portal                  [0.3.71, me@arch-me, pid:1326]
        42. xfce4-pulseaudio-plugin             [0.3.71, me@arch-me, pid:952]
        68. wpctl                               [0.3.71, me@arch-me, pid:548670]

Audio
 &#9500;&#9472; Devices:
 &#9474;      46. HDA NVidia                          [alsa]
 &#9474;      47. UOEOS Laptop Dock                   [alsa]
 &#9474;      48. Family 17h/19h HD Audio Controller  [alsa]
 &#9474;  
 &#9500;&#9472; Sinks:
 &#9474;  *   57. UOEOS Laptop Dock Analog Stereo     [vol: 0.40]
 &#9474;      59. Family 17h/19h HD Audio Controller Analog Stereo [vol: 0.40]
 &#9474;  
 &#9500;&#9472; Sink endpoints:
 &#9474;  
 &#9500;&#9472; Sources:
 &#9474;  *   58. UOEOS Laptop Dock Analog Stereo     [vol: 1.00]
 &#9474;      60. Family 17h/19h HD Audio Controller Analog Stereo [vol: 1.00]
 &#9474;  
 &#9500;&#9472; Source endpoints:
 &#9474;  
 &#9492;&#9472; Streams:

Video
 &#9500;&#9472; Devices:
 &#9474;      43. Integrated Camera                   [v4l2]
 &#9474;      44. Integrated Camera                   [v4l2]
 &#9474;      45. Integrated Camera: Integrated C     [libcamera]
 &#9474;  
 &#9500;&#9472; Sinks:
 &#9474;  
 &#9500;&#9472; Sink endpoints:
 &#9474;  
 &#9500;&#9472; Sources:
 &#9474;  *   49. Integrated Camera (V4L2)           
 &#9474;      51. Built-in Front Camera              
 &#9474;  
 &#9500;&#9472; Source endpoints:
 &#9474;  
 &#9492;&#9472; Streams:

Settings
 &#9492;&#9472; Default Configured Node Names:

		Size: Discrete 848x480
			Interval: Discrete 0.050s (20.000 fps)
		Size: Discrete 960x540
			Interval: Discrete 0.067s (15.000 fps)

```
Also determine sound source (card: 0 ..., device: 1... is equal to hw:0,1. In this example hw:0,0):
I'm total wireplumber here, so no confusion between yours and mine:
```
wpctl status
PipeWire 'pipewire-0' [0.3.71, me@arch-me, cookie:4097745474]
 &#9492;&#9472; Clients:
        31. pipewire                            [0.3.71, me@arch-me, pid:897]
        32. xfwm4                               [0.3.71, me@arch-me, pid:875]
        34. WirePlumber                         [0.3.71, me@arch-me, pid:896]
        35. WirePlumber [export]                [0.3.71, me@arch-me, pid:896]
        41. xdg-desktop-portal                  [0.3.71, me@arch-me, pid:1326]
        42. xfce4-pulseaudio-plugin             [0.3.71, me@arch-me, pid:952]
        68. wpctl                               [0.3.71, me@arch-me, pid:548670]

Audio
 &#9500;&#9472; Devices:
 &#9474;      46. HDA NVidia                          [alsa]
 &#9474;      47. UOEOS Laptop Dock                   [alsa]
 &#9474;      48. Family 17h/19h HD Audio Controller  [alsa]
 &#9474;  
 &#9500;&#9472; Sinks:
 &#9474;  *   57. UOEOS Laptop Dock Analog Stereo     [vol: 0.40]
 &#9474;      59. Family 17h/19h HD Audio Controller Analog Stereo [vol: 0.40]
 &#9474;  
 &#9500;&#9472; Sink endpoints:
 &#9474;  
 &#9500;&#9472; Sources:
 &#9474;  *   58. UOEOS Laptop Dock Analog Stereo     [vol: 1.00]
 &#9474;      60. Family 17h/19h HD Audio Controller Analog Stereo [vol: 1.00]
 &#9474;  
 &#9500;&#9472; Source endpoints:
 &#9474;  
 &#9492;&#9472; Streams:

Video
 &#9500;&#9472; Devices:
 &#9474;      43. Integrated Camera                   [v4l2]
 &#9474;      44. Integrated Camera                   [v4l2]
 &#9474;      45. Integrated Camera: Integrated C     [libcamera]
 &#9474;  
 &#9500;&#9472; Sinks:
 &#9474;  
 &#9500;&#9472; Sink endpoints:
 &#9474;  
 &#9500;&#9472; Sources:
 &#9474;  *   49. Integrated Camera (V4L2)           
 &#9474;      51. Built-in Front Camera              
 &#9474;  
 &#9500;&#9472; Source endpoints:
 &#9474;  
 &#9492;&#9472; Streams:

Settings
 &#9492;&#9472; Default Configured Node Names:

```
I'm not sure if simple-screen-recorder would work but possibly?

---

### Post by Old Jimma on 2023-06-11
Hello 1fallen:

Thank you so much for compiling all of that information! There is alot for me to learn from what you sent. Thanks!

I tried all of it.

What seemed to be most simple was simple-screen-saver. 

TO get that to work, had to figure out (by trial and error) what the /dev/videox was for my web cam (it ws /dev/video4) and to make sure my audio recording device was. Once I got that right, the gui for simple-screen-saver worked well and saved the recording in the folder and file I indicated using the gui.

The only problemwith simple-screen-saver is that it does not make me and my guitar sound like Chet Atkins and his guitar.

Is there an app for that??

;-)
Many thanks!
Old

---

### Post by #&amp;thj^% on 2023-06-11
> **Old Jimma said:**
> 

The only problemwith simple-screen-saver is that it does not make me and my guitar sound like Chet Atkins and his guitar.

Is there an app for that??

;-)
Many thanks!
Old
:lolflag: 
Wouldn't that be great.
Thanks for trying on simple-screen-recorder and verifing.

---

