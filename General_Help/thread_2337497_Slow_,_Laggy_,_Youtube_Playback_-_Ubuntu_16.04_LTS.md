---
title: "Slow , Laggy , Youtube Playback - Ubuntu 16.04 LTS"
date: 2016-09-18
forum: General Help
---

### Post by scumbum on 2016-09-18
I'm running a Dell Laptop inspiron 1300 . 

1gig ram , 1.5ghz

I've installed the correct intel video drivers and get really slow laggy youtube playback with firefox and chromium . I've tried playing the videos using VLC , through the chromium feature where it sends the video from chromium over to VLC player . Can't seem to get anything to work . 

Internet connection is fast enough 15 mbps .

---

### Post by Bucky Ball on 2016-09-19
> **scumbum said:**
> I'm running a Dell Laptop inspiron 1300 . 

1gig ram , 1.5ghz

I've installed the correct intel video drivers and get really slow laggy youtube playback with firefox and chromium .

Welcome. Totally unsurprising. What version of Ubuntu are you running? I'd be surprised if you are getting anything like a satisfactory experience with the latest Ubuntu releases on that machine. Perhaps try something lighter if you're not already, Xubuntu or Lubuntu.

Frankly, for the latest Ubuntu, say 16.04 LTS, that machine is past it. My research tells me it is from 2006? Please confirm that is the model. Lubuntu it would be if so. You may also get lucky with Xubuntu or Xubuntu-core.

PS: You've installed the correct Intel video drivers? Most are in the kernel already so not sure what you installed. Please also confirm this and give the output of this command between ```
 tags, please (green link in my signature, bottom of my post):

[code]sudo lshw -C video
```

---

### Post by scumbum on 2016-09-20
> **Bucky Ball said:**
> Welcome. Totally unsurprising. What version of Ubuntu are you running? I'd be surprised if you are getting anything like a satisfactory experience with the latest Ubuntu releases on that machine. Perhaps try something lighter if you're not already, Xubuntu or Lubuntu.

Frankly, for the latest Ubuntu, say 16.04 LTS, that machine is past it. My research tells me it is from 2006? Please confirm that is the model. Lubuntu it would be if so. You may also get lucky with Xubuntu or Xubuntu-core.

PS: You've installed the correct Intel video drivers? Most are in the kernel already so not sure what you installed. Please also confirm this and give the output of this command between ```
 tags, please (green link in my signature, bottom of my post):

