---
title: "Added a GeForce4 MX480 graphics card and Ubuntu broke ..."
date: 2017-03-10
forum: General Help
---

### Post by michael351 on 2017-03-10
I have 16.04 loaded on an old Pentium 32bit machine. It was an experiment to learn more about Ubuntu on one of my old boxes.
I decided to add a GeForce4 MX480 AGP graphics card to see if I can get better 2D graphics response from the windows.

After adding the card - nothing - the port worked, but was using the existing Nouveau drivers. 

So i decided to update the graphics with nvidia and broke everything - Ubuntu would not boot (kernal panic)

Not a big deal since this is an experiment anyway - I re-loaded Ubuntu but with the updates and 3rd party drivers selected. I had to do a boot-repair to fix Grub (I always have to do that) and now can't get it to boot at all (Kernal panic). 

I wonder if I need to reload the OS with no updates checked and try to install the drivers one at a time?

---

### Post by Bucky Ball on 2017-03-10
> **michael351 said:**
> I wonder if I need to reload the OS with no updates checked and try to install the drivers one at a time?

For your situation and any other install, this is best. Leave them unticked. No updates, no third-party proprietary drivers during install. Once the OS is installed and up and running, do an update then open 'Software and Updates> Other Software' and tick 'Canonical Partners Repo'. 

Update once more (which should happen when you leave that GUI) then check 'Additional Drivers' for a graphics driver (don't download from outside the official repositories, including from NVidia). If there is a driver with 'proprietary, tested', install that and reboot.

Have you tried booting with the 'nomodeset' option? During install, when you get to the purple screen with the icon at the bottom, hit any key. That should take you to a menu where you can hit F6 and a menu will pop up. Choose 'nomodeset' and proceed. 

You can also add nomodeset at a regular boot by choosing the kernel you want to boot but hit 'e' to edit the kernal line. Add 'nomodeset' at the end of the line that ends with 'quiet splash'. Follow instructions at bottom of screen to save and continue.

---

### Post by michael351 on 2017-03-11
I have a kernal fault and can't get past that - so I'll have to re-install the OS. But this time I will follow your suggestions above!
I'll post how it works out later today.

---

### Post by mikewhatever on 2017-03-11
I'd go with Xubutnu or Lubuntu on an old machine like that. Ubuntu with Unity is very nice on a new PC, but can be too much for GeForce4 era hardware.

---

### Post by Bucky Ball on 2017-03-11
> **mikewhatever said:**
> I'd go with Xubutnu or Lubuntu on an old machine like that. Ubuntu with Unity is very nice on a new PC, but can be too much for GeForce4 era hardware.

+1. I haven't used anything but Xubuntu (or close enough to it!) for years on all my machines, puny or monolithic.

---

### Post by michael351 on 2017-03-11
Bummer ... I'm really hosed for some reason.

I re-installed Ubuntu 16.04 from scratch using my ISO disk.
It installed as normal.

When I re-booted, the system went into Grub Rescue (been there each time).
so I loaded the ubuntu disk and downloaded boot-repair (as I have done before) and ran that.
It worked normally, but when I rebooted, grub rescue still came up.

something's not right. I have done this on this machine before (going from 14 to 16) with no problem.

Any suggestions?

(I'll rerun boot-repair and pastebin the summary. It looked normal to me)

---

### Post by mörgæs on 2017-03-11
You are already receiving suggestions, first of all switching to a lighter Buntu than Ubuntu.

---

### Post by michael351 on 2017-03-11
ubuntu worked fine before ... so i am just trying to get it back again the way it was.

here is the pastebin from boot-repair ...

[http://paste2.org/NpKjCdsn](http://paste2.org/NpKjCdsn)

If I can't get this to work - then I'll try Xbuntu ...

---

### Post by michael351 on 2017-03-11
> **mörgæs said:**
> You are already receiving suggestions, first of all switching to a lighter Buntu than Ubuntu.

I installed Xubuntu next to ubuntu and did a boot-repair - which worked this time.
But when Grub loaded it showed two copies of Ubuntu!? no Xubuntu. I was able to load ubuntu like I used to , but now that I have played with Xubuntu, it's much better for my old machine (pentium + GeForce4 MX480).

I'll have to reload Xubuntu and just erase the disk from scratch. ... slowly getting to the MX480 drivers ...

---

### Post by michael351 on 2017-03-11
> **Bucky Ball said:**
> For your situation and any other install, this is best. Leave them unticked. No updates, no third-party proprietary drivers during install. Once the OS is installed and up and running, do an update then open 'Software and Updates> Other Software' and tick 'Canonical Partners Repo'. 

Update once more (which should happen when you leave that GUI) then check 'Additional Drivers' for a graphics driver (don't download from outside the official repositories, including from NVidia). If there is a driver with 'proprietary, tested', install that and reboot.

Have you tried booting with the 'nomodeset' option? During install, when you get to the purple screen with the icon at the bottom, hit any key. That should take you to a menu where you can hit F6 and a menu will pop up. Choose 'nomodeset' and proceed. 

You can also add nomodeset at a regular boot by choosing the kernel you want to boot but hit 'e' to edit the kernal line. Add 'nomodeset' at the end of the line that ends with 'quiet splash'. Follow instructions at bottom of screen to save and continue.

I was able to load Ubuntu and add the Canonical Partners Repo .. when I searched for additional drivers, none showed up. Anything else to try?  thanks

---

### Post by mörgæs on 2017-03-12
It would surprise me a lot if closed source drivers are available for such an old graphics card. My guess is that the Nouveau drivers are all there are (and they are not that bad!) 

If you like Xubuntu then [Xubuntu Core]("https://xubuntu.org/news/introducing-xubuntu-core/") might be even faster.

---

### Post by Yellow Pasque on 2017-03-13
> **mörgæs said:**
> My guess is that the Nouveau drivers are all there are

Correct. Geforce4 is too old for proprietary nvidia driver. Nouveau driver should work "out of the box" and trying to install other video drivers will lead to pain and problems.

---

### Post by Yellow Pasque on 2017-03-13
> **michael351 said:**
> So i decided to update the graphics with nvidia and broke everything - Ubuntu would not boot (kernal panic)

[https://ubuntuforums.org/showthread.php?t=2354602&p=13615738#post13615738](https://ubuntuforums.org/showthread.php?t=2354602&p=13615738#post13615738)
LOL. I just realized that last week I told this user not to install nvidia drivers and that Unity would be slow. So what does user do? Installs Ubuntu/Unity and tries to install nvidia driver. Why do I even waste my time? ](*,)

---

