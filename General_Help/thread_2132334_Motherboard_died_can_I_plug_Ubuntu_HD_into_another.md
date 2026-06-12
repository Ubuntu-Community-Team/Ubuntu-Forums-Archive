---
title: "Motherboard died can I plug Ubuntu HD into another model?"
date: 2013-04-04
forum: General Help
---

### Post by virgodave61 on 2013-04-04
My motherboard died, it was an EMachine and this seams to be a typical problem with them. I'm not sure if I should replace the motherboard or just by something better. My question is, if I plug my HD into a different motherboard will it recognize and adjust to the new motherboard(I know Windows will throw up, if you do this), or do I have to reinstall Ubuntu and if so can I install over the old installation, what is involved?
Thanks,
Dave

---

### Post by doubled on 2013-04-04
I've had limited experience plugging an HD into a different MB with different video, sound, and MB resources. The times I have done it have been met with success, perhaps with an adjustment to the video so the desktop looks right. It's NOT likely to work if you are moving from an IDE to a SATA HD (or SSD). I certainly recommend you not simply replace the MB in the e-machine but go to another system or build your own if you can.

If you have to reinstall, leave the /home partition intact and just reinstall the system in / . Try first without reformatting. If that doesn't work, then reformat / and install a fresh system. Your desktop and files in your user directory will remain intact (though a backup is always advisable).

---

### Post by Redalien0304 on 2013-04-04
If you have 2nd desktop or laptop that should work via a Usb cable. i personally would Recover what you can 1st from Hdd then reinstall Cause the Original install Info is the Hdd.

---

### Post by sudodus on 2013-04-04
> **virgodave61 said:**
> My motherboard died, it was an EMachine and this seams to be a typical problem with them. I'm not sure if I should replace the motherboard or just by something better. My question is, if I plug my HD into a different motherboard will it recognize and adjust to the new motherboard(I know Windows will throw up, if you do this), or do I have to reinstall Ubuntu and if so can I install over the old installation, what is involved?
Thanks,
Dave

Yes, I have done it and do it all the time with a USB 3 pendrive, where I have installed Lubuntu 12.04 + Xubuntu desktop. I have no proprietory drivers in the system, so it is ***generally portable***, runs with Intel, Nvidia and Radeon graphics.

I have also moved my main installation Ubuntu 12.04 LTS (Unity) + Lubuntu desktop + Kubuntu desktop from a computer with AMD CPUs to one with Intel Xeon CPUs. Both computers have Nvidia graphics. And it works well. In 10.04 LTS, there was a minor problem with the graphics drivers (the same was not good in both computers), but in 12.04 it is ***portable within my corner of the Nvidia world***.

This is one of the great things with free software. There are no locks, only some thresholds due to proprietary drivers :-D

> **alien0304 said:**
> If you have 2nd desktop or laptop that should  work via a Usb cable. i personally would Recover what you can 1st from  Hdd then reinstall Cause the Original install Info is the Hdd.

If the drive can be properly connected it does not matter if it is IDE or SATA, HDD, SSD or simple flash (except for speed). Otherwise it can be ***cloned*** to a suitable drive in the new computer.

---

### Post by Cheesemill on 2013-04-04
> **virgodave61 said:**
> My motherboard died, it was an EMachine and this seams to be a typical problem with them. I'm not sure if I should replace the motherboard or just by something better. My question is, if I plug my HD into a different motherboard will it recognize and adjust to the new motherboard(I know Windows will throw up, if you do this), or do I have to reinstall Ubuntu and if so can I install over the old installation, what is involved?
Thanks,
Dave

It's not a problem at all, I do it all the time.

Unlike Windows which probes for hardware and sets up specific drivers when you install, the Linux kernel probes the hardware and loads the correct drivers on each boot (this is why it's possible to have a Live CD).

I have a full installation of Ubuntu on a USB stick which has worked on  every machine I've every tried it on (more than 50 machines at last  count).

The only time you could run into any problems is if you have installed any of the restricted graphics drivers and are switching from ATI to Nvidia or vice-versa.

---

### Post by virgodave61 on 2013-04-04
Thanks everyone for your input! This concerns me greatly because my Linux is my heart and soul and have spent hundreds of hours making things work esp. for my microchip programming and 3D printer and don't want to mess things up. This is why I've been spanked by the forum, because updates/upgrades often trash functionality. Thanks everyone again and I consider this issue solved!:D

---

### Post by conradin on 2013-04-04
Done it tons of times. Its one of the best features of the OS. keep in mind that certain things might need adjustment, like video settings, and you might have compatibility issues if you go form a 64 bit CPU to a 32 bit CPU.

---