[code]sudo lshw -C video
```

&#65279;Thanks for the help . 

Yes , my Dell Laptop came out in 2005 it seems . 

Ok , so I installed Lubuntu and while the OS does run faster and everything seems much better , I'm still have the same laggy , slow , issue when watching youtube videos . 

I tried installing the intel driver I mentioned earlier here , [https://01.org/linuxgraphics/downloads](https://01.org/linuxgraphics/downloads)

But it doesn't seem to make a difference with video quality . 

heres what I get after running your command in terminal , 


  [*-display:0             
       description: VGA compatible controller
       product: Mobile 915GM/GMS/910GML Express Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:dff00000-dff7ffff ioport:eff8(size=8) memory:c0000000-cfffffff memory:dfec0000-dfefffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 915GM/GMS/910GML Express Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:dff80000-dfffffff]

---

### Post by Bucky Ball on 2016-09-21
I wouldn't bother trying to install drivers from any third-party. No point. The correct drivers for that card are already in the Ubuntu kernel and you are using them. The bottom line is it seems the video card is simply not up to it.

If you drop to a lower resolutions while watching video (say 480 on youtube) does it improve then get worse as you up the res? If so, graphics card.

---

### Post by mörgæs on 2016-09-21
I am not sure I would call the web site mentioned 'third party'. Then, who are first and second parties? 

Anyway, it's an official Intel web site and for newer graphics processors their drivers often make a big difference. I don't know if they benefit an old one like the one in question here.

I have collected some advice for [speeding up old hardware]("https://ubuntuforums.org/showthread.php?t=2130640&p=12580289&viewfull=1#post12580289"). Maybe some of it works and maybe you are just stuck with the performance as it is.

---

### Post by Bucky Ball on 2016-09-21
Proprietary then. Better? :)

Either way, the drivers for that card are present in the kernel so there's no point installing them from elsewhere. Sure we're all aware that's my point.

---

### Post by scumbum on 2016-09-21
> **mörgæs said:**
> I am not sure I would call the web site mentioned 'third party'. Then, who are first and second parties? 

Anyway, it's an official Intel web site and for newer graphics processors their drivers often make a big difference. I don't know if they benefit an old one like the one in question here.

I have collected some advice for [speeding up old hardware]("https://ubuntuforums.org/showthread.php?t=2130640&p=12580289&viewfull=1#post12580289"). Maybe some of it works and maybe you are just stuck with the performance as it is.

Thanks , I'll give it a try . 

Overall the stock performance with Lubuntu is pretty good , just youtube playback is too slow , laggy .

> **Bucky Ball said:**
> I wouldn't bother trying to install drivers from any third-party. No point. The correct drivers for that card are already in the Ubuntu kernel and you are using them. The bottom line is it seems the video card is simply not up to it.

If you drop to a lower resolutions while watching video (say 480 on youtube) does it improve then get worse as you up the res? If so, graphics card.

Yes if I drop the resolution it plays at 240p , but even 480p it can't playback right . 

If I download a youtube video at the highest resolution 720p and play that video back from my hard drive , it plays perfectly . I read somewhere that it has to do with flash player and how it uses the video card to playback the video .

---

### Post by Bucky Ball on 2016-09-21
Make sure you have the 'Canonical Partners' repo enabled in the 'Other Software' tab of 'Software and Updates' then try installing ubuntu-restricted-extras and reboot. Do you have flash installed at all? That should make sure you do.

---

### Post by mörgæs on 2016-09-21
Is Youtube still using Flash? I thought they had moved to HTML 5. 

If it's only a problem while streaming then something else could be the matter. Please run again the command from post 2 with *network* in stead of *video*. Remember CODE tags for the output.

---

### Post by scumbum on 2016-09-21
> **Bucky Ball said:**
> Make sure you have the 'Canonical Partners' repo enabled in the 'Other Software' tab of 'Software and Updates' then try installing ubuntu-restricted-extras and reboot. Do you have flash installed at all? That should make sure you do.

Ok , did all that , but it didn't fix the problem . 

I saw flash for ubuntu 16.04 get installed in terminal , so flash should be up to date .

> **mörgæs said:**
> Is Youtube still using Flash? I thought they had moved to HTML 5. 

If it's only a problem while streaming then something else could be the matter. Please run again the command from post 2 with *network* in stead of *video*. Remember CODE tags for the output.


Here you go , 

```
[ *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:14:22:9c:84:cc
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10Mbit/s
       resources: irq:18 memory:dfbfc000-dfbfdfff
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:17 memory:dfbfe000-dfbfffff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:16:ce:20:c7:b8
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=4.4.0-31-generic firmware=666.2 ip=192.168.1.84 link=yes multicast=yes wireless=IEEE 802.11bg]
```

---

### Post by mörgæs on 2016-09-22
The network gear looks fine. I was afraid it was some old 802.11b card.

Do you see a lot of network traffic while streaming?

---

### Post by scumbum on 2016-09-22
> **mörgæs said:**
> The network gear looks fine. I was afraid it was some old 802.11b card.

Do you see a lot of network traffic while streaming?

No , just me on the internet , I get 15 mbps download speed . 

Oh well , at least I can download a youtube video and watch it from my hard drive . All other internet and computer fuctions work good with Lubuntu so if I can't get this youtube playback to work its ok , this computer still has some usefulness .

---

