---
title: "Help with Motion"
date: 2013-03-28
forum: General Help
---

### Post by parly on 2013-03-28
Hi, I have been trying to use motion (camera recording) on my ubuntu 10.04 64bit and am having some issues. I have looked everywhere for an answer but cannot seem to find it. I am using a Logitech C10 and I have already set up all the motion configurations but still get the following results;


_**When I do not start the motion detection daemon separately, I get this: **_
```

user@ubuntu:~$ sudo motion
[0] Processing thread 0 - config file /etc/motion/motion.conf
[0] Motion 3.2.11 Started
[0] ffmpeg LIBAVCODEC_BUILD 3412993 LIBAVFORMAT_BUILD 3415808
[0] Thread 1 is from /etc/motion/motion.conf
[1] Thread 1 started
[0] motion-httpd/3.2.11 running, accepting connections
[0] motion-httpd: waiting for data on port TCP 8080
[1] cap.driver: "uvcvideo"
[1] cap.card: "UVC Camera (046d:081b)"
[1] cap.bus_info: "usb-0000:00:1d.7-2"
[1] cap.capabilities=0x04000001
[1] - VIDEO_CAPTURE
[1] - STREAMING
[1] Supported palettes:
[1] 0: YUYV (YUV 4:2:2 (YUYV))
[1] 1: MJPG (MJPEG)
[1] index_format 2 Test palette MJPG (1280x720)
[1] Using palette MJPG (1280x720) bytesperlines 0 sizeimage 816000 colorspace 00000008
[1] VIDIOC_G_JPEGCOMP not supported but it should be (does your webcam driver support this ioctl?)
[1] found control 0x00980900, "Brightness", range 0,255 
[1]     "Brightness", default 128, current 128
[1] found control 0x00980901, "Contrast", range 0,255 
[1]     "Contrast", default 32, current 32
[1] found control 0x00980902, "Saturation", range 0,255 
[1]     "Saturation", default 32, current 32
[1] found control 0x00980913, "Gain", range 0,255 
[1]     "Gain", default 0, current 0
[1] mmap information:
[1] frames=4
[1] 0 length=816000
[1] 1 length=816000
[1] 2 length=816000
[1] 3 length=816000
[1] Using V4L2
[1] Resizing pre_capture buffer to 1 items
[0] httpd - Finishing
[0] httpd Closing
[0] httpd thread exit
Corrupt JPEG data: 4 extraneous bytes before marker 0xd4
[1] mjpegtoyuv420p: Corrupt image ... continue
Corrupt JPEG data: 4 extraneous bytes before marker 0xd1
[1] mjpegtoyuv420p: Corrupt image ... continue
Corrupt JPEG data: 2 extraneous bytes before marker 0xd0
[1] mjpegtoyuv420p: Corrupt image ... continue
Corrupt JPEG data: 1 extraneous bytes before marker 0xd7
[1] mjpegtoyuv420p: Corrupt image ... continue
[1] mjpegtoyuv420p: Corrupt image ... continue
Corrupt JPEG data: 2 extraneous bytes before marker 0xd2
[1] mjpegtoyuv420p: Corrupt image ... continue
Corrupt JPEG data: 1 extraneous bytes before marker 0xd7
[1] mjpegtoyuv420p: Corrupt image ... continue
Corrupt JPEG data: 1 extraneous bytes before marker 0xd0
[1] mjpegtoyuv420p: Corrupt image ... continue
Corrupt JPEG data: 2 extraneous bytes before marker 0xd5
[1] mjpegtoyuv420p: Corrupt image ... continue
Corrupt JPEG data: 3 extraneous bytes before marker 0xd1
[1] mjpegtoyuv420p: Corrupt image ... continue
Corrupt JPEG data: 1 extraneous bytes before marker 0xd1
[1] mjpegtoyuv420p: Corrupt image ... continue
Corrupt JPEG data: 1 extraneous bytes before marker 0xd0
[1] mjpegtoyuv420p: Corrupt image ... continue
Corrupt JPEG data: 3 extraneous bytes before marker 0xd7
[1] mjpegtoyuv420p: Corrupt image ... continue
[1] Error capturing first image
[1] Started stream webcam server in port 8081
[1] Thread exiting
[1] Calling vid_close() from motion_cleanup
[1] Closing video device /dev/video0
[0] Motion terminating

```


