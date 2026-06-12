---
title: "Excessive Memory &amp; Processor Usage"
date: 2021-03-01
forum: General Help
---

### Post by malfindin on 2021-03-01
First off my "Disk Cache" is using 74% of my RAM, but even when I clear it my processor is still lagging due to process called:
"kcmshell5 kcm_memory" which is taking an average of 55% of my processor even when I have no apps open.

I see no other posts that reference this process. In fact I'm having difficulty figuring out what it even is...google is no help. Though apparently there is a K-POP band of the same name. 

Kubuntu 20.04.2

Thoughts?

---

### Post by ActionParsnip on 2021-03-01
This is normal. You permanent storage is super slow compared to the system RAM. The OS is keeping files in there to make the system faster for you. As real applications are ran then cache will make way and reduce itself.

Are you seeing system slowness?

---

### Post by TheFu on 2021-03-01
We need some facts

```
inxi -Fz
free -hm
```

Please help us to help you.

---

### Post by malfindin on 2021-03-01
Oh my YES. Slowness to the point of the system being unusable.  If I open one single page in a browser, any browser, I type and it takes 10 seconds for the text to appear on the screen.

---

### Post by malfindin on 2021-03-01
I'll post those in 30 min.  It'll take me that long to boot it, log in to the forums, and post the info...at least. 1 hour might be a more realistic estimate.  I am currently on my other computer.

---

### Post by TheFu on 2021-03-01
> **malfindin said:**
> Oh my YES. Slowness to the point of the system being unusable.  If I open one single page in a browser, any browser, I type and it takes 10 seconds for the text to appear on the screen.

I'd go with a very light GUI to start.  No DE, just a window manager.  openbox, fvwm, fluxbox are light.

---

### Post by malfindin on 2021-03-01
I'm still working on it. It's going to take about 30 to install inxi. 
P.S. I have gigabyte fiber...BTW

---

### Post by malfindin on 2021-03-01
I am partial to Lubuntu...

But there should be no need for a lighter OS. The system is not all that bad.  It runs Win 10 very fast...

---

### Post by malfindin on 2021-03-01
Well that took forever. Please NOTE this system runs Kubuntu very fast from USB stick. It's only after installing it that the slowness occurs.

OUTPUT of inxi
```
System:    Kernel: 5.8.0-44-generic x86_64 bits: 64 Desktop: KDE Plasma 5.18.5 
           Distro: Ubuntu 20.04.2 LTS (Focal Fossa) 
Machine:   Type: Laptop System: TOSHIBA product: Satellite C855D v: PSCBUU-006005 serial: <filter> 
           Mobo: TOSHIBA model: Portable PC v: MP serial: <filter> UEFI: Insyde v: 6.20 date: 11/07/2012 
Battery:   ID-1: BAT0 charge: 34.4 Wh condition: 34.4/48.6 Wh (71%) 
CPU:       Topology: Dual Core model: AMD A6-4400M APU with Radeon HD Graphics bits: 64 type: MCP 
           L2 cache: 1024 KiB 
           Speed: 2695 MHz min/max: 1400/2700 MHz Core speeds (MHz): 1: 2695 2: 2695 
Graphics:  Device-1: AMD Trinity 2 [Radeon HD 7520G] driver: radeon v: kernel 
           Display: x11 server: X.Org 1.20.9 driver: radeon FAILED: ati unloaded: fbdev,modesetting,vesa 
           resolution: 1366x768~60Hz 
           OpenGL: renderer: AMD ARUBA (DRM 2.50.0 / 5.8.0-44-generic LLVM 11.0.0) v: 4.3 Mesa 20.2.6 
Audio:     Device-1: AMD Trinity HDMI Audio driver: snd_hda_intel 
           Device-2: AMD FCH Azalia driver: snd_hda_intel 
           Sound Server: ALSA v: k5.8.0-44-generic 
Network:   Device-1: Qualcomm Atheros AR8162 Fast Ethernet driver: alx 
           IF: enp1s0 state: down mac: <filter> 
           Device-2: Realtek RTL8723AE PCIe Wireless Network Adapter driver: rtl8723ae 
           IF: wlp2s0 state: up mac: <filter> 
Drives:    Local Storage: total: 698.64 GiB used: 25.99 GiB (3.7%) 
           ID-1: /dev/sda vendor: Seagate model: ST750LX003-1AC154 size: 698.64 GiB 
Partition: ID-1: / size: 457.35 GiB used: 25.95 GiB (5.7%) fs: ext4 dev: /dev/sda2 
           ID-2: swap-1 size: 3.81 GiB used: 13.5 MiB (0.3%) fs: swap dev: /dev/sda5 
Sensors:   System Temperatures: cpu: 55.8 C mobo: N/A gpu: radeon temp: 56 C 
           Fan Speeds (RPM): N/A 
Info:      Processes: 163 Uptime: 2h 49m Memory: 3.32 GiB used: 934.5 MiB (27.5%) Shell: bash inxi: 3.0.38 
```

