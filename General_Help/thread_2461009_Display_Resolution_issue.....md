---
title: "Display/ Resolution issue...."
date: 2021-04-22
forum: General Help
---

### Post by jakemaverick911 on 2021-04-22
So, just upgraded my monitor, namely to this one

[https://www.laptopsdirect.co.uk/philips-27-v-line-273v7qdab-full-hd-ips-hdmi-monitor-273v7qdab-00/version.asp#!#specs](https://www.laptopsdirect.co.uk/philips-27-v-line-273v7qdab-full-hd-ips-hdmi-monitor-273v7qdab-00/version.asp#!#specs)

I'm using Xubuntu Bionic Beaver. Current settings at 1680x1050 @ 60 Hz, I now need to change to 1920x1080 @ 75 Hz. I've tried the xandr command and the error message I get is 'Size 1920x1080 not found in available modes'.

I remember it being a pain to do last time I did it many years ago....pretty stuck now. Looked at a few threads on the issue and nothing seems to solve the problem. Many thanks in anticipation if anybody can help with this one?

---

### Post by ajgreeny on 2021-04-22
We need more info about your system so as a start let's see the output of command ```
inxi -Fzx
```
Please use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**

---

### Post by Yellow Pasque on 2021-04-22
Look at:
```
xrandr -q
```
Also, copy/paste /var/log/Xorg.0.log if possible. Use code tags as it's a lot of text.

@aj, this isn't an issue with installing/upgrading Ubuntu itself, so maybe move to 'Hardware'?

---

### Post by jakemaverick911 on 2021-04-22
ok thanks, i get 

```
System:    Host: Orac Kernel: 4.4.0-210-generic x86_64 (64 bit gcc: 5.4.0)
           Desktop: Xfce 4.12.3 (Gtk 2.24.28) Distro: Ubuntu 16.04 xenial
Machine:   System: Hewlett-Packard product: HP Compaq 8100 Elite SFF PC
           Mobo: Hewlett-Packard model: 304Ah
           Bios: Hewlett-Packard v: 786H1 v01.02 date: 12/16/2009
CPU:       Dual core Intel Core i5 650 (-HT-MCP-) cache: 4096 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 12769
           clock speeds: max: 3333 MHz 1: 1866 MHz 2: 1199 MHz 3: 1199 MHz
           4: 1866 MHz
Graphics:  Card: Intel Core Processor Integrated Graphics Controller
           bus-ID: 00:02.0
           Display Server: X.Org 1.18.4 drivers: intel (unloaded: fbdev,vesa)
           Resolution: 1680x1050@59.95hz
           GLX Renderer: Mesa DRI Intel Ironlake Desktop
           GLX Version: 2.1 Mesa 18.0.5 Direct Rendering: Yes
Audio:     Card Intel 5 Series/3400 Series High Definition Audio
           driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture v: k4.4.0-210-generic
Network:   Card-1: Intel 82578DM Gigabit Network Connection
           driver: e1000e v: 3.2.6-k port: 1100 bus-ID: 00:19.0
           IF: enp0s25 state: down mac: <filter>
           Card-2: Ralink RT2870/RT3070 Wireless Adapter
           driver: rt2800usb v: 2.3.0 usb-ID: 001-003
           IF: wlx7cdd9013a8a3 state: N/A mac: N/A
Drives:    HDD Total Size: 674.8GB (83.3% used)
           ID-1: /dev/sda model: TS128GSSD370S size: 128.0GB
           ID-2: /dev/sdb model: ST500DM002 size: 500.1GB
           ID-3: USB /dev/sde model: SD/MMC size: 31.3GB
           ID-4: USB /dev/sdh model: Ultra_Fit size: 15.4GB
Partition: ID-1: / size: 62G used: 40G (69%) fs: ext4 dev: /dev/sda6
           ID-2: swap-1 size: 3.35GB used: 0.00GB (0%) fs: swap dev: /dev/dm-0
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 36.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 262 Uptime: 2:01 Memory: 2231.5/11814.5MB
           Init: systemd runlevel: 5 Gcc sys: 5.4.0
           Client: Shell (bash 4.3.481) inxi: 2.2.35
```

---

### Post by jakemaverick911 on 2021-04-22
and for the second command i get

```
Screen 0: minimum 8 x 8, current 1680 x 1050, maximum 32767 x 32767
DP1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
VGA1 connected 1680x1050+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1680x1050     59.95 +
   1024x768      60.00  
   800x600       60.32    56.25  
   848x480       60.00  
   640x480       59.94  
   1680x1050_60.00  59.95* 
VIRTUAL1 disconnected (normal left inverted right x axis y axis)
```


and sorry, don't quite understand the copy and paste bit as it's been long while since i have had to ask for support?

---

### Post by jakemaverick911 on 2021-04-22
```

System:    Host: Orac Kernel: 4.4.0-210-generic x86_64 (64 bit gcc: 5.4.0)
           Desktop: Xfce 4.12.3 (Gtk 2.24.28) Distro: Ubuntu 16.04 xenial
Machine:   System: Hewlett-Packard product: HP Compaq 8100 Elite SFF PC
           Mobo: Hewlett-Packard model: 304Ah
           Bios: Hewlett-Packard v: 786H1 v01.02 date: 12/16/2009
CPU:       Dual core Intel Core i5 650 (-HT-MCP-) cache: 4096 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 12769
           clock speeds: max: 3333 MHz 1: 1866 MHz 2: 1199 MHz 3: 1199 MHz
           4: 1866 MHz
Graphics:  Card: Intel Core Processor Integrated Graphics Controller
           bus-ID: 00:02.0
           Display Server: X.Org 1.18.4 drivers: intel (unloaded: fbdev,vesa)
           Resolution: 1680x1050@59.95hz
           GLX Renderer: Mesa DRI Intel Ironlake Desktop
           GLX Version: 2.1 Mesa 18.0.5 Direct Rendering: Yes
Audio:     Card Intel 5 Series/3400 Series High Definition Audio
           driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture v: k4.4.0-210-generic
Network:   Card-1: Intel 82578DM Gigabit Network Connection
           driver: e1000e v: 3.2.6-k port: 1100 bus-ID: 00:19.0
           IF: enp0s25 state: down mac: <filter>
           Card-2: Ralink RT2870/RT3070 Wireless Adapter
           driver: rt2800usb v: 2.3.0 usb-ID: 001-003
           IF: wlx7cdd9013a8a3 state: N/A mac: N/A
Drives:    HDD Total Size: 674.8GB (83.3% used)
           ID-1: /dev/sda model: TS128GSSD370S size: 128.0GB
           ID-2: /dev/sdb model: ST500DM002 size: 500.1GB
           ID-3: USB /dev/sde model: SD/MMC size: 31.3GB
           ID-4: USB /dev/sdh model: Ultra_Fit size: 15.4GB
Partition: ID-1: / size: 62G used: 40G (69%) fs: ext4 dev: /dev/sda6
           ID-2: swap-1 size: 3.35GB used: 0.00GB (0%) fs: swap dev: /dev/dm-0
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 36.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 262 Uptime: 2:01 Memory: 2231.5/11814.5MB
           Init: systemd runlevel: 5 Gcc sys: 5.4.0
           Client: Shell (bash 4.3.481) inxi: 2.2.35 

```

---

### Post by jakemaverick911 on 2021-04-22
sorry aj, i didn't 'see' the lst line of your post until now ;-)

---

### Post by ActionParsnip on 2021-04-22
Isn't 16.04 end of life next month?

---

### Post by jakemaverick911 on 2021-04-22
```

Screen 0: minimum 8 x 8, current 1680 x 1050, maximum 32767 x 32767
DP1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
VGA1 connected 1680x1050+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1680x1050     59.95 +
   1024x768      60.00  
   800x600       60.32    56.25  
   848x480       60.00  
   640x480       59.94  
   1680x1050_60.00  59.95* 
VIRTUAL1 disconnected (normal left inverted right x axis y axis)

```

---

### Post by jakemaverick911 on 2021-04-22
i do not know on that....i'm happy with what it is so don't feel need to upgrade! unless newer version got better options in the Display GUI....

---

### Post by CelticWarrior on 2021-04-22
No, not unless nothing. Not upgrading is not an option unless you contract ESM.
EoL release no longer receive security updates.

---

### Post by Yellow Pasque on 2021-04-22
So it seems the EDID is not being read properly. If you have a different VGA cable, you may want to try that first. Make sure both ends are connected firmly and screwed in.
If you don't have a spare cable or it exhibits the same issue, try:
[https://wiki.ubuntu.com/X/Config/Resolution#Adding_undetected_resolutions](https://wiki.ubuntu.com/X/Config/Resolution#Adding_undetected_resolutions)

---

### Post by ActionParsnip on 2021-04-23
> **jakemaverick911 said:**
> i do not know on that....i'm happy with what it is so don't feel need to upgrade! unless newer version got better options in the Display GUI....

Once your release goes end of life (EOL) it will no longer receive updates or community support and will be considered unsecure. The OS will obviously continue to function

---

### Post by jakemaverick911 on 2021-04-23
> **ActionParsnip said:**
> Once your release goes end of life (EOL) it will no longer receive updates or community support and will be considered unsecure. The OS will obviously continue to function

ahhh..... that is a thought! just didn't want to risk losing all my settings and apps and things, it's not just the OS install that takes the time, it is everything else....! :-(

---

### Post by jakemaverick911 on 2021-04-23
> **Yellow Pasque said:**
> So it seems the EDID is not being read properly. If you have a different VGA cable, you may want to try that first. Make sure both ends are connected firmly and screwed in.
If you don't have a spare cable or it exhibits the same issue, try:
[https://wiki.ubuntu.com/X/Config/Resolution#Adding_undetected_resolutions](https://wiki.ubuntu.com/X/Config/Resolution#Adding_undetected_resolutions)

ah....I'm actually using a kvm, so that cd be interfering......i shall try later, thanks!

---

### Post by ActionParsnip on 2021-04-23
> **jakemaverick911 said:**
> ahhh..... that is a thought! just didn't want to risk losing all my settings and apps and things, it's not just the OS install that takes the time, it is everything else....! :-(

Then ensure your backups are up to date and restore your data when you reinstall with the new version....

---

### Post by Yellow Pasque on 2021-04-23
> ah....I'm actually using a kvm

So you are running Ubuntu inside a VM (i.e. as a guest)?

---

### Post by tea for one on 2021-04-23
> **jakemaverick911 said:**
> ah....I'm actually using a kvm, so that cd be interfering......i shall try later, thanks!

KVM - Keyboard, Video & Mouse
KVM - kernel based Virtual Machine

I wonder which one it is?

---

### Post by Yellow Pasque on 2021-04-23
> **tea for one said:**
> KVM - Keyboard, Video & Mouse
KVM - kernel based Virtual Machine
I wonder which one it is?

Good point. It's probably a KVM switch, and yes, I've seen those interfere with EDID.

---

### Post by ajgreeny on 2021-04-23
*Thread moved to **Virtualisation**.* which is more appropriate and a better fit.

We might have found you an answer quicker if you had mentioned that this was a VM using KVM but whether VM or hard metal install, you really **MUST** either upgrade or reinstall a supported version.
An unsupported version is not only a risk to you but also potentially all other computer users as you machine might more easily be turned into a spam bot or similar.

---

### Post by jakemaverick911 on 2021-04-23
yes, keyboard video and mouse ;-)

---

### Post by jakemaverick911 on 2021-04-23
> **ActionParsnip said:**
> Then ensure your backups are up to date and restore your data when you reinstall with the new version....

can u recommend something to restore data after? i've had trouble years ago when i used something, aptik maybe or similar sounding and i lost some stuff :-(

---

### Post by jakemaverick911 on 2021-04-23
just looking at it again.....and it really is a pain to connect vga cable directly as it means moving worktops and things out of the way in order to get to it.....will that wiki page definitely work via the KVM? as that is looking like my best option atm....

---

### Post by QIII on 2021-04-23
Moved back to General Help.

Keyboard/Video/Mouse versus Kernel-based Virtual Machine.

One might avoid confusion by speaking of a KVM ***swtich*** rather than just KVM on a Linux Forum.  For most of us, KVM means virtualization.

---

### Post by jakemaverick911 on 2021-04-23
> **QIII said:**
> Moved back to General Help.

Keyboard/Video/Mouse versus Kernel-based Virtual Machine.

One might avoid confusion by speaking of a KVM ***swtich*** rather than just KVM on a Linux Forum.  For most of us, KVM means virtualization.

apologies....i know nothing on virtualisation! actually, perhaps did it once many years back thinking on it....but I had no idea that KVM could stand for something else.....besides from the context, was it not obvious?

---

### Post by ajgreeny on 2021-04-24
Mea culpa!

Sorry, but KVM to me means virtualisation as mentioned by QIII.
I know absolutely nothing about KVM switches!

---

### Post by Yellow Pasque on 2021-04-24
> will that wiki page definitely work via the KVM?

It may. Try it. Either it will work or the last command will give you an error.

---

### Post by jakemaverick911 on 2021-04-24
oh my! just bypassed the kvm and connected directly...and it automatically connected and sorted itself out! never known linux to do that before....so it looks like problem solved, 'cept it's still at 60 Hz when it should be 75 Hz.....anyway to change that bit? 60 Hz doesn't seem to be a problem...but it hink higher refresh rate is better on the eyes? then will have to go through it all again when i sort out what to upgrade to next..... :-( thanks for help folks!

---

### Post by Yellow Pasque on 2021-04-24
> **jakemaverick911 said:**
> oh my! just bypassed the kvm and connected directly...and it automatically connected and sorted itself out! never known linux to do that before....so it looks like problem solved, 'cept it's still at 60 Hz when it should be 75 Hz.....anyway to change that bit? 60 Hz doesn't seem to be a problem...but it hink higher refresh rate is better on the eyes? then will have to go through it all again when i sort out what to upgrade to next..... :-( thanks for help folks!

[https://wiki.ubuntu.com/X/Config/Resolution#Adding_undetected_resolutions](https://wiki.ubuntu.com/X/Config/Resolution#Adding_undetected_resolutions)

---

### Post by jakemaverick911 on 2021-04-24
ok getting annoying now, put kvm back in and it's gone back to how it was before, it did not remember! :-(

---

### Post by jakemaverick911 on 2021-04-24
> **Yellow Pasque said:**
> [https://wiki.ubuntu.com/X/Config/Resolution#Adding_undetected_resolutions](https://wiki.ubuntu.com/X/Config/Resolution#Adding_undetected_resolutions)

i shall definitely try that next.....tad knackered now though, might be tomorrow....

---

### Post by jakemaverick911 on 2021-04-24
are these beans actually worth anything that i'm accumulating here....? ;-)

---

### Post by Yellow Pasque on 2021-04-24
> **jakemaverick911 said:**
> are these beans actually worth anything that i'm accumulating here....? ;-)

I'm a sarcastic/cynical kind of guy, so my apologies if the thing under my name leads you to question your beliefs. Getting off track though...

---

