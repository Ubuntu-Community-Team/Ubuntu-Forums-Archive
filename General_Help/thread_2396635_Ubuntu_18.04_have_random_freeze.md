---
title: "Ubuntu 18.04 have random freeze"
date: 2018-07-18
forum: General Help
---

### Post by tackskull on 2018-07-18
Hi there,

I am a new linux user and I have choose ubuntu in dual boot with windows 10 (1tb hard disk with 800g for ubuntu and 200g for windows10). After a month I've installed it on my laptop something weird is happening. 

Some times the ubuntu get totally freeze without reason, in this situation I am not able to do anything, I try some button combination but nothing happen, the only thing I am able to so is just to move the mouse cursor, nothing else. I am only able to shut down the pc with the power button.

For having some information I used the inxi -Fz command on terminal and this is what I get:  

```

System:    Host: tackskull-Lenovo-ideapad-320-15ABR Kernel: 4.15.0-24-generic x86_64
           bits: 64
           Desktop: Gnome 3.28.1 Distro: Ubuntu 18.04 LTS
Machine:   Device: laptop System: LENOVO product: 80XS v: Lenovo ideapad 320-15ABR serial: N/A
           Mobo: LENOVO model: LNVNB161216 v: SDK0J40709WIN serial: N/A
           UEFI: LENOVO v: 5QCN18WW date: 07/13/2017
Battery    BAT0: charge: 13.7 Wh 46.0% condition: 29.8/30.0 Wh (99%)
CPU:       Quad core AMD A10-9620P RADEON R5 10 COMPUTE CORES 4C+6G (-MCP-) 
           cache: 4096 KB
           clock speeds: max: 2500 MHz 1: 1763 MHz 2: 1624 MHz 3: 1584 MHz
           4: 1592 MHz
Graphics:  Card-1: Advanced Micro Devices [AMD/ATI] Carrizo
           Card-2: Advanced Micro Devices [AMD/ATI] Topaz XT [Radeon R7 M260/M265 / M340/M360 / M440/M445]
           Display Server: x11 (X.Org 1.19.6 ) drivers: amdgpu,amdgpu
           Resolution: 1920x1080@50.00hz
           OpenGL: renderer: AMD CARRIZO (DRM 3.23.0 / 4.15.0-24-generic, LLVM 6.0.0)
           version: 4.5 Mesa 18.0.5
Audio:     Card-1 Advanced Micro Devices [AMD] Device 157a
           driver: snd_hda_intel
           Card-2 Advanced Micro Devices [AMD/ATI] Kabini HDMI/DP Audio
           driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.15.0-24-generic
Network:   Card-1: Qualcomm Atheros QCA9377 802.11ac Wireless Network Adapter
           driver: ath10k_pci
           IF: wlp1s0 state: down mac: <filter>
           Card-2: Realtek RTL8111/8168/8411 PCIE Gigabit Ethernet Controller
           driver: r8169
           IF: enp2s0 state: up speed: 100 Mbps duplex: full mac: <filter>
           Card-3: Atheros
           IF: null-if-id state: N/A speed: N/A duplex: N/A mac: N/A
Drives:    HDD Total Size: 1000.2GB (65.7% used)
           ID-1: /dev/sda model: WDC_WD10SPZX size: 1000.2GB
Partition: ID-1: / size: 693G used: 609G (93%) fs: ext4 dev: /dev/sda6
           ID-2: swap-1 size: 0.97GB used: 0.00GB (0%)
           fs: swap dev: /dev/zram0
           ID-3: swap-2 size: 0.97GB used: 0.00GB (0%)
           fs: swap dev: /dev/zram1
           ID-4: swap-3 size: 0.97GB used: 0.00GB (0%)
           fs: swap dev: /dev/zram2
           ID-5: swap-4 size: 0.97GB used: 0.00GB (0%)
           fs: swap dev: /dev/zram3
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 0.0C mobo: N/A gpu: 59.0,N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 243 Uptime: 1:07 Memory: 2771.6/7424.7MB
           Client: Shell (bash) inxi: 2.3.56

```


