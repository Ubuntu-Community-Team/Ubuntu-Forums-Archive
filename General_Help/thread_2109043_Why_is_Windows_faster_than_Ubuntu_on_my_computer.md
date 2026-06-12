---
title: "Why is Windows faster than Ubuntu on my computer?"
date: 2013-01-26
forum: General Help
---

### Post by lordfkiller on 2013-01-26
I used to use Ubuntu a couple of years ago, back in Windows XP's era (on a different computer) and I remember it was much faster than Windows.
Recently I switched back to Ubuntu (12.10) But this time it runs more slowly than Windows 7, much more slowly. Opening apps for the first time takes forever (VLC, Chrome, Nautilus etc) Also when I run Windows 7 on Ubuntu with VirtualBox, it is still faster than Ubuntu!

So what's the deal with my Ubuntu? I don't think that's the way it's supposed to be. 

I am using the 64bit version, but I have tried 32 bit one as well and it's no different.

Any help is appreciated!

---

### Post by ibjsb4 on 2013-01-26
Could be your video driver.

Got enough ram?

Have you tried 2D?

There's a chance 12o4 would run faster.

---

### Post by ACubed10 on 2013-01-26
I was going to say, it's probably due to the incorrect drivers being loaded.  Should be way faster than Windows

---

### Post by lichtderwelt on 2013-01-26
the ideea is that nautilius is making on icons that preview. You can disable it from the meniu of tools or preferences nautilius. What I still miss is why is opening faster with right click open then directly double click.

---

### Post by Frogs Hair on 2013-01-26
The Memory and CPU requirements have changed form a couple of years ago so the dual boot will require more resources. Depending on you your hardware you might want to consider Xubuntu or Lubuntu . 12.10 is snappy for me and the XFCE session is even faster than unity.

---

### Post by sudodus on 2013-01-26
Try another desktop environment! I suggest that you download some iso files and try them live (booted from a CD or USB drive)

Lubuntu with the ultra-light desktop environment LXDE
Xubuntu with the light desktop environment XFCE

And as suggested earlier, try the version 12.04 LTS, which is well tested today. That standard Ubuntu version has long time support for 5 years. and that Xubuntu version has long time support for 3 years.

---

### Post by lordfkiller on 2013-01-26
I have tried nouveau, Nvidia driver from its website, and Nvidia proprietary driver from repos, which is what I'm using now. 

I have tried both GNOME and Unity, with and without 3D effects - no difference. 

This is not a dual boot. I currently have only Ubuntu on my system.

I think my hardware is fast enough to run Ubuntu and GNOME or Unity. Specs here: [http://www.superwarehouse.com/Sony_VAIO_CW2QGX_B_Notebook/VPCCW2QGX_B/p/1619055](http://www.superwarehouse.com/Sony_VAIO_CW2QGX_B_Notebook/VPCCW2QGX_B/p/1619055)

Processor
Processor:	Intel Core i7 620M / 2.66 GHz
Max Turbo Speed:	3.33 GHz
Multi-Core Technology:	Dual-Core
64-bit Computing:	Yes
Features:	Intel Turbo Boost Technology
Chipset Type:	Mobile Intel PM55 Express

RAM
Installed Size:	4 GB / 8 GB (max)
Technology:	DDR3 SDRAM, 1066 MHz
Configuration Features:	2 x 2 GB

Video
Graphics Processor / Vendor:	NVIDIA GeForce GT 320M
Video Memory:	512 MB
Total Available Graphics Memory:	2263 MB

I'll probably try LTS version.

---

### Post by sudodus on 2013-01-26
Yes, you have horsepower and memory enough for a lot of eye candy :KS

I am running 12.04 LTS, welcome to 'our user group' ;-)

---

### Post by offgridguy on 2013-01-26
> **sudodus said:**
> Yes, you have horsepower and memory enough for a lot of eye candy :KS

I am running 12.04 LTS, welcome to 'our user group' ;-)
I agree, the specs look good, +1 for 12.04

---

