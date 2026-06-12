---
title: "select timeout error when I play a video"
date: 2023-07-12
forum: General Help
---

### Post by coolboy6272 on 2023-07-12
I have an external camera from Sony. But when I use it for displaying video output, randomly sometimes it shows this error:



[ WARN:0@72.803] global cap_v4l.cpp:1119 tryIoctl VIDEOIO(V4L2:/dev/video0): select() timeout.


And the video output is freezed . Please help me with this.
Thanks

---

### Post by coolboy6272 on 2023-07-13
Pls say solutions &#128591;

---

### Post by Rubi1200 on 2023-07-26
Not sure I can help but will at least try and point you in the right direction.

1. have you checked the cable from the camera to the computer, have you tried another cable?
2. do you have the same problem if you try this on another computer?
3. what version of Ubuntu are you using?
4. what are the hardware specs. like RAM, graphics card etc.

The more information you give us, the easier it will be to try and help.

---

### Post by #&amp;thj^% on 2023-07-26
+1 to Rubi 1200 suggestions, the more info we get the better chance we have to help you.
Show this as well:
```
id -a

```
This is most often the problem, an example form mine:
```
uid=1000(me) gid=1000(me) groups=1000(me),4(adm),24(cdrom),27(sudo),30(dip),**[COLOR="#FF0000"]44(video),[/COLOR]**46(plugdev),114(lpadmin),115(sambashare),143(libvirt)

```
We are looking for the part in "red" if you do not see video listed, then run:
```
sudo usermod -a -G video $LOGNAME
```
Then after logout to see the change.

---

