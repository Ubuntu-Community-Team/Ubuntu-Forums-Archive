---
title: "[SOLVED] nividia driver works in kubuntu, not ubuntu"
date: 2007-12-28
forum: General Help
---

### Post by snickers295 on 2007-12-28
how come the nividia driver works in kubuntu but not ubuntu?
when i enable it in ubuntu, it locks my screen resolution at 800x600 and i like 1280x1024 but it doesn't in kubuntu?

---

### Post by Kzin on 2007-12-28
Hmmm, it works for me.  What card do you have?

---

### Post by snickers295 on 2007-12-28
NVIDIA geforce2 ddr (generic)
the accelerated graphics driver works fine on kubuntu but locks screen resolution in  ubuntu

---

### Post by Kzin on 2007-12-28
Hmmm, maybe it is a video ram setting?
As per [http://ubuntuforums.org/showthread.php?t=364605](http://ubuntuforums.org/showthread.php?t=364605)
Or you may need to manually set up Horiz  and Vert in your xorg.conf....
As per [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/148089](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/148089)

---

### Post by Kzin on 2007-12-28
Actually there seems to be a lot of people having trouble with nVidia stuff... Consider trying using your ATI Radeon 9250?

:lolflag:

---

### Post by randavance on 2007-12-28
Happens with NVIDIAs I get the same problem with mine.

Hit alt+ctl+f1

this will pull up a different command line

log in

```
sudo dpkg-reconfigure xserver-xorg
```

put in your password

most of it is just hitting ok, but make sure when the list of card types come up choose "NV"

read everything carefully

restart when your done

you can also try installing the NVIDIA driver in the restricted drivers app from the system menu.

---

### Post by randavance on 2007-12-28
> **Kzin said:**
> Actually there seems to be a lot of people having trouble with nVidia stuff... Consider trying using your ATI Radeon 9250?

:lolflag:

NVIDIAs are actually wonderful for Linux, you just need to have x configured correctly.

A lot of the time its because people will be running two graphics cards, i'm personally running the integrated dell card and the nvidia which was the upgrade, this tends to be where x gets confused.

---

### Post by Kzin on 2007-12-28
> **randavance said:**
> NVIDIAs are actually wonderful for Linux, you just need to have x configured correctly.

A lot of the time its because people will be running two graphics cards, i'm personally running the integrated dell card and the nvidia which was the upgrade, this tends to be where x gets confused.

:lolflag:

No argument there, never had a problem with nVidia cards & linux (knock on wood, I haven't had anything other than nVidia since 2002 or so).  Was just joking because I looked through his previous posts and he was having trouble with the ATI in Kbuntu.  Seems that quite a few others have had problems with nVidia/Ubuntu, tho...  Also have a friend complaining about graphics performance outright in Ubuntu (works better in Kbuntu for him??) and that his integrated Intel out performs his nVidia.  Don't have his exact specs on hand, but perhaps I'll create another thread about it in a more relevant location when I next talk to him about his hardware.

---

### Post by snickers295 on 2007-12-28
none of those solutions work and neither does my ati card.

---

### Post by snickers295 on 2008-01-02
odd, i messed my hard drive up (nothing new, i like going though and playing with system files) so i installed ubuntu and the driver worked just fine.

---

### Post by Kzin on 2008-01-03
> **snickers295 said:**
> odd, i messed my hard drive up (nothing new, i like going though and playing with system files) so i installed ubuntu and the driver worked just fine.

Odd indeed.  Well, glad its working for ya now!  :)

---

### Post by snickers295 on 2008-01-03
ok i feel stupid now.
i had the 3d acceleration driver enabled but, i didn't have the "nVida" driver chosen in screens/graphics. 
thanks all

---

