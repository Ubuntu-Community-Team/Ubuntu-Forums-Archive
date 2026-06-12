---
title: "Radeon 680M Display Corruption"
date: 2023-08-19
forum: General Help
---

### Post by number45zephan on 2023-08-19
Hello, I’ve been experiencing an odd issue with getting Ubuntu 22.04.3 (or any other Linux distro) working properly on my laptop that has a 6900hs and a 3050 (Lenovo Slim 7 Pro X).

I run into display corruption after making it past grub, but I can sometimes get the machine to boot properly by hard resetting the system an arbitrary amount of times. 

The display corruption was originally intermittent, so I went into the bios and disabled the Nvidia GPU to simplify things, but that just made the corruption persistent, leading me to believe it’s an issue specifically with however this laptop has implemented the iGPU. 

Any ideas on this one? I’ve tried Manjaro, Pop! and Ubuntu but get the issue across them all. Interestingly I can make it through the installer just fine on Ubuntu, but post-install still has the corruption.

---

### Post by ajgreeny on 2023-08-19
How did you install the proprietary driver or was it what appeared after installing?
Which driver version do you have?

Have a look in Additional-Drivers to see what that offers.

---

### Post by number45zephan on 2023-08-19
This is without installing any proprietary drivers. As far as I understand it, the AMD drivers are integrated into the kernel these days, right?

I’ve tried a minimal install with and without including third party drivers.

---

### Post by QIII on 2023-08-19
So you have a dedicated (in this case the integrated mobo GPU has primacy) NVIDIA GPU on the mobo and an AMD GPU on the APU die, correct?

---

### Post by #&amp;thj^% on 2023-08-19
> **QIII said:**
> So you have a dedicated (in this case the integrated mobo GPU has primacy) NVIDIA GPU on the mobo and an AMD GPU on the APU die, correct?
+1
OP please show us this:
```
lspci | grep VGA
```
EDIT:
```
lspci -nn | grep -E 'VGA|Display'
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation TU117M [GeForce GTX 1650 Ti Mobile] [10de:1f95] (rev a1)
05:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Renoir [1002:1636] (rev c7)

```
And: 
```
inxi -G | grep API
  API: OpenGL v: 4.6 Mesa 23.0.4-0ubuntu1~23.04.1 renderer: AMD Radeon

```

---

