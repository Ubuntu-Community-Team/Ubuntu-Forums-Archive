---
title: "xawtv gives XF86DGANoDirectVideoMode"
date: 2007-01-09
forum: General Help
---

### Post by madubuntuer on 2007-01-09
xawtv is detecting my video card properly but give that error when I try starting xawtv.

root@ubuntu:/home/s# xawtv -device /dev/video0
This is xawtv-3.94, running on Linux/x86_64 (2.6.15-23-amd64-generic)
X Error of failed request:  XF86DGANoDirectVideoMode
  Major opcode of failed request:  136 (XFree86-DGA)
  Minor opcode of failed request:  1 (XF86DGAGetVideoLL)
  Serial number of failed request:  65
  Current serial number in output stream:  65

root@ubuntu:/home/s# xawtv -hwscan
This is xawtv-3.94, running on Linux/x86_64 (2.6.15-23-amd64-generic)
looking for available devices
port 57-57
    type : Xvideo, image scaler
    name : NV17 Video Texture

port 58-89
    type : Xvideo, image scaler
    name : NV05 Video Blitter

/dev/video0: OK                         [ -device /dev/video0 ]
    type : v4l2
    name : BT878 video ( *** UNKNOWN/GENER
    flags: overlay capture tuner

---

### Post by kerinin on 2007-01-27
same problem here
```

kerinin@simon:~$ xawtv
This is xawtv-3.95, running on Linux/x86_64 (2.6.17-10-generic)
X Error of failed request:  XF86DGANoDirectVideoMode
  Major opcode of failed request:  137 (XFree86-DGA)
  Minor opcode of failed request:  1 (XF86DGAGetVideoLL)
  Serial number of failed request:  65
  Current serial number in output stream:  65
```

---

### Post by MJN on 2007-01-30
Have you guys got Nvidia graphics cards, and using the nvidia-glx drivers? I think I've read somewhere that Nvidia don't support DGA anymore.
 
Try running **xawtv -nodga -device /dev/video0**
 
Mathew

---

### Post by lukew on 2007-03-15
> **MJN said:**
> Have you guys got Nvidia graphics cards, and using the nvidia-glx drivers? I think I've read somewhere that Nvidia don't support DGA anymore.
 
Try running **xawtv -nodga -device /dev/video0**
 
Mathew

Thanks; worked a treat!

Luke

---

### Post by darkhut on 2007-07-08
wow..thank you for the nice fix..I should have looked in the man but eh..anyway..ubuntu is so nice with noobs comparing to other distributions:)

---

### Post by SheffieldBlade17 on 2008-05-20
I have the Nvidia card and tried that line and this is what I get:

 xawtv -nodga -device /dev/video0
This is xawtv-3.95.dfsg.1, running on Linux/x86_64 (2.6.24-16-generic)
xinerama 0: 1280x800+0+0
X Error of failed request:  XF86DGANoDirectVideoMode
  Major opcode of failed request:  136 (XFree86-DGA)
  Minor opcode of failed request:  1 (XF86DGAGetVideoLL)
  Serial number of failed request:  13
  Current serial number in output stream:  13
v4l-conf had some trouble, trying to continue anyway
Warning: Missing charsets in String to FontSet conversion
Warning: Cannot convert string "-*-lucidatypewriter-bold-r-normal-*-14-*-*-*-m-*-iso8859-*,           -*-courier-bold-r-normal-*-14-*-*-*-m-*-iso8859-*,          -gnu-unifont-bold-r-normal--16-*-*-*-c-*-*-*,        -efont-biwidth-bold-r-normal--16-*-*-*-*-*-*-*,                 -*-*-bold-r-normal-*-16-*-*-*-m-*-*-*,                 -*-*-bold-r-normal-*-16-*-*-*-c-*-*-*,                         -*-*-*-*-*-*-16-*-*-*-*-*-*-*,*" to type FontSet
Warning: Missing charsets in String to FontSet conversion
Warning: Unable to load any usable fontset
Warning: Missing charsets in String to FontSet conversion
Warning: Unable to load any usable fontset
Error: Aborting: no fontset found

---

### Post by mathanr on 2008-07-08
thanks but no audio and no clear picture please help me and see my attachment of my tech draw on my tv tuner card

---

