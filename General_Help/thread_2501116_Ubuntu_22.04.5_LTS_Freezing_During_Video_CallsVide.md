---
title: "Ubuntu 22.04.5 LTS Freezing During Video Calls/Video Playback – Audio Continues, No I"
date: 2024-09-23
forum: General Help
---

### Post by dispatuble on 2024-09-23
I'm encountering a frustrating issue with my system that has been  running fine for years, but recently it has started freezing randomly  once a day. Here's my setup:

 OS: Ubuntu 22.04.5 LTS CPU: 11th Gen Intel i7-1165G7 @ 2.80 GHz RAM: 32GB Graphics: Intel TigerLake-LP GT2 Laptop: HP ProBook 450 G5

My system freezes unexpectedly, and the problem seems to happen  during video calls (Zoom, Meet, etc.) or when watching videos on social  media (both Chrome and Firefox). 
The symptoms are as follows:

 The screen freezes, but I can still hear audio and, in the case of  video calls, I can continue talking with others, though the screen  remains stuck. Neither the external USB mouse/keyboard nor the internal  keyboard/trackpad respond. Ctrl+Alt+Delete does nothing. After waiting 10&#8211;15 minutes, sometimes the system starts responding  again, but most of the time, I have to perform a hard reboot. I checked system temperatures using sensors around crash times, and  everything seems to be within normal ranges. Given that audio continues working and the screen remains stuck  visually, I suspect it's something related to the graphics card or a  driver issue. Does anyone have suggestions for troubleshooting or fixing  this?
 Any help would be much appreciated! Thank you!

---

### Post by him610 on 2024-09-25
Post results between code tags please,
```
inxi -bmxz

```

---

### Post by marekduda on 2024-09-27
If the audio&#8217;s still working, but the screen freezes, it def seems like a graphics [issue]("https://cardetailingfargo.com/"). Since you&#8217;ve got Intel graphics, you might want to check if your iGPU drivers are up to date, especially since TigerLake stuff can be a bit finicky on Linux.
Also, maybe try disabling hardware acceleration in both Chrome and Firefox. Sometimes that messes with video playback, and it could be what&#8217;s freezing your screen. If it still happens, check the logs (dmesg, syslog, etc.) around the time of the freeze to see if any errors pop up. Could give you more clues on what's going wrong. Worst case, you could test a different kernel version to see if that stabilizes things.

---

### Post by ActionParsnip on 2024-09-27
You may want to make sure you have the latest BIOS
Latest is 01.28.00 Rev.A dated May 13, 2024

---

### Post by TheFu on 2024-09-27
Besides checking the things listed above, all good ideas, look at the system log files for any hardware issues.  Google "ubuntu log files" if you don't know how.

---

### Post by vmpx on 2024-10-31
Try nomodeset parameter in GRUB.

---