_**When I start the motion detection daemon separately, I get this: **_
```

user@ubuntu:/etc/motion$ sudo service motion start
[sudo] password for user: 
 * Starting motion detection daemon : motion                             [ OK ] 
user@ubuntu:/etc/motion$ sudo motion
[0] Processing thread 0 - config file /etc/motion/motion.conf
[0] Motion 3.2.11 Started
[0] ffmpeg LIBAVCODEC_BUILD 3412993 LIBAVFORMAT_BUILD 3415808
[0] Thread 1 is from /etc/motion/motion.conf
[1] Thread 1 started
[0] httpd bind(): 
[0] httpd thread exit
[1] cap.driver: "uvcvideo"
[1] cap.card: "UVC Camera (046d:081b)"
[1] cap.bus_info: "usb-0000:00:1d.7-7.3"
[1] cap.capabilities=0x04000001
[1] - VIDEO_CAPTURE
[1] - STREAMING
[1] Error selecting input 0 VIDIOC_S_INPUT: 
[1] ioctl(VIDIOCGMBUF) - Error device does not support memory map
[1] V4L capturing using read is deprecated!
[1] Motion only supports mmap.
[1] Could not fetch initial image from camera
[1] Motion continues using width and height from config file(s)
[1] Resizing pre_capture buffer to 1 items
[1] Started stream webcam server in port 8081
[1] Retrying until successful connection with camera

```

I have searched everywhere for answers to the following lines;
[1] VIDIOC_G_JPEGCOMP not supported but it should be (does your webcam driver support this ioctl?)
and
[1] ioctl(VIDIOCGMBUF) - Error device does not support memory map

because I have seen other people having this same problem so thought this might be the common problem but cannot find any solutions. Hopefully someone here has already set this up and knows where I am at/how to move past this point.

Thank you anyone for your help in advance!

---

### Post by papibe on 2013-03-28
Hi parly. Welcome to the forums ):P

Could you post the result of this command?
```
grep ^[[:alpha:]]  /etc/motion/motion.conf
```
Regards.

---

### Post by parly on 2013-03-28
> **papibe said:**
> Hi parly. Welcome to the forums ):P

Could you post the result of this command?
```
grep ^[[:alpha:]]  /etc/motion/motion.conf
```
Regards.

Thanks, here it is;

