---
title: "Ubuntu 16.04.x 64 bit LTS &quot;Xenial Xerus:&quot; choppy video performance"
date: 2016-10-01
forum: General Help
---

### Post by Welly Wu on 2016-10-01
I own a mid-2015 Zareason Zeto gaming desktop PC and here are the technical specifications:

```
[COLOR=#1D2129][FONT=helvetica]Mid-2015 ZaReason Zeto desktop[/FONT][/COLOR]
[COLOR=#1D2129][FONT=helvetica]EVGA Hadron Air case [/FONT][/COLOR]
[COLOR=#1D2129][FONT=helvetica]EVGA 500 watt 80+ Gold PSU [/FONT][/COLOR]
[COLOR=#1D2129][FONT=helvetica]Gigabyte GA-H97N-WiFi motherboard [/FONT][/COLOR]
[COLOR=#1D2129][FONT=helvetica]Intel Core i7-4790 CPU [/FONT][/COLOR]
[COLOR=#1D2129][FONT=helvetica]16 GB DDR3 1,600 MHz RAM [/FONT][/COLOR]
[COLOR=#1D2129][FONT=helvetica]EVGA SC nVidia Geforce GTX Titan X 12 GB GDDR5 VRAM GPU [/FONT][/COLOR]
[COLOR=#1D2129][FONT=helvetica]802.11 AC WiFi + Bluetooth 4.0 [/FONT][/COLOR]
[COLOR=#1D2129][FONT=helvetica]2x Gigabit Ethernet[/FONT][/COLOR]
[COLOR=#1D2129][FONT=helvetica]Crucial M550 2.5" SATA-III 6 GB/s 1 TB SSD [Ubuntu 16.04.1 64 bit LTS GNU/Linux][/FONT][/COLOR]
[COLOR=#1D2129][FONT=helvetica]WD Blue SATA-III 6 GB/s 4 TB 5,400 RPM 64 MB cache + 8 GB MLC NAND FLASH SSHD [media library] [/FONT][/COLOR]
[COLOR=#1D2129][FONT=helvetica]WD Black SATA-III 6 TB 7,200 RPM 128 MB cache HDD[/FONT][/COLOR]
[COLOR=#1D2129][FONT=helvetica]WD My Cloud Personal Cloud 8 TB NAS[/FONT][/COLOR]
[COLOR=#1D2129][FONT=helvetica]Plugable USB 3.0 UASP 8.0+ TB dock[/FONT][/COLOR]
[COLOR=#1D2129][FONT=helvetica]Transcend StoreJet MIL-STD USB 3.0 2 TB portable HDD [backups] [/FONT][/COLOR]
[COLOR=#1D2129][FONT=helvetica]16X DVD/CD burner[/FONT][/COLOR]
[COLOR=#1D2129][FONT=helvetica]AOC G2460PG 24" FHD 1 ms 144 hZ nVidia 3D Vision & G-SYNC monitor + ULMB[/FONT][/COLOR]
[COLOR=#1D2129][FONT=helvetica]Logitech G910 Orion Spark RGB mechanical keyboard [/FONT][/COLOR]
[COLOR=#1D2129][FONT=helvetica]Logitech Proteus Core G502 RGB mouse [/FONT][/COLOR]
[COLOR=#1D2129][FONT=helvetica]Logitech G440 hard mousepad [/FONT][/COLOR]
[COLOR=#1D2129][FONT=helvetica]Logitech G633 Artemis Spectrum RGB headset [/FONT][/COLOR]
[COLOR=#1D2129][FONT=helvetica]Logitech HD Pro C920 FHD webcam [/FONT][/COLOR]
[COLOR=#1D2129][FONT=helvetica]Cat 6 Ethernet cables [/FONT][/COLOR]
[COLOR=#1D2129][FONT=helvetica]USB 3.0 cables[/FONT][/COLOR]
[COLOR=#1D2129][FONT=helvetica]Microsoft XBOX 360 controller[/FONT][/COLOR]
[COLOR=#1D2129][FONT=helvetica]Steam Controller[/FONT][/COLOR]
[COLOR=#1D2129][FONT=helvetica]Steam Link[/FONT][/COLOR]
[COLOR=#1D2129][FONT=helvetica]Hewlett Packard 4630[/FONT][/COLOR]
[COLOR=#1D2129][FONT=helvetica]Oppo Digital HA-1[/FONT][/COLOR]
[COLOR=#1D2129][FONT=helvetica]Sennheiser HD 800 & CH 800 S cable[/FONT][/COLOR]
[COLOR=#1D2129][FONT=helvetica]HiSense 40H4C 40" FHD Roku HDTV[/FONT][/COLOR]
[COLOR=#1D2129][FONT=helvetica]HDMI 2.0 cables[/FONT][/COLOR]
[COLOR=#1D2129][FONT=helvetica]Verizon FiOS Quantum custom TV essentials package[/FONT][/COLOR]
[COLOR=#1D2129][FONT=helvetica]Verizon FiOS HD Set Top Box[/FONT][/COLOR]
[COLOR=#1D2129][FONT=helvetica]Verizon FiOS Quantum Gateway Router [50/50 MB/s symmetrical Internet][/FONT][/COLOR]
[COLOR=#1D2129][FONT=helvetica]Verizon FiOS Digital Voice[/FONT][/COLOR]
[COLOR=#1D2129][FONT=helvetica]Yubico YubiKey[/FONT][/COLOR]
[COLOR=#1D2129][FONT=helvetica]APC BRG1500G UPS
```

I installed Ubuntu 16.04.1 64 bit LTS GNU/Linux using the default Linux kernel 4.4.x AMD64 and I experience choppy video performance when playing HTML5 and Adobe Flash videos from numerous websites like Google YouTube, Vimeo, Netflix, Hulu, etc. When I play SteamOS + GNU/Linux PC game titles, I also experience choppy video performance. To be specific, frames are dropped and there are random stutters in video playback or PC gaming.

I did quite a bit of research and I did my fair share of self-support to fix the Intel HD Audio audio technical issues, downgraded to the latest stable nVidia proprietary graphics drivers, and upgraded the Linux kernel. These measures helped to improve the smoothness of video performance, but the underlying problem still exists.

Please tell me what information that you will need from me and how to furnish it to this community to be of greater help to troubleshoot and resolve my technical issues with regard to choppy video performance. I understand that this is an issue that has plagued previous Ubuntu versions when each one was installed bare metal on a desktop or laptop PC in the past and I am hoping to pinpoint the root cause and solve it fairly quickly.

Thank you.[/FONT][/COLOR]

---

### Post by oldfred on 2016-10-02
Welly, shortest post I have seen from you. :)
But please use code tags on longer text or code.

Is the driver suggested here the one you have installed?
 Updated driver search by nVidia model, do not download, just check correct driver version
