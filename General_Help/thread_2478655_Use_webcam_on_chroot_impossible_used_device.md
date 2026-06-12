---
title: "Use webcam on chroot impossible: used device"
date: 2022-09-01
forum: General Help
---

### Post by gbsatti on 2022-09-01
Hello !
I thank any one who agrees to help me for solving my problem.
I don't wanted to cause damage to my initial root environment, so i decided to use chroot and use my webcam camera. On my initial root, i can find video0 on ```
/dev/sam/video0
```

Here is what i did:

```
mount /dev/sda1 /mnt/core
```
Then i installed ubuntu 15.04 vivid (the last that supports my kernel) on /mnt/core
After that:
```
mount --bind /dev /mnt/core/dev
mount -t proc /proc /mnt/core/proc
mount -t sysfs /sys /mnt/core/sys
mount -t devpts devpts /mnt/core/dev/pts

```
then i use chroot: 
```
chroot /mnt/core /bin/bash
```
Everything is fine now. I used mknod to create video node:
```
mknod /dev/video0 c 81 0
```
and chmod: 
```
sudo chmod g+rw /dev/video0
```
Then i installed motion to get access to my camera (after adding old repos in sources.list):
motion i installing fine: no errors.
But when i start motion, here is what i get:
```
Error selecting input 0 VIDIOC_S_INPUT.
``` and also ```
Closing video device /dev/video0
``` and sometimes fatal error concerning /dev/video0. In 192.168.1.20:8081 i have a grey screen: unable to find video.
I thought it was only motion, so i tried with other apps, particulary i tried to shoot a photo with fswebcam, here is what i get:
 ```
--- Opening /dev/video0...
Trying source module v4l2...
/dev/video0 opened.
No input was specified, using the first.
Error selecting input 0
VIDIOC_S_INPUT: Device or resource busy
```
I killed motion and according to last error message, i thought my video0 device was used by another program. I used this to show who is using video0 ```
sudo fuser /dev/video0
``` but nothing is using my device video0.
After one week, i still cannot find how i can use my video0 device on chroot. Maybe the device is used by initial root, but i don't know if i can kill process in initial root and how i can find them.
Thank you in advance for any help :)

---

### Post by TheFu on 2022-09-01
I have no idea what you are trying to accomplish, but processes show up in the process table.  The 'ps' command shows them.  You can also use 'lsof' to see which processes have a file opened.  These are basic Unix commands, so I expect you can find a guide or read the manpage for the options needed to get the information you seek.

---

