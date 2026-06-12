---
title: "Nvidia driver not working"
date: 2015-01-30
forum: General Help
---

### Post by Xanthius on 2015-01-30
I need help with an issue caused by the xorg-edgers ppa updating my video drivers to the 364.16 as of now I'm having a black login screen.
While I realize the edgers ppa is the latest of the latest drivers, it's been great by giving me FPS improvements with each update up until now..
I've been able to get things working by doing the "sudo prime-select intel" and restarting lightdm by my nvidia card isn't working anymore.
I was able to figure this one out by using lynx, I have no alternative backup system.

I've tried to purge nvidia*, installing the nvidia-330, 331, 340 and again the 346 but with no luck and I seek assistance..

System configuration:
I have the Dell XPS L702X, it has a Intel card (hd3000) with nvidia 550M.
The internal display and the MDP (Mini display port) is directly connected to the intel card.
The HDMI port however is directly connected to the nvidia card meaning you can't extend your desktop if your monitor is connected to the HDMI port while the nvidia card is disabled.

My setup:
My internal display is enabled, my secondary screen is connected on the MDP (Mini display port) set to extended mode.


Error logs:
[http://pastebin.com/JHxg4gni](http://pastebin.com/JHxg4gni) (xorg.8.log) (nvidia 331 driver that used to work)
All the other logs refer to the same thing, no screen found.
However as every update backups the "xorg.conf" file in /etc/X11/xorg.conf.YYYYMMDD I've tried to overwrite with every old config file I had and none of them worked.

So.. while I've been using Ubuntu full time for over a year I'm just not experienced enough to resolve this issue cause I don't know where it's going wrong.
Even with the latest edge drivers installed, the system software center wasn't even enlisting those drivers as its only listing 304, 331 and 340.

Please help me, im getting 7 FPS in games on windowed mode where I used to beable to get 70 on fullscreen.
If I'm not able to resolve this issue soon, I'll do a full re-install and I really want to avoid this.

```
lspci | grep -i vga
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation GF106M [GeForce GT 550M] (rev ff)
```

cat /var/log/dpkg.log | grep '2015-01-31' > [http://pastebin.com/vgjkuX4h](http://pastebin.com/vgjkuX4h)
cat /var/log/dpkg.log | grep '2015-01-30' > [http://pastebin.com/wMDsdgSh](http://pastebin.com/wMDsdgSh)

---

### Post by sandyd on 2015-01-30
Are you having the same error messages as the ones in [https://github.com/Bumblebee-Project/Bumblebee/issues/580#issuecomment-67444409](https://github.com/Bumblebee-Project/Bumblebee/issues/580#issuecomment-67444409)?

If so, try the fixes there.

---

### Post by Xanthius on 2015-01-30
Well, the error message is the same yes but Bumblebee has been pretty much obsolete with Ubuntu 14.04 with nvidia's 319+ drivers as prime-select comes from the nvidia-prime package pretty much out of the box.
While I did what you asked, it does not really resolve the issue.

The bumblebee way loads by default from the intel card and you can select which application with primusrun you want to run from your nvidia card.
So if I would try to launch a game that has a launcher on its own, I can primusrun the launcher but since the launcher launches the game it decides to run on my intel card anyways.
This didn't happen when I forced bumblebee to launch from my nvidia card at login, but that is not good for a computer as temperatures were high even when doing nothing.

With the native nvidia drivers that came with ubuntu 14.04 it completely took bumblebee out of the equation and things were good. Much higher FPS and temperatures/voltages were regulated when not using 3d applications on the profile in nvidia-settings.

---

### Post by john407 on 2015-05-28
Any resolution to this? I have the same configuration with the same issue.

---

### Post by ccbmailroom on 2015-05-28
I found a page with a whole bunch of drivers for AMD processors at

[http://support.amd.com/en-us/download/desktop?os=Ubuntu%20x86%2064](http://support.amd.com/en-us/download/desktop?os=Ubuntu%20x86%2064)

But I'm not sure which one works with my HP 15-g012dx.  I mean really, Windows 8 had better video quality before I installed Ubuntu 14.04.  Any help on this?

---

### Post by ccbmailroom on 2015-06-06
Okay, for my **HP 15-g012dx **, I did use the driver AMD Catalyst&#8482; 15.5 Proprietary Ubuntu 14.04 x86_64 Video Driver for Graphics Accelerators on the "https://support.amd.com/en-us/download/desktop?os=Ubuntu%20x86%2064" page so the visuals of the desktop work fine.  I cannot view any videos on Facebook, nor watch one of my favorite streaming websites twitch.tv so I guess Ubuntu does not support Flash anymore.  Hope that helps anyone that finds this post.

---

### Post by ccbmailroom on 2015-07-12
Did my third reinstall of Ubuntu 14.04 of this summer this morning because of update crashing.  I did notice on this most recent install install I took a photo of it with my mobile phone.  Here's what a popup says mid install:

"Running the "unity" desktop environment is not fully supported by your graphics hardware.  You will maybe end up in a very slow environment after the upgrade.  our advice is to keep the LTS version for now.  For more information see [http://wiki.ubuntu.com/X/Bugs/UpdateManagerWarningForUnity3D](http://wiki.ubuntu.com/X/Bugs/UpdateManagerWarningForUnity3D) Do you still want to continue with the upgrade?"

There is a Yes/No button below that.  More than likely that's why video editing is not possible in Ubuntu on an HP AMD A8 laptop, (possibly why the updates lock up / crash so often).  The video driver I referenced above is the best one I could find for this laptop.

*** Also no video drivers from [http://support.amd.com/en-us/download/desktop?os=Ubuntu%20x86%2064](http://support.amd.com/en-us/download/desktop?os=Ubuntu%20x86%2064) work anymore so now that the un-updated graphics look like crap.  yay Ubuntu!  (My personal favor to Ubuntu and AMD developers, please create supported architecture for HP AMD laptops.  I miss using my reliable Gateway computer years ago!!!!)

---

### Post by ccbmailroom on 2015-07-16
The laptop crashed again Monday night of this week trying to update flash.

I just haven't got the support I've needed to keep this laptop running Ubuntu.  I've had a go at it but it just hasn't worked out.  Thank you to those who have helped with suggestions and ways of working things out but it's time to put Windows back on this laptop.

Thank you all again, I've really enjoyed it and appreciate all of the help.  Thank you tremendously.

Botch

---

