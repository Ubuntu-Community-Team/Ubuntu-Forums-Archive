---
title: "Nvidia problems on Laptop Thinkbook"
date: 2023-05-02
forum: General Help
---

### Post by pautorras on 2023-05-02
Hi,

I've some problems with nvidia driver.

Using inxi -iG it shows:
```

Graphics:
  Device-1: Intel Alder Lake-P Integrated Graphics driver: i915 v: kernel
  Device-2: NVIDIA GA107M [GeForce RTX 2050] driver: N/A
  Device-3: Luxvisions Innotech Integrated Camera type: USB
    driver: uvcvideo
  Display: x11 server: X.Org v: 1.21.1.4 driver: X: loaded: modesetting
    unloaded: fbdev,vesa gpu: i915 resolution: 1: 1920x1080~60Hz
    2: 1920x1080~60Hz 3: 1920x1200~60Hz
  OpenGL: renderer: Mesa Intel Graphics (ADL GT2) v: 4.6 Mesa 22.2.5
Network:
  Device-1: Intel Alder Lake-P PCH CNVi WiFi driver: iwlwifi
  IF: wlp0s20f3 state: down mac: 3c:e9:f7:42:25:c5
  Device-2: Intel Ethernet I219-V driver: e1000e
  IF: enp0s31f6 state: down mac: 98:8f:e0:65:0e:89
  Device-3: ASIX AX88179 Gigabit Ethernet type: USB driver: ax88179_178a
  IF: enx34298f7661fc state: up speed: 1000 Mbps duplex: full
    mac: 34:29:8f:76:61:fc
  IP v4: 192.16.70.80/24 type: noprefixroute scope: global
  IP v6: fe80::dd47:fbdf:704d:d073/64 type: noprefixroute scope: link
  IF-ID-1: vmnet1 state: unknown speed: N/A duplex: N/A
    mac: 00:50:56:c0:00:01
  IP v4: 192.168.102.1/24 scope: global
  IP v6: fe80::250:56ff:fec0:1/64 scope: link
  IF-ID-2: vmnet8 state: unknown speed: N/A duplex: N/A
    mac: 00:50:56:c0:00:08
  IP v4: 172.16.216.1/24 scope: global
  IP v6: fe80::250:56ff:fec0:8/64 scope: link
  WAN IP: 192.16.70.80

```

I've tried with X.Org X Server and also with NVIDIA drivers, and I'm getting flicker issues.
How can I fix it?

Best Regards,
Pau

---

### Post by #&amp;thj^% on 2023-05-02
I'm not sure I understand here?
I see no nvidia driver installed???
Please show us this:
```
nvidia-smi
```
And:
```
cat /proc/driver/nvidia/version

```

---

### Post by pautorras on 2023-05-03
Hi,

If I use owner nvidia driver 530:
System behaviour:
[LIST]
[*]Less flickering. But not 0.
[*]System is slower to show desktop on reboot or power on.
[*]Some apps, like google chrome, are a lot slower, and it makes some strange effects loading the app.
[/LIST]

nvidia-smi output:
```

No devices were found

```

cat /proc/driver/nvidia/version output:
```

NVRM version: NVIDIA UNIX Open Kernel Module for x86_64  530.41.03  Release Build  (dvs-builder@U16-T02-35-3)  Thu Mar 16 19:33:35 UTC 2023
GCC version:  gcc version 11.3.0 (Ubuntu 11.3.0-1ubuntu1~22.04.1) 

```


=====================================================================================

If I use X.Org X server (free source code driver):
System behaviour:
[LIST]
[*]Notorious flickering.
[*]System is very quick on all apps and reboot/power on operations.
[/LIST]

nvidia-smi output:
```

bash: /usr/bin/nvidia-smi: File or folder does not exist

```

cat /proc/driver/nvidia/version output:
```

NVRM version: NVIDIA UNIX Open Kernel Module for x86_64  530.41.03  Release Build  (dvs-builder@U16-T02-35-3)  Thu Mar 16 19:33:35 UTC 2023
GCC version:  gcc version 11.3.0 (Ubuntu 11.3.0-1ubuntu1~22.04.1) 
cat: 'output:': File or folder does not exist

```


Thanks in advance.

