---
title: "Resizing desktop with lcd tv"
date: 2008-02-21
forum: General Help
---

### Post by coopar on 2008-02-21
Hi, I've recently installed Ubuntu on a pc connected to an LCD tv but am having problems resizing desktop to fit onto screen. After installation and installing nvidia drivers through Envy the desktop spills over the edge of the screen making it difficult to work with it - close button is out of view, control panel along bottom is barely visible. Have messed about a bit but being a complete noob on linux I am struggling on how to resize the desktop. Anyone help. 

Thanks,

Alex

---

### Post by phrawzty on 2008-02-21
It sounds like you're trying to use a resolution which is too large for your display (the TV).  Try adjusting your resolution, and seeing if that helps :

System > Preferences > Screen Resolution

---

### Post by overdrank on 2008-02-21
> **coopar said:**
> Hi, I've recently installed Ubuntu on a pc connected to an LCD tv but am having problems resizing desktop to fit onto screen. After installation and installing nvidia drivers through Envy the desktop spills over the edge of the screen making it difficult to work with it - close button is out of view, control panel along bottom is barely visible. Have messed about a bit but being a complete noob on linux I am struggling on how to resize the desktop. Anyone help. 

Thanks,

Alex

HI and welcome, have you tried using the nvidia-settings to adjust the resolution? Use this command in the terminal located under applications, accessories. ```
gksudo nvidia-settings
```

---

### Post by coopar on 2008-02-22
Sorry, thanks for your help guys but its not a resolution issue. The desktop overscans on the lcd screen so some of the screen goes off the edge. Have tried to see if the tv can be adjusted from the service menu but I dont think it can. The machine dual boots at the moment with Vista on it also and the nvidia conrol panel allows you to manually resize the desktop which obviously cures the overscan problem. However I dont have that luxury with linux. Have only just migrated to Ubuntu so am completely lost on this. My problem is that I dont know enough about the OS to find my way about easily, the learning curve is steep but I fully intend to stick it out. Hey I am having fun even with the problems!

Thanks for any info that may help.

coopar

---

### Post by UnixGeeK on 2008-07-19
I have the same exact problem, and it seems there is no solution to it yet. I'm connecting my tv via hdmi. I hope nvidia can improve the linux drivers in this area, as this is easily solved in Vista with the "resize desktop" feature.

---

