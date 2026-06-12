---
title: "Can't get wireless internet working"
date: 2008-04-30
forum: General Help
---

### Post by snakeman21 on 2008-04-30
I recently decided to switch to a Linux OS.  I originally wanted Ubuntu, but didn't have enough RAM to run it, so I got Xubuntu instead.  I installed it on a computer that I built about two years ago.  I've got 128 MB of RAM, a 6.4 GB hard drive, and four USB ports.  Up until a couple of weeks ago, I was running Windows 98 SE.  I partitioned my hard drive with the Linux partitioner, assigning 3 GB to Xubuntu, 3 GB to Windows, and the leftover as swap.  My plan is to first switch all of my files over to Xubuntu, get all my hardware working on Xubuntu, then delete Windows entirely.  So far, everything worked like a charm.  Linux was SO much easier.  However, when I tried to get my wireless internet adapter working, I ran into a problem:  Xubuntu refuses to acknowledge that the adapter exists!  It is a Linksys Wireless USB network adapter, model WUSB11 version 2.5, serial number B412303707.  I know that my USB ports are fine, because when I plug in any other device, Xubuntu has no trouble detecting and identifying it.  When I plug in the wireless adapter...Nothing.  I rebooted in Windows, downloaded the Linux driver from the Linksys website, and saved it to an mp3 player.  I restarted in Xubuntu again and transfered the driver to the desktop.  But when I tried to install it, I found that the "driver" was an archive of files, none of which were executable, and most of which Xubuntu couldn't even recognize.  The file was useless.  Since then, I have tried downloading the Linux driver from different sources, with the same result.  Please help, I really don't want to keep Winblows around just so I can have internet.  Just remember that I'm still new to Linux and have no idea how to use Terminal.  
     I don't get  the chance to visit this site often, so if you can, email me.  [email]snakeman_21@yahoo.com[/email].   Any advice would be greatly appreciated!

---

### Post by encompass on 2008-04-30
Well, interesting you have so little ram and hd for a 2 year old computer.  I have more ram and hd space and it was made in 1999!
Anyway,
Don't worry about the driver... let's run a few commands to see if we can learn more about this device.
Open a terminal... application... accessories... terminal
and run this command...
```
lsusb
```
but sure to do this with the usb device in the computer... this should give us an idea of what exactly is in this wireless adapter.  So many adapters are different but have that same model name.
As for downloading a driver... linux comes with practically every driver you will need.  For example, your video, network, and other what not are working becuase they have drivers for it built into linux.  As for windows you have to download each thing manually.
So... happy to see you in linux.  You computer will barely surf the internet... but hey... happy to see you anyway. :D

---

### Post by snakeman21 on 2008-04-30
Okay, I did that... a list of all of my USB ports popped up with some info...Three of them were blank because there was nothing plugged into them.  The one that had the adapter showed me this:

"Bus 001 Device 002: ID 066b:2212 Linksys, Inc.  WUSB11v2.5 802.11b Adapter"

All of this is information I already head from what is printed on the Linksys except for the "802.11b Adapter" part.  Now, what do I do with this info?  It means nothing to me.  
I appreciate the help, by the way.

---

### Post by encompass on 2008-05-01
Let's give this a try...
it seems there is support for your card.  But we have to install an additional peice of software.  It will cost you 19.95 plus torvalds tax. Just kidding, ;D
Run this...
```

sudo apt-get install linux-wlan-ng

```
And reboot... then run this command...
```

ifconfig

```
And post the output here.
Good luck!

---

### Post by snakeman21 on 2008-05-01
I only got to try the first part of that before I ran into a problem.  I opened the terminal, typed "sudo apt-get install linux-wlan-ng", and it asked me for my password.  I put it in, and this is what I got...

Reading package lists... Done
Building dependency tree
Reading state information... Done
E:  Couldn't find package linux-wlan-ng

Apparently, Xubuntu didn't come with that package.  Is there any way I could download it?  I'm going to google it as soon as I finish typing this...Get back to me, though.

---

### Post by encompass on 2008-05-01
So... in searching for your solution I found a fantastic guid that can help you... 
If you need help with it... you can write back here and I can help you out.
Odd's are you just haven't enabled it or other what not.
[https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb](https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb)
Good luck!  BTW... according to the article, you don't have to install the driver at all in the newest ubuntu. 8.04.
As for getting it to work with your wireless network.  Have you tried the network manager in the upper right-handcorner?  If you network is visable it show be able to see it and you simple click on it and fill in the information.  Hope that helps you out.
This is a picture of network manager in action.
[http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/)
Notice how when it is clicked it shows the available networks.
Good luck dude.

---

### Post by snakeman21 on 2008-05-01
The driver you suggested (Prism II) requires the package linux-wlan-ng.  I do not have this package.  I tried dowloading it, but Terminal still tells me it can't be found.  It did NOT come with my CD-ROM.  Pleas remember that I am not running Ubuntu, I don't have enough RAM for that.  I'm running Xubuntu.  However, I do have a Ubunto CD.  Could I put the Ubuntu CD in my computer and get that package?

---

### Post by BB_DaKraxor on 2008-05-01
Strange... which version of Ubuntu are you using? I use 8.04 Xubuntu and I do have that package.

