---
title: "using ubuntu as media center."
date: 2019-12-15
forum: General Help
---

### Post by wolftrax on 2019-12-15
I remember there once was a ubuntu distribution for using it as a media center and I cant find that anywhere on the download page .   I have a television and dvd player but I don't have access to any channels and the only way I can watch television is using my computer to watch out free online television channels so I can follow  the news and perhaps watch a movie once in a while.  I don't want netflix or any paid for channels I just want to watch the news and usually I watch more dokumentaries and older movies on youtube than I do watch movies from my DVD collection so I wanted to set up a old laptop as media center and use it with wireless internet connected to the television .

is there still a media center distribution of ubuntu out or do need to just download a minimal image and find a light weight desktop and just use that instead ?  its only firefox I need and perhaps there are some free programs like tux tv or something I could find useful.

---

### Post by CatKiller on 2019-12-15
> **wolftrax said:**
> I remember there once was a ubuntu distribution for using it as a media center and I cant find that anywhere on the download page .

You could be thinking of Mythbuntu, which ran MythTV and did briefly become an official flavour, or Kodibuntu, which came from the Kodi devs. Both distro projects are discontinued.

It's easy enough to install whichever base you want, make it automatically log in, and start whichever media centre application you want. 

Otherwise there's libreELEC, which is aimed at very low powered devices like the raspberry pi.

---

### Post by wolftrax on 2019-12-15
yeah it was  mytth ubuntu I was thinking about.    I have this idea that I have a old laptop which is very very old and cant really run a full desktop normal installation and just download the miniimal iso image and build a media center out of it.   it would need a wireless adapter because it has no build in wireless network card.-  its a HP pavilion ze5900 which I currently just use play around with solaris 10 .  but its still functional .

---

### Post by TheFu on 2019-12-15
> **wolftrax said:**
> yeah it was  mytth ubuntu I was thinking about.    I have this idea that I have a old laptop which is very very old and cant really run a full desktop normal installation and just download the miniimal iso image and build a media center out of it.   it would need a wireless adapter because it has no build in wireless network card.-  its a HP pavilion ze5900 which I currently just use play around with solaris 10 .  but its still functional .

For watching live TV using an antenna, that will be _extremely country specific_.  If you are in the USA, then ATSC tuner will be required.  South America and Europe use different standards.

So you have a problem.  Old laptops don't have GPUs with hardware-based video decoders and they have slow CPUs, so this setup might not be able to display anything over 600p resolution without struggles, dropped frames, problems. OTOH, any laptop less than 5 yrs old will have a GPU with HW decoding built in, even the $80 chomebooks will handle this stuff perfectly at 1080p resolutions. I have a chromebook from 2013 that replaced an ITX AMD E350 system.  The E350 couldn't do any hidef video.

OTOH, a $35 raspberry pi v3 makes a nice kodi playback machine - add $16 for a case+PSU+microSD to hold the OS, so about $50 all in.  There is GPU support for both mpeg2 and h.264 video built in. It is silent and uses 2a and 5V of power.  There are specialized media center specific distros just for that device.  I use OSMC, which is a custom Kodi distro.   By far the easiest TV tuner to use with ATSC signals is hd-homerun devices.  

The world is about to jump to 4K video, so it might be worth spending $20-30 more on a newer Raspberry Pi that can do 4K video playback.

If you can post the GPU and CPU for the laptop, we can probably make a guess as to the video resolution that will playback acceptably.

---

### Post by wolftrax on 2019-12-15
all my computers are over ten years old..   the one I was thinking about using has no OS installed at the moment but its a fujitsu siemens with a intel core duo CPU as far as I remember. I was considering getting a dell optiplex stationary for that purpose but usually I just use the dual screen option and set it up with my television.  

I have no antenna or anything in my home which is why I watch DVDs and youtube and the Danish television channels are available as live stream .  I dont want netflix or any paid service . 

the rasperry PI sounds interesting but I am not sure it is easy to get here.  

I got a linux black box -x1  digital settopbox which I got from a second hand store and I cant figure out what it is but it looks like some kind of device intended to use with a televison , it has LAN input and a cardreader and it also have connections for antenna and connections to the television set. 

there is no manual with it and I cant find it on google but it looks like the kind of device that follows with a paid for service that people then give away to second hand stores and I can find many of those very cheap.   I bought this one because it says linux and I figure I might get it to work.  it also says that it finds over 50 free channels but I have not tried to set it up yet because I cant find any usermanual on the internet for it.   

