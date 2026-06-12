---
title: "Having problems playing video and using Openshot Video Editor"
date: 2016-07-29
forum: General Help
---

### Post by gregg3 on 2016-07-29
Hi. I've got an 11 year old Dell Optiplex GX520 that I'm running Xubuntu 16.04 on. I couldn't run a .mov file on it, and I also noticed I couldn't use Openshot Video Editor. I tried playing the .mov in Parole, VLC and Videos. It seemed to do the best in Videos but was still a mess. (The audio seemed okay though.) The symptoms: the video would freeze, there would be a green screen that would take over and noticeable pixelation of a large part of the screen often occurred. I converted the .mov to an .mkv and the .mkv played a little better but still had major problems. So I researched and added Ubuntu Restricted Extras. This helped. The video played better but not properly. The video would play smoothly for a few seconds and then hitch, then smoothly, then hitch and so on. The audio seemed fine. But adding an audio track to a video track on Openshot Video Editor swamped the whole process. One last thought: videos (Youtube and stock video sites etc) play flawlessly in my Chrome browser.

I am a genuine newbie. I have put a new hard drive into this computer (the computer had flamed out at work and they were going to throw it out but  I figured out the hard drive was the reason and salvaged it), doubled the RAM (from 2-->4GB), and really would like to be able to use it to do some light video editing. 

I have asked around a bit and gotten all kinds of advice, including getting a new video card that would supposedly be free or next to nothing, but no one has been able to give me any specific suggestions. Any help would be appreciated. Thank you.

---

### Post by CantankRus on 2016-07-29
Install inxi.
```
sudo apt install inxi
```

and copy and paste your computer details by running... 
```
inxi -b
```

eg
```
**[COLOR="#006400"]glen@Xenial:~$[/COLOR] inxi -b**
System:    Host: Xenial Kernel: 4.4.0-31-generic x86_64 (64 bit) Desktop: Unity 7.4.0
           Distro: Ubuntu 16.04 xenial
Machine:   Mobo: Gigabyte model: GA-78LMT-USB3 v: x.x Bios: Award v: FA date: 04/23/2013
CPU:       Quad core AMD FX-4300 (-MCP-) speed/max: 1400/3800 MHz
Graphics:  Card: NVIDIA GF116 [GeForce GTX 550 Ti]
           Display Server: X.Org 1.18.3 drivers: nvidia (unloaded: fbdev,vesa,nouveau)
           Resolution: 1680x1050@59.88hz
           GLX Renderer: GeForce GTX 550 Ti/PCIe/SSE2 GLX Version: 4.5.0 NVIDIA 367.27
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller driver: r8169
Drives:    HDD Total Size: 870.2GB (13.5% used)
Info:      Processes: 232 Uptime: 8:10 Memory: 1137.2/3933.5MB Client: Shell (bash) inxi: 2.2.35
```

---

### Post by gregg3 on 2016-07-30
> **CantankRus said:**
> Install inxi.
```
sudo apt install inxi
```

and copy and paste your computer details by running... 
```
inxi -b
```

eg
```
**[COLOR=#006400]glen@Xenial:~$[/COLOR] inxi -b**
System:    Host: Xenial Kernel: 4.4.0-31-generic x86_64 (64 bit) Desktop: Unity 7.4.0
           Distro: Ubuntu 16.04 xenial
Machine:   Mobo: Gigabyte model: GA-78LMT-USB3 v: x.x Bios: Award v: FA date: 04/23/2013
CPU:       Quad core AMD FX-4300 (-MCP-) speed/max: 1400/3800 MHz
Graphics:  Card: NVIDIA GF116 [GeForce GTX 550 Ti]
           Display Server: X.Org 1.18.3 drivers: nvidia (unloaded: fbdev,vesa,nouveau)
           Resolution: 1680x1050@59.88hz
           GLX Renderer: GeForce GTX 550 Ti/PCIe/SSE2 GLX Version: 4.5.0 NVIDIA 367.27
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller driver: r8169
Drives:    HDD Total Size: 870.2GB (13.5% used)
Info:      Processes: 232 Uptime: 8:10 Memory: 1137.2/3933.5MB Client: Shell (bash) inxi: 2.2.35
```


Thank you, Rus.