```
$ apt-cache search linux-wlan-ng
linux-wlan-ng - utilities for wireless prism2 cards
linux-wlan-ng-doc - documentation for wlan-ng
linux-wlan-ng-firmware - firmware files used by the linux-wlan-ng driver
linux-wlan-ng-source - linux-wlan-ng driver

```

Perhaps you need to run```
apt-get update
```

---

### Post by snakeman21 on 2008-05-01
I'll try all that, but how can I get an update with no internet connection?  And I did put my ubuntu cd in and found the package...but when I transfered it to the hard disk, I had the same problem as the original driver--A file archive with no executable files, and most files couldn't be recognized.
Also no luck on the network manager.  I had tried it already, but tried again just for kicks.  Any more ideas?

---

### Post by BB_DaKraxor on 2008-05-01
I see you're not familiar with Linux at all so I'll try to explain some basics.

A package in Debian-based systems, like Ubuntu (Xubuntu, Kubuntu and Edubuntu are almost completely the same, so when I say Ubuntu, I usually mean all of them) should be a .deb file. You can install .deb files by typing
```
sudo dpkg -i my_deb_file.deb
```
You can download the package linux-wlan-ng manually from [_here_]("http://archive.ubuntu.com/ubuntu/pool/main/l/linux-wlan-ng/linux-wlan-ng_0.2.8+svn1839+dfsg-2ubuntu4_i386.deb") (this works with 8.04 Hardy Heron, that is the latest release, be sure you use that).

apt is a nice tool that downloads and installs packages and their dependencies so you don't have to do it manually like in winblows. Like this:

```
sudo apt-get install firefox
```

This will download and install the latest (stable) release of Firefox. You type sudo before a command to run it as the root user (system administrator).

Hope you get everything.

---

### Post by snakeman21 on 2008-05-01
Okay, I just tried "apt-get update".  As I expected, I got a ton of messages telling me that the system couldn't access the webpage.  Its only suggestion was to run apt-get update...which is weird because that's what it just tried to do!  Anyways, I have to go to work pretty soon, so I'm gonna give you all the info I can.  I've already mentioned that I have 128 MB of RAM and a 6.4 GB HD.  The version of Ubuntu that I have is Xubuntu 8.04.  I am looking at the CD right now.  It says, "Xubuntu 8.04 I386 ALT"  
Additionally, when I ran terminal and put in "apt-cache search" with the different linux-wlan-ng suggestions that BB_DaKraxor suggested, nothing happened.  It simply brought me down to the next line for a new command.  No response, no error, no NOTHING.  
I don't know, man.  I really like Xubuntu, but it'll be pretty useless to me without the internet.  That's 90% of what I use my computer for.  It's kind of disappointing that it only took a couple of hours to partition my hard drive, completely install Xubuntu, AND get all of my hardware and programs working in it with no problem, but then it stopped me at the only thing I REALLY wanted--internet.  Right now I'm on the same computer, running in Windblows 98 SE.  To make matters worse, I recently got a new monitor.  When I hooked it up to make sure it worked properly, I was running Xubuntu.  It worked fine, so I threw my old crappy monitor out.  I didn't use windows again until a couple of days later.  When I did, I found that with the new monitor, Winblows is stuck in 16 color.  Anybody who has seen a nice monitor in 16-color know that it S-U-C-K-S.  I figured it wouldn't matter because I was doing away with Windows.  But I can't do that until I get my internet up and running on Xubuntu.  At this point, I can't very well switch back to Windows, either, because of the monitor problem.  It is literally so bad that whenever someone sends pictures to my email, I can't see what they are until I either send them to a USB drive and look at them in Xubuntu, or save them to  disk and put them on my crappy laptop.  (Gateway 2000 with Winblows ME....ANCIENT!!!)  
Even if this doesn't work out, your input and suggestions are greatly appreciated!

---

### Post by snakeman21 on 2008-05-01
I didn't plan on coming back here today, but I've got a couple of hours before I have to go to work.  First of all, *thank you BB_DaKraxor!*  I finally installed the package (linux-wlan-ng) thanks to your link.  Now, to get back to the original problem, I'm going to reboot in Ubuntu, and run ifconfig.  Then I'll switch back over it winblows and post the output.

---

### Post by snakeman21 on 2008-05-01
Results from running ifconfig:

Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:4 errors:0 dropped:0 overruns:0 frame:0
TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:200 (200.0 B) TX bytes:200 (200.0 B)

This information means nothing to me.  Back to my original question...How do I get my Linksys to work?

---

### Post by encompass on 2008-05-01
According to the link I gave you... you don't need that driver anyway.  It should work right away with your system.  We shouldn't have to install the driver at all.
Could you run this command and tell me what you get?
```

ifconfig

```
Thanks...
I would like to find the lines like this...
```
eth0      Link encap:Ethernet  HWaddr 00:d0:59:6a:fa:b4  
          inet addr:192.168.0.103  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2d0:59ff:fe6a:fab4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1497 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1572 errors:1 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:843103 (823.3 KB)  TX bytes:289930 (283.1 KB)
          Interrupt:11 Base address:0x1c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:280 errors:0 dropped:0 overruns:0 frame:0
          TX packets:280 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14000 (13.6 KB)  TX bytes:14000 (13.6 KB)
```
I need to get the lines eth0 eth1 lo and wlan0 from that command.  Basically the first column.  you don't have to write all that down.

