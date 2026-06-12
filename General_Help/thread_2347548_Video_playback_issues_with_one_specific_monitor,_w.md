---
title: "Video playback issues with one specific monitor, works fine otherwise"
date: 2016-12-26
forum: General Help
---

### Post by luxoboy on 2016-12-26
Hello,

I'm having an issue which is driving me quite crazy!

Let me first introduce the system I'm using:
[LIST]
[*]Asus K73SV laptop 
[*]i5-2410M with Intel Graphics 3000 
[*]Nvidia GT540M 
[*]Ubuntu 16.04 
[*]Kernel 4.4.0 
[*]Laptop monitor is 1600x900 
[/LIST]
Because of the presence of two graphics card, prime is enabled. I am using the Intel integrated graphics card (I've had issues when using the Nvidia card).

Now, the issue I have is that I encounter video playback issues when the video is displayed on a SONY EX500 LDC TV (connected with HDMI). The symptoms are out of sync audio in Kodi, stuttering/frame drops. I hesitated posting this on Kodi forums because I thought it was related to Kodi. But I'm fairly sure it's a wider issue as I've observed some stuttering/frame drops watching videos with VLC for example.

The weird part is that it happens only with that specific monitor. I'm also using another 1080p LCD monitor and it's working fine. It's also working fine with the laptop monitor.
Let me add that this TV is working fine. I used to use it plugged to a Raspberry Pi running OSMC (Kodi) via HDMI and it was also working perfectly.

I've tried different screen configurations: screen expanded, TV only. 
I've also tried to remove ~/.config/monitors.xml.

Here is my xorg.conf (located at /etc/X11/xorg.cong.06272015)
```
Section "ServerLayout"
    Identifier "layout"
    Screen 0 "nvidia"
    Inactive "intel"
EndSection

Section "Device"
    Identifier "intel"
    Driver "intel"
    BusID "PCI:0@0:2:0"
    Option "AccelMethod" "SNA"
EndSection

Section "Screen"
    Identifier "intel"
    Device "intel"
EndSection

Section "Device"
    Identifier "nvidia"
    Driver "nvidia"
    BusID "PCI:1@0:0:0"
    Option "ConstrainCursor" "off"
EndSection

Section "Screen"
    Identifier "nvidia"
    Device "nvidia"
    Option "AllowEmptyInitialConfiguration" "on"
    Option "IgnoreDisplayDevices" "CRT"
EndSection
```

What I don't understand is how this can be monitor specific. Are there other config files regarding Xorg server/monitors that could change the behaviour on a monitor basis?

Do not hesitate if you need more information or config files.

Thank you very much.

---

### Post by SeijiSensei on 2016-12-26
> Here is my xorg.conf (located at /etc/X11/xorg.cong.06272015)
That's a version of xorg.conf created on June 27, 2015.  The real xorg.conf has exactly that name.

I strongly recommend trying to get the NVIDIA card working properly with its proprietary driver so you can take advantage of the special video decoding hardware on the device.  Can you disable the Intel adapter entirely in the BIOS?  That's what I did on the hybrid AMD/Intel laptop I have.  

NVIDIA adapters can have a quirk when used with TVs.  When connected to both my Sony Bravia and my LG the text would be tiny and nearly unreadable.  If that's a problem for you, you can solve it by installing the proprietary NVIDIA driver, then running the command
```
sudo nvidia-xconfig
```
That will create a new version of xorg.conf.  In the "Monitor" section of that file add the line
```
Option "DPI" "100x100"
```
then log out and log back in.  The text should now display correctly.

---

### Post by luxoboy on 2016-12-27
> **SeijiSensei said:**
> That's a version of xorg.conf created on June 27, 2015.  The real xorg.conf has exactly that name.

There is no xorg.conf. And it seems normal for recent versions of Ubuntu.

Unfortunately the technology called "Optimus" (having an Intel GPU + a Nvidia card) doesn't allow to disable the Intel card in the BIOS. That's why it took so much time for a decent support (prime) to be available in Linux.

According to software-properties-gtk ("Additional drivers" tab) I have the proprietary Nvidia driver installed (tested and packaged for Ubuntu). This one is from Ubuntu official repos I think.
And when I switch to the Nvidia card, it gets pretty bad. Even after running nvidia-xconfig. Then the laptop's monitor has resolution of 640*480 and can't be set with a higher resolution.

Ideally yes I would like to use the Nvidia card but it seems to be broken on my system for some reason. I could install the proprietary driver directly from Nvidia but I don't want to because it means reinstall after each kernel update.

But do you really think it's driver related?

**EDIT**
Well after messing around with prime and nvidia settings I managed to get a working display using the Nvidia card.
So that's good news!

The bad news is that I have the same issues with the Sony TV. Playback is working fine with laptop monitor and other LCD external monitor.

---

### Post by SeijiSensei on 2016-12-27
Let's try another player.

```

sudo apt-get install smplayer mpv

```

After installation, launch SMPlayer and go to Options > Preferences.  On the General page, select mpv as the player engine.  Then in the Video tab, choose vdpau as the output driver.  Any better?  If so, see if you can tell Kodi to use the vdpau driver.

I used a Bravia model at least two or three generations older than yours with a couple of different computers and NVIDIA adapters.  Other than the issue with tiny font sizes, it worked fine.

---

### Post by luxoboy on 2016-12-27
Well, it's working.

Using SMplayer with or without vdpau driver, playback is fine.
I had tried enabling/disabling vpdau in Kodi before so I don't think it's related to that.
Seems like Kodi's internal player and VLC struggle with that TV. I didn't think the playback on one screen could depend on the player used - I still don't understand how that's possible!

I guess now I'll have to take a look to have Kodi use mplayer (which seems possible).

Thank you very much for your help!

---