```

user@ubuntu:~$ sudo grep ^[[:alpha:]]  /etc/motion/motion.conf
[sudo] password for user: 
daemon off
process_id_file /var/run/motion/motion.pid 
setup_mode off
videodevice /dev/video0
v4l2_palette 8
input 8
norm 0
frequency 0
rotate 0
width 1280
height 720
framerate 10
minimum_frame_time 0
netcam_tolerant_check off
auto_brightness off
brightness 0
contrast 0
saturation 0
hue 0
roundrobin_frames 1
roundrobin_skip 1
switchfilter off
threshold 1500
threshold_tune off
noise_level 32
noise_tune on
despeckle EedDl
smart_mask_speed 0
lightswitch 0
minimum_motion_frames 1
pre_capture 0
post_capture 70
gap 60
max_mpeg_time 0
output_all off
output_normal off
output_motion off
quality 75
ppm off
ffmpeg_cap_new on
ffmpeg_cap_motion off
ffmpeg_timelapse 0
ffmpeg_timelapse_mode daily
ffmpeg_bps 500000
ffmpeg_variable_bitrate 0
ffmpeg_video_codec mpeg4
ffmpeg_deinterlace off
snapshot_interval 0
locate off
text_right %Y-%m-%d\n%T-%q
text_changes off
text_event %Y%m%d%H%M%S
text_double on
target_dir /home/user/Media/Camera
snapshot_filename %v--%Y-%m-%d---%H-%M-%S-snapshot
jpeg_filename %v--%Y-%m-%d---%H-%M-%S-%q
movie_filename %v--%Y-%m-%d---%H-%M-%S
timelapse_filename %Y%m%d-timelapse
webcam_port 8081
webcam_quality 50
webcam_motion off
webcam_maxrate 1
webcam_localhost on
webcam_limit 0
control_port 8080
control_localhost on
control_html_output on
track_type 0
track_auto off
track_motorx 0
track_motory 0
track_maxx 0
track_maxy 0
track_iomojo_id 0
track_step_angle_x 10
track_step_angle_y 10
track_move_wait 10
track_speed 255
track_stepsize 40
quiet on
sql_log_image on
sql_log_snapshot on
sql_log_mpeg off
sql_log_timelapse off
sql_query insert into security(camera, filename, frame, file_type, time_stamp, event_time_stamp) values('%t', '%f', '%q', '%n', '%Y-%m-%d %T', '%C')

```

---

### Post by papibe on 2013-03-28
Thanks.

Here's a few tips:
[LIST]
[*]Connect the camera directly to the computer, not through a usb hub.
[*]Are you using USB 2.0? Maybe you don't have the bandwidth to handle the camera. 
[*]Set a lower resolution, that may help with the previous point.
[*]I personally use NTSC instead of PAL (norm 1), but that may not be an issue.
[*]This is what usually solve any of my problems:

Install this package:
```
sudo apt-get install libv4l-0
```
And then call motion preloading a library:
```
LD_PRELOAD=/usr/lib/x86_64-linux-gnu/libv4l/v4l2convert.so  motion
```
[/LIST]
Just a few thought. Let us know how it goes.
Regards.

---

### Post by parly on 2013-03-29
Well it looks like its progress... not quite there but progress ;)

still seems to give the same error but this time "camera monitor" pops up saying the camera /video0 has been turned on which did not happen before

```

user@ubuntu:~$ sudo apt-get install libv4l-0
[sudo] password for user:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libv4l-0 is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-38 linux-headers-2.6.32-38-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

```

