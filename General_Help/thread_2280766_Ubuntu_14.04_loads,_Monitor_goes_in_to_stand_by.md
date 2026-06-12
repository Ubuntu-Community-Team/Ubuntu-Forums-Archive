---
title: "Ubuntu 14.04 loads, Monitor goes in to stand by"
date: 2015-06-02
forum: General Help
---

### Post by John_Creane on 2015-06-02
When I power up Ubuntu 14.04 on my desktop it gives me the bios & boot options & then the screen goes blank and I get a message that my monitor is not receiving a signal from the computer & it slips in to stand by before I get to the screen to decrypt my Hard Drive or the Log on screen.  
 

 I can get the screen up if I unhook & reconnect the DVI cable that connects to my Nvidea Gf108 GeForce GT 440 video card to my monitor but it is a real pain. This monitor doesn't have an HDMI port to connect to. However when I unplug the monitor & connect to my tv using HDMI it loads without any issues.  
 

 What is causing my problem here?  
 

 I have gone to additional drivers for the Graphics card & set it to use the open source driver,  
 I have run $ sudo apt-get update
 $
sudo apt-get upgrade 

 & also ran  
 apt-cache policy
linux-image-generic 
apt-cache
policy linux-firmware sudo apt-get dist-upgrade should work.  
 &
 apt-get
install linux-generic  None of these have fixed my issue. 
I am able to connect to Windows 8.1 with this monitor without any issues so I don't think it is a hardware issue. 

Any help would be appreciated


***DuckHook fix below solved my problem although I had to reinstall a proprietary Nvidea driver in the additional drivers after the reboot.

---

### Post by DuckHook on 2015-06-02
You are probably running into an ACPI bug where your system tests for ACPI compatibility at boot, but the testing signal is interpreted by your monitor as a signal to turn the monitor off. The workaround is to turn off ACPI support, which is not really much of a loss, since the Desktop Environment of most distros have alternate ways of blanking screen or putting the monitor to sleep, etc.

To turn off ACPI at boot:```
sudo nano /etc/default/grub
```add "acpi=off" to the appropriate line so that it looks like:```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off"
```Write changes to file and exit. Then:```
sudo update-grub
```Reboot and see if this solves the problem. If it does, please mark this thread "solved". If not, post back to this thread and we can look at other possible issues.

---

