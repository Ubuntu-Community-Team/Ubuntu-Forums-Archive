---
title: "nvidia driver disappeared"
date: 2023-07-20
forum: General Help
---

### Post by guine on 2023-07-20
After having my install of darktable upgrade to the new version(4.4.1) through software center I noticed that it wasn't using my GPU so I tried closing darktable and running these 2 commands which had always worked to get darktable using my GPU again in the past(usually after my computer locked with darktable open)
```
sudo modprobe nvidia-uvm
sudo rmmod nvidia-uvm
```
But after attempting the first command I got this error
```
modprobe: ERROR: could not insert 'nvidia_uvm': Key was rejected by service
```
When I had first launched darktable after the upgrade I also got a message about nvidia driver names changing(unfortunately I didn't record the message) so I started trying to see what nvidia driver was installed so I tried running
```
nvidia-smi
```
and got this message
```
NVIDIA-SMI has failed because it couldn't communicate with the NVIDIA driver. Make sure that the latest NVIDIA driver is installed and running.
```
Is there anything else I should be checking to see if I still have a NVIDIA driver installed or should I just be trying to install a new driver again?
I currently have ubuntu 23.04 installed.

---

### Post by MAFoElffen on 2023-07-20
What is the output of this?:
```

apt list nvidia-driver-* --installed

```

---

### Post by guine on 2023-07-21
```
nvidia-driver-510/lunar-updates,lunar-security,now 525.125.06-0ubuntu0.23.04.1 amd64 [installed]
nvidia-driver-525/lunar-updates,lunar-security,now 525.125.06-0ubuntu0.23.04.1 amd64 [installed,automatic]
```
Is this likely meaning its just not being found by darktable?

---

### Post by #&amp;thj^% on 2023-07-21
You show 2 nvidia drivers "nvidia-driver-510/ nvidia-driver-525/" that won't work well, only one driver install.
Remove one then reboot to see.
```
sudo apt autoremove --purge nvidia-driver-510
```
If you just want to be sure also run before the reboot and after the removal of driver 510
```
sudo apt install --reinstall nvidia-driver-525 nvidia-dkms-525
```
now reboot and paste back your "nvidia-smi"
```
Fri Jul 21 11:04:05 2023       
+---------------------------------------------------------------------------------------+
| NVIDIA-SMI 535.54.03              Driver Version: 535.54.03    CUDA Version: 12.2     |
|-----------------------------------------+----------------------+----------------------+
| GPU  Name                 Persistence-M | Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp   Perf          Pwr:Usage/Cap |         Memory-Usage | GPU-Util  Compute M. |
|                                         |                      |               MIG M. |
|=========================================+======================+======================|
|   0  NVIDIA GeForce GTX 1650 Ti     Off | 00000000:01:00.0  On |                  N/A |
| N/A   36C    P8               1W /  50W |    364MiB /  4096MiB |      7%      Default |
|                                         |                      |                  N/A |
+-----------------------------------------+----------------------+----------------------+
                                                                                         
+---------------------------------------------------------------------------------------+
| Processes:                                                                            |
|  GPU   GI   CI        PID   Type   Process name                            GPU Memory |
|        ID   ID                                                             Usage      |
|=======================================================================================|
|    0   N/A  N/A      9771      G   /usr/lib/xorg/Xorg                          216MiB |
|    0   N/A  N/A     15502      G   xfwm4                                         2MiB |
|    0   N/A  N/A    386693      G   /usr/lib/firefox/firefox                    143MiB |
+---------------------------------------------------------------------------------------+

```
```
apt policy darktable
darktable:
  Installed: 4.2.1-4
  Candidate: 4.2.1-4
  Version table:
 *** 4.2.1-4 500
        500 http://us.archive.ubuntu.com/ubuntu lunar/universe amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by guine on 2023-07-21
After removing 510 and reinstalling 525 I got this for nvidia-smi
```
NVIDIA-SMI has failed because it couldn't communicate with the NVIDIA driver. Make sure that the latest NVIDIA driver is installed and running.
```
I also ran this apt list nvidia-driver-* --installed to see what came up and got this
```
nvidia-driver-525/lunar-updates,lunar-security,now 525.125.06-0ubuntu0.23.04.1 amd64 [installed]
N: There is 1 additional version. Please use the '-a' switch to see it
```
and with the -a at the end I got this
```
nvidia-driver-525/lunar-updates,lunar-security,now 525.125.06-0ubuntu0.23.04.1 amd64 [installed]
nvidia-driver-525/lunar 525.105.17-0ubuntu1 amd64
```

---

### Post by #&amp;thj^% on 2023-07-22
Well now I suggest you follow this bit by bit, (Exactly like below)
```
sudo apt autoremove --purge nvidia*
```
Now to be sure we start with a clean palate reboot now>>
After the reboot reinstall with:
```
sudo apt install nvidia-driver-525 nvidia-dkms-525
```
The DKMS package is important so don't skip it.
One more reboot to your new nvidia driver.
I curious as to what card you have:
```
inxi -G | grep Device
  Device-1: NVIDIA TU117M [GeForce GTX 1650 Ti Mobile] driver: nvidia
  Device-2: Syntek Integrated Camera type: USB driver: uvcvideo

```
Also Wayland still not playing nice with Nvidia, I'm using x11 session:
```
inxi -G | grep x11 && inxi -G | grep wayland
  Display: x11 server: X.Org v: 1.21.1.7 driver: X: loaded: nvidia

```

---

### Post by guine on 2023-07-22
When doing the nvidia purge I got these errors
```
E: Unable to locate package nvidia-bug-report.log
E: Couldn't find any package by glob 'nvidia-bug-report.log'
E: Unable to locate package nvidia-bug-report.log.gz
E: Couldn't find any package by glob 'nvidia-bug-report.log.gz'
```
Should I try anything else before the new install?

For GPU this is what I have
```
  Device-1: Intel TigerLake-LP GT2 [Iris Xe Graphics] driver: i915 v: kernel
  Device-2: NVIDIA GA107M [GeForce RTX 3050 Mobile] driver: N/A
  Device-3: IMC Networks USB2.0 HD UVC WebCam type: USB driver: uvcvideo
```
This GPU has been pretty fussy for me and took a while to get set up correctly when I first got this computer.

---

### Post by #&amp;thj^% on 2023-07-22
Good I'm glad your here now, can you show me this please:
```
apt list --installed *xorg*
```
Your right about that card though I help with a few folks on that card, can be a real deal breaker for some on Nvidia
I would also like to see this as well before the re-install
```
inxi -G | grep wayland
```

---

### Post by guine on 2023-07-22
I have this for xorg (forgot to mention I use xorg rather than wayland for monitor profiling)
```
Listing... Done
xorg-docs-core/lunar,lunar,now 1:1.7.1-1.2 all [installed,automatic]
xorg/lunar,now 1:7.7+23ubuntu2 amd64 [installed]
xserver-xorg-core/lunar,now 2:21.1.7-1ubuntu3 amd64 [installed,automatic]
xserver-xorg-input-all/lunar,now 1:7.7+23ubuntu2 amd64 [installed,automatic]
xserver-xorg-input-libinput/lunar,now 1.2.1-1 amd64 [installed,automatic]
xserver-xorg-input-wacom/lunar,now 1:1.1.0-1ubuntu1 amd64 [installed,automatic]
xserver-xorg-legacy/lunar,now 2:21.1.7-1ubuntu3 amd64 [installed,automatic]
xserver-xorg-video-all/lunar,now 1:7.7+23ubuntu2 amd64 [installed,automatic]
xserver-xorg-video-amdgpu/lunar,now 23.0.0-1 amd64 [installed,automatic]
xserver-xorg-video-ati/lunar,now 1:19.1.0-3 amd64 [installed,automatic]
xserver-xorg-video-fbdev/lunar,now 1:0.5.0-2build1 amd64 [installed,automatic]
xserver-xorg-video-intel/lunar,now 2:2.99.917+git20210115-1 amd64 [installed,automatic]
xserver-xorg-video-nouveau/lunar,now 1:1.0.17-2build1 amd64 [installed,automatic]
xserver-xorg-video-nvidia-525/lunar-updates,lunar-security,now 525.125.06-0ubuntu0.23.04.1 amd64 [installed,automatic]
xserver-xorg-video-qxl/lunar,now 0.1.5+git20200331-3 amd64 [installed,automatic]
xserver-xorg-video-radeon/lunar,now 1:19.1.0-3 amd64 [installed,automatic]
xserver-xorg-video-vesa/lunar,now 1:2.5.0-1build4 amd64 [installed,automatic]
xserver-xorg-video-vmware/lunar,now 1:13.3.0-3.1 amd64 [installed,automatic]
xserver-xorg/lunar,now 1:7.7+23ubuntu2 amd64 [installed,automatic]

```

And for wayland I got this
```
  Display: wayland server: X.Org v: 1.22.1.8 with: Xwayland v: 22.1.8
```

---

### Post by MAFoElffen on 2023-07-22
Forgot... nvidia-smi is part of package 'nvidia-utils-525' and...

On reboot, ensure that the SecureBoot setting is set to 'disabled'. If enabled, that will cause the driver to have problems with some people with signing issues with dkms.

---

### Post by #&amp;thj^% on 2023-07-22
> **MAFoElffen said:**
> Forgot... nvidia-smi is part of package 'nvidia-utils-525' and...

On reboot, ensure that the SecureBoot setting is set to 'disabled'. If enabled, that will cause the driver to have problems with some people with signing issues with dkms.

+1 To the above
And the OP is using a Wayland session, which is horrible for Nvidia drivers
@guine can you login to a x11 session first.
```
apt policy xwayland
xwayland:
  Installed: (none)
  Candidate: 2:22.1.8-1ubuntu1
  Version table:
     2:22.1.8-1ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu lunar/main amd64 Packages

```

---

### Post by guine on 2023-07-22
When trying to install nvidia I kept getting this message
```
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
nvidia-driver-525 is already the newest version (525.125.06-0ubuntu0.23.04.1).
nvidia-dkms-525 is already the newest version (525.125.06-0ubuntu0.23.04.1).
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
```
I decided to try the whole purge reboot install reboot process over again and was still getting them same error, after a couple more reboots(once where my wireless didn't want to show up but that fixed on its own with another restart) and after the last restart I tried the install again with the same message so I tried launching darktable just to see what happened and it gave me a message that it found a gpu and seems to be rendering highly processed images faster. I did notice in one of the restarts that the system had switched back to wayland instead of x11 so I switched it back to x11. I'm wondering if my computer had just switched back to wayland without me noticing on a reboot after a recent update because darktable had been running slow(although claiming it found my gpu) since an update a computer update week or 2 ago that couldve caused everything to slow down.

---

### Post by #&amp;thj^% on 2023-07-22
I've heard all kinds of reasons in my journey with Wayland gets set without a user's knowledge with "Updates" 
I just think now Ubuntu sets Wayland as default OTB we might have to check that once in while.
So are you now all good now?
How does your "nvidia-smi" now look?

---

### Post by guine on 2023-07-22
I got this
```
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 525.125.06   Driver Version: 525.125.06   CUDA Version: 12.0     |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|                               |                      |               MIG M. |
|===============================+======================+======================|
|   0  NVIDIA GeForce ...  Off  | 00000000:01:00.0 Off |                  N/A |
| N/A   58C    P0    N/A /  35W |      5MiB /  4096MiB |      0%      Default |
|                               |                      |                  N/A |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                                  |
|  GPU   GI   CI        PID   Type   Process name                  GPU Memory |
|        ID   ID                                                   Usage      |
|=============================================================================|
|    0   N/A  N/A      7598      G   /usr/lib/xorg/Xorg                  4MiB |
+-----------------------------------------------------------------------------+
```
If thats looking like its supposed to I think it may be working correctly. I tried doing a quick edit in darktable using some of the more intensive modules and doing some out of order for the pixel pipe to test its speed and its definitely running faster now.
Thanks

---

### Post by #&amp;thj^% on 2023-07-22
Yes, Text Book on the look...Good Job!
It was fun Thank You

---

### Post by guine on 2023-07-22
Sounds good, thanks again for the help.

---

