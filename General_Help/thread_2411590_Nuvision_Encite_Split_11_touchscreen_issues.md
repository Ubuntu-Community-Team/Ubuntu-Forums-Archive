---
title: "Nuvision Encite Split 11 touchscreen issues"
date: 2019-02-01
forum: General Help
---

### Post by William_Klee on 2019-02-01
Sorry, but this is going to ramble a bit. I've been meaning to ask this for a couple weeks, but just haven't had the time, and it's getting late.

I bought a Nuvision Encite Split 11 tablet, with the intention of putting linux on it and using it as an e-reader. It came with Win10, and both auto-rotation and touchscreen worked. I didn't anticipate any major problems, since I've installed linux (usually Lubuntu with some Gnome & KDE packages on top) on at least 3 or 4 touch-screen windows laptops without issue. Granted, auto-rotate was iffy, at best, but I can always use xrandr to rotate the display as I like. The touchscreen, though, always worked out of the box.

On this thing, though, not so much. I've had a couple of issues.

First, and most obvious, the display. In Lubuntu, the display is oriented correctly, but in Ubuntu, it's inverted. Again, though, that's easy enough to fix, and I'll eventually add a small script to the auto-start to rotate it to normal.

Secondly, the touchscreen does not work, at all. The touchscreen is a Silead GSL1680, IIRC, and a bit of google-fu tells me the silead drivers were folded into the linux kernel in 2016. Further, modinfo silead shows me that it's there (/lib/modules/4.15.0-45-generic/kernel/drivers/input/touchscreen/silead.ko, to be exact).

So, the question is, how do I get the touchscreen to work?

The machine itself looks almost exactly like a Microsoft Surface Pro 4 (I think it was - I compared my Nuvision to a Surface Pro in Best Buy a couple months ago, and they looked virtually identical).

Some specs:
Made by Nuvision, model name is Encite Split 11, model number is NES11-C5432SSA
CPU: Intel Celeron N3350 @ 1.1 GHz
RAM: 4 GB
Display: 1920x1080
Internal Storage: 32 GB emmc
External Storage: microSD, up to 256 GB
Ports: 1x USB-C, 1x power, 1x keyboard connector

It's a nice enough little machine, for the price, and comes with USB-C to HDMI and USB-C to USB-A adapters.

---

### Post by tsg2513 on 2019-02-01
> **William_Klee said:**
> Sorry, but this is going to ramble a bit. I've been meaning to ask this for a couple weeks, but just haven't had the time, and it's getting late.

I bought a Nuvision Encite Split 11 tablet, with the intention of putting linux on it and using it as an e-reader. It came with Win10, and both auto-rotation and touchscreen worked. I didn't anticipate any major problems, since I've installed linux (usually Lubuntu with some Gnome & KDE packages on top) on at least 3 or 4 touch-screen windows laptops without issue. Granted, auto-rotate was iffy, at best, but I can always use xrandr to rotate the display as I like. The touchscreen, though, always worked out of the box.

On this thing, though, not so much. I've had a couple of issues.

First, and most obvious, the display. In Lubuntu, the display is oriented correctly, but in Ubuntu, it's inverted. Again, though, that's easy enough to fix, and I'll eventually add a small script to the auto-start to rotate it to normal.

Secondly, the touchscreen does not work, at all. The touchscreen is a Silead GSL1680, IIRC, and a bit of google-fu tells me the silead drivers were folded into the linux kernel in 2016. Further, modinfo silead shows me that it's there (/lib/modules/4.15.0-45-generic/kernel/drivers/input/touchscreen/silead.ko, to be exact).

So, the question is, how do I get the touchscreen to work?

The machine itself looks almost exactly like a Microsoft Surface Pro 4 (I think it was - I compared my Nuvision to a Surface Pro in Best Buy a couple months ago, and they looked virtually identical).

Some specs:
Made by Nuvision, model name is Encite Split 11, model number is NES11-C5432SSA
CPU: Intel Celeron N3350 @ 1.1 GHz
RAM: 4 GB
Display: 1920x1080
Internal Storage: 32 GB emmc
External Storage: microSD, up to 256 GB
Ports: 1x USB-C, 1x power, 1x keyboard connector

It's a nice enough little machine, for the price, and comes with USB-C to HDMI and USB-C to USB-A adapters.

