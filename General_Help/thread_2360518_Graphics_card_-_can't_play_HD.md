---
title: "Graphics card - can't play HD"
date: 2017-05-05
forum: General Help
---

### Post by fund_raiser on 2017-05-05
Hi,

I embedded discrete graphics card gt 710 into my mobo just to increase video performance. Next through "additional drivers" I installed nvidia driver *version 375.39 from nvidia-375 (proprietary, tested). *Very oddly, I can't play YT vidios with 720p or 1080p - the picture hangs/stops. 480p video is OK. I checked the card on win7 (the same computer as I use dual boot) and I was able to play the 1080p videos with no problem at all.  On win7 all is fine. What is wrong on Lubuntu? Shall I install sth else?

The driver seems to be installed properly as *System tools* has on its list *Nvidia X server settings*, which I can open and navigate through. Previously I used integrated Intel graphics (mobo: g31m-es2l).

My computer is running Lubuntu32 bits

Thx

---

### Post by fund_raiser on 2017-06-17
Hi

Lubuntu is designed for older machines. My machine is not totally old as it is about 9 years. However as I have learned Linux does not support hardware acceleration, and as a result you can't watch hd videos on you-tube because the graphics card is not used as it should be. What I mean is that linux uses CPU to play hd videos it doesn't use graphics card. As a result to play hd video you need good CPU. 

My story:
I used to use integrated graphics but I found that I can't play 720p  on you-tube. Then I bought a discrete graphics card to fix the problem.  But nothing has changed! 
I did try both proprietary and none-proprietary nvidia driver, but to no avail.

So you can't use Lubuntu on older machines to play 720p video. In my case when I play 720p video on you-tube the CPU usage is 100% and the picture hangs every few seconds, whereas on win 7 the CPU usage is 10%(!). I think the problem is the driver and poor support of it on Linux. 

After digging I found as stated above linux do not support hardware acceleration. So what is Lubuntu for? For typing letters? If it doesn't use HA (hardware acceleration) then even pages load slower. What shall I do? What does it look like on your machines? Shall I switch from Lubuntu to Ubuntu? Will it change anything. My CPU is E2220, 2 GB DDR2, brand new graphics GT710.

---

### Post by lisati on 2017-06-17
Threads merged.

If help isn't forthcoming within a day or two, it is acceptable to [BUMP]("http://www.webopedia.com/TERM/T/thread_bump.html") your thread into view. All we ask is that you don't make more than one "BUMP" within the space of 12 hours.

---

### Post by vasa1 on 2017-06-17
> **fund_raiser said:**
> ...

Lubuntu is designed for older machines. ... However as I have learned Linux does not support hardware acceleration, ...
After digging I found as stated above linux do not support hardware acceleration. So what is Lubuntu for? For typing letters? ... ... Shall I switch from Lubuntu to Ubuntu? Will it change anything. ...
Yes, you can use Lubuntu and any other distro or operating system for typing letters. So let's not have anymore derogatory comments.

As you've stated twice, Linux doesn't support hardware acceleration and so why should the change from Lubuntu to Ubuntu change anything?

---

### Post by santosh83 on 2017-06-18
Hi fund_raiser,

