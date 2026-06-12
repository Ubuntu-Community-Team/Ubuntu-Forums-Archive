---
title: "motion with RTSP stream"
date: 2014-06-07
forum: General Help
---

### Post by Jevgenij on 2014-06-07
hello, I am trying to capture video with motion software from cheap Chinese IP camera, that is ONVIF compatible.
I can see and capture video on my windows machine with stupid out-of-the-box software, but is worthless. I want it to work with motion.
so in the IP cam settings, in MediaServer tab, I see:
Authentication                           enable/disable                           -tried both       
Media access port                     554                                                   -does not lets me change it 
Media access protocol            TCP or UDP                                   -tried both 
PTZ control port                         8091                                                -no reason to change that
Web Access Port                       80                                                     -tried 8080


I can see video with VLC on windows machine entering url   rtsp://192.168.0.254:554/mpeg4

but when I open 192.168.0.254:80 or :8080 on my browser the device keeps saying PLEASE INSTALL THE PLUG (the damn genuine software)


my motions threadX.conf file:

netcam_userpass admin:password
text_left Foscam IP
netcam_url rtsp://192.168.0.254:554/mpeg4
target_dir /var/www/unius/www/record
webcam_port 8081

gives me output:
.....
[1] Invalid netcam_url (rtsp://192.168.0.254:554/mpeg4)
[1] Could not fetch initial image from camera
[1] Motion continues using width and height from config file(s)                   <-- using 1280x720 resolution
[1] Resizing pre_capture buffer to 1 items
[1] Started stream webcam server in port 8081
[1] Retrying until successful connection with camera
[1] Invalid netcam_url (rtsp://192.168.0.254:554/mpeg4)
.....



so the question is: 

can motion handle rtsp stream? if yes, how it is done? if not, what software to use on ubuntu server, without GUI

---

### Post by Jevgenij on 2014-06-09
figured out that motion does not support RTSP streams. any ideas how to record RTSP stream with motion detection on ubuntu 12.04 server?

---

### Post by Mike_Wilson on 2014-06-25
Check out [https://github.com/hyperbolic2346/motion](https://github.com/hyperbolic2346/motion) for a fork that supports RTSP. I haven't been paying attention to this too much since I wrote it, but it looks like there have been some forks. Maybe someone has improved upon it. I need to get back in to it a little since the code isn't properly handling camera resets currently.

---

### Post by aliceander on 2014-07-28
I'm interested in your work since I have an rstp camera.  I've downloaded the code and have just started to look at it.  Configure has a problem autodetecting ffmpeg libraries (when ffmpeg went multiarch and the libraries moved location and configure doesn't look in the new locations).  I will be looking into how to work around that, but just in case you already have a solution, please let me know.  I'm excited to get this working since my netcam is limited in what it can do, but it can support rstp.

---

### Post by Mike_Wilson on 2014-07-28
> **aliceander said:**
> I'm interested in your work since I have an rstp camera.  I've downloaded the code and have just started to look at it.  Configure has a problem autodetecting ffmpeg libraries (when ffmpeg went multiarch and the libraries moved location and configure doesn't look in the new locations).  I will be looking into how to work around that, but just in case you already have a solution, please let me know.  I'm excited to get this working since my netcam is limited in what it can do, but it can support rstp.

You want to include the path to your ffmpeg on the configure line. I downloaded the ffmpeg source, built it and then used the following configure:

./configure --with-ffmpeg=$HOME/ffmpeg --with-ffmpeg-headers=$HOME/ffmpeg/include --with-ffmpeg-libs=" -lavformat -lavcodec -lavutil -lx264 -lvpx -lvorbis -lvorbisenc"

---

### Post by aliceander on 2014-07-30
Oh, man, THANK YOU!  I had trouble compiling the code the other night and gave up.  I will try again this weekend.  I'm excited about getting motion working with rtsp support.

---

### Post by aliceander on 2014-07-30
BTW Did you use the current ffmpeg code (e.g. current tarball, svn trunk, etc), or an archived version?

---

### Post by Mike_Wilson on 2014-07-31
I downloaded and installed the latest version at the time I did the work. I assume the latest will work fine.

---