```

user@ubuntu:~$ LD_PRELOAD=/usr/lib/x86_64-linux-gnu/libv4l/v4l2convert.so  motion
ERROR: ld.so: object '/usr/lib/x86_64-linux-gnu/libv4l/v4l2convert.so' from LD_PRELOAD cannot be preloaded: ignored.
[0] could not open configfile /etc/motion/motion.conf:
[0] Not config file to process using default values
[0] Motion 3.2.11 Started
[0] ffmpeg LIBAVCODEC_BUILD 3412993 LIBAVFORMAT_BUILD 3415808
[1] Thread 1 started
[1] cap.driver: "uvcvideo"
[1] cap.card: "UVC Camera (046d:081b)"
[1] cap.bus_info: "usb-0000:00:1d.7-7.3"
[1] cap.capabilities=0x04000001
[1] - VIDEO_CAPTURE
[1] - STREAMING
[1] Supported palettes:
[1] 0: YUYV (YUV 4:2:2 (YUYV))
[1] 1: MJPG (MJPEG)
[1] index_format 2 Test palette MJPG (352x288)
[1] Using palette MJPG (352x288) bytesperlines 0 sizeimage 102400 colorspace 00000008
[1] VIDIOC_G_JPEGCOMP not supported but it should be (does your webcam driver support this ioctl?)
[1] found control 0x00980900, "Brightness", range 0,255
[1]     "Brightness", default 128, current 128
[1] found control 0x00980901, "Contrast", range 0,255
[1]     "Contrast", default 32, current 32
[1] found control 0x00980902, "Saturation", range 0,255
[1]     "Saturation", default 32, current 32
[1] found control 0x00980913, "Gain", range 0,255
[1]     "Gain", default 0, current 0
[1] mmap information:
[1] frames=4
[1] 0 length=102400
[1] 1 length=102400
[1] 2 length=102400
[1] 3 length=102400
[1] Using V4L2
[1] Resizing pre_capture buffer to 1 items
Corrupt JPEG data: 1 extraneous bytes before marker 0xd4
[1] mjpegtoyuv420p: Corrupt image ... continue
Corrupt JPEG data: 1 extraneous bytes before marker 0xd3
[1] mjpegtoyuv420p: Corrupt image ... continue
Corrupt JPEG data: 3 extraneous bytes before marker 0xd7
[1] mjpegtoyuv420p: Corrupt image ... continue
Corrupt JPEG data: 3 extraneous bytes before marker 0xd4
[1] mjpegtoyuv420p: Corrupt image ... continue
Corrupt JPEG data: 1 extraneous bytes before marker 0xd2
[1] mjpegtoyuv420p: Corrupt image ... continue
[1] Error capturing first image
Corrupt JPEG data: 4 extraneous bytes before marker 0xd4
[1] mjpegtoyuv420p: Corrupt image ... continue
Corrupt JPEG data: 1 extraneous bytes before marker 0xd4
[1] mjpegtoyuv420p: Corrupt image ... continue
Corrupt JPEG data: 1 extraneous bytes before marker 0xd7
[1] mjpegtoyuv420p: Corrupt image ... continue
Corrupt JPEG data: 1 extraneous bytes before marker 0xd2
[1] mjpegtoyuv420p: Corrupt image ... continue
Corrupt JPEG data: 1 extraneous bytes before marker 0xd7
[1] mjpegtoyuv420p: Corrupt image ... continue
Corrupt JPEG data: 4 extraneous bytes before marker 0xd3
[1] Thread exiting
[1] Calling vid_close() from motion_cleanup
[1] Closing video device /dev/video0
[0] Motion terminating
user@ubuntu:~$

```

> 
&#8730; | Connect the camera directly to the computer, not through a usb hub.
Are you using USB 2.0? Maybe you don't have the bandwidth to handle the camera.
&#8730; | Set a lower resolution, that may help with the previous point.
I personally use NTSC instead of PAL (norm 1), but that may not be an issue.
&#8730; | This is what usually solve any of my problems:


I tried a different cam, pluged it directly into the tower and lowered the res all the way down to default 235X288. This still gave me the error only difference is I do not get the corrupt image errror anymore. Here is what came back after the cam/res change;
 - I did try running the camera with cheese and it runs fine so it is not a connection issue

```

user@ubuntu:~$ LD_PRELOAD=/usr/lib/x86_64-linux-gnu/libv4l/v4l2convert.so  motion
ERROR: ld.so: object '/usr/lib/x86_64-linux-gnu/libv4l/v4l2convert.so' from LD_PRELOAD cannot be preloaded: ignored.
[0] could not open configfile /etc/motion/motion.conf: 
[0] Not config file to process using default values
[0] Motion 3.2.11 Started
[0] ffmpeg LIBAVCODEC_BUILD 3412993 LIBAVFORMAT_BUILD 3415808
[1] Thread 1 started
[1] Failed to open video device /dev/video0: 
[1] Could not fetch initial image from camera
[1] Motion continues using width and height from config file(s)
[1] Resizing pre_capture buffer to 1 items
[1] Retrying until successful connection with camera
[1] Failed to open video device /dev/video0: 
[1] Retrying until successful connection with camera
[1] Failed to open video device /dev/video0: 
[1] Thread exiting
[0] Motion terminating
user@ubuntu:~$ 

```



Thank you for all your help :D

---

### Post by papibe on 2013-03-29
A couple of things:

