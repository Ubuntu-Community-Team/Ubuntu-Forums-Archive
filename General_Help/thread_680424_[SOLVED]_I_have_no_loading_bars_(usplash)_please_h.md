---
title: "[SOLVED] I have no loading bars (usplash?) please help!"
date: 2008-01-27
forum: General Help
---

### Post by Bodsda on 2008-01-27
Hi, during my boot sequence, just after the grub os selection i am presented with a message "Video mode not supported" where the loading bar should be. I have always had this problem, except from when i use the live cd. I am running Ubuntu 7.10 Gutsy amd64 and have a Nvidia 7600gt 

Please help!

---

### Post by ushimitsudoki on 2008-01-27
(As discussed in #ubuntu)

I have the same issue on 7.10 amd64 with NVIDIA 8800GTS 512.

I am almost sure it is something to do with usplash not being able to use the video card.
Removing "splash" from /boot/grub/menu.lst results in never "losing" the monitor signal, but of course you don't get a graphical loading screen.

Also, I was unable to use the LiveCD to install on the box, because of the video card, and had to use the alternate install. I am guessing these issues are related.

Everything is fine once the NVIDIA drivers are loaded.

---

### Post by danwood76 on 2008-01-28
Have you tried modifying the usplash config file?

Ive found that if you install with an ati or nvidia card it defaults to 1280x1024 which is out of range on some peoples cards before the proper drivers have loaded.
And obviously once the drivers load properly it can do the other resolutions.

Try ```
 sudo gedit /etc/usplash.conf
```
and setting the xres and yres to something lower.
The safest bet is probably VGA res,
```

# Usplash configuration file
xres=640
yres=480

```
But I would have thought setting this to whatever your monitor can support should work.

regards,
Danny

---

### Post by ushimitsudoki on 2008-01-28
Just a note that this did -not- work for me.

I tried both 640x480 and 1280x720 (because that is the resolution my monitor is when the BIOS graphic screen displays).

---

### Post by Battie on 2008-01-28
Hi!

This fix did not work for me either.  I can't find the thread that explains this fix, but this worked for me:

[http://ubuntuforums.org/showpost.php?p=3635667&postcount=9](http://ubuntuforums.org/showpost.php?p=3635667&postcount=9)

IIRC, these framebuffers are blacklisted for a reason, but I've suffered no ill effects from it.

As others have commented, vesa16fb may not be necessary, and the nvidia one probably should be enabled too.

Good luck!

---

### Post by gwpritch on 2008-01-28
Try 1280x800

---

### Post by Bodsda on 2008-01-28
gwpritch your half way there..,.lol,.,.i now get the unloading bar but not the loading bar, e.g when i restart/shut down my machine i see the bars but i dont see them when i boot up the machine

---

### Post by gwpritch on 2008-01-28
That's odd!
The other thing you could try is to:

```
sudo gedit /boot/grub/menu.lst
```

and remove the 'quiet' and 'splash' options from the kernel boot line and defoptions.

This will remove usplash completely.  See if that speeds things up for you.

---

### Post by danwood76 on 2008-01-28
I noticed this same thing on a nvidia based machine at work today.
I think maybe that the nvidia drivers/cards dont support the usplash before their drivers properly load.

I will have a play with the machine at work tomorrow to see if  can get the splash working.

regards,
Danny

---

### Post by Bodsda on 2008-01-28
[http://ubuntuforums.org/showthread.php?t=454392&page=3](http://ubuntuforums.org/showthread.php?t=454392&page=3)

SOLVED 

Just add 1 line to the file in that link,.,. cheers guys

---

### Post by gwpritch on 2008-01-28
I have a nvidia card and it worked fine once the screen res was set probably. The bug seems to be in detecting the proper res in the first place...seems to be a common problem in the forums. Mine was detected as 1280x1024 which my laptop doesn't support. Changing it to 1280x800 fixed it all...slow boot, usplash (boot-up and shutdown) and all.

---

