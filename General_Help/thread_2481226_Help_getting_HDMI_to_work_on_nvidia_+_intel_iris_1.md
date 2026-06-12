---
title: "Help getting HDMI to work on nvidia + intel iris 12th gen laptop"
date: 2022-11-22
forum: General Help
---

### Post by xeraster on 2022-11-22
I have this Clevo laptop. It's model number is v155pnjq. It has a 12th-gen 12500h cpu, nvidia graphics and also intel integrated iris graphics. It's also running an insyde bios and there is no way to update the bios or that I've found.

I cannot get the hdmi port to work for anything. A second monitor never shows up in nvidia settings or in display settings.

Secure boot is disabled. I tried nvidia driver 515 and 520. I attempted to install optimus which is from my understanding a hybrid graphics manager but that just made aptitude report errors and l couldn't install stuff anymore until I reinstalled the os.

I've removed "nomodeset=x" from everything I can find. I tried nomodeset=1 and nomodeset=0 in all the files I removed nomodeset from (nothing different happened regardless of what I tried) I tried adding "nomodeset=0" to grub. I tried adding "nomodeset=1" to grub. I tried it without nomodeset. I tried prime-select nvidia. I tried prime-select intel. I tried using mainline to update to the latest kernel of 6.0.9. I tried reinstalling ubuntu a few times. I'm running kernel 5.15.0-53 as I just reinstalled after rendering my ubuntu install unbootable because I was copy-pasting random stuff from forum posts in kind of a last-ditch effort.

xrandr -q shows:

```

Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 32767 x 32767
eDP-1-1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 344mm x 193mm
   1920x1080    144.15*+  60.01    59.97    59.96    60.20    59.93  
   1680x1050     59.95    59.88  
   1400x1050     74.76    59.98  
   1600x900      59.99    59.94    59.95    59.82  
   1280x1024     85.02    75.02    60.02  
   1400x900      59.96    59.88  
   1280x960      85.00    60.00  
   1440x810      60.00    59.97  
   1368x768      59.88    59.85  
   1280x800      59.99    59.97    59.81    59.91  
   1152x864      75.00  
   1280x720      60.00    59.99    59.86    59.74  
   1024x768      85.00    75.05    60.04    85.00    75.03    70.07    60.00  
   1024x768i     86.96  
   960x720       85.00    75.00    60.00  
   928x696       75.00    60.05  
   896x672       75.05    60.01  
   1024x576      59.95    59.96    59.90    59.82  
   960x600       59.93    60.00  
   832x624       74.55  
   960x540       59.96    59.99    59.63    59.82  
   800x600       85.00    75.00    70.00    65.00    60.00    85.14    72.19    75.00    60.32    56.25  
   840x525       60.01    59.88  
   864x486       59.92    59.57  
   700x525       74.76    59.98  
   800x450       59.95    59.82  
   640x512       85.02    75.02    60.02  
   700x450       59.96    59.88  
   640x480       85.09    60.00    85.01    72.81    75.00    59.94  
   720x405       59.51    58.99  
   720x400       85.04  
   684x384       59.88    59.85  
   640x400       59.88    59.98    85.08  
   576x432       75.00  
   640x360       59.86    59.83    59.84    59.32  
   640x350       85.08  
   512x384       85.00    75.03    70.07    60.00  
   512x384i      87.06  
   512x288       60.00    59.92  
   416x312       74.66  
   480x270       59.63    59.82  
   400x300       85.27    72.19    75.12    60.32    56.34  
   432x243       59.92    59.57  
   320x240       85.18    72.81    75.00    60.05  
   360x202       59.51    59.13  
   360x200       85.04  
   320x200       85.27  
   320x180       59.84    59.32  
   320x175       85.27  
DP-1-1 disconnected (normal left inverted right x axis y axis)
HDMI-1-1 disconnected (normal left inverted right x axis y axis)
DP-1-2 disconnected (normal left inverted right x axis y axis)
DP-1-3 disconnected (normal left inverted right x axis y axis)
DP-1-4 disconnected (normal left inverted right x axis y axis)
HDMI-1-2 disconnected (normal left inverted right x axis y axis)

```

