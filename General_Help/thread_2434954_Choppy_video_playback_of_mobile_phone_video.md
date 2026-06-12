---
title: "Choppy video playback of mobile phone video"
date: 2020-01-14
forum: General Help
---

### Post by carusoswi on 2020-01-14
I am shooting video with a Google Pixel 2 smartphone.  I shot a good bit of footage handheld over the holidays which was buttery smooth.  Used Vegas Pro 16 in Windows 10 to edit it, no problems.  Then, I decided to get a gimbal to improve my efforts.  I am using the Smooth 4 gimbal and have downloaded and installed Filmic Pro ap on my Pixel 2.  I was stunned when I the footage appeared very choppy.  Slow pans look as though I am moving the smartphone over a saw.  This problem was obvious on my screen while shooting, even more obvious when files were transferred to and played back on my PC (via Ubuntu-VLC).  I have written Filmic Pro and Google support for advice.  

I have now discovered that setting the Filmic Pro software to record at 60 FPS rather than its default 24 FPS corrects the problem when shooting, and that footage played back on the phone is also free of choppiness.  However, that footage, when transferred to and played back using Ubuntu-VLC is very choppy.  I booted into Windows 10 and double clicking on those files brings up Windows default video player which also plays the footage smoothly.

So, what is wrong with my Ubuntu setup that is causing this problem.  While I go back a long while with Vegas (version 2 as released by Sonic Foundry), I would much prefer to do my editing in Linux using Blender 2.8.  I am missing something here.  I would appreciate any advice.

Thanks.

Caruso

---

### Post by CatKiller on 2020-01-14
> **carusoswi said:**
> However, that footage, when transferred to and played back using Ubuntu-VLC is very choppy.

VLC doesn't do hardware-accelerated video decoding, even if it's available. mpv does, as an alternative.

---

### Post by carusoswi on 2020-01-14
CatKiller:
Thank you for the reply.  I always though VLC the bee's knees for media playback, but never to late to learn a new trick.  Went to software, installed mpv, enabled all sources via snap, but it will not launch, either directly or via the 'open with' file option.  What am I doing wrong?
Caruso

---

### Post by CatKiller on 2020-01-15
I haven't tried the snap version of mpv (in fact, I remove snapd from my systems so I never have any snaps) but snaps are restricted in where they can read or write to. That might be why mpv can't read your files.

There are ways to configure snaps to be able to read from more places that you could look up, or you could install the standard apt version of mpv instead.

---

### Post by SeijiSensei on 2020-01-15
I'd remove the snap version of mpv then run
```
sudo apt install mpv smplayer
```
SMPlayer is a GUI front-end to programs like mpv and the older mplayer.

---

### Post by carusoswi on 2020-01-17
I appreciate the replies, but so far, no joy.  I made a recording using Codec: H264 - MPEG-4 AVC (part 10) (avc1) (this is what VLC reports) with a resolution of 1280 x 720.  It plays, but is still jerky.  I downloaded MVP, but it will not open on my system for some reason.  I also installed SMPlayer, but it crashes when I try to open a file.

FWIW, I am running an Asus G74sx with 16 GB RAM, Intel Core i7 with Nvidia GeForce GTX 560m 2GB video, if that information helps.

Windows 10 runs any file I throw at it smoothly.  Even VLC displays smooth video in Windows.

My long experience with Ubuntu (from version 6.xx) over the years leads me to expect that the opposite would be true.  Something is not right, and I will have to keep searching for an answer.  BTW, I do use snap aps and am familiar with granting the necessary permissions.

I appreciate the replies, the advice, and have discovered a number of new video players that I will try out on my system.

For now, when I want to edit/render current footage, I will look to Windows and Vegas Pro 16 until I get this (or this gets) sorted out.

Thanks, again.

Caruso

---

### Post by CelticWarrior on 2020-01-17
> **carusoswi said:**
> FWIW, I am running an Asus G74sx with 16 GB RAM, Intel Core i7 with Nvidia GeForce GTX 560m 2GB video, if that information helps.

Have you installed the Nvidia proprietary drivers? Which version?
This information is crucial and should have been in the first post. Your issues seems to be related with the use of the default open-source driver instead of the Nvidia one.

The problems with MPV/SMPlayer are likely to be related with the aforementioned drivers situation but may also be a symptom of other problems.

