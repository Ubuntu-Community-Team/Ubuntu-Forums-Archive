---
title: "pixelated screen"
date: 2017-03-09
forum: General Help
---

### Post by marlsechanson on 2017-03-09
My display is pixelated. I've just recently installed Ubuntu  16.10. the graphics card is an Nvidia Geforce 710a,  Every time I install Linux on this computer (hp 23 pavilion 23-h020a),  regardless of the distro, this same problem occurs. Windows was run on a  separate hard drive without the same  problem. So I don't think it's  the monitor itself. 

   What could it be, and how can I fix it? has anyone had a similar experience? because I've been trying to solve this for the better part of two weeks

[IMG]http://i.imgur.com/Zjk7Y54.jpg[/IMG]

---

### Post by QIII on 2017-03-09
Hello!

Please do not include table or other formatting created by other sites.

---

### Post by marlsechanson on 2017-03-09
sorry about that.

---

### Post by Perfect Storm on 2017-03-09
Lets get some info from your card:
```
nvidia-smi
```

---

### Post by marlsechanson on 2017-03-09
```
 

Thu Mar  9 17:28:42 2017     
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 370.28                 Driver Version: 370.28                    |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce 710A        Off  | 0000:01:00.0     N/A |                  N/A |
| N/A   39C    P0    N/A /  N/A |    275MiB /   982MiB |     N/A      Default |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                       GPU Memory |
|  GPU       PID  Type  Process name                               Usage      |
|=============================================================================|
|    0                  Not Supported                                         |
+-----------------------------------------------------------------------------+

```

---

### Post by Perfect Storm on 2017-03-09
The driver seems up to date. How's the nvidia driver that you can download through ubuntu works? Still the same pixeled?

---

### Post by marlsechanson on 2017-03-09
yeah, I tried the propriety drivers that you can download directly through ubuntu, I tried the "graphics-driver" team's propriety gpu drivers for nvidia, I've tried setting the resolution to all the different kinds of resolutions that were available, I''ve tried doing the same through xrandr. All the same. 

I've reinstalled the x server , reinstalled all the drivers about 20 times. tried making it work with the noveau driver, even tried using the nvidia drivers directly from nvidia's website. All to no change.

---

### Post by Perfect Storm on 2017-03-09
How did the card worked in Windows? It could be that the card is damaged.

---

### Post by marlsechanson on 2017-03-09
The card seemed to work fine in Windows, it wasn't pixelated. I hope the card isn't damaged as I think it's soldered to the motherbother :-|

---

### Post by Perfect Storm on 2017-03-09
try reinstall xorg and install xorg-devel then reinstall the driver.

---

### Post by marlsechanson on 2017-03-09
I've reinstalled xorg, for the other install, do you mean xorg-dev?

---

### Post by Perfect Storm on 2017-03-09
aye

EDIT: have you tried this: [https://ubuntuforums.org/showthread.php?t=2149662&p=12918727#post12918727](https://ubuntuforums.org/showthread.php?t=2149662&p=12918727#post12918727)

---

### Post by marlsechanson on 2017-03-09
I've edited the splash screen and done nomodeset , I haven't attempted to blacklist nouveau, I'll try it now

---

### Post by Perfect Storm on 2017-03-09
yeah, xorg-dev

---

### Post by marlsechanson on 2017-03-09
I tried both nouveau.blacklist=1 and nomodeset in grub2, and nothing worked. :/

---

### Post by Perfect Storm on 2017-03-09
Then I'm little lost on what's wrong.

---

### Post by marlsechanson on 2017-03-09
Same here, I seriously have no clue. thanks for the help though.
Does anyone else have an idea on what to do?

---

### Post by marlsechanson on 2017-03-09
I just had a thought, grub2 seems to have the correct resolution, but as soon as the kernel starts booting up, the console becomes pixelated. Could grub2 have the correct settings? How exactly would I use this to configure Ubuntu? 

here's the output of vbeinfo:
[IMG]http://i.imgur.com/6kFG1LC.jpg[/IMG]

---

