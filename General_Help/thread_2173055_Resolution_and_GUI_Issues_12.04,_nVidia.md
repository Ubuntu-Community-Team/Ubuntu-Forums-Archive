---
title: "Resolution and GUI Issues 12.04, nVidia"
date: 2013-09-07
forum: General Help
---

### Post by Charles2531 on 2013-09-07
So I've been using Ubuntu for a few months now, but just today when I booted up my computer I got an unusual problem. The resolution has been changed to 640x480, and when I try to change it, it says there are no higher resolutions that I can use. I normally run Ubuntu at 1440x900. The biggest problem is now that the majority of the Ubuntu GUI is off-screen, and completely unusuable. The only thing that I can think of that could have caused this is a video driver update. I have read about solutions to my problem, but none have worked at all. 

Luckily, I have a spare installation disk, but I have a lot of important files that I don't want to lose that I hadn't gotten around to setting up backups for yet. Is there a way that I could reinstall Ubuntu without losing these files?

I am using a nVidia GeForce GTX 560 on Ubuntu 12.04.



[FONT=Verdana]UPDATE: I downloaded the nVidia driver 325, and the resolution went back to normal. However, the sidebar and top menu are still missing.[/FONT]

---

### Post by QDR06VV9 on 2013-09-07
> **Charles2531 said:**
> So I've been using Ubuntu for a few months now, but just today when I booted up my computer I got an unusual problem. The resolution has been changed to 640x480, and when I try to change it, it says there are no higher resolutions that I can use. I normally run Ubuntu at 1440x900. The biggest problem is now that the majority of the Ubuntu GUI is off-screen, and completely unusuable. The only thing that I can think of that could have caused this is a video driver update. I have read about solutions to my problem, but none have worked at all. 

Luckily, I have a spare installation disk, but I have a lot of important files that I don't want to lose that I hadn't gotten around to setting up backups for yet. Is there a way that I could reinstall Ubuntu without losing these files?

I am using a nVidia GeForce GTX 560 on Ubuntu 12.04.
Im Assumeing you already have installed nVidia driver 325 for xedggers ppa?

---

### Post by carlwsnyder on 2013-09-07
First, boot with a Linux Live disk.  If your display can be set to 1440x900, the problem is your video settings in your installation, not your video driver necessarily.  If your display is normal with the Live disk, you can probably also back up all of your files with the Live disk.  If you have a separate /home partition, you can re-install Ubuntu without ever affecting your data files.

It could also be your cable/connection either on your computer, or on your display if the Live desktop is also only able to give you 640x480, or another hardware problem.

---

### Post by Charles2531 on 2013-09-07
I tried this one again, and it actually worked now... to an extent. Now the resolution is fine, but the Ubuntu gui is still missing.

---

### Post by carlwsnyder on 2013-09-08
Did you check that the GUI elements are simply 'hidden' off screen?  There is a setting in your GUI to hide the menu and top bar to keep it out of the way when using a netbook/limited display.

---

