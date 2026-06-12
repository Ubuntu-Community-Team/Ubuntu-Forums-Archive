---
title: "Disk annoyance bottleneck: Is it hardware or kernel related?"
date: 2017-12-24
forum: General Help
---

### Post by lectra on 2017-12-24
Recently, I have been starting to have a significant performance bottleneck overall with occasional "attempted read outside of hda" errors on boot. I noticed this the next boot after a kernel update about a month ago. At first, I thought that I just happened to be having a hardware issue at first, and more specifically, my cooling fan may have gone out since I no longer noticed the warm breeze out the side and the problem would be most notably after the system has been running awhile. (It didn't). I verified inside the case and took the opportunity to button down a couple things that were coming loose, such as the lid hinges. I then installed Psensors and found that my processor was holding at 50 to 60 degrees C whether idle, browsing, or playing Unreal. Higher than I like but I hear an AMD C-50 is happiest there. Hard disk (suspected cause) is staying between 20 degrees C to 45 degrees C. This is on a Toshiba Satellite C655G-S5200 which has been upgraded to 8GB ram from 2GB three or four months ago.  Thing is, I don't hear the hard disk acting up.  As I troubleshoot, what would I look for to determine if the SATA hard disk or the kernel is the holdup?

Oh. I forgot to mention I'm running Kubunto 16.04 LTS.

---

### Post by oldos2er on 2017-12-24
Have you run smartctl on the disk? Might be wise to check.

[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

---

