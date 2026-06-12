---
title: "Can't change resolution: some commands not working in terminal."
date: 2013-10-08
forum: General Help
---

### Post by Kyle_Rhyne on 2013-10-08
Hello, I'm new to using ubuntu and just finised installing 13.04 amd64 in my machine. First thing I noticed is that more than half of the icons on the left of my screen are missing, and the only resolutions offered by ubuntu are 1920x1080 and 1024x720 (both 16:9). I also believe that there should be some things on the top of the screen that are missing as well. 

I looked on the internet for some solutions already and have had people tell me to use XrandR or gksudo nvidia-settings. Neither of those incited any sort of visible response. If anybody can help me I would greatly appreciate it.

EDIT: Just discovered; My windows 7 will not boot now.

---

### Post by grahammechanical on 2013-10-08
When you installed Ubuntu did you tick the box to install third party software? If you did then you installed a proprietary video driver at the same time. Is your video adapter a Nvidia card or some other? If you have a Nvidia card and are using a Nvidia driver then you will find a Nvidia settings utility in the Dash. That is the one to use. In System Settings we have a Displays utility that is only activated if we are using the open source (Nouveau) video driver.

Remember, a modern OS like Linux/Ubuntu does not set the screen resolution from a configuration file. When Ubuntu loads it searches the monitor for Extended Display Identification Data (EDID) and sets the screen resolution to the optimum setting chosen by the monitor manufacturer. It is not sensible to run a monitor outside of the optimum settings chosen by the manufacturer. It is your choice. But this is why Ubuntu limits certain actions.

What things do you think are missing from the Launcher and the global menu? What did you expect to find there?

Regards

---

### Post by Kyle_Rhyne on 2013-10-08
I did install the third party software, and i'm using two evga geforce 570s that were set up for SLI in windows. I do not know which driver to use since there are so many in the list along with the open source driver. Should have noted that by "missing" I meant that the icons and top of the screen is cut off from the rest of the world. I can click up there to see that there are menu dropdowns, but i can't see what i'm selecting. I'll try loading different drivers and moving the display around with my television remote and reply with results if any. 

Still cant get windows 7 to boot again. Before I installed Ubuntu I was running a raid 10 volume of 4 hdd. Now when I get to the grub boot loader and select the Windows 7 (loader) it shows the windows logo screen and then a blue screen displays for a fraction of a second and the system restarts.

---

### Post by Kyle_Rhyne on 2013-10-08
I must be missing something here but I still have no idea how to make the screen fit my television. I'm using the mini-hdmi out if it makes a difference.

---

### Post by Kyle_Rhyne on 2013-10-08
OK. I was able to get the NVIDIA X Server Settings window to display more than just one tab. Now Whatever custom resolution I set, I still cannot get the display to show me the whole desktop. PLEASE somebody help!

---

### Post by CatKiller on 2013-10-09
It's called overscan. It's because you're using a television.

---