Pau

---

### Post by #&amp;thj^% on 2023-05-03
You would be better off with the driver from our repos instead of the .run binary 
```
cat /proc/driver/nvidia/version
NVRM version: NVIDIA UNIX x86_64 Kernel Module  530.41.03  Thu Mar 16 19:48:20 UTC 2023
GCC version:  gcc version 12.2.0 (Ubuntu 12.2.0-17ubuntu1) 

```
```
 nvidia-smi
Wed May  3 11:40:24 2023       
+---------------------------------------------------------------------------------------+
| NVIDIA-SMI 530.41.03              Driver Version: 530.41.03    CUDA Version: 12.1     |
|-----------------------------------------+----------------------+----------------------+
| GPU  Name                  Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf            Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|                                         |                      |               MIG M. |
|=========================================+======================+======================|
|   0  NVIDIA GeForce GTX 1650 Ti      Off| 00000000:01:00.0  On |                  N/A |
| N/A   37C    P8                2W /  N/A|    465MiB /  4096MiB |     14%      Default |
|                                         |                      |                  N/A |
+-----------------------------------------+----------------------+----------------------+
                                                                                         
+---------------------------------------------------------------------------------------+
| Processes:                                                                            |
|  GPU   GI   CI        PID   Type   Process name                            GPU Memory |
|        ID   ID                                                             Usage      |
|=======================================================================================|
|    0   N/A  N/A      5844      G   /usr/lib/xorg/Xorg                          315MiB |
|    0   N/A  N/A      6671      G   xfwm4                                         2MiB |
|    0   N/A  N/A    570935      G   /usr/lib/firefox/firefox                    145MiB |
+---------------------------------------------------------------------------------------+


```
with added PPA:
```
 apt policy nvidia-driver-530
nvidia-driver-530:
  Installed: 530.41.03-0ubuntu2
  Candidate: 530.41.03-0ubuntu2
  Version table:
 *** 530.41.03-0ubuntu2 500
        500 https://ppa.launchpadcontent.net/graphics-drivers/ppa/ubuntu lunar/main amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by pautorras on 2023-05-04
Dear @1fallen,

How can I install the driver from the repos?

Thanks,
Pau

---

### Post by #&amp;thj^% on 2023-05-04
I've been spoiled by the PPA found here: [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
And the PPA is optional but highly suggested for a nicer install.
After the PPA is added run:(One Line at a time)
```
sudo apt update
sudo apt install nvidia-driver-525 nvidia-dkms-525 nvidia-settings
```
If you need more help just ask. :)
Please remove the old driver first though.
EDIT: If you want or need the 530 driver just change all 525 to 530
```
sudo apt install nvidia-driver-530 nvidia-dkms-530 nvidia-settings
```

---

### Post by pautorras on 2023-05-05
Hi all,

As @1fallen said, I've installed nvidia drivers from apt command. And some unexpected behavior has been fixed (like google chome take long time to init).
But, when I use software like Anydesk or OBS, things go wrong, and flickering appears again.

I have found on internet problems with Anydesk and OBS, and it refers to "allow flipping" nvidia setting. Turning off this setting, it seems to work great.
[https://www.reddit.com/r/AnyDesk/comments/1171i53/anydesk_flickering_when_using_nvidia_driver_linux/](https://www.reddit.com/r/AnyDesk/comments/1171i53/anydesk_flickering_when_using_nvidia_driver_linux/)
[https://obsproject.com/forum/threads/nvidia-flipping-toggling.101322/](https://obsproject.com/forum/threads/nvidia-flipping-toggling.101322/)

The problem is that I don't find any "allow flipping" in Nvidia settings.
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292172&stc=1[/IMG]
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292173&stc=1[/IMG]
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292176&stc=1[/IMG]
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292177&stc=1[/IMG]

In PRIME Profiles it appears a checklist with:
NVIDIA (Performance Mode)
NVIDIA On-Demand
Intel (Power Saving Mode) [U][B](this option is grayed)

[/B][/U]
See attached nvidia-smi code and cat code:

```