Can you guys help me to solve this annoing trouble? Thanks

---

### Post by kc1di on 2018-07-18
There have been problems with the 4.15.0-24-generic x86_64 kernel. I would downgrade for now to the 4.15.0-23 version and see if that fixes the problem.  Later on 4.15.0-26 or so may work better.

---

### Post by tackskull on 2018-07-18
I am not understanding, I don't know anything about pc stuff, can you tell me what and how have I to do?

---

### Post by kc1di on 2018-07-18
you may already have the older kernel installed, when you boot up you can get to the grub menu by hitting the esc key just has it begins to boot.
in the grub menu you will find a list of installed kernels - if it's there select 4.15.0-23 instead of 4.15.0-24.  If it's not there you can install it via synaptic but doing a search for```
kernel-4.15.0
```.

---

### Post by tackskull on 2018-07-20
ok I did it, will se if the freeze is fixed. Now each time I turn on my pc I have to do this or is the kernel now  fixed on 4.15.0-23?

---

### Post by tackskull on 2018-07-23
I am keep using Ubuntu and I am having the issue again, so nothing changed. It seems the problem happen when I am managing many heavy archives ( I am managing a lot of them) or when I have many tabs open on firefox. Sometimes happen when I do some stuff togheter.

My pc is a laptop lenovo ideapad 320:

processor: AMD A10-9620P
Ram: 8Gb
video card: AMD Radeon R7
Hard disk: 1Tb

---

### Post by tackskull on 2018-07-31
Can you guys help me with this? I would be very thankfull

---

