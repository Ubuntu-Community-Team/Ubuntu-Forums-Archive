---
title: "Audio output crash when playing audio on Audacity"
date: 2023-05-03
forum: General Help
---

### Post by enricobe on 2023-05-03
Hello,
can someone please test the following steps to make the audio management crash? I can make it crash everytime on Kubuntu 23.04 but I can't undestand if it's something related to my PC, to KDE Plasma or to Ubuntu.

I have a PC that is connected to the HDMI screen and to the earphones via audio jack. So I have 2 outputs: HDMI + Earphones.

1) Put the audio output to HDMI
2) Play an mp3 file for few seconds to check everything works
3) Open an audio file in Audacity
4) Play the audio file in Audacity
5) While playing, change the audio output to earphones.

On my PC this make the audio system to crash. Kubuntu says that there is no input/output devices. The only way to restore it, is rebooting the system.
If I change the audio output while playing from any media player (like VLC) it works fine. The audio system crashes only if I change the output while playing an audio in Audacity

---

### Post by #&amp;thj^% on 2023-05-03
I was hoping to confirm your findings, but still going strong here:
```
wpctl status
PipeWire 'pipewire-0' [0.3.65, me@zfs-me, cookie:2610085359]
 &#9492;&#9472; Clients:
        31. pipewire                            [0.3.65, me@zfs-me, pid:6386]
        33. WirePlumber                         [0.3.65, me@zfs-me, pid:6385]
        34. WirePlumber [export]                [0.3.65, me@zfs-me, pid:6385]
        40. xdg-desktop-portal                  [0.3.65, me@zfs-me, pid:6600]
        52. xfce4-pulseaudio-plugin             [0.3.65, me@zfs-me, pid:6718]
        76. ALSA plug-in [audacity]             [0.3.65, me@zfs-me, pid:931717]
        81. PulseAudio Volume Control           [0.3.65, me@zfs-me, pid:936727]
       158. wpctl                               [0.3.65, me@zfs-me, pid:937866]

Audio
 &#9500;&#9472; Devices:
 &#9474;      43. HDA NVidia                          [alsa]
 &#9474;      44. UOEOS Laptop Dock                   [alsa]
 &#9474;      45. Family 17h/19h HD Audio Controller  [alsa]
 &#9474;  
 &#9500;&#9472; Sinks:
 &#9474;      32. UOEOS Laptop Dock Analog Stereo     [vol: 0.40]
 &#9474;      49. Family 17h/19h HD Audio Controller Analog Stereo [vol: 0.35]
 &#9474;  *   53. HDA NVidia Digital Surround 5.1 (HDMI) [vol: 0.40]
 &#9474;  
 &#9500;&#9472; Sink endpoints:
 &#9474;  
 &#9500;&#9472; Sources:
 &#9474;  *   50. Family 17h/19h HD Audio Controller Analog Stereo [vol: 1.00]
 &#9474;      51. UOEOS Laptop Dock Analog Stereo     [vol: 1.00]
 &#9474;  
 &#9500;&#9472; Source endpoints:
 &#9474;  
 &#9492;&#9472; Streams:
        69. PulseAudio Volume Control                                   
             90. input_FL        < ALC257 Analog:monitor_FL	[active]
             91. monitor_FL     
             92. input_FR        < ALC257 Analog:monitor_FR	[active]
             93. monitor_FR     
        70. PulseAudio Volume Control                                   
             86. input_FL        < UOEOS Laptop Dock:capture_FL	[active]
             87. monitor_FL     
             88. input_FR        < UOEOS Laptop Dock:capture_FR	[active]
             89. monitor_FR     
        71. PulseAudio Volume Control                                   
            132. monitor_FR     
            133. monitor_FL     
           [B] 134. input_FR        < ALSA plug-in [audacity]:output_FR	[active]
            135. input_FL        < ALSA plug-in [audacity]:output_FL	[active]
            144. input_RL        < ALSA plug-in [audacity]:output_RL	[active]
            145. monitor_RL     
            146. input_RR        < ALSA plug-in [audacity]:output_RR	[active]
            147. monitor_RR     
        [B]    148. input_FC        < ALSA plug-in [audacity]:output_FC	[active]
            149. monitor_FC     
            150. input_LFE       < ALSA plug-in [audacity]:output_LFE	[active]
            151. monitor_LFE    [/B][/B]
        72. PulseAudio Volume Control                                   
             94. input_FL        < ALC257 Analog:capture_FL	[active]
             95. monitor_FL     
             96. input_FR        < ALC257 Analog:capture_FR	[active]
             97. monitor_FR     
        78. ALSA plug-in [audacity]                                     
             54. output_FC       > SAMSUNG:playback_FC	[active]
             68. output_FL       > SAMSUNG:playback_FL	[active]
             82. output_RL       > SAMSUNG:playback_RL	[active]
            101. output_LFE      > SAMSUNG:playback_LFE	[active]
            136. output_RR       > SAMSUNG:playback_RR	[active]
            137. output_FR       > SAMSUNG:playback_FR	[active]
        80. PulseAudio Volume Control                                   
             48. input_FL        < UOEOS Laptop Dock:monitor_FL	[active]
             83. monitor_FL     
             84. input_FR        < UOEOS Laptop Dock:monitor_FR	[active]
             85. monitor_FR     
       119. PulseAudio Volume Control                                   
            102. input_RL        < SAMSUNG:monitor_RL	[active]
            103. monitor_FL     
            104. input_FR        < SAMSUNG:monitor_FR	[active]
            105. input_FL        < SAMSUNG:monitor_FL	[active]
            116. monitor_RL     
            117. monitor_FR     
            120. input_RR        < SAMSUNG:monitor_RR	[active]
            121. monitor_RR     
            122. input_FC        < SAMSUNG:monitor_FC	[active]
            123. monitor_FC     
            124. input_LFE       < SAMSUNG:monitor_LFE	[active]
            125. monitor_LFE    

Video
 &#9500;&#9472; Devices:
 &#9474;      41. Integrated Camera                   [v4l2]
 &#9474;      42. Integrated Camera                   [v4l2]
 &#9474;  
 &#9500;&#9472; Sinks:
 &#9474;  
 &#9500;&#9472; Sink endpoints:
 &#9474;  
 &#9500;&#9472; Sources:
 &#9474;  *   46. Integrated Camera (V4L2)           
 &#9474;  
 &#9500;&#9472; Source endpoints:
 &#9474;  
 &#9492;&#9472; Streams:

Settings
 &#9492;&#9472; Default Configured Node Names:
         0. Audio/Sink    alsa_output.pci-0000_01_00.1.hdmi-surround
         1. Audio/Source  alsa_input.pci-0000_05_00.6.analog-stereo



```

