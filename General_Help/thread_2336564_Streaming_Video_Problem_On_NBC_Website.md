---
title: "Streaming Video Problem On NBC Website"
date: 2016-09-09
forum: General Help
---

### Post by sasafrass452 on 2016-09-09
Whenever I try to play streaming videos on the NBC website, it appears  choppy &/or pixelated. This occurs in both firefox & chromium.  Here are the plugins I currently have installed:

[[IMG]https://s14.postimg.org/9ja8ia25p/Screenshot_from_2016_09_09_09_24_43.png[/IMG]]("https://postimg.org/image/9ja8ia25p/")

---

### Post by DuckHook on 2016-09-09
Need far more info.

[LIST=1]
[*]What driver are you using?
[*]What are your HW specs? Esp GPU, CPU, RAM, monitor resolution? You may just want to post relevant sections of:```
sudo lshw -sanitize
```
[*]What codec does NBC use for their videos? (Those of us who don't use NBC site would have no clue)
[*]Pls post output of:```
lspci -vk | grep -iA13 vga
```
[/LIST]

---

### Post by sasafrass452 on 2016-09-09
The CPU is AMD A8-6410 APU with AMD Radeon R5 Graphics. I have a high resolution monitor, & 4gb of RAM.

I assume NBC uses flash, but I could be wrong. If it's not flash, I don't know what codec they use. Please note, this issue only occurs on their website.

```
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Mullins [Radeon R4/R5 Graphics] (rev 05) (prog-if 00 [VGA controller])
    Subsystem: Lenovo Mullins [Radeon R4/R5 Graphics]
    Flags: bus master, fast devsel, latency 0, IRQ 37
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at f0000000 (64-bit, prefetchable) [size=8M]
    I/O ports at 3000 [size=256]
    Memory at f0d00000 (32-bit, non-prefetchable) [size=256K]
    Expansion ROM at f0a00000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: radeon
    Kernel modules: radeon

00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Kabini HDMI/DP Audio
    Subsystem: Lenovo Kabini HDMI/DP Audio
```

> **DuckHook said:**
> Need far more info.

[LIST=1]
[*]What driver are you using? 
[*]What are your HW specs? Esp GPU, CPU, RAM, monitor resolution? You may just want to post relevant sections of:```
sudo lshw -sanitize
``` 
[*]What codec does NBC use for their videos? (Those of us who don't use NBC site would have no clue) 
[*]Pls post output of:```
lspci -vk | grep -iA13 vga
``` 
[/LIST]


---

### Post by DuckHook on 2016-09-10
> **sasafrass452 said:**
> The CPU is AMD A8-6410 APU with AMD Radeon R5 Graphics. I have a high resolution monitor, & 4gb of RAM.Your APU is an entry-level one but also a relatively recent model. Along with your RAM, which is ample, it really should not have any problem displaying flash content. The results of your lspci look normal with nothing out of the ordinary, and they show that you are using the open-source community maintained *radeon* driver which again is as it should be.> I assume NBC uses flash, but I could be wrong. If it's not flash, I don't know what codec they use. Please note, this issue only occurs on their website.It is odd that this only happens on NBC's site. Therefore, I suspect that they are not using flash (please note that this is just a baldfaced guess&#8213;please don't base your actions on such poor conjecture). Or at least, their version of flash may not be optimized for the Shockwave flash that you have installed.

How did you install your flash? Did you follow these instructions?

[https://help.ubuntu.com/16.04/ubuntu-help/net-install-flash.html](https://help.ubuntu.com/16.04/ubuntu-help/net-install-flash.html)

You might also wish to install Chrome (I'm assuming you are using Firefox) which comes from Google and has built-in flash support. Note that it must be Chrome, not Chromium. Chromium has no flash support (which is conversely why I use it), though it can be added. Since you are looking for flash support, make sure you install Chrome. Chrome is not in the repos. You must go to Google's site. Instructions below.

[https://www.linuxbabe.com/ubuntu/install-google-chrome-ubuntu-16-04-lts](https://www.linuxbabe.com/ubuntu/install-google-chrome-ubuntu-16-04-lts)

---

### Post by sasafrass452 on 2016-09-11
I installed flash with either synaptic or ubuntu software. I have now installed Chrome from google's website, & tried playing a video at nbc's website. It does work better, though I can't say it's perfect.... It seems to start a little pixelated at first(not as bad as firefox), but gets clearer after a minute or so. I'm now testing the extensions that I've added, so I'll see how well they work. I might fully switch to chrome, but I'm not quite decided yet....

> **DuckHook said:**
> Your APU is an entry-level one but also a relatively recent model. Along with your RAM, which is ample, it really should not have any problem displaying flash content. The results of your lspci look normal with nothing out of the ordinary, and they show that you are using the open-source community maintained *radeon* driver which again is as it should be.It is odd that this only happens on NBC's site. Therefore, I suspect that they are not using flash (please note that this is just a baldfaced guess&#8213;please don't base your actions on such poor conjecture). Or at least, their version of flash may not be optimized for the Shockwave flash that you have installed.

How did you install your flash? Did you follow these instructions?

[https://help.ubuntu.com/16.04/ubuntu-help/net-install-flash.html](https://help.ubuntu.com/16.04/ubuntu-help/net-install-flash.html)

You might also wish to install Chrome (I'm assuming you are using Firefox) which comes from Google and has built-in flash support. Note that it must be Chrome, not Chromium. Chromium has no flash support (which is conversely why I use it), though it can be added. Since you are looking for flash support, make sure you install Chrome. Chrome is not in the repos. You must go to Google's site. Instructions below.

[https://www.linuxbabe.com/ubuntu/install-google-chrome-ubuntu-16-04-lts](https://www.linuxbabe.com/ubuntu/install-google-chrome-ubuntu-16-04-lts)

---

