---
title: "HDMI no longer connects to projector"
date: 2022-04-21
forum: General Help
---

### Post by veramocor on 2022-04-21
Hi all,

I am a teacher and have been using my ubuntu laptop for classes happily for 6 months now. I am using an MSI laptop with the following version specs:

> uname -a
Linux dracolich 5.13.0-40-generic #45~20.04.1-Ubuntu SMP Mon Apr 4 09:38:31 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux

When I went to teach class today the projector would not detect my laptop. In the end I had to cancel class and have tried to look into the problem. Here's what happens in the syslog when I plug in the HDMI cable:

[FONT=monospace][COLOR=#000000]Apr 21 10:56:04 dracolich kernel: [  824.062928] nouveau 0000:01:00.0: DRM: Dropped ACPI[/COLOR] reprobe event due to RPM error: -22

Something has changed in the past 24-48 hours, perhaps with a recent update? Please help me to fix this as I rely heavily on this laptop for teaching and I need to solve this ASAP!

Thanks!
[/FONT]

---

### Post by #&amp;thj^% on 2022-04-21
to help us can you show from that machine with problem:
```
lspci | grep -E '3D|VGA'
```

---

### Post by veramocor on 2022-04-21
> **1fallen said:**
> to help us can you show from that machine with problem:
```
lspci | grep -E '3D|VGA'
```

Thank you. Here is the output.

[FONT=monospace][COLOR=#000000]> lspci | grep -E '3D|VGA' [/COLOR]
00:02.0 VGA compatible controller: Intel Corporation UHD Graphics (rev 05) 
01:00.0 VGA compatible controller: NVIDIA Corporation Device 1e91 (rev a1)


[/FONT]

---

### Post by #&amp;thj^% on 2022-04-21
I'll take this a bit slow, to keep your system intact.
using code tags (see my signature) paste back the return of:
```

dpkg -l | grep -i nvidia
```
also this:
```
grep nomodeset /etc/ -rs
```

---

### Post by veramocor on 2022-04-21
> **1fallen said:**
> I'll take this a bit slow, to keep your system intact.
using code tags (see my signature) paste back the return of:
```

dpkg -l | grep -i nvidia
```
also this:
```
grep nomodeset /etc/ -rs
```

The command "dpkg -l | grep -i nvidia" produces no output.

The command "grep nomodeset /etc/ -rs" produces the following:
```

[FONT=monospace][COLOR=#b218b2]/etc/grub.d/10_linux_zfs[/COLOR][COLOR=#18b2b2]:[/COLOR][COLOR=#000000]        GRUB_CMDLINE_LINUX_RECOVERY="${GRUB_CMDLINE_LINUX_RECOVERY} [/COLOR][COLOR=#ff5454]**nomodeset**[/COLOR][COLOR=#000000]" [/COLOR]
[COLOR=#b218b2]/etc/grub.d/10_linux[/COLOR][COLOR=#18b2b2]:[/COLOR][COLOR=#000000]    GRUB_CMDLINE_LINUX_RECOVERY="$GRUB_CMDLINE_LINUX_RECOVERY [/COLOR][COLOR=#ff5454]**nomodeset**[/COLOR][COLOR=#000000]"
[/COLOR][/FONT]
```[FONT=monospace][COLOR=#000000]
[/COLOR]
[/FONT]

---

### Post by veramocor on 2022-04-21
> **veramocor said:**
> The command "dpkg -l | grep -i nvidia" produces no output.

The command "grep nomodeset /etc/ -rs" produces the following:
```

[FONT=monospace][COLOR=#b218b2]/etc/grub.d/10_linux_zfs[/COLOR][COLOR=#18b2b2]:[/COLOR][COLOR=#000000]        GRUB_CMDLINE_LINUX_RECOVERY="${GRUB_CMDLINE_LINUX_RECOVERY} [/COLOR][COLOR=#ff5454]**nomodeset**[/COLOR][COLOR=#000000]" [/COLOR]
[COLOR=#b218b2]/etc/grub.d/10_linux[/COLOR][COLOR=#18b2b2]:[/COLOR][COLOR=#000000]    GRUB_CMDLINE_LINUX_RECOVERY="$GRUB_CMDLINE_LINUX_RECOVERY [/COLOR][COLOR=#ff5454]**nomodeset**[/COLOR][COLOR=#000000]"
[/COLOR][/FONT]
```[FONT=monospace][COLOR=#000000]
[/COLOR]
[/FONT]

Also, like I said, everything was fine until today. I successfully connected to HDMI at class on Tuesday without a problem. There has been an update since then, so my only thought is that something in the update modified my graphics settings.

---

### Post by #&amp;thj^% on 2022-04-21
Is there a reason you don't want the nvidia driver?
are you really using a zfs system? (I need to know to advise)

---

### Post by veramocor on 2022-04-21
> **1fallen said:**
> Is there a reason you don't want the nvidia driver?
are you really using a zfs system? (I need to know to advise)

I'm agnostic to the driver, so I think I'm using whatever was installed as default. I'm happy with whichever driver works. I apologize, I'm not sure what a zfs system is.

---

### Post by veramocor on 2022-04-21
> **veramocor said:**
> I'm agnostic to the driver, so I think I'm using whatever was installed as default. I'm happy with whichever driver works. I apologize, I'm not sure what a zfs system is.

Also, if it's helpful, here is what has been updated since I last successfully used the HDMI:

```

[FONT=monospace][COLOR=#000000]root@dracolich:/var/lib/dpkg/info# find ./ -name \*.list -mtime -3 | sed 's#.list$##;s#.[/COLOR]
*/##' 
bash 
libevdev2:amd64 
libinput-bin 
klibc-utils 
libklibc:amd64 
libinput10:amd64 
ubuntu-release-upgrader-qt 
ubuntu-release-upgrader-core 
python3-distupgrade 
linux-modules-5.13.0-40-generic 
linux-image-5.13.0-40-generic 
linux-modules-extra-5.13.0-40-generic 
linux-generic-hwe-20.04 
linux-image-generic-hwe-20.04 
linux-hwe-5.13-headers-5.13.0-40 
linux-headers-5.13.0-40-generic 
linux-headers-generic-hwe-20.04 
linux-libc-dev:amd64 
teams
[/FONT]
```[FONT=monospace]
[/FONT]

---

### Post by #&amp;thj^% on 2022-04-21
> **veramocor said:**
> I'm agnostic to the driver, so I think I'm using whatever was installed as default..
:lolflag: your not alone there, many have problems, as to why IJDK
I use and prefer the nVidia driver myself.
to check your format:
```
lsblk -f -e7
```
Also one more:
```
xrandr -q
```

---

### Post by veramocor on 2022-04-21
> **1fallen said:**
> :lolflag: your not alone there, many have problems, as to why IJDK
I use and prefer the nVidia driver myself.
to check your format:
```
lsblk -f -e7
```
Also one more:
```
xrandr -q
```

Here's the output

```

[FONT=monospace][COLOR=#000000]root@dracolich:~# lsblk -f -e7 [/COLOR]
NAME        FSTYPE LABEL UUID                                 FSAVAIL FSUSE% MOUNTPOINT 
nvme0n1                                                                       
&#9500;&#9472;nvme0n1p1 vfat         79E0-22C4                             505.8M     1% /boot/efi 
&#9492;&#9472;nvme0n1p2 ext4         9483c555-7e05-422d-9f3b-9291005d88a3  140.4G    80% / 
root@dracolich:~# xrandr -q 
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 16384 x 16384 
eDP-1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 344mm x
 194mm 
   1920x1080    240.00*+  60.01    59.97    59.96    59.93    60.00   
   1680x1050     84.94    74.89    69.88    59.95    59.88   
   1600x1024     60.17   
   1400x1050     85.00    74.76    70.00    59.98   
   1600x900      59.99    59.94    59.95    59.82   
   1280x1024     85.02    75.02    60.02   
   1440x900      59.89   
   1400x900      59.96    59.88   
   1280x960      85.00    60.00   
   1440x810      60.00    59.97   
   1368x768      59.88    59.85   
   1360x768      59.80    59.96   
   1280x800      59.99    59.97    59.81    59.91   
   1152x864     100.00    85.06    85.00    75.00    75.00    70.00    60.00   
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
   800x600       85.00    75.00    70.00    65.00    60.00    85.14    72.19    75.00   
 60.32    56.25   
   840x525       85.02    74.96    69.88    60.01    59.88   
   864x486       59.92    59.57   
   800x512       60.17   
   700x525       85.08    74.76    70.06    59.98   
   800x450       59.95    59.82   
   640x512       85.02    75.02    60.02   
   720x450       59.89   
   700x450       59.96    59.88   
   640x480       85.09    60.00    85.01    72.81    75.00    59.94   
   720x405       59.51    58.99   
   720x400       85.04   
   684x384       59.88    59.85   
   680x384       59.80    59.96   
   640x400       59.88    59.98    85.08   
   576x432      100.11    85.15    85.09    75.00    75.00    70.00    60.06   
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
eDP-1-2 disconnected (normal left inverted right x axis y axis) 
DP-1-1 disconnected (normal left inverted right x axis y axis) 
DP-1-2 disconnected (normal left inverted right x axis y axis) 
HDMI-1-1 disconnected (normal left inverted right x axis y axis)
[/FONT]
```

---

### Post by veramocor on 2022-04-21
> **1fallen said:**
> :lolflag: your not alone there, many have problems, as to why IJDK
I use and prefer the nVidia driver myself.
to check your format:
```
lsblk -f -e7
```
Also one more:
```
xrandr -q
```

Honestly, given that I'm a little on the desperate side, is reverting the recent packages an option? Not sure how to do that.

---

### Post by #&amp;thj^% on 2022-04-21
> **veramocor said:**
> Honestly, given that I'm a little on the desperate side, is reverting the recent packages an option? Not sure how to do that.

possible yes. wise NO.
it just prolongs a pending problem.
your xrandr shows a few times with different screens may have got lost just when you needed it, as shown:
eDP-1-2 
DP-1-1 
DP-1-2 
HDMI-1-1
tell me if you get a display configuration box with: Key combo <Super/or sometimes Windows Logo + p>
if you do leave it open

---

### Post by veramocor on 2022-04-21
> **1fallen said:**
> possible yes. wise NO.
it just prolongs a pending problem.
your xrandr shows a few times with different screens may have got lost just when you needed it, as shown:
eDP-1-2 
DP-1-1 
DP-1-2 
HDMI-1-1
tell me if you get a display configuration box with: Key combo <Super/or sometimes Windows Logo + p>
if you do leave it open

Yes, I get the display configuration box. See attached image.

---

### Post by #&amp;thj^% on 2022-04-21
Can you at this time plug the HDMI projector or another HDMI monitor to check.

---

### Post by veramocor on 2022-04-21
> **1fallen said:**
> Can you at this time plug the HDMI projector or another HDMI monitor to check.

It looks identical with the HDMI plugged in.

---

### Post by #&amp;thj^% on 2022-04-21
bottom of that box connect to "external monitor"

---

### Post by veramocor on 2022-04-21
> **veramocor said:**
> It looks identical with the HDMI plugged in.

Also, the projector claims that there's no signal. Like I said earlier, /var/log/syslog is reporting the following when I plug/unplug the HDMI:

```

[FONT=monospace][COLOR=#000000]Apr 21 12:37:50 dracolich kernel: [ 6535.764294] nouveau 0000:01:00.0: DRM: Dropped ACPI[/COLOR] reprobe event due to RPM error: -22
[/FONT]
```[FONT=monospace]
[/FONT]

---

### Post by veramocor on 2022-04-21
> **1fallen said:**
> bottom of that box connect to "external monitor"

Nothing happens when I select "external screen". It's as though the laptop is not even recognizing the HDMI connection.

---

### Post by #&amp;thj^% on 2022-04-21
> **veramocor said:**
> Also, the projector claims that there's no signal. Like I said earlier, /var/log/syslog is reporting the following when I plug/unplug the HDMI:

```

[FONT=monospace][COLOR=#000000]Apr 21 12:37:50 dracolich kernel: [ 6535.764294] nouveau 0000:01:00.0: DRM: Dropped ACPI[/COLOR] reprobe event due to RPM error: -22
[/FONT]
```[FONT=monospace]
[/FONT]

yep all that is clear, we need to stay clam and relaxed, is there another HDMI monitor that check for sure it's not just the projector.

---

### Post by veramocor on 2022-04-21
> **1fallen said:**
> yep all that is clear, we need to stay clam and relaxed, is there another HDMI monitor that check for sure it's not just the projector.

I've moved to a different classroom and same outcome I'm afraid. No HDMI signal detected by projector, and the display configuration options have no effect.

---

### Post by #&amp;thj^% on 2022-04-21
As badly as i hate to mention a possible bad hdmi port or cable. it still remains.
at this time are you to up to installing the nvidia driver? (it's still a guess if it will help)

---

### Post by veramocor on 2022-04-21
> **1fallen said:**
> As badly as i hate to mention a possible bad hdmi port or cable. it still remains.
at this time are to up to installing the nvidia driver? (it's still a guess if it will help)

Yes, happy to try nvidia. Regarding a possible bad hdmi port (have tried several cables), doesn't the syslog messages whenever I plug/unplug the hdmi cable show that the port is still recognized?

---

### Post by #&amp;thj^% on 2022-04-21
> **veramocor said:**
>  doesn't the syslog messages whenever I plug/unplug the hdmi cable show that the port is still recognized?
yes but doesn't power on.
Ok lets make this thing happen. :)
run: 
```
ubuntu-drivers devices
```
&#8674;select the _recommended driver _&#8674;Apply Changes &#8674;reboot
I got my fingers crossed. ;)

---

### Post by veramocor on 2022-04-21
> **1fallen said:**
> yes but doesn't power on.
Ok lets make this thing happen. :)
run: 
```
ubuntu-drivers devices
```
&#8674;select the _recommended driver _&#8674;Apply Changes &#8674;reboot
I got my fingers crossed. ;)

Here is what happens when I run this as root:

```

[FONT=monospace][COLOR=#000000]> ubuntu-drivers devices [/COLOR]
WARNING:root:_pkg_get_support nvidia-driver-510-server: package has invalid Support PBheader, cannot determine support level 
WARNING:root:_pkg_get_support nvidia-driver-510: package has invalid Support PBheader, cannot determine support level 
== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 == 
modalias : pci:v000010DEd00001E91sv00001462sd000012AEbc03sc00i00 
vendor   : NVIDIA Corporation 
driver   : nvidia-driver-510-server - distro non-free 
driver   : nvidia-driver-470-server - distro non-free 
driver   : nvidia-driver-450-server - distro non-free 
driver   : nvidia-driver-510 - distro non-free 
driver   : nvidia-driver-470 - distro non-free recommended 
driver   : xserver-xorg-video-nouveau - distro free builtin
[/FONT]
```[FONT=monospace]

I'm not sure how to interpret this.
[/FONT]

---

### Post by veramocor on 2022-04-21
I assume I'm currently using xserver-xorg-video-nouveau and need to switch to nvidia-driver-470? Sorry, you might need to explain like I'm 5 on how to do this.

---

### Post by #&amp;thj^% on 2022-04-21
> **veramocor said:**
> Here is what happens when I run this as root:

```

[FONT=monospace][COLOR=#000000]> ubuntu-drivers devices [/COLOR]
WARNING:root:_pkg_get_support nvidia-driver-510-server: package has invalid Support PBheader, cannot determine support level 
WARNING:root:_pkg_get_support nvidia-driver-510: package has invalid Support PBheader, cannot determine support level 
== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 == 
modalias : pci:v000010DEd00001E91sv00001462sd000012AEbc03sc00i00 
vendor   : NVIDIA Corporation 
driver   : nvidia-driver-510-server - distro non-free 
driver   : nvidia-driver-470-server - distro non-free 
driver   : nvidia-driver-450-server - distro non-free 
driver   : nvidia-driver-510 - distro non-free 
driver   : nvidia-driver-470 - distro non-free recommended 
driver   : xserver-xorg-video-nouveau - distro free builtin
[/FONT]
```[FONT=monospace]

I'm not sure how to interpret this.
[/FONT]
well the recommended is "nvidia-driver-470 - distro non-free recommended "
But close the terminal and go to "Software and Updates" in the top tab select "Additional Drivers" let it populate and click the nvidia-driver-470 - distro non-free recommended, let it install and reboot.
I added a screenshot

---

### Post by veramocor on 2022-04-21
> **1fallen said:**
> well the recommended is "nvidia-driver-470 - distro non-free recommended "
But close the terminal and go to "Software and Updates" in the top tab select "Additional Drivers" let it populate and click the nvidia-driver-470 - distro non-free recommended, let it install and reboot.
I added a screenshot

Installing ... will report back.

---

### Post by veramocor on 2022-04-21
> **veramocor said:**
> Installing ... will report back.

I have installed new drivers and rebooted. Now  it *kind of* works. By that, I mean the first time I plug in the HDMI, nothing happens and I get this in the /var/log/syslog:

```

Apr 21 13:51:10 dracolich kernel: [  705.233119] usb usb3: root hub lost power or was reset
Apr 21 13:51:10 dracolich kernel: [  705.233121] usb usb4: root hub lost power or was reset
Apr 21 13:51:11 dracolich wpa_supplicant[864]: wlo1: CTRL-EVENT-SIGNAL-CHANGE above=1 signal=-63 noise=9999 txrate=173300

```

If I unplug and plug back in again, it works, with these log messages:

```

[FONT=monospace][COLOR=#000000]Apr 21 13:52:56 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: RRNotify_OutputChange [/COLOR]
Apr 21 13:52:56 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: #011Output:  630 
Apr 21 13:52:56 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: #011CRTC:  0 
Apr 21 13:52:56 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: #011Mode:  0 
Apr 21 13:52:56 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: #011Rotation:  "Rotate_0" 
Apr 21 13:52:56 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: #011Connection:  "Connected" 
Apr 21 13:52:56 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: #011Subpixel Order:  0 
Apr 21 13:52:56 dracolich org.kde.KScreen[1432]: kscreen.xrandr: XRandROutput 630 update 
Apr 21 13:52:56 dracolich org.kde.KScreen[1432]:  #011m_connected: 1 
Apr 21 13:52:56 dracolich org.kde.KScreen[1432]:  #011m_crtc QObject(0x0) 
Apr 21 13:52:56 dracolich org.kde.KScreen[1432]:  #011CRTC: 0 
Apr 21 13:52:56 dracolich org.kde.KScreen[1432]:  #011MODE: 0 
Apr 21 13:52:56 dracolich org.kde.KScreen[1432]:  #011Connection: 0 
Apr 21 13:52:56 dracolich org.kde.KScreen[1432]:  #011Primary: false 
Apr 21 13:52:56 dracolich org.kde.KScreen[1432]: kscreen.xrandr: Output 630 : connected = true , enabled = false 
Apr 21 13:52:56 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: RRScreenChangeNotify 
Apr 21 13:52:56 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: #011Window: 48234501 
Apr 21 13:52:56 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: #011Root: 2410 
Apr 21 13:52:56 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: #011Rotation:  "Rotate_0" 
Apr 21 13:52:56 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: #011Size ID: 0 
Apr 21 13:52:56 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: #011Size:  1920 1080 
Apr 21 13:52:56 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: #011SizeMM:  497 280 
Apr 21 13:52:56 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: RRNotify_OutputChange 
Apr 21 13:52:56 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: #011Output:  630 
Apr 21 13:52:56 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: #011CRTC:  0 
Apr 21 13:52:56 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: #011Mode:  0 
Apr 21 13:52:56 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: #011Rotation:  "Rotate_0" 
Apr 21 13:52:56 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: #011Connection:  "Connected" 
Apr 21 13:52:56 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: #011Subpixel Order:  0 
Apr 21 13:52:56 dracolich org.kde.KScreen[1432]: kscreen.xrandr: XRandROutput 630 update 
Apr 21 13:52:56 dracolich org.kde.KScreen[1432]:  #011m_connected: 0 
Apr 21 13:52:56 dracolich org.kde.KScreen[1432]:  #011m_crtc QObject(0x0) 
Apr 21 13:52:56 dracolich org.kde.KScreen[1432]:  #011CRTC: 0 
Apr 21 13:52:56 dracolich org.kde.KScreen[1432]:  #011MODE: 0 
Apr 21 13:52:56 dracolich org.kde.KScreen[1432]:  #011Connection: 0 
Apr 21 13:52:56 dracolich org.kde.KScreen[1432]:  #011Primary: false 
Apr 21 13:52:56 dracolich org.kde.KScreen[1432]: kscreen.xrandr: Output 630 : connected = true , enabled = false 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xrandr: Emitting configChanged() 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xrandr: XRandR::setConfig 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xrandr: Requested screen size is QSize(3839, 1080) 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xrandr: Needed CRTCs:  2 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xrandr: Actions to perform: 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]:  #011Primary Output: false 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xrandr: #011Change Screen Size: true 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xrandr: #011#011Old: QSize(1920, 1080) 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]:  #011#011Intermediate: QSize(3839, 1080) 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]:  #011#011New: QSize(3839, 1080) 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xrandr: #011Disable outputs: false 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xrandr: #011Change outputs: true 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xrandr: #011#011 (66) 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xrandr: #011Enable outputs: true 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xrandr: #011#011 (630) 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xrandr: RRSetScreenSize 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]:  #011DPI: 97.9714 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]:  #011Size: QSize(3839, 1080) 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]:  #011SizeMM: QSize(995, 280) 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xrandr: RRSetCrtcConfig (change output) 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]:  #011Output: 66 ( "eDP-1" ) 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]:  #011CRTC: 63 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]:  #011Pos: QPoint(0,0) 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]:  #011Mode: 68 KScreen::Mode(Id: "68" , Size: QSize(1920, 1080) @ 240 ) 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]:  #011Rotation: 1 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xrandr: #011Result:  0 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xrandr: XRandROutput 66 update 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]:  #011m_connected: 0 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]:  #011m_crtc XRandRCrtc(0x55e9f3122570) 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]:  #011CRTC: 63 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]:  #011MODE: 68 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]:  #011Connection: 0 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]:  #011Primary: true 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xrandr: QMap((63, XRandRCrtc(0x55e9f3122570))(64, XRandRCrtc(0x55e9f3120ad0))(65, XRandRCrtc(0x55e9f3121a40))(622, XRandRCrtc(0x55e9f3121850))(623, XRandRCrtc(0x55e9f31218a0))(624, XRandRCrtc(0x55e9f3121050))(625, 
XRandRCrtc(0x55e9f3129980))) 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xrandr: Testing CRTC 63 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]:  #011Free: false 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]:  #011Mode: 68 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]:  #011Possible outputs: QVector(66) 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]:  #011Connected outputs: QVector(66) 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]:  #011Geometry: QRect(0,0 1920x1080) 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xrandr: Testing CRTC 64 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]:  #011Free: true 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]:  #011Mode: 0 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]:  #011Possible outputs: QVector(66) 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]:  #011Connected outputs: QVector() 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]:  #011Geometry: QRect(0,0 0x0) 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xrandr: Testing CRTC 65 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]:  #011Free: true 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]:  #011Mode: 0 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]:  #011Possible outputs: QVector(66) 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]:  #011Connected outputs: QVector() 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]:  #011Geometry: QRect(0,0 0x0) 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xrandr: Testing CRTC 622 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]:  #011Free: true 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]:  #011Mode: 0 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]:  #011Possible outputs: QVector(626, 627, 628, 629, 630, 631) 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]:  #011Connected outputs: QVector() 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]:  #011Geometry: QRect(0,0 0x0) 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xrandr: RRSetCrtcConfig (enable output) 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]:  #011Output: 630 ( "HDMI-1-0" ) 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]:  #011New CRTC: 622 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]:  #011Pos: QPoint(1919,0) 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]:  #011Mode: KScreen::Mode(Id: "2516" , Size: QSize(1920, 1080) @ 60 ) Preferred: "2516" 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]:  #011Rotation: 1 
Apr 21 13:52:57 dracolich rtkit-daemon[1199]: Supervising 5 threads of 3 processes of 1 users. 
Apr 21 13:52:57 dracolich rtkit-daemon[1199]: Successfully made thread 4316 of process 1237 owned by '1000' RT at priority 5. 
Apr 21 13:52:57 dracolich rtkit-daemon[1199]: Supervising 6 threads of 3 processes of 1 users. 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xrandr: #011Result:  0 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xrandr: XRandROutput 630 update 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]:  #011m_connected: 0 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]:  #011m_crtc QObject(0x0) 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]:  #011CRTC: 622 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]:  #011MODE: 2516 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]:  #011Connection: 0 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]:  #011Primary: false 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xrandr: Connected output 630 to CRTC 622 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xrandr: XRandR::setConfig done! 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: RRScreenChangeNotify 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: #011Window: 48234501 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: #011Root: 2410 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: #011Rotation:  "Rotate_0" 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: #011Size ID: 65535 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: #011Size:  3839 1080 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: #011SizeMM:  995 280 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: RRNotify_CrtcChange 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: #011CRTC:  622 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: #011Mode:  2516 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: #011Rotation:  "Rotate_0" 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: #011Geometry:  1919 0 1920 1080 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: RRNotify_OutputChange 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: #011Output:  630 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: #011CRTC:  622 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: #011Mode:  2516 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: #011Rotation:  "Rotate_0" 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: #011Connection:  "Connected" 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: #011Subpixel Order:  0 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: RRScreenChangeNotify 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: #011Window: 48234501 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: #011Root: 2410 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: #011Rotation:  "Rotate_0" 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: #011Size ID: 65535 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: #011Size:  3839 1080 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: #011SizeMM:  995 280 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: RRNotify_CrtcChange 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: #011CRTC:  622 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: #011Mode:  2516 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: #011Rotation:  "Rotate_0" 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: #011Geometry:  1919 0 1920 1080 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: RRNotify_OutputChange 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: #011Output:  630 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: #011CRTC:  622 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: #011Mode:  2516 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: #011Rotation:  "Rotate_0" 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: #011Connection:  "Connected" 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: #011Subpixel Order:  0 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: RRNotify_CrtcChange 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: #011CRTC:  63 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: #011Mode:  68 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: #011Rotation:  "Rotate_0" 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: #011Geometry:  0 0 1920 1080 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: RRNotify_CrtcChange 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: #011CRTC:  64 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: #011Mode:  0 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: #011Rotation:  "Rotate_0" 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: #011Geometry:  0 0 0 0 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: RRNotify_CrtcChange 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: #011CRTC:  65 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: #011Mode:  0 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: #011Rotation:  "Rotate_0" 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: #011Geometry:  0 0 0 0 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: RRNotify_OutputChange 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: #011Output:  66 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: #011CRTC:  63 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: #011Mode:  68 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: #011Rotation:  "Rotate_0" 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: #011Connection:  "Connected" 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xcb.helper: #011Subpixel Order:  0 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xrandr: XRandROutput 630 update 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]:  #011m_connected: 0 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]:  #011m_crtc XRandRCrtc(0x55e9f3121850) 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]:  #011CRTC: 622 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]:  #011MODE: 2516 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]:  #011Connection: 0 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]:  #011Primary: false 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xrandr: Output 630 : connected = true , enabled = true 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xrandr: XRandROutput 630 update 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]:  #011m_connected: 0 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]:  #011m_crtc XRandRCrtc(0x55e9f3121850) 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]:  #011CRTC: 622 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]:  #011MODE: 2516 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]:  #011Connection: 0 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]:  #011Primary: false 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xrandr: Output 630 : connected = true , enabled = true 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xrandr: XRandROutput 66 update 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]:  #011m_connected: 0 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]:  #011m_crtc XRandRCrtc(0x55e9f3122570) 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]:  #011CRTC: 63 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]:  #011MODE: 68 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]:  #011Connection: 0 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]:  #011Primary: true 
Apr 21 13:52:57 dracolich org.kde.KScreen[1432]: kscreen.xrandr: Output 66 : connected = true , enabled = true 
Apr 21 13:52:58 dracolich org.kde.KScreen[1432]: kscreen.xrandr: Emitting configChanged()
[/FONT]
```[FONT=monospace]

I've tried this several times and it only successfully connects to the HDMI on alternate plugins. Any idea what is happening?
[/FONT]

---

### Post by #&amp;thj^% on 2022-04-21
none yet, things of this nature really don't have a one shot fix or magic bullet.
try this please:
```
sudo prime-select nvidia
```
you will have to log out for it to take effect.

---

### Post by veramocor on 2022-04-21
> **1fallen said:**
> none yet, things of this nature really don't have a one shot fix or magic bullet.
try this please:
```
sudo prime-select nvidia
```
you will have to log out for it to take effect.

Right, I just did that and restarted and have good news! The HDMI now appears to be behaving as normal with every plugin. Fallen, I cannot adequately express my gratitude for helping me on this!! You really have rescued me!! In future, I'll keep a close rye on the display drivers when installing and maintaining systems.

---

### Post by #&amp;thj^% on 2022-04-21
Great, that's very kind of you.
and your watch on drivers is always a good idea. :)
EDIT: I forgot to mention to revert back to Intel use:
```
sudo prime-select intel
```

---

### Post by veramocor on 2022-04-27
I have now been using the nvidia driver for about a week and I have a follow-up question if I may. Since using the nvidia driver, the windows environment is often much slower to switch application displays. For example, if I'm using the browser and then switch to a console window so that it appears on top of the browser, it can sometimes take a few seconds to correctly display the console window. Are there any tips on how to improve the response time of the nvidia driver?

---

### Post by #&amp;thj^% on 2022-04-27
> **veramocor said:**
> I have now been using the nvidia driver for about a week and I have a follow-up question if I may. Since using the nvidia driver, the windows environment is often much slower to switch application displays. For example, if I'm using the browser and then switch to a console window so that it appears on top of the browser, it can sometimes take a few seconds to correctly display the console window. Are there any tips on how to improve the response time of the nvidia driver?

Regretfully no. :(
Nvidia and Linux is a, we take what we get from them.
If the nvidia driver is not needed with those cases you cite, switch to intel.
```
sudo prime-select intel
```
not very elegant but it is what it is. :)

---