pau@pau-ThinkBook-16-G4-IAP:~$ nvidia-smi
Fri May  5 12:40:58 2023       
+---------------------------------------------------------------------------------------+
| NVIDIA-SMI 530.41.03              Driver Version: 530.41.03    CUDA Version: 12.1     |
|-----------------------------------------+----------------------+----------------------+
| GPU  Name                  Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf            Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|                                         |                      |               MIG M. |
|=========================================+======================+======================|
|   0  NVIDIA GeForce RTX 2050         Off| 00000000:01:00.0 Off |                  N/A |
| N/A   45C    P0               N/A /  N/A|      5MiB /  4096MiB |      0%      Default |
|                                         |                      |                  N/A |
+-----------------------------------------+----------------------+----------------------+
                                                                                         
+---------------------------------------------------------------------------------------+
| Processes:                                                                            |
|  GPU   GI   CI        PID   Type   Process name                            GPU Memory |
|        ID   ID                                                             Usage      |
|=======================================================================================|
|    0   N/A  N/A      2227      G   /usr/lib/xorg/Xorg                            4MiB |
+---------------------------------------------------------------------------------------+

```

```

pau@pau-ThinkBook-16-G4-IAP:~$ cat /proc/driver/nvidia/version
NVRM version: NVIDIA UNIX x86_64 Kernel Module  530.41.03  Thu Mar 16 19:48:20 UTC 2023
GCC version:  gcc version 11.3.0 (Ubuntu 11.3.0-1ubuntu1~22.04) 

```


[B][U]How can I turn off "Allow flipping"??
[/U][/B]

Best Regards,

Pau

---

### Post by #&amp;thj^% on 2023-05-05
So one of those cards then, I suggest  "Force Full Composition Pipeline"
Also did you add the PPA?
The check box can be found by going to "X Server Display Configuration" in nvidia-settings, selecting the desired monitor, and then clicking "Advanced" at the bottom.
Also screenshot attached.
Now if it still don't work please show:
```
inxi -Gas
```

---

### Post by pautorras on 2023-05-05
Hi @fallen1,

I don't have the options that show your thumbnails.

inxi -Gas output:
```

