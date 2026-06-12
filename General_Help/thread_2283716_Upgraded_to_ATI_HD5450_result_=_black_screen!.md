---
title: "Upgraded to ATI HD5450 result = black screen!"
date: 2015-06-23
forum: General Help
---

### Post by zaoka on 2015-06-23
I installed new Sapphire HD5450 video card and Kubuntu 15.04 does not start anymore, it has black screen right after BIOS screen... dissapear.

With built-in video card it does work fine.

What steps I need to do in order to make my system work with this card?


Thanks

---

### Post by QIII on 2015-06-24
Hello!

What brand and model is the integrated graphics adapter?  Did you have a proprietary driver installed?

---

### Post by wildmanne39 on 2015-06-24
If you had another video card driver installed for your old card you should have removed it before you removed the old card and put in the new.

---

### Post by zaoka on 2015-06-24
Integrated ATI Radeon 3000.

This is motherboard: [http://www.amazon.com/M5A78L-M-LX-PLUS-Micro-Motherboard/dp/B005WUUFBW](http://www.amazon.com/M5A78L-M-LX-PLUS-Micro-Motherboard/dp/B005WUUFBW)

?

---

### Post by leunam12 on 2015-06-24
That is the video card that I had in my previous computer. Never had a problem with it. Strange! do you have image if you boot from USB or DVD?

---

### Post by zaoka on 2015-06-24
Did not try yet.
Card is working fine, however, when watching HD videos on Youtube it does have some lagging... also it uses system memory (256mb). For this reason I got this new Sapphire HD5450 with 1GB of ram to fix this problem and also that way I can free-up some ram for the system since I only have 4GB.

I am not sure do I have to remove current drivers first, restart PC and install new card

or

Install new driver and than install new card....

---

### Post by deadflowr on 2015-06-24
What drivers are installed?

---

### Post by leunam12 on 2015-06-24
Start with your integrated card; remove driver and restart PC with your new card

---

### Post by zaoka on 2015-06-24
```
 [FONT=monospace][COLOR=#000000]sudo lshw -c video [/COLOR]
  *-display                
       description: VGA compatible controller 
       product: RS780L [Radeon 3000] 
       vendor: Advanced Micro Devices, Inc. [AMD/ATI] 
       physical id: 5 
       bus info: pci@0000:01:05.0 
       version: 00 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm msi vga_controller bus_master cap_list rom 
       configuration: driver=radeon latency=0 
       resources: irq:18 memory:d0000000-dfffffff ioport:d000(size=256) memory:febe0000-febeffff 
memory:fea00000-feafffff
[/FONT]

```

```
 [FONT=monospace][COLOR=#000000]sudo find /dev -group video [/COLOR]
/dev/fb0 
/dev/dri/card0 
/dev/dri/renderD128 
/dev/dri/controlD64

[/FONT]

```

---

### Post by zaoka on 2015-06-24
OK this helped:

```
sudo sh /usr/share/ati/fglrx-uninstall.sh
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev*

sudo apt-get install --reinstall xserver-xorg-core libgl1-mesa-glx libgl1-mesa-dri libgl1-mesa-glx libgl1-mesa-dri

sudo dpkg-reconfigure xserver-xorg

sudo reboot
```

As soon as it restarted I turned power off and installed new card.

After that I went to system setting and driver manager and selected fglrx-updates as my driver.


Thanks

---

