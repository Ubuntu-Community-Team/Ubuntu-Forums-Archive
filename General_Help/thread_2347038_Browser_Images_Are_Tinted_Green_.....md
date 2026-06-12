---
title: "Browser Images Are Tinted Green ...."
date: 2016-12-21
forum: General Help
---

### Post by mikey93898 on 2016-12-21
Uhm ... I don't know what the hell is going on with my computer right now, but for the last two days: All the images inside both Chromium and Firefox are tinted green. At first I thought it was some weird thing google was doing to honor an Irish Christmas or something, but no.

I'm guessing it's not exactly a problem with my browser, since multiple browsers are doing this to me right now. And if I save an image, then open it up in an image viewer, it looks normal. So just the browsers.... I'm dumbfounded.

Here's a picture of what these very forums look like to me right now:

[ATTACH=CONFIG]272801[/ATTACH]

I'm using Ubuntu Studio 4.4.0-57-lowlatency

---

### Post by HermanAB on 2016-12-21
Err... maybe you should change your sunglasses?

---

### Post by mikey93898 on 2016-12-21
I only wear sunglasses at night ...

Just another photo for your viewing pleasure. Note that one thumbnail (smaller one) is fine, while the larger image has turned green.

[ATTACH=CONFIG]272802[/ATTACH]

I've already ran: sudo apt-get purge chromium-browser firefox   ... then autoremove and reinstall after deleting .cache ... and nothing. Still green.

---

### Post by vasa1 on 2016-12-21
From #4 in [Posting Guidelines]("https://ubuntuforums.org/showthread.php?t=2158945"): > If you include screenshots, use the forum attachment system rather than an offsite host such as imgur.


---

### Post by vasa1 on 2016-12-21
Do your browsers share common extensions? Have you tried to view images with all extensions disabled?

---

### Post by &amp;KyT$0P# on 2016-12-21
mikey93898, do you have hardware acceleration enabled in either browser?  If so, please disable it, restart the browser, and let us know the results.

---

### Post by mikey93898 on 2016-12-21
> **vasa1 said:**
> From #4 in [Posting Guidelines]("https://ubuntuforums.org/showthread.php?t=2158945"):

Whoops, sorry. Hang on a sec and I'll fix the posts.

---

### Post by mikey93898 on 2016-12-21
Vasa1: Yeah both have the same extensions. I disabled all extensions before I did my full chromium purge and the result was the same ... although I'm about to try again just to be extra sure.

Halogen2: Yes I do have hardware acceleration enabled. If the next chromium purge doesn't fix it, I'll disable hw acceleration and do another.

Will report back! Thank you.

---

### Post by HermanAB on 2016-12-21
It looks like VGA with a broken red wire.

---

### Post by mikey93898 on 2016-12-21
Okay still no luck. I did:

- Disable all extensions
- Delete all chromium temporary files
- Remove folder inside .cache
- Disable hardware acceleration
- sudo apt-get purge chromium-browser
- Reboot system
- Reinstall browser

Still greenstuffs :confused:

Also I'm starting to notice that it may be some weird hue thing, as other images that were mostly blue, have turned reddish/purplish. Green seems way more common, but it's not limited to green.

Here's a screenshot from Wikimedia/Wikicommon's homepage. Note that the video at the bottom looks totally fine. It's only images. And only *certain* images. If you look up at the Michael Cera photo again, the large-sized photo is green'ed, while the thumbnail is fine too.

EDIT: Was going to post some red-ified photos, but the skyline in the wikimedia photo kinda already is, as well.

---

### Post by &amp;KyT$0P# on 2016-12-21
In Firefox, please create a new, clean [profile]("http://kb.mozillazine.org/Profile").  Start Firefox with that profile.  Immediately go into [Firefox Safe Mode]("http://kb.mozillazine.org/Safe_Mode") in this new profile.

Are images still discolored?

If so, please install inxi...
```
sudo apt-get install inxi
```
... and post the output of running this command in Terminal -
```
inxi -Fxxz -! 31
```

---

### Post by mikey93898 on 2016-12-21
> **halogen2 said:**
> In Firefox, please create a new, clean [profile]("http://kb.mozillazine.org/Profile").  Start Firefox with that profile.  Immediately go into [Firefox Safe Mode]("http://kb.mozillazine.org/Safe_Mode") in this new profile.

Are images still discolored?

If so, please install inxi...
```
sudo apt-get install inxi
```
... and post the output of running this command in Terminal -
```
inxi -Fxxz -! 31
```

Thanks for the direction. I reinstalled firefox, made a new profile using the profile manager ("firefox -P"), went to Help->Restart With Addons Disabled, and upon restart, went to twitter, where the homepage images were still discolored.