```
gregory@gregory-OptiPlex-GX520:~/Desktop$ inxi -b
System:    Host: gregory-OptiPlex-GX520 Kernel: 4.4.0-31-generic x86_64 (64 bit) Desktop: Xfce 4.12.3
           Distro: Ubuntu 16.04 xenial
Machine:   System: Dell product: OptiPlex GX520
           Mobo: Dell model: 0XG312 Bios: Dell v: A07 date: 03/31/2006
CPU:       Single core Intel Pentium 4 (-HT-) speed: 2992 MHz (max)
Graphics:  Card: Intel 82945G/GZ Integrated Graphics Controller
           Display Server: X.Org 1.18.3 drivers: intel (unloaded: fbdev,vesa) Resolution: 1280x1024@60.02hz
           GLX Renderer: Mesa DRI Intel 945G GLX Version: 1.4 Mesa 11.2.0
Network:   Card: Broadcom NetXtreme BCM5751 Gigabit Ethernet PCI Express driver: tg3
Drives:    HDD Total Size: 320.1GB (8.7% used)
Info:      Processes: 183 Uptime: 8 min Memory: 982.4/3502.7MB Client: Shell (bash) inxi: 2.2.35 

```

---

### Post by yoshii on 2016-07-30
I think I read that OpenShot is dependent upon the gstreamer suite of codecs, good, bad, and ugly.  I am kinda afraid to mess around with installing them because there's so many different variations on them.  But I did notice that AVIdeMux works better after installing xine and it's recommended dependencies even though I don't use xine anymore (I use VLC).  

Also, it's worth knowing that the .MOV format is pretty old now, and probably not very compatible.  I think it's an Apple QuickTime MOVie with MPEG-4 H.264 embedded inside of it.  It's more compatible and modern to just render to H.264 in MP4 or some other older MP4 like xVid or whatnot.  You could also do an MKV (matroska container) with whatever inside of it.  QuickTime and Apple stuff adds and requires a lot of proprietary metadata if I remember correctly.  But it's not necessary for the rest of the world.

---

