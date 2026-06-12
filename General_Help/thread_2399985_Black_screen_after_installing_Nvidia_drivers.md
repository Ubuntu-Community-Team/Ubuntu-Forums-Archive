---
title: "Black screen after installing Nvidia drivers"
date: 2018-08-31
forum: General Help
---

### Post by jhapurona on 2018-08-31
So I recently installed Ubuntu (haven't used it since Natty Narwhal) to take advantage of Valves new Proton/Steam play advancements. According to guides online, to be able to use Proton I need to be using the proprietary Nvidia driver 396. So I attempted to install it as follows: 
```
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt update
sudo apt install nvidia-driver 396 
sudo nvidia-xconfig
sudo reboot
```
After reboot I was left at a blank screen unable to do anything. The caps and num lock lights were not responding on my keyboard and plugging the monitor directly into my motherboard showed nothing as well. I had to enter recovery mode and purge the Nvidia drivers. I tried installing the driver from the Software & Updates interface and had the exact same problem. I've scoured the internet since yesterday and haven't been able to find anything that works. Any help would be greatly appreciated.

```

System:    Host: Asus-Pro-Gamer Kernel: 4.15.0-33-generic x86_64 bits: 64 Desktop: Gnome 3.28.3
           Distro: Ubuntu 18.04.1 LTS
Machine:   Device: desktop System: ASUS product: All Series serial: N/A
           Mobo: ASUSTeK model: B85-PRO GAMER v: Rev 1.xx serial: N/A
           BIOS: American Megatrends v: 2203 date: 04/27/2015
CPU:       Quad core Intel Core i7-4770 (-MT-MCP-) cache: 8192 KB
           clock speeds: max: 3900 MHz 1: 1161 MHz 2: 1317 MHz 3: 1482 MHz 4: 1366 MHz 5: 1213 MHz 6: 1489 MHz
           7: 1337 MHz 8: 1214 MHz
Graphics:  Card: NVIDIA GP106 [GeForce GTX 1060 6GB]
           Display Server: x11 (X.Org 1.19.6 ) driver: nvidia Resolution: 1680x1050@59.88hz, 1920x1080@60.00hz
           OpenGL: renderer: NV136 version: 4.3 Mesa 18.0.5
Audio:     Card-1 Intel 8 Series/C220 Series High Definition Audio Controller driver: snd_hda_intel
           Card-2 NVIDIA GP106 High Definition Audio Controller driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.15.0-33-generic
Network:   Card-1: Intel Ethernet Connection I217-V driver: e1000e
           IF: eno1 state: down mac: 08:62:66:4b:7b:7e
           Card-2: Realtek RTL8192CE PCIe Wireless Network Adapter driver: rtl8192ce
           IF: wlp2s0 state: down mac: 18:31:bf:57:a9:5f
Drives:    HDD Total Size: 3500.7GB (0.5% used)
           ID-1: /dev/sda model: ST3500418AS size: 500.1GB
           ID-2: /dev/sdb model: SAMSUNG_HD204UI size: 2000.4GB
           ID-3: /dev/sdc model: ST3500418AS size: 500.1GB
           ID-4: /dev/sdd model: Samsung_SSD_850 size: 500.1GB
Partition: ID-1: / size: 450G used: 7.8G (2%) fs: ext4 dev: /dev/sda2
           ID-2: swap-1 size: 8.59GB used: 0.00GB (0%) fs: swap dev: /dev/sda1
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 29.8C mobo: 27.8C gpu: 38.0
           Fan Speeds (in rpm): cpu: 0
Info:      Processes: 263 Uptime: 1:02 Memory: 1384.1/15978.6MB Client: Shell (bash) inxi: 2.3.56

```

```

01:00.0 VGA compatible controller: NVIDIA Corporation GP106 [GeForce GTX 1060 6GB] (rev a1)
    Subsystem: ASUSTeK Computer Inc. GP106 [GeForce GTX 1060 6GB]
    Kernel driver in use: nouveau

```

---

### Post by jhapurona on 2018-09-01
Bump

Still can't figure out what's going on.

---

### Post by sgian on 2018-09-02
As I understand it, you want to remove the NVIDIA 396 driver and reinstall the standard NVIDIA driver (390).  Is that correct?

You may need to remove the graphics ppa you added earlier, if you want to get a NVIDIA driver that is stable on Ubuntu.

When the screen is blank, if you press Ctrl-Alt-F3 do you get a terminal login?  If so, then you can go into your /etc/apt/sources.list through terminal and try to find the grapics ppa you added, then delete it. A command to do this with is
```
sudo nano /etc/apt/sources.list
```

What I usually have to do in this situation is to purge the NVIDIA drivers through terminal, and then reinstall Xorg and nouveau.  That gets me back into the GUI so I can try installing NVIDIA again from scratch.  It has been a while since I had to do this, but I think this should work...
```
sudo apt purge nvidia*
sudo apt install --reinstall xorg xserver-xorg-core
```

If that doesn't work, then let me know what happened.

---

### Post by jhapurona on 2018-09-02
> **sgian said:**
> As I understand it, you want to remove the NVIDIA  396 driver and reinstall the standard NVIDIA driver (390).  Is that  correct?

I need to have driver 396 installed to use Valves new  Proton/Steamplay feature (it's like Crossover but free). Everytime I  install it, I get stuck in the black screen and have to restart in  recovery mode and purge the Nvidia drivers, leaving me back on Nouveau. I did attempt to install Nvidia driver 390, just to see if the issue was exclusive to 396, but I still got the black screen on reboot with that one.

---

### Post by sgian on 2018-09-02
I think you are getting too complicated with the terminal commands.  nvidia-xconfig?  I have never used it, even when I have tried the graphics ppa.  Since you have the graphics ppa already added, you should be able to see the nvidia-396 show up in the "Software and Drivers" app for Ubuntu.  I would recommend using that.  Or the following should be all that is necessary once the ppa is in your sources.list...
```

sudo apt update
sudo apt install nvidia-driver-396

```
Then reboot.  You can also use the ubuntu-drivers command to check the driver name
```

sudo ubuntu-drivers list

```
That will tell you the full driver name that aptitude is expecting, and then do the sudo apt install ...

---

### Post by jhapurona on 2018-09-02
> **sgian said:**
> I think you are getting too complicated with the terminal commands.  nvidia-xconfig?  I have never used it, even when I have tried the graphics ppa.  Since you have the graphics ppa already added, you should be able to see the nvidia-396 show up in the "Software and Drivers" app for Ubuntu.  I would recommend using that.  Or the following should be all that is necessary once the ppa is in your sources.list...
```

sudo apt update
sudo apt install nvidia-driver-396

```
Then reboot.  You can also use the ubuntu-drivers command to check the driver name
```

sudo ubuntu-drivers list

```
That will tell you the full driver name that aptitude is expecting, and then do the sudo apt install ...

That was how I had tried it originally, I have also already tried the Software and Drivers app. I tried nvidia-xconfig at the suggestion of others as they said it may be a matter of the settings not correctly configuring on installation.

---

### Post by sgian on 2018-09-03
I suspect something else is going on.  I noticed that you have a quad core cpu, graphics card, and 4 hard drives.  As a wild guess, how big is your power supply?  Sometimes with a quad core cpu and external graphics cards, I run into a problem with not having a big enough power supply.  Based on [http://www.coolermaster.com/power-supply-calculator/](http://www.coolermaster.com/power-supply-calculator/) with a bunch of guesses on your setup, I'm not sure 650 W is even big enough for your setup, and that is with 3 hard drives and not knowing what else you have.

---

### Post by Bashing-om on 2018-09-03
jhapurona; Hummmmm ///

> 
Graphics:  Card: NVIDIA GP106 [GeForce GTX 1060 6GB]

And Nvidia recommends the 390 version driver for this card:
[https://www.nvidia.com/Download/index.aspx?lang=en-us](https://www.nvidia.com/Download/index.aspx?lang=en-us)
Have you tried the 390 version - purge existing and the xorg.conf file - ?

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by jhapurona on 2018-09-04
Yeah, I thought it best to try 390 after 396 failed so many times, just  to see if it was an issue with that specific driver. It's fine on the  open source drivers just not the proprietary ones, so I'm not sure if  the problem is with the drivers, my setup or both.

---

### Post by Bashing-om on 2018-09-04
jhapuronal Well ..

When all else fails, read the instructions - in this case the log files :)
```

cat /var/log/Xorg.0.log
cat /var/log/gpu-manager.log

```
see what the system thinks.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by jhapurona on 2018-09-06
I did it with the Nvidia drivers installed (from recovery) and purged (from the desktop). Both Xorg logs were empty and the gpu logs were identical:

```
log_file: /var/log/gpu-manager.log
last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
can't access /run/u-d-c-nvidia-was-loaded file
can't access /opt/amdgpu-pro/bin/amdgpu-pro-px
Looking for nvidia modules in /lib/modules/4.15.0-33-generic/updates/dkms
Looking for amdgpu modules in /lib/modules/4.15.0-33-generic/updates/dkms
Is nvidia loaded? no
Was nvidia unloaded? no
Is nvidia blacklisted? no
Is intel loaded? no
Is radeon loaded? no
Is radeon blacklisted? no
Is amdgpu loaded? no
Is amdgpu blacklisted? no
Is amdgpu versioned? no
Is amdgpu pro stack? no
Is nouveau loaded? yes
Is nouveau blacklisted? no
Is nvidia kernel module available? no
Is amdgpu kernel module available? no
Vendor/Device Id: 10de:1c03
BusID "PCI:1@0:0:0"
Is boot vga? yes
Skipping "/dev/dri/card0", driven by "nouveau"
Skipping "/dev/dri/card0", driven by "nouveau"
Found "/dev/dri/card0", driven by "nouveau"
output 0:
    card0-DVI-D-1
output 1:
    card0-DP-2
output 2:
    card0-HDMI-A-1
Number of connected outputs for /dev/dri/card0: 3
Skipping "/dev/dri/card0", driven by "nouveau"
Does it require offloading? no
last cards number = 1
Has amd? no
Has intel? no
Has nvidia? yes
How many cards? 1
Has the system changed? No
Single card detected
Nothing to do
```

---

### Post by Bashing-om on 2018-09-06
jhapurona; Well,

As things stand now you are running on the nouveau driver:
> 
can't access /run/u-d-c-nvidia-was-loaded file
Is nvidia loaded? no
Was nvidia unloaded? no
Is nouveau loaded? yes
Is nvidia kernel module available? no


3 monitors connected ? What results when only one monitor is connected ? We try and reduce to simplest terms .

Is there and issue activating a console interface at the login screen ( ctl+alt+F2) ?
Is the system clean presently of the Nvidia driver ?
```

lsmod | grep nvidia
dpkg -l | grep -i nvidia

```

[INDENT][INDENT]sometimes I wonder
[INDENT][INDENT]and look to find out[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jhapurona on 2018-09-06
> **Bashing-om said:**
> 
As things stand now you are running on the nouveau driver
3 monitors connected ? What results when only one monitor is connected ? We try and reduce to simplest terms .
Is there and issue activating a console interface at the login screen ( ctl+alt+F2) ?


After the installation, when I boot into recovery mode it also claims I'm running the nouveau drivers. Is that due to the recovery mode, or could it be that something isn't configuring correctly?
With 1 monitor it runs the same as triple monitors. Black screen when the Nvidia driver is installed, single monitor output in recovery/desktop after the purge.
TTY2 loads and logs in fine when I am in the desktop. But after installing the drivers, I don't even get to see the login screen and no input works. Not even the caps and num lock lights on my keyboard.

```

$ lsmod | grep nvidia
$ dpkg -l | grep -i nvidia
rc  libnvidia-compute-396:i386                 396.54-0ubuntu0~gpu18.04.1          i386         NVIDIA libcompute package

```

---

### Post by Bashing-om on 2018-09-06
jhapurona; Welp -

So much for the thought that there might be remnants of the nvidia driver .
config files at all ?- should not have a need of them:
Remind me again what release we are working with as the the config directory has changed in later editions.

Show us:
```

ls -al /usr/share/X11/xorg.conf.d/*.conf
ls -al /etc/X11/xorg.conf
tail -v -n +1 /etc/apt/sources.list.d/*

```


Scratch our heads and try to install again from terminal. see what errors the system reports.

[INDENT][INDENT]all I know to do is try try again .
[/INDENT][/INDENT]

---

### Post by jhapurona on 2018-09-18
> **Bashing-om said:**
> jhapurona; Welp -

So much for the thought that there might be remnants of the nvidia driver .
config files at all ?- should not have a need of them:
Remind me again what release we are working with as the the config directory has changed in later editions.

Show us:
```

ls -al /usr/share/X11/xorg.conf.d/*.conf
ls -al /etc/X11/xorg.conf
tail -v -n +1 /etc/apt/sources.list.d/*

```


Scratch our heads and try to install again from terminal. see what errors the system reports.
[INDENT][INDENT]all I know to do is try try again .
[/INDENT]
[/INDENT]


Sorry for the absence, busy time here.

```
$  ls -al /usr/share/X11/xorg.conf.d/*.conf
-rw-r--r-- 1 root root   92 Mar 20 22:02 /usr/share/X11/xorg.conf.d/10-amdgpu.conf
-rw-r--r-- 1 root root 1350 Apr 14 01:31 /usr/share/X11/xorg.conf.d/10-quirks.conf
-rw-r--r-- 1 root root   92 Mar 20 22:17 /usr/share/X11/xorg.conf.d/10-radeon.conf
-rw-r--r-- 1 root root  945 Apr 11 17:50 /usr/share/X11/xorg.conf.d/40-libinput.conf
-rw-r--r-- 1 root root 3025 Apr  3 17:39 /usr/share/X11/xorg.conf.d/70-wacom.conf

$  ls -al /etc/X11/xorg.conf
ls: cannot access '/etc/X11/xorg.conf': No such file or directory

$  tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/google-chrome.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main

==> /etc/apt/sources.list.d/google-chrome.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main

==> /etc/apt/sources.list.d/graphics-drivers-ubuntu-ppa-bionic.list <==
deb http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu bionic main
# deb-src http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu bionic main

==> /etc/apt/sources.list.d/graphics-drivers-ubuntu-ppa-bionic.list.save <==
deb http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu bionic main
# deb-src http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu bionic main

==> /etc/apt/sources.list.d/nilarimogard-ubuntu-webupd8-bionic.list <==
deb http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu bionic main
# deb-src http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu bionic main

==> /etc/apt/sources.list.d/waterfox.list <==
deb https://dl.bintray.com/hawkeye116477/waterfox-deb release main

==> /etc/apt/sources.list.d/waterfox.list.save <==
deb https://dl.bintray.com/hawkeye116477/waterfox-deb release main

```

Now I've remembered some EXTREMELY important information I'd completely forgotten until I went to update my Windows Nvidia driver. On my Windows drive I am running driver 388.13 (the closest Linux equivalent is 384 and it doesn't work for me). **No other driver works for me**, literally. If I attempt to use any other driver version it will black screen once it gets to the login screen. I used that one after Grey Bear on the Nvidia forums (very prolific poster there) told another user with the same issue to use that specific driver and never upgrade ever. I wonder if this is an issue of the Mobo and GPU not playing nice together? 
Do you think my problem on Linux is caused by the same issue? If so how could I possible fix it?

---

### Post by Bashing-om on 2018-09-18
jhapurona; Yuk //

Got me ... Those questions I can not address.
But, something stinks !
> 
sysop@x1810:~$ ls -al /usr/share/X11/xorg.conf.d/
total 40
drwxr-xr-x 2 root root 4096 Sep 18 11:34 .
drwxr-xr-x 5 root root 4096 Aug 28 19:05 ..
-rw-r--r-- 1 root root   92 May 23 01:55 10-amdgpu.conf
-rw-r--r-- 1 root root  206 Aug 28 01:49 10-nvidia.conf
-rw-r--r-- 1 root root 1350 Sep  5 06:13 10-quirks.conf
-rw-r--r-- 1 root root   92 Aug 20 02:19 10-radeon.conf
-rw-r--r-- 1 root root  945 Aug 17 07:04 40-libinput.conf
-rw-r--r-- 1 root root  590 Aug 24 06:29 51-synaptics-quirks.conf
-rw-r--r-- 1 root root 1751 Aug 24 06:29 70-synaptics.conf
-rw-r--r-- 1 root root 3025 Apr  3 02:39 70-wacom.conf
sysop@x1810:~$ 

why do you not have the 10-nvidia.conf file ?

what shows now for:
```

lsmod | grep nvidia
dpkg -l | grep -i nvidia
cat /var/log/gpu-manager.log
sudo dkms status
cat /proc/cmdline

```

Got to be a reason that the Nvidia driver does not load.

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by jhapurona on 2018-09-19
Oh I'd purged everything to do with Nvidia at the time.

The good news is I've fixed the issue and it happens to be exactly what was causing the problems on windows as well. My 1060 Strix is a factory overclocked version, so as a last ditch attempt (after being told by Grey Bear from the Nvidia forums to RMA the card) I thought to flash the VBIOS to the non factory overclock version. Specifically from VBIOS 86.06.0E.00.0A to 86.06.0E.00.08.
The bad news is the weird issue I was getting on Windows with any Nvidia driver installed...is now happening with the Ubuntu proprietary drivers. My broken monitor (water damage) MUST be plugged in, or the PC will freeze, requiring hard reboot. If I disconnect/disable it in display settings, it will crash. It has to be detectable by the drivers for some reason, which sucks since I'd love to turf it given that it's broken. 

On a semi-relatable note, GRUB shows up on that monitor making choosing an option a literal game of memory. Any way to change which monitor displays GRUB?

---

### Post by Bashing-om on 2018-09-20
jhapurona; Uh huh !


Nvidia is coming out with updated and new drivers, maybe these will fill the ticket ? 
> 
 GRUB shows up on that monitor making choosing an option a literal game of memory. Any way to change which monitor displays GRUB?


Nope, as much as I have explored grub, this is a new one on me and I have no idea how grub parses for the display. As this matter is concluded how about marking this thread solved and open a new thread on the grub issue :
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]and we do something different
[/INDENT][/INDENT]

---

### Post by jhapurona on 2018-09-23
I actually managed to fix the issue with the broken monitor by moving my GPU to a different PCI-E port. Now my Ubuntu drive is running wonderfully. Thank you for all of your help.

---

### Post by Bashing-om on 2018-09-23
jhapurona; :)

You do good work .

Just goes to prove, when it is not the software -
[INDENT][INDENT]got to be in the hardware
[/INDENT][/INDENT]

---

### Post by tad30armenta on 2018-12-17
Hey guys, I have a similar problem here.


Hardware: 


```
Asus ROG Strix Z370-H Gaming Mother Board
Intel i78700k
Asus DirectCU 2 GTX 660


Samsung 32'' Tv as main display conected via hdmi
Dell 20'' as a second display connected via dvi port

```

Software:
```
Ubuntu 18.04
Kernel  4.15.0-42-generic
Nvidia drivers 415



```

All was working flawlessly, until i added a new ssd;  after a couple of reboots,  it starts to blank screening my second monitor:

When the PC boots, video is shown on dvi monitor as usual, but once ubuntu is loaded, dvi monitor goes to blank screen, and video is shown on hdmi only.
I've already tried to completely remove all nvidia stuff, even tried several conbinations of kernel and nvidia driver version, both dkms an non dkms, PPA and "dot run" files from nvidia drivers page,  change PCIE port, reset mother board bios to defaults, flashed the gtx card with the stock firmware, just to see if by any chance it could help and  I even tried with another card(gtx 750ti), with the exactly same result.  :/


windows and ubuntu with noveau driver,  doesn't have any problem showing video on both displays at same time.

```
log_file: /var/log/gpu-manager.loglast_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
can't access /opt/amdgpu-pro/bin/amdgpu-pro-px
Looking for nvidia modules in /lib/modules/4.15.0-42-generic/updates/dkms
Found nvidia module: nvidia-uvm.ko
Looking for amdgpu modules in /lib/modules/4.15.0-42-generic/updates/dkms
Is nvidia loaded? yes
Was nvidia unloaded? no
Is nvidia blacklisted? no
Is intel loaded? no
Is radeon loaded? no
Is radeon blacklisted? no
Is amdgpu loaded? no
Is amdgpu blacklisted? no
Is amdgpu versioned? no
Is amdgpu pro stack? no
Is nouveau loaded? no
Is nouveau blacklisted? yes
Is nvidia kernel module available? yes
Is amdgpu kernel module available? no
Vendor/Device Id: 10de:11c0
BusID "PCI:2@0:0:0"
Is boot vga? yes
Skipping "/dev/dri/card0", driven by "nvidia-drm"
Skipping "/dev/dri/card0", driven by "nvidia-drm"
Skipping "/dev/dri/card0", driven by "nvidia-drm"
Skipping "/dev/dri/card0", driven by "nvidia-drm"
Does it require offloading? no
last cards number = 1
Has amd? no
Has intel? no
Has nvidia? yes
How many cards? 1
Has the system changed? No
Single card detected
Nothing to do

```


any ideas??

---

### Post by hgkrug1 on 2019-05-23
The above solution did not work for me. I found a solution for this Nvidia driver issue (on ubuntu 18 and 19). See instructions at the top at [https://ubuntuforums.org/showthread....nvidia+drivers]("https://ubuntuforums.org/showthread.php?t=2419319&highlight=nvidia+drivers"), it worked for me!

Unfortunately, I could not reproduce the installation on a freshly installed system.

---

### Post by hgkrug1 on 2019-05-23
I found a solution for this Nvidia driver issue (on ubuntu 18 and 19). See instructions at the top at [https://ubuntuforums.org/showthread....nvidia+drivers]("https://ubuntuforums.org/showthread.php?t=2419319&highlight=nvidia+drivers"), it worked for me!

However, I found a suitable fix at entry #19 of [https://bugs.launchpad.net/gdm/+bug/1798790](https://bugs.launchpad.net/gdm/+bug/1798790)

Try this as a workaround: edit /etc/gdm3/custom.conf 
and uncomment the line: 
#WaylandEnable=false

---

### Post by fely35 on 2019-06-25
Ubuntu 19.04, nvidia-418: The solution for me was to set the primary display in the PC BIOS to Auto, instead of Nvidia. The bios mentioned that if NVIDIA is selected, the Intel GPU is also active. If you don't have that bios option: Nvidia Optimus: [https://wiki.archlinux.org/index.php/NVIDIA_Optimus#Display_Managers](https://wiki.archlinux.org/index.php/NVIDIA_Optimus#Display_Managers)

---

