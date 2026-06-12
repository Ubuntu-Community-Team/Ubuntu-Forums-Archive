---
title: "Can I install an outdated version of lubuntu?"
date: 2017-07-18
forum: General Help
---

### Post by alexander.vk on 2017-07-18
Hi,

I have an old Compaq CQ10-100 netbook.
It has a really weak 1.6gHZ Intel Atom CPU
1GB DDR2 RAM
This computer is about 8 years old.

It's a very old machine with a non working keyboard (I use onboard and run lubuntu just to type some things)

Fair to say this isn't my main machine. It has none of my data or documents or even pictures on it at all.
I never buy anything online and would never use any passowords on it.
However some basic internet browsing and for default apps in general to work would be ideal.

However, the latest lubuntu LTS 16.4 it seems to struggle with quite a lot. It is extremely slow and the CPU applet almost always shows 90%-100% used CPU.

For this reason i'm wondering whether it would be worth it to install an old version of lubuntu, perhaps even the first version 10.4 since the system requirements are lower for this version and would hopefully better run on my machine.

With these specifics in mind, should I try it? And is there anything else I need to consider?
Do apps still work on lubuntu 10.4 or not at all? If they are in their older versions I'm okay with it.

Lastly, thank you for the help :)

---

### Post by Autodave on 2017-07-18
I have an EEEPC netbook: 900mhz with 1 gig RAM and Xubuntu 16.04 runs fine on that. Not the fastest machine around by any means, but it still boots up in a little over a minute. Once booted, CPU usage drops to 2-3%.

I am wondering if the non-working keyboard is the result of some other failure to the machine and that is why it is so slow?

You may have had a botched installation: bad download, HD hiccuped, etc. I would try another download and install.

---

### Post by vocx on 2017-07-18
> **alexander.vk said:**
> Hi,

I have an old Compaq CQ10-100 netbook.
It has a really weak 1.6gHZ Intel Atom CPU
1GB DDR2 RAM
This computer is about 8 years old.

It's a very old machine with a non working keyboard (I use onboard and run lubuntu just to type some things)

Fair to say this isn't my main machine. It has none of my data or documents or even pictures on it at all.
I never buy anything online and would never use any passowords on it.

However, the latest lubuntu LTS 16.4 it seems to struggle with quite a lot. It is extremely slow and the CPU applet almost always shows 90%-100% used CPU.

For this reason i'm wondering whether it would be worth it to install an old version of lubuntu, perhaps even the first version 10.4 since the system requirements are lower for this version and would hopefully better run on my machine.

With these specifics in mind, should I try it? And is there anything else I need to consider?
Do apps still work on lubuntu 10.4 or not at all? If they are in their older versions I'm okay with it.

Lastly, thank you for the help :)
You absolutely can do whatever you want. If you are really convinced you don't mind old software, and no updates, then go ahead. Personally, I would try to investigate the source of the slowdown. Maybe there is a program that is running in the background slowing things down. Install and run "htop" from the terminal to see which programs are running. Uninstall those that you don't need. Office, gone, games, gone, synaptic, gone, software center, gone, video players, gone, etc. Just keep the bare minimum.

Usually with old computers what makes it slow is the graphical user interface. What about using the computer without the graphical interface, just booting into a terminal. You can still browse the web with command line browsers such as "w3m", "lynx" or "links".

You don't need to install a very old version like 10.04, but what about 14.04, which is the previous long term support version before 16.04. Also, I'm pretty sure there are other Linux distributions that cater to that minimalistic segment. You could try one of those as well. As long as the primary use is just downloading files from the net, there is not much you require.

What about buying a Raspberry Pi 3? It's a USD 90 computer (if you include some peripherals) and it gives you a fully functioning Debian-based computer with basically the same specifications as your current PC.

