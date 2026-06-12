---
title: "Why is Ubuntu so slow compared to Win 10 on my laptop?"
date: 2021-05-23
forum: General Help
---

### Post by vitalifrolov on 2021-05-23
Hello everyone, 

I decided to give Ubuntu a try instead of windows. Installation was easy, and all the programs I need are here. I mostly only use the web browser (opera).

So first thing I noticed after a couple of days of using Ubuntu is how slow everything is. I mean the interface is noticeably slower when you click on something, like the apps menu takes almost 1 second to open. Applications take longer to start. 

Watching YouTube on 1080 I can see slight stuttering and when switching between full screen and normal it takes literally 3 seconds, I counted. I did check with Firefox and it is much better. But i like to use opera, and in windows it is much faster.

Also in windows everything looks better, the image is sharper I guess. 

I have quite a good hardware configuration: 

Thinkpad Yoga X1 gen3
Intel® Core™ i7-8550U CPU @ 1.80GHz × 8
Mesa Intel® UHD Graphics 620 (KBL GT2)
16GB RAM

Is this normal or am I doing something wrong? I always thought Linux should be faster than windows. Is where something I can check or modify to improve things?

---

### Post by ActionParsnip on 2021-05-23
Linux isn't always faster than Windows. Windows isn't always faster than Linux. I can make either OS run as fast or as slow as any other. It's all about configuration, set up and services.
A Linux system running MySQL, LDAP, Email and playing Doom3 at full resolution will run slower than a Windows 10 system that has just logged in with Notepad open.....

---

### Post by vitalifrolov on 2021-05-23
Any advice on how to modify the settings it to make it faster?

---

### Post by SeijiSensei on 2021-05-23
In some areas, like software updates, Linux is far faster than Windows. I can update my entire system in a couple of minutes. Windows, on the other hand, ....

---