---

### Post by enricobe on 2023-05-03
Hello, thank you very much for your test. Are you using Kubuntu or another ubuntu flavour?

EDIT: ok I've seen the "xfce4" plugin now :-) Let's see if someone else can test this on Kubuntu

Do you know how can I track this kind of crash? journalctl returns only

[FONT=monospace][COLOR=#000000]mag 03 21:56:01 enrico-kubuntu plasmashell[6231]: ALSA lib conf.c:4553: (snd_config_update_r) Cannot access file /usr/share/alsa/alsa.conf [/COLOR]
mag 03 21:56:01 enrico-kubuntu plasmashell[6231]: ALSA lib seq.c:935: (snd_seq_open_noupdate) Unknown SEQ default
[/FONT]
[FONT=monospace] EDIT2:
I tried to reproduce the crash and download the entire journalctl. It returns the following

[/FONT]```
mag 03 22:01:17 enrico-kubuntu plasmashell[2420]: file:///usr/lib/x86_64-linux-gnu/qt5/qml/org/kde/plasma/extras/PlaceholderMessage.qml:238:5: QML Heading: Binding loop detected for property "verticalAlignment"
mag 03 22:01:17 enrico-kubuntu plasmashell[2420]: QQmlExpression: Expression file:///usr/share/plasma/plasmoids/org.kde.plasma.private.systemtray/contents/ui/ExpandedRepresentation.qml:181:21 depends on non-NOTIFYable properties:
mag 03 22:01:17 enrico-kubuntu plasmashell[2420]:     QAction::priority
mag 03 22:01:17 enrico-kubuntu plasmashell[2420]:     QAction::priority
mag 03 22:01:17 enrico-kubuntu plasmashell[2420]:     QAction::priority
mag 03 22:01:17 enrico-kubuntu plasmashell[2420]: QQmlExpression: Expression file:///usr/share/plasma/plasmoids/org.kde.plasma.private.systemtray/contents/ui/ExpandedRepresentation.qml:82:17 depends on non-NOTIFYable properties:
mag 03 22:01:17 enrico-kubuntu plasmashell[2420]:     QAction::priority
mag 03 22:01:17 enrico-kubuntu plasmashell[2420]:     QAction::priority
mag 03 22:01:17 enrico-kubuntu plasmashell[2420]:     QAction::priority
mag 03 22:01:17 enrico-kubuntu plasmashell[2420]: trying to show an empty dialog
mag 03 22:01:17 enrico-kubuntu pipewire[2033]: spa.alsa: 'front:0': playback open failed: Device or resource busy
mag 03 22:01:17 enrico-kubuntu pipewire[2033]: spa.alsa: 'front:0': playback open failed: Device or resource busy
mag 03 22:01:17 enrico-kubuntu pipewire[2033]: spa.audioadapter: params Spa:Enum:ParamId:EnumFormat: 0:0 (follower format) Device or resource busy
mag 03 22:01:17 enrico-kubuntu pipewire[2033]: pw.node: (alsa_output.pci-0000_00_1f.3.analog-stereo-45) suspended -> error (Start error: Device or resource busy)
mag 03 22:01:17 enrico-kubuntu plasmashell[2420]: Qt Quick Layouts: Detected recursive rearrange. Aborting after two iterations.
mag 03 22:01:17 enrico-kubuntu plasmashell[2420]: Qt Quick Layouts: Detected recursive rearrange. Aborting after two iterations.
mag 03 22:01:19 enrico-kubuntu pipewire[2033]: pw.link: 0x561263d95670: one of the nodes is in error out:error in:suspended
mag 03 22:01:19 enrico-kubuntu pipewire[2033]: pw.link: 0x561263d97660: one of the nodes is in error out:error in:suspended
mag 03 22:01:20 enrico-kubuntu plasmashell[2420]: QQmlExpression: Expression file:///usr/share/plasma/plasmoids/org.kde.plasma.private.systemtray/contents/ui/ExpandedRepresentation.qml:181:21 depends on non-NOTIFYable properties:
mag 03 22:01:20 enrico-kubuntu plasmashell[2420]:     QAction::priority
mag 03 22:01:20 enrico-kubuntu plasmashell[2420]:     QAction::priority
mag 03 22:01:20 enrico-kubuntu plasmashell[2420]:     QAction::priority
mag 03 22:01:20 enrico-kubuntu plasmashell[2420]: QQmlExpression: Expression file:///usr/share/plasma/plasmoids/org.kde.plasma.private.systemtray/contents/ui/ExpandedRepresentation.qml:181:21 depends on non-NOTIFYable properties:
mag 03 22:01:20 enrico-kubuntu plasmashell[2420]:     QAction::priority
mag 03 22:01:20 enrico-kubuntu plasmashell[2420]:     QAction::priority
mag 03 22:01:20 enrico-kubuntu plasmashell[2420]:     QAction::priority
mag 03 22:01:21 enrico-kubuntu plasmashell[2420]: QQmlExpression: Expression file:///usr/share/plasma/plasmoids/org.kde.plasma.private.systemtray/contents/ui/ExpandedRepresentation.qml:181:21 depends on non-NOTIFYable properties:
mag 03 22:01:21 enrico-kubuntu plasmashell[2420]:     QAction::priority
mag 03 22:01:21 enrico-kubuntu plasmashell[2420]:     QAction::priority
mag 03 22:01:21 enrico-kubuntu plasmashell[2420]:     QAction::priority
mag 03 22:01:23 enrico-kubuntu plasmashell[2420]: QQmlExpression: Expression file:///usr/share/plasma/plasmoids/org.kde.plasma.private.systemtray/contents/ui/ExpandedRepresentation.qml:181:21 depends on non-NOTIFYable properties:
mag 03 22:01:23 enrico-kubuntu plasmashell[2420]:     QAction::priority
mag 03 22:01:23 enrico-kubuntu plasmashell[2420]:     QAction::priority
mag 03 22:01:23 enrico-kubuntu plasmashell[2420]:     QAction::priority
mag 03 22:01:24 enrico-kubuntu plasmashell[2420]: QQmlExpression: Expression file:///usr/share/plasma/plasmoids/org.kde.plasma.private.systemtray/contents/ui/ExpandedRepresentation.qml:181:21 depends on non-NOTIFYable properties:
mag 03 22:01:24 enrico-kubuntu plasmashell[2420]:     QAction::priority
mag 03 22:01:24 enrico-kubuntu plasmashell[2420]:     QAction::priority
mag 03 22:01:24 enrico-kubuntu plasmashell[2420]:     QAction::priority
mag 03 22:01:24 enrico-kubuntu pipewire[2033]: spa.alsa: 'front:0': playback open failed: Device or resource busy
mag 03 22:01:24 enrico-kubuntu pipewire[2033]: spa.alsa: 'front:0': playback open failed: Device or resource busy
mag 03 22:01:24 enrico-kubuntu pipewire[2033]: spa.audioadapter: params Spa:Enum:ParamId:EnumFormat: 0:0 (follower format) Device or resource busy
mag 03 22:01:24 enrico-kubuntu pipewire[2033]: pw.node: (alsa_output.pci-0000_00_1f.3.analog-stereo-45) suspended -> error (Start error: Device or resource busy)
mag 03 22:01:27 enrico-kubuntu plasmashell[2420]: org.kde.plasma.pulseaudio: No object for name "alsa_output.pci-0000_00_1f.3.analog-stereo"
mag 03 22:01:27 enrico-kubuntu plasmashell[2420]: org.kde.plasma.pulseaudio: No object for name "alsa_output.pci-0000_00_1f.3.analog-stereo.monitor"
mag 03 22:01:27 enrico-kubuntu plasmashell[2420]: org.kde.plasma.pulseaudio: No object for name "@DEFAULT_SINK@"
mag 03 22:01:27 enrico-kubuntu plasmashell[2420]: org.kde.plasma.pulseaudio: No object for name "@DEFAULT_SOURCE@"
mag 03 22:01:27 enrico-kubuntu plasmashell[2420]: file:///usr/lib/x86_64-linux-gnu/qt5/qml/org/kde/plasma/extras/PlaceholderMessage.qml:238:5: QML Heading: Binding loop detected for property "verticalAlignment"
mag 03 22:01:27 enrico-kubuntu plasmashell[2420]: org.kde.plasma.pulseaudio: No object for name "@DEFAULT_SINK@"
mag 03 22:01:27 enrico-kubuntu plasmashell[2420]: org.kde.plasma.pulseaudio: No object for name "@DEFAULT_SOURCE@"
mag 03 22:01:27 enrico-kubuntu plasmashell[2420]: org.kde.plasma.pulseaudio: No object for name "alsa_output.pci-0000_00_1f.3.hdmi-stereo.monitor"
mag 03 22:01:32 enrico-kubuntu pipewire[2033]: spa.alsa: 'front:0': playback open failed: Device or resource busy
mag 03 22:01:32 enrico-kubuntu pipewire[2033]: mod.adapter: 0x561263e0e950: can't get format: Device or resource busy
mag 03 22:01:32 enrico-kubuntu wireplumber[2035]: <WpNode:0x55a639952120> Object activation aborted: PipeWire proxy destroyed
mag 03 22:01:32 enrico-kubuntu plasmashell[2420]: org.kde.plasma.pulseaudio: No object for name "alsa_output.pci-0000_00_1f.3.hdmi-stereo"
mag 03 22:01:32 enrico-kubuntu plasmashell[2420]: org.kde.plasma.pulseaudio: No object for name "alsa_output.pci-0000_00_1f.3.hdmi-stereo.monitor"
mag 03 22:01:32 enrico-kubuntu plasmashell[2420]: org.kde.plasma.pulseaudio: No object for name "@DEFAULT_SINK@"
mag 03 22:01:32 enrico-kubuntu plasmashell[2420]: org.kde.plasma.pulseaudio: No object for name "@DEFAULT_SOURCE@"
mag 03 22:01:32 enrico-kubuntu plasmashell[2420]: org.kde.plasma.pulseaudio: No object for name "@DEFAULT_SINK@"
mag 03 22:01:32 enrico-kubuntu plasmashell[2420]: org.kde.plasma.pulseaudio: No object for name "@DEFAULT_SOURCE@"
mag 03 22:01:32 enrico-kubuntu plasmashell[2420]: file:///usr/lib/x86_64-linux-gnu/qt5/qml/org/kde/plasma/extras/PlaceholderMessage.qml:238:5: QML Heading: Binding loop detected for property "verticalAlignment"
mag 03 22:01:32 enrico-kubuntu plasmashell[2420]: org.kde.plasma.pulseaudio: No object for name "auto_null.monitor"
mag 03 22:01:35 enrico-kubuntu kwin_x11[2325]: qt.qpa.xcb: QXcbConnection: XCB error: 3 (BadWindow), sequence: 17416, resource id: 52431383, major code: 15 (QueryTree), minor code: 0
mag 03 22:01:35 enrico-kubuntu kwin_x11[2325]: qt.qpa.xcb: QXcbConnection: XCB error: 3 (BadWindow), sequence: 17474, resource id: 52428929, major code: 15 (QueryTree), minor code: 0
mag 03 22:01:35 enrico-kubuntu kwin_x11[2325]: kwin_core: XCB error: 152 (BadDamage), sequence: 17534, resource id: 16777514, major code: 143 (DAMAGE), minor code: 3 (Subtract)
mag 03 22:01:35 enrico-kubuntu systemd[2026]: app-audacity-bf9b92d8716b4e1586b5338f60640481.scope: Consumed 13.515s CPU time.
mag 03 22:01:39 enrico-kubuntu plasmashell[2747]: QObject::connect: No such slot DesktopProtocol::_k_slotRedirection(KIO::Job *, QUrl)
mag 03 22:01:39 enrico-kubuntu plasmashell[2747]: QObject::connect: No such slot DesktopProtocol::_k_slotRedirection(KIO::Job *, QUrl)
```

[FONT=monospace]
Can you see something interesting? Do you suggest me to report this problem against KDE Plasma?
[/FONT]

---

### Post by #&amp;thj^% on 2023-05-03
Can I see this, I just got back on-line:
```
inxi -Alsa -j
```
EDIT: Also you can run it from the terminal, with the HDMI checked for the device.
Mine:
```
audacity '/home/me/Music/Alt-J - Discography - 2009-2014/Albums (CD Original)/2012 - An Awesome Wave (Limited Edition) - (320 kbps)/03. Tessellate.mp3' 

(process:1401342): Gdk-CRITICAL **: 15:48:12.140: gdk_screen_get_root_window: assertion 'GDK_IS_SCREEN (screen)' failed

(process:1401342): Gdk-CRITICAL **: 15:48:12.140: gdk_window_get_display: assertion 'GDK_IS_WINDOW (window)' failed

(process:1401342): Gdk-CRITICAL **: 15:48:12.140: gdk_cursor_new_from_pixbuf: assertion 'GDK_IS_DISPLAY (display)' failed


```
Those are normal output called by the terminal.

---

### Post by enricobe on 2023-05-04
Thank you. The inxi command returns this

```
[FONT=monospace][COLOR=#5454ff]**Audio:**[/COLOR][COLOR=#000000] [/COLOR]
  [COLOR=#5454ff]**Device-1:**[/COLOR][COLOR=#000000] Intel Alder Lake PCH-P High Definition Audio [/COLOR][COLOR=#5454ff]**driver:**[/COLOR][COLOR=#000000] snd_hda_intel [/COLOR]
    [COLOR=#5454ff]**v:**[/COLOR][COLOR=#000000] kernel [/COLOR][COLOR=#5454ff]**alternate:**[/COLOR][COLOR=#000000] snd_sof_pci_intel_tgl [/COLOR][COLOR=#5454ff]**bus-ID:**[/COLOR][COLOR=#000000] 00:1f.3 [/COLOR]
    [COLOR=#5454ff]**chip-ID:**[/COLOR][COLOR=#000000] 8086:51c8 [/COLOR][COLOR=#5454ff]**class-ID:**[/COLOR][COLOR=#000000] 0401 [/COLOR]
  [COLOR=#5454ff]**Sound API:**[/COLOR][COLOR=#000000] ALSA [/COLOR][COLOR=#5454ff]**v:**[/COLOR][COLOR=#000000] k6.2.0-20-generic [/COLOR][COLOR=#5454ff]**running:**[/COLOR][COLOR=#000000] yes [/COLOR]
  [COLOR=#5454ff]**Sound Server-1:**[/COLOR][COLOR=#000000] PipeWire [/COLOR][COLOR=#5454ff]**v:**[/COLOR][COLOR=#000000] 0.3.65 [/COLOR][COLOR=#5454ff]**running:**[/COLOR][COLOR=#000000] yes [/COLOR]
[COLOR=#5454ff]**Swap:**[/COLOR][COLOR=#000000] [/COLOR]
  [COLOR=#5454ff]**Kernel:**[/COLOR][COLOR=#000000] [/COLOR][COLOR=#5454ff]**swappiness:**[/COLOR][COLOR=#000000] 60 (default) [/COLOR][COLOR=#5454ff]**cache-pressure:**[/COLOR][COLOR=#000000] 100 (default) [/COLOR]
  [COLOR=#5454ff]**ID-1:**[/COLOR][COLOR=#000000] swap-1 [/COLOR][COLOR=#5454ff]**type:**[/COLOR][COLOR=#000000] file [/COLOR][COLOR=#5454ff]**size:**[/COLOR][COLOR=#000000] 2 GiB [/COLOR][COLOR=#5454ff]**used:**[/COLOR][COLOR=#000000] 0 KiB (0.0%) [/COLOR][COLOR=#5454ff]**priority:**[/COLOR][COLOR=#000000] -2 [/COLOR]
    [COLOR=#5454ff]**file:**[/COLOR][COLOR=#000000] /swapfile [/COLOR]
[COLOR=#5454ff]**Sensors:**[/COLOR][COLOR=#000000] [/COLOR]
  [COLOR=#5454ff]**System Temperatures:**[/COLOR][COLOR=#000000] [/COLOR][COLOR=#5454ff]**cpu:**[/COLOR][COLOR=#000000] 41.0 C [/COLOR][COLOR=#5454ff]**mobo:**[/COLOR][COLOR=#000000] N/A [/COLOR]
  [COLOR=#5454ff]**Fan Speeds (RPM):**[/COLOR][COLOR=#000000] N/A[/COLOR]
[/FONT]
```

Running audacity from the terminal doesn't return any error. Audacity works fine, but the audio system seems to break. Later today I'll check from a live-usb ubuntu version if I can reproduce it also on a "new" installation

---

### Post by #&amp;thj^% on 2023-05-04
Well if you want to help run it in Debug mode see screenshot.
I wish I had more to offer but with out seeing some needed logs I'm just guessing now.
But please try this, run it with:
```
 PULSE_LATENCY_MSEC=50 audacity

```
let me know if that's any better.

---

### Post by enricobe on 2023-05-04
Thanks, it seems not to be an Audacity bug, but a Kubuntu bug.
I've tested it on Kubuntu Live and I can reproduce it all the times. I can't reproduce it on Ubuntu standard, so it seems related to Kubuntu.

I'm going to fill an "ubuntu-bug". If you have some free time, can you please download and boot the Kubuntu Live ISO and see if you can reproduce this bug? No problem if you can't or have no time :-) Thanks for the help