---

### Post by carusoswi on 2020-01-17
I included what I knew to include and was hoping that any additional information needed to trace my problem would be requested, so, thanks for the request.  Here is what I get in terminal:
```

caruso2@caruso2-G74Sx:~$ sudo lshw -numeric -C display
[sudo] password for caruso2: 
  *-display                 
       description: VGA compatible controller
       product: GF116M [GeForce GT 560M] [10DE:1251]
       vendor: NVIDIA Corporation [10DE]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:32 memory:f2000000-f3ffffff memory:e0000000-e7ffffff memory:e8000000-ebffffff ioport:d000(size=128) memory:c0000-dffff

```

That output seems to confirm that the proprietary drivers are installed and working on my system, but, by all means, if you need additional info, don't hesitate to ask.  I am a consumer of Ubuntu, and, while I have learned a lot over the years, am still no expert.
Thanks for your help.

Caruso

---

### Post by coffeecat on 2020-01-17
> **carusoswi said:**
> That output seems to confirm that the proprietary drivers are installed and working on my system

Not so. See this from your lshw output:

> **carusoswi said:**
> ```
       configuration: driver=nouveau latency=0

```

The nouveau driver is the default open source one, not the proprietary driver.

By the way, I have added BBCode code tags to your terminal output in order to restore formatting and make it readable. Please use code tags when posting output. There is a link for using code tags in my sig if you need it.

---

### Post by TheFu on 2020-01-17
```
driver=nouveau
```
says the system is NOT using nvidia proprietary drivers.
[https://wiki.videolan.org/VLC_GPU_Decoding/](https://wiki.videolan.org/VLC_GPU_Decoding/)

IMHO, any driver issue complains need to be directed, in writing, to the specific vendors involved.  They spend 99% of their driver effort on Windows.

Snaps run in a constrained environment. Sometimes that limits access to important libraries and device capabilities. I don't know if this impacts vlc specifically or not.

I don't use snaps. If I want a program constrained, then I'll do it using one of the many tools available for that purpose.  IMHO, snaps over constrain.

---

### Post by carusoswi on 2020-01-17
> **coffeecat said:**
> Not so. See this from your lshw output:



The nouveau driver is the default open source one, not the proprietary driver.

By the way, I have added BBCode code tags to your terminal output in order to restore formatting and make it readable. Please use code tags when posting output. There is a link for using code tags in my sig if you need it.

CoffeeCat and all others:

Again, I thank you for sharing your knowledge and advice.  I searched Google and there were instructions on how to add proprietary drivers from within the Ubuntu OS:  **[https://itsfoss.com/install-additional-drivers-ubuntu/](https://itsfoss.com/install-additional-drivers-ubuntu/)**

I am posting my output again.  Let me know what you think:

```

$ sudo lshw -numeric -C display
[sudo] password for caruso2: 
  *-display                 
       description: VGA compatible controller
       product: GF116M [GeForce GT 560M] [10DE:1251]
       vendor: NVIDIA Corporation [10DE]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:32 memory:f2000000-f3ffffff memory:e0000000-e7ffffff memory:e8000000-ebffffff ioport:d000(size=128) memory:c0000-dffff

```

Caruso

---

### Post by CelticWarrior on 2020-01-17
Still using *nouveau*...

You may need to disable Secure Boot in UEFI.

---

### Post by carusoswi on 2020-01-17
I see that.  Was looking in the wrong place.  I am making progress, however, and I have learned a few things as well (not so easy for such an old dog!)
Thanks.
Caruso

---

### Post by TheFu on 2020-01-17
Installing nvidia drivers on LTS should be really easy for supported GPUs.  Older GPUs, that don't have support will be harder, or impossible, to install the proprietary drivers.  I ended up replacing a 7200 GS with a 1030 GT last year because nVidia dropped driver support.
[https://www.omgubuntu.co.uk/2019/07/install-nvidia-driver-update-ubuntu-its](https://www.omgubuntu.co.uk/2019/07/install-nvidia-driver-update-ubuntu-its)
I always try to follow guides for the specific release AND from reputable sources which usually have "ubuntu" in their domain name somewhere.  The guide linked above seems excellent and I've used itsfloss before.

It might be necessary to blacklist the nouveau module.

If the system isn't running an LTS release, I haven't any clue. I only run LTS releases.

---