It is easier to run motion as a regular user as long as you add yourself to the video group (so you can have access to /dev/video):
```
sudo usermod -a -G video yourusername
```

It seems that the path for the LD_PRELOAD variable is incorrect. It works on 12.04, but clearly not in yours. Could you post the result of this command?
```
dpkg -L libv4l-0 | grep convert
```
Regards.

---

### Post by parly on 2013-03-30
ahhh yeah I'm on 10.04... (not a big fan of the new layout lol)


I added myself as a user and here is the result to the other command; 

```

user@ubuntu:~$ dpkg -L libv4l-0 | grep convert
/usr/lib/libv4lconvert.so.0
/usr/lib/libv4l/v4l2convert.so

```

---

### Post by papibe on 2013-04-01
There you go. It's a different path.

Try this then:
```
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so  motion
```
Let us know how it goes.
Regards.

---

### Post by parly on 2013-04-01
gave it a try and it says this about framesizes;

```

user@ubuntu:~$ LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so  motion
[0] could not open configfile /etc/motion/motion.conf: 
[0] Not config file to process using default values
[0] Motion 3.2.11 Started
[0] ffmpeg LIBAVCODEC_BUILD 3412993 LIBAVFORMAT_BUILD 3415808
[1] Thread 1 started
libv4lconvert: warning more framesizes then I can handle!
libv4lconvert: warning more framesizes then I can handle!
[1] cap.driver: "uvcvideo"
[1] cap.card: "UVC Camera (046d:081b)"
[1] cap.bus_info: "usb-0000:00:1d.7-7.3"
[1] cap.capabilities=0x05000001
[1] - VIDEO_CAPTURE
[1] - READWRITE
[1] - STREAMING
[1] Error selecting input 0 VIDIOC_S_INPUT: 
[1] ioctl(VIDIOCGMBUF) - Error device does not support memory map
[1] V4L capturing using read is deprecated!
[1] Motion only supports mmap.
[1] Could not fetch initial image from camera
[1] Motion continues using width and height from config file(s)
[1] Resizing pre_capture buffer to 1 items
[1] Retrying until successful connection with camera
libv4lconvert: warning more framesizes then I can handle!
libv4lconvert: warning more framesizes then I can handle!
[1] cap.driver: "uvcvideo"
[1] cap.card: "UVC Camera (046d:081b)"
[1] cap.bus_info: "usb-0000:00:1d.7-7.3"
[1] cap.capabilities=0x05000001
[1] - VIDEO_CAPTURE
[1] - READWRITE
[1] - STREAMING
[1] Error selecting input 0 VIDIOC_S_INPUT: 
[1] ioctl(VIDIOCGMBUF) - Error device does not support memory map
[1] V4L capturing using read is deprecated!
[1] Motion only supports mmap.
[1] Thread exiting
[0] Motion terminating

```

---

### Post by papibe on 2013-04-01
```
[0] could not open configfile /etc/motion/motion.conf: 
```
By default the conf file is not readable for all users. To enable it:
```
sudo chmod a+r /etc/motion/motion.conf
```
Regards.

---

### Post by parly on 2013-04-03
:) :) :)

The first thing I read about motion was it creates its own user to run and that can cause you issues. Of coruse I actually made a note on it so I wouldn't forget too.

So I ran it and same errors, stopped it, restarted and ran again but this time it seems to be working perfect. I was able to change all the settings and res back to full and it continues to work fine so thank you very much for all your help.

Only question I have is every few motions I get this;

```

[1] File of type 8 saved to: /media/Camera/2013-04-03_10-55-29.avi
[1] File of type 8 saved to: /media/Camera/2013-04-03_10-59-08.avi
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 4 more bits
[1] File of type 8 saved to: /media/Camera/2013-04-03_11-03-17.avi
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 2 more bits
[1] File of type 8 saved to: /media/Camera/2013-04-03_11-07-12.avi
[1] File of type 8 saved to: /media/Camera/2013-04-03_11-10-13.avi

```

---