### Post by CantankRus on 2016-07-31
You will have to research specs of your model.
[**_[COLOR="#B22222"]How to find the product model of your Dell computer[/COLOR]_**]("http://www.dell.com/support/article/us/en/19/SLN298441")
[http://www.dell.com/support/home/us/en/19/Products/desktop/optiplex_desktop](http://www.dell.com/support/home/us/en/19/Products/desktop/optiplex_desktop)

eg pci or pci-express slot for gfx card.
It may need to be a low profile card.

This forum discusses the OptiPlex GX520... [http://www.techsupportforum.com/forums/f24/dell-optiplex-gx520-what-video-card-fits-550947.html](http://www.techsupportforum.com/forums/f24/dell-optiplex-gx520-what-video-card-fits-550947.html)

---

### Post by yoshii on 2016-07-31
I forgot to mention that if you install xine and it's recommended dependencies, i think it provides the needed gstreamer stuff that OpenShot needs.

---

### Post by gregg3 on 2016-08-01
> **yoshii said:**
> I think I read that OpenShot is dependent upon the gstreamer suite of codecs, good, bad, and ugly.  I am kinda afraid to mess around with installing them because there's so many different variations on them.  But I did notice that AVIdeMux works better after installing xine and it's recommended dependencies even though I don't use xine anymore (I use VLC).  

Also, it's worth knowing that the .MOV format is pretty old now, and probably not very compatible.  I think it's an Apple QuickTime MOVie with MPEG-4 H.264 embedded inside of it.  It's more compatible and modern to just render to H.264 in MP4 or some other older MP4 like xVid or whatnot.  You could also do an MKV (matroska container) with whatever inside of it.  QuickTime and Apple stuff adds and requires a lot of proprietary metadata if I remember correctly.  But it's not necessary for the rest of the world.

Thanks yoshii. I'll give xine a shot. (I'd really prefer to at least try to just download something before going through the process of trying to figure out what video card might work and then finding one and installing it etc etc.)

Would this command be the way to go?

```
sudo apt-get install xine-ui libxine1-ffmpeg
```

That is taken from:

[http://ubuntuguide.net/how-to-install-xine-multimedia-player-in-ubuntu](http://ubuntuguide.net/how-to-install-xine-multimedia-player-in-ubuntu)

---

### Post by gregg3 on 2016-08-01
> **CantankRus said:**
> You will have to research specs of your model.
[**_[COLOR=#B22222]How to find the product model of your Dell computer[/COLOR]_**]("http://www.dell.com/support/article/us/en/19/SLN298441")
[http://www.dell.com/support/home/us/en/19/Products/desktop/optiplex_desktop](http://www.dell.com/support/home/us/en/19/Products/desktop/optiplex_desktop)

eg pci or pci-express slot for gfx card.
It may need to be a low profile card.

This forum discusses the OptiPlex GX520... [http://www.techsupportforum.com/forums/f24/dell-optiplex-gx520-what-video-card-fits-550947.html](http://www.techsupportforum.com/forums/f24/dell-optiplex-gx520-what-video-card-fits-550947.html)

Thanks Rus. I went through that tech support link and (from the screenshot 049) my GX520  is the one in the middle. I've attached some photos. I researched pci vs  pci-express and can't really tell which, if either,  would apply to the computer.

When I put my service tag in the Dell model finder all it told me was I had the GX520. 

This is just such an old computer and I'm looking for a cheap easy solution. (Not that there is one.) Thanks.

---

### Post by gregg3 on 2016-08-02
> **yoshii said:**
> I forgot to mention that if you install xine and it's recommended dependencies, i think it provides the needed gstreamer stuff that OpenShot needs.

Tried to install xine. Ran into this:

```
gregory@gregory-OptiPlex-GX520:~/Desktop$ sudo apt-get install xine-ui libxine1-ffmpeg
[sudo] password for gregory: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libxine1-ffmpeg
gregory@gregory-OptiPlex-GX520:~/Desktop$ 
```

---

### Post by gordintoronto on 2016-08-02
Try libxine2-ffmpeg

This kind of thing is a lot easier if you use synaptic package manager, so you can see what is available.

---

### Post by yoshii on 2016-08-02
I'm not sure about libxine, but you could try:  

```

sudo apt-get install --install-recommends xine-ui

```

That should install xine-ui as well as it's dependencies, which are the libs it needs and anything else.  
you could even add "--install-suggests" for it to install even more stuff, although this sometimes add things which really aren't needed.  

I think I accidentally ended up with ISDN service support when I was installing VLC media player with "suggests" turned on.  
But i was able to remove it later.  

I hope this helps.  

But yeah, if you use Synaptic Package Manager, then you can type "xine" into the search form field at the top middle of the screen and get a list of a bunch of stuff related to xine and cherry pick the stuff you want to install.

---

### Post by gregg3 on 2016-08-03
> **gordintoronto said:**
> Try libxine2-ffmpeg

This kind of thing is a lot easier if you use synaptic package manager, so you can see what is available.

Thanks gordin. So from the screenshot it looks like I don't have the libxine2-ffmpeg either, right?

My bad: that screenshot is not from the problem computer. Sorry. (Will post the correct screenshot when I'm on the computer with the problem.)

---

### Post by gregg3 on 2016-08-03
> **yoshii said:**
> I'm not sure about libxine, but you could try:  

```

sudo apt-get install --install-recommends xine-ui

```

That should install xine-ui as well as it's dependencies, which are the libs it needs and anything else.  
you could even add "--install-suggests" for it to install even more stuff, although this sometimes add things which really aren't needed.  

I think I accidentally ended up with ISDN service support when I was installing VLC media player with "suggests" turned on.  
But i was able to remove it later.  

I hope this helps.  

But yeah, if you use Synaptic Package Manager, then you can type "xine" into the search form field at the top middle of the screen and get a list of a bunch of stuff related to xine and cherry pick the stuff you want to install.

Thanks yoshii. I'm not on the that computer but I'll run that command as soon as I am.

---

### Post by gregg3 on 2016-08-04
> **yoshii said:**
> I'm not sure about libxine, but you could try:  

```

sudo apt-get install --install-recommends xine-ui

```

That should install xine-ui as well as it's dependencies, which are the libs it needs and anything else.  
you could even add "--install-suggests" for it to install even more stuff, although this sometimes add things which really aren't needed.  

I think I accidentally ended up with ISDN service support when I was installing VLC media player with "suggests" turned on.  
But i was able to remove it later.  

I hope this helps.  

But yeah, if you use Synaptic Package Manager, then you can type "xine" into the search form field at the top middle of the screen and get a list of a bunch of stuff related to xine and cherry pick the stuff you want to install.

Thanks yoshii. I ran the command. It was kind of strange. xine opened from the terminal the first time (and it was VERY impressive) but then it wouldn't open any more. (Either from the applications menu or the terminal). Anyway, I was able to try the .mov file  in xine and the video was great but within a few seconds the audio cut out. 

I'm calling it  an improvement. 

I'll attach  the last thing that was in the terminal and some screenshots of how it was complaining. At the top of the xine screen it said: There is no mrl

(I really would like to get xine but if not that's okay. I did check Openshot and it played mp4s and mp3s just fine so that was the biggest thing I was looking for.)

```
gregory@gregory-OptiPlex-GX520:~/Desktop$ xine
This is xine (X11 gui) - a free video player v0.99.9.
(c) 2000-2014 The xine Team.
Failed to open VDPAU backend libvdpau_va_gl.so: cannot open shared object file: No such file or directory
vo_vdpau: Can't create vdp device : No vdpau implementation.
gregory@gregory-OptiPlex-GX520:~/Desktop$ xine
This is xine (X11 gui) - a free video player v0.99.9.
(c) 2000-2014 The xine Team.
Failed to open VDPAU backend libvdpau_va_gl.so: cannot open shared object file: No such file or directory
vo_vdpau: Can't create vdp device : No vdpau implementation.
gregory@gregory-OptiPlex-GX520:~/Desktop$ 

```

I really appreciate the help!

---