Additionally, you probably have a cable hanging around... you could plug in your system and run your updates from there... for all we know... these updates may fix your issue.  But who knows. :/

---

### Post by snakeman21 on 2008-05-01
Encompass, you wanted the results of ifconfig.  Here they are, this is all I got.  It doesn't look very promising to me.

```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 B)  TX bytes:200 (200.0)
```


Also, I do not have any cable that I can use for the Internet.  The only connection that I have is the wireless adapter that I am now using in Winblows 98.

---

### Post by encompass on 2008-05-01
Alrighty... let's hope this is the last step.
try this...
```

sudo modprobe prism2_usb

```
do that with the card plugged in.
Then try it out with...
```

ifconfig

```
And see if you get any new interfaces to use for the internet.
You could also try network manager... and unplugging and pluggin back in the usb device.
IF we can't get it working then it may be that you have a different chipset then what it's telling you and we will need to probe for that.

---

### Post by encompass on 2008-05-01
And about your computer just going back to the command line after the command was completed.
99 percent of the time this is a good thing.  In linux we expect things to work.  If they don't THEN tell us about it.  Otherwise it should have done exactly what it was supposed to.  Windows users have grown used to the computer responding to everything you do even when it's not needed.  After a while of working in linux and then you go back to windows... you get really sick of all the notifications because you really don't need them.
So, to explain, most linux programs will only tell you if it didn't work, because computers are SUPPOSED to work rather then kinda work. :D
It's one of the big differences in the style of programmers and designers in linux.

---

### Post by snakeman21 on 2008-05-02
Okay, I gave it that command, and it went right down to the next line.  According to your last entry, that's good.  Then I ran ifconfig again, and here's what I got...

```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:600 (600.0 B)  TX bytes:600 (600.0 B)
```

The only things that changed are the packet amounts (from 4 to 12) and the RX and TX bytes (from 200.0 to 200.0).  Somehow I get the feeling that that's not particularly good.  Especially considering that my wireless adapter still doesn't work in ubuntu.

---

### Post by snakeman21 on 2008-05-02
sorry, typo.  I weant to type "from 200.0 to **600.0**"

---

### Post by encompass on 2008-05-02
All we need to know is that first column.  Not all that data.  Don't worry about that other stuff jsut the labels. Sooooo...
now we are going to check if your card has some funky chipset.
It's a long one... but could you post this in a code tage...
```
like this...
sudo lsusb -v
```
I will look threw that and try to get your chipset.
This is what happens when manufacturers don't work with open source programmers.  Really sucks, some how making it not work in linux makes them money. :confused:

---

### Post by snakeman21 on 2008-05-02
Wow, I kind of feel bad about giving you all this junk to sort through... I really do appreciate you tying to help.  It's good to know that there are still nice people in the world... even if they are on the other side of it!  

Well, here it is...


```
sean@ubuntu:~$ lsusb -v

Bus 001 Device 003: ID 066b:2212 Linksys, Inc. WUSB11v2.5 802.11b Adapter
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x066b Linksys, Inc.
  idProduct          0x2212 WUSB11v2.5 802.11b Adapter
  bcdDevice            1.32
  iManufacturer           0 
  iProduct                0 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           39
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval               1
cannot read device status, Operation not permitted (1)
sean@ubuntu:~$ 
```

I omitted about three quarters of it, because when I ran the command, there was also an mp4 player, a XD memory card reader, and a USB printer plugged in.  I deleted those results and only gave you the results for the Wireless adapter.  Good luck, although from what I've seen from you so far, you shouldn't need it!

---