Here is the output of inxi:

```
System:    Kernel: 4.4.0-57-lowlatency x86_64 (64 bit gcc: 5.4.0) Desktop: Xfce 4.12.3 (Gtk 2.24.28) dm: lightdm
           Distro: Ubuntu 16.04 xenial
Machine:   Mobo: ASUSTeK model: P8Z68-V LE v: Rev X.0x Bios: American Megatrends v: 3903 date: 08/22/2012
CPU:       Quad core Intel Core i7-2600 (-HT-MCP-) cache: 8192 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 27289
           clock speeds: min/max: 1600/3800 MHz 1: 1699 MHz 2: 1684 MHz 3: 1670 MHz 4: 1766 MHz 5: 1625 MHz
           6: 1599 MHz 7: 1661 MHz 8: 1605 MHz
Graphics:  Card: NVIDIA GF119 [GeForce GT 520] bus-ID: 01:00.0 chip-ID: 10de:1040
           Display Server: X.Org 1.18.4 drivers: nouveau (unloaded: fbdev,vesa)
           Resolution: 1280x1024@60.02hz, 1600x900@59.98hz
           GLX Renderer: Gallium 0.4 on NVD9 GLX Version: 3.0 Mesa 11.2.0 Direct Rendering: Yes
Audio:     Card-1 NVIDIA GF119 HDMI Audio Controller driver: snd_hda_intel bus-ID: 01:00.1 chip-ID: 10de:0e08
           Card-2 Intel 6 Series/C200 Series Family High Definition Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0 chip-ID: 8086:1c20
           Card-3 Midiman driver: USB Audio usb-ID: 002-005 chip-ID: 0763:4008
           Card-4 KORG nanoKONTROL2 MIDI Controller driver: USB Audio usb-ID: 002-006 chip-ID: 0944:0117
           Sound: Advanced Linux Sound Architecture v: k4.4.0-57-lowlatency
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169 v: 2.3LK-NAPI port: c000 bus-ID: 06:00.0 chip-ID: 10ec:8168
           IF: enp6s0 state: up speed: 1000 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 7129.4GB (32.1% used)
           ID-1: /dev/sda model: WDC_WD40EZRX size: 4000.8GB serial: WD-WCC4E0SJTPC1 temp: 30C
           ID-2: /dev/sdb model: OCZ size: 128.0GB serial: OCZ-060117PW44S2K912 temp: 0C
           ID-3: /dev/sdc model: ST1000DM003 size: 1000.2GB serial: S1D6N072 temp: 28C
           ID-4: /dev/sdd model: WDC_WD20EARX size: 2000.4GB serial: WD-WCAZAK298144 temp: 34C
Partition: ID-1: / size: 116G used: 29G (27%) fs: ext4 dev: /dev/dm-0
           ID-2: /boot size: 1.9G used: 140M (8%) fs: xfs dev: /dev/sdb1
RAID:      System: supported: N/A
           No RAID devices: /proc/mdstat, md_mod kernel module present
           Unused Devices: none
Sensors:   System Temperatures: cpu: 29.8C mobo: 27.8C gpu: 43.0
           Fan Speeds (in rpm): cpu: 0
Info:      Processes: 351 Uptime: 36 min Memory: 1824.4/24076.1MB
           Init: systemd v: 229 runlevel: 5 default: 2 Gcc sys: 5.4.0
           Client: Shell (bash 4.3.461 running in termin) inxi: 2.2.35
```

---

### Post by &amp;KyT$0P# on 2016-12-21
Ok, before proceeding any further, **back up your entire system!  This is important.**  This graphics stuff can get hairy.

Your CPU has an integrated GPU, aka Intel graphics.  Are you able to try that?

Are you able to try a different driver for your Nvidia GPU, such as the proprietary Nvidia driver in the Ubuntu repositories?


(You're probably thinking, how to try this stuff on your computer?  I've no idea, sorry.  Likely someone else would though.)

---

### Post by lisati on 2016-12-21
> **HermanAB said:**
> It looks like VGA with a broken red wire.

Agreed, but I'm not sure how it would affect screenshots taken with the PrtScr button, if at all.

---

### Post by Impavidus on 2016-12-22
> **HermanAB said:**
> It looks like VGA with a broken red wire.

It looks more like the channels have been cycled. The red shows as green, the green shows as blue, the blue shows as red. But only particular file formats like png and jpeg, not coloured text, videos or gif (I assume that thumbnail is a gif image), so it has something to do with loading/decoding those image formats or the way they are stored in graphics memory. Static images may be stored somewhere else than animations. And only particular applications. Is there anything special in the way chrome and firefox use those same image loading libraries as all the other applications that show the images correctly? Well, yes, they load them progressively. But if this is a bug in the browsers or in libpng or so, why isn't everybody affected? Maybe something to do with the way your graphics driver updates textures that are loaded progressively to graphics memory?