the plan was to get a laptop running as media center and then figure out what this settopbox is and see if I can use this to get free television channels.

---

### Post by TheFu on 2019-12-15
Without knowing where you are, nobody can guess about broadcast TV.

Nobody has suggested **any** paid streaming services.

There are thousands of free streaming channels on the internet, ad supported.  [https://www.justwatch.com/](https://www.justwatch.com/) has a mix of paid and free streaming channels.  Roku has a huge list, but it is easiest to use a roku device for accessing those.  No credit card needed.  I don't know where Roku works or doesn't.  I use it mainly for DRM/paid services, but if you are ok with advertising, there are thousands of other streaming channels.

If you can get snail-mail, getting a raspberry pi should be trivial, unless you live in Iran or North Korea.  Places ship internationally all the time.  Amazon and [https://ameridroid.com/](https://ameridroid.com/) are two options.  There are many others.  For an OSMC streaming device, [https://osmc.tv/](https://osmc.tv/) .

A Core 2Duo or CoreDuo may or may not have an integrated GPU with HW decoding.  Specific models are needed.  I have a Core i5 from 2010 that doesn't have any iGPUs, but Pentium, Celerion, Core i3 and Core i5 CPUs from 2013 and later which do. Big changes happened from 2010 to 2013 related to HW-decoding for video.

---

### Post by wolftrax on 2019-12-16
I live in Denmarfk.   its just a idea I have to keep one of my old laptops alive ,  perhaps a bigger project than I expected reading trough this thread.  we have cheap solutions for television channels and I really just need to figure out if the antenna I do have works or not first.

---

### Post by TheFu on 2019-12-16
The easy way to get an overview of system hardware is to boot from a Try Ubuntu flash drive, install inxi, then run **inxi -Fz**
```
$ inxi -Fz
System:    Host: istar Kernel: 4.4.0-170-generic x86_64 (64 bit) Desktop: N/A
           Distro: Ubuntu 16.04 xenial
Machine:   Mobo: Gigabyte model: **H81M-HD3** v: x.x Bios: American Megatrends v: FA date: 12/01/2014
CPU:       Dual core Intel **Pentium G3258** (-MCP-) cache: 3072 KB 
           clock speeds: max: 3200 MHz 1: 1072 MHz 2: 1191 MHz
Graphics:  Card: Intel Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
           Display Server: X.Org 1.19.6 drivers: intel (unloaded: fbdev,vesa)
           Resolution: 1920x1080@60.01hz
           GLX Renderer: llvmpipe (LLVM 6.0, 128 bits) GLX Version: 3.0 Mesa 18.0.5
Audio:     Card-1 Intel 8 Series/C220 Series High Definition Audio Controller driver: **snd_hda_intel**
           Card-2 Intel Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller
           driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.4.0-170-generic
Network:   Card-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller driver: r8169
           IF: eth0 state: **down** mac: <filter>
           Card-2: **Marvell 88E8001 Gigabit** Ethernet Controller driver: skge
           IF: eth1 state: **up** speed: 1000 Mbps duplex: full mac: <filter>
...
Info:      Processes: 230 Uptime: 9 days Memory: 2830.4/**7687.0MB** Client: Shell (bash) inxi: 2.2.35 

```
Not showing the boring storage/partition/RAID stuff.  Has 24TB+ connected.

It is using a 3rd-gen Intel iGPU. Using old parts, initially spent $126 for a new CPU+MB+8GB RAM.  Dropped in a 4TB Hitachi HDD for the OS and media storage.  It is a plex media server and NAS and Calibre and run a single VM today.  That iGPU handles HW-decoding for mpeg2 and h.264 video, I suppose.  Never really checked.

Anyway, quick and easy overview with 1 command.

---

### Post by wolftrax on 2019-12-17
pretty nifty :) 
anyways I am buying a new stationary (second hand ) which is a dell optiplex and I was thinking I want to use that for media center.  the old laptops I have is over ten years old and I did not expect it to be a bigger project to make a media center set up. 

I was actually hoping mythbuntu stil was available for download. :)

---

### Post by slickymaster on 2019-12-17
Take a look at [MythTV]("https://www.mythtv.org/wiki/Main_Page").

It provides digital video recording functions similar to a TiVo or a Replay, play videos from the file system, from a server, or DVDs.

---

