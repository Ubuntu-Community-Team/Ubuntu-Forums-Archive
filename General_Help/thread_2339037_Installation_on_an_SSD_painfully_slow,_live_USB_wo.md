---
title: "Installation on an SSD painfully slow, live USB works just fine"
date: 2016-10-04
forum: General Help
---

### Post by pommelstrike on 2016-10-04
Attempting to install x64 Ubuntu 16.04. i3-2100, integrated graphics, 8GB ECC memory, brand new Kingston UV400 SSD. And it's PAINFULLY slow. 

Clicking the upper right cog-wheel, it takes full two seconds for the menu to render. Launching a terminal with a keyboard shortcut takes about two seconds as well. Ouch.

I figured unity was too much for the integrated graphics, but then on a whim I launched that very same 16.04 as a USB live session and it was almost flying compared to the SSD. Not perfect, but MUCH more responsive. And actually usable.

What could be wrong here?

---

### Post by TheFu on 2016-10-04
Don't know from the description, but some SATA controllers and SSDs aren't well supported. I'd look for issues there, as a start. May have nothing to do with those things, so don't be surprised.  Also check the motherboard model for issues and if it is really new, sometimes it takes a few months. Running off the flash drive was smart - that should remove the MB, GPU, networking from consideration. Should.  But nothing is guaranteed.

---

### Post by T2uiYKb7 on 2016-10-04
Maybe I'd be looking for non-free packages, PPAs and GitHUB SATA controllers. I did some Googling but there's not much out there, other peoples complaints about speed are no where near as extreme as yours.

Maybe it's only an issue with the installer, packages aren't loaded that would be in a normal boot of an Ubuntu install.

If this was me I'd install Ubuntu from one USB onto another USB, then clone it onto your SSD.

That way you could just boot it from your SSD into a fully installed Ubuntu. I have no idea how fast it would clone to your SSD after what you've said tho.

**Edit: What model is your motherboard? One thing you could try is updating your BIOS, recent motherboards often let you update from a USB after booting into the BIOS menu.**

---

### Post by pommelstrike on 2016-10-04
> **TheFu said:**
> Don't know from the description, but some SATA controllers and SSDs aren't well supported.
So I should try IDE mode, if that's available?

> **TheFu said:**
> Also check the motherboard model for issues and if it is really new, sometimes it takes a few months.
i3-2100 came out in '11. I expect the mobo be about the same age.

> **andrew.nz said:**
> Maybe it's only an issue with the installer, packages aren't loaded that would be in a normal boot of an Ubuntu install.
Used the same stick to install in a different rig. Works just fine.

> **andrew.nz said:**
> If this was me I'd install Ubuntu from one USB onto another USB, then clone it onto your SSD.
I've had no luck with expanding or reducing the partition sizes when cloning. If you have a good resource handy, I'd look at it.

> **andrew.nz said:**
> **Edit: What model is your motherboard? One thing you could try is updating your BIOS, recent motherboards often let you update from a USB after booting into the BIOS menu.**
I tried looking it up from HardInfo, but apparently such basic info isn't available for linux. Model wasn't brightly visible on the mobo either. I guess I'll boot into a windows disk and use HWinfo if worst comes to worst.

---

### Post by oldfred on 2016-10-04
What mode is drive in UEFI?
It should be AHCI, not IDE nor RAID.

There may be other UEFI settings for drive.

---

### Post by T2uiYKb7 on 2016-10-05
I think it's pretty important to find the MOBO model. Could be be fixed by BIOS settings or a BIOS update.

Can you run this and paste the results (it requires sudo privileges but it only collects information):

```
dmidecode | grep -A4 'Base Board'
```

Forget what I said about cloning that was a reach anyway.

---

### Post by pommelstrike on 2016-10-06
Double checked it. The mass storage media mode is indeed AHCI.

> **andrew.nz said:**
> ```
dmidecode | grep -A4 'Base Board'
```
> Manufacturer: Intel Corporation
Product Name: To be filled by O.E.M.
Version: To be filled by O.E.M.
Serial Number: To be filled by O.E.M.

So, that was helpful. :lol:

But it's this one: [http://ark.intel.com/products/53558/Intel-Server-Board-S1200BTS](http://ark.intel.com/products/53558/Intel-Server-Board-S1200BTS)

---

### Post by oldfred on 2016-10-06
Last BIOS/UEFI update shows 2014, but have you installed that update?

---

### Post by pommelstrike on 2016-11-14
> **oldfred said:**
> Last BIOS/UEFI update shows 2014, but have you installed that update?
I have not, but this is confusing as hell. 