[https://www.raspberrypi.org/learning/hardware-guide/components/raspberry-pi/](https://www.raspberrypi.org/learning/hardware-guide/components/raspberry-pi/)

The Raspberry Pi 3 is the third generation Raspberry Pi. It replaced the Raspberry Pi 2 Model B in February 2016. Compared to the Raspberry Pi 2 it has:

[LIST]
[*]A 1.2GHz 64-bit quad-core ARMv8 CPU
[*]802.11n Wireless LAN
[*]Bluetooth 4.1
[*]Bluetooth Low Energy (BLE)
[/LIST]
Like the Pi 2, it also has:

[LIST]
[*]4 USB ports
[*]40 GPIO pins
[*]Full HDMI port
[*]Ethernet port
[*]Combined 3.5mm audio jack and composite video
[*]Camera interface (CSI)
[*]Display interface (DSI)
[*]Micro SD card slot (now push-pull rather than push-push)
[*]VideoCore IV 3D graphics core
[/LIST]

---

### Post by Autodave on 2017-07-18
Sorry: I should have answered the question in your post subject.  I would not use an older version. I was running 14.04 and prior to that 12.04 on the EEPC. Going to the newer versions did not give me much more load than the version just replaced. You would not gain anything going backwards.

---

### Post by alexander.vk on 2017-07-18
This netbook was my mother's and she didn't look after it, it was exposed to cold temperatures and possibly even wine spilled on the keyboard. I've completely removed the keyboard to give the netbook some space to breathe since it can get quite hot during operation.

My aim would be to have the fastest user experience possible with the limitations in place and since there is no personal data on it, security doesn't really concern me.
If I could leave it download a heavy file for example or just browse in Opera without too much hassle that would be ideal.

P.S. @Autodave There could very well be another problem, maybe the motherboard but I really wouldn't know.

Would installing an older less demanding version of lubuntu make this any better?

---

### Post by alexander.vk on 2017-07-18
So I could download 14.04 rather than 10.4? Are the requirements any different?

They are both outdated though, why would I not just download the one that is most minimalistic?

P.S. I've deleted a lot of unnecessary software. Office, games, image editor, anything I could find that isn't necessary.

Unfortunately I don't happen to be as IT literate as most of you so a GUI interface is essential for me.

Hi, I haven't downloaded any apps yet cause I need to go away but opening the task manager, these processes seem to use up most of the CPU
python
xorg
mount.ntfs
lstask
lxpanel

The top 3 mentioned are almost always the biggest consumers.

---

### Post by vocx on 2017-07-18
> **alexander.vk said:**
> So I could download 14.04 rather than 10.4? Are the requirements any different?

They are both outdated though, why would I not just download **the one that is most minimalistic**?

P.S. I've deleted a lot of unnecessary software. Office, games, image editor, anything I could find that isn't necessary.

The requirements are basically always the same, you need a minimum of 128 MB of RAM, 2 GB of hard space to install. This hasn't changed much in 20 years.

Older is not equivalent to more minimalistic. Things do get bloated over time, so it is possible that the programs of 14.04 and 16.04 are a bit more resource intensive than 10.04. However, it is also possible that 14.04 is also more optimized for lightweight use, so it may actually be faster than a previous version. There is just no way of knowing this without installing and running a standardized test of both installations. The reason 14.04 would be better is, it is a long term support version (LTS) so it is still maintained by developers, and will be until April 2019. After that it will really become obsolete. On the other hand, 10.04 became completely obsolete on April 2015. There is no reason somebody would want to install it except for science (historical research purposes).

Also, an older version such as 10.04 will use an old kernel. The kernel provides hardware drivers for your system. If you use a very old Ubuntu, you may find out your hardware is not supported and it doesn't work. So, going with a newer version, such as 14.04 is better.

> 
Unfortunately I don't happen to be as IT literate as most of you so a GUI interface is essential for me.

Hi, I haven't downloaded any apps yet cause I need to go away but opening the task manager, these processes seem to use up most of the CPU
python
xorg
mount.ntfs
lstask
lxpanel

The top 3 mentioned are almost always the biggest consumers.
Please install "htop", and run it from the terminal, it gives a more detailed output. You can rank the programs under use by memory or CPU use, and try to determine what specific operation is consuming those CPU cycles.

Python is a programming language that runs continuously in the system. It runs things like the applets in the system tray, and some other small utilities like that. Removing it would probably not completely break your system but many things will not work, so I would not remove it. Xorg refers to the graphical user interface. If you have a monitor, and your are seeing things on screen, Xorg is working, so you cannot remove it. As I said, usually slowness happens because of the graphical user interface. Mount.ntfs is the program that I guess keeps your external NTFS hard drive mounted, so maybe if you are writing too much data it will continue working.

Xorg could also have heavy use if the drivers for your video card are not the ideal ones. So, maybe if you can install the restricted drivers for that computer, you may see an improvement. Settings > Software & updates > Additional drivers.

---

### Post by QIII on 2017-07-18
LTS releases of both Xubuntu and Lubuntu get 3 years of support, so 14.04 reached EOL in April of 2017.

The earliest supported LTS of each, then, is 16.04.

---

### Post by alexander.vk on 2017-08-03
Hi guys

Thank you so much for the helpful responses. I've found the cause of the system slowdown and it seemed like keeping my SD card in the netbook made it continuously read it and hence work the CPU. 

I understand that downgrading to an older version wouldn't make it faster, thanks to you guys. 

Anyway looks like the problem is solved. Thank you:)

---