### Post by dragonfly41 on 2018-07-31
> [COLOR=#000000]It seems the problem happen when I am managing many heavy archives ( I am managing a lot of them) or when I have many tabs open on firefox. Sometimes happen when I do some stuff togheter.[/COLOR]
Launch System Tools > System Monitor (GUI)
and inspect memory usage for all your running processes.

Multiple tabs consumes memory per tab.

---

### Post by BFG on 2018-08-15
**(Workaround below)**

I've just been having a similar nightmare with a fresh build of 18.04.1 on a HP all-in-one device.
Similar to a laptop, it has a hybrid graphics card with AMD R7 A360 GPU + Intel HD Graphics 4600.

What would happen is that after login the system would hard freeze. Both on Unity and my preferred XFCE. Not even REISUB or ssh would get it back, needing a hard power button reset. The only way to use the system at all was to put "nomodeset" into grub, but that resulted in a 800x600 display.

I read a lot of suggestions to try the open source pro version from the AMD site, but they don't list 18.04 support for the R7.    I don't need fancy graphics capability, I just need a bigger display.

I found a workaround here which worked for me:
[https://unix.stackexchange.com/questions/360709/how-to-blacklist-amdgpu](https://unix.stackexchange.com/questions/360709/how-to-blacklist-amdgpu) 

```
Edit /etc/modprobe.d/blacklist.conf and added the following line:
blacklist amdgpu

Then
sudo update-initramfs -u

and reboot
```

As far as I can tell the amdgpu drivers are unstable in kernel 4.15 and it's causing a lot of sudden freezes for people after doing an update.  Might not be your problem, but worth a try. For this AMD problem there are all kinds of bug reports, such that it's difficult to know which to contribute to. 

I tried 4.17 upstream and it just added problems with a black screen, and I don't really have the time to play with working a proper solution.  I'm going to wait for things to settle down in future releases. If you just need it working then this workaround might be enough

---

### Post by BFG on 2018-09-14
Update. The problem is still present on 4.15.0-34

---

### Post by biomaniac on 2018-09-19
Hey. Same issue here.
Ubuntu just hang up radomly :confused:

---

### Post by sgian on 2018-09-19
I've been dealing with a random freeze too, for a while on Kubuntu 18.04.  It seems related to firefox and my wireless adapter.  So now that I don't use firefox, it doesn't happen as much.  If you know about what time it froze, you can look in the syslog for clues as to what happened, it can be reached in terminal by.
```

nano /var/log/syslog

```
Then hold the page down key until you reach the time that it froze.  "Ctrl-x" will close nano. Or if you have a gui tool for looking at the syslog, that may work too.

---

### Post by biomaniac on 2018-09-19
> **sgian said:**
>  It seems related to firefox and my wireless adapter. 


With firefox? i use chrome and it looks the same. Maybe with wifi. Im noob with syslog but will check it later. 
cheers

---

### Post by jfca283 on 2018-09-27
Hi, 
I've suffered the same as this thread details.
I am using the 4.5.0.34 kernel version. Anybody can offer me a solution to this situation?
My pc is a i78gb ram and I am using a 240 gb ssd drive.
Thank you.

---

### Post by mastablasta on 2018-09-27
> **sgian said:**
> I've been dealing with a random freeze too, for a while on Kubuntu 18.04.  It seems related to firefox and my wireless adapter.  So now that I don't use firefox, it doesn't happen as much.  If you know about what time it froze, you can look in the syslog for clues as to what happened, it can be reached in terminal by.
```

nano /var/log/syslog

```
Then hold the page down key until you reach the time that it froze.  "Ctrl-x" will close nano. Or if you have a gui tool for looking at the syslog, that may work too.


exactly. the "metoo campaign" will get us nowhere in this case. you need to check what is causing the issue then isolate it. i bet people here have different hardware configuration. so first you need to see if you all have the same GPU chip (or at least same brand). it could well be the GPU drivers. GPU drivers usually cause a sudden lock up.

next is gradual worsening until it all stops. this could be monitored and should be noticeable in system monitoring tools (e.g. memory leaks).

finally logs - it there was a sudden error then it would likely be recorded.

---

### Post by jfca283 on 2018-09-27
I receive a message of "radeon ring stalled for more than ..." when I go to the console.
There is not much information about this issue.
I'm a bit lost now with this error...

---

### Post by mastablasta on 2018-09-28
but at least it points to possible GPU driver error. my suggestion is to try and load a newer GPU driver. also check their launchpad for any known issues. 

since new ubuntu has the new wayland and the old xorg, how about switching between the two? does it help?

---

### Post by jfca283 on 2018-09-28
How do I load a newer driver? Via ppa? I think my GPU is a bit older, so I am afraid it won't be supported by new drivers...

---

### Post by jfca283 on 2018-10-01
> I recently installed the new open drive via ppa. The problem persists. So, I've been thinking in buying a cheap NVIDIA card.
Do you think this will solve the freezing and hanging problem with my gpu?
I am still suffering bugs, I assume, with ubuntu.
The system just freezes om every session I use ubuntu.
Rebooting constantly the system will damage my ssd disk?

---

### Post by RHasudunganH on 2018-10-09
It also happen to me. Sometimes my laptop hang/ freeze and only restart using POWER button. At least  1 day happen 1 time, in everyday. Need help.

---

### Post by barben360 on 2018-10-09
Do you have a GPU? That could be graphics drivers.
You can go to "logs" application to see if there are some errors that seem weird or which come back a lot.
In a terminal you can also use htop to see your system's state when it is freezing (maybe RAM is full and system is using the swap space?)
Try to have your system up to date too:

sudo apt update
sudo apt upgrade
sudo apt dist-upgrade

---

### Post by syscl on 2018-10-15
Me as well. I did a fresh install of Ubuntu 18.04.1 LTS, along with updating the kernel to 4.15.0-36, but the desktop environment (Gnome 3.28) always forced me to re-login again. And today, the system hangs at all and I have to give it a hard reboot by pressing the power button.

---

### Post by wildmanne39 on 2018-10-15
Hello syscl, if you want help resolving your issue please start your own thread.

Thanks

---

### Post by hefese on 2018-11-23
Same issue here.... My ubuntu 18.04.1 is fresh installation and the kernel version is 4.15.0-**39**-generic. The first post in this topic is sent in 4 months ago and according to the first poster in this topic, his kernel version is 4.15.0-**24 **. So guys please solve it from now on.

---

### Post by QIII on 2018-11-23
hefese, please start your own thread.

Since this thread has turned into a hijack fest, it is now closed.

---

