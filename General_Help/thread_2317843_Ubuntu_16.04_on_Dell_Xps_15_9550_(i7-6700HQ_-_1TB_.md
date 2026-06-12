---
title: "Ubuntu 16.04 on Dell Xps 15 9550 (i7-6700HQ - 1TB SSD - UHD 4k touch)"
date: 2016-03-20
forum: General Help
---

### Post by Javier_Macias-Guar on 2016-03-20
Hi all,

  Thanks to the [splendid work detailing how to run Ubuntu 15.10 on the Dell XPS 15 9550]("http://ubuntuforums.org/showthread.php?t=2301071")  (started by @jchedstrom and followed up by many others) and the latest specific posts on [running Ubuntu 16.04 beta (by @]("http://ubuntuforums.org/showthread.php?t=2301071&page=29")[[COLOR=#000000]Rommel_Lapuz[/COLOR]]("http://ubuntuforums.org/showthread.php?t=2301071&page=29")[, and others)]("http://ubuntuforums.org/showthread.php?t=2301071&page=29"), I decided to open a new thread on the forum for the Ubuntu 16.04 version, share my experience, and discuss any pending issues.

** UPDATE 2016/04/20: I just found another great information resource on running Linux on the XPS15 9550: [http://wiki.yobi.be/wiki/Laptop_Dell_XPS_15](http://wiki.yobi.be/wiki/Laptop_Dell_XPS_15)**

  My hardware configuration is (my system shipped mid february):

[LIST]
[*]Intel(R) Core(TM) i7-6700HQ CPU @ 2.60GHz 
[*]32G DDR4 RAM 
[*]SSD hard disk (not the usual SAMSUNG reported by others): THNSN51T02U7 NVMe TOSHIBA 1024GB 
[*]Intel HD530 
[*]NVIDIAGeForce GTX 960M 
[/LIST]

   I required a working system with dual boot Ubuntu and Windows 10 (Home edition in my case), and this is what I did:[INDENT]0. Update the BIOS to the latest version provided by DELL:
[/INDENT]

[LIST]
[*=1]I did this from Windows 
[*=1]Reboot and enter BIOS (Press F2 when the DELL logo shows up) 
[*=1]"Restore to BIOS defaults" before continuing. 
[*=1]Exit to reboot 
[/LIST]
[INDENT]1. Boot in windows and create recovery disk from the Windows box, in case something goes wrong.

[/INDENT]
[INDENT]2. Repartition SSD:
[/INDENT]

[LIST=|INDENT=2]
[*]I repartitioned from my original Windows Installation with "Minitool Partition Wizard Free" as I was used to it, but you can do this using gparted without problems, using the /dev/nvme0n1 disk.
[LIST=|INDENT=1]
[*]My XPS came with: 
[/LIST]
              
[/LIST]
[INDENT=3][SIZE=1][FONT=courier new]Partition    | Capacity  | FileS | Type                       | Status
*:ESP        | 500.00 MB | FAT32 | GPT (EFI System partition) | Active & Boot
*:           | 128.00 MB | Other | GPT (Reserved partition)   | None
C:OS         | 941.18 MB | NTFS  | GPT (Data partition)       | System
*:WINRETOOLS | 450.00 MB | NTFS  | GPT (Recovery partition)   | None
*:Image      |  11.63 BB | NTFS  | GPT (Recovery partition)   | None
[/FONT][/SIZE][/INDENT]

[LIST=|INDENT=3]
[*]I resized the windows partition (C:OS) to 100Gb (97.66 in the partition tool) 
[*]The new partition design is (I didn't bothered with separated / /var /home, etc. partitions): 
[/LIST]
[INDENT=3][FONT=courier new][SIZE=1]Partition    | Capacity  | FileS | Type                       | Status
*:ESP        | 500.00 MB | FAT32 | GPT (EFI System partition) | Active & Boot
*:           | 128.00 MB | Other | GPT (Reserved partition)   | None
C:OS         |  97.66 MB | NTFS  | GPT (Data partition)       | System
*:           | 843.52 MB | Unused| GPT (Data partition)       | None
*:WINRETOOLS | 450.00 MB | NTFS  | GPT (Recovery partition)   | None
*:Image      |  11.63 BB | NTFS  | GPT (Recovery partition)   | None[/SIZE]
[/FONT][/INDENT]
[INDENT]
3. Disable fast boot option in windows:
[/INDENT]

[LIST=|INDENT=2]
[*]In Windows 10, run "Control Panel | Hardware and sound | Power Options | Choose what the power buttons do", and at the bottom you'll see "Shutdown settings", with "Turn ohttp://ubuntuforums.org/newthread.php?do=newthread&f=332n fast startup (recommended)", which I disabled. 
[*]I also had the "Hibernate" option disabled by default, and I let it that way 
[/LIST]
[INDENT]4. Get ready for booting windows in Safe mode afterwards:
[/INDENT]

[LIST]
[*=1]Tthis is required to allow successful boot after changing the RAID to AHCI SATA configuration) 
[*=1]While in Windows, WIN+R and execute "msconfig" 
[*=1]Go to "Boot" and select "Safe mode boot". I left "Minimal" selected 
[/LIST]
[INDENT]5. Reboot and enter BIOS (Press F2 when the DELL logo shows up)
[/INDENT]

[LIST=|INDENT=2]
[*]"Secure Boot" | "Secure Boot Enable": Change from "Enabled" to "Disabled" 
[*]"System Configuration" | "SATA Operation": Change from "RAID On" to "AHCI" 
[*]Apply changes and save everything, and finally "Exit", to reboot 
[/LIST]
[INDENT]6. Enter windows. It will show up in Safe mode. 
[/INDENT]

[LIST]
[*=1]In my case I was not able to run msconfig with the WIN+R key, so that I pressed the "Start button" on screen, selected "All applications" and search for "Administrative Tools" and "System Configuration". Then go to the "Boot" tab again and unselect "Safe mode boot". Accept and shutdown. 
[/LIST]
[INDENT]7. Insert 16.04 USB stick (the one I downloaded dated late february), reboot, and enter BIOS again. 
[/INDENT]

[LIST]
[*=1]Go to "General" | "Boot sequence", and move the USB stick entry to the top. 
[*=1]Apply, save eveything, and "Exit" to reboot. 
[*=1]In my system I had "Windows Boot Manager", and then the "THNSN51T02U7 NVMe TOSHIBA 1024GB". 
[/LIST]
[INDENT]8. Enter ubuntu and run installation or run the installer in the Grub Menu. 
[/INDENT]

[LIST]
[*=1]I partitioned ALL the unused disk space in 16Gb SWAP (JIC :-) ) and / (I know this is not wise, but that's it) 
[/LIST]


[LIST]
[*]**The system installed perfectly and I had wifi+touchpad+sleep+shutdown+reboot working out of the box, with a 4k display resolution and tiny sized for everything :-) ** 
[/LIST]
 
  Desktop and additional issues/comments:

[LIST]
[*]Function buttons working: mute, volume up and down, keyboard backlit (off, mid, high intensity), display brightness up and down). 
[*]I'm fan of the "Gnome flashback" desktop, but after installation it didn't work: I couldn't make to appear the right part of the top panel (that with notifiers, and the system menu), and neither the bottom panel with the application list showed up :-(. If you have any clue, I'll really appreciate hints on this issue. 
[*]I finally decide to run the cinnamon desktop (given its suposedly reported ability to run hidpi natively). It works reasonbly well, but I still have some annoying issues. Mainly:
[LIST]
[*]The battery information in the panel does not update!!! (**UPDATE 2016/04/30 Updating to cinammon 3.0 fixed the problem (follow information on [http://www.webupd8.org/2016/04/how-to-install-cinnamon-30-in-ubuntu.html](http://www.webupd8.org/2016/04/how-to-install-cinnamon-30-in-ubuntu.html) (just add ****ppa:embrosyn/cinnamon, update and upgrade)**) 
[*]The touchpad is "lost" sometimes (didn't look into this issue yet) 
[/LIST]
  
[*]To avoid tiny fonts in the Grub screen, add GRUB_GFXMODE=1024x768 to /etc/default/grub and run sudo update-grub 
[/LIST]
 
[LIST]
[*]Regarding the use of NVIDIA/intel:
[LIST]
[*]From the applications menu, I selected "Preferences|Additional drivers", and selected to use the "NVIDIA binary driver - version 361.28 from nvidia-361 (privative, tested). Then apply changes. 
[*]I installed nvidia-prime 
[*]Now I can run nvidia-settings and select either NVIDIA GPU (Performance Mode) or Intel (Power Saving Mode). 
[*]Others reported various stories when using the PPA NVIDIA repositories. I didn't tested them yet. 
[/LIST]
            
[/LIST]
 
[LIST]
[*]Regarding Bluetooth support
[LIST]
[*]Bluetooth seemed to be detected (according to the notification area), but it didn't actually work. 
[*]dmesg showed an error related to a firmware not found:
[SIZE=1][FONT=courier new]...Direct firmware load for brcm/BCM-0a5c-6410.hcd failed...[/FONT][/SIZE] 
[*]Following [https://bbs.archlinux.org/viewtopic.php?id=204739](https://bbs.archlinux.org/viewtopic.php?id=204739) I downloaded the [missing firmware]("https://www.dropbox.com/s/8goc4omhnzxij93/BCM-0a5c-6410.hcd?dl=0") file (thanks @ZombieMeat) [at Dropbox]("https://www.dropbox.com/s/8goc4omhnzxij93/BCM-0a5c-6410.hcd?dl=0") and copied it to /lib/firmware/brcm/ 
[*]Reboot and bluetooth is working (tested at least with a bluetooth speaker) 
[/LIST]
            
[/LIST]
 
[LIST]
[*]Some other details on getting the hidpi to look reasonable in size and application specific information:
[LIST]
[*]I first tried to use the information on [http://askubuntu.com/questions/472262/adapt-ubuntu-to-a-high-dpi-resolution-screen](http://askubuntu.com/questions/472262/adapt-ubuntu-to-a-high-dpi-resolution-screen) and [http://hgdev.co/optimize-ubuntu-interface-scaling-on-hidpi-displays/](http://hgdev.co/optimize-ubuntu-interface-scaling-on-hidpi-displays/) to get usable sizes in the high-DPI screen.  Mainly:
[LIST]
[*]On the system setting for Displays, modify the "Scale for menu and title bars". In my case I used 1.75 or 2.0 and sizes become reasonable 
[/LIST]
  
[*]If you use qt apps (from [https://wiki.archlinux.org/index.php/HiDPI#GUI_toolkits](https://wiki.archlinux.org/index.php/HiDPI#GUI_toolkits)) do (preferrably add this to /etc/profile.d/qt-hidpi.sh)
[LIST]
[*]export QT_DEVICE_PIXEL_RATIO=2 
[/LIST]
  
[*]Run "xrandr --dpi 288" to set precise screen dimensions (From [http://wiki.yobi.be/wiki/Laptop_Dell_XPS_15#HiDPI](http://wiki.yobi.be/wiki/Laptop_Dell_XPS_15#HiDPI)) 
[*]If you use VLC and video overlaps the desktop and/or does not scale, follow [https://wiki.archlinux.org/index.php/VLC_media_player#Video_output_overlaps_the_desktop.2C_does_not_scale_nor_position_properly](https://wiki.archlinux.org/index.php/VLC_media_player#Video_output_overlaps_the_desktop.2C_does_not_scale_nor_position_properly) and set Tools|Preferences|Show setting -> all. Then Video|Output modules|OpenGL GLX (XCB). That's it 
[*]I Used chrome (installed from the official google site supporting debian/ubuntu based systems at [https://www.google.com/linuxrepositories](https://www.google.com/linuxrepositories)/) of firefox. Both of them should take the default scaling from ubuntu. For additional details on adapting firefox, you can refer to [http://askubuntu.com/questions/487032/adjust-firefox-and-thunderbird-to-a-high-dpi-touchscreen-display-retina](http://askubuntu.com/questions/487032/adjust-firefox-and-thunderbird-to-a-high-dpi-touchscreen-display-retina) 
[*]Additional information on:
[LIST=|INDENT=1]
[*][http://askubuntu.com/questions/197828/how-to-find-and-change-the-screen-dpi/462023#462023](http://askubuntu.com/questions/197828/how-to-find-and-change-the-screen-dpi/462023#462023) 
[*][http://askubuntu.com/questions/472262/adapt-ubuntu-to-a-high-dpi-resolution-screen](http://askubuntu.com/questions/472262/adapt-ubuntu-to-a-high-dpi-resolution-screen) 
[*][http://askubuntu.com/questions/594151/icon-scaling-seems-to-work-partially-on-a-dell-4k-display-im-using-ubuntu-14-0](http://askubuntu.com/questions/594151/icon-scaling-seems-to-work-partially-on-a-dell-4k-display-im-using-ubuntu-14-0) 
[/LIST]
              
[/LIST]
              
[/LIST]
 
[LIST]
[*]Problems with palm detection on the touchpad.  [http://stevenkohlmeyer.com/fixing-palm-detect-ubuntu-14-04/](http://stevenkohlmeyer.com/fixing-palm-detect-ubuntu-14-04/) deals with it
[LIST]
[*]In my XPS, xinput reports having two touchpads (?):
[LIST]
[*]DLL06E4:01 06CB:7A13 Touchpad id=13 [slave  pointer  (2)] 
[*]SynPS/2 Synaptics TouchPad id=15 [slave  pointer  (2)] 
[/LIST]
  
[*]I played with id=15 first, without success, but with id=13, things seem to work. This is what I added to startup programs:
[LIST]
[*]xinput set-prop 13 "Synaptics Palm Detection" 1 
[*]xinput set-prop 13 "Synaptics Palm Dimensions" 5, 5 
[/LIST]
  
[*]If you still had problems with detection on edges, you can apply ideas shown in [http://ubuntuforums.org/showthread.php?t=2153813](http://ubuntuforums.org/showthread.php?t=2153813) 
[*]I still have problems to avoid the palm to be undetected and I'm still investigating. If you happen to get usable parameters for the xinput props, please let me know:
[LIST]
[*][B]Update 2016/04/05; I also added "/usr/bin/syndaemon -i 1 -K -d" to the startup applications to disable touchpad while typing. Still not fully tested if that makes a difference 
[/B] 
[*]**Update 2016/04/30: Following [http://wiki.yobi.be/wiki/Laptop_Dell_XPS_15#Touchpad](http://wiki.yobi.be/wiki/Laptop_Dell_XPS_15#Touchpad) I added file /etc/modprobe.d/synaptics.conf with "blacklist i2c-designware-platform" and now disable touchpad when typing works (still have to check if there are any additional side-effects)** 
[/LIST]
     
[/LIST]
  
[*]**Update 2016/04/05: Issues with the DA-200 USB-C to VGA,HDMI,USB,Ethernet dongle:**
[LIST]
[*]**Ethernet only worked when the DA-200 was connected at boot time, and after each suspend-resume it didn't worked either. @jsla7527 at the [15.10 thread]("http://ubuntuforums.org/showthread.php?t=2301071&page=27&p=13442316#post13442316") gives a solution to force usb-c rescanning. You need to run the following command after plugging anything into USB-C port:**
[LIST]
[*]**sudo sh -c "echo 1 > /sys/bus/pci/rescan" ** 
[/LIST]
  
[*]VGA works even whithout the rescan command, but I get random system freezes. Other people reported freezes with HDMI connections, but I haven't investigated this so far. **Update 2016/05/17: I upgraded to kernel 4.6 (as I read that there were improvements in the skylake support for 9350, that I suspected could also benefit 9550) and the VGA connection of the DA-200 seems to work properly (no more flickering nor hangs up during the first two hours of test). I'm using the intel prime profile and will check later what if using nvidia. ** 
[/LIST]
  
[*]**Update 2016/04/20: Sensors detection (from [http://wiki.yobi.be/wiki/Laptop_Dell_XPS_15#Sensors):](http://wiki.yobi.be/wiki/Laptop_Dell_XPS_15#Sensors):)**
[LIST]
[*]**apt-get install lm-sensors** 
[*]**sensors-detect** 
[*]**Follow instructions and modify /etc/modules as instructed ** 
[/LIST]
   
[/LIST]

  So, my pending not-fully-working issues are:

[LIST]
[*]Palm detection: Working parameters are needed 
[*]Gnome flashback not working 
[*]Cinnamon: battery info in the panel notification area does not update 
[*]Touch pad: Breaks from time to time. Update 2016/04/05: No breaks from a couple of weeks ago. I guess 16.04 updates did the trick. 
[*]**Update 2016/04/05: VGA connection through DA-200 randomly freezes the system. ** 
[/LIST]

  That's it for now. I'll try to do some power demands calculations and keep you posted (some results [are already available from @bertusrex at the original 15.10 thread]("http://ubuntuforums.org/showthread.php?t=2301071&page=29")).


  Javi

---

### Post by Tazza101 on 2016-03-20
THANKS A LOT MAN!
I am about to buy this laptop and I was wondering if ubuntu 16.04 fixes the problems I've been reading about and also I was unsure about how to dual boot; you have answered in great detail thanks! :)

---

### Post by holdfenytolvaj on 2016-03-21
Touchpad palm detection might work with kernel 4.5?
[https://github.com/advancingu/XPS13Linux/issues/3](https://github.com/advancingu/XPS13Linux/issues/3)

---

### Post by mick-clarke on 2016-03-23
I've been running 16.04 for a couple of weeks now. I largely followed the same path as the OP using the instructions on the 15.10 thread, but used the non-tested 361 Nvidia driver as I found the tested version gave me lots of issues (go figure). I can swap between the GPUs okay and bluetooth works.

The system is getting more stable everyday with only a couple of key issues, below. I find I'm getting ~6.5 hours life out the battery, or more, and this includes coding, compiling, some docker containers running and the usual supporting web and email - so okay; it includes multiple suspends (close lid) with no significant drain when suspended. That said I get nowhere near some of the values out of powertop (~5-6W) other report at idle; more like 11W+. But I'm happy enough with the battery life for my usage, though getting it up to the nearer 9-10 hours I can get on Windows would be great.

Issues that are annoying:


[LIST]
[*]After suspend I cannot power off or restart without commandline using -f;
[*]The touchpad is still pretty rubbish, but (just about) liveable
[/LIST]

Thanks as always to all the contributors - it's great to see the community working so hard getting issues resolved and changing over the last couple of weeks from what was a marginally unusable installation into a robust system that I now use as my daily machine.

---

### Post by trtzt on 2016-03-23
Hi,

I am using ubuntu 16.04 on the dell 9550 laptop, too. The hardware is basically the same as mentioned in the first post from . I can confirm that bluetooth does not work at the fist place but copying the firmware file will fix it and I was able to connect to my phone via bluetooth. Touchpad works for me altouh i can see 2 touchpads. 
But I am having troubles with my second monitor. I have an external monitor connected via HDMI and every time i power on the computer the whole system will freeze after I have logged on. I cannot move the mouse nor enter any keyboard commands. This happens with both grafikcards, Intel and the Nvidia. Does anyone have a solution for the problem? I have tried reinstalling and reconfiguration of the X server with no change in output. Is this a general skylake problem?

uname -r
 > 
4.4.0-13-generic


X -version
> 
X.Org X Server 1.18.1
Release Date: 2016-02-08
X Protocol Version 11, Revision 0
Build Operating System: Linux 3.13.0-79-generic x86_64 Ubuntu
xorg-server 2:1.18.1-1ubuntu4 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.33.6
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.


sudo ubuntu-drivers devices
 > 
vendor   : NVIDIA Corporation
model    : GM107M [GeForce GTX 960M]
driver   : nvidia-361-updates - distro non-free
driver   : xserver-xorg-video-nouveau - distro free builtin
driver   : nvidia-361 - distro non-free recommended

== cpu-microcode.py ==
driver   : intel-microcode - distro non-free


---

### Post by huaba-net on 2016-03-30
Im running 16.04 and struggling with freezes if external monitor is connected with HDMI. Booting with connected monitor is not possible. Running nvidia-prime, mainly on Intel-GPU. Tested NVIDIA binary driver in version 358.16, 361.20 and 364.12 without success.

Any hints for me?

Thx
Huaba

---

### Post by howefield on 2016-03-30
Moved to the "*Ubuntu Development Version*" forum.

---

### Post by trtzt on 2016-03-30
Hello huaba-net, 
I have had the same problem like you. To disappoint you right away I don't have a perfect solution, just a dirty fix.  My problem is the same, the system freezed at the log in screen when the monitor was connected via HDMI (Dell U2414h). No reaction to keyboard entries nor any loging in the kern.log or Xorg.log... However when the laptop booted up completely and I logged in, with the external monitor disconnected, everything worked fine. When I plugged it in while the system was running, the monitor was correctly recognized and it worked perfectly.  But I did not what to connect and disconnect the HDMI cable every time I booted the system. So what I did was t active the nvidia card via the prime indicator [http://www.webupd8.org/2014/01/prime-indicator-lets-you-quickly-switch.html](http://www.webupd8.org/2014/01/prime-indicator-lets-you-quickly-switch.html). Connected my Second monitor and adjusted everything correctly. The I rebooted system and added the line "nouveau.modeset=1" to the grub command line and pressed F10. The kernel booted, both monitors where running and I was able to log in with no freezes. Right after logged in, I change the grub command line in /etc/default/grub to contain  "GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nouveau.modeset=0" and ran an sudo update-grub. Now it works more or less like  charm. Sometimes I get  CRTC-63 error and left and right monitors are switched. Logging in and out will restore the settings.
It is not possible for me to use the Intel card with both monitors connected.

---

### Post by ant-merlino on 2016-03-31
Hey guys,

Firstly, thanks for all the hard work and info in this thread ant the 15.10 thread.  I just got my XPS yesterday and got Ubuntu on with only minor trouble in a few hours.  My main issue currently is the touchpad.  But not with palm rejection.  Basically if I am moving the cursor with my middle finger, then go to click with my pointer finger, many times the cursor jumps.  It seems as though it thinks that my finger quickly moved from point to point and is like oh snap let me move there. I'm not sure if this is a pressure thing or a timing thing.  But it is frustrating as all heck. Go to click something and randomly jump somewhere else, or worse, click something else.  The other way for me to reproduce the jump is to simply tap with my middle immediately followed by my pointer tap.  The further my fingers are apart the further it jumps. The direction between my fingers is also the direction. So it definitely seems like it isn't really recognizing both fingers or something.

Any help would be appreciated. So far everything else seems to be working!

---

### Post by svenakela on 2016-03-31
Same laptop as OP, installation went on without problems but network is not working. Really stuck, can't figure out how to solve this one.

The Wifi is connected to the router according to the networking icon, no data is going through. If I reconnect to the router the network is ok for a few seconds and then new connections (as in TCP conns) are not accepted anymore. This means that I can't update Ubuntu because the Wifi will drop the connections and nothing will be downloaded. I tried with an external USB Wifi and ended up with the same result so I suspect that the problem is networking and not the card itself.
The network card seems to be working, no logs that relates to networking as far as I can see and the driver and firmware for the card is in place.
Network card is a Broadcom BCM43602
Driver brcmfmac version 7.35.177.61

I've been using the March 25 release of 16.04 Desktop amd64.

---

### Post by svenakela on 2016-03-31
> **svenakela said:**
> Same laptop as OP, installation went on without problems but network is not working. Really stuck, can't figure out how to solve this one.

The Wifi is connected to the router according to the networking icon, no data is going through. If I reconnect to the router the network is ok for a few seconds and then new connections (as in TCP conns) are not accepted anymore. This means that I can't update Ubuntu because the Wifi will drop the connections and nothing will be downloaded. I tried with an external USB Wifi and ended up with the same result so I suspect that the problem is networking and not the card itself.
The network card seems to be working, no logs that relates to networking as far as I can see and the driver and firmware for the card is in place.
Network card is a Broadcom BCM43602
Driver brcmfmac version 7.35.177.61

I've been using the March 25 release of 16.04 Desktop amd64.

I've found the problem! :)
The IPv6 DNS (which is empty) was conflicting somehow with the IPv4 config. I disabled IPv6 for the connection and voilá! :)

Now I just need to get some bigger fonts and tweak the palm detection a little bit and this will be a killer machine!

---

### Post by Starlith on 2016-04-01
I have the 1080p model of this laptop, battery life is pretty good on this.

For touchpad I changed to libinput and I think its better than the Synaptics one. I even have my right click working. Not too sure how I go about reverting back to Synaptics but that doesn't matter as for now I like libinput touchpad as the palm detection is better than Synaptics.

If you wanna give it a go heres what I done.

> sudo apt-get install xserver-xorg-input-libinput

> sudo gedit /usr/share/X11/xorg.conf.d/99-libinput.conf

Then you can copy my config and save to your libinput.conf

> 
Section "InputClass"
        Identifier "libinput"
        Driver "libinput"
        MatchDevicePath "/dev/input/event*"
        Option "Tapping" "True"
        Option "DisableWhileTyping" "True"
        Option "NaturalScrolling" "True"
        Option "AccelProfile" "adaptive"
        Option "AccelSpeed" "0.05"
	Option "ClickMethod" "clickfinger"
        Option "MiddleEmulation" "True"
        Option "ScrollMethod" "twofinger"
        Option "SendEventsMode" "disabled-on-external-mouse"
EndSection


Any improvements let me know ;)

---

### Post by Merijn_Vogel on 2016-04-01
Thanks for this thread! I was unlucky when installing 15.10 and 14.04.x, now running 16.04 and my Dell 9550 with 512Gb SSD works as I wish!

---

### Post by Yeong-Il_Yi on 2016-04-01
Thanks to the OP for this thread. I recently acquired the Dell Precision 5510, which is very similar to the Dell XPS 15 9550. One difference is the graphics: the XPS has the nVidia GeForce GTX 960M, while the Precision has the nVidia Quadro M1000M. I plan on doing a clean install of Ubuntu 16.04 on the Precision when it is released.

---

### Post by GryfonN on 2016-04-06
Hi guys I need help as a noob user with NVIDIA driver installation.

Today I have tried to install Gnome Ubuntu 16.04 beta2 (later also daily iso from 5.4.), with both of them I had a problem to install Nvidia driver from "*Additional Drivers*" application. After I have installed **nvidia-361 **(361.42) or **nvidia-361-updates **after reboot I had black screen. So to get back Nouveau driver I press Ctrl+Alt+F1 > login > uninstall nvidia driver : 

[I]sudo apt-get purge nvidia-*
sudo apt-get autoremove
sudo service gdm restart[/I]

Then I searched for another options of nvidia driver, I added *ppa:graphics-drivers/ppa* and with *apt-cache search nvidia*, I saw that second driver to install could be **nvidia-358**, but after reboot i had same blackscreen. 

I have also tried to install NVIDIA binary driver according to guide from [http://www.allaboutlinux.eu/remove-nouveau-and-install-nvidia-driver-in-ubuntu-15-04/](http://www.allaboutlinux.eu/remove-nouveau-and-install-nvidia-driver-in-ubuntu-15-04/), but I had again black screen after reboot. 

Should I install also some additional packages to these drivers, or what I do wrong ? I also would like to ask for some nice reference link, where I could read about how to install NVIDIA + Intel Graphic driver in laptops, because this is my first machine with Nvidia graphic card and Intel integrated, so I am not familiar with installation of "prime" or "bumblebee", and how to switch between these two graphic cards in laptop. Thx.

**EDIT:**
Finally I found that **nvidia-364** is also available to install and it works. I also found how to install **intel graphic driver** ([http://ubuntuforums.org/showthread.php?t=2301071&page=29](http://ubuntuforums.org/showthread.php?t=2301071&page=29)), but they do not work together. When I switch from NVIDIA to intel and try to relog, I am stuck in login screen. After some testing I decided to stay with intel driver, because it is most friendly to my laptop battery = cca 15W power consumption = "surfing net with music". To switch between drivers I used prime-select , it works, and I also tried to install bumblebee but this was not working for me. So now I will stay with intel driver, enjoy my Gnome Ubuntu on XPS 15 and wait until somebody will find way how to run nvidia driver together with intel.

---

### Post by oscardssmith on 2016-04-12
Has anyone tried the new bios (1.2)? If so, any changes?.

---

### Post by mistur on 2016-04-15
Hello,


I have also a Dell Xps 15 9550 (i7-6700HQ - 1TB SSD - UHD 4k touch)         running ubuntu 15.10 first and upgrade to 16.04 few weeks ago. 

I have 2 issues.
 
First one, for 3 or 4 days, when I open my laptop after I closed my screen, the laptop reboot, here the latest kern.log after the reboot :

> Apr 15 09:45:42 kveikur kernel: [ 4940.692255] ACPI Error: [\_SB_.PCI0.LPCB.H_EC.CHRG] Namespace lookup failure, AE_NOT_FOUND (20160108/psargs-359)
Apr 15 09:45:42 kveikur kernel: [ 4940.692276] ACPI Error: Method parse/execution failed [\PNOT] (Node ffff8804af8dcd20), AE_NOT_FOUND (20160108/psparse-542)
Apr 15 09:45:42 kveikur kernel: [ 4940.692308] ACPI Error: Method parse/execution failed [\_SB.AC._PSR] (Node ffff8804af8efac8), AE_NOT_FOUND (20160108/psparse-542)
Apr 15 09:45:42 kveikur kernel: [ 4940.692444] ACPI Exception: AE_NOT_FOUND, Error reading AC Adapter state (20160108/ac-128)
Apr 15 09:45:45 kveikur kernel: [ 4943.632379] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
Apr 15 09:45:45 kveikur NetworkManager[1033]: <info>  [1460706345.1139] manager: sleep requested (sleeping: no  enabled: yes)
Apr 15 09:45:45 kveikur NetworkManager[1033]: <info>  [1460706345.1140] manager: sleeping...
Apr 15 09:45:45 kveikur NetworkManager[1033]: <info>  [1460706345.1142] device (wlp2s0): state change: activated -> unmanaged (reason 'sleeping') [100 10 37]
Apr 15 09:45:45 kveikur NetworkManager[1033]: <info>  [1460706345.1483] dhcp4 (wlp2s0): canceled DHCP transaction, DHCP client pid 1759
Apr 15 09:45:45 kveikur NetworkManager[1033]: <info>  [1460706345.1483] dhcp4 (wlp2s0): state changed bound -> done
Apr 15 09:45:45 kveikur kernel: [ 4943.675698] brcmf_inetaddr_changed: fail to get arp ip table err:-23
Apr 15 09:45:45 kveikur NetworkManager[1033]: <info>  [1460706345.1570] dns-mgr: Writing DNS information to /sbin/resolvconf
Apr 15 09:45:45 kveikur kernel: [ 4943.678076] brcmf_cfg80211_del_pmksa: Cache entry not found
Apr 15 09:45:45 kveikur kernel: [ 4943.678089] brcmf_cfg80211_del_pmksa: Cache entry not found
Apr 15 09:45:45 kveikur kernel: [ 4943.678096] brcmf_cfg80211_del_pmksa: Cache entry not found
Apr 15 09:45:45 kveikur kernel: [ 4943.678113] brcmf_cfg80211_del_pmksa: Cache entry not found
Apr 15 09:45:45 kveikur kernel: [ 4943.678120] brcmf_cfg80211_del_pmksa: Cache entry not found
Apr 15 09:45:45 kveikur kernel: [ 4943.678126] brcmf_cfg80211_del_pmksa: Cache entry not found
Apr 15 09:45:45 kveikur kernel: [ 4943.696061] brcmf_cfg80211_reg_notifier: not a ISO3166 code
Apr 15 09:45:45 kveikur NetworkManager[1033]: <info>  [1460706345.1859] manager: NetworkManager state is now ASLEEP
Apr 15 09:45:45 kveikur kernel: [ 4944.210744] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
Apr 15 09:45:47 kveikur kernel: [ 4945.801220] ACPI Error: Cannot release Mutex [PATM], not acquired (20160108/exmutex-393)
Apr 15 09:45:47 kveikur kernel: [ 4945.801224] ACPI Error: Method parse/execution failed [\_SB.PCI0.LPCB.ECDV._Q66] (Node ffff8804af8ef0f0), AE_AML_MUTEX_NOT_ACQUIRED (20160108/psparse-542)
Apr 15 09:53:36 kveikur kernel: [    0.000000] Linux version 4.5.1-040501-generic (kernel@gloin) (gcc version 5.2.1 20151010 (Ubuntu 5.2.1-22ubuntu2) ) #201604121331 SMP Tue Apr 12 17:33:29 UTC 2016
Apr 15 09:53:36 kveikur kernel: [    0.000000] Command line: BOOT_IMAGE=/vmlinuz-4.5.1-040501-generic root=UUID=3d43bf5d-2e5b-4c0e-b4d6-13482c05371b ro quiet splash

is anyone have the same behavior ?

I was in kernel 4.4.0-16 and I try to switch to 4.5.1 from [http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=M;O=D](http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=M;O=D) but that does not fix this issue.

The second issue is I cannot run the default ubuntu desktop, X tell me that I have no 3D support, I try to use nvidia card with the official nvidia driver, intel drivers, kernel drivers but, none of them works. I don't have so much time to work on that issue ( I switch to i3wm now and work well) but if someone have and idea to fix this, I will try when I will have time to work one.

Thanks for you help (and for all those informations) 

Yoann

---

### Post by stefano-spell on 2016-04-15
Hello! Thank you for this amazing guide, I succesfully installed Ubuntu on an XPS 15 9550 i7 16gb ram 512gb ssd FHD machine.
Everything works (did not try to install NVIDIA drivers, simply because I only need to develop software on ubuntu, so the dGPU is not essential).

The only problem I have is that the lcd sometimes goes black for half a second randomly and then back to normal. I installed Intel linux graphics and it seems to work, except for this tedious issue.
Does someone have the same problem? I could not find very much on the net, actually.

Thank you again!

---

### Post by dave0109 on 2016-04-16
I had the same issue with the screen blanking out for fractions of a second. There's an issue on [launchpad]("https://bugs.launchpad.net/bugs/1558736") about it, though it is marked as a duplicate of something similar. Either way, installing the older 4.4.0 kernel mention resolved the issues for me.

---

### Post by wundbread on 2016-04-19
> **oscardssmith said:**
> Has anyone tried the new bios (1.2)? If so, any changes?.

The update went smooth.  No differences I have noticed.  

FYI you can install by copying the bios file to /boot/efi/  and pressing F12 at boot, then select update bios.

The two issues still bugging me (freeze when switching modes with an hdmi monitor, headphone jack not working), are still there...

---

### Post by huaba-net on 2016-04-20
Now my external hdmi monitor works with intel card. (@trtzt)

What i've done: 
uninstall nvidia-361 complete (and any other nvidia drivers otherway versions will be mixed up an no login is possible - loginloop), add graphics-drivers ppa, install nvidia-364, install newest kernel (4.4.0.21) with apt-get upgrade 

```

# switch to intelsudo prime-select intel
<logout>
<login>


# uninstall 361
sudo apt-get purge nvidia-361 libcuda1-361 nvidia-opencl-icd-361
#may not be necessary, just to be sure
sudo depmod -a


# install nvidia-364
sudo apt-get install nvidia-364

# complete updates
sudo apt-get update && sudo apt-get upgrade
sudo apt-get dist-upgrade

reboot

```

Now i'm able to connect my hdmi monitor AFTER login without freezes. Booting with connected monitor is not possilbe (freeze on login screen).

Thanks to bertusrex for [this comment]("http://ubuntuforums.org/showthread.php?t=2301071&p=13462404#post13462404")

---

### Post by S4boteur on 2016-04-21
Hey guys, 

I'm running on an XPS 15 9530 4K UHD. Instead of setting 1024x768 in GRUB, you should generate a new, 36px sized grub font, and then use that as a Grub font. This way you solved the HiDPI scaling issue on you laptop. ;) 

```
sudo grub-mkfont --output=/boot/grub/fonts/hack.pf2 --size=38 /usr/share/fonts/truetype/hack/Hack-Regular.ttf
```

I'm using the Hack font as fixed width typeface. If you want, you can use another font, just modify the names accordingly. You can install Hack fonts with this command: 
```
sudo apt install fonts-hack-ttf
```

Edit default grub settings to set the font: 
```
sudo nano /etc/default/grub
```

Paste the snippet below somewhere in the file (I prefer it below the line starting with GRUB_CMDLINE_LINUX): 
```
GRUB_FONT=/boot/grub/fonts/hack.pf2
```

After this, run update-grub:
```
sudo update-grub
```

Enjoy! :) 

Source: [https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)

---

### Post by mick-clarke on 2016-04-24
Has anyone had any luck with better performance from the touchpad? I work mostly mobile and need it to perform well, but largely it drives me nuts!

I've spent hours fiddling with the Synaptics settings, but it's not even close to the function when in Windows (that I rarely use)

Any ideas appreciated.

---

### Post by bart20 on 2016-04-24
> **wundbread said:**
> The update went smooth.  No differences I have noticed.  

FYI you can install by copying the bios file to /boot/efi/  and pressing F12 at boot, then select update bios.

The two issues still bugging me (freeze when switching modes with an hdmi monitor, headphone jack not working), are still there...

[COLOR=#222222][FONT=Verdana]I think I had the same headphone jack issue, no sound coming out. I fixed it by removing my PulseAudio config. [/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]Unplug any headphones you have attached and do an ```
rm -rf ~/.config/pulse/
```[/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana]Log out and back in, and it should work again.[/FONT][/COLOR]

---

### Post by paulll.lucas on 2016-04-25
Thanks so much for this guide!  Also thanks to Starlith for the awesome mouse configuration. 
 I'm still having a fair amount of strange problems and was wondering if anyone else has experienced them. 
I should also note that I'm currently using the Intel nvidia-prime profile (in nvidia-settings), as the Nvidia profile is even more problematic. 

1. Screen randomly flashing black (not often, very sparse) 
2. Slight flickering when scrolling web pages (in firefox, Chrome is completely unusable).
3. Random noise when using a USB soundcard (sounds exactly like when you place a cellphone next to a speaker). 
4. If I use the Atom text editor, whilst typing, random lines start appearing (I'm guessing this is chrome-related as it's running v8).
 Most of these are graphic related, is this mostly just related to poor drivers? Is there anything I can do in the meantime?  Thanks again!

Update:
I should also mention that trying to install the 364 nvidia driver broke my system (login-loop, had to revert to xorg then reinstall 361).
I would not recommend anyone download the Intel Graphics Linux Installer (mentioned here: [http://ubuntuforums.org/showthread.php?t=2301071&page=29](http://ubuntuforums.org/showthread.php?t=2301071&page=29)), it caused a lot of errors and I ended up having to remove it as a broken package. 
This morning I started to experience the system randomly turning itself off. When I turned it back on the bios had reset itself to RAID. I kept getting "No Boot devices found" errors. I'm sure I didn't switch out of Legacy mode ever, but the only way to get back to GRUB and boot any OS's was to switch back to AHCI and UEFI mode.
I had a quick chance to backup my files, but it kept randomly crashing and resetting the BIOS. Now it seems the BIOS doesn't even appear, it just turns on and quickly turns off again. I plan on returning it ASAP. There shouldn't be this much instability, regardless if I'm running linux.

(1080p model, 8gb ram, 256gb ssd)

---

### Post by sze5003 on 2016-04-25
> **paulll.lucas said:**
> Thanks so much for this guide!  Also thanks to Starlith for the awesome mouse configuration.  I'm still having a fair amount of strange problems and was wondering if anyone else has experienced them. I should also note that I'm currently using the Intel nvidia-prime profile (in nvidia-settings), as the Nvidia profile is even more problematic.  - Screen randomly flashing black (not often, very sparse) - Slight flickering when scrolling web pages (in firefox, Chrome is completely unusable) - Random noise when using a USB soundcard (sounds exactly like when you place a cellphone next to a speaker)  - If I use the Atom text editor, whilst typing, random lines start appearing (I'm guessing this is chrome-related as it's running v8) Most of these are graphic related, is this mostly just related to poor drivers? Is there anything I can do in the meantime?  Thanks again!

I have the FHD version and I tried the 361 version of nvidia but mostly I want to use the default Intel/xorg driver for battery. I get a lot of screen flickering randomly on the desktop. I'm not sure how to solve that. I wonder how it hasn't happened for anyone else?

---

### Post by brontal on 2016-04-27
Hi all, beatiful guide, it helps me a lot :) ! just few questions to help me understand in deep please:


[LIST=1]
[*]is there anyone who could explain me what meaning does raid on a single ssd?
[*]before reading this thread I installed ubuntu alongside windows without boot windows in safety mode before switch from RAID to AHCI (I skipped point 4 and 6 becouse I didn't know), so Windows was able to run only with RAID mode on, conversely Ubuntu only in AHCI mode (the guide solved this issue). Why?
[/LIST]

---

### Post by grahammechanical on 2016-04-28
> is there anyone who could explain me what meaning does raid on a single ssd?

I have no wish to disagree with anyone. But, Is it a single SSD?

2 x 512 GB SSD = 1 TB SSD with RAID. In this way manufacturers can offer higher storage capacity by using up existing 512 GB SSD stock and then wait until the price of 1 TB SSD drops before installing 1 TB SSD in their machines.

It is just a guess.

Regards.

---

### Post by sze5003 on 2016-04-29
> **paulll.lucas said:**
> Thanks so much for this guide!  Also thanks to Starlith for the awesome mouse configuration. 
 I'm still having a fair amount of strange problems and was wondering if anyone else has experienced them. 
I should also note that I'm currently using the Intel nvidia-prime profile (in nvidia-settings), as the Nvidia profile is even more problematic. 

1. Screen randomly flashing black (not often, very sparse) 
2. Slight flickering when scrolling web pages (in firefox, Chrome is completely unusable).
3. Random noise when using a USB soundcard (sounds exactly like when you place a cellphone next to a speaker). 
4. If I use the Atom text editor, whilst typing, random lines start appearing (I'm guessing this is chrome-related as it's running v8).
 Most of these are graphic related, is this mostly just related to poor drivers? Is there anything I can do in the meantime?  Thanks again!

Update:
I should also mention that trying to install the 364 nvidia driver broke my system (login-loop, had to revert to xorg then reinstall 361).
I would not recommend anyone download the Intel Graphics Linux Installer (mentioned here: [http://ubuntuforums.org/showthread.php?t=2301071&page=29](http://ubuntuforums.org/showthread.php?t=2301071&page=29)), it caused a lot of errors and I ended up having to remove it as a broken package. 
This morning I started to experience the system randomly turning itself off. When I turned it back on the bios had reset itself to RAID. I kept getting "No Boot devices found" errors. I'm sure I didn't switch out of Legacy mode ever, but the only way to get back to GRUB and boot any OS's was to switch back to AHCI and UEFI mode.
I had a quick chance to backup my files, but it kept randomly crashing and resetting the BIOS. Now it seems the BIOS doesn't even appear, it just turns on and quickly turns off again. I plan on returning it ASAP. There shouldn't be this much instability, regardless if I'm running linux.

(1080p model, 8gb ram, 256gb ssd)

How did you fix the screen flickering issue?

---

### Post by cariboo on 2016-04-29
Moved to General Help, as it has nothing to do with Yakkety.

---

### Post by dave0109 on 2016-04-30
> **sze5003 said:**
> I get a lot of screen flickering randomly on the desktop. I'm not sure how to solve that. I wonder how it hasn't happened for anyone else?

It has - you just haven't searched enough :-)

There are some comments that disabling tlp will help, though that's not something that I've tried, and really, I kind of want tlp to do its thing.

The only thing that worked for me was installing the 4.4.0-040400-generic kernel from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-wily/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-wily/) or the 4.4.1-040401-generic kernel from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4.1-wily/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4.1-wily/) I've not yet had chance to try any of the others, except for 4.5.2 which did NOT fix things on my machine.

To install, I downloaded the following files (for 4.4.1):-
```

linux-headers-4.4.1-040401_4.4.1-040401.201601311534_all.deb
linux-headers-4.4.1-040401-generic_4.4.1-040401.201601311534_amd64.deb
linux-image-4.4.1-040401-generic_4.4.1-040401.201601311534_amd64.deb

```

I put these into a separate directory/folder to make life easier. Once downloaded, I used the following command to install them...
```
dpkg -i *.deb
```

Obviously don't run that if you have other DEB files within the same directory, as it will install all that it finds.  Hence why I used a new directory.  Of course, you could use the command line tab completion to pick each of the 3 files specifically.

After they were installed, I rebooted, chose 'Advance options for Ubuntu' on GRUB, and made sure I picked the newly installed kernel.  In my case this was at the top of the list anyway, so future boots could just chose the normal 'Ubuntu' option.

There are several issues/tickets on lauchpad about it, everyone affected should add their voice otherwise the developers may think the issue just effects a couple of people and it won't get any priority.

The other thing that worked for me was NOT installing Ubuntu Mate. When running with the main Ubuntu, I don't get the flickering even with kernel 4.4.0-21.  My Dell firmware is 1.0.4 if that makes any difference.

---

### Post by sze5003 on 2016-04-30
> **dave0109 said:**
> It has - you just haven't searched enough :-)

There are some comments that disabling tlp will help, though that's not something that I've tried, and really, I kind of want tlp to do its thing.

The only thing that worked for me was installing the 4.4.0-040400-generic kernel from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-wily/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-wily/) or the 4.4.1-040401-generic kernel from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4.1-wily/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4.1-wily/) I've not yet had chance to try any of the others, except for 4.5.2 which did NOT fix things on my machine.

To install, I downloaded the following files (for 4.4.1):-
```

linux-headers-4.4.1-040401_4.4.1-040401.201601311534_all.deb
linux-headers-4.4.1-040401-generic_4.4.1-040401.201601311534_amd64.deb
linux-image-4.4.1-040401-generic_4.4.1-040401.201601311534_amd64.deb

```

I put these into a separate directory/folder to make life easier. Once downloaded, I used the following command to install them...
```
dpkg -i *.deb
```

Obviously don't run that if you have other DEB files within the same directory, as it will install all that it finds.  Hence why I used a new directory.  Of course, you could use the command line tab completion to pick each of the 3 files specifically.

After they were installed, I rebooted, chose 'Advance options for Ubuntu' on GRUB, and made sure I picked the newly installed kernel.  In my case this was at the top of the list anyway, so future boots could just chose the normal 'Ubuntu' option.

There are several issues/tickets on lauchpad about it, everyone affected should add their voice otherwise the developers may think the issue just effects a couple of people and it won't get any priority.

The other thing that worked for me was NOT installing Ubuntu Mate. When running with the main Ubuntu, I don't get the flickering even with kernel 4.4.0-21.  My Dell firmware is 1.0.4 if that makes any difference.

Great thanks for the reply. I did search quite a bit and found the kernel bug tracker. I'll try the kernel you posted and see if that does the trick. I also tried mate last night and it also had the screen flickering.

---

### Post by Javier_Macias-Guar on 2016-04-30
@mick-clarke: I had similar problems with the touchpad and in my case the problem was that the "Disable touchpad while typing" option was not actually working. I guess that it was due to the kernel detecting two devices as the touchpad and it didn't manage to apply the touchpad disabling option properly. 

My solution was blacklisting the i2c-designware-platform as suggested in [http://wiki.yobi.be/wiki/Laptop_Dell_XPS_15#Touchpad](http://wiki.yobi.be/wiki/Laptop_Dell_XPS_15#Touchpad) (just create /etc/modprobe.d/synaptics.conf with "blacklist i2c-designware-platform" in it, reboot and it's done). You will also need to tell your system to active the "Disable touchpad while typing" option (for example running "/usr/bin/syndaemon -i 1 -K -d", or using the config tool from your desktop).

Hope it helps!

---

### Post by dave0109 on 2016-04-30
> **sze5003 said:**
> I also tried mate last night and it also had the screen flickering.
Interesting. So which 'buntu flavour were you getting the flickering on before trying Mate?  That's the only DE version that I saw it on.

---

### Post by michele20 on 2016-04-30
Just wanted to share my experience and ask some questions.

Yesterday I installed Ubuntu Gnome 16.04. The kernel installed was: 4.4.0-21 (I did not manually updated to a new kernel)

In additional drivers, I tried nvidia-361.42 and at the reboot I got only black screen. Uninstalled.

Installed nvidia-364.19
```

sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt-get update
sudo apt-get install nvidia-364

```

It works fine. In the nvidia-settings I'm using the Intel (power save) mode. It works fine but I'm getting definitely less battery life (5hr to respect to 8hr of Windows)

Now I'm wondering if I should install the Intel drivers. I see different comments in this thread about those drivers. Any suggestions?

---

### Post by sze5003 on 2016-05-01
> **dave0109 said:**
> Interesting. So which 'buntu flavour were you getting the flickering on before trying Mate?  That's the only DE version that I saw it on.

I had it on the stock ubuntu 16.04. Once I went into installing the 4.4.01 kernel that you mentioned the flickering went away. I haven't noticed it since. I am also using 361 nvidia proprietary drivers.

> **michele20 said:**
> Just wanted to share my experience and ask some questions.

Yesterday I installed Ubuntu Gnome 16.04. The kernel installed was: 4.4.0-21 (I did not manually updated to a new kernel)

In additional drivers, I tried nvidia-361.42 and at the reboot I got only black screen. Uninstalled.

Installed nvidia-364.19
```

sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt-get update
sudo apt-get install nvidia-364

```

It works fine. In the nvidia-settings I'm using the Intel (power save) mode. It works fine but I'm getting definitely less battery life (5hr to respect to 8hr of Windows)

Now I'm wondering if I should install the Intel drivers. I see different comments in this thread about those drivers. Any suggestions?

I tried removing 361 proprietary drivers and installed 364 like you mention and I could only boot to the login screen and supply a password but it would only reload the login screen. As for intel, I would not try to install proprietary intel drivers since others mention that they are buggy. I am using the intel ones that came with the system now and I get about the same battery life as you. To note, I have the FHD xps 15 9550 model with the 256gb pcie and a 1tb mushkin ssd in the second hd slot which is what I use for Ubuntu.

---

### Post by michele20 on 2016-05-01
Few hours after my post, I decided to try installing the Intel Graphic Driver anyway :D. Actually I had no problem. Here a summary of my steps. 

**Model**
XPS 15
FHD
512 SSD
16 RAM

**Linux kernel**
4.4.0-21-generic (the default one)

**Nvidia Driver**
Installed nvidia-361 from additional driver. Black Screen at login. Uninstalled nvidia-361 (--purge).
Installed nvidia-364.19 from ppa (see previous post)
In the nvidia settings prime I selected the Intel (power save)

[B]Intel Graphic Driver
[/B]Downloaded [Intel Graphics Installer for Linux 1.4.0]("https://01.org/linuxgraphics/downloads")
Installed the Installer
Trick the installer with the previous ubuntu version
Installed the driver


The laptop works fine with no issues (at least I haven't noticed yet). I cannot say if is better or worse than without Intel Driver, but now it seems that the fan are working less (at least when I put in energy saver).

---

### Post by sze5003 on 2016-05-01
> **michele20 said:**
> Few hours after my post, I decided to try installing the Intel Graphic Driver anyway :D. Actually I had no problem. Here a summary of my steps. 

**Model**
XPS 15
FHD
512 SSD
16 RAM

**Linux kernel**
4.4.0-21-generic (the default one)

**Nvidia Driver**
Installed nvidia-361 from additional driver. Black Screen at login. Uninstalled nvidia-361 (--purge).
Installed nvidia-364.19 from ppa (see previous post)
In the nvidia settings prime I selected the Intel (power save)

[B]Intel Graphic Driver
[/B]Downloaded [Intel Graphics Installer for Linux 1.4.0]("https://01.org/linuxgraphics/downloads")
Installed the Installer
Trick the installer with the previous ubuntu version
Installed the driver


The laptop works fine with no issues (at least I haven't noticed yet). I cannot say if is better or worse than without Intel Driver, but now it seems that the fan are working less (at least when I put in energy saver).

So I tried to install the intel driver 1.4.0 by tricking the installer and when I click on the .deb file it opens in software center. I click install and nothing happens. If I click install again a small icon appears with a ? in my unity bar and while hovering over it, says waiting to install.. Not sure why it does not work for me.

---

### Post by michele20 on 2016-05-01
That's a bug of the app Software for the installation of third party softwares. It's going to get fixed in these days.

Install using the command line. You can install it using sudo dpkg -i /path/to/deb/file followed by sudo apt-get install -f .

---

### Post by sze5003 on 2016-05-01
Yea it seems it was a bug. I did install it fine using the terminal now. I am not noticing any difference but I do see I have the intel graphics icon as part of an app now. Driver was installed too and I think I only notice fans now when on the nvidia profile or if I switch back and forth too many times.

---

### Post by mick-clarke on 2016-05-02
> **Javier_Macias-Guar said:**
> @mick-clarke: I had similar problems with the touchpad and in my case the problem was that the "Disable touchpad while typing" option was not actually working. I guess that it was due to the kernel detecting two devices as the touchpad and it didn't manage to apply the touchpad disabling option properly. 

My solution was blacklisting the i2c-designware-platform as suggested in [http://wiki.yobi.be/wiki/Laptop_Dell_XPS_15#Touchpad](http://wiki.yobi.be/wiki/Laptop_Dell_XPS_15#Touchpad) (just create /etc/modprobe.d/synaptics.conf with "blacklist i2c-designware-platform" in it, reboot and it's done). You will also need to tell your system to active the "Disable touchpad while typing" option (for example running "/usr/bin/syndaemon -i 1 -K -d", or using the config tool from your desktop).

Hope it helps!

Thanks Javier, I'll give this a go. I'm installing fresh right now with new machine... long story involving red wine...

---

### Post by ph82 on 2016-05-02
I've got this XPS and so far I can't get dual screens working with Nvidia at all - is this impossible? Has anyone got any good leads as to how to fix it?

I'm just about to try nvidia-prime intel'ing but I think i've done this before and it didn't work, i'm running nvidia-364 and really want my dual screen abilities back! Can anyone help?

Although i'm not currently using it for display I also have the dell USB3 dock/hub which has two displaylink HDMI ports on, getting those working would be glorious (i've tried the displaylink drivers with limited success)  but getting my second screen back is the top priority - i'd like to be able to work again!

---

### Post by dave0109 on 2016-05-02
> **sze5003 said:**
> I had it on the stock ubuntu 16.04. Once I went into installing the 4.4.01 kernel that you mentioned the flickering went away. I haven't noticed it since. I am also using 361 nvidia proprietary drivers.
....
To note, I have the FHD xps 15 9550 model with the 256gb pcie and a 1tb mushkin ssd in the second hd slot which is what I use for Ubuntu.

I might have got carried away seeing someone have the "same" issue as me. I actually have the XPS13 with 1080 screen and integrated graphics, so am using the i915 driver. Which given what you've done to resolve it, makes it seem like a kernel issue. Just puzzled why I only see this with Mate and not Unity or XFCE. Perhaps there's something else between the DE and the underlying O/S coming into play.

---

### Post by Merijn_Vogel on 2016-05-03
Since today I experience a problem after doing an update/dist-upgrade cycle. When I select Wi-Fi networks menu on the login screen is says (1) insufficient privileges. However, when logging in, the WiFi starts already working.

After the update I had more problems, amongst others X not starting. That got solved after I did an update-run in MS Windows including applying "Dell updates".

One other issue/experience: After I closed the lid yesterday the machine seemed to power down as should. However, this morning it got out of it's bag piping hot, with half a battery load spent on trying to cool itself... what could have triggered the machine to boot again? No peripherials were attached (not even a mouse receiver).

---

### Post by sze5003 on 2016-05-03
> **dave0109 said:**
> I might have got carried away seeing someone have the "same" issue as me. I actually have the XPS13 with 1080 screen and integrated graphics, so am using the i915 driver. Which given what you've done to resolve it, makes it seem like a kernel issue. Just puzzled why I only see this with Mate and not Unity or XFCE. Perhaps there's something else between the DE and the underlying O/S coming into play.

For me it was the kernel that solved the flickering since I had it on both versions. Does your xps 13 only have intel graphics? I have both a gtx 960m and the Intel 530 card but in Ubuntu I use only Intel. I noticed there was a 1.20 bios update on the Dell site. I updated mine this past weekend. 

> **Merijn_Vogel said:**
> Since today I experience a problem after doing an update/dist-upgrade cycle. When I select Wi-Fi networks menu on the login screen is says (1) insufficient privileges. However, when logging in, the WiFi starts already working.

After the update I had more problems, amongst others X not starting. That got solved after I did an update-run in MS Windows including applying "Dell updates".

One other issue/experience: After I closed the lid yesterday the machine seemed to power down as should. However, this morning it got out of it's bag piping hot, with half a battery load spent on trying to cool itself... what could have triggered the machine to boot again? No peripherials were attached (not even a mouse receiver).

I just checked for updates and didn't see any from Ubuntu. What you are describing about the machine rebooting itself while its supposed to be sleeping happens for Windows users too. There is a thread about this system on the NotebookReview forums and a couple of pages describe the same issue. The latest bios should have corrected that. I rarely put my system to sleep, I always shut it down. There is a weird occassion where I will put it to sleep for an extended period of time and it seems like it turned off. But because it boots so quickly, I can't tell if booting from cold start or resuming.

---

### Post by Merijn_Vogel on 2016-05-04
With a colleague of mine with the same laptop, we discovered that for me NVidia is no longer working, purging and re-install did not work. I'm now on Intel graphics which is fine for now, but I would love to have the full power of NVidia available. NVidia driver installed is 361.
When starting nvidia-settings from console I see:

```

[FONT=courier new]** Message: PRIME: Requires offloading
** Message: PRIME: is it supported? yes

ERROR: nvidia-settings could not find the registry key file. This file should
       have been installed along with this driver at
       /usr/share/nvidia/nvidia-application-profiles-key-documentation. The
       application profiles will continue to work, but values cannot be
       prepopulated or validated, and will not be listed in the help text.
       Please see the README for possible values and descriptions.[/FONT]

```

If I find any solution I'll update this thread.

---

### Post by Merijn_Vogel on 2016-05-04
Experimenting with 364 nvidia driver from the graphics-drivers PPA did not work: had to revert back to 361. Yet, I have Intel graphics only for the moment.

---

### Post by gspe on 2016-05-05
> **Merijn_Vogel said:**
> 
One other issue/experience: After I closed the lid yesterday the machine seemed to power down as should. However, this morning it got out of it's bag piping hot, with half a battery load spent on trying to cool itself... what could have triggered the machine to boot again? No peripherials were attached (not even a mouse receiver).

I have a Precision 5510 that is similar to XPS 9550, the only difference are the video card and the wifi card.

Today I've almost burned my notebook and my backpack, I closed the lid i checked that it went in sleep and I put it in my backpack. After a couple of hours I tried to take it back and the backpack and the notebook but they were incredibly hot, I cant handle the notebook in my hands!!!


Is there someone that has a solution for this auto-boot, auto-resume problem?

---

### Post by betterwithchemistr on 2016-05-05
> **Merijn_Vogel said:**
>  One other issue/experience: After I closed the lid yesterday the machine seemed to power down as should. However, this morning it got out of it's bag piping hot, with half a battery load spent on trying to cool itself... what could have triggered the machine to boot again? No peripherials were attached (not even a mouse receiver).

> **gspe said:**
> I have a Precision 5510 that is similar to XPS 9550, the only difference are the video card and the wifi card.
Today I've almost burned my notebook and my backpack, I closed the lid i checked that it went in sleep and I put it in my backpack. After a couple of hours I tried to take it back and the backpack and the notebook but they were incredibly hot, I cant handle the notebook in my hands!!!
Is there someone that has a solution for this auto-boot, auto-resume problem?

Which version of the BIOS do you have? I had to downgrade the BIOS from 1.2.0 to 1.1.19, because with version 1.2.0 when I reopened the lid after I put the pc in suspension closing the lid, the computer would reboot. It happened both with ubuntu and windows 10.

---

### Post by gspe on 2016-05-06
Hi,
I have 1.2.0 BIOS. I'll give a try to 1.1.19 version.

---

### Post by svenakela on 2016-05-11
> **mick-clarke said:**
> Has anyone had any luck with better performance from the touchpad? I work mostly mobile and need it to perform well, but largely it drives me nuts!

I've spent hours fiddling with the Synaptics settings, but it's not even close to the function when in Windows (that I rarely use)

Any ideas appreciated.


Yes, check the OP and the updates 2016/04/05 and 2016/04/30 about the pad. Everything you need is there.
I am only using some tighter settings and the first part of the keyboard disable and it seems fine to me.
Add following three startup applications and you will have the same settings:

[B]Disable Touch On Write
[/B]Command: /usr/bin/syndaemon -i 1 -K -d

[B]Palm Detect
[/B]xinput set-prop 17 "Synaptics Palm Detection" 1

[B]Palm Detect Config
[/B]xinput set-prop 17 "Synaptics Palm Dimensions" 10, 10

---

### Post by Fer_Martin on 2016-05-11
Thanks a lot for compiling all these resources for us!!! I have also an XPS 15 9550 and somehow managed to get everything working (Ubuntu 15.10), **EXCEPT for the microphone**. Did any of you have to update the [Realtek drivers]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false") to make it work? Could anybody share their configuration?

Here is my [alsa-info.txt]("https://gist.github.com/f3r/9d858a490b5e9dd221f28b3e27f1c7af")" diagnostics report, generated with:

> wget -O alsa-info.sh [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) && chmod +x ./alsa-info.sh && ./alsa-info.sh

Also, there are some problems with the audio jack; When I unplug the headphones, the sound stops and I need to suspend the system for Ubuntu to start playing again :(

Any hints would be super helpful, thanks!!

---

### Post by Javier_Macias-Guar on 2016-05-12
> **Fer_Martin said:**
> Thanks a lot for compiling all these resources for us!!! I have also an XPS 15 9550 and somehow managed to get everything working (Ubuntu 15.10), **EXCEPT for the microphone**. Did any of you have to update the [Realtek drivers]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false") to make it work? Could anybody share their configuration?

Also, there are some problems with the audio jack; When I unplug the headphones, the sound stops and I need to suspend the system for Ubuntu to start playing again :(

Any hints would be super helpful, thanks!!

I'm using 16.04 and the microphone is working properly (I didn't modify the out-of-the-box configuration, nor the drivers). I'm attaching my alsa-info.txt (generated with your command suggestion) in case it helps: [ATTACH]269012[/ATTACH]

---

### Post by belgattitude on 2016-05-17
Just for info for Ubuntu 16.04 Gnome:

 pretty much everything works out of the box following the instructions located on the first post (huge thanks).

But WIFI support (Broadcom BCM43602) made me crazy because of disconnecting signal. 

I've tried pretty much everything to finally end up using an usb wifi dongle.  
 
I've tried to install the bcmwl-kernel-source (sudo apt-get install bcmwl-kernel-source) but since 4.4.0-18, seems to not work, the bug will probably be taken care of soon ([https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1572659](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1572659)). Let's see when it's fixed.

Bluetooth support also is not working. But no problem with touchpad and touchscreen.

For HiDpi users, Skype & Netbeans looks horrible... Switched to Idea with no problem.

Still I love the laptop :)

---

### Post by Jon_Wehrend on 2016-05-19
Both the Broadcom driver and the bluetooth appear to work reliably with Ubuntu 16.10 Gnome. I'm running 4.4.0-22-generic.

---

### Post by jzl003 on 2016-05-24
Sorry for the noob question but the Xps 15 I got has a "1TB 5400RPM Hard Drive + 32GB Solid State Drive". I would like to dual boot with Windows but spend 99% of my time in Linux so would like to have it run off the 32gb ssd. Has anyone here done this with theirs or have any advice? I've done some research but it seems extremely complicated (which is fine but I'm petrified of bricking my new computer). Any advice would be appreciated, thamks

---

### Post by Christoforos_Samar on 2016-05-26
@belgattitude regarding [COLOR=#000000]WIFI support (Broadcom BCM43602)
[/COLOR]
Have you tried the following?

1) Load wifi module (brcmfmac) on boot


sudo nano /etc/modules


Write inside:


brcmfmac


save file and exit.


3) Edit file rc.local in order to unload and reload on boot brcmfmac module


sudo nano /etc/rc.local


and write inside:


sudo modprobe -r brcmfmac
sudo modprobe brcmfmac


save file and exit.



This worked for me...

---

### Post by michele20 on 2016-05-27
Anyone able to activate some touchpad multigestures with additional software?

---

### Post by jzl003 on 2016-06-04
Another noob question (sorry, I really like using Ubuntu but I have only had one daily driver until now): when I change from "Raid On" to "AHCI", windows gets a BSOD. The consensus seems to be to boot into windows safe mode but that option never comes up. The recovery screen doesn't have that option (there is a startup problems diagnostic but even in all of its menus, there is no "safe-mode" option). Does anyone have any advice or similar experiences? 
[edit] I attached the lineage of menu items I followed in pictures, any help is really appreciated

[:edit:] removed unnecessary (and large) photos. See 2 posts down the fix (if the XPS 15 has an SSD cache in addition to the HDD, make sure it's disabled in windows)

[IMG]https://lh3.googleusercontent.com/ptTLw8YO0BFPJPdZ4XRvIBwubukECePuv4WUUZmVpTo6BRlvh6AB5o83y9kTzRsEeD_dIGV_GMX5wEa-qA2cW5lQcoWpRUjGeioN2aU3yCKNEgf3LfpVP4CU3dNoJ5_bMVKiXYiMaquZqDR-h_ywfjjeJ9A7zVHq7x6Yk5b_al5-dzQeMTE0H_9GU_l3vs3tSCip2OSaC2I3EYTONjFhHbtYKOu_vpesLhgGUiLPgTxDHUJlx1znbekIzBvmwNDuuo1QyZmvnIiG3RfZyNMEBjYeaZbmNahA8QysHsZeD_zOmhyyuvoakFGsHUhRufpXB8NPa1vK6YQbqsQny4SDjFc79lNgV61zrzZyT5VfjYPCfEM1-oS3POwv25YslXTM6fmPsFw1hiskuesY-D1s-Mql_SbnfGaM3Fp3rjwmbGre84G6quhfHjynYxm0n1GQhpF-CvGU0SOhS74qSiFvqW0SiIKrmLELs4iz4w3VaHyJ1NU1Qg0xjc7XlcLRmGLNft-A6Bx8cZznB3wOV66Huw0o1_bnzV1nwIeEs7KOGhzLIrMHixTWH1HzAnI2fYvQOrLH5w6QAqSAtVtRa5o8_EFD6xwyPaQ=s924-no[/IMG]

---

### Post by morhook on 2016-06-08
@jzl003 , for fixing your Windows problem, as noted in first post, you need to enable "Safe boot mode" before changing the hard-disk mode on the BIOS.

> 
[COLOR=#000000]4. Get ready for booting windows in Safe mode afterwards:[/COLOR]


[LIST]
[*]Tthis is required to allow successful boot after changing the RAID to AHCI SATA configuration)
[*]While in Windows, WIN+R and execute "msconfig"
[*]Go to "Boot" and select "Safe mode boot". I left "Minimal" selected
[/LIST]


As you have already changed it, you can change it back to RAID to get inside Windows 10, make the aforementioned step and then go forward again.

Good luck and Godspeed!

---

### Post by jzl003 on 2016-06-08
Thanks!

The problem I was having was that, unlike the OP, I had the model with a 1TB HDD and a 32 GB SSD as a cache. The fix is to go into the intel RST settings and disable the SSD (it seems so obvious now but across most of the guides online, this is never mentioned and I didn't think about it). Then the switch to AHCI works with the safe boot and everything is fine. The Ubuntu system installed perfectly. I still would like to utilize the SSD and might get around to using bcache but the HDD is fine for now

Sorry for not editing my post, I just figured the cache part out and I didn't have a chance to make the edit.

---

### Post by crazybear on 2016-06-11
Was planning on getting this laptop - but before I do two questions:
1] Have people had success generally with font scaling on the 4K screen?
2] Most of  you see to be using a dual boot with Win 10 - which I consider spyware so will NOT use. Has anyone tried Win 7? Does it have or can one get the windows drivers needed for this modern hardware using Win 7?
Thanks

---

### Post by S4boteur on 2016-06-11
1) Definite success, my only unresolved issue is with Photoshop CC in Wine.

GRUB: check OP, or my post in this thread ([http://ubuntuforums.org/showthread.php?t=2317843&p=13473605#post13473605](http://ubuntuforums.org/showthread.php?t=2317843&p=13473605#post13473605) - swapped 9530 to 9550 since then)
Spotify: you can zoom: Ctrl - Shift - +

[ATTACH=CONFIG]269529[/ATTACH]

---

### Post by morhook on 2016-06-13
I've just installed Ubuntu 16.04 on a Dell XPS 15 9550 (i7-6700HQ - 512GB SSD - UHD 4k touch - 16GB RAM) following mostly the guide. Thanks a lot to everyone for sharing!!
I've used gparted to resize the windows partition and that went smooth.

I could turn on Secure Boot after installing. I think everything is working, but the only caveat with that is that for installing third-party-drivers a 'secure boot password' has to be entered.

I could install the driver nvidia-361.45.11 from the mentioned ppa, only when disabling the Secure Boot of the machine.

So far, I'm very happy with the performance and using unity with the Scaling factor (in System Settings -> Displays -> Scale for menu and title bars -> 3.62) :D:):popcorn: @crazybear

Added bluetooth missing driver BCM-0a5c-6410.hd as mentioned by OP, that worked fine also. Found the bluetooth bug was reported in [launchpad ]("https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/1589889")

edit: I've got two commands to restart the wifi (as after suspend it might show the wrong icon, or not connect):

```

sudo modprobe -r brcmfmac && sudo modprobe brcmfmac
#  and
sudo service network-manager restart

```

Edit2: the wifi always connect after suspend. It's just the wrong icon showing in my case

---

### Post by wundbread on 2016-06-16
I'm having difficulty getting the nvidia drivers to work at all.  I've tried 361, 364, and 367, but in every case when I use the nvidia driver (in nvidia-settings or prime-select nvidia) I don't get a login screen, and have to prime-select back to intel.  

Am I missing something?

---

### Post by morhook on 2016-06-16
> **wundbread said:**
> I'm having difficulty getting the nvidia drivers to work at all.  I've tried 361, 364, and 367, but in every case when I use the nvidia driver (in nvidia-settings or prime-select nvidia) I don't get a login screen, and have to prime-select back to intel.  

Am I missing something?

Have you tried to install from command line and with secure boot off? Are you using kernel 4.7? It has a problem compiling code of the driver

---

### Post by huaba-net on 2016-06-17
The new nvidia-367 from Graphics-Drivers Team fix the freeze on boot with connected HDMI display. Tested on Intel with nvidia-prime.

---

### Post by ocn3 on 2016-06-19
> **huaba-net said:**
> The new nvidia-367 from Graphics-Drivers Team fix the freeze on boot with connected HDMI display. Tested on Intel with nvidia-prime.


This means Intel drivers are in use, right ?


I have this problem with nvidia drivers not working with an external monitor (ubuntu gnome 16.04 w/ 4.4.0-24 kernel). They are stable working with internal monitor, but result in a blank screen when an external monitor plugged in (via HDMI or USB-C VGA/HDMI). I tried 364.19 and 367.27.


Intel drivers (1.4.0) worked fine with external monitor but were pretty unstable, caused reboots every now and then even w/o external monitor and nvidia drivers installed.


Has anyone had any luck so far to make nvidia work with an external monitor ?


cheers

---

### Post by morhook on 2016-06-20
> **ocn3 said:**
> This means Intel drivers are in use, right ?


I have this problem with nvidia drivers not working with an external monitor (ubuntu gnome 16.04 w/ 4.4.0-24 kernel). They are stable working with internal monitor, but result in a blank screen when an external monitor plugged in (via HDMI or USB-C VGA/HDMI). I tried 364.19 and 367.27.


Intel drivers (1.4.0) worked fine with external monitor but were pretty unstable, caused reboots every now and then even w/o external monitor and nvidia drivers installed.


Has anyone had any luck so far to make nvidia work with an external monitor ?


cheers

Here with 361.45.11-0ubuntu0~gpu16.04.1 I'm able to connect an external HDMI monitor correctly (Unity - Ubuntu 16.04 w/ 4.4.0-24 kernel). With ```
sudo prime-select nvidia
``` and with ```
sudo prime-select intel
```

The problem on boot still happens though (I have to connect my external monitor when already booted with nvidia driver selected)

---

### Post by sergio62 on 2016-06-22
Working here with kernel 4.4.0-24 and nvidia 364 only the internal screen.

When I try to connect my external monitor using HDMI port (not usb-c), then the external monitor does not show anything, and the notebook screen is also blank, painting sometime the mouse.

I was thinking in testing the latest kernel 4.6.2, but I read that there are also problems.

With nvidia 361 the X does not start, and the same with 367.

Ah, I am using ubuntu16.04 gnome desktop.

---

### Post by sergio62 on 2016-06-23
Could be differences between using directly the HDMI port or using the HDMI port of a docking station through USB-C?

---

### Post by huaba-net on 2016-06-24
Ok, im using Nvidia-367, no Intel driver 1.4.0 installed, kernel 4.4.0-24 and directly HDMI connected display. Intel is set in Nvidia-Prime.

Boot and login with connected HDMI display works fine.

---

### Post by sergio62 on 2016-06-24
I only achieved to use external HDMI with intel driver. 
For extend the desktop to the secondary monitor, I use "xrandr", but the graphics have less quality. For use only the secondary screen as primary, I disable the notebook screen and works fine.

---

### Post by rvanderwerf on 2016-06-25
hows bluetooth working for everyone? I cannot get it to work at all on any kernel (4.4.0, 4.4.8, 4.7-rc4) with symptoms here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1593477](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1593477) I even tried the hcd file in the bug in firmware directory but no luck....

---

### Post by ocn3 on 2016-06-26
> **huaba-net said:**
> Ok, im using Nvidia-367, no Intel driver 1.4.0 installed, kernel 4.4.0-24 and directly HDMI connected display. Intel is set in Nvidia-Prime.

Boot and login with connected HDMI display works fine.

Thanks **huaba-net**, I finally realised that nvidia drivers can use Intel GPU w/o Intel (1.4.0) drivers installed. So I decided to give it a try on this weekend on my working machine and removed 1.4.0 completely in hope that nvidia drivers will be more stable with Intel GPU. 

Unfortunately, it didn't change anything. I removed Intel drivers (1.4.0), then removed and reinstalled nvidia drivers (367), then had to reinstall the whole OS entirely as after removing intel drivers it started to complain about "System Errors" all the time.

So I ended up with the same result. Intel GPU on nvidia drivers (367) works with external display but it's unstable and crashes the OS every now and then. Nvidia GPU is stable with nvidia drivers, but doesn't work with external display. It's a kind of a real problem when you need to share your display for a talk/demo...

---

### Post by Javier_Macias-Guar on 2016-07-04
> **michele20 said:**
> Anyone able to activate some touchpad multigestures with additional software?

What multigestures are you referring to? I have working out of the box:


[LIST]
[*]Double tap -> right click
[*]Triple tap -> middle click
[*]Horizontal and vertical displacement with two fingers
[/LIST]
 
  I'm usinng cinamon (don't know if this is relevant).

---

### Post by bertusrex on 2016-07-06
> **rvanderwerf said:**
> hows bluetooth working for everyone? I  cannot get it to work at all on any kernel (4.4.0, 4.4.8, 4.7-rc4) with  symptoms here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1593477](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1593477) I even tried the hcd file in the bug in firmware directory but no luck....

Bluetooth has been fine with me for several 4.4/4.6/4.7rc kernel versions. Currently I'm using revision 481 of the firmware file (but others worked too): hex2hcd'd from BCM20703A1_001.001.005.0214.0481.hex. I've attached it with the correct filename to put in /lib/firmware/brcm.

Make sure permissons/ownership are correct:
```

-rw-r--r-- 1 root root 54734 may 19 21:22 /lib/firmware/brcm/BCM-0a5c-6410.hcd
```

dmesg should show something like this:
```

[ 6828.577574] Bluetooth: hci0: BCM (001.001.005) build 0481
```

---

### Post by bertusrex on 2016-07-06
New BIOS version 1.2.10 available for XPS 15 9550

Fixes/changes:
1.Fixed Dell Thunderbolt Dock (TB15) device will lost after S3 resume
2.Fixed LCD flickering when in lowest brightness
3.Fixed After McAfee encrypted, the PCIE NVMe SSD \ SATA SSD can't boot to OS issue
4.Fixed Wake on WLAN takes a long time with Intel 1830/1820A Wireless card
5.Fixed USB audio/mouse may be lag while connected to Dell Thunderbolt Dock (TB15) and Dell Dock (WD15)
6.Support for Windows 10 Enterprise features
7.Fixed incorrect Thunderbolt security level reading from Driver
8.Fixed Touchpad may be lost after Dell Thunderbolt Dock (TB15) device connected
9. Add passthrough MAC address shows on BIOS Setup feature.
10.Fixed System will become shut-down with connected to Dell Thunderbolt Dock (TB15) after S4 Resume.

Download [here]("http://www.dell.com/support/home/en/en/endhs1/Drivers/DriversDetails?driverId=96T2K&fileId=3551253765&osCode=WT64A&productCode=xps-15-9550-laptop&languageCode=du&categoryId=BI")

---

### Post by jzl003 on 2016-07-06
My most recent problem is that randomly the touchpad will not move the cursor (it basically stops working). However, if I click and move my finger at the same time then it does work. I figure this is something to do with palm detection gone wrong but I can't seem to fix it. I tried to find anyone with a similar problem but I haven't so far. Any help is appreciated!

---

### Post by morhook on 2016-07-08
I've updated my BIOS with mentioned 01.02.10 and my suspend looks broken. I close the lid (or suspend from the menu) and looks suspended. After trying to un-suspend, the machine seems working (CAPS-LOCK key responds), but nothing appears on the screen. Someone else has this problem?

Edit: confirmed that the problem is just the internal monitor. Connected an external monitor and could access a working system

Edit2: I could unlock the screen! Even on this state pushing the brigthness button up several times turned on the internal monitor. Only drawback is that the screen seems stuck on most brilliant state. Related to this, after upgrading BIOS, the least-brilliant-state turns off the monitor (obviously, before I suspend where it's stuck on most brilliant state).

---

### Post by betterwithchemistr on 2016-07-09
> **morhook said:**
> I've updated my BIOS with mentioned 01.02.10 and my suspend looks broken. I close the lid (or suspend from the menu) and looks suspended. After trying to un-suspend, the machine seems working (CAPS-LOCK key responds), but nothing appears on the screen. Someone else has this problem?

Edit: confirmed that the problem is just the internal monitor. Connected an external monitor and could access a working system

It was happening to me too, I had to roll back to 1.1.19.

---

### Post by bertusrex on 2016-07-09
> **morhook said:**
> I've updated my BIOS with mentioned 01.02.10 and my suspend looks broken. I close the lid (or suspend from the menu) and looks suspended. After trying to un-suspend, the machine seems working (CAPS-LOCK key responds), but nothing appears on the screen. Someone else has this problem?

Edit: confirmed that the problem is just the internal monitor. Connected an external monitor and could access a working system

Not happening here, suspend works well with bios 1.2.10 (ok, one minor glitch: bluetooth is not automatically turned back on after resume).

I'm using a newer kernel (4.6.3) though, plus I have a FHD screen which I usually use with i915 instead of nvidia.

---

### Post by camilo0365 on 2016-07-10
Do you have the 1.1.19 BIOS installer? I can't find it in Dell Drivers website. Thanks!

---

### Post by morhook on 2016-07-10
I've downgraded from 1.2.10 to 1.2.0 (where my brightness works ok, even on the BIOS setup a strange effect happened on lowest brightness setting without battery). You can download 1.1.19 from a guy that saved them: [https://drive.google.com/folderview?id=0B-8WtGQ_zS6PeVRjeVF2MHdDb0E&usp=drive_web](https://drive.google.com/folderview?id=0B-8WtGQ_zS6PeVRjeVF2MHdDb0E&usp=drive_web) (looks like 1.1.19 BIOS has been taken away from the Dell site)

Edit: other people with 4K had brigthness problems on lower setting on reddit

---

### Post by matstam on 2016-07-11
Downgrading BIOS firmware to 1.1.19 (from 1.2.10) fixed the restore/suspend black screen, thanks morhook

---

### Post by morhook on 2016-07-11
Have you tried @matstam and @camilo0365 installing 1.2.0? Do you have both 4k displays? That one is working fine in all cases here on my machine (here some people is reporting brightness problems with A10 BIOS 1.2.10 [https://www.reddit.com/r/Dell/comments/4rayuh/dell_xps_15_9550_a10_system_bios_driver_details/?](https://www.reddit.com/r/Dell/comments/4rayuh/dell_xps_15_9550_a10_system_bios_driver_details/?) )

---

### Post by danielh16 on 2016-07-17
Hi everyone, thank you for all of the info on this thread. It has been a great help in setting up my new XPS 15 9550. I set it up following the OP's directions (minus anything for the 4K monitor as I just have the FHD one). 


I have run into an irritating issue with configuring the trackpad:
Synaptics has the TapAndDragGesture enabled by default, which allows you to tap twice and then drag the cursor around the screen as if you are holding down the mouse button and dragging. I don't like this functionality and would like to disable it. I followed the advice at [http://wiki.yobi.be/wiki/Laptop_Dell_XPS_15#Touchpad](http://wiki.yobi.be/wiki/Laptop_Dell_XPS_15#Touchpad) in order to fix the issue of the trackpad being detected more than once, and now I can configure my touchpad with synclient. 


However, when I attempt to disable TapAndDragGesture, instead of fully disabling it, it seems to just limit the amount of time that dragging works when I double tap (I can double tap and drag, but it will only drag for a short amount of time, and then stop dragging and just move the cursor like normal). This is just as irritating, as it still drags for long enough for me to accidentally move tabs around, etc. Does anyone know how I can fully disable this gesture? 


One other question: when changing touchpad configurations using synclient, what is the best way to make these changes last through a reboot? I have found many different ways to do this, and some don't seem to work...


Thanks in advance!

---

### Post by giup2 on 2016-07-18
Hi everyone, and thanks for the interesting job on this thread.
I'm planning to buy this notebook, and i need to use an external monitor with it (Dell u2515h 2560x1440).
Sorry about the question, but, is there a way to have external monitor working (on HDMI or DP), also on booting while the monitor is connected, without freezes or any others problems?

Thanks!

---

### Post by rockorequin on 2016-07-20
> **giup2 said:**
> Hi everyone, and thanks for the interesting job on this thread.
I'm planning to buy this notebook, and i need to use an external monitor with it (Dell u2515h 2560x1440).
Sorry about the question, but, is there a way to have external monitor working (on HDMI or DP), also on booting while the monitor is connected, without freezes or any others problems?

Thanks!

Yes, mine is working completely fine with an external monitor (Dell something-or-other @1920x1080) connected via HDMI.

@morhook: thanks for the heads up on the BIOS and brightness issues. I have the same issues with BIOS 1.2.10 on my 4K screen:

[LIST]
[*]After boot, you only get 13 graduated levels of brightness, and the lowest one turns the laptop screen completely off
[*]After resume, you only get completely off or 100% brightness, which means it often resumes with the laptop screen completely off, and you have to manually set it back to the second highest level before it turns on again
[*]After resume, whenever the screen goes off due to dpms kicking in and you press a key to wake it back up, the laptop screen stays off until you manually set it back to the second highest level
[*]
[/LIST]

But it works correctly with the 1.2.0 BIOS (you get 20 graduated levels of brightness; the screen is still visible at the lowest level; and it works the same before and after resume).

Does anyone know how to report this to Dell?


Btw, the external monitor works correctly with either BIOS.

---

### Post by Javier_Macias-Guar on 2016-07-20
> **giup2 said:**
> Hi everyone, and thanks for the interesting job on this thread.
I'm planning to buy this notebook, and i need to use an external monitor with it (Dell u2515h 2560x1440).
Sorry about the question, but, is there a way to have external monitor working (on HDMI or DP), also on booting while the monitor is connected, without freezes or any others problems?

Thanks!

I'm running Ubuntu 16.04 with 4.6.0-040600-generic, with a Dell UP3216Q monitor at 4K 60Hz with intel card (I have not tested the nvidia yet). Everything works perfectly, even when the monitor is connected on boot. The monitor is connected using a startech USB-C to DP cable ([https://www.startech.com/AV/usb-c-video-adapters/displayport-over-usb-c-to-displayport-adapter~CDP2DPMM6B](https://www.startech.com/AV/usb-c-video-adapters/displayport-over-usb-c-to-displayport-adapter~CDP2DPMM6B)).

Hope it helps.

---

### Post by morhook on 2016-07-25
Someone has reported the brightness 4K problem with Bios 1.2.10 on Dell forum [http://en.community.dell.com/techcenter/os-applications/f/4613/p/19985875/20927410#20927410](http://en.community.dell.com/techcenter/os-applications/f/4613/p/19985875/20927410#20927410)

---

### Post by rockorequin on 2016-08-13
> **morhook said:**
> Someone has reported the brightness 4K problem with Bios 1.2.10 on Dell forum [http://en.community.dell.com/techcenter/os-applications/f/4613/p/19985875/20927410#20927410](http://en.community.dell.com/techcenter/os-applications/f/4613/p/19985875/20927410#20927410)

That post didn't sound very hopeful (they said they had referred it to Canonical, when it's clearly a BIOS regression!) but Dell confirmed to me separately that they are aware of the issue and are "continuing to investigate how to resolve" it.

FYI, I had two other issues in the meantime:

1. The headphones weren't working at all. I fixed this in alsamixer by un-muting the first headphone output (MM was displayed at the bottom of the column; selecting the column and pressing M toggled the mute. Note that it doesn't auto-unmute if you just change the volume). I also get the same problem as others have mentioned, where sometimes it only detects the HDMI audio output; clearing the contents of ~/.config/pulseaudio/ and issueing "pulseaudio -k" fixes this. 

2. The laptop was rebooting on resume (it's really annoying if you lose work that way!). It did almost the same thing in Windows, too - I just got a black screen on resume and CTRL-ALT-DEL did a reboot. I fixed it by changing the BIOS settings (still on 1.2.0 because of the 4K brightness issue). I reset the BIOS settings to default, changed the disk back to AHCI and reconstructed my Ubuntu boot, set POST behaviour back to minimal (or it takes longer to boot), and I also enabled USB recharging during sleep. I suspect that last one might have been the key. The way the laptop was behaving, it was as if it lost its RAM contents during sleep, so maybe the BIOS was disconnecting the battery completely.

---

### Post by betterwithchemistr on 2016-08-25
A new BIOS is available (1.2.13, [http://www.dell.com/support/home/it/it/itdhs1/Drivers/DriversDetails?driverId=CVYFC&fileId=3562904341&osCode=WT64A&productCode=xps-15-9550-laptop&languageCode=it&categoryId=BI](http://www.dell.com/support/home/it/it/itdhs1/Drivers/DriversDetails?driverId=CVYFC&fileId=3562904341&osCode=WT64A&productCode=xps-15-9550-laptop&languageCode=it&categoryId=BI)).
Have anyone already tried it?

---

### Post by bgcngm on 2016-08-29
> **betterwithchemistr said:**
> A new BIOS is available (1.2.13, [http://www.dell.com/support/home/it/it/itdhs1/Drivers/DriversDetails?driverId=CVYFC&fileId=3562904341&osCode=WT64A&productCode=xps-15-9550-laptop&languageCode=it&categoryId=BI](http://www.dell.com/support/home/it/it/itdhs1/Drivers/DriversDetails?driverId=CVYFC&fileId=3562904341&osCode=WT64A&productCode=xps-15-9550-laptop&languageCode=it&categoryId=BI)).
Have anyone already tried it?
Yeah, I did and the brightness issue is still there. :/

---

### Post by betterwithchemistr on 2016-08-30
> **bgcngm said:**
> Yeah, I did and the brightness issue is still there. :/

I don't have the brightness issue (4K display) but the computer still fails on resume (although it seems a bit random... sometimes it fails, sometimes it wakes up normally...) :(

---

### Post by ckam032 on 2016-09-01
Hey guys, I was wondering if there are any tweaks you can do to the intel card? I've been using Nvidia because on intel, animations are choppy in every distro I've tried.

---

### Post by rockorequin on 2016-09-02
> **betterwithchemistr said:**
> I don't have the brightness issue (4K display) but the computer still fails on resume (although it seems a bit random... sometimes it fails, sometimes it wakes up normally...) :(

Just checking, did you try what I mentioned in a post above? I reset the BIOS settings to default, changed the disk back to AHCI and reconstructed my Ubuntu boot, set POST behaviour back to minimal (or it takes longer to boot), and I also enabled USB recharging during sleep. Do you have that last one set?

---

### Post by 2iii7 on 2016-09-02
I have BIOS 1.2.13 on i5 FHD. Problems so far:
When suspending on AC by closing the lid the computer goes to sleep for a sec, then resumes. When suspending from the power menu again the computer suspends and stays suspended and can be resumed. On battery suspend is working fine by closing the lid.
Brightness control has 12 steps on that version.

---

### Post by rockorequin on 2016-09-02
I just tested BIOS 1.2.13 and I still have the brightness problem after resume (there is only 100% brightness or screen off).

Just to clarify an earlier comment I made about about the setting for supplying power during sleep, it's in BIOS System Configuration and it's called USB Powershare (it supplies power even when the PC is off).

---

### Post by betterwithchemistr on 2016-09-02
> **rockorequin said:**
> Just checking, did you try what I mentioned in a post above? I reset the BIOS settings to default, changed the disk back to AHCI and reconstructed my Ubuntu boot, set POST behaviour back to minimal (or it takes longer to boot), and I also enabled USB recharging during sleep. Do you have that last one set?

Hi, I didn't try what you mentioned above, but I have the USB Powershare enabled: the strange thing is that when the PC is turned off or in sleep, if I plug something in the usb port (e.g. the cellphone) it doesn't work. With the previous version of the bios I had (the last one before the 1.2.0 version.. maybe 1.1.19?) it worked.

I'll give a try to what you mentioned above in a few days, I don't have time right now :(

Thank you :)

-- EDIT -- 

Hi, now I tried what you mentioned, I've noticed that:
when I'm on Linux (Ubuntu GNOME) and put the pc to sleep and reopen the lid, the screen remains black, but if I type my password to unlock it and press enter, then when I increase the luminosity (f12 key) the screen turns on, but the luminosity level is stuck to maximum;
when I'm on Windows (Win 10) the pc wakes up normally after I put it in sleep mode (and the luminosity level is not stuck).

Also, USB Powershare is enabled in BIOS, and if I connect via usb the cellphone when the pc is on it starts charging normally, but when I close the lid the phone stops charging (both in linux and windows).

Hope this helps :)

---

### Post by kuscsik on 2016-09-03
I just got my new XPS 15 with the UHD screen. I also experienced the issue with not able to recover from a suspend. The solution for me was to downgrade the BIOS version to 1.2.
In the recent 1.2.3 Dell updated the Suspend/Resume code... which I guess is not Linux friendly.

---

### Post by amit272 on 2016-09-11
Hello guys! Thanks for guide, it really helps.

Does anybody knows what is with sound drivers? Sound is not clear on maximum as it was on preinstalled Windows 10. Somebody have any solution?

---

### Post by ibrkanac on 2016-09-15
Any luck with BIOS 1.2.14 I cant get suspend working, closed lid or power button, also it broke usb-c docking station!?

---

### Post by morhook on 2016-09-18
For fixing the brightness suspend/resume problem looks like there's a solution for Dell Precision 5510 that could be applied on Dell XPS 15 9550. Add the script on /lib/systemd/system-sleep/97fixbacklight (with chmod 755):

```

#!/bin/sh
# From patchwork.freedesktop.org/.../
# and en.community.dell.com/.../19985320
# Suspend Resume fails to restore PWM_GRANUALITY
# Based on script by Tony.Jewell@Cregganna.Com


INTEL_REG=/usr/bin/intel_reg
ADDR="0x000c2000"
SAVE_FILE=/var/lib/systemd/save_intel_reg_pwm_granuality


[ -x "$INTEL_REG" ] || exit 0


case "$1" in
        pre)
        echo "$0: Saving Intel Register PWM_GRANUALITY"
        "$INTEL_REG" read "$ADDR" \
            | (read addr value && echo "$value") \
            >"$SAVE_FILE"
    sync
    ;;
    post)
        value=`cat "$SAVE_FILE" 2>/dev/null`
        if [ -n "$value" ]
        then
            echo "$0: Restoring Intel Register PWM_GRANUALITY $value"
            "$INTEL_REG" write "$ADDR" "$value"
            rm "$SAVE_FILE"
        fi
    ;;
esac

```

The bug was reported on the kernel: [https://bugs.freedesktop.org/show_bug.cgi?id=97486](https://bugs.freedesktop.org/show_bug.cgi?id=97486)
Source of script: [http://en.community.dell.com/techcenter/os-applications/f/4613/p/19985320/20941236#20941236](http://en.community.dell.com/techcenter/os-applications/f/4613/p/19985320/20941236#20941236)

p.s.: I have just tested this with BIOS 01.02.14 ! Only problem is that on lowest brightness setting the monitor turns off all light (you can still see the screen if you turn on a flashlight pointing the monitor though)

---

### Post by mlabieniec on 2016-09-25
> **morhook said:**
> For fixing the brightness suspend/resume problem looks like there's a solution for Dell Precision 5510 that could be applied on Dell XPS 15 9550. Add the script on /lib/systemd/system-sleep/97fixbacklight (with chmod 755):

```

#!/bin/sh
# From patchwork.freedesktop.org/.../
# and en.community.dell.com/.../19985320
# Suspend Resume fails to restore PWM_GRANUALITY
# Based on script by Tony.Jewell@Cregganna.Com


INTEL_REG=/usr/bin/intel_reg
ADDR="0x000c2000"
SAVE_FILE=/var/lib/systemd/save_intel_reg_pwm_granuality


[ -x "$INTEL_REG" ] || exit 0


case "$1" in
        pre)
        echo "$0: Saving Intel Register PWM_GRANUALITY"
        "$INTEL_REG" read "$ADDR" \
            | (read addr value && echo "$value") \
            >"$SAVE_FILE"
    sync
    ;;
    post)
        value=`cat "$SAVE_FILE" 2>/dev/null`
        if [ -n "$value" ]
        then
            echo "$0: Restoring Intel Register PWM_GRANUALITY $value"
            "$INTEL_REG" write "$ADDR" "$value"
            rm "$SAVE_FILE"
        fi
    ;;
esac

```

The bug was reported on the kernel: [https://bugs.freedesktop.org/show_bug.cgi?id=97486](https://bugs.freedesktop.org/show_bug.cgi?id=97486)
Source of script: [http://en.community.dell.com/techcenter/os-applications/f/4613/p/19985320/20941236#20941236](http://en.community.dell.com/techcenter/os-applications/f/4613/p/19985320/20941236#20941236)

p.s.: I have just tested this with BIOS 01.02.14 ! Only problem is that on lowest brightness setting the monitor turns off all light (you can still see the screen if you turn on a flashlight pointing the monitor though)
is
This worked for me on my XPS 15 9550. I originally had to check "Block Sleep" in the bios, which at least made the laptop come back after lid close / power button (technically not suspended though obviously). But adding this script worked after unchecking Block Sleep in bios. Nvidia drivers do not work for me, Intel drivers have been working fine thought. I'm on Ubuntu 16.04 Ubuntu Gnome, no other problems so far, thanks for the great guide.

---

### Post by lordyak on 2016-09-27
Greetings,

Like others have said, the initial guide was fantastic for getting everything set up.  I've got Xenial running with the 4.6.7 kernel on the XPS 15 9550 and using the WD-15 dock.  Firmware is updated to 1.2.14 (laptop shipped with 1.2.12 and would not charge).  So far, so good.

My problem started yesterday, when I got the crazy idea to add a display via the dock.  I'm attempting to add a 4K display over either mini displayport or HDMI on the dock.  When adding the monitor and enabling via the Display menu (either connection), my system experiences a hard freeze.  I've done some research and found this is a common problem, but none of the suggested solutions (Intel drivers, Nvidia drivers, bumblebee, PRIME, etc.) have worked for me.  In my current config, I'm using the nvidia 367.44 drivers from the graphics-drivers ppa with the default Ubuntu drivers for the Intel graphics.  Via nvidia-settings, I'm using Intel graphics.  I can reliably reproduce the freeze with any permutation of drivers and performance profiles.

If I use the on-board HDMI connector, I can add the external display at full 4K resolution, and everything works flawlessly (both via Displays and via xrandr).  

Having played around with xrandr, I've found that I can add the device, but only at 1920x1080.  If I add at the detected 3840x2160 mode: ```
xrandr --output DP1-1 --mode 3840x2160 --right-of eDP1
```

nothing happens.  If I choose 1920x1080, it mounts and works correctly, but at a much-reduced resolution.  

Has anyone else on here had any luck attaching a 4K display via the dock?  If so, what else can I try to get this working?

---

### Post by markdueck-bz on 2016-10-01
I had some of the same problem smentioned here about blank display, and running on bios 1.2.0 because anything later did not work well.  Thanks to this thread, I have it fixed.

kernel:  4.7.6
Bios:    1.2.14

so far suspend and display brightness all work.  Display brightness worked after the above mentioned fixbacklight script. 

I did have this error everytime my kernel updated:
W: Possible missing firmware /lib/firmware/i915/kbl_dmc_ver1.bin for module i915

so I followed this thread:  [http://askubuntu.com/questions/717338/installing-4-4-rc7-kernel-yields-i915-module-not-available](http://askubuntu.com/questions/717338/installing-4-4-rc7-kernel-yields-i915-module-not-available)   and updated the linux_firmware to the latest using this link: 
[http://ubuntu-master.mirror.tudos.de/ubuntu/pool/main/l/linux-firmware/?C=M;O=D](http://ubuntu-master.mirror.tudos.de/ubuntu/pool/main/l/linux-firmware/?C=M;O=D)

I hope that helps some.  And for those still running old BIOS, update and try with the backlight fix script above.  It should work.

---

### Post by edmyloo on 2016-10-05
Hey everyone!

I'm on kernel 4.7 and A6 BIOS (1.2.0) and I'm having trouble getting suspend working correctly. Whenever I suspend, I'll pull out my laptop and it's burning hot since it's been on the whole time and stowed in my backpack.
I'm running Debian Stretch on a model with touch, i5, nvidia graphics, SSD, etc. If anyone has any leads on this, please let me know! :)

Edit: I've also tried with the newest BIOS version and the fixbacklight script above. Same problem with suspend! :(

---

### Post by markdueck-bz on 2016-10-13
hi edmyloo,
what kernel are you on?   I have noticed that my laptop will come on if it gets a hard bump, even though the screen does not open at all.  Does anyone else have this issue?

---

### Post by uptherescotland on 2016-10-13
Hi guys,
As many have said before this thread is amazing. I've got 16.04 up and running on my XPS 15 9550 really quickly thanks to this thread.

However, I'm stuck with an issue relating to the headphones
When I plug them in, it seems they get detected but can't hear anything.
I've checked alsamixer and  [FONT=monospace][COLOR=#000000]pavucontrol and they both detect them. 
In alsamixer when I plug them in the speaker volume gets turned down and the headphone volume is turned up but still no sound through the headphones.

Has anyone had this or has any ideas on how to fix this?
Any help would be greatly appreciated.

Thank you all in advance.
[/COLOR]
[/FONT]

---

### Post by alberink-stampfini on 2016-10-14
> **uptherescotland said:**
> Hi guys,
However, I'm stuck with an issue relating to the headphones
When I plug them in, it seems they get detected but can't hear anything.
I've checked alsamixer and  [FONT=monospace][COLOR=#000000]pavucontrol and they both detect them. 
In alsamixer when I plug them in the speaker volume gets turned down and the headphone volume is turned up but still no sound through the headphones.

Has anyone had this or has any ideas on how to fix this?
Any help would be greatly appreciated.

Thank you all in advance.
[/COLOR]
[/FONT]

Same problem here. Headphone detection is very unreliable or non-existant. Also, if it does work, then unplugging the headphones fails to restore the state. Would love to hear if someone fixed this as well. I have the WD15 docking station as well and the headphone output there is detected reliably. Swithing to that output is not automatic as well, but manual switching works reliably.

I'm running kernel 4.8.0-21 on Ubuntu 16.10 Beta2.

---

### Post by Tazza101 on 2016-10-15
> **uptherescotland said:**
> Hi guys,
As many have said before this thread is amazing. I've got 16.04 up and running on my XPS 15 9550 really quickly thanks to this thread.

However, I'm stuck with an issue relating to the headphones
When I plug them in, it seems they get detected but can't hear anything.
I've checked alsamixer and  [FONT=monospace][COLOR=#000000]pavucontrol and they both detect them. 
In alsamixer when I plug them in the speaker volume gets turned down and the headphone volume is turned up but still no sound through the headphones.

Has anyone had this or has any ideas on how to fix this?
Any help would be greatly appreciated.

Thank you all in advance.
[/COLOR]
[/FONT]
Hello, when I boot into the system I also have the problem of sound not coming out from headphones, even if they are recognize and the volume is up on alsamixer. HOWEVER if I suspend and resume the laptop the problem disappears... so, since I rarely shut down the machine completely, it is a non problem.

A few more updates/questions:

- On the Dell support forum ([http://en.community.dell.com/techcenter/os-applications/f/4613/t/19985875?pi22229=3#20927410](http://en.community.dell.com/techcenter/os-applications/f/4613/t/19985875?pi22229=3#20927410)) someone reports that with kernel [COLOR=#333333][FONT=&quot]4.4.0-42 [/FONT][/COLOR]the backlight problem after resume (which came after a bios update) is no longer present! I am going to upgrade the bios, if the problem is NOT solved I will post an update

-Is anyone experiencing problems with nvidia drivers and strange behavior when taking screenshots? See on askubuntu: 
[https://askubuntu.com/questions/833328/problems-with-running-nvidia-370-driver-with-nvidia-quadro-m1000m-ubuntu-16-04#comment1275779_833328](https://askubuntu.com/questions/833328/problems-with-running-nvidia-370-driver-with-nvidia-quadro-m1000m-ubuntu-16-04#comment1275779_833328) 
[https://askubuntu.com/questions/801378/screenshot-problem-ubuntu-16-04#comment1275771_801378](https://askubuntu.com/questions/801378/screenshot-problem-ubuntu-16-04#comment1275771_801378)

-There will be a new thread now that ubuntu 16.10 is out? anyone tried upgrading?

Thanks to everyone for contributing in making this machine working propertly!  (If only MATLAB & Mathematica developers made a high-DPI GUI my real life problems with the machines would be gone...)

---

### Post by the_person on 2016-10-16
Has anyone else had extreme instability with usb c even after running the following command?

```
sudo sh -c "echo 1 > /sys/bus/pci/rescan"
```

I am on xubuntu 16.04 using the WD15 dock for the laptop and every time I plug it in the system will generally slow down significantly, sometimes it will pop up a notification to switch displays but even when it does the external (display port) will not turn on.  I have tried a few other desktop environments with similar results, LXDE seems to work but unfortunately I don't really like LXDE.  Any help figuring out how to debug this would be greatly appreciated.

edit: uname -a results
Linux Flere 4.4.0-21-generic #37-Ubuntu SMP Mon Apr 18 18:33:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

edit2: found a solution: Install 16.10 and it just works.  Hopefully this works for others who run into the same problem.

---

### Post by mlabieniec on 2016-10-16
Are you having any luck with the nvidia card? I finally got mine to work when I switch with nvidia-prime from intel, but when I reboot or suspend it doesn't come back up :( I do have the intel 3d drivers, but was doing the same thing before...intel isn't the best performance, the nvidia works fantastic ... trying with the updating kernel 4.7.6 to see if that fixes it.

---

### Post by kuscsik on 2016-10-17
Hi,

I thought you may find this useful. On the XPS 15 with the Broadcomm wifi there were couple of power management
issues with the recent Kernels. I built a 4.9rc1 Ubuntu kernel with the default ubuntu config where finally these issues
seems to be solved. I can put the laptop to sleep and battery life is better.  Nvidia drivers work (v370.28).

Here is the link to my binary Kernel:

[http://people.linaro.org/~zoltan.kuscsik/xps15/](http://people.linaro.org/~zoltan.kuscsik/xps15/)

The files with MD5 sum:

ce5740adedc1c810c61e9906a5acc9db  linux-firmware-image-4.9.0-rc1-custom_4.9.0-rc1-custom-5_amd64.deb
cae5763b5a82a34ece389685b64acf1a  linux-headers-4.9.0-rc1-custom_4.9.0-rc1-custom-5_amd64.deb
7c378e6be5215d2d13eb8e7c7fcc4117  linux-image-4.9.0-rc1-custom_4.9.0-rc1-custom-5_amd64.deb
5b8129ce4ed966554665bba9ab1e9efb  linux-libc-dev_4.9.0-rc1-custom-5_amd64.deb

Use it for your own risk.

Zoltan

---

### Post by Tazza101 on 2016-10-21
Thank you kuscik, I didn't try the kernel yet, but anyway it's good to know it's there.

But I was wondering: the regressions in the power management were introduced with kernel 4.8 (i.e. are they present in ubuntu 16.10), or just in the 4.9?

> **kuscsik said:**
> Hi,

I thought you may find this useful. On the XPS 15 with the Broadcomm wifi there were couple of power management
issues with the recent Kernels. I built a 4.9rc1 Ubuntu kernel with the default ubuntu config where finally these issues
seems to be solved. I can put the laptop to sleep and battery life is better.  Nvidia drivers work (v370.28).

Here is the link to my binary Kernel:

[http://people.linaro.org/~zoltan.kuscsik/xps15/](http://people.linaro.org/~zoltan.kuscsik/xps15/)

The files with MD5 sum:

ce5740adedc1c810c61e9906a5acc9db  linux-firmware-image-4.9.0-rc1-custom_4.9.0-rc1-custom-5_amd64.deb
cae5763b5a82a34ece389685b64acf1a  linux-headers-4.9.0-rc1-custom_4.9.0-rc1-custom-5_amd64.deb
7c378e6be5215d2d13eb8e7c7fcc4117  linux-image-4.9.0-rc1-custom_4.9.0-rc1-custom-5_amd64.deb
5b8129ce4ed966554665bba9ab1e9efb  linux-libc-dev_4.9.0-rc1-custom-5_amd64.deb

Use it for your own risk.

Zoltan

---

### Post by edmyloo on 2016-10-23
> **markdueck-bz said:**
> hi edmyloo,
what kernel are you on?   I have noticed that my laptop will come on if it gets a hard bump, even though the screen does not open at all.  Does anyone else have this issue?

I'm on 4.7 but this also happened when I was on 4.6! It's pretty frustrating that I can't just close the lid and shove it in my backpack without it overheating.

---

### Post by matthias.kurz on 2016-11-03
Is the "Gnome flashback" desktop working? Did someone try it? Maybe with the newer Ubuntu 16.10?

---

### Post by Javier_Macias-Guar on 2016-11-03
> **matthias.kurz said:**
> Is the "Gnome flashback" desktop working? Did someone try it? Maybe with the newer Ubuntu 16.10?

I tried (hard) to make it work during my initial attempts with 16.04 (back in March 2016), without success. I didn't attempt to install it since then, but given that I'm not a fan of Unity, I finally tested cinnamon and I'm very happy with it. I first installed the stock version in 16.04, and now I'm running cinnamon 3 (following the instructions at [http://www.webupd8.org/2016/04/how-to-install-cinnamon-30-in-ubuntu.html](http://www.webupd8.org/2016/04/how-to-install-cinnamon-30-in-ubuntu.html)). There should be more recent howtos on this, but it worked for me.
Cinnamon has good support for HiDPI, allows having panel applets (which are important for me) and has additional nice capabilities, being highly customizable too.

Hope it helps!

PS: I'm still running 16.04 with kernel 4.6.0-040600-generic

---

### Post by alberink-stampfini on 2016-11-04
I wanted to report something I hadn't seen before:

On my installation of Ubuntu 16.10, I was looking at my Software Center and found that I got offered an XPS 9550 bios update! I didn't know that this was integrated already in Ubuntu. I had downgraded my BIOS to 1.2.10 and this was the update to 1.2.14. Installed worked without a hitch. Unfortunately, BIOS 1.2.14 still kills the backlight. On 1.2.10 I can bring up the backlight by cranking up the backlight to the max, logging in and setting a register (cumbersome, but it works!), but resuming on BIOS 1.2.14 results in a reboot.

Unfortunately no Changelog is presented when looking at the details, but this was a nice suprise in and of itself.

---

### Post by cleanie on 2016-11-05
@Starlith:
**Thanks** for posting this helpful information. I agree that libinput driver behaves much more natural (on my XPS 15 9550) than the synaptics driver. I just decreased the Accel Speed to 0.01.

---

### Post by astroman3001gt on 2016-11-05
Hi,

Just to confirm, does anyone was able to run the nvidia drivers at high performance?
Hi am using the drivers v370.28 and a kernel of 4.7, but whenever I switch to the high performance setting in nvidia settings, the screen gets black when I logout, and there is no login screen, I always have to select the prime intel to be able to work it.

Any feedback?
Thanks

---

### Post by Javier_Macias-Guar on 2016-11-05
> **astroman3001gt said:**
> Hi,

Just to confirm, does anyone was able to run the nvidia drivers at high performance?
Hi am using the drivers v370.28 and a kernel of 4.7, but whenever I switch to the high performance setting in nvidia settings, the screen gets black when I logout, and there is no login screen, I always have to select the prime intel to be able to work it.

Any feedback?
Thanks

I am running 4.6.0-040600-generic with nvidia-367 and it seem to work. I didn't install nvidia support manually, but was a "side effect" of my installation of CUDA (following instructions at [https://developer.nvidia.com/cuda-downloads](https://developer.nvidia.com/cuda-downloads) and using the deb local file installation). The deb file took care of all packages to install and it worked perfectly. 

Hope it helps and good luck!

PS: If you go for the cuda approach, you may need to first remove all previous nvidia related packages ([http://askubuntu.com/questions/799184/how-can-i-install-cuda-on-ubuntu-16-04](http://askubuntu.com/questions/799184/how-can-i-install-cuda-on-ubuntu-16-04))

---

### Post by astroman3001gt on 2016-11-07
@Javier
Thanks, I tried, but I had the same result.

It is strange that when I use: nvidia-detecter it reports none.

Also whenever I install the driver of nvidia I keep having these warnings:

update-initramfs: Generating /boot/initrd.img-4.7.7-040707-generic
W: Possible missing firmware /lib/firmware/i915/kbl_dmc_ver1.bin for module i915
W: Possible missing firmware /lib/firmware/i915/skl_guc_ver6.bin for module i915

Any ideas how can I find and fix the problem?

---

### Post by Javier_Macias-Guar on 2016-11-07
> **astroman3001gt said:**
> @Javier
Thanks, I tried, but I had the same result.

It is strange that when I use: nvidia-detecter it reports none.

Also whenever I install the driver of nvidia I keep having these warnings:

update-initramfs: Generating /boot/initrd.img-4.7.7-040707-generic
W: Possible missing firmware /lib/firmware/i915/kbl_dmc_ver1.bin for module i915
W: Possible missing firmware /lib/firmware/i915/skl_guc_ver6.bin for module i915

Any ideas how can I find and fix the problem?

[FONT=courier new]nvidia-detector[/FONT] also reports "none" when I'm on Intel.

However, [FONT=courier new]inxi -G[/FONT] reports:

[FONT=courier new]Graphics:  Card-1: Intel Skylake Integrated Graphics
          Card-2: NVIDIA GM107M [GeForce GTX 960M]
   [FONT=courier new]       [/FONT]           Display Server: X.Org 1.18.3 drivers: intel (unloaded: fbdev,vesa)
   [FONT=courier new]       [/FONT]           Resolution: 3840x2160@60.00hz
   [FONT=courier new]       [/FONT]           GLX Renderer: Mesa DRI Intel HD Graphics 530 (Skylake GT2) GLX Version: 3.0 Mesa 11.2.0[/FONT]

Regarding the firmware issues, maybe [http://askubuntu.com/questions/811453/w-possible-missing-firmware-for-module-i915-bpo-when-updating-initramfs](http://askubuntu.com/questions/811453/w-possible-missing-firmware-for-module-i915-bpo-when-updating-initramfs) can help.

Good luck!

---

### Post by astroman3001gt on 2016-11-07
Hi,

Yes indeed, when I do inxi -G, I have the same report.

I will try to solve the firmware issues, but I am not sure if this is the problem. Thanks anyway. If someone have other ideas, please let me know.

---

### Post by astroman3001gt on 2016-11-10
Hi,

Just a bit of more information that might ring a bell in you guys to help me solve the issue.
When I have a second monitor connected with DisplayLink, and I switch the prime for high performance, the secondary monitor works, only the laptop monitor (main display) is not detected.
So I guess the nvidia driver is working correctly. Any ideas on what can be done to detect the main display?

in dmesg I noticed the following:

[   58.536584] vgaarb: this pci device is not a vga device


Thanks in advance

---

### Post by AION2009 on 2016-11-14
Hi everybody!

I just got my new Precision 5510 (mostly same as the XPS15).

My specs are i7-6820HQ, 32GB, 512GB (nvme), Quadro 1000M and FHD display.

I went trough some different Ubuntu versions (and the pre-installed one) and kind of destroyed all of them while trying to install nvidia binary drivers. Yeah, I'm kind of rusty as I have not been dealing with these issues for a while.

But at last I got some luck with 16.10 +nvidia-367 + bumblebee setup and now it is working as expected, like a charm to be more specific ;)

All things work expect I'm having some hard time with the USB-C.

I have this Dell DA200 (and the LAN adapter that came with the laptop) and both inhibit this strange behavior. I have mostly been playing with the DA200 but when ever I try the LAN adapter I run into similar problems.

1. They work as expected when plugged in before or after the OS has started.
2. When the OS goes to sleep, sometimes (mostly of the times) the computer gets woken once with a lock-screen notification "1 Power Notification" and huge error marker. If I try even to move the cursor the notification goes away and no logs (systemlog, kern.log, dmesg, nothings points anything to that direction. Only thing I have been able to pin-point into the same timeframe is odd behavior of the WiFi in the vicinity of the error notification).
3. After this DA200 nor the LAN adapter are recognized. Nothing whatsoever. I try to plug in and out multiple times and nothing fixes them.
4. (This is not too sure about but it seems that  if the I let the computer sleep again at this point it may, something like 1 out of 5 or something, fix the problem)
5. Only reboot is sufficient to fix this.
6. If I left the DA200 plugged in for the reboot the OS will hang or it will throw outright kernel panic. 


Anyone seem any similar behavior? I have the USB-C dock also but haven't yet had time to play with it but I'm kind of waiting to see some similar behavior.

Some information:

```

xxx@xxx:~$ uname -a
Linux xxx 4.8.0-27-generic #29-Ubuntu SMP Thu Oct 20 21:03:13 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

xxx@xxx:~$ cat /etc/*release*
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.10
DISTRIB_CODENAME=yakkety
DISTRIB_DESCRIPTION="Ubuntu 16.10"
NAME="Ubuntu"
VERSION="16.10 (Yakkety Yak)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 16.10"
VERSION_ID="16.10"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="http://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
VERSION_CODENAME=yakkety
UBUNTU_CODENAME=yakkety

xxx@xxx:~$ lsmod |grep dell
dell_led               16384  1
dell_wmi               16384  0
dell_rbtn              16384  0
dell_laptop            20480  0
dell_smbios            16384  3 dell_wmi,dell_led,dell_laptop
dcdbas                 16384  1 dell_smbios
dell_smm_hwmon         16384  0
dell_smo8800           16384  0
wmi                    16384  3 dell_wmi,dell_led,mxm_wmi
sparse_keymap          16384  2 dell_wmi,intel_hid
video                  40960  3 dell_wmi,dell_laptop,i915





```


And for the interested people, the panic :)

[https://goo.gl/photos/NR3hH1YcajxU7Q8X9](https://goo.gl/photos/NR3hH1YcajxU7Q8X9)

Brgs,
Sampo

---

### Post by fmiz on 2016-11-20
Check this for latest bluetooth firmware [https://github.com/winterheart/broadcom-bt-firmware](https://github.com/winterheart/broadcom-bt-firmware)
With a bluetooth mouse the last version does work better (less disconnection, less pointer lag when wifi is transferring data). Note that the file name is different, you have to rename it. (new firmware is [https://github.com/winterheart/broadcom-bt-firmware/blob/master/brcm/BCM20703A1-0a5c-6410.hcd](https://github.com/winterheart/broadcom-bt-firmware/blob/master/brcm/BCM20703A1-0a5c-6410.hcd) )

---

### Post by jmcooper8 on 2016-11-21
You said, "I added file /etc/modprobe.d/synaptics.conf with blacklist i2c-designware-platform". Unfortunately, when I add this, my trackpad almost completely stops working. I'm running Ubuntu 16.10. Curious if anyone else has run into this. without blacklisting, it doesn't seem like any of the other xinput settings are having an affect.

---

### Post by kevinml2 on 2016-11-21
> **markdueck-bz said:**
> 

so I followed this thread:  [http://askubuntu.com/questions/717338/installing-4-4-rc7-kernel-yields-i915-module-not-available](http://askubuntu.com/questions/717338/installing-4-4-rc7-kernel-yields-i915-module-not-available)   and updated the linux_firmware to the latest using this link: 
[http://ubuntu-master.mirror.tudos.de/ubuntu/pool/main/l/linux-firmware/?C=M;O=D](http://ubuntu-master.mirror.tudos.de/ubuntu/pool/main/l/linux-firmware/?C=M;O=D)

I hope that helps some.  And for those still running old BIOS, update and try with the backlight fix script above.  It should work.

That archive mirror should be OK, but for good security habits, it's better directing people to the Intel site itself for files and procedures [https://01.org/linuxgraphics/downloads/sklgucver43](https://01.org/linuxgraphics/downloads/sklgucver43) 
Also, that's just a warning about kaby lake chipset firmware. It really shouldn't be an issue unless you have a kaby lake based computer (e.g. brand new higher end model MB or Laptop purchased very recently).

---

### Post by Tazza101 on 2016-11-27
Thanks for pointing out the new firmware... however I still think the bluetooth is not perfectly working under ubuntu... 
I have a bluetooth mouse which works fine if I stay VERY close to the computer. 
I also have an AmazonBasics Bluetooth Audio Receiver and it's practically unusable, at already 2m from the computer (with my android phone no problem whatsoever).
Blueman shows a very weak connection signal even when they are very close.
Unders windows 10 the situation is much better... so I guess it's a problem of the drivers... anybody experiencing anything similar?

By the way I think I'm going to buy an intel 8260 card and follow these instructions: [URL="http://www.windowscentral.com/upgrade-wifi-dell-xps-15"]http://www.windowscentral.com/upgrade-wifi-dell-xp-15
[/URL](if you buy a xps 15 now there's actually a Killer wireless/bluetooth card not the dell card with the broadcom chip, I think there must be a reason...)
From what I read so far the intel 8260 is the one mounted in the precision 5510 and it should run fine under linux, anybody already did the upgrade?

> **fmiz said:**
> Check this for latest bluetooth firmware [https://github.com/winterheart/broadcom-bt-firmware](https://github.com/winterheart/broadcom-bt-firmware)
With a bluetooth mouse the last version does work better (less disconnection, less pointer lag when wifi is transferring data). Note that the file name is different, you have to rename it. (new firmware is [https://github.com/winterheart/broadcom-bt-firmware/blob/master/brcm/BCM20703A1-0a5c-6410.hcd](https://github.com/winterheart/broadcom-bt-firmware/blob/master/brcm/BCM20703A1-0a5c-6410.hcd) )

---

### Post by bgcngm on 2016-12-02
Dell XPS 15 9550 1.2.16 System BIOS

Anyone tried already? This was released 1 day ago.

---

### Post by farcrats on 2016-12-03
Seaching and searching the net and then i found this. You SAVED my life!  Thank you

---

### Post by betterwithchemistr on 2016-12-04
> **bgcngm said:**
> Dell XPS 15 9550 1.2.16 System BIOS

Anyone tried already? This was released 1 day ago.

I've updated the BIOS yesterday from 1.2.0 to 1.2.16. So far I haven't noticed any problem (no flickering, no problem when waking the computer from sleep, no battery problem...).

:)

---

### Post by rockorequin on 2016-12-04
> **bgcngm said:**
> Dell XPS 15 9550 1.2.16 System BIOS

Anyone tried already? This was released 1 day ago.

I just loaded it, and so far it seems ok except that the lowest brightness setting still turns off the screen completely. But the brightness keys respond quickly, unlike in 1.2.14, and most importantly, brightness works after suspend/resume.

---

### Post by rockorequin on 2016-12-05
@betterwithchemistr - do you have the 4k screen? I have, and I'm still seeing random flickering with BIOS 1.2.16 when the screen brightness is on lower settings.

---

### Post by betterwithchemistr on 2016-12-06
> **rockorequin said:**
> @betterwithchemistr - do you have the 4k screen? I have, and I'm still seeing random flickering with BIOS 1.2.16 when the screen brightness is on lower settings.

Yes, I have the 4K screen but I didn't experience the flickering problem even with previous versions of the BIOS.

---

### Post by superlinguini on 2016-12-06
Hi all,

I'm new to this forum but I've followed the instructions  to dual boot Ubuntu 16.04 LTS on my Dell XPS 15 9550 (1080p, 512gb NVMe,  960m). I'm trying to get hibernate to work on Ubuntu but it's not  working. I've seen that the issue might be using bios version 1.2.10.  Should I upgrade it to 1.2.16? How do the newer bios versions affect  Windows and screen brightness/flickering also? Thanks a ton for any and  all help!

---

### Post by rockorequin on 2016-12-10
> **superlinguini said:**
> Hi all,

I'm new to this forum but I've followed the instructions  to dual boot Ubuntu 16.04 LTS on my Dell XPS 15 9550 (1080p, 512gb NVMe,  960m). I'm trying to get hibernate to work on Ubuntu but it's not  working. I've seen that the issue might be using bios version 1.2.10.  Should I upgrade it to 1.2.16? How do the newer bios versions affect  Windows and screen brightness/flickering also? Thanks a ton for any and  all help!

You can upgrade to 1.2.16 by downloading the executable from the Dell site (eg from [http://www.dell.com/support/home/au/en/aubsd1/product-support/product/xps-15-9550-laptop/drivers](http://www.dell.com/support/home/au/en/aubsd1/product-support/product/xps-15-9550-laptop/drivers) - look for the BIOS driver) and running it (in Windoze).

I think the release notes indicate that fixes since 1.2.0 are mostly for issues with the docking station. IIRC, the first release after 1.2.0 claimed to have a fix for an issue with the screen. However, for me, it's the opposite - 1.2.0 doesn't have a screen flickering issue, but every BIOS since then does. It's a pretty woeful effort. 

I've read that not everyone can see screen flickering - I think it's something to do with persistence of vision, but if can see it, the screen flickering is more obvious at lower brightness settings, and it occurs in both Linux and Windoze. Dell suggests that upgrading the Windoze Intel graphics drivers may fix it, but that won't help the flickering issue in Linux since I'm already running the latest 4.9-rc8 kernel.

Sorry, I can't help with hiberation. I only use suspend-to-RAM, which mostly works except on two separate occasions where the BIOS got itself into a state where suspending and then removing power makes it lose its RAM completely (again, in both Linux and Windoze) and resuming just made it reboot from scratch. I was able to fix this on both occasions by resetting the BIOS settings to default (and then making the appropriate changes so that Ubuntu can boot).

---

### Post by kevinml2 on 2016-12-10
> **rockorequin said:**
> You can upgrade to 1.2.16 by downloading the executable from the Dell site (eg from [http://www.dell.com/support/home/au/en/aubsd1/product-support/product/xps-15-9550-laptop/drivers](http://www.dell.com/support/home/au/en/aubsd1/product-support/product/xps-15-9550-laptop/drivers) - look for the BIOS driver) and running it (in Windoze).

 
You do **not** need Microsoft Windows to update the bios. 
Ubuntu 16.04 and later will automatically notify the user of the new bios and update it upon user approval. 
The "manual" way is to simply use a USB flash drive and the laptop bios screen.

---

### Post by rockorequin on 2016-12-12
> **kevinml2 said:**
> You do **not** need Microsoft Windows to update the bios. 
Ubuntu 16.04 and later will automatically notify the user of the new bios and update it upon user approval. 
The "manual" way is to simply use a USB flash drive and the laptop bios screen.

Hey, that's cool. Could you be more specific about the automatic notification - do I need to set something up (my Ubuntu currently doesn't tell me there's an update available). Also, when you say you can update the BIOS from the BIOS screen, do you mean via a menu item and by loading the exe from Dell?

---

### Post by etherizim on 2016-12-20
> **kevinml2 said:**
> You do **not** need Microsoft Windows to update the bios. 
Ubuntu 16.04 and later will automatically notify the user of the new bios and update it upon user approval. 
The "manual" way is to simply use a USB flash drive and the laptop bios screen.

I am currently running Linux Mint 18.1 (released December 16th, 2016) and the 4.9.0 kernel (released December 11th)I have been trying so dearly to install the latest BIOS.  What steps did you take to install it?  

I am running 1.2.10 and I have tried the 1.2.14 and 1.2.16 BIOS. I have tried the following ways and none were successful. 
Every time I run the update, the it looks as if it is working and the system correctly restarts twice. one to install, one to restart post install, but every time I hit F12 on the second reboot, my BIOS version remains at 1.2.10.  Do I need to reset my BIOS settings to default and then install?

[LIST=1]
[*]Placing the .exe on my /boot/efi/ partition and running it via BIOS Flash
[*]Placing the .exe on a USB and running it via BIOS Flash
[*]Placing the .exe on a FreeDOS USB drive and running via C:XPS~.exe
[/LIST]

Also a new BIOS just got posted as of December 19, 2016: [http://www.dell.com/support/home/us/en/04/product-support/product/xps-15-9550-laptop/drivers?os=biosa](http://www.dell.com/support/home/us/en/04/product-support/product/xps-15-9550-laptop/drivers?os=biosa)

[IMG]http://i.imgur.com/xKkB5uR.png[/IMG]

---

### Post by Tazza101 on 2016-12-30
I just installed the 1.2.18 BIOS, it's highly recommended since it solved a few bugs for me:


1) Since installing 1.2.16 I had a very annoying bug: everytime I was on battery and I suspended my laptop it would actually turn off!!
2) The lowest brightness setting is now available again and it does not turn off the sceen
3) The screen flickering at low brightness seems to be gone (maybe more testing to confirm this)


Bye everyone



> **etherizim said:**
> I am currently running Linux Mint 18.1 (released December 16th, 2016) and the 4.9.0 kernel (released December 11th)I have been trying so dearly to install the latest BIOS.  What steps did you take to install it?  

I am running 1.2.10 and I have tried the 1.2.14 and 1.2.16 BIOS. I have tried the following ways and none were successful. 
Every time I run the update, the it looks as if it is working and the system correctly restarts twice. one to install, one to restart post install, but every time I hit F12 on the second reboot, my BIOS version remains at 1.2.10.  Do I need to reset my BIOS settings to default and then install?

[LIST=1]
[*]Placing the .exe on my /boot/efi/ partition and running it via BIOS Flash
[*]Placing the .exe on a USB and running it via BIOS Flash
[*]Placing the .exe on a FreeDOS USB drive and running via C:XPS~.exe
[/LIST]

Also a new BIOS just got posted as of December 19, 2016: [http://www.dell.com/support/home/us/en/04/product-support/product/xps-15-9550-laptop/drivers?os=biosa](http://www.dell.com/support/home/us/en/04/product-support/product/xps-15-9550-laptop/drivers?os=biosa)

[IMG]http://i.imgur.com/xKkB5uR.png[/IMG]

---

### Post by morhook on 2016-12-30
I could install BIOS 1.2.18 (A16) via the BIOS Flash update (/boot/efi/ directory) and priorly 1.2.16 via Windows. I think the machine of @etherizim might have an issue. Try to reset the BIOS settings, as probably the method is not related with the error of not upgrading.

My low-brightness setting is also fixed here!

---

### Post by rukab on 2017-01-06
The instructions here have worked great. For those still having issues with touchpad, on [page 2 ]("https://ubuntuforums.org/showthread.php?t=2317843&page=2#post_13463968")there is a post to use

```
[COLOR=#000000]*sudo apt-get install xserver-xorg-input-libinput*[/COLOR]
```

the libinput driver works A LOT better than the synaptics one. Try it and you'll see. It solved all touchpad palm sensitivity issues for me.


A different problem that still persists for me is HiDpi scaling for certain apps (Eclipse, Skype etc.). Seems to be java apps but can't quite find a solution. It's a big deal because one of my work tools is built on eclipse and I def need to get it to work.

---

### Post by 7ql6 on 2017-01-08
> **rukab said:**
> the libinput driver works A LOT better than the synaptics one. Try it and you'll see. It solved all touchpad palm sensitivity issues for me.

Thank you. It really solved the palm sensitivity but I also lost the possibility to configure natural scrolling and sensitivity in the unity settings. :(
Also right click with two fingers doesn't work anymore.

---

### Post by jlparsons on 2017-01-09
I've got most things working but can't get around the issue of horizontal artefacts showing during video playback.  This happens on either GPU and on both the laptop screen and attached monitors.  Anyone had the same issue and managed to fix it?

---

### Post by rukab on 2017-01-10
> **7ql6 said:**
> Thank you. It really solved the palm sensitivity but I also lost the possibility to configure natural scrolling and sensitivity in the unity settings. :(
Also right click with two fingers doesn't work anymore.

All those should be configurable. See all options here: [https://www.mankier.com/4/libinput](https://www.mankier.com/4/libinput) and make sure to set up config file as instructed in the [earlier post]("https://ubuntuforums.org/showthread.php?t=2317843&page=2#post_13463968"). For me when i first installed it it defaulted to hard click instead of tap-to-click. Once I enabled tapping click in options then 2 finger right click (tap), and 3 finger middle click (tap) started working fine. FYI I had to restart after setting options.

---

### Post by gpistre on 2017-01-26
Has anyone had problems with pressure sensitivity ?

It is much too sensitive right now (almost seems it detects the tap BEFORE I even touch the touchpad).

The synaptics settings related to this (FingerHigh, FingerLow) have absolutely no effect. libinput doesn't seem to have any settings related to pressure. 

And in the system settings (I use KDE), the pressure sensitivity settings are all greyed out.

Any idea ?

---

### Post by rukab on 2017-01-26
@gpistre I have noticed mine being very sensitive but haven't bothered much to try to fix it. I have a problem often with clicking and dragging. I'm just trying to move the cursor but it will pick up whatever's under it and move it.

---

### Post by 7ql6 on 2017-01-27
Having a Dell XPS 15 9550 with NVIDIA GM107M / GeForce GTX 960M as well.
However, since it's release I upgraded to Ubuntu 16.10 Yakkety Yak.

The old nVidia drivers 361 and 364 aren't available anymore in this release.
Versions 367, 370, 375 and 378 are resulting in a black screen instead login screen.
Did anyone had success running Yakkety with the dedicated nVidia card?
I actually just want a non-hacky solution and I purged and reinstalled a few times.

My module blacklist looks like this now:

[FONT=courier new]# /etc/modprobe.d/blacklist.conf

[/FONT][FONT=courier new]blacklist nouveau[/FONT]
[FONT=courier new]blacklist nvidiafb[/FONT]
[FONT=courier new]blacklist vga16fb[/FONT]
[FONT=courier new]blacklist rivafb[/FONT]
[FONT=courier new]blacklist rivatv[/FONT]
[FONT=courier new]blacklist lbm-nouveau[/FONT]
[FONT=courier new]options nouveau modeset=0[/FONT]
[FONT=courier new]alias nouveau off[/FONT]
[FONT=courier new]alias lbm-nouveau off
[/FONT]
and I also added

[FONT=courier new]GRUB_CMDLINE_LINUX_DEFAULT="acpi_osi=Linux"[/FONT]

to grub config (and updated it of course).

But as you may have guessed: no success so far.

---

### Post by doxapar2 on 2017-02-09
> **jlparsons said:**
> I've got most things working but can't get around the issue of horizontal artefacts showing during video playback.  This happens on either GPU and on both the laptop screen and attached monitors.  Anyone had the same issue and managed to fix it?

I've also got this issue. Overall, video performance is poor.  Using nvidia 378 drivers. Major horizontal tearing, especially when playing movies, etc.

Still looking for a fix..

---

### Post by berget2 on 2017-02-10
i have the 1080p version of the 9550.
and i am so tierd of Windows and Dells pathetic attemt to fix drivers.

yesterday i tried to run ubuntu live from an usb, and everything seams to work but the audio.
the thing is that i am using the Dell wd15 usb type c hub. the monitor, internet, charging, external harddrive work but could not get any audio from the hub.
anyone know a fix?


[COLOR=#212121][FONT=arial]pathetic attempt to fix drivers[/FONT][/COLOR][COLOR=#212121][FONT=arial]pathetic attempt to fix drivers[/FONT][/COLOR][COLOR=#212121][FONT=arial]pathetic attempt to fix drivers[/FONT][/COLOR][COLOR=#212121][FONT=arial]pathetic attempt to fix drivers[/FONT][/COLOR][COLOR=#212121][FONT=arial]pathetic attempt to fix drivers[/FONT][/COLOR][COLOR=#212121][FONT=arial]pathetic attempt to fix drivers[/FONT][/COLOR][COLOR=#212121][FONT=arial]pathetic attempt to fix drivers[/FONT][/COLOR]

---

### Post by berget2 on 2017-02-11
how do i copy the bluetooth firmware? :o

---

### Post by philtysoe on 2017-03-04
Thank you so much for writing this up!  I just followed this to install Fedora on an XPS 15 and it worked a charm :D

---

### Post by jetson23 on 2017-03-05
Hello everyone. First time post here. I have sort of a noob question that I'm hoping someone can help me with. 

First of all, I have a Dell XPS 15 9560 (512 GB SSD/16 GB/non-touch); I know this is a 9550 thread, but I'm thinking the steps should be pretty much the same, and I'm not finding a lot of resources out there for the 9560. If someone knows of any, please link me.

I'm trying to set up dual boot with Windows 10. I am following the instructions in the first post, and everything is going fine until I get to here:

[COLOR=#000000]7. Insert 16.04 USB stick (the one I downloaded dated late february), reboot, and enter BIOS again.[/COLOR]


[LIST]
[*]Go to "General" | "Boot sequence", and move the USB stick entry to the top.
[*]Apply, save eveything, and "Exit" to reboot.
[*]In my system I had "Windows Boot Manager", and then the "THNSN51T02U7 NVMe TOSHIBA 1024GB".
[/LIST]

There may be more than one problem. The first one is that in General | Boot Sequence, I can't move the USB stick entry to the top. In the Boot Sequence pane, there is a checkbox for "Windows Boot Manager", and below that another pane, "Boot List Option". Here UEFI is selected. There is no option to move the USB stick with these selections. When I exit and reboot with these settings, Windows boots, I can't get to the USB boot at all.

If I change the "Boot List Option" pane to select Legacy(instead of UEFI), above in the "Boot Sequence" pane I get a list of boot devices, including "USB Storage Device". If I move that to the top, save and reboot, I get a black screen with an error message that says something like "no boot device available, press any key to reboot."

So I think the two potential problems are:

1. I'm not doing something right or I'm missing something in General | Boot Sequence. 

and/or:

2. Something is wrong with my USB drive or stick. I have tried 2 different USB sticks. All I did was copy the Ubuntu 16.04 ISO onto the USB. I did see information about creating a UEFI USB boot drive with Rufus. I did try that at one point, but I may or may not have had the correct options selected in "Boot Sequence".

Does anyone have an ideas? If the problem is with #1, I'm guessing it's an easy fix that involves carelessness on my part. If it's #2, maybe there's extra steps I need to take with the 9560? 

Thanks in advance.

---

### Post by jetson23 on 2017-03-06
So after browsing some more, I found this thread:

[https://ubuntuforums.org/showthread.php?t=2354727](https://ubuntuforums.org/showthread.php?t=2354727)

I wonder if my problem is with #2 above? I'll to use the info there to create my USB. But I still think it won't be found at boot time. Still looking for help...

---

### Post by f(fanta) on 2017-03-10
Instead of changing the disk mode from RAID to AHCI, consider trying to install Ubuntu server, which comes with support for RAID, and should detect it at installation time. You can then add Unity later.

---

### Post by cleanie on 2017-03-13
After using libinput I switched back to the synaptics driver (more setting options). But with synaptics I have the problem, that **sometimes** a single tap to click is not recognized by the applications. evtest reports correct BTN_TOUCH events, but the applications do **sometimes** not react. Does anyone have an idea what the reason for this is and how to solve this?
```
synclient settings:
    LeftEdge                = 1585
    RightEdge               = 5357
    TopEdge                 = 1446
    BottomEdge              = 4406
    FingerLow               = 25
    FingerHigh              = 30
    MaxTapTime              = 180
    MaxTapMove              = 245
    MaxDoubleTapTime        = 100
    SingleTapTimeout        = 180
    ClickTime               = 0
    EmulateMidButtonTime    = 0
    EmulateTwoFingerMinZ    = 282
    EmulateTwoFingerMinW    = 7
    VertScrollDelta         = 111
    HorizScrollDelta        = 111
    VertEdgeScroll          = 0
    HorizEdgeScroll         = 0
    CornerCoasting          = 0
    VertTwoFingerScroll     = 1
    HorizTwoFingerScroll    = 0
    MinSpeed                = 1
    MaxSpeed                = 1.75
    AccelFactor             = 0.0358809
    TouchpadOff             = 0
    LockedDrags             = 0
    LockedDragTimeout       = 5000
    RTCornerButton          = 2
    RBCornerButton          = 3
    LTCornerButton          = 0
    LBCornerButton          = 0
    TapButton1              = 1
    TapButton2              = 3
    TapButton3              = 0
    ClickFinger1            = 1
    ClickFinger2            = 3
    ClickFinger3            = 0
    CircularScrolling       = 0
    CircScrollDelta         = 0.1
    CircScrollTrigger       = 0
    CircularPad             = 0
    PalmDetect              = 1
    PalmMinWidth            = 10
    PalmMinZ                = 200
    CoastingSpeed           = 20
    CoastingFriction        = 50
    PressureMotionMinZ      = 30
    PressureMotionMaxZ      = 160
    PressureMotionMinFactor = 1
    PressureMotionMaxFactor = 1
    ResolutionDetect        = 1
    GrabEventDevice         = 0
    TapAndDragGesture       = 1
    AreaLeftEdge            = 0
    AreaRightEdge           = 0
    AreaTopEdge             = 0
    AreaBottomEdge          = 0
    HorizHysteresis         = 27
    VertHysteresis          = 27
    ClickPad                = 1
    RightButtonAreaLeft     = 3471
    RightButtonAreaRight    = 0
    RightButtonAreaTop      = 4026
    RightButtonAreaBottom   = 0
    MiddleButtonAreaLeft    = 0
    MiddleButtonAreaRight   = 0
    MiddleButtonAreaTop     = 0
    MiddleButtonAreaBottom  = 0

```
Edit: it seems that deactivating DLL06E4:01 06CB:7A13 Touchpad (via blacklist i2c-designware-platform) was the reason. Using the DLL06E4:01 06CB:7A13 Touchpad works - no tap-to-click problems anymore :-)

---

### Post by mina2 on 2017-03-24
Thanks for the guide! We were struggling to install Ubuntu on the xps and then we found your thread. The details are outstanding, you explain every button. Thanks a lot Javi

---

### Post by micahgalizia on 2017-05-06
Hi,

After upgrading to 17.04 the lack of palm detection was making me insane. The switch to libimput sorted it -- TYVM.

Quick question -- has anyone had any luck with Bluetooth mice? I have the Logitech MX Master and it now pairs and works in 17.04, but its _really_ skippy/inconsistant.  Any suggestions would be greatly appreciated.

---

### Post by morhook on 2017-05-07
I´ve used briefly (one week) a magic mouse from Apple. It worked fine!! I´ve updated to 17.04 too.

---

### Post by astroman3001gt on 2017-06-07
Hi,

Any feedback from upgrading to 17.04, or a fresh install?

Thanks

---

### Post by micahgalizia on 2017-06-08
> **astroman3001gt said:**
> Hi,

Any feedback from upgrading to 17.04, or a fresh install?

Thanks

Upgrade worked fine for me. As posted above, I had to change to the udev mouse to get it to not behave crazy. Otherwise, its pretty much all good.

---

### Post by astroman3001gt on 2017-06-12
> **micahgalizia said:**
> Upgrade worked fine for me. As posted above, I had to change to the udev mouse to get it to not behave crazy. Otherwise, its pretty much all good.

Thanks, I will give it a try in the next weeks.

---

### Post by danielh16 on 2017-07-12
I'm having an issue with suspend in Ubuntu 16.04 with this computer. When I close the lid or suspend using ```
systemctl suspend
``` It sometimes (about half the time) fails to suspend. The screen goes dark as if it is about to suspend, but after about 1 second it flashes back directly to the login screen.

It seems to be related to the wifi card or wifi card driver. Looking at dmesg: 

```
[36421.655649] PM: Syncing filesystems ... done.
[36421.683307] PM: Preparing system for sleep (mem)
[36421.684074] vgaarb: this pci device is not a vga device
[36422.903378] Freezing user space processes ... (elapsed 0.002 seconds) done.
[36422.905434] Freezing remaining freezable tasks ... (elapsed 0.001 seconds) done.
[36422.906683] PM: Suspending system (mem)
[36422.906701] Suspending console(s) (use no_console_suspend to debug)
[COLOR=#ff0000][36426.600844] brcmf_pcie_suspend: Timeout on response for entering D3 substate
[36426.600857] pci_legacy_suspend(): brcmf_pcie_suspend+0x0/0x1b0 [brcmfmac] returns -5
[36426.600862] dpm_run_callback(): pci_pm_suspend+0x0/0x140 returns -5
[36426.600865] PM: Device 0000:02:00.0 failed to suspend async: error -5
[36426.601041] PM: Some devices failed to suspend, or early wake event detected[/COLOR]
[36426.603867] rtc_cmos 00:02: System wakeup disabled by ACPI
[36426.976865] ata2: SATA link down (SStatus 4 SControl 300)
[36427.111569] PM: resume of devices complete after 510.515 msecs
[36427.116048] PM: Finishing wakeup.
```

Has anyone else run into this issue? Through various searches I have found others with seemingly similar issues, but no solutions as of yet have fixed it for me.

---

### Post by WhatAreTheStandards on 2017-07-24
Great instructions.  Thanks!  My XPS 15 is dual-booting like a champ.

---

### Post by telefono on 2017-08-12
> **danielh16 said:**
> I'm having an issue with suspend in Ubuntu 16.04 with this computer. When I close the lid or suspend using ```
systemctl suspend
``` It sometimes (about half the time) fails to suspend. The screen goes dark as if it is about to suspend, but after about 1 second it flashes back directly to the login screen.

It seems to be related to the wifi card or wifi card driver. Looking at dmesg: 

```
[36421.655649] PM: Syncing filesystems ... done.
[36421.683307] PM: Preparing system for sleep (mem)
[36421.684074] vgaarb: this pci device is not a vga device
[36422.903378] Freezing user space processes ... (elapsed 0.002 seconds) done.
[36422.905434] Freezing remaining freezable tasks ... (elapsed 0.001 seconds) done.
[36422.906683] PM: Suspending system (mem)
[36422.906701] Suspending console(s) (use no_console_suspend to debug)
[COLOR=#ff0000][36426.600844] brcmf_pcie_suspend: Timeout on response for entering D3 substate
[36426.600857] pci_legacy_suspend(): brcmf_pcie_suspend+0x0/0x1b0 [brcmfmac] returns -5
[36426.600862] dpm_run_callback(): pci_pm_suspend+0x0/0x140 returns -5
[36426.600865] PM: Device 0000:02:00.0 failed to suspend async: error -5
[36426.601041] PM: Some devices failed to suspend, or early wake event detected[/COLOR]
[36426.603867] rtc_cmos 00:02: System wakeup disabled by ACPI
[36426.976865] ata2: SATA link down (SStatus 4 SControl 300)
[36427.111569] PM: resume of devices complete after 510.515 msecs
[36427.116048] PM: Finishing wakeup.
```

Has anyone else run into this issue? Through various searches I have found others with seemingly similar issues, but no solutions as of yet have fixed it for me.

Hey! I have the same issue when I suspend my computer. What fixed the problem for me (I think, I rebooted a couple of time and it works, but maybe it's not THE FIX):

I upgraded the Kernel on my Ubuntu (I'm using 17.04) and I installed the lastest kernel: [B]Linux 4.12.0-041200-generic

[/B]I did follow this guide: [https://www.tecmint.com/upgrade-kernel-in-ubuntu/](https://www.tecmint.com/upgrade-kernel-in-ubuntu/)

Hope it works for you as well, keep me in the loop. 

Cheers!

---

### Post by jetson23 on 2017-08-17
I'm not sure this is the right thread for this question, but it was very helpful in getting my dual boot XPS 15(Ubuntu/Windows 10) up and running 16.04 so I thought I'd start here.

A few days ago, I ran into an issue where every time I reboot from Ubuntu, I get messages that look like the attached picture, and the restart never completes. I have searched and found a couple potential solutions, here:

[https://www.reddit.com/r/linuxquestions/comments/6929r4/ubuntu_16_wont_shut_down_and_freezes/](https://www.reddit.com/r/linuxquestions/comments/6929r4/ubuntu_16_wont_shut_down_and_freezes/)

and here(linked from above):

[https://www.reddit.com/r/linux4noobs/comments/692ifx/ubuntu_16_wont_shut_down_and_freezes/dh38gqn/](https://www.reddit.com/r/linux4noobs/comments/692ifx/ubuntu_16_wont_shut_down_and_freezes/dh38gqn/)

neither of which worked. In fact, one or both caused serious problems with my Ubuntu partition, I had to boot into recovery mode and undo them as I could not type or use the mouse when booting into Ubuntu.

Any help would be appreciated.

---

### Post by thaisdbraz on 2017-09-17
Hi
Im having issue with a vvveeery loudy  fan
tryied installing i8kutils by then the fan was constantly turning on and off.
after that tryied to update de bios to XPS_15_9560_1.5.0 but it returned to be just loud!!!!
please help

can not stading my pc right now

---