I don't think it's quite correct that *Linux* doesn't support hardware accelerated videos. It does just fine. The problem are *browsers*. AFAIK, Firefox is yet to get hw acceleration support on Linux (it has this on Windows). I think (I may be wrong here, in any case a quick Web search will set you straight) Chrome is in the same boat. If you **download** the YouTube videos and then play them via an installed media player like VLC, you'll find that hardware acceleration does work (unless your graphics card is completely unsupported on Linux, which shouldn't be the case for the most popular models out there).

So yes, apparently hardware acceleration within browsers has some roadblock on Linux. Folks keep saying it'll land soon. In the meantime I guess you'll have to download the videos and watch them from a dedicated app.

---

### Post by TheFu on 2017-06-18
Remember reading that Firefox doesn't enable HW accel video on Linux by default. There is a setting in the about:config for that ... [http://www.omgubuntu.co.uk/2017/04/small-tweak-makes-firefox-linux-run-much-faster](http://www.omgubuntu.co.uk/2017/04/small-tweak-makes-firefox-linux-run-much-faster)> 
Enable Hardware Acceleration in Firefox

Firefox comes with hardware acceleration disabled on all Linux distributions (alright, citation needed, but anecdotally this does seems to be the case).
....
type about:config in the address bar, and hit enter/return.

Using the search box to find the *layers.acceleration.force-enabled* setting. Double-click on the ‘false’ listed under the ‘value’ column to set it to ‘**true**’.


No sure if restarting the browser or rebooting is needed after.

---

### Post by SeijiSensei on 2017-06-18
Open a YouTube video in full-screen mode, right-click on the image, and choose Settings.  Check the box to enable hardware acceleration if it is not checked.  If it was not enabled, that change will probably fix the problem. Otherwise....

I have a GTX 750 with the most recent driver available for 14.04 installed -- 375.39, the same as you.  Everything plays at the best-available resolution.

Let's try something other than YouTube.  Install smplayer and mpv ("sudo apt install smplayer mpv") and try to play a 720p or 1080p video file.  If you don't have any, you can get some samples here: [http://www.h264info.com/clips.html](http://www.h264info.com/clips.html).  Start smplayer, then use Options > Preferences and select "mpv" as the "engine" from the General tab and "vdpau" as the Output Driver in the Video tab.  Now play a sample file.  How does it do?

SMPlayer comes with an accessory called SMTube to play YouTube videos locally.  If you find you cannot play something on YouTube with your browser and Flash, try playing the same video with SMTube.

VDPAU is NVIDIA's technology for decoding H.264 videos with its on-board hardware codec.  Both choosing "enable hardware acceleration" in Flash or the "vdpau" driver in SMPlayer turn on this feature for their respective players.  It's pretty mandatory for highly-compressed modern videos especially on machines with weaker CPUs.

---

### Post by TheFu on 2017-06-18
You can also just use mpv from the command line with a URL.
```
$ mpv [https://www.youtube.com/watch?v=04wQXRNfcd0](https://www.youtube.com/watch?v=04wQXRNfcd0)
```

And there's **youtube-dl** to pull the content local first, if the internet connection is poor.
 
All my recent experience is with onboard Intel iGPUs. Don't recall when they started including video decoding. My Asus Eee 1008H didn't have any.  That had an N280 Atom.

My current laptop has an Intel HD Graphics 5500 (Broadwell GT2) and doesn't have any issues with video playback.

---

### Post by fund_raiser on 2017-07-09
So your laptop is quite a new machine. Go and see your CPU usage at 1080p on YT ... 

I have upgraded my machine too. I am using g2020 and the integrated **GPU Intel HD Graphics**. Computer is capable of playing 720p but at the CPU usage 60-70%. 

But the reason why I am writing this post here is that when I watch video with SMplayer there is no v-sync. I can see vertical tearing. Is there a simple way to enable v-sync in SMplayer?

Lubuntu user

---

### Post by efflandt on 2017-07-09
See if you can find out what version your PCI Express (PCIe) slot is. I suspect it is PCIe 1.0. While PCIe 2.0 or 3.0 are backwards compatible with even PCIe 1.0, in my experience PCIe is just to slow to effectively make full use of a modern graphics card.

For example I tried putting my GTX 750 Ti (PCIe 3.0) in an old Dell Dimension 4700 with PCIe 1.0 and it worked, but for full screen DVI connected real 720p (1280x720) screen, YouTube videos would drop frames (freeze momentarily). I was not until I tried my GTX 550 Ti (PCIe 2.0), which also dropped frames that I discovered that it would play YouTube videos smoothly if throttled to 480p. Both of those graphics cards work fine for streaming HD on 1080p screen in my main PC with PCIe 2.0 slot (which is 7 years old from 2010). 

So while the the GT 710 is a fairly low end graphics card, in that old PC even a better graphics card is unlikely to work any better if it has a PCIe 1.0 slot.

---

