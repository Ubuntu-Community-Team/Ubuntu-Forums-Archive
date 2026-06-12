---
title: "Ubuntu 20.04.5 Problems with NVIDIA GeForce RTX 3060 6GB Drivers"
date: 2023-03-03
forum: General Help
---

### Post by maiels12 on 2023-03-03
Hey everyone.

I have a brand new machine. The specs: AMD Ryzen 7 5800H and NVIDIA GeForce RTX 3060 GPU. I installed Ubuntu 20.04 with no problems. After a while I started to look into if my nvidia driver is visible and if the card is recognized. Well, it was not.

I am not exaggerating when I say that I tried all solutions I could find on Askubuntu, Ubuntu forums and the general internet to try and make this card visible. I would run several times one after the other into the what seems to me, the very popular, "blinking cursor in top left corner". I would easily fix this by just entering **ttyl3** and reinstalling the drivers.

Until I noticed in a comment that **nvidia-driver-525-open** is not supported on all boards and I should switch to **nvidia-driver-525** - so I did. Finally, all was working fine. I could run **nvidia-smi** and I would get results and **nvidia-settings** would contain all the GPU details and not only the "demand" or "performance" mode selection.

Previously, my system wouldn't see my second monitor which I connect through a docking station with a USB-C cable. Now I tested it and it worked! I could use a second monitor.

But not for long. Suddenly the screen turned to 0 brightness and the brightness controls (Fn keys + settings slider) wouldn't work anymore. i believe that, somehow, the USB-C port got corrupted because I would be getting this error ```
USCI_PDOS  failed (-95)
``` every time I would reboot and the docking station was plugged in (regardless if the HDMI cable was in the docking station or not). Further more, once every other boot the screen would just turn black and freeze.

 As I saw online, I fixed this by:
[LIST=1]
[*]Entering recovery mode;
[*]Enabling networking;
[*]Jump into root;
[*]Purge nvidida "**sudo apt purge nvidia***"
[*]Run "**sudo apt ubuntu-drivers install**"
[*]update grub and dpkg.
[/LIST]

When booted (finally) into the system I would run a **sudo apt update && sudo apt upgrade** just to be on the safe side. Again, the installed driver was **nvidia-driver-525-open`**. Another post suggested to just downgrade driver versions until you get the right one.

The thing is that **EVERY** other version up to **nvididia-driver-470** would brick the machine: either get stuck in boot, blanks screen (not even with blinking cursor) or right out boot but have no brightness control. And I would need to resort to the steps above. Currently, as I am writing this, I am still on **nvidia-driver-525-open** 

