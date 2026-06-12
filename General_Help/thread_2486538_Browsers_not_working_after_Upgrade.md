---
title: "Browsers not working after Upgrade"
date: 2023-05-03
forum: General Help
---

### Post by KDMerrill on 2023-05-03
I recently upgraded from 20.04 to 22.04, and after the upgrade, when I try to launch either Chrome of Firefox....it looks like they launch, but there are no browser windows to be found, and all open windows shake uncontrollably until I force their respective processes closed.  The browser 'Web' works fine, but Chrome and Firefox just havoc.  Any suggestions?  I've read the tip to disable hardware acceleration, but if I can't even find a window, I have don't know how to check to see if hardware acceleration is even turned on.?.?.?

Kevin in VA

---

### Post by TenPlus1 on 2023-05-03
You could try and install the .deb version of Firefox to try out and see if that helps: [https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04](https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04)

---

### Post by KDMerrill on 2023-05-03
yea, no joy unfortunately.  Still seeing same behaviour.  When I launched Firefox from the command line I did notice this, though I'm not sure what it means:

[GFX1]: No Us detected via PCI

Then when I close the process, I got thes elines:

[ERROR glean_core] Error setting metrics feature config: Json(Error("EOF while parsing a value", line: 1, column: 0))
ALSA lib conf.c:4120:(snd_config_update_r) Cannot access file /usr/share/alsa/alsa.conf
ALSA lib seq.c:935:(snd_seq_open_noupdate) Unknown SEQ default

Not sure what alsa is....but I know when I lost all sound I was also getting warnings that listed alsa as well.

---

### Post by #&amp;thj^% on 2023-05-03
> **KDMerrill said:**
> yea, no joy unfortunately.  Still seeing same behaviour.  When I launched Firefox from the command line I did notice this, though I'm not sure what it means:

[GFX1]: No Us detected via PCI

Then when I close the process, I got thes elines:

[ERROR glean_core] Error setting metrics feature config: Json(Error("EOF while parsing a value", line: 1, column: 0))
ALSA lib conf.c:4120:(snd_config_update_r) Cannot access file /usr/share/alsa/alsa.conf
ALSA lib seq.c:935:(snd_seq_open_noupdate) Unknown SEQ default

Not sure what alsa is....but I know when I lost all sound I was also getting warnings that listed alsa as well.

Here you go: Advanced Linux Sound Architecture
and show us this as well:
```
inxi -Gns

```

---

### Post by KDMerrill on 2023-05-03
Curser in Terminal just flashed after that command....finally killed it with ^C - but it never returned a response.

---

### Post by #&amp;thj^% on 2023-05-03
My Dear Friend, This sounds like a great time to back-up what you want/need for a clean fresh install.
EDIT: It sounds to me like the Upgrade left you with a lot of corruption.

---

### Post by KDMerrill on 2023-05-03
100% agree.  Unfortunately, I installed a Plextor PX-891SAF DVD writer to make a fresh boot disk....and the damned thing will only mount as a read-only device, so now I'm Googling left and right trying to figure out how to make this DVD writer work....so I can make a boot disc.....so I can wipe my system and do a CLEAN install !!  Grrrrrrr !!!

---

### Post by Holger_Gehrke on 2023-05-03
Wouldn't it be faster to make a bootable USB Flash drive ? If you can't use one of those for some reason, writing a DVD needs specialized software like Brasero, k3b, or xfburn. You can't just mount a DVD as a writable device.

Holger

---

### Post by #&amp;thj^% on 2023-05-03
Agree with Holger USB the only way to burn...lol

---

### Post by KDMerrill on 2023-05-03
It's a DVD burner.  With a fstab entry it's working fine for burning DVDs now, but I swear every time I fix 1 problem another one pops up.  My DVD-Rs are 4.7GB.....and the 22.04 .iso is 4.9GB.  Brasero IS what I am using.

I tried a bootable USB thumb drive one time and didn't have much luck, but perhaps I will try that again.  Just need to change my BIOS boot-order.

---

### Post by #&amp;thj^% on 2023-05-03
> **KDMerrill said:**
> My DVD-Rs are 4.7GB.....and the 22.04 .iso is 4.9GB.  Brasero IS what I am using.
You can see a possible problem there right? "size"
> **KDMerrill said:**
> 
I tried a bootable USB thumb drive one time and didn't have much luck, but perhaps I will try that again.  Just need to change my BIOS boot-order.
Might be the tool used, for me I use 2 or three for my use's for ISO's i just stick with balenaEtcher. Tried and True never let's me down

---