[http://www.geforce.com/drivers](http://www.geforce.com/drivers) 

It looks like Titan needs the very newest drivers.
Did you install from nVidia with .run (not recommended), Ubuntu repository (may not be new enough) or from ppa?

 #What is installed
dpkg -l | grep -i nvidia
dkms status

 sudo apt-cache policy nvidia* 
lsmod | grep nvidia 

 Ubuntu Launches Its "Fresh" Proprietary Driver PPA - August 2015
[http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA](http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA)
Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
sudo apt-add-repository ppa:graphics-drivers/ppa 

 # Shows standard repository versions
ubuntu-drivers devices
sudo apt-add-repository ppa:graphics-drivers/ppa
# should show newest versions available in addition
ubuntu-drivers devices 

If you need to change drivers, you must fully purge old driver. Not sure details on a .run but it has its own script.

 # Houseclean out all old versions to avoid issues
sudo apt-get remove --purge < nvidiadriverpackagename>
# [ using the correct names] for each driver, before running:
sudo apt-get purge nvidia*
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

---

### Post by Welly Wu on 2016-10-02
```
wellywu@ZareasonZeto:~$ dpkg -l|grep -i nvidiaii  bbswitch-dkms                                               0.8-3ubuntu1                                                amd64        Interface for toggling the power on NVIDIA Optimus video cards
ii  libcuda1-367                                                367.44-0ubuntu0~gpu16.04.1                                  amd64        NVIDIA CUDA runtime library
ii  nvidia-367                                                  367.44-0ubuntu0~gpu16.04.1                                  amd64        NVIDIA binary driver - version 367.44
ii  nvidia-opencl-icd-367                                       367.44-0ubuntu0~gpu16.04.1                                  amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                                0.8.2                                                       amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                                             370.28-0ubuntu0~gpu16.04.1                                  amd64        Tool for configuring the NVIDIA graphics driver
wellywu@ZareasonZeto:~$ dkms status
bbswitch, 0.8, 4.4.0-38-generic, x86_64: installed
bbswitch, 0.8, 4.6.7-040607-generic, x86_64: installed
nvidia-367, 367.44, 4.4.0-38-generic, x86_64: installed
nvidia-367, 367.44, 4.6.7-040607-generic, x86_64: installed
wellywu@ZareasonZeto:~$
```

```
wellywu@ZareasonZeto:~$ sudo apt-cache policy nvidia*[sudo] password for wellywu: 
nvidia-325-updates:
  Installed: (none)
  Candidate: (none)
  Version table:
nvidia-346-updates:
  Installed: (none)
  Candidate: 352.63-0ubuntu3
  Version table:
     352.63-0ubuntu3 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/restricted amd64 Packages
nvidia-driver-binary:
  Installed: (none)
  Candidate: (none)
  Version table:
nvidia-331-dev:
  Installed: (none)
  Candidate: 340.98-0ubuntu0~gpu16.04.1
  Version table:
     340.98-0ubuntu0~gpu16.04.1 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 Packages
     340.96-0ubuntu3 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/restricted amd64 Packages
nvidia-304-updates-dev:
  Installed: (none)
  Candidate: 304.132-0ubuntu0~gpu16.04.1
  Version table:
     304.132-0ubuntu0~gpu16.04.1 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 Packages
     304.131-0ubuntu3 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/restricted amd64 Packages
nvidia-libopencl1-346-updates:
  Installed: (none)
  Candidate: 352.63-0ubuntu3
  Version table:
     352.63-0ubuntu3 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/multiverse amd64 Packages
nvidia-340-updates-uvm:
  Installed: (none)
  Candidate: 340.96-0ubuntu2
  Version table:
     340.96-0ubuntu2 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/restricted amd64 Packages
nvidia-331-updates-uvm:
  Installed: (none)
  Candidate: 340.98-0ubuntu0~gpu16.04.1
  Version table:
     340.98-0ubuntu0~gpu16.04.1 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 Packages
     340.96-0ubuntu3 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/restricted amd64 Packages
nvidia-glx:
  Installed: (none)
  Candidate: (none)
  Version table:
nvidia-cg-toolkit:
  Installed: (none)
  Candidate: 3.1.0013-2
  Version table:
     3.1.0013-2 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/multiverse amd64 Packages
nvidia-opencl-icd-340-updates:
  Installed: (none)
  Candidate: 340.98-0ubuntu0~gpu16.04.1
  Version table:
     340.98-0ubuntu0~gpu16.04.1 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 Packages
     340.96-0ubuntu3 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/multiverse amd64 Packages
nvidia-370-dev:
  Installed: (none)
  Candidate: 370.28-0ubuntu0~gpu16.04.1
  Version table:
     370.28-0ubuntu0~gpu16.04.1 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 Packages
nvidia:
  Installed: (none)
  Candidate: (none)
  Version table:
nvidia-driver:
  Installed: (none)
  Candidate: (none)
  Version table:
nvidia-364-dev:
  Installed: (none)
  Candidate: 364.19-0ubuntu0~gpu16.04.6
  Version table:
     364.19-0ubuntu0~gpu16.04.6 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 Packages
nvidia-358-dev:
  Installed: (none)
  Candidate: 358.16-0ubuntu0~gpu16.04.5
  Version table:
     358.16-0ubuntu0~gpu16.04.5 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 Packages
nvidia-modprobe:
  Installed: (none)
  Candidate: 361.28-1
  Version table:
     361.28-1 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/multiverse amd64 Packages
nvidia-texture-tools:
  Installed: (none)
  Candidate: (none)
  Version table:
nvidia-legacy-340xx-vdpau-driver:
  Installed: (none)
  Candidate: (none)
  Version table:
nvidia-349-updates:
  Installed: (none)
  Candidate: (none)
  Version table:
nvidia-kernel-686-pae:
  Installed: (none)
  Candidate: (none)
  Version table:
nvidia-opencl-icd-304-updates:
  Installed: (none)
  Candidate: 304.132-0ubuntu0~gpu16.04.1
  Version table:
     304.132-0ubuntu0~gpu16.04.1 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 Packages
     304.131-0ubuntu3 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/restricted amd64 Packages
nvidia-310-updates:
  Installed: (none)
  Candidate: (none)
  Version table:
nvidia-331-updates:
  Installed: (none)
  Candidate: 340.98-0ubuntu0~gpu16.04.1
  Version table:
     340.98-0ubuntu0~gpu16.04.1 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 Packages
     340.96-0ubuntu3 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/restricted amd64 Packages
nvidia-352-dev:
  Installed: (none)
  Candidate: 361.42-0ubuntu2
  Version table:
     361.42-0ubuntu2 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/restricted amd64 Packages
     352.79-0ubuntu0~gpu16.04.2 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 Packages
nvidia-vdpau-driver:
  Installed: (none)
  Candidate: (none)
  Version table:
nvidia-346-dev:
  Installed: (none)
  Candidate: 352.63-0ubuntu3
  Version table:
     352.63-0ubuntu3 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/restricted amd64 Packages
nvidia-libopencl1-331-updates:
  Installed: (none)
  Candidate: 340.98-0ubuntu0~gpu16.04.1
  Version table:
     340.98-0ubuntu0~gpu16.04.1 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 Packages
     340.96-0ubuntu3 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/multiverse amd64 Packages
nvidia-smi:
  Installed: (none)
  Candidate: (none)
  Version table:
nvidia-opencl-icd-361-updates:
  Installed: (none)
  Candidate: 361.42-0ubuntu2
  Version table:
     361.42-0ubuntu2 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/multiverse amd64 Packages
nvidia-313-updates:
  Installed: (none)
  Candidate: (none)
  Version table:
nvidia-334-updates:
  Installed: (none)
  Candidate: (none)
  Version table:
nvidia-331-uvm:
  Installed: (none)
  Candidate: 340.98-0ubuntu0~gpu16.04.1
  Version table:
     340.98-0ubuntu0~gpu16.04.1 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 Packages
     340.96-0ubuntu3 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/restricted amd64 Packages
nvidia-prime:
  Installed: 0.8.2
  Candidate: 0.8.2
  Version table:
 *** 0.8.2 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/main amd64 Packages
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status
nvidia-kernel-dkms:
  Installed: (none)
  Candidate: (none)
  Version table:
nvidia-current-updates:
  Installed: (none)
  Candidate: 304.131-0ubuntu3
  Version table:
     304.131-0ubuntu3 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/restricted amd64 Packages
nvidia-340-dev:
  Installed: (none)
  Candidate: 340.98-0ubuntu0~gpu16.04.1
  Version table:
     340.98-0ubuntu0~gpu16.04.1 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 Packages
     340.96-0ubuntu3 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/restricted amd64 Packages
nvidia-nsight:
  Installed: (none)
  Candidate: 7.5.18-0ubuntu1
  Version table:
     7.5.18-0ubuntu1 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/multiverse amd64 Packages
nvidia-common:
  Installed: (none)
  Candidate: 1:0.4.17.2
  Version table:
     1:0.4.17.2 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial-updates/universe amd64 Packages
     1:0.4.17 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/universe amd64 Packages
     1:0.4.15 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 Packages
nvidia-opencl-icd-346-updates:
  Installed: (none)
  Candidate: 352.63-0ubuntu3
  Version table:
     352.63-0ubuntu3 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/multiverse amd64 Packages
nvidia-352-updates:
  Installed: (none)
  Candidate: 361.42-0ubuntu2
  Version table:
     361.42-0ubuntu2 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/restricted amd64 Packages
nvidia-kernel-amd64:
  Installed: (none)
  Candidate: (none)
  Version table:
nvidia-current-dev:
  Installed: (none)
  Candidate: 304.132-0ubuntu0~gpu16.04.1
  Version table:
     304.132-0ubuntu0~gpu16.04.1 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 Packages
     304.131-0ubuntu3 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/restricted amd64 Packages
nvidia-libopencl1-352-updates:
  Installed: (none)
  Candidate: 361.42-0ubuntu2
  Version table:
     361.42-0ubuntu2 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/multiverse amd64 Packages
nvidia-355-updates:
  Installed: (none)
  Candidate: (none)
  Version table:
nvidia-current:
  Installed: (none)
  Candidate: 304.132-0ubuntu0~gpu16.04.1
  Version table:
     304.132-0ubuntu0~gpu16.04.1 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 Packages
     304.131-0ubuntu3 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/restricted amd64 Packages
nvidia-profiler:
  Installed: (none)
  Candidate: 7.5.18-0ubuntu1
  Version table:
     7.5.18-0ubuntu1 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/multiverse amd64 Packages
nvidia-337-updates:
  Installed: (none)
  Candidate: (none)
  Version table:
nvidia-367-dev:
  Installed: (none)
  Candidate: 367.44-0ubuntu0~gpu16.04.1
  Version table:
     367.44-0ubuntu0~gpu16.04.1 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 Packages
nvidia-cuda-toolkit:
  Installed: (none)
  Candidate: 7.5.18-0ubuntu1
  Version table:
     7.5.18-0ubuntu1 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/multiverse amd64 Packages
nvidia-340-updates-dev:
  Installed: (none)
  Candidate: 340.98-0ubuntu0~gpu16.04.1
  Version table:
     340.98-0ubuntu0~gpu16.04.1 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 Packages
     340.96-0ubuntu3 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/restricted amd64 Packages
nvidia-319-updates:
  Installed: (none)
  Candidate: (none)
  Version table:
nvidia-304-dev:
  Installed: (none)
  Candidate: 304.132-0ubuntu0~gpu16.04.1
  Version table:
     304.132-0ubuntu0~gpu16.04.1 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 Packages
     304.131-0ubuntu3 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/restricted amd64 Packages
nvidia-331-updates-dev:
  Installed: (none)
  Candidate: 340.98-0ubuntu0~gpu16.04.1
  Version table:
     340.98-0ubuntu0~gpu16.04.1 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 Packages
     340.96-0ubuntu3 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/restricted amd64 Packages
nvidia-visual-profiler:
  Installed: (none)
  Candidate: 7.5.18-0ubuntu1
  Version table:
     7.5.18-0ubuntu1 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/multiverse amd64 Packages
nvidia-persistenced:
  Installed: (none)
  Candidate: 361.28-1
  Version table:
     361.28-1 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/multiverse amd64 Packages
nvidia-current-updates-dev:
  Installed: (none)
  Candidate: 304.131-0ubuntu3
  Version table:
     304.131-0ubuntu3 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/restricted amd64 Packages
nvidia-361-dev:
  Installed: (none)
  Candidate: 361.45.18-0ubuntu0~gpu16.04.1
  Version table:
     361.45.18-0ubuntu0~gpu16.04.1 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 Packages
     361.42-0ubuntu2 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/restricted amd64 Packages
nvidia-settings-binary:
  Installed: (none)
  Candidate: (none)
  Version table:
nvidia-355-dev:
  Installed: (none)
  Candidate: 355.11-0ubuntu0~gpu16.04.4
  Version table:
     355.11-0ubuntu0~gpu16.04.4 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 Packages
nvidia-361-updates-dev:
  Installed: (none)
  Candidate: 361.42-0ubuntu2
  Version table:
     361.42-0ubuntu2 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/restricted amd64 Packages
nvidia-libopencl1-304:
  Installed: (none)
  Candidate: 304.132-0ubuntu0~gpu16.04.1
  Version table:
     304.132-0ubuntu0~gpu16.04.1 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 Packages
     304.131-0ubuntu3 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/multiverse amd64 Packages
nvidia-libopencl1-331:
  Installed: (none)
  Candidate: 340.98-0ubuntu0~gpu16.04.1
  Version table:
     340.98-0ubuntu0~gpu16.04.1 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 Packages
     340.96-0ubuntu3 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/multiverse amd64 Packages
nvidia-libopencl1-340:
  Installed: (none)
  Candidate: 340.98-0ubuntu0~gpu16.04.1
  Version table:
     340.98-0ubuntu0~gpu16.04.1 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 Packages
     340.96-0ubuntu3 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/multiverse amd64 Packages
nvidia-libopencl1-346:
  Installed: (none)
  Candidate: 352.63-0ubuntu3
  Version table:
     352.63-0ubuntu3 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/multiverse amd64 Packages
nvidia-libopencl1-352:
  Installed: (none)
  Candidate: 361.42-0ubuntu2
  Version table:
     361.42-0ubuntu2 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/multiverse amd64 Packages
     352.79-0ubuntu0~gpu16.04.2 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 Packages
nvidia-libopencl1-355:
  Installed: (none)
  Candidate: 355.11-0ubuntu0~gpu16.04.4
  Version table:
     355.11-0ubuntu0~gpu16.04.4 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 Packages
nvidia-libopencl1-358:
  Installed: (none)
  Candidate: 358.16-0ubuntu0~gpu16.04.5
  Version table:
     358.16-0ubuntu0~gpu16.04.5 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 Packages
nvidia-libopencl1-361:
  Installed: (none)
  Candidate: 361.45.18-0ubuntu0~gpu16.04.1
  Version table:
     361.45.18-0ubuntu0~gpu16.04.1 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 Packages
     361.42-0ubuntu2 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/multiverse amd64 Packages
nvidia-libopencl1-364:
  Installed: (none)
  Candidate: 364.19-0ubuntu0~gpu16.04.6
  Version table:
     364.19-0ubuntu0~gpu16.04.6 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 Packages
nvidia-libopencl1-367:
  Installed: (none)
  Candidate: 367.44-0ubuntu0~gpu16.04.1
  Version table:
     367.44-0ubuntu0~gpu16.04.1 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 Packages
nvidia-libopencl1-370:
  Installed: (none)
  Candidate: 370.28-0ubuntu0~gpu16.04.1
  Version table:
     370.28-0ubuntu0~gpu16.04.1 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 Packages
nvidia-kernel-486:
  Installed: (none)
  Candidate: (none)
  Version table:
nvidia-352-updates-dev:
  Installed: (none)
  Candidate: 361.42-0ubuntu2
  Version table:
     361.42-0ubuntu2 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/restricted amd64 Packages
nvidia-opencl-icd-331-updates:
  Installed: (none)
  Candidate: 340.98-0ubuntu0~gpu16.04.1
  Version table:
     340.98-0ubuntu0~gpu16.04.1 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 Packages
     340.96-0ubuntu3 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/multiverse amd64 Packages
nvidia-opencl-icd-352-updates:
  Installed: (none)
  Candidate: 361.42-0ubuntu2
  Version table:
     361.42-0ubuntu2 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/multiverse amd64 Packages
nvidia-304-updates:
  Installed: (none)
  Candidate: 304.132-0ubuntu0~gpu16.04.1
  Version table:
     304.132-0ubuntu0~gpu16.04.1 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 Packages
     304.131-0ubuntu3 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/restricted amd64 Packages
nvidia-340-uvm:
  Installed: (none)
  Candidate: 340.98-0ubuntu0~gpu16.04.1
  Version table:
     340.98-0ubuntu0~gpu16.04.1 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 Packages
     340.96-0ubuntu3 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/restricted amd64 Packages
nvidia-libopencl1-304-updates:
  Installed: (none)
  Candidate: 304.132-0ubuntu0~gpu16.04.1
  Version table:
     304.132-0ubuntu0~gpu16.04.1 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 Packages
     304.131-0ubuntu3 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/multiverse amd64 Packages
nvidia-cuda-dev:
  Installed: (none)
  Candidate: 7.5.18-0ubuntu1
  Version table:
     7.5.18-0ubuntu1 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/multiverse amd64 Packages
nvidia-cuda-doc:
  Installed: (none)
  Candidate: 7.5.18-0ubuntu1
  Version table:
     7.5.18-0ubuntu1 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/multiverse amd64 Packages
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/multiverse i386 Packages
nvidia-340-updates:
  Installed: (none)
  Candidate: 340.98-0ubuntu0~gpu16.04.1
  Version table:
     340.98-0ubuntu0~gpu16.04.1 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 Packages
     340.96-0ubuntu3 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/restricted amd64 Packages
nvidia-361-updates:
  Installed: (none)
  Candidate: 361.42-0ubuntu2
  Version table:
     361.42-0ubuntu2 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/restricted amd64 Packages
nvidia-libopencl1-dev:
  Installed: (none)
  Candidate: (none)
  Version table:
nvidia-opencl-dev:
  Installed: (none)
  Candidate: 7.5.18-0ubuntu1
  Version table:
     7.5.18-0ubuntu1 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/multiverse amd64 Packages
nvidia-cg-dev:
  Installed: (none)
  Candidate: 3.1.0013-2
  Version table:
     3.1.0013-2 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/multiverse amd64 Packages
nvidia-cg-doc:
  Installed: (none)
  Candidate: 3.1.0013-2
  Version table:
     3.1.0013-2 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/multiverse amd64 Packages
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/multiverse i386 Packages
nvidia-libopencl1:
  Installed: (none)
  Candidate: (none)
  Version table:
nvidia-libopencl1-340-updates:
  Installed: (none)
  Candidate: 340.98-0ubuntu0~gpu16.04.1
  Version table:
     340.98-0ubuntu0~gpu16.04.1 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 Packages
     340.96-0ubuntu3 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/multiverse amd64 Packages
nvidia-libopencl1-361-updates:
  Installed: (none)
  Candidate: 361.42-0ubuntu2
  Version table:
     361.42-0ubuntu2 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/multiverse amd64 Packages
nvidia-opencl-icd-304:
  Installed: (none)
  Candidate: 304.132-0ubuntu0~gpu16.04.1
  Version table:
     304.132-0ubuntu0~gpu16.04.1 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 Packages
     304.131-0ubuntu3 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/restricted amd64 Packages
nvidia-opencl-icd-331:
  Installed: (none)
  Candidate: 340.98-0ubuntu0~gpu16.04.1
  Version table:
     340.98-0ubuntu0~gpu16.04.1 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 Packages
     340.96-0ubuntu3 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/multiverse amd64 Packages
nvidia-opencl-icd-340:
  Installed: (none)
  Candidate: 340.98-0ubuntu0~gpu16.04.1
  Version table:
     340.98-0ubuntu0~gpu16.04.1 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 Packages
     340.96-0ubuntu3 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/restricted amd64 Packages
nvidia-opencl-icd-346:
  Installed: (none)
  Candidate: 352.63-0ubuntu3
  Version table:
     352.63-0ubuntu3 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/multiverse amd64 Packages
nvidia-opencl-icd-352:
  Installed: (none)
  Candidate: 361.42-0ubuntu2
  Version table:
     361.42-0ubuntu2 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/multiverse amd64 Packages
     352.79-0ubuntu0~gpu16.04.2 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 Packages
nvidia-opencl-icd-355:
  Installed: (none)
  Candidate: 355.11-0ubuntu0~gpu16.04.4
  Version table:
     355.11-0ubuntu0~gpu16.04.4 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 Packages
nvidia-opencl-icd-358:
  Installed: (none)
  Candidate: 358.16-0ubuntu0~gpu16.04.5
  Version table:
     358.16-0ubuntu0~gpu16.04.5 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 Packages
nvidia-opencl-icd-361:
  Installed: (none)
  Candidate: 361.45.18-0ubuntu0~gpu16.04.1
  Version table:
     361.45.18-0ubuntu0~gpu16.04.1 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 Packages
     361.42-0ubuntu2 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/restricted amd64 Packages
nvidia-opencl-icd-364:
  Installed: (none)
  Candidate: 364.19-0ubuntu0~gpu16.04.6
  Version table:
     364.19-0ubuntu0~gpu16.04.6 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 Packages
nvidia-opencl-icd-367:
  Installed: 367.44-0ubuntu0~gpu16.04.1
  Candidate: 367.44-0ubuntu0~gpu16.04.1
  Version table:
 *** 367.44-0ubuntu0~gpu16.04.1 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status
nvidia-opencl-icd-370:
  Installed: (none)
  Candidate: 370.28-0ubuntu0~gpu16.04.1
  Version table:
     370.28-0ubuntu0~gpu16.04.1 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 Packages
nvidia-cuda-gdb:
  Installed: (none)
  Candidate: 7.5.18-0ubuntu1
  Version table:
     7.5.18-0ubuntu1 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/multiverse amd64 Packages
nvidia-experimental-304:
  Installed: (none)
  Candidate: 304.131-0ubuntu3
  Version table:
     304.131-0ubuntu3 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/restricted amd64 Packages
nvidia-experimental-310:
  Installed: (none)
  Candidate: (none)
  Version table:
nvidia-experimental-313:
  Installed: (none)
  Candidate: (none)
  Version table:
nvidia-experimental-319:
  Installed: (none)
  Candidate: (none)
  Version table:
nvidia-experimental-325:
  Installed: (none)
  Candidate: (none)
  Version table:
nvidia-experimental-331:
  Installed: (none)
  Candidate: (none)
  Version table:
nvidia-experimental-334:
  Installed: (none)
  Candidate: (none)
  Version table:
nvidia-experimental-337:
  Installed: (none)
  Candidate: (none)
  Version table:
nvidia-experimental-340:
  Installed: (none)
  Candidate: (none)
  Version table:
nvidia-experimental-343:
  Installed: (none)
  Candidate: (none)
  Version table:
nvidia-experimental-346:
  Installed: (none)
  Candidate: (none)
  Version table:
nvidia-experimental-349:
  Installed: (none)
  Candidate: (none)
  Version table:
nvidia-experimental-352:
  Installed: (none)
  Candidate: (none)
  Version table:
nvidia-experimental-355:
  Installed: (none)
  Candidate: (none)
  Version table:
nvidia-experimental-304-dev:
  Installed: (none)
  Candidate: 304.131-0ubuntu3
  Version table:
     304.131-0ubuntu3 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/restricted amd64 Packages
nvidia-343-updates:
  Installed: (none)
  Candidate: (none)
  Version table:
nvidia-304:
  Installed: (none)
  Candidate: 304.132-0ubuntu0~gpu16.04.1
  Version table:
     304.132-0ubuntu0~gpu16.04.1 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 Packages
     304.131-0ubuntu3 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/restricted amd64 Packages
nvidia-310:
  Installed: (none)
  Candidate: (none)
  Version table:
nvidia-313:
  Installed: (none)
  Candidate: (none)
  Version table:
nvidia-319:
  Installed: (none)
  Candidate: (none)
  Version table:
nvidia-325:
  Installed: (none)
  Candidate: (none)
  Version table:
nvidia-331:
  Installed: (none)
  Candidate: 340.98-0ubuntu0~gpu16.04.1
  Version table:
     340.98-0ubuntu0~gpu16.04.1 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 Packages
     340.96-0ubuntu3 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/restricted amd64 Packages
nvidia-334:
  Installed: (none)
  Candidate: (none)
  Version table:
nvidia-337:
  Installed: (none)
  Candidate: (none)
  Version table:
nvidia-340:
  Installed: (none)
  Candidate: 340.98-0ubuntu0~gpu16.04.1
  Version table:
     340.98-0ubuntu0~gpu16.04.1 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 Packages
     340.96-0ubuntu3 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/restricted amd64 Packages
nvidia-343:
  Installed: (none)
  Candidate: (none)
  Version table:
nvidia-346:
  Installed: (none)
  Candidate: 352.63-0ubuntu3
  Version table:
     352.63-0ubuntu3 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/restricted amd64 Packages
nvidia-349:
  Installed: (none)
  Candidate: (none)
  Version table:
nvidia-352:
  Installed: (none)
  Candidate: 361.42-0ubuntu2
  Version table:
     361.42-0ubuntu2 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/restricted amd64 Packages
     352.79-0ubuntu0~gpu16.04.2 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 Packages
nvidia-355:
  Installed: (none)
  Candidate: 355.11-0ubuntu0~gpu16.04.4
  Version table:
     355.11-0ubuntu0~gpu16.04.4 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 Packages
nvidia-358:
  Installed: (none)
  Candidate: 358.16-0ubuntu0~gpu16.04.5
  Version table:
     358.16-0ubuntu0~gpu16.04.5 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 Packages
nvidia-361:
  Installed: (none)
  Candidate: 361.45.18-0ubuntu0~gpu16.04.1
  Version table:
     361.45.18-0ubuntu0~gpu16.04.1 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 Packages
     361.42-0ubuntu2 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/restricted amd64 Packages
nvidia-364:
  Installed: (none)
  Candidate: 364.19-0ubuntu0~gpu16.04.6
  Version table:
     364.19-0ubuntu0~gpu16.04.6 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 Packages
nvidia-367:
  Installed: 367.44-0ubuntu0~gpu16.04.1
  Candidate: 367.44-0ubuntu0~gpu16.04.1
  Version table:
 *** 367.44-0ubuntu0~gpu16.04.1 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status
nvidia-370:
  Installed: (none)
  Candidate: 370.28-0ubuntu0~gpu16.04.1
  Version table:
     370.28-0ubuntu0~gpu16.04.1 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 Packages
nvidia-346-updates-dev:
  Installed: (none)
  Candidate: 352.63-0ubuntu3
  Version table:
     352.63-0ubuntu3 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/restricted amd64 Packages
nvidia-settings:
  Installed: 370.28-0ubuntu0~gpu16.04.1
  Candidate: 370.28-0ubuntu0~gpu16.04.1
  Version table:
 *** 370.28-0ubuntu0~gpu16.04.1 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status
     361.42-0ubuntu1 500
        500 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive xenial/main amd64 Packages
nvidia-opencl-icd:
  Installed: (none)
  Candidate: (none)
  Version table:
wellywu@ZareasonZeto:~$
```

```
wellywu@ZareasonZeto:~$ lsmod | grep nvidianvidia_uvm            745472  0
nvidia_drm             45056  1
nvidia_modeset        765952  9 nvidia_drm
drm_kms_helper        155648  1 nvidia_drm
drm                   364544  4 drm_kms_helper,nvidia_drm
nvidia              11476992  157 nvidia_modeset,nvidia_uvm
wellywu@ZareasonZeto:~$ 
```

---

### Post by Welly Wu on 2016-10-02
I added both the Xorg Edgers and Ubuntu Graphics Drivers PPAs and I installed 367.44 64 bit from the PPAs. Then, I restarted my desktop PC. I noticed that after setting VLC to use VDPAU as the graphics rendering that my TV shows and movies play smoothly again. Just so you know, I am connected to Private Internet Access VPN and I use the Vivaldi web browser to watch online videos. I am thinking that I might need to try Google Chrome or Mozilla Firefox and disconnect from the VPN to see if online videos will play smoothly again. I might try this later today.

Here is my vivaldi://gpu configuration:
```
[COLOR=#000000][FONT=sans-serif]**Graphics Feature Status**


[LIST]
[*]Canvas: [COLOR=#008000]Hardware accelerated[/COLOR]
[*]Flash: [COLOR=#008000]Hardware accelerated[/COLOR]
[*]Flash Stage3D: [COLOR=#008000]Hardware accelerated[/COLOR]
[*]Flash Stage3D Baseline profile: [COLOR=#008000]Hardware accelerated[/COLOR]
[*]Compositing: [COLOR=#008000]Hardware accelerated[/COLOR]
[*]Multiple Raster Threads: [COLOR=#008000]Enabled[/COLOR]
[*]Native GpuMemoryBuffers: [COLOR=#808000]Software only. Hardware acceleration disabled[/COLOR]
[*]Rasterization: [COLOR=#008000]Hardware accelerated on all pages[/COLOR]
[*]Video Decode: [COLOR=#008000]Hardware accelerated[/COLOR]
[*]Video Encode: [COLOR=#008000]Hardware accelerated[/COLOR]
[*]WebGL: [COLOR=#008000]Hardware accelerated[/COLOR]
[/LIST]
[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]**Driver Bug Workarounds**


[LIST]
[*]clear_uniforms_before_first_program_use
[*]disable_discard_framebuffer
[*]disable_framebuffer_cmaa
[*]force_cube_complete
[*]init_gl_position_in_vertex_shader
[*]init_vertex_attributes
[*]pack_parameters_workaround_with_pack_buffer
[*]scalarize_vec_and_mat_constructor_args
[*]unpack_alignment_workaround_with_unpack_buffer
[*]unpack_overlapping_rows_separately_unpack_buffer
[*]use_current_program_after_successful_link
[*]use_virtualized_gl_contexts
[/LIST]
[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]**Problems Detected**


[LIST]
[*]Always call glUseProgram after a successful link to avoid a driver bug: [349137]("http://crbug.com/349137")
*Applied Workarounds: [COLOR=#808000]use_current_program_after_successful_link[/COLOR]*
[*][I]Program link fails in NVIDIA Linux if gl_Position is not set: [286468]("http://crbug.com/286468")
*Applied Workarounds: [COLOR=#808000]init_gl_position_in_vertex_shader[/COLOR]*[/I]
[*][I][I]Clear uniforms before first program use on all platforms: [124764]("http://crbug.com/124764"), [349137]("http://crbug.com/349137")
*Applied Workarounds: [COLOR=#808000]clear_uniforms_before_first_program_use[/COLOR]*[/I][/I]
[*][I][I][I]Linux NVIDIA drivers don't have the correct defaults for vertex attributes: [351528]("http://crbug.com/351528")
*Applied Workarounds: [COLOR=#808000]init_vertex_attributes[/COLOR]*[/I][/I][/I]
[*][I][I][I]Always rewrite vec/mat constructors to be consistent: [398694]("http://crbug.com/398694")
*Applied Workarounds: [COLOR=#808000]scalarize_vec_and_mat_constructor_args[/COLOR]*[/I][/I][/I]
[*][I][I][I]MakeCurrent is slow on Linux with NVIDIA drivers: [449150]("http://crbug.com/449150"), [514510]("http://crbug.com/514510")
*Applied Workarounds: [COLOR=#808000]use_virtualized_gl_contexts[/COLOR]*[/I][/I][/I]
[*][I][I][I]NVIDIA fails glReadPixels from incomplete cube map texture: [518889]("http://crbug.com/518889")
*Applied Workarounds: [COLOR=#808000]force_cube_complete[/COLOR]*[/I][/I][/I]
[*][I][I][I]Pack parameters work incorrectly with pack buffer bound: [563714]("http://crbug.com/563714")
*Applied Workarounds: [COLOR=#808000]pack_parameters_workaround_with_pack_buffer[/COLOR]*[/I][/I][/I]
[*][I][I][I]Alignment works incorrectly with unpack buffer bound: [563714]("http://crbug.com/563714")
*Applied Workarounds: [COLOR=#808000]unpack_alignment_workaround_with_unpack_buffer[/COLOR]*[/I][/I][/I]
[*][I][I][I]Framebuffer discarding can hurt performance on non-tilers: [570897]("http://crbug.com/570897")
*Applied Workarounds: [COLOR=#808000]disable_discard_framebuffer[/COLOR]*[/I][/I][/I]
[*][I][I][I]Unpacking overlapping rows from unpack buffers is unstable on NVIDIA GL driver: [596774]("http://crbug.com/596774")
*Applied Workarounds: [COLOR=#808000]unpack_overlapping_rows_separately_unpack_buffer[/COLOR]*[/I][/I][/I]
[*][I][I][I]Limited enabling of Chromium GL_INTEL_framebuffer_CMAA: [535198]("http://crbug.com/535198")
*Applied Workarounds: [COLOR=#808000]disable_framebuffer_cmaa[/COLOR]*[/I][/I][/I]
[*][I][I][I]Native GpuMemoryBuffers have been disabled, either via about:flags or command line.
*Disabled Features: [COLOR=#FF0000]native_gpu_memory_buffers[/COLOR]*[/I][/I][/I]
[/LIST]
[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]***[I][I]Version Information*[/I][/I]**

[TABLE="width: 1845"]
[TR]
[TD]**Data exported**[/TD]
[TD]10/2/2016, 2:06:49 PM[/TD]
[/TR]
[TR]
[TD]**Chrome version**[/TD]
[TD]Chrome/53.0.2785.122[/TD]
[/TR]
[TR]
[TD]**Operating system**[/TD]
[TD]Linux 4.6.7-040607-generic[/TD]
[/TR]
[TR]
[TD]**Software rendering list version**[/TD]
[TD]0[/TD]
[/TR]
[TR]
[TD]**Driver bug list version**[/TD]
[TD]8.93[/TD]
[/TR]
[TR]
[TD]**ANGLE commit id**[/TD]
[TD]unknown hash[/TD]
[/TR]
[TR]
[TD]**2D graphics backend**[/TD]
[TD]Skia[/TD]
[/TR]
[TR]
[TD]**Command Line Args**[/TD]
[TD]--ppapi-flash-path=/usr/lib/pepperflashplugin-nonfree/libpepflashplayer.so --ppapi-flash-version=23.0.0.162 --always-authorize-plugins --disable-translate --ppapi-flash-path=/usr/lib/pepperflashplugin-nonfree/libpepflashplayer.so --ppapi-flash-version=23.0.0.162 --window-depth=24 --wm-user-time-ms=42037071 --x11-visual-id=33 --window-depth=24 --x11-visual-id=33 --wm-user-time-ms=42701701 --flag-switches-begin --allow-nacl-socket-api=* --enable-fast-unload --force-gpu-rasterization --use-simple-cache-backend=on --enable-tcp-fastopen --enable-webgl-draft-extensions --ignore-gpu-blacklist --sync-url=https://chrome-sync.sandbox.google.com/chrome-sync/alpha --enable-features=WebRTC-H264WithOpenH264FFmpeg --flag-switches-end[/TD]
[/TR]
[/TABLE]


[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]***[I][I]Driver Information*[/I][/I]**

[TABLE="width: 1845"]
[TR]
[TD]**Initialization time**[/TD]
[TD]271[/TD]
[/TR]
[TR]
[TD]**In-process GPU**[/TD]
[TD]false[/TD]
[/TR]
[TR]
[TD]**Sandboxed**[/TD]
[TD]true[/TD]
[/TR]
[TR]
[TD]**GPU0**[/TD]
[TD]VENDOR = 0x10de, DEVICE= 0x17c2[/TD]
[/TR]
[TR]
[TD]**Optimus**[/TD]
[TD]false[/TD]
[/TR]
[TR]
[TD]**AMD switchable**[/TD]
[TD]false[/TD]
[/TR]
[TR]
[TD]**Driver vendor**[/TD]
[TD]NVIDIA[/TD]
[/TR]
[TR]
[TD]**Driver version**[/TD]
[TD]367.44[/TD]
[/TR]
[TR]
[TD]**Driver date**[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]**Pixel shader version**[/TD]
[TD]4.50[/TD]
[/TR]
[TR]
[TD]**Vertex shader version**[/TD]
[TD]4.50[/TD]
[/TR]
[TR]
[TD]**Max. MSAA samples**[/TD]
[TD]32[/TD]
[/TR]
[TR]
[TD]**Machine model name**[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]**Machine model version**[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]**GL_VENDOR**[/TD]
[TD]NVIDIA Corporation[/TD]
[/TR]
[TR]
[TD]**GL_RENDERER**[/TD]
[TD]GeForce GTX TITAN X/PCIe/SSE2[/TD]
[/TR]
[TR]
[TD]**GL_VERSION**[/TD]
[TD]4.5.0 NVIDIA 367.44[/TD]
[/TR]
[TR]
[TD]**GL_EXTENSIONS**[/TD]
[TD]GL_AMD_multi_draw_indirect GL_AMD_seamless_cubemap_per_texture GL_AMD_vertex_shader_viewport_index GL_AMD_vertex_shader_layer GL_ARB_arrays_of_arrays GL_ARB_base_instance GL_ARB_bindless_texture GL_ARB_blend_func_extended GL_ARB_buffer_storage GL_ARB_cl_event GL_ARB_clear_buffer_object GL_ARB_clear_texture GL_ARB_clip_control GL_ARB_color_buffer_float GL_ARB_compatibility GL_ARB_compressed_texture_pixel_storage GL_ARB_conservative_depth GL_ARB_compute_shader GL_ARB_compute_variable_group_size GL_ARB_conditional_render_inverted GL_ARB_copy_buffer GL_ARB_copy_image GL_ARB_cull_distance GL_ARB_debug_output GL_ARB_depth_buffer_float GL_ARB_depth_clamp GL_ARB_depth_texture GL_ARB_derivative_control GL_ARB_direct_state_access GL_ARB_draw_buffers GL_ARB_draw_buffers_blend GL_ARB_draw_indirect GL_ARB_draw_elements_base_vertex GL_ARB_draw_instanced GL_ARB_enhanced_layouts GL_ARB_ES2_compatibility GL_ARB_ES3_compatibility GL_ARB_ES3_1_compatibility GL_ARB_ES3_2_compatibility GL_ARB_explicit_attrib_location GL_ARB_explicit_uniform_location GL_ARB_fragment_coord_conventions GL_ARB_fragment_layer_viewport GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_fragment_shader_interlock GL_ARB_framebuffer_no_attachments GL_ARB_framebuffer_object GL_ARB_framebuffer_sRGB GL_ARB_geometry_shader4 GL_ARB_get_program_binary GL_ARB_get_texture_sub_image GL_ARB_gpu_shader5 GL_ARB_gpu_shader_fp64 GL_ARB_gpu_shader_int64 GL_ARB_half_float_pixel GL_ARB_half_float_vertex GL_ARB_imaging GL_ARB_indirect_parameters GL_ARB_instanced_arrays GL_ARB_internalformat_query GL_ARB_internalformat_query2 GL_ARB_invalidate_subdata GL_ARB_map_buffer_alignment GL_ARB_map_buffer_range GL_ARB_multi_bind GL_ARB_multi_draw_indirect GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_occlusion_query2 GL_ARB_parallel_shader_compile GL_ARB_pipeline_statistics_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_post_depth_coverage GL_ARB_program_interface_query GL_ARB_provoking_vertex GL_ARB_query_buffer_object GL_ARB_robust_buffer_access_behavior GL_ARB_robustness GL_ARB_sample_locations GL_ARB_sample_shading GL_ARB_sampler_objects GL_ARB_seamless_cube_map GL_ARB_seamless_cubemap_per_texture GL_ARB_separate_shader_objects GL_ARB_shader_atomic_counter_ops GL_ARB_shader_atomic_counters GL_ARB_shader_ballot GL_ARB_shader_bit_encoding GL_ARB_shader_clock GL_ARB_shader_draw_parameters GL_ARB_shader_group_vote GL_ARB_shader_image_load_store GL_ARB_shader_image_size GL_ARB_shader_objects GL_ARB_shader_precision GL_ARB_shader_storage_buffer_object GL_ARB_shader_subroutine GL_ARB_shader_texture_image_samples GL_ARB_shader_texture_lod GL_ARB_shading_language_100 GL_ARB_shader_viewport_layer_array GL_ARB_shading_language_420pack GL_ARB_shading_language_include GL_ARB_shading_language_packing GL_ARB_shadow GL_ARB_sparse_buffer GL_ARB_sparse_texture GL_ARB_sparse_texture2 GL_ARB_sparse_texture_clamp GL_ARB_stencil_texturing GL_ARB_sync GL_ARB_tessellation_shader GL_ARB_texture_barrier GL_ARB_texture_border_clamp GL_ARB_texture_buffer_object GL_ARB_texture_buffer_object_rgb32 GL_ARB_texture_buffer_range GL_ARB_texture_compression GL_ARB_texture_compression_bptc GL_ARB_texture_compression_rgtc GL_ARB_texture_cube_map GL_ARB_texture_cube_map_array GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_filter_minmax GL_ARB_texture_float GL_ARB_texture_gather GL_ARB_texture_mirror_clamp_to_edge GL_ARB_texture_mirrored_repeat GL_ARB_texture_multisample GL_ARB_texture_non_power_of_two GL_ARB_texture_query_levels GL_ARB_texture_query_lod GL_ARB_texture_rectangle GL_ARB_texture_rg GL_ARB_texture_rgb10_a2ui GL_ARB_texture_stencil8 GL_ARB_texture_storage GL_ARB_texture_storage_multisample GL_ARB_texture_swizzle GL_ARB_texture_view GL_ARB_timer_query GL_ARB_transform_feedback2 GL_ARB_transform_feedback3 GL_ARB_transform_feedback_instanced GL_ARB_transform_feedback_overflow_query GL_ARB_transpose_matrix GL_ARB_uniform_buffer_object GL_ARB_vertex_array_bgra GL_ARB_vertex_array_object GL_ARB_vertex_attrib_64bit GL_ARB_vertex_attrib_binding GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_vertex_type_10f_11f_11f_rev GL_ARB_vertex_type_2_10_10_10_rev GL_ARB_viewport_array GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_texture_float GL_ATI_texture_mirror_once GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_bindable_uniform GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_depth_bounds_test GL_EXT_direct_state_access GL_EXT_draw_buffers2 GL_EXT_draw_instanced GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXTX_framebuffer_mixed_formats GL_EXT_framebuffer_multisample_blit_scaled GL_EXT_framebuffer_object GL_EXT_framebuffer_sRGB GL_EXT_geometry_shader4 GL_EXT_gpu_program_parameters GL_EXT_gpu_shader4 GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_float GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_polygon_offset_clamp GL_EXT_post_depth_coverage GL_EXT_provoking_vertex GL_EXT_raster_multisample GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_shader_objects GL_EXT_separate_specular_color GL_EXT_shader_image_load_formatted GL_EXT_shader_image_load_store GL_EXT_shader_integer_mix GL_EXT_shadow_funcs GL_EXT_sparse_texture2 GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_array GL_EXT_texture_buffer_object GL_EXT_texture_compression_dxt1 GL_EXT_texture_compression_latc GL_EXT_texture_compression_rgtc GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_filter_minmax GL_EXT_texture_integer GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_shared_exponent GL_EXT_texture_sRGB GL_EXT_texture_sRGB_decode GL_EXT_texture_storage GL_EXT_texture_swizzle GL_EXT_timer_query GL_EXT_transform_feedback2 GL_EXT_vertex_array GL_EXT_vertex_array_bgra GL_EXT_vertex_attrib_64bit GL_EXT_x11_sync_object GL_EXT_import_sync_object GL_NV_robustness_video_memory_purge GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KHR_context_flush_control GL_KHR_debug GL_KHR_no_error GL_KHR_robust_buffer_access_behavior GL_KHR_robustness GL_KTX_buffer_region GL_NV_bindless_multi_draw_indirect GL_NV_bindless_multi_draw_indirect_count GL_NV_bindless_texture GL_NV_blend_equation_advanced GL_NV_blend_equation_advanced_coherent GL_NV_blend_square GL_NV_command_list GL_NV_compute_program5 GL_NV_conditional_render GL_NV_conservative_raster GL_NV_conservative_raster_dilate GL_NV_copy_depth_to_color GL_NV_copy_image GL_NV_depth_buffer_float GL_NV_depth_clamp GL_NV_draw_texture GL_NV_draw_vulkan_image GL_NV_ES1_1_compatibility GL_NV_ES3_1_compatibility GL_NV_explicit_multisample GL_NV_fence GL_NV_fill_rectangle GL_NV_float_buffer GL_NV_fog_distance GL_NV_fragment_coverage_to_color GL_NV_fragment_program GL_NV_fragment_program_option GL_NV_fragment_program2 GL_NV_fragment_shader_interlock GL_NV_framebuffer_mixed_samples GL_NV_framebuffer_multisample_coverage GL_NV_geometry_shader4 GL_NV_geometry_shader_passthrough GL_NV_gpu_program4 GL_NV_internalformat_sample_query GL_NV_gpu_program4_1 GL_NV_gpu_program5 GL_NV_gpu_program5_mem_extended GL_NV_gpu_program_fp64 GL_NV_gpu_shader5 GL_NV_half_float GL_NV_light_max_exponent GL_NV_multisample_coverage GL_NV_multisample_filter_hint GL_NV_occlusion_query GL_NV_packed_depth_stencil GL_NV_parameter_buffer_object GL_NV_parameter_buffer_object2 GL_NV_path_rendering GL_NV_path_rendering_shared_edge GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_primitive_restart GL_NV_register_combiners GL_NV_register_combiners2 GL_NV_sample_locations GL_NV_sample_mask_override_coverage GL_NV_shader_atomic_counters GL_NV_shader_atomic_float GL_NV_shader_atomic_fp16_vector GL_NV_shader_atomic_int64 GL_NV_shader_buffer_load GL_NV_shader_storage_buffer_object GL_NV_texgen_reflection GL_NV_texture_barrier GL_NV_texture_compression_vtc GL_NV_texture_env_combine4 GL_NV_texture_multisample GL_NV_texture_rectangle GL_NV_texture_shader GL_NV_texture_shader2 GL_NV_texture_shader3 GL_NV_transform_feedback GL_NV_transform_feedback2 GL_NV_uniform_buffer_unified_memory GL_NV_vdpau_interop GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_attrib_integer_64bit GL_NV_vertex_buffer_unified_memory GL_NV_vertex_program GL_NV_vertex_program1_1 GL_NV_vertex_program2 GL_NV_vertex_program2_option GL_NV_vertex_program3 GL_NV_viewport_array2 GL_NV_viewport_swizzle GL_NVX_conditional_render GL_NVX_gpu_memory_info GL_NVX_nvenc_interop GL_NV_shader_thread_group GL_NV_shader_thread_shuffle GL_KHR_blend_equation_advanced GL_KHR_blend_equation_advanced_coherent GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SUN_slice_accum[/TD]
[/TR]
[TR]
[TD]**Disabled Extensions**[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]**Window system binding vendor**[/TD]
[TD]NVIDIA Corporation[/TD]
[/TR]
[TR]
[TD]**Window system binding version**[/TD]
[TD]1.4[/TD]
[/TR]
[TR]
[TD]**Window system binding extensions**[/TD]
[TD]GLX_EXT_visual_info GLX_EXT_visual_rating GLX_SGIX_fbconfig GLX_SGIX_pbuffer GLX_SGI_video_sync GLX_SGI_swap_control GLX_EXT_swap_control GLX_EXT_swap_control_tear GLX_EXT_texture_from_pixmap GLX_EXT_buffer_age GLX_ARB_create_context GLX_ARB_create_context_profile GLX_EXT_create_context_es_profile GLX_EXT_create_context_es2_profile GLX_ARB_create_context_robustness GLX_NV_delay_before_swap GLX_EXT_stereo_tree GLX_EXT_libglvnd GLX_ARB_context_flush_control GLX_NV_robustness_video_memory_purge GLX_ARB_multisample GLX_NV_float_buffer GLX_ARB_fbconfig_float GLX_EXT_framebuffer_sRGB GLX_NV_copy_image[/TD]
[/TR]
[TR]
[TD]**Window manager**[/TD]
[TD]Compiz[/TD]
[/TR]
[TR]
[TD]**XDG_CURRENT_DESKTOP**[/TD]
[TD]Unity[/TD]
[/TR]
[TR]
[TD]**GDMSESSION**[/TD]
[TD]ubuntu[/TD]
[/TR]
[TR]
[TD]**Compositing manager**[/TD]
[TD]Yes[/TD]
[/TR]
[TR]
[TD]**Direct rendering**[/TD]
[TD]Yes[/TD]
[/TR]
[TR]
[TD]**Reset notification strategy**[/TD]
[TD]0x8252[/TD]
[/TR]
[TR]
[TD]**GPU process crash count**[/TD]
[TD]0[/TD]
[/TR]
[/TABLE]


[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]***[I][I]Compositor Information*[/I][/I]**

[TABLE="width: 1845"]
[TR]
[TD]**Tile Update Mode**[/TD]
[TD]One-copy[/TD]
[/TR]
[TR]
[TD]**Partial Raster**[/TD]
[TD]Enabled[/TD]
[/TR]
[/TABLE]


[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]***[I][I]GpuMemoryBuffers Status*[/I][/I]**

[TABLE="width: 1845"]
[TR]
[TD]**ATC**[/TD]
[TD]Software only[/TD]
[/TR]
[TR]
[TD]**ATCIA**[/TD]
[TD]Software only[/TD]
[/TR]
[TR]
[TD]**DXT1**[/TD]
[TD]Software only[/TD]
[/TR]
[TR]
[TD]**DXT5**[/TD]
[TD]Software only[/TD]
[/TR]
[TR]
[TD]**ETC1**[/TD]
[TD]Software only[/TD]
[/TR]
[TR]
[TD]**R_8**[/TD]
[TD]Software only[/TD]
[/TR]
[TR]
[TD]**BGR_565**[/TD]
[TD]Software only[/TD]
[/TR]
[TR]
[TD]**RGBA_4444**[/TD]
[TD]Software only[/TD]
[/TR]
[TR]
[TD]**RGBX_8888**[/TD]
[TD]Software only[/TD]
[/TR]
[TR]
[TD]**RGBA_8888**[/TD]
[TD]Software only[/TD]
[/TR]
[TR]
[TD]**BGRX_8888**[/TD]
[TD]Software only[/TD]
[/TR]
[TR]
[TD]**BGRA_8888**[/TD]
[TD]Software only[/TD]
[/TR]
[TR]
[TD]**YVU_420**[/TD]
[TD]Software only[/TD]
[/TR]
[TR]
[TD]**YUV_420_BIPLANAR**[/TD]
[TD]Software only[/TD]
[/TR]
[TR]
[TD]**UYVY_422**[/TD]
[TD]Software only[/TD]
[/TR]
[/TABLE]


[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]***[I][I]Log Messages*[/I][/I]**


[LIST]
[*]*[I][I][30630:30630:1002/081626:WARNING:x11_util.cc(1409)] : X error received: serial 351, error_code 3 (BadWindow), request_code 4, minor_code 0 (Unknown)*[/I][/I]
[*]*[I][I][30630:30630:1002/081721:WARNING:x11_util.cc(1409)] : X error received: serial 405, error_code 3 (BadWindow), request_code 4, minor_code 0 (Unknown)*[/I][/I]
[*]*[I][I][30630:30630:1002/081725:WARNING:x11_util.cc(1409)] : X error received: serial 435, error_code 3 (BadWindow), request_code 4, minor_code 0 (Unknown)*[/I][/I]
[*]*[I][I][30630:30630:1002/081902:WARNING:x11_util.cc(1409)] : X error received: serial 476, error_code 3 (BadWindow), request_code 4, minor_code 0 (Unknown)*[/I][/I]
[*]*[I][I][30630:30630:1002/084136:WARNING:x11_util.cc(1409)] : X error received: serial 578, error_code 3 (BadWindow), request_code 4, minor_code 0 (Unknown)*[/I][/I]
[*]*[I][I][30630:30630:1002/133425:WARNING:x11_util.cc(1409)] : X error received: serial 765, error_code 3 (BadWindow), request_code 4, minor_code 0 (Unknown)*[/I][/I]
[*]*[I][I][30630:30630:1002/140016:WARNING:x11_util.cc(1409)] : X error received: serial 883, error_code 3 (BadWindow), request_code 4, minor_code 0 (Unknown)*[/I][/I]
[/LIST]
[/FONT][/COLOR]

```

---

### Post by Welly Wu on 2016-10-02
I just ran an Ookla Speedtest while connected to PIA VPN US New York City gateway server and here are my results:

Ping: 6 ms
Download: 53.14 MB/s
Upload: 57.73 MB/s

---

### Post by Welly Wu on 2016-10-02
Here is some important general information about my desktop PC:

wellywu@ZareasonZeto:~$ uname -r
4.6.7-040607-generic
wellywu@ZareasonZeto:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial
wellywu@ZareasonZeto:~$

---

### Post by oldfred on 2016-10-02
It looks like you have bbswitch installed.
That is for laptops that can switch between the internal Intel gpu and the graphics gpu.
Desktops cannot do that, so no need for bbswitch. And at least one other thread I saw user uninstalled it and it seemed to help.

---

### Post by Welly Wu on 2016-10-02
How do I uninstall bbswitch? What else can you see from the information that I posted which may be causing poor desktop video performance?

Thank you very much for telling me this now. I had no idea.

---

### Post by Welly Wu on 2016-10-02
At this point, what should I do?

Should I sudo apt-get purge nvidia* and copy my Xorg configuration files to a backup file and restart my desktop PC and reinstall the latest 367.44 64 bit proprietary nVidia graphics drivers again? Will the BBSwitch be reinstalled again? Do I need to check my UEFI to ensure that the Intel iGP is disabled prior to reinstalling the proprietary nVidia graphics drivers again?

Is it possible to remove the bbswitch and keep things the same? What else do I need to know?

---

### Post by Welly Wu on 2016-10-02
```
sudo apt-get remove --purge bbswitch-dkms
```

I figured it out. Now, I will restart my desktop PC and test desktop video performance again. Here's to my two fingers crossed for now.

---

### Post by Welly Wu on 2016-10-02
I removed the bbswitch-dkms software package and things continue to improve. Playing online videos is smoother with fewer dropped frames. There are a few random dropped frames during online video playback. VLC using the nVidia VDPAU hardware accelerated decoding is much smoother with few dropped frames.

Is there anything else that I can do to eliminate dropped video frames and random stuttering in video performance?

---

### Post by oldfred on 2016-10-02
I see 367 is long lived branch, but ppa has 370. Does nVidia say the changes to 370 help your model or just general improvements?

I think bbswitch was for use with Bumblebee, but new copies of nVidia have obsoleted Bumblebee for most systems. But Bumblebee was only for dual video laptops anyway.

---

### Post by Welly Wu on 2016-10-02
oldfred:

Thank you very much for the replies and help thus far.

Nvidia 370.28 64 bit is beta which means that I am not likely to try it until the 370 series becomes stable in the future. I check the nVidia website fairly regularly since I own three computers. I also own a mid-2016 Acer Predator 17X gaming laptop and a mid-2015 Apple MacBook Pro 15" with Retina Display. I use Microsoft Windows 10 Pro 64 bit "Anniversary Update" and MacOS 10.12 64 bit "Sierra." Since I am using Ubuntu 16.04.x 64 bit LTS GNU/Linux on my mid-2015 Zareason Zeto gaming desktop PC, I want to use as much stable software as possible. I don't need the latest and greatest stable software packages, but I found that upgrading to Linux kernel 3.67 AMD64 helped to improve desktop video performance a bit better. I may downgrade to Linux kernel 4.4.x AMD64 to test it now that I realized thanks to your help to remove bbswitch-dkms software package later tonight just to see how it performs.

Is there anything else that I should do other than to keep Ubuntu up to date on a regular basis? I am hoping nVidia fixes whatever problems with desktop video performance with the 370 series or a newer series to follow.

---

### Post by oldfred on 2016-10-02
Cannot help much further.

My desktop was intended not to even have a video card & just use the Intel gpu.
But I missed video outputs on z97 motherboard did not match any of the video inputs on older LCD monitor. So I added an older nVidia 620GT just to have correct ports. But primarily using open source video driver without issue. One or two of my installs I have installed the nVidia from Ubunutu's repository which is not quite the newest. Did not notice any real difference with my now older card.

---

### Post by Welly Wu on 2016-10-02
I wanted to thank oldfred for his input and help this weekend. I downgraded to Linux kernel 4.4.x AMD64 and I checked for updates and Ubuntu downloaded and installed more open and closed source software packages for the Xorg display server and client along with graphics drivers. After I restarted my desktop PC, desktop video performance is very smooth. There are almost no dropped video frames or random stuttering for online videos and for my TV show in VLC. I have to test SteamOS + GNU/Linux PC game titles this upcoming week, but I will get to that when I have time. I am experiencing near fluid desktop video performance once again and I am grateful to oldfred and the Ubuntu Forums community for taking a look at my thread.

---

### Post by Welly Wu on 2016-10-04
This problem still persists. I upgraded to Linux kernel 3.8 AMD64 and nVidia 370.28 AMD64 and I still get pretty choppy video performance. At this point, I think I might move to a different GNU/Linux distribution, but I am open to ideas. What else can I do to fix this problem? It's affecting all video playback from SteamOS + GNU/Linux PC game titles to playing back online videos to playing TV shows that I downloaded and play using VLC with the VDPAU option selected.

---

### Post by mc4man on 2016-10-04
dropped frames (choppy playback) can result from A/V desynchronisation. What happens if you playback any of these samples which are video only?
[http://jell.yfish.us/](http://jell.yfish.us/)

No fan here of vlc, maybe you should learn/try [mpv]("https://mpv.io/") though not sure that's your style of player so to speak (vlc has Tools > Codec info..> Statistics that may be informative, alt+o c alt+t from keyboard

---

### Post by RichardET on 2016-10-04
> **mc4man said:**
> dropped frames (choppy playback) can result from A/V desynchronisation. What happens if you playback any of these samples which are video only?
[http://jell.yfish.us/](http://jell.yfish.us/)

No fan here of vlc, maybe you should learn/try [mpv]("https://mpv.io/") though not sure that's your style of player so to speak (vlc has Tools > Codec info..> Statistics that may be informative, alt+o c alt+t from keyboard

Thanks for the above link of files.  On my Inspiron 3655 with an A8 processor, onboard ATI graphics, the playback is quite good.  I am using 64 bit Ubuntu Mate, version 16.04.1;

---

### Post by Welly Wu on 2016-10-04
mc4man:

I downloaded the top two files and the video playback was smooth on both of them although there was no audio. Can you explain A/V desychronization in detail to me? What is causing this problem with choppy video playback and how do I fix it?

---

### Post by Welly Wu on 2016-10-04
```
https://wiki.ubuntu.com/PulseAudio
```

Is this a step in the right direction? I get smooth video performance, but I get audio stuttering at random times. Do I need to fix my pulseaudio? How do I do this?

---

### Post by Welly Wu on 2016-10-04
This time, I solved it myself and it was simple. I installed pavucontrol and I disabled the Intel sound card since it is not connected and audio and video are synchronized. I won't mark this thread as solved yet because I have to test this further, but it seems to be fixed for now. I need to test TV shows using VLC and I need to test SteamOS + GNU/Linux PC game titles later today. My close friend Robert W. is coming later and I don't know when he will call me so I should be home to test these things out on my desktop PC. I got a tip that pulseaudio enable sound output to all sound devices and this can be a bad thing because it leads to audio video desynchronisation so I installed pavucontrol and I disabled the Intel sound card.

---

### Post by mc4man on 2016-10-04
> **Welly Wu said:**
>  so I installed pavucontrol and I disabled the Intel sound card.
Good, was going to say that because your issue was across all types of Audio/Video (vid's, games, online, ect) to  look into your audio settings. (- also you mentioned early on " to fix the Intel HD Audio audio technical issues" which seemed a bit of a red flag.

---

### Post by Welly Wu on 2016-10-04
I tested SteamOS + GNU/Linux PC game titles and the issue is now resolved to my own satisfaction. Online videos play smoothly as do ones that I downloaded and play through VLC. I had to disable the Intel HD Audio on my desktop PC to fix this problem using pavucontrol. It turned out to be a simple fix. I might downgrade to Linux kernel 4.4.x AMD64 and nVidia 367.xx AMD64 to keep my desktop PC stable later today and test it.

---

### Post by Geoffrey_Arndt on 2016-10-04
WooHooWelly! . . . Way to go, . . . shows "persistence" to detail really pays off!

---

### Post by Welly Wu on 2016-10-04
I remember installing Ubuntu 16.04.1 64 bit LTS GNU/Linux this past Saturday and I immediately encountered this problem, but I had no clue what was the underlying cause so I did my own research and tried a bunch of different things that didn't work until I reached out to Ubuntu Forum members to get more insight into the issue. Once I gave the tip of the Intel HD Audio issue and mc4man replied, I knew exactly what to do to solve it permanently and it was a very simple fix. I am glad that I stuck with Ubuntu because switching to another GNU/Linux distribution would involve more work and I'm mostly familiar with RHEL, CentOS, and Ubuntu. For my home desktop PC, I prefer Ubuntu as it is much more user friendly compared to RHEL or CentOS and I pay for RHEL Desktop every year through their subscription model. Ubuntu is ideal for SteamOS because Valve Corporation continues to support it as a targeted distribution and it is very user friendly in general. Most of the research results assume Ubuntu is being used so it would be harder to resolve this same problem had I switched to RHEL or CentOS.

Ubuntu is as easy as apple pie. Ubuntu 16.04.x 64 bit LTS GNU/Linux features key improvements across the board of which the most noticeable is the GNOME Software Center which is vastly superior to the old Ubuntu Software Center. It also has a very large software repository and PPAs and this version in particular is much more responsive and faster than previous versions due to systemD. Most of the Linux software that I installed require Ubuntu so I was hesitant about switching to RHEL or CentOS.

---

### Post by leextremist on 2017-06-26
Hi Gents,
This is what helped me [https://askubuntu.com/questions/779042/ubuntu-16-04-is-slow-and-lags](https://askubuntu.com/questions/779042/ubuntu-16-04-is-slow-and-lags) just thought I should share.

---