OUTPUT of free
```
              total        used        free      shared  buff/cache   available
Mem:          3.3Gi       823Mi       909Mi        19Mi       1.6Gi       2.3Gi
Swap:         3.8Gi        13Mi       3.8Gi
```

---

### Post by malfindin on 2021-03-01
Thank you all for your help. I've been using and installing Linux for clients since 2007 and never seen anything like this.

---

### Post by malfindin on 2021-03-01
UPDATE on system...I installed Lubuntu-Desktop to see if the problem was KDE related. 

It ran VERY fast in Lubuntu with no issues, but Lubuntu was saying I needed to reboot.

After reboot I cannot get into Linux anymore, the BOOT menu, or even the BIOS.

None of the function keys do anything and Windows 10 fires up no matter what I do.

---

### Post by CelticWarrior on 2021-03-01
You can access UEFI ("BIOS") settings from Windows anc change the boot order back to Ubuntu.

---

### Post by malfindin on 2021-03-01
I fixed that issue by booting to a USB drive and editing my uefi config. So we're back up.  Lubuntu still runs GREAT & Kubuntu still runs VERY slow.  If we can fix this it would be good.  The customer wants KDE.

---

### Post by malfindin on 2021-03-01
The short answer is NO...but I fixed it another way.

We are back to why is Kubutnu NOT working when I've had no issues with it on 17 computers up until this one???

I literally do this for a living and have never encountered a problem until today.

---

### Post by HermanAB on 2021-03-01
You don't perhaps have a file indexer running in KDE?  Some years ago, there was a desktop indexing fad - in KDE it was called nepomuk.  It never worked properly and the main character behind it passed on to the great computer in the sky...  Maybe a new disciple started such a thing again?

Anyhoo, 'top' or 'htop' will reveal the culprit and then you can kill it.  If it is really necessary, it will spin up again.

---

### Post by TheFu on 2021-03-01
This is an average 2-core system w/ 3G of RAM.  

If you ssh into to the system, is it slow or is the slowdown purely GUI stuff?

If GUI-only, check that the GPU drivers for the fast and slow DEs are the same.

I haven't touched KDE since around 2002, so doubtful I can help.  On 20.04, my first install was Mate and it was terribly slow. I'd elected the ZFS booting option too. After about an hour trying to figure out the issue, I reinstalled using LVM instead and it was faster - though still slow. Another hour of troubleshooting and I switched to fvwm (which was my plan anyway) and never looked back. The system flies.  It is a VM with 1 core, 3G, using QXL video drivers (it is a VM). I'm on the 5.4.x kernel.
Have you considered using the 5.4 kernel to see if that matters?

---

### Post by malfindin on 2021-03-01
Not sure if this helps but I've booted the system in Kubuntu from TWO different USB thumb drives and neither has the memory and speed issues.  It's only when I install and boot from the HD... Could it be that this system has a Hybrid Drive?

---

### Post by malfindin on 2021-03-01
It's not GUI related.  I have tried MATE and LUBUNTU and KDE and it runs fine in all of them.  If you install to the HD then MATE and LUBUNTU don't see the NIC. KUBUNTU sees the NIC and runs slow.

---

### Post by malfindin on 2021-03-01
This is without a doubt the weirdest problem I have ever encountered.

