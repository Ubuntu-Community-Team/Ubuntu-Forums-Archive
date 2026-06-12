---
title: "Any ideas as to why I'm seeing this?"
date: 2012-10-27
forum: General Help
---

### Post by DNSBubba on 2012-10-27
[(This)]("http://imgur.com/hxDgz") is in 12.10 64 bit, using a Geforce GTX 560 Ti.

The corruption pop's up from time to time in Firefox as well. Granted, I'm not entirely sure that the proper drivers are installed, given how that process has changed, although I've confirmed that graphic acceleration is enabled, using glxinfo | grep rendering.

Honestly, I'm not sure of the drivers because I'm seeing a ton of tearing and lagging when moving windows. Everything was working well before 12.10. Any ideas would be greatly appreciated.

---

### Post by oldfred on 2012-10-27
There are a lot of issues with proprietary drivers in 12.10. They left off the headers so dpkg does not install the proprietary drivers correctly.

Run this first, just to make sure you have headers.

sudo apt-get install linux-headers-generic

then go into drivers to see what nVidia driver you have install or if you do.

right click to change desktop background
When the window appear, click all settings, now you see the system settings window.
Next, click on Software source, go in the additional drivers tab.
Select the 3 rd option, using video driver for the nvidia

You should see three different options for nVidia drivers.
nvidia-current
nvidia-current-updates
nvidia-experimental-304

I think with my older nVidia 9600GT, I am running current-updates with out any major issues.

---

### Post by DNSBubba on 2012-10-27
Thanks for your response. Following your instructions, the headers are installed. However, when I go to Additional Drivers in Software Sources, it's blank.

---

### Post by oldfred on 2012-10-27
You can from command line add drivers:

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install linux-headers-generic
# only reason to purge is there are several versions, if you know you have different nVidia use that: 
sudp apt-get purge nvidia*
sudo apt-get install nvidia-current
sudo dpkg-reconfigure nvidia-current

I think I used command line originally for nvidia-current and it seemed to be working even after a reboot. But next day it did not. So I went back and installed nvidia-current-updates and that has worked after several reboots. But I am in 12.04 right now so I have not confirmed today that it works. :)

---

### Post by DNSBubba on 2012-10-27
Thanks oldfred, but following your instructions, while it does seem to install the drivers, seems to limit me to a max resolution of 1024x768.

---

### Post by oldfred on 2012-10-27
I still have gnome-panel so I use the old menus. But in System Tools, Administration, I have Nvidia X-Server Settings. I do not remember now if I also installed that or it was part of the standard install. Does that find your monitor correctly?

Found that is installed as part of nvidia-settings.
So I have nvidia-settings-updates

---

### Post by DNSBubba on 2012-10-27
It did find the monitor, and identified the card.

---

### Post by oldfred on 2012-10-27
Then does it offer the correct resolution?

---

### Post by Rebelli0us on 2012-10-27
Linux Mint includes NVIDIA driver, so you don't need to mess around. Just to test, install Mint on a USB flash drive to see if you're happy with the video driver... works fine with my GTX 550 Ti

---

### Post by DNSBubba on 2012-10-27
Will do. Thanks for the advice.

---

### Post by DNSBubba on 2012-10-27
> **Rebelli0us said:**
> Linux Mint includes NVIDIA driver, so you don't need to mess around. Just to test, install Mint on a USB flash drive to see if you're happy with the video driver... works fine with my GTX 550 Ti

WOW! I removed my Ubuntu install, and installed Mint. I know it's derived from Ubuntu, but what a different experience. And, yes, the driver issue is gone. It installed without a hitch. Big time thanks!

---

### Post by Rebelli0us on 2012-10-28
> **DNSBubba said:**
> WOW! I removed my Ubuntu install, and installed Mint. I know it's derived from Ubuntu, but what a different experience. And, yes, the driver issue is gone. It installed without a hitch. Big time thanks!

You're welcome. If by any chance you're using the latest z77 chipset you'll experience random crashes with Mint. In that case you'll need to [install updated kernel]("http://www.upubuntu.com/2012/05/how-to-install-linux-kernel-336-via-ppa.html"). 

OTOH, Ubuntu 12.10 comes with the latest kernel, so you can run Ubunter but [install Mint MATE desktop]("http://wiki.mate-desktop.org/download?&#ubuntu_quantal_quetzal_1210_repository") **instead** of Unity... and then download & add the proprietary drivers from nVidia.

---

