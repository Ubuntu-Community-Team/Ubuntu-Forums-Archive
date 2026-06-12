---
title: "How to permanently turn off dedicated graphics card on laptop?"
date: 2020-11-10
forum: General Help
---

### Post by linuxboi2 on 2020-11-10
It's an Acer Aspire 7 with a GTX1050 dedicated graphics card. The battery on it lasts 1h:30min with a full charge. I noticed the fans are working all the time, albeit not too loud (but still annoying enough), for no reason (ie. when the laptop is idling with nothing running or I’m doing very light browsing etc.). Sometimes the fans would start spinning a bit harder for 10-15 second then go back to normal speeds, again for no reason. I suspect all this could be the graphic cards fault.  
 
 I tried installing proprietary nvidia drivers and disabling the card in Nvidia X Server Settings, but the problem persisted. Now I'd like to try a different approach. Any advice on how I could (semi)permanently turn off the graphics card and use only the integrated one, while still being able to turn it on in the future in case the need arises.

---

### Post by ActionParsnip on 2020-11-10
Possibly in the BIOS..?

---

### Post by linuxboi2 on 2020-11-10
For some reason this bios (InsydeH2O) doesn't have that option

---

### Post by HermanAB on 2020-11-11
Unload the device driver with *rmmod* and see if the system cools down.  If not, then it is not the graphic card that is the problem.

Use *lsmod* to list the loaded drivers and find the potential culprit.

BTW, connect to the machine over SSH from another machine when you futz with screen drivers, since you can end up with no screen at all, which can be hard to recover from!

---

### Post by linuxboi2 on 2020-11-11
There doesn't seem to be any nvidia module on the list. I've found "nouveau", but I assume that would make me lose the screen as you've said. Could it be hidden under some different name?

---

### Post by SeijiSensei on 2020-11-11
If the NVIDIA module is installed in the kernel, then you should see this:
```

$ lsmod | grep nvidia

nvidia_uvm           1007616  0
nvidia_drm             49152  9
nvidia_modeset       1183744  32 nvidia_drm
nvidia              19722240  1739 nvidia_uvm,nvidia_modeset
drm_kms_helper        184320  1 nvidia_drm
drm                   491520  12 drm_kms_helper,nvidia_drm

```

If you don't see entries like that, only ones for nouveau, you're not using the proprietary driver.  Did you install the driver using the Driver Manager app in Settings?

---

### Post by HermanAB on 2020-11-11
So you have the FOSS driver loaded.  Again, ensure that sshd is working and that you can connect from another machine, since you can too easily end up with a black screen, leaving you poking around like after an accident in a coal mine.

---

### Post by linuxboi2 on 2020-11-11
My mistake...I forgot that there can be no nvidia drivers listed, as I've removed them and went back to nouveau after being unable to disable the graphics card using them (through Nvidia X Server Settings). So it's obvious I'm only seeing nouveau.
Should I reinstall them and try removing those modules which are used by the dedicated card or try some different approach?

---

### Post by linuxboi2 on 2020-11-11
I'll make sure to connect from another machine. What should I remove from the kernel and how can it be returned in case I lose my screen or something similar. nvidia show nothing, but nouveau outputs these:

nouveau              
mxm_wmi                
ttm                  
drm_kms_helper      
i2c_algo_bit           
drm                 
wmi                   
video

---

### Post by CelticWarrior on 2020-11-13
With Nvidia drivers you can use Nvidia X Server Settings to switch graphics. Reboot.
With nouveau you can't.

---

### Post by linuxboi2 on 2020-11-13
I already tried doing that with X Server Settings, but the problem remained. Now I'm looking for an alternative way to disable the dedicated graphics card.

---

### Post by CelticWarrior on 2020-11-13
There's no alternative way and how do you know it wasn't running with iGPU Intel instead?
Fasn are obviously no such indicator because rebooting after the switch may need them to run for a while because the temperature sensor says it's still hot. And very likely those fans could use a serious cleanup. And the motherboard's firmware, BIOS or UEFI, an update. What it doesn't need is nonsense based on wrong assumptions.

---

### Post by linuxboi2 on 2020-11-13
The firmware and BIOS are up to date, the insides of the laptop were thoroughly cleaned and thermal paste was changed, while the laptop itself was given enough time to cool down many times (e.g. when it was shut down overnight). I'm not claiming it wasn't running with iGPU, but merely attempting to discover an alternative way of disabling the dedicated GPU in case the X Server Settings route was for some reason unsuccessful (as the persistent fan and battery drain issues suggest).

---

