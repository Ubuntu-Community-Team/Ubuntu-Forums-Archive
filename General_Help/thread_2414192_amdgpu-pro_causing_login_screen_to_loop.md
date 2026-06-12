---
title: "amdgpu-pro causing login screen to loop"
date: 2019-03-06
forum: General Help
---

### Post by kwalker332 on 2019-03-06
I'm new to Ubuntu, ie poor with terminology and cmnd line.
Running Ubuntu 18.04 on Lubin i7 7700 with a 
[TABLE]
[TR]
[TD]SAPPHIRE Radeon RX 550 DirectX 12 11268-01CPO 4GB 128-Bit GDDR5 Video Card[/TD]
[/TR]
[/TABLE]
Currently, things are okay but not great with amdgpu drivers which I think are open source. [FONT=Arial]I am having video issues w/ default movie player as well as cheese the webcam app. [/FONT][https://ubuntuforums.org/showthread.php?t=1764741](https://ubuntuforums.org/showthread.php?t=1764741)[FONT=Arial] I don't have the color correction option available which I'm assuming is from having the wrong video driver. I know vlc works but this computer is almost exclusively for video editing and sharing so I need it to not have gaps in functionality. 
[/FONT][FONT=Arial]
root@siren-HP-Pavilion-Desktop-PC-570-p0xx:/home/siren# lshw -c video[/FONT]
[FONT=Arial]*-display [/FONT]
[FONT=Arial]description: VGA compatible controller[/FONT]
[FONT=Arial]product: Lexa PRO [Radeon RX 550/550X][/FONT]
[FONT=Arial]vendor: Advanced Micro Devices, Inc. [AMD/ATI][/FONT]
[FONT=Arial]physical id: 0[/FONT]
[FONT=Arial]bus info: pci@0000:01:00.0[/FONT]
[FONT=Arial]version: c7[/FONT]
[FONT=Arial]width: 64 bits[/FONT]
[FONT=Arial]clock: 33MHz[/FONT]
[FONT=Arial]capabilities: pm pciexpress msi vga_controller bus_master cap_list rom[/FONT]
[FONT=Arial]configuration: driver=amdgpu latency=0[/FONT]
[FONT=Arial]resources: irq:130 memory:c0000000-cfffffff memory:d0000000-d01fffff ioport:e000(size=256) memory:df300000-df33ffff memory:c0000-dffff[/FONT]
[FONT=Arial]root@siren-HP-Pavilion-Desktop-PC-570-p0xx:/home/siren# [/FONT]

I cannot play games that I could with the integrated intel graphics though so I'm trying to follow this guide to install proprietary drivers. [https://amdgpu-install.readthedocs.io/en/latest/](https://amdgpu-install.readthedocs.io/en/latest/)

I have tried installing several times requiring wipe/reinstall of ubuntu. I need help understanding my system's current state as well as where to go from here without bricking my os any more times. Are dedicated graphics active? Do integrated cards work with dedicated or should it only be dedicated? 

I checked the box to install proprietary drivers when fresh installing this OS but graphics are clearly not right.

When I run:
[COLOR=#000000]./amdgpu-pro-install --px[/COLOR]
 ./amdgpu-install -y     or...
./amdgpu-pro-install-y--opencl=pal,legacy

I reboot and a login screen asks for the password and then allows me to put it in but never logs in.

---

### Post by kwalker332 on 2019-03-12
[https://amdgpu-install.readthedocs.io/en/latest/install-installing.html](https://amdgpu-install.readthedocs.io/en/latest/install-installing.html)



These drivers are giving me errors

[COLOR=#000000]./amdgpu-pro-install --px[/COLOR]

Command ran correctly until the end.

WARNING: amdgpu dkms failed for running kernel


Options:
-h|--help Display this help message
--dryrun Print list of packages to install and exit
--px (DEPRECATED) PX platform support
--version=VERSION Install the specified driver VERSION
--pro Install "pro" support (legacy OpenGL and Vulkan)
--opencl=legacy Install legacy OpenCL support
--opencl=pal Install PAL OpenCL support
--opencl=legacy,pal Install both legacy and PAL OpenCL support
--headless Headless installation (only OpenCL support)
--no-dkms Do not install amdgpu-dkms package
--compute (DEPRECATED) Equal to --opencl=legacy --headless



Unless the -h|--help option is given, 'apt-get' or 'aptitude' options
may be present.



This is for Ubuntu only, I don't know what depracated means. Expired? 
./amdgpu-pro-install --px [IMG]https://ubuntuforums.org/blob:https://mail.google.com/3307121d-d5af-4472-b1d3-c985da8bbc39[/IMG] 

I am unable to boot even if I go to previous kernal (4.18 variations)


I tried dpkg from advanced options in GRUB
still not letting me log in. 

Partially resolved: 
I used UKUU to install 4.15 kernal Then booted into 4.15
and found and installed a missing xorg file that was in the 17.4 AMD download named: xserver-xorg-video-modesetting-amdgpu-pro_1.19.0-514569_amd64

I was able to run 
./amdgpu-pro-install --px

with no errors. 
I believe it's because I've manually installed this modsetting xorg file 
I got from the 17.4 AMD driver package (this was 18.50)  I'm on kernal 4.15 down from 4.18.

Rebooted, login loop, ctrl alt F2 and
I then reinstalled xorg with: [https://askubuntu.com/questions/21309/how-to-restore-xserver](https://askubuntu.com/questions/21309/how-to-restore-xserver)
sudo apt-get install --reinstall xserver-xorg
It solved the login loop and rebooted. Success but I'm not getting 4k support in display manager.
The GPU manager seems to confirm installation. The "Radeon" in set to off.

log_file: /var/log/gpu-manager.log
last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
can't access /run/u-d-c-nvidia-was-loaded file
Looking for nvidia modules in /lib/modules/4.18.0-17-generic/updates/dkms
Looking for amdgpu modules in /lib/modules/4.18.0-17-generic/updates/dkms
Is nvidia loaded? no
Was nvidia unloaded? no
Is nvidia blacklisted? no
Is intel loaded? no
Is radeon loaded? no
Is radeon blacklisted? yes
Is amdgpu loaded? yes
Is amdgpu blacklisted? no
Is amdgpu versioned? no
Is amdgpu pro stack? no
Is nouveau loaded? no
Is nouveau blacklisted? no
Is nvidia kernel module available? no
Is amdgpu kernel module available? no
******I believe this was enabled when I was booted into 4.15 Kernal but now that I'm back at default 4.18, it says "no".*******
------------Solve by using 4.15 and removing later kernals?
Vendor/Device Id: 1002:699f
BusID "PCI:1@0:0:0"
Is boot vga? yes
Found "/dev/dri/card0", driven by "amdgpu"
output 0:
card0-HDMI-A-1
output 1:
card0-DVI-D-1
output 2:
card0-DP-1
Number of connected outputs for /dev/dri/card0: 3
Skipping "/dev/dri/card0", driven by "amdgpu"
Skipping "/dev/dri/card0", driven by "amdgpu"
Skipping "/dev/dri/card0", driven by "amdgpu"
Does it require offloading? no
last cards number = 1
Has amd? yes
Has intel? no
Has nvidia? no
How many cards? 1
Has the system changed? No
Single card detected
Nothing to do

Output from commands I think are relevant:

siren@siren-HP-Pavilion-Desktop-PC-570-p0xx:~$ dpkg -l amdgpu-pro
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name Version Architecture Description
+++-=========================-=================-=================-========================================================
ii amdgpu-pro 18.50-725072 amd64 Meta package to install amdgpu Pro components.
siren@siren-HP-Pavilion-Desktop-PC-570-p0xx:~$ 
siren@siren-HP-Pavilion-Desktop-PC-570-p0xx:~$ lspci -k | grep -EA3 'VGA|3D|Display' 
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Lexa PRO [Radeon RX 550/550X] (rev c7)
Subsystem: Sapphire Technology Limited Lexa PRO [Radeon RX 550]
Kernel driver in use: amdgpu
Kernel modules: amdgpu
siren@siren-HP-Pavilion-Desktop-PC-570-p0xx:~$ sudo lshw -c video
[sudo] password for siren: 
*-display 
description: VGA compatible controller
product: Lexa PRO [Radeon RX 550/550X]
vendor: Advanced Micro Devices, Inc. [AMD/ATI]
physical id: 0
bus info: pci@0000:01:00.0
version: c7
width: 64 bits
clock: 33MHz
capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
configuration: driver=amdgpu latency=0
resources: irq:128 memory:c0000000-cfffffff memory:d0000000-d01fffff ioport:e000(size=256) memory:df300000-df33ffff memo




I believe this means that I did not get all the features of the proprietary driver. When I look in system software updates settings, there is nothing in "additional drivers" and even says there are no proprietary drivers in use.

I'm needing to get this right because I will be using WINE for games(spotty now but some apps are better than on windows), video processing natively and possibly in VBOXes. 

I have usability but I can't even set my screen to 4k. Please help.

---

### Post by wildmanne39 on 2019-03-12
Please use the default font color and properties unless you need to highlight or draw attention to a part of your post.

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

If you do not receive a reply you can bump your thread once every twelve hours to keep your thread in view of the volunteers here on the forum.

I am not sure that you can trouble shoot a driver problem from vbox because virtual machines do not run on the physical hardware and do not use the hardware driver, it uses its own driver.

---

### Post by kwalker332 on 2019-03-12
siren@siren-HP-Pavilion-Desktop-PC-570-p0xx:~$ xrandr --listproviders
Providers: number : 1
Provider 0: id: 0x57 cap: 0x9, Source Output, Sink Offload crtcs: 5 outputs: 3 associated providers: 0 name:Radeon RX 550 Series @ pci:0000:01:00.0
siren@siren-HP-Pavilion-Desktop-PC-570-p0xx:~$ 

Does this mean the dedicated card is the only one doing any work?

---

### Post by kwalker332 on 2019-04-13
> **wildmanne39 said:**
> Please use the default font color and properties unless you need to highlight or draw attention to a part of your post.

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

If you do not receive a reply you can bump your thread once every twelve hours to keep your thread in view of the volunteers here on the forum.

I am not sure that you can trouble shoot a driver problem from vbox because virtual machines do not run on the physical hardware and do not use the hardware driver, it uses its own driver.

removed highlighted text I don't understand what that, (html code?,) is for.

I took your advice and tried a external hdd instead of VBOX I think a partition would have been easier to match now.

---

