---
title: "Using youtube slows down my computer"
date: 2016-05-16
forum: General Help
---

### Post by 1two3 on 2016-05-16
I had this problem before when I had Ubuntu Desktop 14.04 64bit LTS with LVM and disk encryption.
I remember writing some command in the terminal which showed that it's not a RAM problem but a CPU problem. 

I reinstalled Ubuntu and at the same time I installed 16.04 this time and WITHOUT LVM and disk encryption in case it was that which was slowing the computer down. 

But the computer still slows down. 

In software & Updates > Additonal drivers it says that it's using the x.org server Nouveau display driver (open source) which I've read is the best driver to use on linux if you having Nvidia GPU.

I have Intel Core i5-3230M 2.6GHz(3.2GHz) and Nvidia GeForce GT 630M with 1GB Dedicated VRAM. 
I also have 8GB DDR3 Memory (RAM).
I have a 500GB HDD. No SSD.

Please, help me.. this is such a crippling problem :<

---

### Post by oldrocker99 on 2016-05-16
> **1two3 said:**
> 

In software & Updates > Additonal drivers it says that it's using the x.org server Nouveau display driver (open source) which I've read is the best driver to use on linux if you having Nvidia GPU.



I don't know where you read this, but the nVidia driver is well-known to be far superior to the Nouveau driver, and you should get far better results with the nVidia driver. 

If you had an ATI card, the open source radeon drivers are far superior to ATI's drivers, which is why they're not available in 16.04.

---

### Post by 1two3 on 2016-05-16
> **oldrocker99 said:**
> I don't know where you read this, but the nVidia driver is well-known to be far superior to the Nouveau driver, and you should get far better results with the nVidia driver. 

If you had an ATI card, the open source radeon drivers are far superior to ATI's drivers, which is why they're not available in 16.04.

I just switched to an Nvidia driver instead.
There are 4 different ones to choose between.
2 of them are legacy drivers. 
All of them have the (propieretary) tag and the one chose was the latest non legacy driver which also had a (tested) tag.
I loaded up steam and watched a video trailer for a game and my computer became super slow after that, it's still really slow even after I shut off steam.

---

### Post by $yl9pAR%t on 2016-05-16
To be sure you have nvidia driver in use, please show us output of this command:

```
inxi -b
```

---

### Post by 1two3 on 2016-05-16
> **mefisto888 said:**
> To be sure you have nvidia driver in use, please show us output of this command:

```
inxi -b
```

Card-1: Intel 3rd Gen Core processor Graphics Controller
           Card-2: NVIDIA GF108M [GeForce GT 630M]
           Display Server: X.Org 1.18.3 driver: nvidia
           Resolution: 1920x1080@59.97hz
           GLX Renderer: GeForce GT 630M/PCIe/SSE2

---

### Post by 1two3 on 2016-05-17
After some searching I found out that the additional drivers that are available with Ubuntu are never the latest drivers. 
You have to manually go to Nvidias website and download and install the latest driver.

I'm currently reading through this: [http://us.download.nvidia.com/XFree86/Linux-x86_64/310.32/README/index.html](http://us.download.nvidia.com/XFree86/Linux-x86_64/310.32/README/index.html)

