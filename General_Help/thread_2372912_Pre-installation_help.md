---
title: "Pre-installation help"
date: 2017-09-30
forum: General Help
---

### Post by shreyas93 on 2017-09-30
Hi,
I have an Asus E200HA laptop with Intel® Cherry Trail Quad-Core Z8300 Processor, 1.84 GHz. It has 2GB ram and 32GB  eMMC (28.3 available). I am planning on installing xubuntu on this laptop. I have never used a distro before and was wondering if this pc is good enough to run xubuntu without problems. It currently runs windows 10, which eats up most of my storage space. How much space will xubuntu take up? And is there any better lightweight alternative. 
Thanks!

EDIT: So i tried live booting xubuntu 16.04, on my first 2 attempts my laptop shut down after the xubuntu loading screen. On my third attempt i got the following error
[ATTACH=CONFIG]276934[/ATTACH]
How should i proceed?

---

### Post by mörgæs on 2017-09-30
Hi, welcome to the fora.

Yes, Xubuntu will most likely run fine. I would expect it to take a maximum of 5 GB of hard disk space. 

I suggest that you try a live boot of a 64 bit Xubuntu 17.04 and see if you like the performance. If not then Lubuntu is another alternative.

---

### Post by shreyas93 on 2017-09-30
Thanks for the quick response mate. Will try out the live boot :D

---

### Post by shreyas93 on 2017-09-30
Hi, 
I have 2 external NTFS formatted HDD, will they work with xubuntu?

---

### Post by slickymaster on 2017-09-30
Yes, Linux systems read and write on NTFS file systems.

---

### Post by shreyas93 on 2017-09-30
Thanks :)

---

### Post by shreyas93 on 2017-10-02
[COLOR=#000000]So i tried live booting xubuntu 16.04, on my first 2 attempts my laptop shut down after the xubuntu loading screen. On my third attempt i got the following error[/COLOR]
[[IMG]https://ubuntuforums.org/attachment.php?attachmentid=276934&d=1506922584&thumb=1[/IMG]]("https://ubuntuforums.org/attachment.php?attachmentid=276934&d=1506922584")
[COLOR=#000000]How should i proceed?[/COLOR]

---

### Post by mörgæs on 2017-10-02
Are 17.04 or 17.10 (beta) better?

---

### Post by ian-weisser on 2017-10-02
> **shreyas93 said:**
> [COLOR=#000000]So i tried live booting xubuntu 16.04, on my first 2 attempts my laptop shut down after the xubuntu loading screen. On my third attempt i got the following error[/COLOR]
[[IMG]https://ubuntuforums.org/attachment.php?attachmentid=276934&d=1506922584&thumb=1[/IMG]]("https://ubuntuforums.org/attachment.php?attachmentid=276934&d=1506922584")
[COLOR=#000000]How should i proceed?[/COLOR]

Your hardware is overheating. Fix or replace it. That's why it's shutting down unexpectedly.
Does not seem like an Ubuntu issue.

---

### Post by mörgæs on 2017-10-02
I would first try a live boot of a recent Xubuntu. Power management could have improved. 

Are the air channels clean?

---

### Post by shreyas93 on 2017-10-05
Got my live boot to work!(Don't know why or how). But the OS itself seems very buggy. The wifi did not work, neither did the audio. Even the mouse seemed laggy. Is this an issue with the live boot or the OS itself? I loved the look and feel of the OS and would love to install it. But if these problems are persistent in the OS, I might be better off with Windows.

---

### Post by ian-weisser on 2017-10-05
Your experience differs from mine - I recently installed on different hardware, and everything worked perfectly out-of-the-box. Of course, my release of Ubuntu is newer and my hardware is older than yours.

Your problems are "persistent in the OS" in the sense that you happen to have purchased hardware that requires additional work to function with Linux.
It's the component manufacturer's responsibility to ensure their compatibility (driver) is added to the Linux kernel. Many manufacturers do, some shoddy manufacturers don't.

How much work? It depends upon your hardware.
Within the live environment, open a terminal. Use the commands 'lshw', 'lsusb', and 'lspci' to determine the exact model of your non-functioning component (wireless, audio, etc.)
Then search here for that model number to see how others made it work.

The main reason for the original creation of Live environments was to test hardware compatibility. Different hardware behavior after install (works Live but fails Installed) is only occasional, and usually due to settings that are easily changed.

EDIT: Of course, your hardware looks *newer* than mid-2015, so it's unlikely that 16.04 will work well for you. Those drivers were simply not added to the kernel yet. Try a much newer release of Ubuntu.

---

### Post by vasa1 on 2017-10-05
> **shreyas93 said:**
> Got my live boot to work!(Don't know why or how). But the OS itself seems very buggy. The wifi did not work, neither did the audio. Even the mouse seemed laggy. Is this an issue with the live boot or the OS itself? I loved the look and feel of the OS and would love to install it. But if these problems are persistent in the OS, I might be better off with Windows.If Windows runs better on this particular machine, you would be better off with Windows. OTOH, you could try your live USB on another machine. You may have better luck!

---

### Post by mörgæs on 2017-10-05
The live boot is a frozen image from the release date. It has not received updates which the installed version has on a daily basis.

Therefore a real (updated) install always works better than the live boot.

Which release of Xubuntu did you try?

Wifi often needs certain settings. This is nothing special for your hardware.

---

### Post by shreyas93 on 2017-10-05
Tried Xubuntu 16.04

---

### Post by shreyas93 on 2017-10-05
Thanks. Will try it out.

---

### Post by mörgæs on 2017-10-05
Now posting third time: You should try a recent Buntu, perferably 17.10. 

Your hardware is a few months old. How can you expect stale software like 16.04 (though partly upgraded since the release) to support what was at that time future hardware? 

Signing out.

---

### Post by shreyas93 on 2017-10-07
Ok. I'll try the latest version. Hopefully it'll work fine. Thanks :)

---

### Post by shreyas93 on 2017-10-20
So I finally got around to trying xubuntu 17.04(the latest one). In the live boot everything seems to work fine except the internet. My laptop connects to the wifi but no pages load. Is this just for the live boot? Will it work after a proper install? Also, my SD card is not detected. Any solutions?

---