### Post by mattyasaurus on 2013-01-26
> **lordfkiller said:**
> I used to use Ubuntu a couple of years ago, back in Windows XP's era (on a different computer) and I remember it was much faster than Windows.
Recently I switched back to Ubuntu (12.10) But this time it runs more slowly than Windows 7, much more slowly. Opening apps for the first time takes forever (VLC, Chrome, Nautilus etc) Also when I run Windows 7 on Ubuntu with VirtualBox, it is still faster than Ubuntu!

So what's the deal with my Ubuntu? I don't think that's the way it's supposed to be. 

I am using the 64bit version, but I have tried 32 bit one as well and it's no different.

Any help is appreciated!

Hi there! You could try installing 'Preload' -  Its a background service that monitors applications you use. It learns the libraries and binaries you use and then loads them into memory ahead of time so your applications start faster. To install enter the following into Terminal:
```
sudo apt-get install preload
```You could also take a look at your 'Startup applications'. As when you log into Ubuntu applications can automatically start. Also packages can automatically add there own autostart entries. You can control these startup applications from the 'Startup applications' dialog.

[IMG]http://www.howtogeek.com/wp-content/uploads/2012/06/image35.png[/IMG]

Ubuntu hides most of the system's default auto start entries from this dialog. To view them run the following command in Terminal:
```
sudo sed -i ‘s/NoDisplay=true/NoDisplay=false/g’ /etc/xdg/autostart/*.desktop
```

---

### Post by orb9220 on 2013-01-26
Hmmm I'm wondering about that M on video. Is it shared memory from ram?

> Video
Graphics Processor / Vendor: NVIDIA GeForce GT 320M
Video Memory: 512 MB
Total Available Graphics Memory: 2263 MB

Think I read somewhere of the same problem with shared ram for video chipset. Solution was go to the Bios and reserve just 256mb as ceiling for it. As total graphics memory is showing 2263.

Just a thought and don't know if that is your issue.
.

---

### Post by 3rdalbum on 2013-01-26
> **orb9220 said:**
> Hmmm I'm wondering about that M on video. Is it shared memory from ram?



Think I read somewhere of the same problem with shared ram for video chipset. Solution was go to the Bios and reserve just 256mb as ceiling for it. As total graphics memory is showing 2263.

Just a thought and don't know if that is your issue.
.

Shared video memory should never cause slow application startup, only low graphical performance.

There may be a process running on the computer that is erroneously using a lot of CPU time or I/O capability. You can find out if this is the case by looking in System Monitor - nothing should be using more than a couple of percent of CPU.

Program startups will be slightly slower on Linux, unless you have an SSD, due to dynamic linking. Windows uses mostly static linking of libraries which IMHO is inefficient and has security implications.

---

### Post by lordfkiller on 2013-01-27
No it's not shared RAM. The graphics card has its own 512 MB memory. Since it says "Total Available Graphics Memory: 2263 MB" then I suppose it can borrow some more memory if needed.

---

### Post by lordfkiller on 2013-01-27
> **3rdalbum said:**
> Shared video memory should never cause slow application startup, only low graphical performance.

There may be a process running on the computer that is erroneously using a lot of CPU time or I/O capability. You can find out if this is the case by looking in System Monitor - nothing should be using more than a couple of percent of CPU.

Program startups will be slightly slower on Linux, unless you have an SSD, due to dynamic linking. Windows uses mostly static linking of libraries which IMHO is inefficient and has security implications.

CPU is usually under %5 for each core, and more than %50 of my memory is usually  empty and available.

---

### Post by tartalo on 2013-01-27
> **lordfkiller said:**
> I have tried both GNOME and Unity, with and without 3D effects - no difference.

Unity is heavily based on Gnome. In my personal subjective and non scientific experience they are first and second in the slow & unresponsive ranking of DEs. Both slower than Windows 7.

Regardless of the Graphic card driver you choose and other optimizations you might apply, **do try Kubuntu, Xubuntu and Lubuntu**. (KDE might need some customization to fell "faster than Windows")

---

### Post by lordfkiller on 2013-01-27
> **tartalo said:**
> Unity is heavily based on Gnome. In my personal subjective and non scientific experience they are first and second in the slow & unresponsive ranking of DEs. Both slower than Windows 7.