But I'm not sure if this guide is valid for me?
Can you look at this requirements page pease? [http://us.download.nvidia.com/XFree86/Linux-x86_64/310.32/README/minimumrequirements.html](http://us.download.nvidia.com/XFree86/Linux-x86_64/310.32/README/minimumrequirements.html)

Can I follow that guide when I have a Ubuntu Desktop 16.04 64bit LTS?

---

### Post by howefield on 2016-05-17
> **1two3 said:**
> After some searching I found out that the additional drivers that are available with Ubuntu are never the latest drivers. 
You have to manually go to Nvidias website and download and install the latest driver.

Alternatively for the latest nvidia drivers have a look at : [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

---

### Post by 1two3 on 2016-05-17
> **howefield said:**
> Alternatively for the latest nvidia drivers have a look at : [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

What is that? 
I've read the whole page but I still don't understand what I just read lol

This is a list of the drivers I can choose between from Software & Updates > Additional drivers:


[LIST=1]
[*]NVIDIA binary driver - version 361.42 from nvidia-361 (proprietary, tested)
[*]NVIDIA legacy binary driver - version 304.131 from nvidia 304-updates (proprietary)
[*]NVIDIA binary driver - version 340.96 from nvidia-340 (proprietary)
[*]X.Org X server - Nouveau display driver from xserver-xorg-video-nouveau (open source)
[*]NVIDIA legacy binary driver - version 304.131 from nvidia-304 (proprietary)
[/LIST]


[B]Bios mode is legacy bios btw, should I try the driver #2?
[/B]

I also have another device in Software & Updates > Additional drivers that says "Unknown: Unknown" and below it "This device is not working" with two options:

[LIST=1]
[*]Using Processor microcode firmware for Intel CPUs from intel-microcode (proprietary)
[*]Do not use the device
[/LIST]

Currently the #2 option is being used. I didn't have this unknown device listed in Addtional drivers in Ubuntu 14.04. It appeared in Ubuntu 16.04 only and since I this same problem with computer becoming slow every time I watch some kind of video on both ubuntu installs I don't think this unknown driver is causing the issue but what do I know :)
Please, let me know if there anything else I can tell you that can help figure out what's wrong, The computer is basically unusable when it becomes so slow all the time. 
I don't have this problem when I install Windows on this computer.

---

### Post by 1two3 on 2016-05-17
> **howefield said:**
> Alternatively for the latest nvidia drivers have a look at : [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

Oh, I think I understand what that is now..
It's basically a tool that auto updates and configures your nvidia driver for you?

I am a bit confused by install instructions though.. can you tell me how to install it?
Sorry for being a super noobie about this.. strange that it should be so hard for me to follow their install instructions :P

---

### Post by $yl9pAR%t on 2016-05-17
Before you will give a try this PPA suggested by howefield try again [COLOR=#000000]nvidia-361 (proprietary, tested).

I guess you have now nvidia-340 so do it this way:

1. Go to additionall drivers
2. Choose [/COLOR][COLOR=#000000]xserver-xorg-video-nouveau driver
3. Reboot
4. Choose [/COLOR][COLOR=#000000]nvidia-361 (proprietary, tested)
5. Reboot[/COLOR]

---

### Post by 1two3 on 2016-05-17
> **mefisto888 said:**
> Before you will give a try this PPA suggested by howefield try again [COLOR=#000000]nvidia-361 (proprietary, tested).

I guess you have now nvidia-340 so do it this way:

1. Go to additionall drivers
2. Choose [/COLOR][COLOR=#000000]xserver-xorg-video-nouveau driver
3. Reboot
4. Choose [/COLOR][COLOR=#000000]nvidia-361 (proprietary, tested)
5. Reboot[/COLOR]

I'm already using the 361 and have also done a reboot.

---

### Post by $yl9pAR%t on 2016-05-17
Did you switch to 361 directly from nouveau or from other nvidia driver?

---

### Post by 1two3 on 2016-05-17
> **mefisto888 said:**
> Did you switch to 361 directly from nouveau or from other nvidia driver?

From the Nouveau driver.

---

### Post by howefield on 2016-05-17
> **1two3 said:**
> Oh, I think I understand what that is now..
It's basically a tool that auto updates and configures your nvidia driver for you?

Sorry, had to go earlier.

Yes that's all it is, an easier way to get more up to date drivers than what you'll find in "additional drivers" .. 164.19 at the moment. Although I only posted it to give you an alternative to the riskier method of installing them yourself via the nvidia website. For what it is worth I don't think you'd see much (any) difference between the 361 series that you have in additional drivers and the 364 in the ppa, at least with regard youtube videos.

I think your issue lies elsewhere.

---

### Post by 1two3 on 2016-05-17
I've been reading more about the PPA.. this is how far I've come on understanding what to do:

1. write this in the Terminal: **sudo add-apt-repository ppa:[B]graphics-drivers/ppa**[/B]

2. **sudo apt-get update**

And after these two steps I don't know what to do.
I guess I'm supposed to **sudo apt-get install **something?

---

### Post by 1two3 on 2016-05-17
> **howefield said:**
> Sorry, had to go earlier.

Yes that's all it is, an easier way to get more up to date drivers than what you'll find in "additional drivers" .. 164.19 at the moment. Although I only posted it to give you an alternative to the riskier method of installing them yourself via the nvidia website. For what it is worth I don't think you'd see much (any) difference between the 361 series that you have in additional drivers and the 364 in the ppa, at least with regard youtube videos.

I think your issue lies elsewhere.

Hmm, yeah.. you're probably right.. 
I just have no idea what to do?
This really is super crippling.. I don't know if there's any point in keeping linux if I can't fix this.. I've already spent weeks trying to fix my computer and get a proper working installation of Ubuntu.
It's a really demoralizing experience but it feels like I have no choice.. windows is really complete ********.. but at least windows works :/

---

### Post by howefield on 2016-05-17
> **1two3 said:**
> I guess I'm supposed to **sudo apt-get install **something?

The name of the package looks to be nvidia-graphics-drivers-364, so...

```
sudo apt-get install nvidia-graphics-drivers-364
```

---

### Post by 1two3 on 2016-05-18
> **howefield said:**
> The name of the package looks to be nvidia-graphics-drivers-364, so...

```
sudo apt-get install nvidia-graphics-drivers-364
```

I just tried that but it gave me the error: **E: Unable to locate package nvidia-graphics-drivers-364**

Any clue why?

---

### Post by howefield on 2016-05-18
Have just tested in 16.04 and see the driver listed in Additional Drivers after adding the ppa and doing a sudo apt update. Installed and working.

---

### Post by $yl9pAR%t on 2016-05-18
> [COLOR=#000000]I just tried that but it gave me the error: [/COLOR]**E: Unable to locate package nvidia-graphics-drivers-364**

In terminal it should be probably:

```
sudo apt-get install nvidia-364
```

Anyway, I am personally very interested if this nvidia-364 driver will resolve the problem.

---

### Post by howefield on 2016-05-18
> **mefisto888 said:**
> ```
sudo apt-get install nvidia-364
```

Yep, looks like that is the correct package name...

```
hugh@xenial:~$ apt show nvidia*364*

Package: nvidia-364
Version: 364.19-0ubuntu0~gpu16.04.3
Priority: optional
Section: misc
Source: nvidia-graphics-drivers-364
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Installed-Size: 303 MB
Provides: nvidia-driver-binary, nvidia-persistenced, xorg-driver-binary, xorg-driver-video
Depends: x11-common (>= 1:7.0.0), make, sed (>> 3.0), dkms, linux-libc-dev, libc6-dev, patch, acpid, lib32gcc1, libc6-i386, passwd, adduser, libc6 (>= 2.2.5), libgl1, libwayland-client0 (>= 1.3.92), libwayland-server0 (>= 1.2.0), libx11-6, libxext6, xorg-video-abi-11 | xorg-video-abi-12 | xorg-video-abi-13 | xorg-video-abi-14 | xorg-video-abi-15 | xorg-video-abi-18 | xorg-video-abi-19 | xorg-video-abi-20, xserver-xorg-core
Recommends: nvidia-settings (>= 331.20), nvidia-prime (>= 0.5) | bumblebee, libcuda1-364, nvidia-opencl-icd-364
Conflicts: nvidia-persistenced, xorg-driver-binary
Replaces: nvidia-persistenced, xorg-driver-binary
Download-Size: 68.6 MB
APT-Manual-Installed: yes
APT-Sources: http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 Packages
Description: NVIDIA binary driver - version 364.19
 The binary driver provide optimized hardware acceleration of OpenGL
 applications via a direct-rendering X Server. AGP, PCIe, SLI, TV-out
 and flat panel displays are also supported.
 .
 This package also includes the source for building the kernel module
 required by the Xorg driver, and provides NVIDIA's implementation of
 the Video Decode and presentation API. The latter enables acceleration
 for GeForce 8 and later series cards for h264 video.
 .
 Release Notes and supported GPUs:
 http://www.nvidia.com/object/linux-display-amd64-364.19-driver.html
```

---

### Post by 1two3 on 2016-05-18
I just got done testing the 364 driver.. didn't help unfortunately. 
I was able to install it the way howefield said.. by going to Software & Updates > Additional Drivers after adding the PPA. 
I also restarted the computer.

---

### Post by 1two3 on 2016-05-18
I found out the problem could be because of NVIDIA Optimus ([https://www.nvidia.com/object/optimus_technology.html](https://www.nvidia.com/object/optimus_technology.html)).
Why? I have Intel CPU and NVIDIA GPU and my computer is just a few years old, maybe even just a couple years old. 

Windows supports Optimus technology but Ubuntu doesn't. 
So what I need to try is installing Bumblebee ([https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)).

I'll let you know how it goes.. hopefully it's not too difficult to install. 
It's unfortunate that everything is so difficult to install on Ubuntu/Linux if it's not in apt-get.
The installation instructions are usually a bit hard to understand etc.

---

### Post by 1two3 on 2016-05-18
On the Bumblebee wiki it says:

> The Bumblebee project recommends you install drivers only through APT  and not drivers provided by nvidia.com directly. With that said,  whenever you update your drivers through supported repositories, you  need to setup the correct config values in /etc/bumblebee/bumblebee.conf.

I wonder if it was a bad idea in this case to install the latest Nvidia driver from the PPA?
Should I uninstall it again?

I'll try first just installing bumblebee before anything else, I'm getting nearer to understanding how Bumblebee works now.

---

### Post by howefield on 2016-05-18
Well, you did install the nvidia drivers via apt. Additional drivers is a front end that uses the apt packaging system to install the packages.

---

### Post by 1two3 on 2016-05-18
I am having problem getting Bumblebee to work.

I wrote in the Terminal: **[B]sudo apt-get install bumblebee bumblebee-nvidia primus linux-headers-generic**[/B] then I reboot computer. 
Then I tried **primusrun steam** but got this error: 

Error: Couldn't find bootstrap, it's not safe to reset Steam. Please contact technical support.


I tried also **optirun steam** but got another error:

[ERROR]Cannot access secondary GPU, secondary X is not active.
[ERROR]Aborting because fallback start is disabled.


The output of **sudo dpkg --print-foreign-architectures** is **i386**.

I wrote **sudo apt-get install primus-libs-ia32** and it was already installed.


> 
primus-libs-ia32:i386 is already the newest version (0~20150328-1).
primus-libs-ia32:i386 set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.


I'm out of ideas what to try next..

---

### Post by $yl9pAR%t on 2016-05-18
I am afraid, you have lost your main aim, the title suggests it was performance and I think Bumblebee will not help with this. Besides about Bumblebee and Ubuntu 16.04 you can read thread (no hope) here:

[http://askubuntu.com/questions/766745/do-i-need-to-install-bumblebee-for-hybrid-graphics-system-to-enable-optimus-on-u](http://askubuntu.com/questions/766745/do-i-need-to-install-bumblebee-for-hybrid-graphics-system-to-enable-optimus-on-u)

You did so much, so perhaps my simple suggestion will not be a problem for you. At least it should return your OS to the earlier stage.

1. Get rid of "bumblebee"

2. Reboot your OS and at the login screen press Ctrl+Alt+F4, you will be in text mode.

3. After logging in:

```
sudo apt-get purge nvidia*
```

next

```
sudo reboot
```

4. Again, at the login screen Ctrl+Alt+F4

5. After logging in:

```
sudo apt-get update
```

```
sudo apt-get dist-upgrade
```

```
sudo apt-get install nvidia-361
```

```
sudo reboot
```

---

### Post by 1two3 on 2016-05-19
> **mefisto888 said:**
> I am afraid, you have lost your main aim, the title suggests it was performance and I think Bumblebee will not help with this. Besides about Bumblebee and Ubuntu 16.04 you can read thread (no hope) here:

[http://askubuntu.com/questions/766745/do-i-need-to-install-bumblebee-for-hybrid-graphics-system-to-enable-optimus-on-u](http://askubuntu.com/questions/766745/do-i-need-to-install-bumblebee-for-hybrid-graphics-system-to-enable-optimus-on-u)

You did so much, so perhaps my simple suggestion will not be a problem for you. At least it should return your OS to the earlier stage.

1. Get rid of "bumblebee"

2. Reboot your OS and at the login screen press Ctrl+Alt+F4, you will be in text mode.

3. After logging in:

```
sudo apt-get purge nvidia*
```

next

```
sudo reboot
```

4. Again, at the login screen Ctrl+Alt+F4

5. After logging in:

```
sudo apt-get update
```

```
sudo apt-get dist-upgrade
```

```
sudo apt-get install nvidia-361
```

```
sudo reboot
```


Wow.. That's really sad to hear..
I don't understand how I can have this unfixable problem? 
How am I ever going to feel about touching Ubuntu ever again after this experience :/
But my only others choices are no security/privacy Windows or super expensive mac

---