I am stumped. I`ve been reinstalling and updating nvidia drivers and consulting solutions for hours. Is there any way to get this card working? I no solution works I will completely reinstall the system. Maybe I just corrupted packages when I kept going so much into recovery and removing/installing packages...


P.S.: initially I even tried updating to 22.04 - no chance there. It doesn't even boot and gets stuck directly into the blinking cursor.

---

### Post by Bashing-om on 2023-03-03
maiels12 ; Hello - Welcome to the Forums.

Hummm .. autoinstall choosing the 525 version driver is unexpected.
As Nvidia recommends the 460.56 :
[https://www.nvidia.com/download/driverresults.aspx/170804/en-us/](https://www.nvidia.com/download/driverresults.aspx/170804/en-us/)
That is available in the software repo:
> 
sysop@x2204mini:~$ apt list nvidia-driver-460
Listing... Done
nvidia-driver-460/jammy-security,jammy-updates 470.161.03-0ubuntu0.22.04.1 amd64


Maybe try again to purge the 525 version driver and install " nvidia-driver-460 " ?

-worth a shot-

---

### Post by #&amp;thj^% on 2023-03-03
> **Bashing-om said:**
> maiels12 ; Hello - Welcome to the Forums.

Hummm .. autoinstall choosing the 525 version driver is unexpected.
As Nvidia recommends the 460.56 :


Maybe try again to purge the 525 version driver and install " nvidia-driver-460 " ?

-worth a shot-
I have it as : [https://www.nvidia.com/Download/index.aspx?lang=en-us](https://www.nvidia.com/Download/index.aspx?lang=en-us)
```
Version: 	525.89.02
Release Date: 	2023.2.8
Operating System: 	Linux 64-bit
Language: 	English (US)
File Size: 	394.93 MB 
```
A big plus 1 on the purge the old, before trying a reinstall.

---

### Post by Bashing-om on 2023-03-03
Ouch !!

I do stand corrected - it is the 525 recommended version for the GeForce RTX 3060 card.

Now I have to wonder how that happened on my part :(

[INDENT]peer review is a good thing
[/INDENT]

---

### Post by #&amp;thj^% on 2023-03-03
> **Bashing-om said:**
> Ouch !!


Now I have to wonder how that happened on my part :(

[INDENT]peer review is a good thing
[/INDENT]
I wouldn't waste another second on that, happens to us all...and we all know that. :)

---

### Post by maiels12 on 2023-03-04
Thanks you all. The problem is still not completely solved but at least I have something working. I basically did the same things, with some modification. 

For a more comprehensive purge of all nvidia presence on my machine I just ran ```
sudo apt purge '^nvidia-.*'
``` to make sure I get everything. I haven't mentioned before but before any new install I would always purge first.

To install the driver I resumed to choosing a driver from [here]("https://www.nvidia.com/Download/driverResults.aspx/199656/en-us/") as you guys recommended. It seems that installing the driver this way finally made the system recognize the GPU. I can see details of it in nvidia-settings and nvidia-smi.
It's funny that nvidia themselves recommend in the driver .run file interface to install it this way, because apt installers or the additional drivers from ubuntu might not be reliable.


Adding a second monitor works. Although, only in mirror or single-monitor use. Dual display just turns the screen black on the secod monitor.
The USB-C port still gets corrupted, somehow. I get the same ```
[COLOR=#000000][FONT=&amp]USCI_PDOS  failed (-95)[/FONT][/COLOR]
``` during boot, but this time it skips it and doesn't get stuck.

For the moment it is fine. I got a semi-working card. A second monitor, although nice, is not mandatory at the moment since my current machine has a way better resolution.

I booted and rebooted the system multiple times to confirm.

The weirdest part is that I still can not change brightness. At least now its stuck at around 70%.

Should I go to the nvidia forums and report this as a possible bug?

Thanks!

---

### Post by #&amp;thj^% on 2023-03-04
I'm glad things are fine for now, but soon a kernel version upgrade will/might break it again.
I need to be careful in my wording, for drivers, I nor Bashing-om recommenced the downloaded driver from Nvidia.com, but rather used it as the driver-version in our Repos to use.
I'm not one to talk though:
```
nvidia-smi
Sat Mar  4 13:39:17 2023       
+---------------------------------------------------------------------------------------+
| NVIDIA-SMI 530.30.02              Driver Version: 530.30.02    CUDA Version: 12.1     |
|-----------------------------------------+----------------------+----------------------+
| GPU  Name                  Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf            Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|                                         |                      |               MIG M. |
|=========================================+======================+======================|
|   0  NVIDIA GeForce GTX 1650 Ti      Off| 00000000:01:00.0 Off |                  N/A |
| N/A   43C    P0               16W /  50W|    819MiB /  4096MiB |     14%      Default |
|                                         |                      |                  N/A |
+-----------------------------------------+----------------------+----------------------+
                                                                                         
+---------------------------------------------------------------------------------------+
| Processes:                                                                            |
|  GPU   GI   CI        PID   Type   Process name                            GPU Memory |
|        ID   ID                                                             Usage      |
|=======================================================================================|
|    0   N/A  N/A       786      G   /usr/lib/xorg/Xorg                          652MiB |
|    0   N/A  N/A      1144      G   xfwm4                                         2MiB |
|    0   N/A  N/A    944155      G   firefox                                     126MiB |
+---------------------------------------------------------------------------------------+

```
As far as the brightness level Nvidia will only work on the HDMI port, and your laptop should have a brightness level on your keyboard for the On Screen, mine is <Fn+F6 and Fn+F5>

---

### Post by maiels12 on 2023-03-04
Well, that's the thing. The keys themselves work (exactly the ones you mentioned). The Brightness slider does go up and down. Even dragging it manually in the settings works. The brightness itself doesn't change.

---

### Post by #&amp;thj^% on 2023-03-04
You could file a bug against it, at Nvidia.com though
one final thought, which monitor is the brightness level not changing on?
EDIT: and if ti is the HDMI, check with a different cable.(You would be surprised how often this is the problem)
> Adding a second monitor works. Although, only in mirror or single-monitor use. Dual display just turns the screen black on the secod monitor.
The USB-C port still gets corrupted, somehow. I get the same 
This is now sounding more and more like a cable problem.

---

### Post by maiels12 on 2023-03-04
Well, I am currently not using the second monitor. With it I was just testing out functionality. Therefore, there is no cable involved and the brightness problem is at my main display.

---

### Post by #&amp;thj^% on 2023-03-04
Thanks for that.
your card tested out very well in what I was able to see.
what does this return please:
```
inxi -G
```
example with my hdmi active
```
inxi -Gz
Graphics:
  Device-1: NVIDIA TU117M [GeForce GTX 1650 Ti Mobile] driver: nvidia
    v: 530.30.02
  Device-2: Syntek Integrated Camera type: USB driver: uvcvideo
  Display: x11 server: X.Org v: 1.21.1.7 driver: X: loaded: nvidia
    unloaded: fbdev,modesetting,nouveau,vesa gpu: nvidia resolution:
    1: 1920x1080~120Hz 2: 4096x2160~60Hz
  API: OpenGL v: 4.6.0 NVIDIA 530.30.02 renderer: NVIDIA GeForce GTX 1650
    Ti/PCIe/SSE2


```

---

### Post by maiels12 on 2023-03-04
This is the output of ```
inxi -G
```
```
Graphics:  Device-1: NVIDIA driver: nvidia v: 525.89.02 
  Device-2: AMD driver: amdgpu v: kernel 
  Display: x11 server: X.Org 1.20.13 driver: ati,radeon 
  resolution: 2560x1600~60Hz 
  OpenGL: renderer: AMD RENOIR (DRM 3.42.0 5.15.0-67-generic LLVM 12.0.0) 
  v: 4.6 Mesa 21.2.6
```

---

### Post by #&amp;thj^% on 2023-03-04
That looks bug worthy.
will this do anything for the main display
```
xrandr --output <outputname> --brightness 0.8
```
to find that main display use:
```
xrandr --current --verbose
```
I'm now very curious.
EDIT: I keep forgetting this, is there an option in your bios for switchable-graphics? if so switch to nvidia gpu only.

---

### Post by maiels12 on 2023-03-04
```
xrandr --current --verbose
```
Displays Screen 0, DisplayPort-1 and then DP-1-0 through DP-1-4. A piece of Screen 0:
```
Screen 0: minimum 320 x 200, current 2560 x 1600, maximum 16384 x 16384eDP connected primary 2560x1600+0+0 (0x57) normal (normal left inverted right x axis y axis) 344mm x 215mm
    Identifier: 0x53
    Timestamp:  16371083
    Subpixel:   unknown
    Gamma:      1.0:1.0:1.0
    Brightness: 1.0



```
Then for ```
xrandr --output 0x53 --brightness 0.8
```
Seems to successfully change brightness.

---

### Post by #&amp;thj^% on 2023-03-04
I'm now very curious.
EDIT: I keep forgetting this, is there an option in your bios for switchable-graphics? if so switch to nvidia gpu only. 
then run some of the key functions

---

### Post by maiels12 on 2023-03-04
Yeah, I can choose from "Switchable" and "Discrete" - Discrete would be the nvidia GPU.
I chose Discrete. It seems that the brightness buttons now works, with a weird behavior nonetheless.
At around 30% brightness just jumps to full bright and reverts if it is set below or higher than that.

---

### Post by #&amp;thj^% on 2023-03-04
That is normal for linux and hardware.

---

### Post by maiels12 on 2023-03-04
Well, then I guess it works fine. I`ll give it a try again with a second monitor. It seems that the output of ```
xrandr --current --verbose
``` has changed too.
Thanks a bunch for the help!

---

### Post by #&amp;thj^% on 2023-03-04
Happy to, enjoy.;)

---