I found a thread (that I forgot the link to) where someone said to try  to manually add stuff to the disconnected hdmi outputs. I couldn't get  it do do anything other than report crtc errors for every valid crtc  from 0 to 3.

```
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 520.56.06    Driver Version: 520.56.06    CUDA Version: 11.8     |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|                               |                      |               MIG M. |
|===============================+======================+======================|
|   0  NVIDIA GeForce ...  Off  | 00000000:01:00.0 Off |                  N/A |
| N/A   42C    P0    18W /  N/A |    290MiB /  4096MiB |     10%      Default |
|                               |                      |                  N/A |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                                  |
|  GPU   GI   CI        PID   Type   Process name                  GPU Memory |
|        ID   ID                                                   Usage      |
|=============================================================================|
|    0   N/A  N/A      1231      G   /usr/lib/xorg/Xorg                125MiB |
|    0   N/A  N/A      1992      G   cinnamon                           28MiB |
|    0   N/A  N/A      2471      G   ...5/usr/lib/firefox/firefox      135MiB |
+-----------------------------------------------------------------------------+
```

here is the output of nvidia-bug-report.sh[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291282&stc=1[/IMG][ATTACH]291282[/ATTACH]

[here is the output of "inxi -Fayz" https://pastebin.com/PRpwSvcA]("https://pastebin.com/PRpwSvcA")

I'm completely out of ideas. There seem to be more support on arch and manjaro forums so I guess I could try installing one those if literally no one here has a single idea on what to try.

Let me know if there are other useful reports I need to post

---

### Post by MAFoElffen on 2022-11-22
I see your two hdmi ports. What resolution would you want them set to? (For me to calculate the modesets...)

Once you post back with that, I'll post commands for you to try.

---

### Post by xeraster on 2022-11-23
It would be nice to set hdmi output to either 1080p 60fps or 1080p 30fps

---

### Post by MAFoElffen on 2022-11-23
Tell me how this goes (GTF)

First set session as xorg xserver...
```

xrandr --newmode "1920x1080_60.00"  172.80  1920 2040 2248 2576  1080 1081 1084 1118  -HSync +Vsyn
xrandr --addmode HDMI-1-1 "1920x1080_60.00"
xrandr --addmode HDMI-1-2 "1920x1080_60.00"
xrandr --output HDMI-1-1 --mode "1920x1080_60.00"
xrandr --output HDMI-1-2 --mode "1920x1080_60.00"

```
This is just a test. Will not be persistent yet...

Query again with 
```

xrandr -q

```

---

### Post by grahammechanical on 2022-11-23
Might I be allowed to add a little information that may possibly cause more confusion. :)

xrandr is a utility that works with the X-Server windowing system. It does not work on the Wayland compositor that Ubuntu 22.04 faults to. It is possible to switch to Ubuntu on X-Server by accessing a menu at the login screen. Click on the cog icon.

I recently purchased a laptop with Ubuntu pre-installed. It also is a Clevo laptop with an Insyde UEFI/BIOS. It has an Intel UHD graphics and not IRIS graphics. I have no problem connecting to a TV as a monitor using HDMI. Of course, I do have to select HDMI as the TV source.

What monitor is being used? What resolutions does it support. Modern monitors have something called Extended Display Identification Data (EDID) stored in an integrated circuit. Ubuntu usually reads the EDID to both set the default resolution and frequency and to offer alternatives.

Is it possible to eliminate the monitor as a cause of this problem? It seems that Wayland alternatives to xrandr are more experimental than tested.

Regards

---

### Post by MAFoElffen on 2022-11-23
+1 -- Or the cable... Usually if it doesn't show as anything returning as attached to a port in the results of 
```

xrandr -q

```
It's usually because it doesn't "see" something attached/connected to that port. Which could be a cable, or that there is something wrong with the display's EDID Table.

---

### Post by xeraster on 2022-11-23
> **MAFoElffen said:**
> Tell me how this goes (GTF)

First set session as xorg xserver...
```

xrandr --newmode "1920x1080_60.00"  172.80  1920 2040 2248 2576  1080 1081 1084 1118  -HSync +Vsyn
xrandr --addmode HDMI-1-1 "1920x1080_60.00"
xrandr --addmode HDMI-1-2 "1920x1080_60.00"
xrandr --output HDMI-1-1 --mode "1920x1080_60.00"
xrandr --output HDMI-1-2 --mode "1920x1080_60.00"

```
This is just a test. Will not be persistent yet...

Query again with
```

xrandr -q

```

This seems like it's going to work at first. The commands "xrandr --output HDMI-1-1 --mode "1920x1080_60.00" or "xrandr --output HDMI-1-2 --mode "1920x1080_60.00" cause the entire system to freeze. Even ctrl+alt+F3 doesn't do anything do get out of it and I have to hold the power button to force a shutdown.

Here is the output of xrandr -q after trying the first 3 commands you suggested and with the tv plugged in:
```

Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 32767 x 32767
eDP-1-1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 344mm x 193mm
   1920x1080    144.15*+  60.01    59.97    59.96    60.20    59.93  
   1680x1050     59.95    59.88  
   1400x1050     74.76    59.98  
   1600x900      59.99    59.94    59.95    59.82  
   1280x1024     85.02    75.02    60.02  
   1400x900      59.96    59.88  
   1280x960      85.00    60.00  
   1440x810      60.00    59.97  
   1368x768      59.88    59.85  
   1280x800      59.99    59.97    59.81    59.91  
   1152x864      75.00  
   1280x720      60.00    59.99    59.86    59.74  
   1024x768      85.00    75.05    60.04    85.00    75.03    70.07    60.00  
   1024x768i     86.96  
   960x720       85.00    75.00    60.00  
   928x696       75.00    60.05  
   896x672       75.05    60.01  
   1024x576      59.95    59.96    59.90    59.82  
   960x600       59.93    60.00  
   832x624       74.55  
   960x540       59.96    59.99    59.63    59.82  
   800x600       85.00    75.00    70.00    65.00    60.00    85.14    72.19    75.00    60.32    56.25  
   840x525       60.01    59.88  
   864x486       59.92    59.57  
   700x525       74.76    59.98  
   800x450       59.95    59.82  
   640x512       85.02    75.02    60.02  
   700x450       59.96    59.88  
   640x480       85.09    60.00    85.01    72.81    75.00    59.94  
   720x405       59.51    58.99  
   720x400       85.04  
   684x384       59.88    59.85  
   640x400       59.88    59.98    85.08  
   576x432       75.00  
   640x360       59.86    59.83    59.84    59.32  
   640x350       85.08  
   512x384       85.00    75.03    70.07    60.00  
   512x384i      87.06  
   512x288       60.00    59.92  
   416x312       74.66  
   480x270       59.63    59.82  
   400x300       85.27    72.19    75.12    60.32    56.34  
   432x243       59.92    59.57  
   320x240       85.18    72.81    75.00    60.05  
   360x202       59.51    59.13  
   360x200       85.04  
   320x200       85.27  
   320x180       59.84    59.32  
   320x175       85.27  
DP-1-1 disconnected (normal left inverted right x axis y axis)
HDMI-1-1 disconnected (normal left inverted right x axis y axis)
   1920x1080_60.00  60.00  
DP-1-2 disconnected (normal left inverted right x axis y axis)
DP-1-3 disconnected (normal left inverted right x axis y axis)
DP-1-4 disconnected (normal left inverted right x axis y axis)
HDMI-1-2 disconnected (normal left inverted right x axis y axis)
   1920x1080_60.00  60.00  
  1920x1080_60.00 (0x293) 172.800MHz -HSync
        h: width  1920 start 2040 end 2248 total 2576 skew    0 clock  67.08KHz
        v: height 1080 start 1081 end 1084 total 1118           clock  60.00Hz


```

> **grahammechanical said:**
> Might I be allowed to add a little information that may possibly cause more confusion.

xrandr is a utility that works with the X-Server windowing system. It does not work on the Wayland compositor that Ubuntu 22.04 faults to. It is possible to switch to Ubuntu on X-Server by accessing a menu at the login screen. Click on the cog icon.

I recently purchased a laptop with Ubuntu pre-installed. It also is a Clevo laptop with an Insyde UEFI/BIOS. It has an Intel UHD graphics and not IRIS graphics. I have no problem connecting to a TV as a monitor using HDMI. Of course, I do have to select HDMI as the TV source.

What monitor is being used? What resolutions does it support. Modern monitors have something called Extended Display Identification Data (EDID) stored in an integrated circuit. Ubuntu usually reads the EDID to both set the default resolution and frequency and to offer alternatives.

Is it possible to eliminate the monitor as a cause of this problem? It seems that Wayland alternatives to xrandr are more experimental than tested.

Regards

The tv that i'm trying to connect to works with another Clevo laptop I have. All I have to do is plug in the hdmi cable and it does what it's supposed to. The tv is a Visio V505-H9.

Also, I didn't have the option to set xorg but settings is showing x11 insread of wayland in settings also when I type echo $XDG_SESSION_TYPE into a terminal window. Is that the same or is it different?
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291292&stc=1[/IMG]

Here is the output of xrandr -q **on my other Clevo laptop** which has nvidia graphics only while it is connected to the same tv (which works normally):
```

Screen 0: minimum 8 x 8, current 5760 x 2160, maximum 32767 x 32767
DP-0 disconnected (normal left inverted right x axis y axis)
DP-1 disconnected (normal left inverted right x axis y axis)
HDMI-0 connected 3840x2160+1920+0 (normal left inverted right x axis y axis) 1096mm x 616mm
   3840x2160     30.00*+  59.94    50.00    29.97    25.00    23.98  
   4096x2160     59.94    50.00    24.00  
   1920x1080    119.88   100.00    60.00    59.94    50.00    29.97    25.00    23.98  
   1280x720      59.94    50.00  
   1024x768      75.03    70.07    60.00  
   800x600       75.00    72.19    60.32  
   720x576       50.00  
   720x480       59.94  
   640x480       75.00    59.94    59.93  
DP-2 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 344mm x 194mm
   1920x1080    144.01*+  72.01  
DP-3 disconnected (normal left inverted right x axis y axis)
DP-4 disconnected (normal left inverted right x axis y axis)

```

---

### Post by xeraster on 2022-11-27
ok I might be on to something. This laptop has a mini displayport and a  usb-c port. I bought a mini displayport to hdmi adapter and a usb-c to  hdmi adapter. The usb-c to hdmi adapter very unsurprisingly didn't work.  The mini displayport to hdmi didn't let me output video but it *actually* changed something. If I plug in the mini displayport to hdmi adapter and plug an hdmi cable into the adapter and connect the other end to my tv, it doesn't work and won't let me output video ***_HOWEVER_*** if I run xrandr -q, the entire computer freezes for about half of a second before printing the xrandr output (and showing that none of the displays execpt DP-1 is connected). Normally, it never freezes the computer just from running xrandr -q.

This is the closest thing to progress I've ever achieved with this. Is there any way to find out why xrandr -q makes the computer freeze when I run it while something is connected to the mini display port?

---

### Post by xeraster on 2022-12-03
Ok. I didn't fix it completely but I just made a huge amount of progress.

There is this thing called Liquoirx Kernel [https://launchpad.net/~damentz/+archive/ubuntu/liquorix](https://launchpad.net/~damentz/+archive/ubuntu/liquorix). I previously tried installing the latest kernel in mainline and it didn't fix the problem. Liquorix is a "distro kernel replacement built using the best configuration and kernel sources for desktop, multimedia, and gaming workloads." I assume that means they really really dug into the kernel compile options and selected options that support more bleeding edge hardware or something whereas the mainline kernels just use whatever default ubuntu distro settings (and therefore not working ones for me) are default.

While installing the Liquorix kernel doesn't make the hdmi port work, it does make the mini displayport work and I can plug the laptop into my tv using a mini displayport to hdmi adapter. The sound even works over hdmi.

Overall, while I would really really like to get the regular hdmi port working, with how little progress of any kind I had made before finding this trick, I can accept this. Maybe later kernels or nvidia drivers in a few months or years will fix it and in the meantime I can enjoy not having Windows on this laptop.

Also, for anyone with the same laptop as me (Clevo V155PNJQ) wondering how to get the lighted keyboard advanced features to work, use this: [https://github.com/tuxedocomputers/tuxedo-keyboard](https://github.com/tuxedocomputers/tuxedo-keyboard)

---