---

### Post by #&amp;thj^% on 2023-05-04
> **enricobe said:**
> 
I'm going to fill an "ubuntu-bug". If you have some free time, can you please download and boot the Kubuntu Live ISO and see if you can reproduce this bug? No problem if you can't or have no time :-) Thanks for the help

Nice of you file the bug, but they will revert you back to Audacity.
I'll have some play time in day or two for kubuntu. ;)

---

### Post by enricobe on 2023-05-06
> **1fallen said:**
> Nice of you file the bug, but they will revert you back to Audacity.
I'll have some play time in day or two for kubuntu. ;)

Thank you very much. If you can reproduce the bug, please mark "Does this bug affect you?" this bug report:
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/2018536](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/2018536)

Thanks!

---

### Post by #&amp;thj^% on 2023-05-06
Dang I'm still doing alright on my end, i did notice in your report alsa-driver.
Could you please try to re-install "alsa-base"
```
sudo apt install --reinstall alsa-base
```
FTR: kubuntu 23.04 was a KVM install.
EDIT: I need to add a possible difference with my sound, and this is strictly up to you >> it runs as follows:
 ```
sudo apt install pipewire-media-session- wireplumber
systemctl --user --now enable wireplumber.service
sudo apt install pipewire-alsa
sudo cp /usr/share/doc/pipewire/examples/alsa.conf.d/99-pipewire-default.conf /etc/alsa/conf.d/
**####That one may not find any directory, No big deal here** 
sudo add-apt-repository ppa:aglasgall/pipewire-extra-bt-codecs
**####I add these codecs now because they were dropped in 23.04** 
sudo apt install libldacbt-{abr,enc}2 libspa-0.2-bluetooth pulseaudio-module-bluetooth-
```
my install includes
```
apt depends audacity
audacity
  Depends: audacity-data (= 3.2.4+dfsg-1)
  Depends: libasound2 (>= 1.0.16)
  Depends: libc6 (>= 2.34)
  Depends: libexpat1 (>= 2.0.1)
  Depends: libflac++10 (>= 1.3.1)
  Depends: libflac12 (>= 1.3.0)
  Depends: libgcc-s1 (>= 3.3.1)
  Depends: libgdk-pixbuf-2.0-0 (>= 2.22.0)
  Depends: libglib2.0-0 (>= 2.12.0)
  Depends: libgtk-3-0 (>= 3.9.10)
  Depends: libid3tag0 (>= 0.15.1b)
  Depends: liblilv-0-0 (>= 0.24.0~dfsg0)
  Depends: libmpg123-0 (>= 1.28.0)
  Depends: libogg0 (>= 1.0rc3)
  Depends: libportaudio2 (>= 19+svn20101113)
  Depends: libportmidi0
  Depends: libportsmf0v5
  Depends: libsbsms10 (>= 2.3.0)
  Depends: libsndfile1 (>= 1.0.20)
  Depends: libsoundtouch1 (>= 2.0.0)
  Depends: libsoxr0 (>= 0.1.0)
  Depends: libsqlite3-0 (>= 3.20.0)
  Depends: libstdc++6 (>= 12)
  Depends: libsuil-0-0 (>= 0.8.0~dfsg0)
  Depends: libtwolame0 (>= 0.3.6)
  Depends: libuuid1 (>= 2.16)
  Depends: libvamp-hostsdk3v5 (>= 2.10.0)
  Depends: libvorbis0a (>= 1.1.2)
  Depends: libvorbisenc2 (>= 1.1.2)
  Depends: libvorbisfile3 (>= 1.1.2)
  Depends: libwavpack1 (>= 5.2.0)
  Depends: libwxbase3.2-1 (>= 3.2.1+dfsg)
  Depends: libwxgtk3.2-1 (>= 3.2.1+dfsg-2)
  Suggests: <ladspa-plugin>
    amb-plugins
    blepvco
    bs2b-ladspa
    csladspa
    guitarix-ladspa
    rev-plugins
    vco-plugins
    ambdec
    autotalent
    blop
    caps
    cmt
    dpf-plugins-ladspa
    fil-plugins
    invada-studio-plugins-ladspa
    ladspa-sdk
    lsp-plugins-ladspa
    mcp-plugins
    omins
    ste-plugins
    swh-plugins
    tap-plugins
    wah-plugins

```
Sound:
```
 inxi -A
Audio:
  Device-1: Intel 82801I HD Audio driver: snd_hda_intel
  Sound API: ALSA v: k6.2.0-20-generic running: yes
  Sound Server-1: PipeWire v: 0.3.65 running: yes

```
```
inxi -Sxxxxa
System:
  Host: me-Standard-PC-Q35-ICH9-2009 Kernel: 6.2.0-20-generic arch: x86_64
    bits: 64 compiler: N/A parameters: BOOT_IMAGE=/boot/vmlinuz-6.2.0-20-generic
    root=UUID=00f2cbae-128c-49bf-909e-73bda2193f39 ro quiet splash
    vt.handoff=7
  Desktop: KDE Plasma v: 5.27.4 tk: Qt v: 5.15.8 wm: kwin_x11 vt: 1 dm: SDDM
    Distro: Ubuntu 23.04 (Lunar Lobster)

```

