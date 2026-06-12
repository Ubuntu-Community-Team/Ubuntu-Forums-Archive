---
title: "webcam not detected"
date: 2014-05-22
forum: General Help
---

### Post by monkeybrain20122 on 2014-05-22
I have just installed xubuntu 14.04  on my friend's old Sony Vaio laptop (VGN SZ320cp) to replace WinXP. 

Everything works except for the webcam. 
lsusb shows
```
Bus 001 Device 003: ID 05ca:1830 Ricoh Co., Ltd Visual Communication Camera VGP-VCC2 [R5U870]
```

I followed the instructions to install the r5u8x package from [http://askubuntu.com/questions/241965/ubuntu-does-not-detect-my-vaio-webcam](http://askubuntu.com/questions/241965/ubuntu-does-not-detect-my-vaio-webcam)
It compiled and installed with no problem and 
```
sudo r5u87x-loader --reload
[sudo] password for user: 
r5u87x firmware loader v0.2

Searching for device...
Found camera: 05ca:1830
Camera reports positive microcode state.
Camera reports microcode version 0x0100.
Not doing anything - camera already setup.

Successfully uploaded firmware to device 05ca:1830!
Reloading uvcvideo module...
Finished.

```

So it seemed the operation went through successfully. I have also added user to the video group.

But after reboot guvcview still doesn't pick up the webcam. Skype also complains that no device found. 

Please advise, thanks.

Edited: this is xubuntu 64-bit.

---

### Post by dannyboy79 on 2014-05-23
is it creating a video device node? check /dev/ for video0 or video1
```
ls -la /dev/ | grep video
```

---

### Post by monkeybrain20122 on 2014-05-23
Ok, it turns out that the r5u87x doesn't support this particular webcam (WDM) [http://www.arakhne.org/ricoh/](http://www.arakhne.org/ricoh/)

Tried to compile the r5u870 kernel module and got "error: no include path in which to search for stdint.h"
I reached the same impass as post #4  from this old thread [http://ubuntuforums.org/showthread.php?t=1802677](http://ubuntuforums.org/showthread.php?t=1802677)

Well will try to grab an old kernel and compile to see if I have any luck. If not will just tell the guy to buy a usb webcam for $5.

Edited:@dannyboy79
Thanks for the reply, I found one blog where a comment claims that the r5u87x works for this webcam (am away from that laptop so can't get the bookmark now). I will check again and reinstall the r5u87x (good that I have made a .deb) and post back before I go the old kernel route..

---

### Post by monkeybrain20122 on 2014-05-23
> **dannyboy79 said:**
> is it creating a video device node? check /dev/ for video0 or video1
```
ls -la /dev/ | grep video
```

Hi, this is what I got

```
$ ls -la /dev/ | grep video
crw-rw----   1 root video    10, 175 May 23 20:40 agpgart
crw-rw----   1 root video    29,   0 May 23 20:40 fb0

```

---

### Post by dannyboy79 on 2014-05-24
if there's no video device being created than I am guessing the module doesn't support that webcam

---

### Post by monkeybrain20122 on 2014-05-25
I installed kernel 3.2 from mainline and was able to compile and install the r5u870 kernel module without error, but all hell broke loose when running "sudo modprobe r5u870", the desktop disappeared and turned into a black screen full of texts, no problem booting back into the original kernel though.

So finally the only way that works for me is to install xubuntu 12.04 instead and compile r5u870 there. Cheese works, google hangout works but guvcview doesn't work and current version of skype doesn't work (but skype 2.1 does) 

Not sure why it didn't work in xubuntu 14.04 even with the right kernel version.

Here is the procedure (if you have a Ricoh r5u870  WDM webcam so the ru587x user space tools don't work)

Install *buntu 12.04,
get r5u870 from [https://code.google.com/p/r5u870/downloads/list](https://code.google.com/p/r5u870/downloads/list)
Extract.
Open the file r5u870/usbcam/usbcam_fops.c., delete the line ".compat_ioctl    = v4l_compat_ioctl32," and save.
Open a terminal, cd into the extracted folder and run
```

make
make install
sudo modprobe r5u870
```
Reboot, that's it.
Now current version of skype doesn't work, video test only shows a black box. But skype 2.1 does work, download it from the links in the third post here [https://code.google.com/p/r5u870/issues/detail?id=8](https://code.google.com/p/r5u870/issues/detail?id=8)

Now of course a kernel update will wipe it out, so would have to log into the correct kernel version for this to work eventually.

---

### Post by monkeybrain20122 on 2014-05-28
Just found out there is a problem with skype 2.1. I can make video out calls with no problem but not receiving calls. It will ring when calls arrive, no problem answering but video doesn't start and it doesn't pick up video  from incoming callers either. After a few minutes with audio only connection just drops.

I don't expect to find a solution for this, it is a very old and deprecated version of skype, so I am not starting a new thread. But then you never know, there are some amazing people in this community. some people may know how to fix this :)

Anyway, if this doesn't get resolved I am going to tell my friend either to make out calls only or dish out $10 for a bloody usb webcam, or dump skype and switch to google hang out which works perfectly even with this cam.

---