Platform ID: S1200BTS (fair enough)
BIOS version: s1200bt.86b.100.00.0030 (which doesn't even show up in google)


This seems to be what I want: [https://downloadcenter.intel.com/download/23896/Intel-Server-Board-S1200BTS-Firmware-Update-Package-for-EFI](https://downloadcenter.intel.com/download/23896/Intel-Server-Board-S1200BTS-Firmware-Update-Package-for-EFI)


But how do I know if I'm R28 or lower? It's the release number, but ... is that last 0030 digit? I can just upgrade without additional steps?

---

### Post by pommelstrike on 2016-11-14
Okay, did the BIOS update. All went fine. I'm on R42 now. That 0030 was indeed the R30 number I was looking for.


Booted up the OS. Resolution was really off and stretched (1024x900, I think... yea super weird numbers), but all snappy.


Reboot. Resolution goes back to 1280x1024, AAAAAAND it's slow again. 


Any thoughts?

---

### Post by TheFu on 2016-11-14
Searched a little this morning for solutions ... [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1538040](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1538040) - there is a setting.

Someone at my LUG yesterday had an extremely powerful laptop (i7 + 24G or RAM) and stock Ubuntu took over an hour to install (not pulling any updates or drivers off the network). He also had an SSD.

If that bug is relevant to your system, please report a "me too" there.

---

### Post by pommelstrike on 2016-11-15
Added barrier=0 to the root drive mount options. Rebooted. No noticeable improvement.

I'm suspecting graphics related issues, as the rig worked just fine speed wise after the firmware update messed up the resolution.

---

### Post by pommelstrike on 2016-11-22
So, I'm quite sure the issue is graphics related. The intel server board graphics have been an endless grief on Windows side as well. Plus I plugged the SSD into a rig with a regular graphics card, and it worked just fine. So...

```
$ sudo lshw -c video
[sudo] password for it: 
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: SM712 LynxEM+
       vendor: Silicon Motion, Inc.
       physical id: 2
       bus info: pci@0000:03:02.0
       version: b0
       width: 32 bits
       clock: 66MHz
       capabilities: pm vga_controller cap_list
       configuration: latency=32
       resources: memory:c0000000-c0ffffff
```

How would I remove the current driver? And what, if anything, should I replace it with? At the very least, I want to block the rig from implementing this buggy one again.

I don't really care if the resolution is smaller, or a little bit off in this particular instance. If it's snappy, it's good enough for me.

---

### Post by sudodus on 2016-11-22
Are you running in graphical mode (or text screen)? In graphical mode use try with xrandr in a text window. In my computer I get

```
$ xrandr
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 16384 x 16384
DVI-I-1 disconnected (normal left inverted right x axis y axis)
HDMI-1 disconnected (normal left inverted right x axis y axis)
VGA-1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 530mm x 300mm

   1920x1080     60.00*+
   1600x1200     60.00  
   1680x1050     59.95  
   1280x1024     60.02  
   1440x900      59.89  
   1280x960      60.00  
   1280x800      59.81  
   1024x768      60.00  
   800x600       60.32    56.25  
   640x480       60.00  
```

and I can set a lower resolution with an option from the list, for example

```
xrandr -s 1280x800
```

Will this help you find something that works?

***Edit:*** You could also try some [boot options](http://ubuntuforums.org/showthread.php?t=2230389&p=13370808#post13370808), for example nomodeset.

---

### Post by oldfred on 2016-11-22
This is not the built in Intel video. - SM712 LynxEM+ Silicon Motion, Inc.
Is it from a video card or do you have a switchable graphics laptop?
Can you in UEFI/BIOS set to use just the Intel video? And is that a different video out or the switchable?

Found this, says it is from 2011 and worked with the now very old 2.6 kernel.
[https://h-node.org/videocards/view/en/344/Silicon-Motion-Inc--SM712-LynxEM+--rev-b0-](https://h-node.org/videocards/view/en/344/Silicon-Motion-Inc--SM712-LynxEM+--rev-b0-)
You may have to make sure older driver is installed.

---

### Post by pommelstrike on 2016-11-22
> **sudodus said:**
> Are you running in graphical mode (or text screen)? In graphical mode use try with xrandr in a text window.
Graphical, yes. Thanks for the xrandr tip, will look into it.

> **oldfred said:**
> This is not the built in Intel video. - SM712 LynxEM+ Silicon Motion, Inc.
Is it from a video card or do you have a switchable graphics laptop?
Can you in UEFI/BIOS set to use just the Intel video? And is that a different video out or the switchable?
It's a server board's integrated video. Not sure if I can switch it to a different mode in BIOS. Will look!

> **oldfred said:**
> Found this, says it is from 2011 and worked with the now very old 2.6 kernel.
[https://h-node.org/videocards/view/en/344/Silicon-Motion-Inc--SM712-LynxEM+--rev-b0-](https://h-node.org/videocards/view/en/344/Silicon-Motion-Inc--SM712-LynxEM+--rev-b0-)
You may have to make sure older driver is installed.
Switching the driver is what I was asking how to do in the first place :D I've installed some nvidia drivers to Ubuntu back in the day, but that was automated and straightforward. This doesn't seem to be.


Weird part is, "lshw -c video" doesn't even show the driver under configuration, although it should.

---

### Post by sudodus on 2016-11-22
Servers are often equipped with simple graphics, because they are expected to run in text mode or even headless, without a monitor, and be connected to via the network, for example via ssh. So your solution might be to 'dumb down' the graphics for example to use lower resolution. Maybe you can even try 1024x768 and 800x600 or run in text mode.

On the other hand, it might be possible to plug in a better graphics card (if you happen to find a used card or buy a second hand card, it might help a lot - but some old cards do not work well with the current linux versions, so if that is what you want, you can start a thread in the Ubuntu hardware forum).

---

### Post by TheFu on 2016-11-22
My i3 system from 2015 reports:
```
$ sudo lshw -C video
  *-display               
       description: VGA compatible controller
       product: Broadwell-U Integrated Graphics
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=**i915** latency=0
       resources: irq:43 memory:e0000000-e0ffffff memory:d0000000-dfffffff ioport:1800(size=64)

```
In 2011, don't know if the i3 had build-in GPUs.  The listed device above, 
```
       product: SM712 LynxEM+
       vendor: Silicon Motion, Inc.

```is listed as "UNCLAIMED" - doesn't that mean no driver is installed?  So get the driver, compile it, and use modprobe to add it to the kernel manually. There might be an ubuntu package - idunno. [https://www.cyberciti.biz/faq/add-remove-list-linux-kernel-modules/](https://www.cyberciti.biz/faq/add-remove-list-linux-kernel-modules/) has general details.  [ftp://www.x.org/pub/X11R6.8.0/doc/siliconmotion.4.html](ftp://www.x.org/pub/X11R6.8.0/doc/siliconmotion.4.html) has some more details.  Seems there are a few bugs with the driver and the kernel devs have decided not to fix them (from the comments) because nobody has the expertise and the chips aren't popular. xserver-xorg-video-siliconmotion is probably the video driver package. 

In 2011, the intel GPUs were minimal and didn't support HW decoding of mpeg2 videos. If that is something you seek, get a new video card that supports both mpeg2 and h.264 video decoding in HW would be my advice, knowing nothing else about the situation.

---

### Post by irongolem0982 on 2016-11-22
test your SSD:

boot into a live session, then: 
```
sudo apt-get install gnome-disks -y && sudo gnome-disks
```

[SIZE=1]note: gnome-disks is included on lubuntu but i am not sure about ubuntu (hence sudo apt-get)
[/SIZE]
click the SSD in the left pane then click the settings gear in the upper right hand corner (may be hamburger icon depending on icon theme) and select benchmark. see if you get extremely slow speeds there.

Edit:
Nevermind I changed my mind it looks too much like a graphics issue. still worth a shot though???

---

### Post by oldfred on 2016-11-22
In synaptic I see a transitional package for Silicon Graphics driver.
Transitional package for:
 xserver-xorg-video-siliconmotion-lts-xenial

[http://www.phoronix.com/scan.php?page=news_item&px=MTEzNzc](http://www.phoronix.com/scan.php?page=news_item&px=MTEzNzc)
Silicon Motion Has Open-Source Driver, But Fails
[http://www.phoronix.com/scan.php?page=news_item&px=MTA2OTk](http://www.phoronix.com/scan.php?page=news_item&px=MTA2OTk)

---

### Post by pommelstrike on 2016-12-02
I tried some of that, but it seemed futile and ridiculously complex such a simple issue. Popped in a random graphics card. Works perfect.

---

### Post by TheFu on 2016-12-02
> **pommelstrike said:**
> I tried some of that, but it seemed futile and ridiculously complex such a simple issue. Popped in a random graphics card. Works perfect.

Yep. We don't always understand whether people are willing to spend $20 on a solution or if they are stubborn and want a $0 solution that takes 100 hrs of effort.  

Collectively, we are an odd bunch and need both types in the community. The stubborn people are why Linux exists.

---

### Post by sudodus on 2016-12-02
Congratulations and thanks for sharing your solution :KS

---

