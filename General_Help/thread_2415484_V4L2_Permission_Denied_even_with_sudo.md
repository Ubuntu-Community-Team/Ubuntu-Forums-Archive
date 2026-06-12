---
title: "V4L2 Permission Denied even with sudo"
date: 2019-03-26
forum: General Help
---

### Post by csete on 2019-03-26
I'm trying to set up a webcam (Logitech C270) on my Ubuntu 18.04 system.  I'm having strange permission issues that I don't understand.  I've added my usual user to the "video" group (logged in and out) and I've also tried with sudo and in both cases I'm seeing:

sudo mjpg-streamer -i "input_uvc.so -r 1280x720 -f 30" -o "output_http.so -w ./www"                                             1 &#8629;
[sudo] password for user:
MJPG Streamer Version: git rev: f387bb44e6c087271b763b27da998bf2e06c4f5d
 i: Using V4L2 device.: /dev/video0
 i: Desired Resolution: 1280 x 720
 i: Frames Per Second.: 30
 i: Format............: JPEG
 i: TV-Norm...........: DEFAULT
ERROR opening V4L interface: Permission denied
 Init v4L2 failed !! exit fatal
 i: init_VideoIn failed

Cheese also fails to show the camera.  However, if I use VLC, I can see the camera.  So, I have two programs claiming permissions issues even with root authority and one that works.  I'm stumped and could use some direction.

Thanks,
Craig

---

### Post by TheFu on 2019-03-26
What you've done with the group seems reasonable.  Running GUI tools as root isn't a good idea, but if you must, always use sudo -H {name of GUI tool}, so the HOME directory is modified to be that for 'root', not left as your userid, which can cause strange problems.

I've never gotten cheese to work, ever.

[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam) provided for lurkers.
[https://help.ubuntu.com/community/UVC](https://help.ubuntu.com/community/UVC)

I always used either uvc-something or **obs**.  **guvcview** is the tool.  I'm on a new box now and need to get the webcam working.  cheese locked up the GUI, hard.  So did guvcview.  I had to physically walk to a different machine and ssh back in, kill the process and all is well again.  About a month ago, I modified the system to run most programs in a firejail, by default, so some of the issues I have are with that.  But neither cheese nor guvcview have that modification and syslog proves that along with not having **any** other issues.

I know my webcam works. Used it for some video calls through my nextcloud server over the last month. Worked perfectly. I'm not in the video unix group. My permissions are:
```
crw-rw----+ 1 root video 81, 0 Mar 24 16:04 video0
```

Added myself to the video group and guvcview worked perfectly.  I just edited the /etc/group file, ran **newgrp** (no args) in that terminal, then ran guvcview and it worked perfectly.  I'm lazy and didn't want the hassles of having to get my browser tabs up again and a few website logins going. The logout and login method should work even better.  Does '**id**' prove that your userid is in the video group?

---

### Post by csete on 2019-04-01
It turned out that I had two problems.  Installing guvcview fixed cheese for some reason?  mjpg-streamer was fixed by setting the appropriate permissions for the snap that I was using based on: [https://snapcraft.io/mjpg-streamer](https://snapcraft.io/mjpg-streamer)

---