---

### Post by enricobe on 2023-05-07
Hello,
I tried to reinstall alsa, but the problem still happens. The other commands you suggested returned some dependencies errors so I'll keep the system as-is because I don't won't to risk breaking everything :)
I'll try to ask on the KDE channels if someone can try to reproduce this bug. I don't even know how to find useful information as I can't fully understand which Plasma component is crashing.

EDIT: I can't reproduce it on Fedora KDE. I noticed that Fedora has pipewire 0.3.67 instead of 0.3.65. I'll try to understand if I can update pipwire on Ubuntu, otherwise I'll wait for an update

---

### Post by #&amp;thj^% on 2023-05-07
> **enricobe said:**
> Hello,
I tried to reinstall alsa, but the problem still happens. The other commands you suggested returned some dependencies errors so I'll keep the system as-is because I don't won't to risk breaking everything :)
I'll try to ask on the KDE channels if someone can try to reproduce this bug. I don't even know how to find useful information as I can't fully understand which Plasma component is crashing.

EDIT: I can't reproduce it on Fedora KDE. I noticed that Fedora has pipewire 0.3.67 instead of 0.3.65. I'll try to understand if I can update pipwire on Ubuntu, otherwise I'll wait for an update

If you show me those errors, i can help you. That's sounds fishy "dependencies errors" and might be where your problem is as well.
The only out of place code comes in from the PPA for the Codecs. (They were dropped in 23.04 for licensing reasons)

---

### Post by enricobe on 2023-05-07
Hello,
I tried to re-execute the commands you suggested and they worked fine... I don't know why I get the dependencies issue some hours ago, probably my bad.

I'm really happy to say that your suggestion solved the problem! Now everything works fine! THANKS!

---

### Post by #&amp;thj^% on 2023-05-07
> **enricobe said:**
> Hello,
I tried to re-execute the commands you suggested and they worked fine... I don't know why I get the dependencies issue some hours ago, probably my bad.

I'm really happy to say that your suggestion solved the problem! Now everything works fine! THANKS!

Very Nice, and it might be helpful if you also marked the Bug report as solved, so they are not chasing their tails. ;)

---

### Post by enricobe on 2023-05-07
> **1fallen said:**
> Very Nice, and it might be helpful if you also marked the Bug report as solved, so they are not chasing their tails. ;)

Done! Thanks again

---

