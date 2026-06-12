---
title: "[SOLVED] Unable to install nVidia 8800 drivers on Gutsy."
date: 2007-11-11
forum: General Help
---

### Post by overlord.gaurav on 2007-11-11
I have nVidia 8800 GTS. I had Feisty Fawn till now, and I had got my graphic card working using Envy in Feisty. I made a fresh install of Gutsy Gibbon two days ago. I had no problems in the setup. When Gutsy finally booted up, the only resolution available was 640X480. I believed that it was because I hadn't installed the graphic card drivers. I used the Restricted Driver Manager to install the driver, because I heard that it has been working fine for many people. After a reboot, I was left with a dialog box saying:
Running in low graphics mode.
Unable to detect your graphic card and monitor.

And then I had to choose the graphic card driver, so I chose "nv" from the list. Then, Gutsy started again, with the same low resolution. I tried Envy, and again, it didn't work. After working hard for a day, I got the different screen resolutions. But, I'm still unable to install my graphic card drivers. 
I also found that, whenever I try to install the drivers my xorg.conf changes to failsafe xorg.
I've attached the failsafe xorg and the current xorg.conf.
Kindly help.

---

### Post by overlord.gaurav on 2007-11-12
It's the third day since I'm on Gutsy without my graphic card enabled, kindly help.

---

### Post by nzadLithium on 2007-12-11
i duno if your still checking this thread but if you are run 
sudo apt-get remove nvidia-glx
sudo apt-get remove nvidia-glx-old 
(those two lines are incase you installed the older drivers for some weird reason :D)

sudo apt-get install nvidia-glx-new

sudo nvidia-xconfig

restart x and hopefully it will be all good :)

---

### Post by skymera on 2007-12-11
Envy script, hands down it will fix youyr drivers.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

install an fdrun it, it will detect your carfd and download the correct drivers.

good luck!!

---

### Post by Jimmey on 2007-12-11
Do what nzadLithium says.

Also, nv is the OSS driver for nVdia cards that only provides the basic 2D rendering. 

You should choose "nvidia" from any similar lists - This is the proper driver.

---

### Post by fridgebuzz on 2007-12-11
Also check your monitor settings, that was my problem.

---

### Post by overlord.gaurav on 2007-12-16
Ok, I tried all the above steps. None proved to bear any fruits.
And the screen resolution is really messy at my end.

---

### Post by nzadLithium on 2007-12-22
your problem could be that the latest driver in ubuntu repos is not up to date and therefore does not support the 8800. I dont know i think they would have updated but i cant check since i havent updated to gutsy yet. You could try building from the 'binary blob???' from nvidia. goto there website and find the latest linux installer. try installing from that. should be a how to somewhere

---

### Post by overlord.gaurav on 2008-07-01
I don't know if anyone is reading this or not..!?
Anyway, I've finally figured out what was wrong with the graphic card. It was the BIOS version. I updated my BIOS and now it works just fine!

---