### Post by oldfred on 2021-05-23
This is all related to boot, but some settings may improve performance also.
Slow Boot --------------------------------
[https://ubuntuforums.org/showthread.php?t=2450783](https://ubuntuforums.org/showthread.php?t=2450783)
[https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499](https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499)
[https://ubuntuforums.org/showthread.php?t=2417453](https://ubuntuforums.org/showthread.php?t=2417453) & 
[https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392](https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392) & 
[https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html](https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html)
[https://askmeaboutlinux.com/2019/11/28/how-to-speed-up-boot-time-on-linux-if-it-boots-slowly/](https://askmeaboutlinux.com/2019/11/28/how-to-speed-up-boot-time-on-linux-if-it-boots-slowly/)


Both Windows & Ubuntu work much better with an SSD.

But I was able to install Kubuntu in my 2006 Intel CoreDuo with 1.5GB of RAM and it would work reasonably well after adjusting some settings.
On that low end system, full Ubuntu would not install, years ago full Ubuntu would install, but  be slow and I could only open one large app and maybe a couple small apps. If I opened more or lots of tabs in Firefox, it turned gray, and I could tell it was using swap. I typically installed a lighter weight gui for that old system and then it worked a bit better.

---

### Post by vitalifrolov on 2021-05-23
Booting is not a problem. It boots quite fast. I do have an SSD and 16gb of Ram and a fast processor. It should be fast. My main concern is the slow interface and opera browser.

---

### Post by grahammechanical on 2021-05-23
So, your question should be: "Why is the Windows version of Opera so much faster than the Linux version of Opera?" That is a question that you should be asking the developers of Opera.

You buy a laptop pre-installed with Windows 10. There has been cooperation between the Microsoft developers and the makers of the hardware to set up everything just fine. You then install another operating system that is crafted to run on a range of hardware and where there has been little or no cooperation between the makers of the hardware and the developers of the operating system. And that situation is the answer to your question of "Why?"

A lot of us are just thankful that we are able to install a Linux distribution and get decent use out of it. Try installing a Linux distribution on the very latest, high specification hardware. You quite likely will find that some of the hardware is not recognised. In Linux it is the Linux developers that provide hardware drivers. With Microsoft Windows it is the hardware manufacturers who provide the Windows drivers. They want their hardware to be compatible with Microsoft Windows. Otherwise it will not be used in machines for sale. The manufacturers do not see Linux as a means of making money. And it takes a while for the Linux developers to catch up. Especially as no one is providing free samples of hardware to test the drivers on.

For example, the mouse I am using came with a Windows driver. Without it the mouse would not work on Windows. But there was no Linux driver. I did not need it as Linux came with suitable drivers as part of the OS.

I would like to buy a laptop pre-installed with Ubuntu. The trouble is, those suppliers who sell machines with Linux pre-installed seem to think that only Linux developers would want one of their machines. So, the machine is highly specified with an equally high price. The manufacturers do not expect to sell Linux machines to the mass market.

Regards

---

### Post by Impavidus on 2021-05-23
Are there any background tasks taking too much CPU time? Use top or some equivalent tool to check. Is it using swap? It shouldn't with your RAM. Graphics driver problems can also cause this, but aren't expected with Intel graphics.

---

### Post by ActionParsnip on 2021-05-23
What is the output of
```

sudo lshw -C display

```
Thanks

---

### Post by vitalifrolov on 2021-05-23
```
~$ sudo lshw -C display

  *-display                 
       description: VGA compatible controller
       product: UHD Graphics 620
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       logical name: /dev/fb0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom fb
       configuration: depth=32 driver=i915 latency=0 mode=2560x1440 visual=truecolor xres=2560 yres=1440
       resources: iomemory:2f0-2ef iomemory:2f0-2ef irq:167 memory:2ffa000000-2ffaffffff memory:2fa0000000-2fafffffff ioport:e000(size=64) memory:c0000-dffff
```

I checked with HTOP and I am using only about 2GB of RAM, and almost no processor power. I think its normal. I guess I was expecting more, everyone is saying how fast Linux is, so I was kinda expecting to get a performance boost. Will use Firefox instead of Opera. Its like 1.5 times faster, and YouTube is much smoother in Firefox.

---

### Post by pantazi on 2021-05-24
I use a 10 year old HP8460p laptop running Focal Fossa, stripped out apps not required and after reading the forum recently regarding the Brave browser, swapped to that from Firefox just to see if there was any difference.
Immediately my system is much quicker (it wasn't slow before) and the screen is noticeably sharper. I wouldn't return to Windows ever. Three years now with Ubuntu and I'm 73 years young!

---

### Post by riverhawk on 2021-05-24
My advice would be to install Xubuntu. it's basically Ubuntu, but has Xfce instead as a windows manager. Xfce is very lightweight and runs really fast.

---

### Post by dddman on 2021-05-24
My machine is a couple of years old and with similar specs.  I run Ubuntu 20.04 and really don't see any blazing speed difference.  I think the difference comes to play on old machines with less cores/ram/slow clock.

---

### Post by HermanAB on 2021-05-25
Hmmm, with those specs it should work fine, being similar to my old and trusty Macbook Pro.  I think that you have a bad video device driver.  My way to fix that, is to install ffmpeg and check the video performance with glxgears.

---

### Post by vitalifrolov on 2021-05-25
I have ffmpeg installed. With glxgears I get: 301 frames in 5.0 seconds = 60.012 FPS. 

I guess my system is running normally. Its just you guys probably cant compare it if you are just using only 1 OS on your computer. In my case I have a dual boot set up and win 10 is much snappier and looks nicer. I will check out some other Linux flavors, looks like Ubuntu not for me.

---

### Post by dragonfly41 on 2021-05-25
I can report that my Windows 10 (on internal hard drive)  is much less "snappier" than Ubuntu 20.04.
I went through an "upgrade" yesterday and it took more than an hour.
Then I have to wait for antivirus to go through its paces.
I installed EASUS Cleanup to clean up 500MB of junk.
Navigation is not crisp.

Rebooting out into Ubuntu 20.04 running on external USB SSD is much snappier.

---

### Post by dddman on 2021-05-25
I also run win10, but I don&#8217;t dual boot.  I first set up dual boot and it worked fine, but for me it was a removal nightmare.    I prefer to run both systems concurrently being able to choose between them with a click of the mouse.  Virtualbox will do this without having to partition the drive or make any changes to Windows boot software.
 
 Unlike you, I find them both to be fast.  I can&#8217;t help but feel you suffer from some sort of glitch with yours.  Maybe reinstall a different version and/or flavor, that can be done right on top of the current install.  As for looks, there is no end to customizing a desktop.
 
 Good luck either way

---