Regardless of the Graphic card driver you choose and other optimizations you might apply, **do try Kubuntu, Xubuntu and Lubuntu**. (KDE might need some customization to fell "faster than Windows")

That's disappointing. Faster speed was the main thing we boasted about when talking to Windows users.

---

### Post by sudodus on 2013-01-27
> **lordfkiller said:**
> That's disappointing. Faster speed was the main thing we boasted about when talking to Windows users.
You have to choose between eye-candy and speed, or get more horsepower and memory, so that you can manage both eye-candy and speed. With the existing hardware you get very good speed running

- Lubuntu with the ultra-light LXDE
- Xubuntu with the light XFCE

You can install several desktop environments into the same Ubuntu and use a light-weight desktop environment, when you watch high definition video, and use Unity or KDE for other tasks, when you want the eye-candy and can afford slower response.

You select the desktop environment for each session at the log in screen.

---

### Post by mcduck on 2013-01-27
> **lordfkiller said:**
> That's disappointing. Faster speed was the main thing we boasted about when talking to Windows users.

Keep in mind that there are many more things one can mean with "fast" than just application startup.

For example, would you consider a setup where applications start slower, but complete their task quicker, to be faster or slower?

Also Windows does preload quite a few of the common applications on startup, so if it's quick aplication startup you are looking for, then following mattyasaurus' suggestion about preload would be worth looking at.

---

### Post by lordfkiller on 2013-01-27
> **tartalo said:**
> Unity is heavily based on Gnome. In my personal subjective and non scientific experience they are first and second in the slow & unresponsive ranking of DEs. Both slower than Windows 7.

Regardless of the Graphic card driver you choose and other optimizations you might apply, **do try Kubuntu, Xubuntu and Lubuntu**. (KDE might need some customization to fell "faster than Windows")

> **sudodus said:**
> You have to choose between eye-candy and speed, or get more horsepower and memory, so that you can manage both eye-candy and speed. With the existing hardware you get very good speed running

- Lubuntu with the ultra-light LXDE
- Xubuntu with the light XFCE

You can install several desktop environments into the same Ubuntu and use a light-weight desktop environment, when you watch high definition video, and use Unity or KDE for other tasks, when you want the eye-candy and can afford slower response.

You select the desktop environment for each session at the log in screen.

I don't believe faster processor or more memory is going to make any difference. I play Call of Duty on this computer! Does GNOME need more resources than that? Besides, my memory is only %34 full all the time and CPU usage in under %10 on both cores.
I doesn't make any difference what I'm doing. As I said, starting applications takes too long, and it doesn't matter whether I am watching HD video or browsing the web or doing nothing at all.

---

### Post by lordfkiller on 2013-01-27
> **mcduck said:**
> Keep in mind that there are many more things one can mean with "fast" than just application startup.

For example, would you consider a setup where applications start slower, but complete their task quicker, to be faster or slower?

Also Windows does preload quite a few of the common applications on startup, so if it's quick aplication startup you are looking for, then following mattyasaurus' suggestion about preload would be worth looking at.

I'm sure Windows doesn't pre load VLC. 

As I said, aside from slow application start ups, everything else is great. Even for VLC, once it opens there's no problem, even when I'm watching a blu-ray quality movie. NetBeans works well also.

I also don't think its the hard-drive because Windows is still fast when run within Ubuntu on a virtual machine.

---

### Post by 3rdalbum on 2013-01-27
It is probably just a difference between dynamic and static linking. Linux does dynamic linking, which does mean slower program startup than static but it saves on RAM and disk space (and download time!). There are also security benefits. One security update in a library will fix all programs that use the library without the program's author having to do anything. 

Startup speeds are a little slower with dynamic linking as it must find libraries from different parts of the disk and work out exactly what is needed.

There may be other things you can try so I'll let others make suggestions. I have noticed VLC is more sluggish to start than on previous systems so I wouldn't mind trying something.

---

### Post by ibjsb4 on 2013-01-27
How bout bring up "top" (with the always on top option) and watching it as you try various programs.  See if it gives any clues.

```
top
```

---