Just brainstorming.

---

### Post by kingneutron on 2016-12-22
--I don't think this is a software issue.  I'd recommend trying your monitor on another PC and maybe look into replacing the VGA cable.  If nothing manifests, backup and reinstall fresh into another partition or drive. (As always, make sure everything is connected right and possibly re-seat the VGA card with the motherboard power unplugged.)

---

### Post by mikey93898 on 2016-12-22
Yeah I feel like it's more likely my graphics card now. If it were libpng/etc, I would have the same problem in normal image viewers.

To those suggesting it's the VGA cable... I can assure you it is definitely not. If it were the cable, 1) All my screenshots would look 100% fine to you as they happen before output to hardware, 2) All images, video, and CSS would see the same issue, 3) It wouldn't be happening on both my monitors (I can drag the browser between both a VGA and a DVI monitor and still get the same problem) , and 4) I'd have this issue in normal image viewers too

I'm still stumped. Thinking about backing up my entire system again real quick with /etc+/var and just wiping this madness, lol. But first, I'll try disabling my graphics drivers as suggested somehow.

---

### Post by mikey93898 on 2016-12-22
Quick update. Sorry if I've already mentioned this, but I just downloaded a green'ed image to my desktop, and it suddenly looks normal. So definitely something wrong with whatever my browsers are using.

EDIT: I just noticed -- Certain Extension colors are changing colors too! Obv I had them disabled, and just turned them back on again after all the tests didn't work.

---

### Post by mikey93898 on 2016-12-23
Friends - I have the answer!

**The long version: **Tried installing NVIDIA drivers from the repos (apparently having forgotten I already had them installed from NVIDIA directly), and then somehow miraculously crashed my entire OS partition to the point where I had to straight-up reinstall the OS. Reinstalled a few programs, brought back my home folder from a second drive, and BLAM - GREEN AGAIN!!!!! Reinstalled the OS a second time and very carefully reinstalled as few programs as possible until the green showed up, until I finally found the culprit:

**Short Version: **It was *dispcalgui* !!!!!!

I have no idea why or how, but apparently either dispcalgui is no longer working correctly, or the color calibration profiles I have for my monitors became corrupted, or some setting somewhere got changed ... I don't really know. All I know is that when I uninstall dispcalgui, my colors go back to normal.

So now I'm just sitting here with my 50 year old Spyder 3 hanging over the screen, hoping that a new calibration file will do the trick. Haha. 

Thank you for everyone who helped try and solve this problem. I can answer any questions or run tests still if you'd like, but I'm pretty sure this is the end of my color nightmare.

(btw: Would this technically count as "Solved", if I still don't know what exactly happened with dispcalgui, and haven't yet confirmed the new color profiles work?)

---

### Post by mikey93898 on 2016-12-23
Okay maybe I didn't quite have the answer, but I'm almost there. Redoing the color profiles was an incredible waste of time, and my stuff is still green. 

**However!** The issue is now fixed in Firefox with the setting in about:config of "gfx.color_management.enablev4" set to true. I guess this instructs Firefox to accept the fact I'm using custom ICC color profiles for my monitors. Everything in Firefox is perfect now.

I'm at a loss for how to do this in Chromium now. There used to be a flag called "--enable-monitor-profile" that worked somewhat, but was removed. So now I need to find some way of addressing this issue with Chromium. Blargh.

Should I stay here or try some other google related forum?

---

### Post by vasa1 on 2016-12-23
> **mikey93898 said:**
> ...
I'm at a loss for how to do this in Chromium now. There used to be a flag called "--enable-monitor-profile" that worked somewhat, but was removed. So now I need to find some way of addressing this issue with Chromium. ...
[http://peter.sh/experiments/chromium-command-line-switches/](http://peter.sh/experiments/chromium-command-line-switches/) has a list of switches. Have you looked there? Maybe search for *color*? Nothing relevant came up with *profile* to my mind.

---

### Post by mikey93898 on 2016-12-24
> **vasa1 said:**
> [http://peter.sh/experiments/chromium-command-line-switches/](http://peter.sh/experiments/chromium-command-line-switches/) has a list of switches. Have you looked there? Maybe search for *color*? Nothing relevant came up with *profile* to my mind.

 Thanks man. I'll check it out. I suppose for now, it won't be the end of the world to switch back to firefox for awhile.

---