I am glad to see this post as I have been struggling with the same exact issue on the same exact device. Perhaps there is someone out there that knows how to resolve this. I have also tried so many distros that I can't even recall but have had the same results each time...no touchscreen on any of them and an inverted screen on some. I even went as far as doing a clean Windows 10 install and still...no touchscreen! I also downloaded the Driver package from NuVision's site and unzipped the package to find the Touchscreen folder is empty! I emailed their tech support but never got a response. So, I packed it all up and threw it in a closet where it will remain until a fix surfaces. It is a shame because as you said, the hardware looks and feels really nice.

---

### Post by William_Klee on 2019-02-01
Exactly what I've gone through. My brother works 2nd-tier tech support for one of the major computer manufacturers, and said he thinks he can get working (in Windows) if I can't. If I give up on it, and he can get it working, I'll try to post a detailed step by step. Until then, I'd really like to get the touchscreen working in linux.

---

### Post by danielneon on 2019-02-25
> **William_Klee said:**
> Sorry, but this is going to ramble a bit. I've been meaning to ask this for a couple weeks, but just haven't had the time, and it's getting late.

I bought a Nuvision Encite Split 11 tablet, with the intention of putting linux on it and using it as an e-reader. It came with Win10, and both auto-rotation and touchscreen worked. I didn't anticipate any major problems, since I've installed linux (usually Lubuntu with some Gnome & KDE packages on top) on at least 3 or 4 touch-screen windows laptops without issue. Granted, auto-rotate was iffy, at best, but I can always use xrandr to rotate the display as I like. The touchscreen, though, always worked out of the box.

On this thing, though, not so much. I've had a couple of issues.

First, and most obvious, the display. In Lubuntu, the display is oriented correctly, but in Ubuntu, it's inverted. Again, though, that's easy enough to fix, and I'll eventually add a small script to the auto-start to rotate it to normal.

Secondly, the touchscreen does not work, at all. The touchscreen is a Silead GSL1680, IIRC, and a bit of google-fu tells me the silead drivers were folded into the linux kernel in 2016. Further, modinfo silead shows me that it's there (/lib/modules/4.15.0-45-generic/kernel/drivers/input/touchscreen/silead.ko, to be exact).

So, the question is, how do I get the touchscreen to work?

The machine itself looks almost exactly like a Microsoft Surface Pro 4 (I think it was - I compared my Nuvision to a Surface Pro in Best Buy a couple months ago, and they looked virtually identical).

Some specs:
Made by Nuvision, model name is Encite Split 11, model number is NES11-C5432SSA
CPU: Intel Celeron N3350 @ 1.1 GHz
RAM: 4 GB
Display: 1920x1080
Internal Storage: 32 GB emmc
External Storage: microSD, up to 256 GB
Ports: 1x USB-C, 1x power, 1x keyboard connector

It's a nice enough little machine, for the price, and comes with USB-C to HDMI and USB-C to USB-A adapters.

I'm having the same trouble with a different tablet (same silead chip); I was able to fix the auto-rotate in Gnome though. iio-sensor-proxy ([https://github.com/hadess/iio-sensor-proxy](https://github.com/hadess/iio-sensor-proxy)) handles accelerometer orientation in Gnome. I was able to add two lines to 60-sensor.hwdb ([https://github.com/systemd/systemd/blob/master/hwdb/60-sensor.hwdb](https://github.com/systemd/systemd/blob/master/hwdb/60-sensor.hwdb)) to flip the x-axis in my case. Here is a thread with more details: [https://unix.stackexchange.com/questions/410826/change-iio-sensors-data-via-custom-accel-mount-matrix](https://unix.stackexchange.com/questions/410826/change-iio-sensors-data-via-custom-accel-mount-matrix) .

---

### Post by tsg2513 on 2019-03-04
I noticed that NuVision recently added the Touch Screen Driver to the Drivers in their download section of their website and I have successfully restored Windows 10 with no problems.

---

