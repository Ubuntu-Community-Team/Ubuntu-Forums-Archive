---
title: "how to know which nvidia driver to install in 22.04.1 for GeForce GT710 card."
date: 2022-10-17
forum: General Help
---

### Post by Nosphky on 2022-10-17
I had to re-install UbuntuStudio from scratch a few days ago and now I have a graphics problem, I believe. During Zoom meetings (twice today) I lost control of the pc, mouse and keyboard inputs stopped working. I loaded the latest Calibre and it will not display any ebook. 

I had this problem with Calibre when I first installed 22.04.1 in September and Kovid Goyal indicated then that it was a driver problem. I somehow managed at that time to update the driver from 'nouveau' to something else but unfortunately, I wasn't smart enough to record what I did. And now, the problem seems insurmountable. So I'm requesting a bit of help, please.

inxi -GCS shows the following[FONT=monospace][COLOR=#000000]
[/COLOR]
```
  Host:  Kernel: 5.15.0-50-lowlatency x86_64 bits: 64
    Desktop: KDE Plasma 5.24.6 Distro: Ubuntu 22.04.1 LTS (Jammy Jellyfish)
CPU:
  Info: quad core model: Intel Core i5-4440 bits: 64 type: MCP cache:
    L2: 1024 KiB
  Speed (MHz): avg: 1594 min/max: 800/3300 cores: 1: 1336 2: 949 3: 1397
    4: 2696
Graphics:
  Device-1: Intel Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics
    driver: i915 v: kernel
  Device-2: NVIDIA GK208B [GeForce GT 710] driver: nouveau v: kernel
  Device-3: Logitech C922 Pro Stream Webcam type: USB
    driver: snd-usb-audio,uvcvideo
  Display: x11 server: X.Org v: 1.21.1.3 driver: X: loaded: modesetting
    unloaded: fbdev,vesa gpu: nouveau resolution: 1920x1080~60Hz
  OpenGL: renderer: NV106 v: 4.3 Mesa 22.0.5
```

and a search for driver versions on my system shows:
[/FONT]```
[FONT=monospace][COLOR=#ff5454]**nvidia-driver-390**[/COLOR][COLOR=#000000] - NVIDIA driver metapackage [/COLOR]
[COLOR=#ff5454]**nvidia-driver-418**[/COLOR][COLOR=#000000] - Transitional package for nvidia-driver-430 [/COLOR]
[COLOR=#ff5454]**nvidia-driver-418**[/COLOR][COLOR=#000000]-server - NVIDIA Server Driver metapackage [/COLOR]
[COLOR=#ff5454]**nvidia-driver-430**[/COLOR][COLOR=#000000] - Transitional package for nvidia-driver-440 [/COLOR]
[COLOR=#ff5454]**nvidia-driver-450**[/COLOR][COLOR=#000000]-server - NVIDIA Server Driver metapackage [/COLOR]
[COLOR=#ff5454]**nvidia-driver-470**[/COLOR][COLOR=#000000] - NVIDIA driver metapackage [/COLOR]
[COLOR=#ff5454]**nvidia-driver-470**[/COLOR][COLOR=#000000]-server - NVIDIA Server Driver metapackage [/COLOR]
[COLOR=#ff5454]**nvidia-driver-510**[/COLOR][COLOR=#000000] - NVIDIA driver metapackage [/COLOR]
[COLOR=#ff5454]**nvidia-driver-510**[/COLOR][COLOR=#000000]-server - NVIDIA Server Driver metapackage [/COLOR]
[COLOR=#ff5454]**nvidia-driver-435**[/COLOR][COLOR=#000000] - Transitional package for nvidia-driver-455 [/COLOR]
[COLOR=#ff5454]**nvidia-driver-440**[/COLOR][COLOR=#000000] - Transitional package for nvidia-driver-450 [/COLOR]
[COLOR=#ff5454]**nvidia-driver-440**[/COLOR][COLOR=#000000]-server - Transitional package for nvidia-driver-450-server [/COLOR]
[COLOR=#ff5454]**nvidia-driver-450**[/COLOR][COLOR=#000000] - Transitional package for nvidia-driver-460 [/COLOR]
[COLOR=#ff5454]**nvidia-driver-455**[/COLOR][COLOR=#000000] - Transitional package for nvidia-driver-460 [/COLOR]
[COLOR=#ff5454]**nvidia-driver-460**[/COLOR][COLOR=#000000] - Transitional package for nvidia-driver-470 [/COLOR]
[COLOR=#ff5454]**nvidia-driver-460**[/COLOR][COLOR=#000000]-server - Transitional package for nvidia-driver-470-server [/COLOR]
[COLOR=#ff5454]**nvidia-driver-465**[/COLOR][COLOR=#000000] - Transitional package for nvidia-driver-470 [/COLOR]
[COLOR=#ff5454]**nvidia-driver-495**[/COLOR][COLOR=#000000] - Transitional package for nvidia-driver-510 [/COLOR]
[COLOR=#ff5454]**nvidia-driver-515**[/COLOR][COLOR=#000000] - NVIDIA driver metapackage [/COLOR]
[COLOR=#ff5454]**nvidia-driver-515**[/COLOR][COLOR=#000000]-open - NVIDIA driver (open kernel) metapackage [/COLOR]
[COLOR=#ff5454]**nvidia-driver-515**[/COLOR][COLOR=#000000]-server - NVIDIA Server Driver metapackage[/COLOR][/FONT]
```
[FONT=monospace] 
So how do I know which nvidia-driver-xxx package to use and how do I get the system to ignore the 'nouveau' driver and use that nvidia driver?
[/FONT]

---

### Post by TheFu on 2022-10-17
If you find the "additional drivers" menu option, it should have the one for your card at the top.

From a non-GUI setup/terminal, I use 
```
sudo ubuntu-drivers autoinstall
```
but I think they removed the "autoinstall" option in 22.04. No idea why. It always worked for me.

Nvidia does drop support for older cards from time to time, so if you need/want to keep using the proprietary nvidia driver, at some point, you'll need to buy a new GPU. I don't think that happened with the 7xx series yet.  I just checked any my older GT 430 is supported still with the 390 driver (updated August 2022).

Looks like the GT 710 should be using  470.xxx.xx drivers. Pick the latest one through the ubuntu-drivers or GUI.  Don't grab them from nvidia directly.  That method leads to anger, hate, then suffering.

> "Fear is the path to the dark side. Fear leads to anger. Anger leads to hate. Hate leads to suffering." - Master Yoda

---

### Post by Nosphky on 2022-10-18
Hi TheFu

> If you find the "additional drivers" menu option, it should have the one for your card at the top.

I used to be able to find "additional drivers" in the previous UbuntuStudio 20.04 Xfce set up but with KDE Plasma, I can't find it. The equivalent application handling software seems to be 'Discover' and it does list software sources but it doesn't appear to have any 'additional drivers' entry.

If I install the 470.xxx.xx drivers, will the system automatically use them rather than the 'nouveau' driver which the clean installation picked?

---

### Post by TheFu on 2022-10-18
I haven't used KDE since 2000-ish and don't have 22.04 on any physical systems here, so I don't have first-hand knowledge.  

Try it.  See if nvidia shows up in the list of kernel modules after reboot.  Changing video drivers are one of the few times a reboot is mandated.   To see kernel modules that are loaded, use lsmod.  It will look something like this:
```
$ lsmod |grep nvid
nvidia_uvm           1003520  0
nvidia_drm             57344  4
nvidia_modeset       1200128  9 nvidia_drm
nvidia              35418112  534 nvidia_uvm,nvidia_modeset
drm_kms_helper        184320  1 nvidia_drm
drm                   495616  8 drm_kms_helper,nvidia,nvidia_drm
```
If there isn't **any** nvidia in that output, then it didn't work and 1 more step is needed. If there are, they are being used, as hoped.  I think the driver install handles the extra step automatically. Always has here.

---

### Post by Nosphky on 2022-10-18
Well, it looks like autoinstall is included in 22.04.1. I just did 
          ```
sudo ubuntu-drivers autoinstall
```
and the machine launched into 5 minutes of downloading etc and then another 2 or 3 minutes of unpacking etc before announcing it was done. I saw lots of *-nvidia-*-470 stuff whizzing by so felt quite encouraged. When it was finished, I quit all open applications (Firefox and the terminal) and used the launcher to 'restart'.

The dialogue announced that restart would be in 30 seconds so I clicked ok and all appeared normal - except that a minute or so later I was looking at the Gigabyte splash screen for what seemed like rather a long time, expecting to see a Gigabyte/UbuntuStudio splash screen take its place. But no !  After a couple of minutes, my screen said 'no signal'. I tried a few times to reboot - even going into the boot settings - but the box is bricked.

I'm on my standby Windows 10 box at the moment. My linux box is back where I found myself about 10 days ago when I had this same inability to boot. At that time, I had been using 22.04.1 with KDE Plasma with an nvidia driver for several weeks in a very satisfactory manner until one morning it wouldn't start.

So about 10 days ago, I reloaded 22.04.1 from a live usb and spent the past week getting things re-installed and the way I liked them. The KDE Plasma installation took a little longer to boot than the 20.04 Xfce UbuntuStudio but not seriously longer. I got used to the little differences - you can get used to anything - but I never really saw any advantage to me in using KDE Plasma and often wondered why the developers saw an advantage in going that way.

Looks like I'm going to have to make another clean install but maybe I'll go Xubuntu this time.  Unless someone has some magic to get the linux box booted.

---

### Post by TheFu on 2022-10-18
So ... if I'm reading and understanding correctly, the latest drivers are a problem for your specific nvidia GPU.  Maybe try the prior driver?
Also, if you are seeing a black screen, there are "black screen" troubleshooting web pages with things to try.
[https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen](https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen)

Another consideration in 22.04 is that nvidia is poorly supported using Wayland, so always use X/Windows, not Wayland. In theory, any desktop that sees an Nvidia GPU use not use Wayland, but who knows on your system? Something else to check.  The release notes go into more known issues and are always worth reading.

---

### Post by Nosphky on 2022-10-18
No - I'm not getting a blank screen - it's just not booting past the mother board's splash screen. 

Somewhere in the system dumps I looked at when investigating my video card, I saw mention of Wayland. But that's way beyond my pay grade - I don't even know what Wayland is let alone whether I have a choice of something else nor at which stage I would make that choice. 

My hardware has been without a problem all through 18.04 and 20.04 so I was hoping it would continue ok thro 22.04. Perhaps I shall try and reinstall 20.04 and see if that still works ok and if not, then maybe some new hardware is called for.

---

### Post by Nosphky on 2022-10-18
No - I'm not getting a blank screen - it's just not booting past the mother board's splash screen. 

Somewhere in the system dumps I looked at when investigating my video card, I saw mention of Wayland. But that's way beyond my pay grade - I don't even know what Wayland is let alone whether I have a choice of something else nor at which stage I would make that choice. 

My hardware has been without a problem all through 18.04 and 20.04 so I was hoping it would continue ok thro 22.04. Perhaps I shall try and reinstall 20.04 and see if that still works ok and if not, then maybe some new hardware is called for.

EDIT ....
I've been seeking out some info about Wayland and I see that it is a display or window/compositor server which is now standard in 22.04. I also see that X11 is an older alternative. Trouble is, I don't ever recall having been asked to make a choice during installation and I don't recall having ever seen any setting which gave me the choice once the distro had been installed.

If, as you mention, Wayland doesn't play too nicely with nvidia cards, maybe I could retry another installtion of 22.04.1 but using X11 instead of Wayland. How would I make / implement that choice?

---

### Post by TheFu on 2022-10-18
> **Nosphky said:**
>  
EDIT ....
I've been seeking out some info about Wayland and I see that it is a display or window/compositor server which is now standard in 22.04. I also see that X11 is an older alternative. Trouble is, I don't ever recall having been asked to make a choice during installation and I don't recall having ever seen any setting which gave me the choice once the distro had been installed.

X11 isn't just older, but it is 40 yrs old AND proven.  You've been using it with any graphical Unix/Linux all this time.  Canonical has tried to make Wayland the default a few times before and failed going back to 2017.  In 22.04, they tried again and it seems to work ok for people with AMD GPUs, but to good for people with nvidia GPUs.

You can search for how to choose it on the login screen. It isn't an "installation" choice.  It is one of those things that is easy to show, but harder to explain in text.  I'd look for a youtube video about choosing Xorg at login, not wayland.  15 seconds watching any of those videos will clarify.

---

### Post by Nosphky on 2022-10-19
> **TheFu said:**
> X11 isn't just older, but it is 40 yrs old AND proven.  You've been using it with any graphical Unix/Linux all this time.  Canonical has tried to make Wayland the default a few times before and failed going back to 2017.  In 22.04, they tried again and it seems to work ok for people with AMD GPUs, but to good for people with nvidia GPUs.

You can search for how to choose it on the login screen. It isn't an "installation" choice.  It is one of those things that is easy to show, but harder to explain in text.  I'd look for a youtube video about choosing Xorg at login, not wayland.  15 seconds watching any of those videos will clarify.

Thanks for that. I'll do a bit more research and then maybe give the 22.04.1 with KDE Plasma another shot.  Although I don't mind using a terminal, I'm quite content to have a gui for interfacing with settings. I really just want to boot up and start work, not really being fascinated by stuff like Wayland (which I never heard of before) and X11.

We'll see what happens with my next attempt. In the meantime, thank goodness for my standby W10 box. I'll have to move up to W11 sooner or later but I'm not fascinated either by the promise of updated icons.

---

### Post by TheFu on 2022-10-19
I have a few spare microSD cards with an Ubuntu-Mate ISO on them. That's what I boot for emergency use.  

I think Lubuntu and Xubuntu don't ship with Wayland at all, so either ISO would be a good fallback too.  Plus, if you setup a multi-boot flash drive with something like Ventoy, you can just drop almost any ISO into a specific partition of the flash storage and boot it on any x86-64 system, anywhere.  After all, I need this as part of my restore process for when a HDD/SSD boot device fails and for troubleshooting hardware.

Almost any USB flash drive should work, but I stopped buying anything but microSD years ago and use cheap adapters for either SDHC (cameras) or USB3.2 adapters when the microSD storage as needed in a different physical device mostly they are used in tablets, phones or raspberry pi computers around there.

I've never touched Win10, much less Win11 or Win8.  I have an old Win7 system inside a virtual machine running Quicken from 2013 that gets used for taxes and personal finance and investment tracking.  I'm still looking for Linux replacements for those 2 needs, but don't expect anything at the current popularity of Linux desktops for a long time. That's fine.  That same Win7 virtual machine has been relocated a number of times to new hardware and it didn't know the difference. It hasn't been patched since MSFT changed the EULA when the Win10 alpha was released . nearly a decade ago. No new software has been installed on it since around 2012.  **I really dislike the terms in the MSFT EULA.** Fortunately, I'm in a position that doesn't mandate using anything new from that company anymore and don't expect to ever touch their stuff again. NEVER.  I refuse to use exFAT, for example and try to get Android devices that support f2fs on the microSD storage. Takes extra research and some extra compromises. These are certainly 1st world issues compared to 90% of the world.  Not giving MSFT 1 more penny is a jihad (as in holy quest) of mine.

---

### Post by Nosphky on 2022-10-19
I've checked on YouTube and Google and as you suggested there's lots of  stuff and I've learned quite a bit but I'm no further along. Most advice  about selected X11 rather than Wayland are all about Gnome ; on the  login prompt/screen, select Xas the option - I don't see any options.  101 advices on editing /etc/gdm3/custom.conf to set WaylandEnable to  false.  problem is, the KDE Plasma desktop installation does not have an  /etc/gdm3/ directory.

I found reference to KDE using a Simple  Display Manager SDDM and I found an /etc/sddm/ which contains a couple  of scripts - 1 wayland-session and the other xsession. But I don't find  what makes the choice and calls one script or the other. These two  scripts anyway only appear to set up various shells.

I have found  lots of stuff complaining about the poor performance of nvidia graphics  cards under Wayland - some blame linux for introducing Wayland before  it's ready and others blame nvidia for not keeping up. It's a real pita  for a simple user but I haven't found out a clear instruction for  forcing KDE Plasma to use X.

I've exhausted my time available today, unfortunately.

---

### Post by TheFu on 2022-10-19
There are lots of opinions about Wayland vs Xorg (X/Windows).  I have some too, tainted by my workflows which Wayland doesn't support.

Maybe a KDE guru will come in and make suggestions for your needs?  I can't.  

I'm doing what I can to remove nvidia hardware from my systems when it makes sense.  I've had enough hassles.  If I was spending $600+ on a GPU, perhaps nvidia would make sense.  My goal is to have the minimal GPU necessary - i.e. the cheapest, that "just works".  Today, those are AMD iGPUs included with Ryzen APUs like the 5600G.  I was a long-time nvidia user for the last 20 yrs.  AMD wasn't always easy either, so we were stuck with iGPUs included with Intel CPUs.  there were fine until video editing became important. Waiting 5 seconds for a screen refresh isn't good.

But we all have different requirements. Running a GT 710 says your needs and mine are likely similar. That's the only reason I posted the paragraph above.  The iGPU in the Ryzen 5600G is faster than the GT 1030 I have in a Ryzen 2600. It is clear.  Overall, it costs less too.

---

### Post by Nosphky on 2022-10-22
After a few days of overwhelm with a complete neighborhood electrical failure taking the utility company more than half a day to fix followed by trip to the airport to collect family members with flights delayed. And other family obligations. So when I got back to the display problems, I decided to try changing the graphics card for an AMD Radion of some sort but I'm living in the sticks and our friendly computer shop in a nearby village tried all his suppliers but no AMD cards in stock (except high end - but I'm no gamer so I don't want to spend 500 euro.

I decided to give the motherboard integrated graphics a go. I removed the GeForce GT 710 and it seems to run ok. An inxi -GCS query shows that  I'm using an  [FONT=monospace][COLOR=#000000] x11 [/COLOR][COLOR=#5454ff]**server:**[/COLOR][COLOR=#000000] X.Org [/COLOR][COLOR=#5454ff]**v:**[/COLOR][COLOR=#000000] 1.21.1.3 

I'll wait and see if any of the problems return with this basic setup.
[/COLOR]
[/FONT]

---

### Post by oldfred on 2022-10-22
Since I was using a low end nVidia card, I comared it to my Intel chips performance.
Intel was better.

I believe this is yours:
[https://www.videocardbenchmark.net/compare/2622vs2451/GeForce-710A-vs-Intel-HD-4600](https://www.videocardbenchmark.net/compare/2622vs2451/GeForce-710A-vs-Intel-HD-4600)
Intel HD4600  632
Nvidia 710      486
Or better not to use nVidia.

---

### Post by Nosphky on 2022-10-23
Thanks for that link, oldfred. Yes, you're quite right, that is (was) my combination. It seems that the Intel 4600 has the better benchmark score.

So far, the 22.04.1 with KDE Plasma desktop seems to be behaving fine with no odd display effects (yet?) since I removed the GeForce GT710 card.

I think this thread has run its course so I'll mark it solved.

---