### Post by encompass on 2008-05-02
Well, I feel at a loss for words here... everything in me tells me this card should be working.
Even this guy had the EXACT card as and got it working with no problem at all.
VERY weird.
I have sent a message to him and if we are lucky he will respond.
The only idea I have left if that you unplug everything.  Restart the computer... plugin the usb wireless card and nothing else, and see if you can connect or get anything from ifconfig command.  IF you don't run sudo modprobe prism2_usb and unplug and plug it back in and try again.  I just don't see how this card is not working.  Are you using this device at the end of an extension cable?  And having many devices plugged in COULD be an issue.  We shall see, shan't we. :D
Thanks for the complement... but this thing is getting me upset... it goes against all the laws of linux I know. :D
[http://ubuntuforums.org/showthread.php?t=776255&goto=newpost](http://ubuntuforums.org/showthread.php?t=776255&goto=newpost)

---

### Post by snakeman21 on 2008-05-02
No, I'm not using an extension cable, I'm using the USB cable that came with it.  Also tried unplugging everything but the adapter...no luck.  
Hopefully, it's just some small, simple, stupid little problem that both of us overlooked... because like I said, switching to Ubuntu is useless to me without internet.  And as I said before, My new monitor doesn't work worth a damn in winblows for some reason...probably too new.  So at this point, both OS's are pretty annoying.  I'll be SO happy when I finally get this thing working... It's going to be so satisfying to delete Winblows.  Kind of like giving a big middle finger to Bill Gates, in my own special way.

---

### Post by encompass on 2008-05-02
Sorry, but did you try all the steps I asked above?  I am just making sure so we don't miss anything.
Well at this point, perhaps you could tell me a little bit about your computer setup.  For example, what is the model of the computer.  Speed, brand, and even this output may help...
```

dmesg
----------------
lshw
----------------
lsusb -v
----------------
lspci
----------------

```
I would like to have ALL of that.  Because I want to see if anything is interfering with anything else.
Thanks.

---

### Post by encompass on 2008-05-02
So... if we can't get that to work... we can use a tool called ndiswrapper.  This is a pretty amazing tool... it takes a windows driver and wraps itself around it and turns it into a linux driver.
It seems that that is how they used to do this driver back when the open source driver didn't work very well.
But it uses a little more memory, not a lot but a little, and I don't like that fact that your already running so low on memory.  128 is VERY small.  I am suprised you can start firefox.
Try this command... I am not sure if it will work or not...
```
sudo apt-get install ndiswrapper-common
```
if it installs great otherwise you will need to copy it again.  I can get you the link when you need it.

---

### Post by snakeman21 on 2008-05-02
Okay, I'll run those commands and post the results.  But first, Just let me make sure I'm not a COMPLETE idiot.  
While further exploring the network configuration, I realized that I haven't done ANYTHING to configure the network.  Do I have to?  Or should it just work, like in Windows?  If I do, I have no clue how to do it.  You're going to have to walk me through it, step-by-step.  Secondly, when I was installing the adapter in Windows, I noticed that before I finished, only one of the two lights was on.  Afterwards, both of them came on.  Since then, sometimes the signal is weak or undetectable.  When this happens, the second light goes out.  so basically, the first light is a power indicator, and the second one is a status indicator.  Now, when I boot in ubuntu, BOTH lights come on, even though it doesn't work.  Which leads me to believe that it works fine, but I haven't configured the network correctly.  (I fooled around with the network configurations today, with no luck)  Am I just an idiot? Or is there really a problem?  
Give me a couple of minutes, and I'll have the results of those commands for you.

---

### Post by snakeman21 on 2008-05-03
Sorry that took so long, I had to stop to feed the iguana and the snakes.
I know that 128 MB of RAM is small, but you'd be surprised at how many more advance programs I can run with no problem with it...I don't know how it works, but I can even run things like Windows Media Player 11, blender, and Cannon Easy-Photo-Print.  Firefox is a breeze.  Hey...just out of curiosity...How did you know I was using Firefox?  
So that program...ndiswrapper?  you're saying that with that I could just take the Windows 98 driver and turn it into a linux driver?  That is SO cool.
Anyways, here are the results from those commands...
```

sean@ubuntu:~$ dmesg
[    0.000000] Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000008000000 (usable)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fffc0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 128MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 32768) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->    32768
[    0.000000]   HighMem     32768 ->    32768
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->    32768
[    0.000000] On node 0 totalpages: 32768
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 224 pages used for memmap
[    0.000000]   Normal zone: 28448 pages, LIFO batch:7
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.1 present.
[    0.000000] ACPI: DMI BIOS year==0, assuming ACPI-capable machine
[    0.000000] Allocating PCI resources starting at 10000000 (gap: 08000000:f6c00000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 32512
[    0.000000] Kernel command line: root=UUID=bf71c2c2-4b01-4d15-b856-a820cf5413c0 ro quiet splash
[    0.000000] Found and enabled local APIC!
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 512 (order: 9, 2048 bytes)
[    0.000000] Detected 601.392 MHz processor.
[   53.101398] Console: colour VGA+ 80x25
[   53.101411] console [tty0] enabled
[   53.101658] Dentry cache hash table entries: 16384 (order: 4, 65536 bytes)
[   53.101835] Inode-cache hash table entries: 8192 (order: 3, 32768 bytes)
[   53.116541] Memory: 118008k/131072k available (2157k kernel code, 12512k reserved, 998k data, 364k init, 0k highmem)
[   53.116569] virtual kernel memory layout:
[   53.116573]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   53.116578]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   53.116582]     vmalloc : 0xc8800000 - 0xff7fe000   ( 879 MB)
[   53.116587]     lowmem  : 0xc0000000 - 0xc8000000   ( 128 MB)
[   53.116592]       .init : 0xc041b000 - 0xc0476000   ( 364 kB)
[   53.116596]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB)
[   53.116601]       .text : 0xc0100000 - 0xc031b5a4   (2157 kB)
[   53.116612] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   53.116702] SLUB: Genslabs=11, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   53.196706] Calibrating delay using timer specific routine.. 1204.03 BogoMIPS (lpj=2408068)
[   53.196784] Security Framework initialized
[   53.196806] SELinux:  Disabled at boot.
[   53.196847] AppArmor: AppArmor initialized
[   53.196860] Failure registering capabilities with primary security module.
[   53.196886] Mount-cache hash table entries: 512
[   53.197224] CPU: After generic identify, caps: 0383fbff 00000000 00000000 00000000 00000000 00000000 00000000 00000000
[   53.197261] CPU: L1 I cache: 16K, L1 D cache: 16K
[   53.197269] CPU: L2 cache: 256K
[   53.197279] CPU: After all inits, caps: 0383fbff 00000000 00000000 00000040 00000000 00000000 00000000 00000000
[   53.197314] Compat vDSO mapped to ffffe000.
[   53.197355] Checking 'hlt' instruction... OK.
[   53.213433] SMP alternatives: switching to UP code
[   53.217615] Freeing SMP alternatives: 11k freed
[   53.217994] Early unpacking initramfs... done
[   54.333630] ACPI: Core revision 20070126
[   54.333746] ACPI Exception (tbxface-0629): AE_NO_ACPI_TABLES, While loading namespace from ACPI tables [20070126]
[   54.333761] ACPI: Unable to load the System Description Tables
[   54.333941] CPU0: Intel Pentium III (Coppermine) stepping 01
[   54.333958] SMP motherboard not detected.
[   54.548316] Brought up 1 CPUs
[   54.548377] CPU0 attaching sched-domain:
[   54.548386]  domain 0: span 01
[   54.548392]   groups: 01
[   54.548993] net_namespace: 64 bytes
[   54.549020] Booting paravirtualized kernel on bare hardware
[   54.550945] Time: 14:41:06  Date: 05/02/08
[   54.551035] NET: Registered protocol family 16
[   54.551763] EISA bus registered
[   54.552799] PCI: PCI BIOS revision 2.10 entry at 0xfdb91, last bus=1
[   54.552809] PCI: Using configuration type 1
[   54.552816] Setting up standard PCI resources
[   54.567581] ACPI: Interpreter disabled.
[   54.567593] Linux Plug and Play Support v0.97 (c) Adam Belay
[   54.567701] pnp: PnP ACPI: disabled
[   54.567713] PnPBIOS: Scanning system for PnP BIOS support...
[   54.567765] PnPBIOS: Found PnP BIOS installation structure at 0xc00f74e0
[   54.567776] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0x6a04, dseg 0xf0000
[   54.570928] PnPBIOS: 16 nodes reported by PnP BIOS; 16 recorded by driver
[   54.571747] PCI: Probing PCI hardware
[   54.571809] PCI: Probing PCI hardware (bus 00)
[   54.572299] * Found PM-Timer Bug on the chipset. Due to workarounds for a bug,
[   54.572305] * this clock source is slow. Consider trying other clock sources
[   54.572363] PCI quirk: region 0400-043f claimed by PIIX4 ACPI
[   54.572373] PCI quirk: region 0440-044f claimed by PIIX4 SMB
[   54.574108] PCI: Using IRQ router PIIX/ICH [8086/7110] at 0000:00:07.0
[   54.580412] NET: Registered protocol family 8
[   54.580421] NET: Registered protocol family 20
[   54.580665] AppArmor: AppArmor Filesystem Enabled
[   54.580797] system 00:00: iomem range 0x0-0x9fbff could not be reserved
[   54.580809] system 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
[   54.580820] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
[   54.580831] system 00:00: iomem range 0x100000-0x7ffffff could not be reserved
[   54.580842] system 00:00: iomem range 0xfec00000-0xfec00fff could not be reserved
[   54.580853] system 00:00: iomem range 0xfee00000-0xfee00fff could not be reserved
[   54.580863] system 00:00: iomem range 0xfffc0000-0xffffffff could not be reserved
[   54.580904] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[   54.580915] system 00:08: ioport range 0xcf8-0xcff could not be reserved
[   54.580925] system 00:08: ioport range 0x400-0x43f has been reserved
[   54.580935] system 00:08: ioport range 0x440-0x44f has been reserved
[   54.580946] system 00:08: iomem range 0x0-0x0 could not be reserved
[   54.580956] system 00:08: iomem range 0x0-0x0 could not be reserved
[   54.580965] system 00:08: iomem range 0x0-0x0 could not be reserved
[   54.580974] system 00:08: iomem range 0x0-0x0 could not be reserved
[   54.580983] system 00:08: iomem range 0x0-0x0 could not be reserved
[   54.580992] system 00:08: iomem range 0x0-0x0 could not be reserved
[   54.581002] system 00:08: iomem range 0x0-0x0 could not be reserved
[   54.581011] system 00:08: iomem range 0x0-0x0 could not be reserved
[   54.581031] system 00:09: ioport range 0x290-0x297 has been reserved
[   54.582431] PCI: Bridge: 0000:00:01.0
[   54.582442]   IO window: d000-dfff
[   54.582453]   MEM window: fca00000-feafffff
[   54.582461]   PREFETCH window: f0800000-f48fffff
[   54.582512] NET: Registered protocol family 2
[   54.584159] Time: tsc clocksource has been installed.
[   54.616427] IP route cache hash table entries: 1024 (order: 0, 4096 bytes)
[   54.617208] TCP established hash table entries: 4096 (order: 3, 32768 bytes)
[   54.617320] TCP bind hash table entries: 4096 (order: 3, 32768 bytes)
[   54.617425] TCP: Hash tables configured (established 4096 bind 4096)
[   54.617434] TCP reno registered
[   54.628552] checking if image is initramfs... it is
[   56.763152] Freeing initrd memory: 7279k freed
[   56.764982] audit: initializing netlink socket (disabled)
[   56.765024] audit(1209739267.544:1): initialized
[   56.772649] VFS: Disk quotas dquot_6.5.1
[   56.772973] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   56.773484] io scheduler noop registered
[   56.773494] io scheduler anticipatory registered
[   56.773501] io scheduler deadline registered
[   56.773553] io scheduler cfq registered (default)
[   56.773583] Limiting direct PCI/PCI transfers.
[   56.773645] Boot video device is 0000:01:00.0
[   56.774377] isapnp: Scanning for PnP cards...
[   57.128492] isapnp: No Plug & Play device found
[   57.247787] Real Time Clock Driver v1.12ac
[   57.248033] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   57.248303] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   57.248728] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   57.250500] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   57.251319] 00:0b: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   57.254052] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   57.254302] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   57.254657] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[   57.256882] serio: i8042 KBD port at 0x60,0x64 irq 1
[   57.256898] serio: i8042 AUX port at 0x60,0x64 irq 12
[   57.263414] mice: PS/2 mouse device common for all mice
[   57.263819] EISA: Probing bus 0 at eisa.0
[   57.263886] EISA: Detected 0 cards.
[   57.263896] cpuidle: using governor ladder
[   57.263903] cpuidle: using governor menu
[   57.264394] NET: Registered protocol family 1
[   57.264490] Using IPI No-Shortcut mode
[   57.264577] registered taskstats version 1
[   57.264780]   Magic number: 8:758:686
[   57.264992] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   57.264999] EDD information not available.
[   57.266299] Freeing unused kernel memory: 364k freed
[   57.288536] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   58.955667] fuse init (API version 7.9)
[   59.065878] thermal: Unknown symbol acpi_processor_set_thermal_limit
[   60.273963] usbcore: registered new interface driver usbfs
[   60.274036] usbcore: registered new interface driver hub
[   60.305861] usbcore: registered new device driver usb
[   60.326142] SCSI subsystem initialized
[   60.697695] USB Universal Host Controller Interface driver v3.0
[   60.697896] PCI: setting IRQ 10 as level-triggered
[   60.697905] PCI: Found IRQ 10 for device 0000:00:07.2
[   60.697926] PCI: Sharing IRQ 10 with 0000:00:0b.0
[   60.697953] uhci_hcd 0000:00:07.2: UHCI Host Controller
[   60.698489] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[   60.698540] uhci_hcd 0000:00:07.2: irq 10, io base 0x0000ef80
[   60.698999] usb usb1: configuration #1 chosen from 1 choice
[   60.699081] hub 1-0:1.0: USB hub found
[   60.699101] hub 1-0:1.0: 2 ports detected
[   60.757687] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   60.786789] libata version 3.00 loaded.
[   60.803256] PCI: setting IRQ 11 as level-triggered
[   60.803269] PCI: Found IRQ 11 for device 0000:00:13.0
[   60.803312] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   60.803387] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[   60.803424] ohci_hcd 0000:00:13.0: irq 11, io mem 0xfebff000
[   60.815812] Floppy drive(s): fd0 is 1.44M
[   60.833493] FDC 0 is a post-1991 82077
[   60.859869] usb usb2: configuration #1 chosen from 1 choice
[   60.859956] hub 2-0:1.0: USB hub found
[   60.859980] hub 2-0:1.0: 2 ports detected
[   60.963379] ata_piix 0000:00:07.1: version 2.12
[   60.965916] scsi0 : ata_piix
[   60.968453] scsi1 : ata_piix
[   60.968606] ata1: PATA max UDMA/33 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[   60.968616] ata2: PATA max UDMA/33 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[   61.042806] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   61.145792] ata1.00: ATA-4: WDC AC26400R, 22.01N23, max UDMA/66
[   61.145808] ata1.00: 12594960 sectors, multi 16: LBA 
[   61.177788] ata1.00: configured for UDMA/33
[   61.209704] usb 1-1: configuration #1 chosen from 1 choice
[   61.457331] usb 1-2: new full speed USB device using uhci_hcd and address 3
[   61.553670] ata2.00: ATAPI: SAMSUNG DVD-ROM SD-608, BN13, max MWDMA2
[   61.608126] usb 1-2: config 1 has an invalid interface number: 1 but max is 0
[   61.608144] usb 1-2: config 1 has no interface number 0
[   61.620385] usb 1-2: configuration #1 chosen from 1 choice
[   61.725591] ata2.00: configured for MWDMA2
[   61.725966] scsi 0:0:0:0: Direct-Access     ATA      WDC AC26400R     22.0 PQ: 0 ANSI: 5
[   61.726884] scsi 1:0:0:0: CD-ROM            SAMSUNG  DVD-ROM SD-608   1.3  PQ: 0 ANSI: 5
[   62.637028] usbcore: registered new interface driver libusual
[   62.655053] Driver 'sd' needs updating - please use bus_type methods
[   62.660286] sd 0:0:0:0: [sda] 12594960 512-byte hardware sectors (6449 MB)
[   62.660339] sd 0:0:0:0: [sda] Write Protect is off
[   62.660349] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   62.660420] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   62.660594] sd 0:0:0:0: [sda] 12594960 512-byte hardware sectors (6449 MB)
[   62.660635] sd 0:0:0:0: [sda] Write Protect is off
[   62.660644] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   62.660711] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   62.660726]  sda: sda1 sda2 sda3
[   62.685061] Driver 'sr' needs updating - please use bus_type methods
[   62.686914] Initializing USB Mass Storage driver...
[   62.690003] scsi2 : SCSI emulation for USB Mass Storage devices
[   62.692841] usbcore: registered new interface driver usb-storage
[   62.692863] USB Mass Storage support registered.
[   62.693136] usb-storage: device found at 2
[   62.693144] usb-storage: waiting for device to settle before scanning
[   62.710973] sd 0:0:0:0: [sda] Attached SCSI disk
[   62.726286] sr0: scsi3-mmc drive: 4x/32x cd/rw xa/form2 cdda tray
[   62.726302] Uniform CD-ROM driver Revision: 3.20
[   62.726480] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   62.750385] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   62.750453] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   63.450486] Attempting manual resume
[   63.450498] swsusp: Resume From Partition 8:3
[   63.450505] PM: Checking swsusp image.
[   63.451031] PM: Resume from disk failed.
[   63.538078] kjournald starting.  Commit interval 5 seconds
[   63.538120] EXT3-fs: mounted filesystem with ordered data mode.
[   67.695154] usb-storage: device scan complete
[   67.698344] scsi 2:0:0:0: Direct-Access     SigmaTel MSCN             0100 PQ: 0 ANSI: 4
[   67.704289] sd 2:0:0:0: [sdb] 984832 2048-byte hardware sectors (2017 MB)
[   67.707220] sd 2:0:0:0: [sdb] Write Protect is off
[   67.707231] sd 2:0:0:0: [sdb] Mode Sense: 3e 00 00 00
[   67.707239] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   67.716213] sd 2:0:0:0: [sdb] 984832 2048-byte hardware sectors (2017 MB)
[   67.719214] sd 2:0:0:0: [sdb] Write Protect is off
[   67.719224] sd 2:0:0:0: [sdb] Mode Sense: 3e 00 00 00
[   67.719232] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   67.719245]  sdb: sdb1
[   68.019135] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[   68.019264] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   86.067413] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   86.699957] input: PS/2 Logitech Mouse as /devices/platform/i8042/serio1/input/input3
[   88.890463] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   89.006374] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   89.039529] piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
[   89.039555] piix4_smbus 0000:00:07.3: Host SMBus controller not enabled!
[   89.121044] parport_pc 00:0c: reported by Plug and Play BIOS
[   89.121125] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   89.192326] Linux agpgart interface v0.102
[   89.219923] agpgart: Detected an Intel 440BX Chipset.
[   89.224616] agpgart: AGP aperture is 64M @ 0xf8000000
[   92.024494] prism2usb_init: prism2_usb.o: 0.2.8 Loaded
[   92.024507] prism2usb_init: dev_info is: prism2_usb
[   93.029151] hfa384x_usbctlx_complete_sync: CTLX[1] error: state(Request failed)
[   93.728514] PCI: Found IRQ 10 for device 0000:00:0b.0
[   93.728536] PCI: Sharing IRQ 10 with 0000:00:07.2
[   94.286593] gameport: CS4281 Gameport is pci0000:00:0b.0/gameport0, speed 2711kHz
[   95.032874] hfa384x_usbctlx_complete_sync: CTLX[1] error: state(Request failed)
[   95.032896] hfa384x_drvr_start: cmd_initialize() failed on two attempts, results -5 and -5
[   95.033898] prism2sta_ifstate: hfa384x_drvr_start() failed,result=-5
[   95.033967] usbcore: registered new interface driver prism2_usb
[  100.082639] hfa384x_usbctlx_complete_sync: CTLX[1] error: state(Request failed)
[  102.085357] hfa384x_usbctlx_complete_sync: CTLX[1] error: state(Request failed)
[  102.085371] hfa384x_drvr_start: cmd_initialize() failed on two attempts, results -5 and -5
[  102.086379] prism2sta_ifstate: hfa384x_drvr_start() failed,result=-5
[  102.570028] loop: module loaded
[  102.665914] lp0: using parport0 (interrupt-driven).
[  103.107630] Adding 433744k swap on /dev/sda3.  Priority:-1 extents:1 across:433744k
[  103.861391] EXT3 FS on sda2, internal journal
[  106.855754] ip_tables: (C) 2000-2006 Netfilter Core Team
[  108.941914] acpi_cpufreq: Unknown symbol acpi_processor_notify_smm
[  108.942169] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performance
[  108.943054] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performance
[  108.943444] acpi_cpufreq: Unknown symbol acpi_processor_register_performance
[  112.590088] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[  112.993687] ppdev: user-space parallel port driver
[  114.125259] audit(1209753725.800:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4395 profile="/usr/sbin/cupsd" namespace="default"
[  117.945447] Bluetooth: Core ver 2.11
[  117.947681] NET: Registered protocol family 31
[  117.947695] Bluetooth: HCI device and connection manager initialized
[  117.947707] Bluetooth: HCI socket layer initialized
[  118.165730] Bluetooth: L2CAP ver 2.9
[  118.165745] Bluetooth: L2CAP socket layer initialized
[  118.249809] Bluetooth: RFCOMM socket layer initialized
[  118.251459] Bluetooth: RFCOMM TTY layer initialized
[  118.251471] Bluetooth: RFCOMM ver 1.8
[  217.949140] NET: Registered protocol family 10
[  217.954109] lo: Disabled Privacy Extensions

**And the next one...**

sean@ubuntu:~$ lshw
WARNING: you should run this program as super-user.
ubuntu                    
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 128MiB
     *-cpu
          product: Pentium III (Coppermine)
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.8.1
          size: 600MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse up
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 32KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 256KiB
     *-pci
          description: Host bridge
          product: 440BX/ZX/DX - 82443BX/ZX/DX Host bridge
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel latency=32 module=intel_agp
        *-pci
             description: PCI bridge
             product: 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display UNCLAIMED
                description: VGA compatible controller
                product: NV6 [Vanta/Vanta LT]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 15
                width: 32 bits
                clock: 66MHz
                capabilities: vga_controller bus_master cap_list
                configuration: latency=32 maxlatency=1 mingnt=5
        *-isa
             description: ISA bridge
             product: 82371AB/EB/MB PIIX4 ISA
             vendor: Intel Corporation
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82371AB/EB/MB PIIX4 IDE
             vendor: Intel Corporation
             physical id: 7.1
             bus info: pci@0000:00:07.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=32 module=ata_piix
        *-usb:0
             description: USB Controller
             product: 82371AB/EB/MB PIIX4 USB
             vendor: Intel Corporation
             physical id: 7.2
             bus info: pci@0000:00:07.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-bridge UNCLAIMED
             description: Bridge
             product: 82371AB/EB/MB PIIX4 ACPI
             vendor: Intel Corporation
             physical id: 7.3
             bus info: pci@0000:00:07.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bridge
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: Crystal CS4281 PCI Audio
             vendor: Cirrus Logic
             physical id: b
             bus info: pci@0000:00:0b.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=CS4281 latency=32 maxlatency=24 mingnt=4 module=snd_cs4281
        *-usb:1
             description: USB Controller
             product: 82C861
             vendor: OPTi Inc.
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32 module=ohci_hcd
  *-scsi
       physical id: 1
       bus info: scsi@2
       logical name: scsi2
       capabilities: scsi-host
       configuration: driver=usb-storage
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: wlan0
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

**And the next one...**

sean@ubuntu:~$ lsusb -v

Bus 002 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 001 Device 003: ID 066b:2212 Linksys, Inc. WUSB11v2.5 802.11b Adapter
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x066b Linksys, Inc.
  idProduct          0x2212 WUSB11v2.5 802.11b Adapter
  bcdDevice            1.32
  iManufacturer           0 
  iProduct                0 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           39
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval               1
cannot read device status, Operation not permitted (1)

Bus 001 Device 002: ID 066f:8000 SigmaTel, Inc. SigmaTel MSCN USB Device [MP3 Player]
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x066f SigmaTel, Inc.
  idProduct          0x8000 SigmaTel MSCN USB Device [MP3 Player]
  bcdDevice           10.01
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          4 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              5 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
cannot read device status, Operation not permitted (1)

Bus 001 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

**And last, but not least...**

sean@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:0b.0 Multimedia audio controller: Cirrus Logic Crystal CS4281 PCI Audio (rev 01)
00:13.0 USB Controller: OPTi Inc. 82C861 (rev 10)
01:00.0 VGA compatible controller: nVidia Corporation NV6 [Vanta/Vanta LT] (rev 15)

```

Sorry, I know it's a lot of info.

---

### Post by encompass on 2008-05-03
try this one for the heck of it...
modprobe prism2_usb prism2_doreset=1

---

### Post by encompass on 2008-05-03
were you able to run that sudo apt-get install ndsiwrapper-common command?
and for your wireless card setup...
[http://paradigma.pt/ja/slog/wp-content/uploads/Screenshot-Network%20settings-Connections.png](http://paradigma.pt/ja/slog/wp-content/uploads/Screenshot-Network%20settings-Connections.png)
can you find the program that does this?  You should see just a modem connection but if you see your wireless too then you can go do a backflip.

---

### Post by snakeman21 on 2008-05-03
No, the wrapper didn't work...terminal said it couldn't find the package.  I'll try that other command you just gave me and get back to you.
And no, I don't see a modem connection on my network setup.  There are two things listed:  Wired connection, which says, "roaming mode enabled" underneath it, and point to point connection, which says, "this network interface is not configured" underneath it.  
All right, I'm going to go run that command and post the results... I should get to bed soon, though.  I don't know what time it is over there, but here, it's 2:00 am.

---

### Post by snakeman21 on 2008-05-03
Okay, I put in modprobe prism2_usb prism2_doreset=1.  Nothing happened, it dropped down to the next command line.  So, that's good, right?  What did that do?  
I'm going to bed...I'll check this when I get up before work.

---

### Post by adisor19 on 2008-05-08
I have 100% the exact same problem as this guy. I'm also using a Linksys WUSB11 v2.5 USB adapter.

Bus 001 Device 004: ID 066b:2212 Linksys, Inc. WUSB11v2.5 802.11b Adapter
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x066b Linksys, Inc.
  idProduct          0x2212 WUSB11v2.5 802.11b Adapter
  bcdDevice            1.32
  iManufacturer           0 
  iProduct                0 
  iSerial                 1 01190003
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           39
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval               1
Device Status:     0x0000
  (Bus Powered)



Help :'(

Adi

---

### Post by encompass on 2008-05-08
Really?!  Now did you ever have this working in linux before?
What about your computer, what kind of computer do you have?

---

