---
title: "FirePro 3D V7800 dual monitor"
date: 2013-01-18
forum: General Help
---

### Post by ROVguy on 2013-01-18
Hello All,

I have been trying to move from Windows to Ubuntu but I have a monitor problem.

I am running a FirePro 3D V7800 graphics card on a ASUS P6T6 WS Revolution mother board. When I try to run dual monitor the system freezes up and I need to manually shut down. 

I have tried installing the drivers from the additional drivers page with not success. I have also looked at similar formus that could have drivers that would work and had no luck there either. Lastly I downloaded drivers from [http://support.amd.com/us/gpudownload/fire/Pages/fire_linux.aspx](http://support.amd.com/us/gpudownload/fire/Pages/fire_linux.aspx) and tried to install the driver through terminal from the download page. This to did not work. 

On the last one I'm not sure if I'm doing things wrong as I am not familiar with terminal.
I unzipped the folder then through terminal I went into it and ran the command "sudo apt-get install amd-driver-installer-9.003.3-x86.x86_64.run"

I got this back 
"E: Unable to locate amd-driver-installer-9.003.3-x86.x86_64.run"
"E: Couldn't find any package by regex 'amd-driver-installer-9.003.3-x86.x86_64.run' "

Could I get help installing this downloaded driver or steps on how to download and install proper drivers from the net?

Thanks for any and all help

---

### Post by gifford on 2013-01-18
I'm not able to understand what drivers you are now using? I assume you are not using the proprietary AMD drivers and that those are the ones you are having trouble in downloading and installing.

AMD has released a new Catalyst Display Driver and instructions on installation are here: 
[http://www.upubuntu.com/2013/01/amd-catalyst-display-driver-131-adds.html](http://www.upubuntu.com/2013/01/amd-catalyst-display-driver-131-adds.html)

Also, what version of Ubuntu are you using?

You need to change to the downloads directory to see the file that you downloaded and enter your commands from that directory.
Enter CD Downloads from your terminal.

---

### Post by ROVguy on 2013-01-18
Hello gifford,

I figured I'd miss something. Its Ubuntu 12.04.
The drivers that I am using are what gets installed during the installation of the operating system. I do a update after the install.(sudo apt-get update)

I have tried AMDs previous release and now this 13.1 release even though  "Workstation Graphics" is not on the list of supported products.  During the install  after the 3rd line typed I get the error
E: Unable to locate package fglrx-installer

Also, when I was trying to install from the download folder I did entered the Download folder and the folder which I downloaded before trying the install. 
cd Downloads/fglrx-9.003.3

One last thing. The freezing up doesn't happen every time but it does happen frequently especially while in Display system settings when I'm trying to configure the dual monitor.

---

### Post by gifford on 2013-01-18
The drivers you get during the install are open source and not proprietary. You have to go to system settings and under hardware, additional drivers. It will scan for your card and suggest the appropriate proprietary driver. Let the system do the install for you.

Hope this helps.

---

### Post by ROVguy on 2013-01-21
Going to system settings and installing AMD drivers is the first thing I tried. Occasionally I was able to install the drivers but when I tried the second install (the update ) the thing would error and not install and it would also get rid of the AMD drivers that I installed. When I only did the first driver I would have the same results of freezing up.
  The last thing that happened was that when I rebooted the systems I was sent to the terminal page F1 where I was asked to log in, the desktop  never fired up. I did try the startx which didn't do anything. I also tried installing desktop but was told it already exists. I also tried starting desktop on other terminal pages F1-F6.

Since not being able to get to the desktop I downloaded the newest OS 12.10 64 and had slight better results with less glitches than 12.04. The only issue that I have had so far with the new OS is that after reboot of the OS and after logging in I have had a blank background image without any buttons. All that is possible is a manually shut down.

---