### Post by MAFoElffen on 2023-08-19
> **number45zephan said:**
> This is without installing any proprietary drivers. [COLOR=#ff0000]As far as I understand it, the AMD drivers are integrated into the kernel these days, right?[/COLOR]

I’ve tried a minimal install with and without including third party drivers.
Sort of... Let me explain it this way...

If you look in /usr/lib/firmware/... You will see ./nvidia & ./amdgpu (along with the firmware for a lot more devices). For the opensource driver to work, it has to load as a module to the kernel. The opensource drivers are not really 'part' of the kernel, but rather drivers inside package linux-firmware... If you trace through syslog, and grep amdgpu, use can see the individual firmware drivers loaded for it...

A few kernel versions back, most users didn't have to do anything for this to happen, it just worked. Then something did happen.

Some users had to blacklist the radeon driver ad set up kernel boot parameters for the amdgpu kernel module to load. The load the module manually, add the module to the module list, and update the initramfs image, with it loaded. IDK. The dkms, should be doing that. This works for quite a few kernel versions, until we get to kernel version 6.2.0-26. If you search on my username and search term "modprobe amdgpu" you will find some of those threads and what is used...

For example: [https://ubuntuforums.org/showthread.php?t=2489867](https://ubuntuforums.org/showthread.php?t=2489867)

There is a new problem there with amdpgu and this kernel. I don't have it sorted out yet. I don't have this hardware, but have been trying to help people with it just from experience.  If someone could donate or loan me the device hardware I could do more testing, instead of having others try things them report back. Sorry. Doing what i can with what i have. 

Even loading the firmware blob from the kernel.org github is not helping with this kernel. I have two users that do not want to use the AMD closed source driver, and we have tried about 2 pages of work-arounds... and the next step for them is trying the closed source drivers.

Having said that, many nVidia Users that have updated to Linux Kernel 6.2.0-26 are havig issues also. Especially with nvidia-driver-535. I'm using that driver and kernel and cannot recreate those problems yet.

Now... The Linux Mint Forums are abuzz with this problem also recently... For both amdgpu and nVidia. What they are recommending to their users is to do
```

sudo update
sudo apt-get install linux-oem-22.04c

```
-OR-
```

sudo add-apt-repository ppa:canonical-kernel-team
sudo apt update

```
Like I said, i haven't recreated the issues yet with 6.2.0-26, so I have not tested these yet. But effectively, both would be using different, patched kernels.

---

### Post by MAFoElffen on 2023-08-19
I would hate to say this, but we need "guinea pigs" with issues, that can try different work-arounds to see what does or does not work for them. I realize that one "fix" may work for someone, but not the next, because of differing hardware combinations. That is just how these things play out.

There are current issues with both GPU drivers in this recent Linux Kernel Series. What is a distractor, is that some of the current issues which both these drivers are not just Linux specific (happening with Windows drivers also), so not related to Linux kernel at all.

EDIT: ^^^ This does not exclude Intel i915... It is recently having issues with this recent kernel Series and firmware also. Something is in the water.

---

### Post by #&amp;thj^% on 2023-08-19
No issues here but I'm a tester so here goes my precious ZFS-Root with both AMD and Nvidia
First The Warning***
```
Repository: 'deb https://ppa.launchpadcontent.net/canonical-kernel-team/ppa/ubuntu/ lunar main'
Description:
This ppa is used for building pre-release and test kernels.

It IS NOT RECOMMENDED that you subscribe to this PPA.

More info: https://launchpad.net/~canonical-kernel-team/+archive/ubuntu/ppa
Adding repository.
Press [ENTER] to continue or Ctrl-c to cancel.

The following package was automatically installed and is no longer required:
  nvidia-firmware-535-535.86.05
Use 'sudo apt autoremove' to remove it.
The following NEW packages will be installed:
  linux-headers-6.2.0-32 linux-headers-6.2.0-32-generic
  linux-image-6.2.0-32-generic linux-modules-6.2.0-32-generic
  linux-modules-extra-6.2.0-32-generic nvidia-driver-core-535
  nvidia-firmware-535-535.98
The following packages will be upgraded:
  libnvidia-cfg1-535 libnvidia-common-535 libnvidia-compute-535
  libnvidia-compute-535:i386 libnvidia-decode-535 libnvidia-decode-535:i386
  libnvidia-encode-535 libnvidia-encode-535:i386 libnvidia-extra-535
  libnvidia-fbc1-535 libnvidia-fbc1-535:i386 libnvidia-gl-535
  libnvidia-gl-535:i386 linux-generic linux-headers-generic
  linux-image-generic linux-libc-dev nvidia-compute-utils-535 nvidia-dkms-535
  nvidia-driver-535 nvidia-kernel-common-535 nvidia-kernel-source-535
  nvidia-utils-535 xserver-xorg-video-nvidia-535
24 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 531 MB of archives.
After this operation, 749 MB of additional disk space will be used.
Do you want to continue? [Y/n] 


```
Done and I'm a happy camper:
```
inxi -SG && inxi -p | grep zfs
System:
  Host: zfs-me Kernel: 6.2.0-32-generic arch: x86_64 bits: 64 Desktop: Xfce
    v: 4.18.1 Distro: Linux Lite 6.4 LTS
Graphics:
  Device-1: NVIDIA TU117M [GeForce GTX 1650 Ti Mobile] driver: nvidia
    v: 535.98
  Device-2: AMD Renoir driver: amdgpu v: kernel
  Device-3: Syntek Integrated Camera type: USB driver: uvcvideo
  Display: x11 server: X.Org v: 1.21.1.7 driver: X: loaded: amdgpu,nvidia
    unloaded: fbdev,modesetting,nouveau,vesa dri: radeonsi gpu: amdgpu
    resolution: 1920x1080~120Hz
  API: OpenGL v: 4.6 Mesa 23.0.4-0ubuntu1~23.04.1 renderer: AMD Radeon
    Graphics (renoir LLVM 15.0.7 DRM 3.49 6.2.0-32-generic)
  ID-1: / size: 201.33 GiB used: 9.62 GiB (4.8%) fs: zfs
  ID-2: /boot size: 1.38 GiB used: 723.6 MiB (51.1%) fs: zfs
  ID-4: /home/me size: 201.89 GiB used: 10.19 GiB (5.0%) fs: zfs
  ID-5: /root size: 191.71 GiB used: 2.9 MiB (0.0%) fs: zfs
  ID-6: /srv size: 191.7 GiB used: 128 KiB (0.0%) fs: zfs
  ID-7: /usr/local size: 191.7 GiB used: 256 KiB (0.0%) fs: zfs
  ID-8: /var/games size: 191.7 GiB used: 128 KiB (0.0%) fs: zfs
  ID-9: /var/lib size: 200.62 GiB used: 8.91 GiB (4.4%) fs: zfs
    fs: zfs logical: rpool/ROOT/ubuntu_d1lsb0/var/lib/AccountsService
    fs: zfs logical: rpool/ROOT/ubuntu_d1lsb0/var/lib/NetworkManager
  ID-12: /var/lib/apt size: 192.31 GiB used: 623.8 MiB (0.3%) fs: zfs
  ID-13: /var/lib/dpkg size: 191.78 GiB used: 73.4 MiB (0.0%) fs: zfs
  ID-14: /var/log size: 191.78 GiB used: 81.8 MiB (0.0%) fs: zfs
  ID-15: /var/mail size: 191.7 GiB used: 128 KiB (0.0%) fs: zfs
  ID-16: /var/snap size: 191.7 GiB used: 128 KiB (0.0%) fs: zfs
  ID-17: /var/spool size: 191.7 GiB used: 128 KiB (0.0%) fs: zfs
  ID-18: /var/www size: 191.7 GiB used: 128 KiB (0.0%) fs: zfs

```
now for nvidia:
```
 nvidia-smi
Sat Aug 19 13:08:00 2023       
+---------------------------------------------------------------------------------------+
| NVIDIA-SMI 535.98                 Driver Version: 535.98       CUDA Version: 12.2     |
|-----------------------------------------+----------------------+----------------------+
| GPU  Name                 Persistence-M | Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp   Perf          Pwr:Usage/Cap |         Memory-Usage | GPU-Util  Compute M. |
|                                         |                      |               MIG M. |
|=========================================+======================+======================|
|   0  NVIDIA GeForce GTX 1650 Ti     Off | 00000000:01:00.0 Off |                  N/A |
| N/A   39C    P8               1W /  50W |      5MiB /  4096MiB |      0%      Default |
|                                         |                      |                  N/A |
+-----------------------------------------+----------------------+----------------------+
                                                                                         
+---------------------------------------------------------------------------------------+
| Processes:                                                                            |
|  GPU   GI   CI        PID   Type   Process name                            GPU Memory |
|        ID   ID                                                             Usage      |
|=======================================================================================|
|    0   N/A  N/A      6933      G   /usr/lib/xorg/Xorg                            4MiB |
+---------------------------------------------------------------------------------------+

```
```
zpool status
  pool: bpool
 state: ONLINE
config:

	NAME                                    STATE     READ WRITE CKSUM
	bpool                                   ONLINE       0     0     0
	  18d52db8-9b4c-6d4e-8415-3550bdbfd60c  ONLINE       0     0     0

errors: No known data errors

  pool: rpool
 state: ONLINE
config:

	NAME                                    STATE     READ WRITE CKSUM
	rpool                                   ONLINE       0     0     0
	  d6013007-da4e-134f-b787-50f9b10fb475  ONLINE       0     0     0

errors: No known data errors

```

---

### Post by MAFoElffen on 2023-08-19
Dang. I didn't mean "personally" on that install of yours... LOL. I know how precious that installation is of yours. (And you use it for "work.")

There we go!!! So far, so good. I know you know how to get back to square one if needed.

I have the same nVidia GPU, but I have 13th Gen i915 as my iGPU... 

Because you stepped up, I'll take ZFS snapshots on my own new Workstation and do the same on it. But I had to update the firmware on it to the latest firmware blog on it, just because the 13th Gen Z790 chipset on it... So it may not be as true a test. It basically has the same nVidia GPU (1660ti), but i915 as iGPU (ARC A780).
```

mafoelffen@msi-ubuntu:~$ sudo lspci | grep -i 'vga\|display'
00:02.0 Display controller: Intel Corporation Device a780 (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation TU116 [GeForce GTX 1660 Ti] (rev a1)
mafoelffen@msi-ubuntu:~$ sudo lshw -c video -businfo
Bus info          Device          Class          Description
============================================================
pci@0000:01:00.0                  display        TU116 [GeForce GTX 1660 Ti]
pci@0000:00:02.0                  display        Intel Corporation
mafoelffen@msi-ubuntu:~$ sudo lshw -c video
  *-display                 
       description: VGA compatible controller
       product: TU116 [GeForce GTX 1660 Ti]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:250 memory:72000000-72ffffff memory:90000000-9fffffff memory:a0000000-a1ffffff ioport:5000(size=128) memory:c0000-dffff
  *-display
       description: Display controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 04
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm bus_master cap_list
       configuration: driver=i915 latency=0
       resources: irq:219 memory:71000000-71ffffff memory:80000000-8fffffff ioport:6000(size=64) memory:75000000-7bffffff

```
I'll do that when I get home from work tonight or tomorrow morning...

EDIT: I need to borrow a recent AMD GPU from somewhere.., All I have in storage are old ATI/AMD Radeon cards. Maybe I should contact the Computer Recycler I used to volunteer for to see if he would donate one for this. Right now, I'm strapped for funds.

---

### Post by number45zephan on 2023-08-20
Seems like I’m getting this issue regardless of the kernel I try. After playing around with it a bit more, the corruption only occurs on the internal display of the laptop. External displays don’t have the corruption and function as expected, even when the NVIDIA GPU is disabled by the bios. 

Driver stuff (NVIDIA GPU disabled in BIOS):

```
lspci | grep VGA
03:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Rembrandt (rev 01)

```

```
lspci -nn | grep -E 'VGA|Display'
03:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Rembrandt [1002:1681] (rev 01)

```

```
inxi -G | grep API
API: OpenGL v: 4.6 Mesa 23.0.4-0ubuntu1~22.04.1 renderer: REMBRANDT

```

Kernels Tested: 

```

Default Kernel
uname -r
6.2.0-26-generic

```

```
linux-oem-22.04c
uname -r
6.4.6-76060406-generic

```

---

### Post by number45zephan on 2023-08-20
I appreciate the info. Unfortunately updating the kernel doesn’t seem to have helped my issue. I suspect the issue is specific to something with this hardware, but it’s interesting to me others are having weird GPU issues.

---

### Post by #&amp;thj^% on 2023-08-20
It would seem you tried just the linux-oem-22.04c kernel and not the "ppa:canonical-kernel-team"
I had a poster over on Arch Linux with the identical laptop you have and we tried this:
If you decide to test it use
```
sudo nano /etc/X11/xorg.conf
```
```
/etc/X11/xorg.conf

Section "ServerLayout"
        Identifier "layout"
        Screen 0 "intel"
        Inactive "nvidia"
        Option "AllowNVIDIAGPUScreens"
EndSection

Section "Device"
        Identifier "nvidia"
        Driver "nvidia"
EndSection

Section "Screen"
        Identifier "nvidia"
        Device "nvidia"
EndSection

Section "Device"
        Identifier "intel"
        Driver "modesetting"
        BusID "PCI:03:00.0 "
EndSection

Section "Screen"
        Identifier "intel"
        Device "intel"
EndSection
```
Save the file and reboot.
How ever you don't seem to want the nVida GPU active so this will be a crap shoot

---

### Post by MAFoElffen on 2023-08-20
I'm here to ask if you tried to update the linux-firmware for amdgpu yet?

In today's updates it updated a kernel on one of my machines, and report it was missing an i915 firmware file... The third ZFS machine in a week with i915 as the iGPU, where it said it was missing Linux firmware files while rebuilding the ZFS module with zfs-dkms. Now all three of my ZFS-ON-Root machines that have Intel iGPU's have updated Linux Firmware.

Not saying this is related, but you are trying to use amdgpu, which the opensource driver module is using the firmware files directly from /usr/lib/firmware/amdgpu, which is "linux-firmware" from the same kernel.org blob.

Worth a try if you haven't...
RE: [https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/](https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/)

If you need instructions for how to do that, just ask.

---

### Post by #&amp;thj^% on 2023-08-20
> **MAFoElffen said:**
> I'm here to ask if you tried to update the linux-firmware for amdgpu yet?

Worth a try if you haven't...
RE: [https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/](https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/)

If you need instructions for how to do that, just ask.

+1
```
cd /usr/lib/firmware/ && ls | grep amd
amd
amdgpu
amd-ucode

```
We really need to get to cause here.

---

### Post by number45zephan on 2023-08-22
[QUOTE=1fallen;14155013]
```
sudo nano /etc/X11/xorg.conf
```
```

Section "Device"
        Identifier "intel"
        Driver "modesetting"
        BusID "PCI:03:00.0 "
EndSection

Section "Screen"
        Identifier "intel"
        Device "intel"
EndSection
```
/QUOTE]

That looks like it's a config for someone with an Intel iGPU? If not I'll give it a try tomorrow. Unfortunately I've been really busy and haven't gotten the chance to get further into this issue. I'm fine to have the Nvidia GPU active, but I get the corruption with either enabled so I am just trying to get down to what is causing it. If disabling the Nvidia GPU isn't helpful we can swap back to it being enabled, but for now Ubuntu is just going to see the AMD GPU.

I do also get this output when running that other command:
```

cd /usr/lib/firmware/ && ls | grep amd
amd
amdgpu
amd-ucode

```


I added the "ppa:canonical-kernel-team", but there weren't any updates available. Was I supposed to try a specific kernel they have on that one?

---

### Post by number45zephan on 2023-08-22
I'm not familiar with how to grab the latest linux-firmware. Could you help me with that?

---

### Post by MAFoElffen on 2023-08-22
I suspected you might, so I wrote thse instructions for you:
```

## Go to the kernel.org git 
## -- https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/
## and get the latest firmware tarfile link. Adjust the DL link and filename 'here' accordingly.

DL_LINK="https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/snapshot/linux-firmware-20230804.tar.gz"
FILNAME="linux-firmware-20230804.tar.gz"

mkdir $HOME/Downloads/linux-firmware
mkdir $HOME/Downloads/linux-firmware/amdgpu
cd $HOME/Downloads/Linux-firmware

wget -n -t 5 -T 10 $DL_LINK

# Look in tar...
tar -tvf $FILENAME | grep -m1 'amdgpu'

# Extract just folder 'amdgpu' into the target folder
tar -xvf $FILENAME amdgpu/ -C ./amdgpu

sudo cp ./amdgpu/* /usr/lib/firmware/amdgpu/

```

---

### Post by #&amp;thj^% on 2023-08-22
> **MAFoElffen said:**
> I suspected you might, so I wrote thse instructions for you:
```

## Go to the kernel.org git 
## -- https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/
## and get the latest firmware tarfile link. Adjust the DL link and filename 'here' accordingly.

DL_LINK="https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/snapshot/linux-firmware-20230804.tar.gz"
FILNAME="linux-firmware-20230804.tar.gz"

mkdir $HOME/Downloads/linux-firmware
mkdir $HOME/Downloads/linux-firmware/amdgpu
cd $HOME/Downloads/Linux-firmware

wget -n -t 5 -T 10 $DL_LINK

# Look in tar...
tar -tvf $FILENAME | grep -m1 'amdgpu'

# Extract just folder 'amdgpu' into the target folder
tar -xvf $FILENAME amdgpu/ -C ./amdgpu

sudo cp ./amdgpu/* /usr/lib/firmware/amdgpu/

```
+1 Nice work.
Now if you do decide to add that PPA mentioned by MAFoElffen and myself >>>DON'T, it's already progressed to:
```
apt policy nvidia-driver-535 nvidia-dkms-535
nvidia-driver-535:
  Installed: 535.104.05-0ubuntu0.23.04.1
  Candidate: 535.104.05-0ubuntu0.23.04.1
  Version table:
 *** 535.104.05-0ubuntu0.23.04.1 500
        500 https://ppa.launchpadcontent.net/canonical-kernel-team/ppa/ubuntu lunar/main amd64 Packages
        100 /var/lib/dpkg/status
     535.86.05-0ubuntu0.23.04.1 500
        500 http://us.archive.ubuntu.com/ubuntu lunar-updates/restricted amd64 Packages
        500 http://security.ubuntu.com/ubuntu lunar-security/restricted amd64 Packages
nvidia-dkms-535:
  Installed: 535.104.05-0ubuntu0.23.04.1
  Candidate: 535.104.05-0ubuntu0.23.04.1
  Version table:
 *** 535.104.05-0ubuntu0.23.04.1 500
        500 https://ppa.launchpadcontent.net/canonical-kernel-team/ppa/ubuntu lunar/main amd64 Packages
        100 /var/lib/dpkg/status
     535.86.05-0ubuntu0.23.04.1 500
        500 http://us.archive.ubuntu.com/ubuntu lunar-updates/restricted amd64 Packages
        500 http://security.ubuntu.com/ubuntu lunar-security/restricted amd64 Packages

```
This brought my screen to the Black Death screen, it was an easy fix for me, but not a desirable occurrence for a production system.
Current firmware on 23.04 is:
```
apt policy linux-firmware
linux-firmware:
  Installed: 20230323.gitbcdcfbcf-0ubuntu1.6
  Candidate: 20230323.gitbcdcfbcf-0ubuntu1.6
  Version table:
 *** 20230323.gitbcdcfbcf-0ubuntu1.6 500
        500 http://us.archive.ubuntu.com/ubuntu lunar-updates/main amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu lunar-updates/main i386 Packages
        100 /var/lib/dpkg/status
     20230323.gitbcdcfbcf-0ubuntu1.2 500
        500 http://security.ubuntu.com/ubuntu lunar-security/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu lunar-security/main i386 Packages
     20230323.gitbcdcfbcf-0ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu lunar/main amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu lunar/main i386 Packages

```

---

### Post by number45zephan on 2023-08-23
I've managed to get a stable system on my end, and I suspect it has to  do with this system's implementation of shutting the Nvidia GPU down  from the BIOS. 

So, I'll make a short list of what I did to get things stable:
[LIST]
[*]Set bios to hybrid graphics (The default)
[*]Install Pop! with third party drivers + pull updates during install
[*]Build and install the rtw89 repo  My Wi-Fi didn't work out of the box with Pop! or Manjaro, but did with Ubuntu.
[*]Using the system76 utility, swap to hybrid graphics from the default (nvidia).
[/LIST]

I've been using it for a little bit and haven't gotten any of the display corruption that I was getting with the hybrid graphics drivers on Manjaro and Ubuntu/KUbuntu. Interestingly, the Wi-Fi driver gets unstable when on iGPU only as well. 

That BIOS switch is a surefire way to get the display corruption still, so it's best to just avoid that on this machine, at least for the time being.

---

### Post by #&amp;thj^% on 2023-08-23
> **number45zephan said:**
> 

That BIOS switch is a surefire way to get the display corruption still, so it's best to just avoid that on this machine, at least for the time being.
+1
Good Job.=d>

---

### Post by MAFoElffen on 2023-08-23
> **number45zephan said:**
> [QUOTE=1fallen;14155013]
```
sudo nano /etc/X11/xorg.conf
```
```

Section "Device"
        Identifier "intel"
        Driver "modesetting"
        BusID "PCI:03:00.0 "
EndSection

Section "Screen"
        Identifier "intel"
        Device "intel"
EndSection
```


That looks like it's a config for someone with an Intel iGPU? If not I'll give it a try tomorrow. Unfortunately I've been really busy and haven't gotten the chance to get further into this issue. I'm fine to have the Nvidia GPU active, but I get the corruption with either enabled so I am just trying to get down to what is causing it. If disabling the Nvidia GPU isn't helpful we can swap back to it being enabled, but for now Ubuntu is just going to see the AMD GPU.
[/QUOTE]
No. The names used for identifiers are misleading in that. Nowhere does not say "intel" as a driver. 

It actually has a slight mistake in there, in the naming conventions.  If I were to take liberties with that...
```

Section "ServerLayout"
        Identifier "layout"
        Screen 0 "Device1"
        Inactive "Device0"
        Option "AllowNVIDIAGPUScreens"
EndSection

Section "Device"
        Identifier "Device0"
        Driver "nvidia"
EndSection

Section "Screen"
        Identifier "Screen0"
        Device "Device0"
EndSection

Section "Device"
        Identifier "Device1"
        Driver "modesetting"
        BusID "PCI:03:00.0 "
EndSection

Section "Screen"
        Identifier "Screen1"
        Device "Device1"
EndSection

```
Does that make more sense now?

The limitation of that is that the "modesettig" driver is a basic 2D framebuffer driver that uses KMS modesets in the kernel.

---