### Post by kizimo on 2019-08-24
[https://hackaday.io/project/83212-liberating-a-50-windows-tablet/log/116445-testing-the-touchscreen]("https://hackaday.io/project/83212-liberating-a-50-windows-tablet/log/116445-testing-the-touchscreen") worked for me....still need to calibrate it tho...

---

### Post by incognitio222 on 2020-03-28
> **tsg2513 said:**
> I noticed that NuVision recently added the Touch Screen Driver to the Drivers in their download section of their website and I have successfully restored Windows 10 with no problems.


Hi, so I recently obtained the Nuvision Split 11 and learned Nuvision does not properly support their devices after I had already formatted and installed windows 10 version 1909. If you visit NuVision's download page now, the drivers download for the Split 11 and other device are dead. I did did download the OS restore (Six hours to download if you do not pay the hosting site for continuous fast downloading :(), NuVison provided was not a bootable version of it so I had to make one. I was able to restore the Spit 11, but the restore they provided has errors. Once I had windows and the drivers installed from the restore I ran a Powershell command to backup all of the driver "Export-WindowsDriver -Online -Destination D:\Drivers" - You have to run Powershell in administrators mode. Once I had the drivers backed up I created a windows 10 installation of Version 1909 the latest release as of 3/15/2020 when I made the Windows 10 iso. I integrated the drives so they would work during the install, and would install automatically when windows 10 installed. Additionally; all updates as of 3/15/2020 were slipstreamed into the distribution using NTLite ([https://www.ntlite.com/](https://www.ntlite.com/)). I sent the links to the extracted drivers and the Windows 10 distribution to NuVision Support, but they still did not download my provided drivers and Windows 10 iso to make available to everyone.

If you need to install your drivers for windows 10, or you would like to do a fresh install of Windows 10 Version 1909, you are welcome to visit my Google Drive and download them. I ask you please help me help others with the NuVision Split 11 by providing a link to this page or my google driver for other to download since it seams NuVision does not really care to. I have also provided instructions on how to use the iso if you have never done it before.

With the exception of Split 11 Drivers and Windows 10 Updates integrated, the windows 10 ISO is exactly as Microsoft Provides it. You will not need a CD-Key as it is
integrated by NuVision in the bios and windows will just load it automatically from there. other than that it is a normal Windows 10 installation.

[https://drive.google.com/open?id=1I7N4FZuO1JhxQ-jTe8rHktIQQXi0Gb-o](https://drive.google.com/open?id=1I7N4FZuO1JhxQ-jTe8rHktIQQXi0Gb-o)


I already did the below for the "NuVision_(Split11)_Windows10 _(Version1909)_English_x64.iso" I only provided it if you ever need it and did not l know about it.


If you would like to ever add your drivers to the install process for a Windows 10 installation and know about DISM, you can integrate your windows drivers into the boot.wim for the Windows PE installer. To add the drivers to the final installation, you must use NTLite. to use DISM, you need to install Microsoft's ADK Setup utility first.


To integrate your driver's for the Windows PE environment:
1.) Install Microsoft's ADK Setup Utility first. "[https://docs.microsoft.com/en-us/windows-hardware/get-started/adk-install](https://docs.microsoft.com/en-us/windows-hardware/get-started/adk-install)"
2.) Create a folder not in you C root, but another drive if you have one.
3.) Copy the boot.wim from the installation iso to your new folder, you can find it in \sources\boot.wim 
3a.) you can use WinRaR to extract the iso to a folder, or just copy it form the open iso in PowerISO
4.) Make a batch file in your directory you created and copied the boot.wim to and paste below code.
4a.) You can open notepad paste the below code into it, select the option all files, not txt and add .bat to the end. and save
4b.) on this line "DISM /mount-wim /wimfile:%WimFile% /index:1 /mountdir:%MountDir%" index:1, you need to set this to your index, most of the time it is 1
4c.) This command in administrator mode will list available indexes "DISM /Get-ImageInfo /imagefile:D:\"your boot.wim directory"\boot.wim"
5.) if you open your folder with your batch file and boot.wim, just right click on the batch file and select run as administrator.
the batch will do everything for you.



DISM Batch script needs to be run as administrator:

@echo off


SET WimFile="%~dp0boot.wim"
SET MountDir="%~dp0MNT"
SET DriverDir="%~dp0Drivers"


ECHO Boot.wim File:
ECHO %WimFile%


ECHO Making Mount Directory "MNT":
IF NOT EXIST %MountDir% mkdir %MountDir%
ECHO %MountDir%


ECHO Driver Directory:
ECHO %DriverDir%


DISM /get-wiminfo /wimfile:%WimFile%


DISM /mount-wim /wimfile:%WimFile% /index:1 /mountdir:%MountDir%


DISM /Image:%MountDir% /Add-Driver /Driver:%DriverDir% /recurse


DISM /image:%MountDir% /get-drivers


DISM /unmount-wim /mountdir:%MountDir% /commit


ECHO Removing Mount Directory
rmdir %MountDir%


PAUSE




Exit


I am hopeful you can find this if you need it...

---

### Post by coffeecat on 2020-03-28
@incognitio222, this is an Ubuntu, not Windows forum. The hint is in the name. The OP was requesting help for an issue when they had installed Lubuntu on this device.

Old thread closed to prevent further off-topic necromancy.

---

