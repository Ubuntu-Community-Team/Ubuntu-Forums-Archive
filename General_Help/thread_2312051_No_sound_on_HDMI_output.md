---
title: "No sound on HDMI output"
date: 2016-02-01
forum: General Help
---

### Post by windyrij on 2016-02-01
I am hoping to stream Iplayer to a flatscreen TV, but unable to get sound on the HDMI input (video OK).
I have searched on Google, and tried various suggestions, but no luck so far.
Any help would be much appreciated, thanks -  John

Hardware:
Desktop system -
Elitegroup GS6710 Ultra motherboard|AMD Athlon AMD64 3200+|2 GB ram|Asus Geforce 210 Silent 1GB|on board AC97 audio SIS SI 7012.

Drivers:
Linux Kernel 3.2.0-23 generic
Alsa 1.0.24
Nouveau kernel module 3.2.0-23 generic

Installed software:
Xubuntu 12.04 -fresh install, no updates
Pulseaudio Volume Control GUI (pavucontrol)
Mixer GUI (xfce4-mixer)
Alsamixer (terminal use) 1.0.25

Tests so far:
1. HDMI cable and TV proved by running sample video/sound clip from Windows 7 Multimedia Center on dual boot laptop. Sound OK on TV.
2. Running video/sound clip on Xubuntu 12.04 from same laptop via HDMI - no sound on TV. Sound OK on laptop speakers.
3. Running video/sound clip on Xubuntu 12.04 from desktop machine via HDMI - no sound on TV. Sound OK on PC speakers.
 (Same result when running Mint 11 from live CD on desktop system and using built-in sound tests.)
4. Running alsamixer in terminal: Select HDA Nvidia (F6). S/PDIF 0-3 displayed. Can be muted/unmuted, but no control of volume via up/down arrow keys.
5. Running Pulseaudio Volume Control:
    (a) Output Device tab:
         High Definition Audio Controller Digital Stereo
         Port: HDMI/DisplayPort
                 No sound output to TV or signal on bar when playing video/sound clip.
        Output Device tab:
        Built-in Analogue Stereo
        Port: Analogue Output/Amplifier
                       Sound output to desktop speakers and signal on bar when playing video/sound clip.
    (b) Configuration tab:
         High Definition Audio Controller
           Profile: Digital Stereo (HDMI) Output
         Built-in Audio
           Profile: Analogue Stereo Output
6.
```

john@john:~/Desktop$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SI7012 [SiS SI7012], device 0: Intel ICH [SiS SI7012]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
john@john:~/Desktop$ 

```

---

### Post by Vladlenin5000 on 2016-02-01
The HDMI audio output a) resides on your graphics card therefore b) it is controlled by the graphics card drivers. Which driver are you using? The default open source *nouveau* driver for Nvidia cards may not provide the correct support for HDMI audio. Also you need to change the output in sound settings, it isn't automatic and the OS often defaults to the internal sound card.

---

### Post by windyrij on 2016-02-03
Hello Vladlenin500:

Thanks for your reply. Regarding the driver:
Part of lspci -k
code-----
01:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce 210] (rev a2)
    Subsystem: ASUSTeK Computer Inc. Device 852d
    Kernel driver in use: nouveau
    Kernel modules: nouveau, nvidiafb
01:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)
    Subsystem: ASUSTeK Computer Inc. Device 852d
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel
code----

glxinfo | grep OPenGL gives:
code-------
john@john:~$ glxinfo | grep OpenGL
OpenGL vendor string: nouveau
OpenGL renderer string: Gallium 0.4 on NVA8
OpenGL version string: 2.1 Mesa 8.0.2
OpenGL shading language version string: 1.20
OpenGL extensions:
code------
Does this answer your question about the driver version?

There is no recommended driver listed under Settings|Additional drivers. None are activated.

---

### Post by Vladlenin5000 on 2016-02-03
Well, back to the beginning. I'm sorry I've missed a vital detail about your system: Xubuntu **12.04**.
Only the standard Ubuntu 12.04 is still supported; other flavors had 3 years support only (this changed in the next LTS which was 14.04). This is the reason for not having drivers offered (and not being able to install many software and even critical updates).

Please upgrade to a supported release (14.04 should be fine for your hardware) and come back here if the problem persists. Again, you should try the proprietary drivers which you undoubtedly will see offered if running a supported release.
As per forum policy I won't give any further support.

---

### Post by windyrij on 2016-02-05
Hello Vladlenin5000 and thank you for your reply again:

I downloaded Xubuntu 14.04.3 and burnt a Live DVD, then installed. Had to disable ACPI in the BIOS (AMI 08/13/2007) and add "nomodeset" to the DVD boot (F6 - add options), to get the install to start.
When the install completed, the desktop was in VGA 800x600, with no other resolutions available. The driver was the Nouveau X.Org driver.

Next - "Additional Drivers" and install "NVIDIA binary 340.96 proprietary driver". This is recommended on the NVIDIA site for the  Geforce 210 (GT218) card.
On re-start blank screen on PC monitor (connected to VGA port on card).
Re-start again with "nomodeset" in grub entry, before "quiet splash". X server fails to start, and screen defaults to a command prompt.
Other points.
1. Starting up with a running TV connected to the HDMI port on the card, PC monitor blank, display now on TV.
2. with X.org driver and VGA display, Sound Settings|Output Devices tab shows:
High Definition Audio Controller Digital Stereo HDMI
Port: HDMI/Displayport 3 (unplugged)
Built-in Audio Analogue Stereo
Port: Analogue Output/Amplifier
3. Sound Settings|Configuration tab shows:
High Definition Audio Controller
Profile: Digital Stereo (HDMI) Output (unplugged)
Built-in Audio
Profile: Analogue Stereo Duplex
Conecting the TV, before startup makes no difference.

Three different issues here, loss of X server, display output switching and "unplugged".
Any guidance would be welcome!  Many thanks,   John

---