pau@pau-ThinkBook-16-G4-IAP:~$ inxi -Gas
Graphics:
  Device-1: Intel Alder Lake-P Integrated Graphics vendor: Lenovo
    driver: i915 v: kernel ports: active: HDMI-A-1,eDP-1
    empty: DP-1, DP-2, DP-3, DP-4 bus-ID: 00:02.0 chip-ID: 8086:46a6
    class-ID: 0300
  Device-2: NVIDIA GA107M [GeForce RTX 2050] vendor: Lenovo driver: nvidia
    v: 530.41.03 alternate: nvidiafb,nouveau,nvidia_drm pcie: gen: 1
    speed: 2.5 GT/s lanes: 4 link-max: gen: 4 speed: 16 GT/s lanes: 16
    bus-ID: 01:00.0 chip-ID: 10de:25a9 class-ID: 0302
  Device-3: Luxvisions Innotech Integrated Camera type: USB
    driver: uvcvideo bus-ID: 3-6:7 chip-ID: 30c9:0030 class-ID: 0e02
    serial: 0001
  Display: x11 server: X.Org v: 1.21.1.4 compositor: gnome-shell v: 42.5
    driver: X: loaded: modesetting,nouveau,nvidia unloaded: fbdev,vesa
    gpu: i915 display-ID: :1 screens: 1
  Screen-1: 0 s-res: 3840x1200 s-dpi: 96 s-size: 1016x318mm (40.0x12.5")
    s-diag: 1065mm (41.9")
  Monitor-1: HDMI-1 mapped: HDMI-A-1 pos: right model: Dell U2414H
    serial: 9TG4644L4AUL built: 2014 res: 1920x1080 hz: 60 dpi: 93 gamma: 1.2
    size: 527x296mm (20.7x11.7") diag: 604mm (23.8") ratio: 16:9 modes:
    max: 1920x1080 min: 720x400
  Monitor-2: eDP-1 pos: primary,left built: 2020 res: 1920x1200 hz: 60
    dpi: 142 gamma: 1.2 size: 344x215mm (13.5x8.5") diag: 406mm (16")
    ratio: 16:10 modes: 2560x1600
  OpenGL: renderer: Mesa Intel Graphics (ADL GT2) v: 4.6 Mesa 22.2.5
    direct render: Yes
Sensors:
  System Temperatures: cpu: 27.8 C mobo: N/A
  Fan Speeds (RPM): N/A



```

---

### Post by #&amp;thj^% on 2023-05-05
Do you have a choice in your Bios for selecting the Nvidia card only? (Not just prime-select)
Also if that's not an option in your Bios and I don't like offering things like this, but If your brave enough you can create a file called "**/etc/X11/xorg.conf.d/20-nvidia.conf"**

And add these lines
```

Section "Device"
        Identifier "Nvidia Card"
        Driver     "nvidia"
        VendorName "NVIDIA Corporation"
        BoardName  "GeForce RTX 2050"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    Option         "metamodes" "nvidia-auto-select +0+0 {ForceFullCompositionPipeline=On}"
    Option         "AllowIndirectGLXProtocol" "off"
    Option         "TripleBuffer" "on"
EndSection

```
You will have to reboot after the edit.

---

### Post by #&amp;thj^% on 2023-05-06
Did I lose you?

---

### Post by pautorras on 2023-05-08
Hi @1fallen,


I don't have BIOS option to select only Nvidia graphic card.
About create the file 20-nvidia.conf, I've some questions.


If I create the file:
¿Could be changed by Ubuntu upgrade or ditro upgrade?
My PC is a notebook, and I move with him everywhere. Sometimes I use only the embedeed display, sometimes I have one extra monitor and also with two extra monitors with dock station. The monitors are not always the same monitors model. ¿Could this file have problems with these constant changes of display?




Thanks in advance.


Pau

---

### Post by #&amp;thj^% on 2023-05-08
> **pautorras said:**
> Hi @1fallen,


I don't have BIOS option to select only Nvidia graphic card.
About create the file 20-nvidia.conf, I've some questions.


If I create the file:
¿Could be changed by Ubuntu upgrade or ditro upgrade?
My PC is a notebook, and I move with him everywhere. Sometimes I use only the embedeed display, sometimes I have one extra monitor and also with two extra monitors with dock station. The monitors are not always the same monitors model. ¿Could this file have problems with these constant changes of display?




Thanks in advance.


Pau
Constant change can be a real deal breaker, and the Dock has been added new to me, and I'm sure where you will see the tearing is in the monitors connected to the Dock.
If you have Intel for internal GPU that's worth a look.
Example: I have "Intel CometLake-U GT2 [UHD Graphics" with HDMI port to a 55inch TV, I'll see some tearing there but was solved with:
```
sudo mkdir -p /etc/X11/xorg.conf.d 
sudo touch /etc/X11/xorg.conf.d/20-intel.conf
sudo nano /etc/X11/xorg.conf.d/20-intel.conf
####With This added
Section "Device"
    Identifier "Intel Graphics"
    Driver "i915"
    Option "TearFree"    "true"
    Option "AccelMod"    "uxa"
    Option "DRI"         "3" 
EndSection

```
I think your dock has some of the problems with Video Quality.
```
Graphics:
  Device-1: Intel CometLake-U GT2 [UHD Graphics] driver: i915 v: kernel
  Device-2: IMC Networks Integrated Camera type: USB driver: uvcvideo
  Display: x11 server: X.Org v: 1.21.1.7 with: Xwayland v: 22.1.8 driver: X:
    loaded: modesetting unloaded: fbdev,vesa dri: iris gpu: i915 resolution:
    1: N/A 2: 1920x1080~60Hz
  API: OpenGL v: 4.6 Mesa 23.0.2 renderer: Mesa Intel UHD Graphics (CML GT2)

```

---

### Post by MAFoElffen on 2023-05-08
Just an observation. Wrong place in nVidia settings... It's there. Look at my attachment.

---

### Post by pautorras on 2023-05-09
Hi @1fallen,

I have problems only with the embedded display on notebook. With second or third display connected directly by HDMI cable or by dock station, don't give me any problems.
In the integrated notebook display, I've problems only when I execute programs like Anydesk and OBS Studio. Other programs and apps, are working without problems.

Thanks!

Pau

---

### Post by pautorras on 2023-05-12
Hi @1fallen, do you have any new idea from last reply?

Thanks in advance

---

