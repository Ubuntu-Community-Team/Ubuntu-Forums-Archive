---
title: "Connecting Ubuntu hard drive to a new PC"
date: 2016-08-27
forum: General Help
---

### Post by tech291083 on 2016-08-27
Friends,

I have installed Ubuntu Desktop 16.04 LTS on one my hard drive as the only OS, and I have fully updated Ubuntu. This hard drive is only 4 months old and working fine. But in my own experience with Ubuntu, I have never had to install any driver after installing the same, and yes I use a normal PC, not for gaming etc. If I connect this hard drive to another PC and try to run the already installed and updated Ubuntu on it, will it run smoothly? Will it pick up the changes in a new set of hardware itself?

Thanks.

---

### Post by Dennis N on 2016-08-27
Best to try it out and see if it boots and runs as you would hope. Personally, I have tried this a couple of times with a Ubuntu that was installed on a USB HDD, moving it to another machine, and it did not work for me. You may have better luck than my limited experience.

---

### Post by tech291083 on 2016-08-27
> **Dennis N said:**
> Best to try it out and see if it boots and runs as you would hope. Personally, I have tried this a couple of times with a Ubuntu that was installed on a USB HDD, moving it to another machine, and it did not work for me. You may have better luck than my limited experience.

Well at least, you tried, I am yet to make any serious attempt. Thanks for sharing your own experience.

---

### Post by tech291083 on 2016-08-27
I just have to mention that I love the way Ubuntu just picks up all my drivers - LAN, chip-set, audio, video on its own, without making any fuss whatsoever. I have no dedicated graphics card to worry about though. Thanks.

---

### Post by Dennis N on 2016-08-27
Hope is not lost. Since that experiment was a couple of years ago, I just tried this again but using a different target machine and it booted and is working. The computers both have Intel CPU and graphics, but of different vintage.

---

### Post by grahammechanical on 2016-08-27
Are you using a proprietary video driver? Use System Settings>Software & Updates>Additional Drivers tab to switch to the open source video driver. Otherwise there may be a conflict with the video drivers if the new video adapter is from a different manufacturer to the old video adapter. Even if the manufacturer is the same the existing proprietary video driver may not have support for newer adapters. Your new system may need a newer proprietary video driver.

Best to use the open source video driver for the change over. The Ubuntu live session uses the open source video driver. 

Regards

---

### Post by tech291083 on 2016-08-27
> **grahammechanical said:**
> 
Are you using a proprietary video driver? Use System Settings>Software & Updates>Additional Drivers tab to switch to the open source video driver. Otherwise there may be a conflict with the video drivers if the new video adapter is from a different manufacturer to the old video adapter. Even if the manufacturer is the same the existing proprietary video driver may not have support for newer adapters. Your new system may need a newer proprietary video driver.



Hi grahammechanical,

I believe you are asking me to install the correct video drivers when I connect my hard drive, which has Ubuntu installed on it to a totally different PC by - System Settings>Software & Updates>Additional Drivers tab, right? And what is Ubuntu refuses to boot at all when connected to another PC? What are the options then, if any?

Normally, whenever I install Ubuntu Desktop version on my own hard drive/PC, I never install any drivers whatsoever, I only update Ubuntu on a regular basis, sometimes daily. And the very reason is that I do not have a dedicated graphics card. But the real reason, which might be a total stupidity on my part to say the least, is the fact that Ubuntu has always worked very well on my PC even if I just install and update it and ignore installing drivers of any sort whatsoever. I have always thought that Ubuntu has the required motherboard drives of all sorts in its latest releases, so why bother look somewhere else. Am I doing anything wrong by not installing motherboard drives for Ubuntu? Should I change my mindset? Please feel free to suggest the right thing.

> 
Best to use the open source video driver for the change over. The Ubuntu live session uses the open source video driver. 


I never knew that Ubuntu live session uses the open source video driver. This is really interesting. 

Thanks a lot. Regards.

---

### Post by yancek on 2016-08-27
If you are using a proprietary graphics driver on your current system and you move that harddrive to another computer and have very different hardware (graphics) then you can expect problems.  Not unsolvable.

You basically move the drive to the new PC, and correctly connect it then set it to first boot priority in the BIOS.  It should boot but not knowing anything about the hardware on either machine there is no way for anyone to give you any assurances.

---

### Post by wildmanne39 on 2016-08-28
It has been a long time before UEFI but I have done it three times without trouble but I always removed the proprietary drivers before I took the drive out of the computer to put it into a new computer.

In each case when I turned the new computer on it used the open source driver and booted and operated perfectly.

---

### Post by sudodus on 2016-08-28
> **Wild Man said:**
> It has been a long time before UEFI but I have done it three times without trouble but I always removed the proprietary drivers before I took the drive out of the computer to put it into a new computer.

In each case when I turned the new computer on it used the open source driver and booted and operated perfectly.
+1

(In addition to graphics, there might also be a proprietary driver for wifi.)

---