---

### Post by malfindin on 2021-03-01
ONE MORE POINT OF INFO:  In Windows 10 it sees the NIC and says all drivers are installed, but fails to see any of my internal Networks unless I plug in a secondary USB NIC.  It sees my neighbors wireless but not my own.

---

### Post by malfindin on 2021-03-01
So if I wanted to try installing fvwm is it in the repository?  If not how do I install it?

---

### Post by Holger_Gehrke on 2021-03-01
> **malfindin said:**
> 
"kcmshell5 kcm_memory" which is taking an average of 55% of my processor even when I have no apps open.

I see no other posts that reference this process. In fact I'm having difficulty figuring out what it even is...google is no help. Though apparently there is a K-POP band of the same name. 


Seems you are the victim of your search engine deciding what you should see ... If I ask duckduckgo for kcmshell5 I get [this page]("https://techbase.kde.org/Development/Tutorials/KCM_HowTo#kcmshell5") in the KDE Techbase as the first hit. Seems kcmshell5 is the 'KConfig Module Shell' for KDE 5 - a program for opening modules for manipulating and showing configuration and system information - and kcm_memory is a module for showing memory usage. Do you happen to run some kind of memory usage display as a dock app ? I recall having a somewhat similar problem on XFCE; there are two dock apps in XFCE for showing the processor load and one of the two makes Xorg go crazy (around 200% CPU load; two of four cores doing nothing but running Xorg) if it runs in a panel set to automatically hide itself ...

---

### Post by malfindin on 2021-03-01
I'm 99% sure at this point that the issue was the Hybrid SSD/conventional HD.   I've replaced it and I'm starting from scratch.

LET'S CALL IT A DAY.

EVERYONE -- THANK YOU FOR YOUR HELP

---

### Post by malfindin on 2021-03-01
Yeah I was using Google. I think I have resolved the issue, but only by replacing the HD.

No I was not using any memory usage apps.

---

### Post by TheFu on 2021-03-01
> **malfindin said:**
> So if I wanted to try installing fvwm is it in the repository?  If not how do I install it?

```
sudo apt install fvwm
```

Is this a trick question?  Always assume that method, unless someone goes out of their way.

---

### Post by TheFu on 2021-03-01
> **malfindin said:**
> It's not GUI related.  I have tried MATE and LUBUNTU and KDE and it runs fine in all of them.  If you install to the HD then MATE and LUBUNTU don't see the NIC. KUBUNTU sees the NIC and runs slow.

Sorry, I didn't choose the correct words.  I was thinking the GPU drivers would be different between the fast and slow running boots.  Check those.

---

### Post by malfindin on 2021-03-02
Sometimes Desktop managers don't install with their actual names, like KDE is installed with sudo apt-get install kubuntu-desktop.

I figured it out and thank you I like it... SUPER FAST

---

### Post by TheFu on 2021-03-02
> **malfindin said:**
> Sometimes Desktop managers don't install with their actual names, like KDE is installed with sudo apt-get install kubuntu-desktop.

I figured it out and thank you I like it... SUPER FAST

fvwm isn't a DE - it is just a WM. It was created when systems had 16MB of RAM total.

---

### Post by malfindin on 2021-03-02
I may have tracked the issue down to a bad USB port on the system that was preventing correct install. It seems to generate write errors, but not read errors--which is why everything always ran great from USB, but not after install.

My final solution was to do the ENTIRE INSTALL on a different computer and then transfer the hard-drive to the Laptop.

This is also why the issues were so random and seemingly unrelated.   Just a case of random HD corruption. Thanks again for all the help.

Usually I'm the one that helps other people:)

---

### Post by malfindin on 2021-03-03
I remember those days. My first professional computer was a 486 with math co-processor and 8 meg of RAM.  I used it to run video poker game analysis software (VPExact) for my job, which at the time was running a Progressive Jackpot Gambling Team in Lake Tahoe.  I miss those days...  It took 29 hours from the time you pushed enter for it to run through the 2.6 million possible combinations of a 52 card deck.  The same calculation now runs in 5 seconds...well 10 if I'm using my phone:)

Peace be with you...

---

