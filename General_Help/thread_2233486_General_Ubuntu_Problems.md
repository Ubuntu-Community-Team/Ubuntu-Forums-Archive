---
title: "General Ubuntu Problems"
date: 2014-07-08
forum: General Help
---

### Post by Electricitee on 2014-07-08
A few days ago I installed Ubuntu 14.04 on my laptop (64bit, Windows 7, Pentium Dual-Core @ 2.30 GHz, 4.00GB RAM). The md5sum checked and I installed it onto a 8gb flash drive. I did not use a swap partition, and the whole 8gb drive was a ext4 partition.

I opted for English on the install but halfway through the steps the language turned to Welsh and I had to use 
google translate to understand it. It would have a dialog of welsh and then the next step would have a english caption. 
Once I installed it the system language was still welsh and I had to download the english language packs. Actually, the english language packs were "incomplete".

Next, the software update thing pulled up. The list of items was buggy (vertical white lines), and then when I clicked out 
of the window my dash disappeared and all it was was the red background of the dash. So I switched to a tty and tried to 
login. Kernel panic.

I had to force shutdown. On startup it looked fine, worked fine, but I tried to open firefox to test things out and 
after loading and typing ubuntu.com in the address bar, firefox froze. Then my dock disappeared again. This time I 
couldn't switch to a tty and ended up force shutting down.

If you need more data/specs please ask, I'm on windows right now and don't know how to find things (data/specs/video card) on it as well as Linux.

Thank you.

---

### Post by craig10x on 2014-07-08
Was reading your other thread about this...many others will chime in with their suggestions and questions to ask you to help you along...just one thing i wanted to mention is it's always a good idea to burn the iso image at the slowest speed you can to avoid errors in the disc which could cause installation problems...not sure if you had done that, but just a suggestion...
The kind of things you experienced is extremely uncommon with ubuntu..usually running live sessions of the disc and installing go perfectly...

Edit: sorry, missed the part that you were trying to install ubuntu on a flash drive rather then your laptop's actual hard drive...so disregard my comments...

---

### Post by Bucky Ball on 2014-07-08
Any chance of a link to the instructions you used to create this persistent USB install or an explanation of how you did it? Was the USB stick blank before you installed (i.e. free/unallocated space or freshly formatted)?

---

### Post by Electricitee on 2014-07-08
USB Stick freshly formatted.

I used the official bootable usb stick page to make a bootable usb stick. Then I booted from that and installed to another, 8gib flash drive acting as the root partition. And then I booted from the 8gib one.

---

### Post by buzzingrobot on 2014-07-08
I've had notices of incomplete language file installation on more than one distribution.  

Ignoring the USB aspect, some of this sounds like a video problem and some sounds like a bad installer (not a faulty image, but errors in the extracted files the installer uses.)

Anyone know if 8Gb is large enough for an install to proceed normally?   I know a bare install here creates a filesystem that takes almost 7Gb, and that's after the installer deletes a considerable number of files before the reboot.

---

### Post by Electricitee on 2014-07-08
How do I fix the "bad installer"? Do I need to re-install with a "good" installer or is what I have fine?

"video problem": How do I fix it? How do I know what things to install...I have an embedded graphics card of unknown specs.

---

### Post by ibjsb4 on 2014-07-09
If I was having that much difficulty with ubuntu, I would try something else.

[http://xubuntu.org/](http://xubuntu.org/)

---

### Post by buzzingrobot on 2014-07-09
> **Electricitee said:**
> How do I fix the "bad installer"? Do I need to re-install with a "good" installer or is what I have fine? 

I don't know. We don't know what the problem really is.  We do know that you were trying an unusual install scenario and that the problems you saw happened when the installer was in control.

i speculated that, perhaps, the installer needs more than 8Gb of space and fails ungraciously when it's not available.

> "video problem": How do I fix it? How do I know what things to install...I have an embedded graphics card of unknown specs.

Executing ```

lspci | grep VGA

```

in a terminal/console will identify the video card in use. Intel video drivers are reliable and contained in the kernel.  They typically "just work".  AMD and Nvidia cards sometimes do not "just work".

---

### Post by mastablasta on 2014-07-09
> **buzzingrobot said:**
> 
Anyone know if 8Gb is large enough for an install to proceed normally?   I know a bare install here creates a filesystem that takes almost 7Gb, and that's after the installer deletes a considerable number of files before the reboot.

it is enough.

one question is was 8 GB really available on the USB. system takes about 6-7 GB depending on Ubuntu distro.


and more importantly is how you installed it? from what did you boot and initialise the install? was it from a CD? from another USB stick? if it's from USB stick how did you create it?


as for the installer if you suspect it is the installer at fault then an alternative option might be to use either minimal install iso or the "one button installer" developed by a forum member.

i still do not understand why would burning speed matter? if recorder is sold with 16x speed then it should record at 16x speed. the very files after burn option is there to check that the burn was done correctly. if it's not available in the burn software, then it is available on ubuntu disk when you boot from it.

---

### Post by buzzingrobot on 2014-07-09
The filesystem consumes a bit of space, so if things were really tight it's conceivable that was the issue. (A 16-gig USB stick here formatted FAT32 shows 15.6 gigs available.) The installer expands the ISO image on the target drive and cleans up after itself when it's finished.

I have one USB stick that seems sensitive to burning speed:  Too slow or too fast both won't work.

---

### Post by Electricitee on 2014-07-09
How I installed it: [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows) for a 4gb flash drive (no persistence). I booted from that and ran the installer. I installed onto another 8gb flash drive. I don't know the speed of which the program burned it. When the empty drive was formatted as NTFS before the installer re-formatted it, there were 7.6 GB of free space.

When I boot into Ubuntu again I'll run the command. Last night I ran Ubuntu for 25 minutes with no issues, and I did everything from installing software to browsing the web to playing a 2d game...and everything worked fine. Why did it just "fix" itself?

Also, if I install programs and take up more space on the 8gb hard drive I'll run out of room. Can I move some of the folders/mount points to another flash drive, or should I re-install on a 32gb flash drive? I plan on storing data on the computer's main NTFS internal HD, for transfer between OS's.

---

### Post by stalkingwolf on 2014-07-09
id reinstall on a 32gb.  I have several Os's installed on thumb drives . I always use  16 gig drives or larger . a little extra fudge room.

---

### Post by Bucky Ball on 2014-07-09
> **Electricitee said:**
> When the empty drive was formatted as NTFS before the installer re-formatted it ...

I mentioned this earlier: generally the USB you are installing FROM should be formatted as FAT32 (in some cases FAT16 I've heard) before you create the bootable image on it. Fresh FAT format.

---

### Post by Electricitee on 2014-07-09
The USB I installed FROM was fat32. The one I installed TO was ntfs before I re-partitioned it to ext4.

And it shouldn't matter because the pendrive linux web site says "[COLOR=#0066ff]Fat16, Fat32, or NTFS Formatted Flash Drive".[/COLOR][COLOR=#0066ff]


[/COLOR][COLOR=#000000][/COLOR]

---

