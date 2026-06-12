---
title: "EDID kernel parameters above 6.2"
date: 2024-01-31
forum: General Help
---

### Post by libertyspike138 on 2024-01-31
Hello I have a machine that is on 22.04.3 LTS running lowlatency HWE kernel. The graphics are Intel HD 530 using the i915 driver. Pretty recently my system updated from kernel 6.2.0-1018-lowlatency to 6.5.0-14-lowlatency at which point graphics stopped working and it loaded up as 640X480 and would only max out at 1024X768 instead of 1080 so I ended up removing it and reverting back to kernel 6.2.0-1018-lowlatency. I just saw there was an update to 6.5.0-15-lowlatency so I once again gave it a try yet still the same thing. Is there some sort of incompatibility beyond 6.2.0-1018-lowlatency with this GPU / driver? Thanks!

---

### Post by libertyspike138 on 2024-01-31
So what I previously failed to mention is the fact that I'm using an old VGA KVM switch that has it's own EDID data that maxes out at 1024X768. I have always got around this by connecting the monitor directly to the machine, extracting the EDID data from the monitor as a binary file and then pushing the actual monitor EDID data as a kernel parameter when the KVM is hooked up like this "drm.edid_firmware=edid/HP_24w.bin". Out of curiosity I decided to hook the monitor up directly while booting 6.5 and it was fine so at this point the only conclusion I can come to is that the way you would push such a kernel parameter for an EDID has changed between kernel 6.2 & 6.5. If anybody has any suggestions it would be greatly appreciated. P.S. Buying an expensive 4 way HDMI KVM switch is not an option, this KVM is not that old and has USB that replaced my old PS2 one. :D

---

### Post by libertyspike138 on 2024-01-31
Also thought that I would mention that at one point the kernel parameter used to be "drm_kms_helper.edid_firmware=edid/edid.bin" but at some point it switched to "drm.edid_firmware=edid/edid.bin" but apparently this does not work now above 6.2.

---

### Post by MAFoElffen on 2024-01-31
That should still be current.

RE: [https://docs.kernel.org/admin-guide/kernel-parameters.html](https://docs.kernel.org/admin-guide/kernel-parameters.html)
> 
  drm.edid_firmware=[<connector>:]<file>[,[<connector>:]<file>][INDENT]Broken monitors, graphic adapters, KVMs and EDIDless panels may send no or incorrect EDID data sets. This parameter allows to specify an EDID data sets
                        in the /lib/firmware directory that are used instead. Generic built-in EDID data sets are used, if one of edid/1024x768.bin, edid/1280x1024.bin, edid/1680x1050.bin, or edid/1920x1080.bin is given and no file with the same name exists. Details and instructions how to build your own EDID data are available in Documentation/admin-guide/edid.rst. An EDID data set will only be used for a particular connector, if its name and a colon are prepended to the EDID name. Each connector may use a unique EDID data set by separating the files with a comma.  An EDID data set with no connector name will be used for any connectors not explicitly specified.
[/INDENT]
 
I would file a bug against linux 
```

ubuntu-bug linux

```
and tell them it is for Linux image, those series low-latency kernels are not honoring that kernel parameter option. It seems to be a bug. Maybe in how the kernel was compiled. It doesn't look like there was any change upstream.

---

### Post by libertyspike138 on 2024-01-31
What is strange is that if I run "cat /sys/module/drm_kms_helper/parameters/edid_firmware" it still returns "edid/HP_24w.bin" when booting under 6.5.X and it still shows up as "HPN 24"" in my display preferences but all of my resolutions are gone above 1024X768.

The following is all searches for edid in dmesg -H.

"
[  +0.020644] i915 0000:00:02.0: Direct firmware load for edid/HP_24>
[  +0.000009] i915 0000:00:02.0: [drm] *ERROR* [CONNECTOR:108:DP-1] >
[  +0.003338] fbcon: i915drmfb (fb0) is primary device
[  +0.031765] Console: switching to colour frame buffer device 128x48
[  +0.017750] i915 0000:00:02.0: [drm] fb0: i915drmfb frame buffer d>
[  +0.025692] i915 0000:00:02.0: Direct firmware load for edid/HP_24>
[  +0.000043] i915 0000:00:02.0: [drm] *ERROR* [CONNECTOR:108:DP-1] >
[  +0.027311] i915 0000:00:02.0: Direct firmware load for edid/HP_24>
[  +0.000004] i915 0000:00:02.0: [drm] *ERROR* [CONNECTOR:108:DP-1] >
"

If I run xrandr when booting to kernel 6.5.X it returns the following.

"
xrandr
Screen 0: minimum 320 x 200, current 640 x 480, maximum 16384 x 16384
HDMI-1 disconnected (normal left inverted right x axis y axis)
HDMI-2 disconnected (normal left inverted right x axis y axis)
DP-1 connected 640x480+0+0 (normal left inverted right x axis y axis) 527mm x 296mm
   640x480       59.94*+
   1024x768      60.00  
   800x600       60.32    56.25  
   848x480       60.00  
HDMI-3 disconnected (normal left inverted right x axis y axis)
"

But when booting it 6.2.X it returns

"
xrandr
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 16384 x 16384
HDMI-1 disconnected (normal left inverted right x axis y axis)
HDMI-2 disconnected (normal left inverted right x axis y axis)
DP-1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 527mm x 296mm
   1920x1080     60.00*+
   1680x1050     59.95  
   1600x900      60.00  
   1280x1024     60.02  
   1440x900      59.89  
   1280x800      59.81  
   1280x720      60.00  
   1024x768      60.00  
   800x600       60.32  
   640x480       59.94  
   720x400       70.08  
HDMI-3 disconnected (normal left inverted right x axis y axis)
"

---

### Post by libertyspike138 on 2024-01-31
If I boot my working 6.2.X kernel without the kernel parameter "drm.edid_firmware=edid/edid.bin" to use my extracted edid I end up with the same 4 low resolutions that I get when booting 6.5.X. I also installed generic to make sure that it was not only affecting lowlatency and ended up with the same results.

---

### Post by libertyspike138 on 2024-01-31
I have mostly solved it. I decided to go ahead and re run xrandr and it did switch over so I was wondering why my xrandr script was not doing it automatically at startup and I checked and then remembered that I had disabled it at some point. The reason that I had disabled it quite some time ago was because it became redundant either after "drm_kms_helper.edid_firmware=edid/edid.bin" was deprecated and became "drm.edid_firmware=edid/edid.bin" or after a kernel update. What started happening was all the resolutions would just work and my script was creating duplicate resolutions so it was no longer needed but I can see that it is once again needed on a kernel above 6.2. Now the problem that I have is after login it is on 640X480 for a moment before switching to 1080 and as a result it skrinks my plank panel to a tiny fraction of what it should be unless I go in and change the resolution in my display preferences so I need to find a way to run it and set the resolution before login instead of a startup application on login.

---

### Post by libertyspike138 on 2024-01-31
So I tried copying ~/.config/monitors.xml to /var/lib/gdm3/.config/ and running "sudo dpkg-reconfigure gdm3" with no changes and ended up having to create a xorg.conf file that was not present like it was in the old days in order to avoid using the script and having to start in 640X480 first. My keystore screen and login screen remain at 640X480 but it is now logging in at my desired resolution after creating the xorg.conf file.

I still don't know what all of this is about. Is it failing because it is trying to load it before the keystore unlocks the rpool to grab it? 

"
[  +0.020587] i915 0000:00:02.0: Direct firmware load for edid/HP_24w.bin failed with error -2
[  +0.000021] i915 0000:00:02.0: [drm] *ERROR* [CONNECTOR:108:DP-1] Requesting EDID firmware "edid/HP_24w.bin" failed (err=-2)
[  +0.003503] fbcon: i915drmfb (fb0) is primary device
[  +0.042318] Console: switching to colour frame buffer device 128x48
[  +0.019248] i915 0000:00:02.0: [drm] fb0: i915drmfb frame buffer device
[  +0.030015] i915 0000:00:02.0: Direct firmware load for edid/HP_24w.bin failed with error -2
[  +0.000050] i915 0000:00:02.0: [drm] *ERROR* [CONNECTOR:108:DP-1] Requesting EDID firmware "edid/HP_24w.bin" failed (err=-2)
[  +0.038171] i915 0000:00:02.0: Direct firmware load for edid/HP_24w.bin failed with error -2
[  +0.000004] i915 0000:00:02.0: [drm] *ERROR* [CONNECTOR:108:DP-1] Requesting EDID firmware "edid/HP_24w.bin" failed (err=-2)
"

If I run "cat /sys/module/drm_kms_helper/parameters/edid_firmware" it still returns "edid/HP_24w.bin" is loaded and the monitor name still shows up in my display preferences...

---

### Post by libertyspike138 on 2024-02-01
As I suspected it does not find the edid due to it being on an encrypted zpool so I created a hook with the following.
"
#!/bin/sh
PREREQ=""
prereqs()
{
echo "$PREREQ"
}
case $1 in
prereqs)
prereqs
exit 0
;;
esac
. /usr/share/initramfs-tools/hook-functions
# Begin real processing below this line
mkdir -p "${DESTDIR}/lib/firmware/edid"
cp -a /lib/firmware/edid/HP_24w.bin "${DESTDIR}/lib/firmware/edid/HP_24w.bin"
exit 0
"
Now the error messages are gone in dmesg and even though I mostly use xfce under X11, if I use Wayland instead I'm still stuck with 640X480 up to 1024X768 resolution unless I run xrandr scripts after login considering that Wayland does not use the xorg.conf file where I set my res to 1080.

---

### Post by MAFoElffen on 2024-02-01
I was going to say, in xorg.conf, Section device, you could have also used 
```

  Option         "CustomEDID" "DFP-0:/lib/firmware/edid/HP_24w.bin"
  Option         "IgnoreEDID" "false"
  Option         "UseEDID" "true"

```
But you are using Wayland...

---

### Post by libertyspike138 on 2024-02-02
I mostly xfce with X11 but when I was testing Wayland after getting rid of the dmesg errors I noticed it is still only has the low resolutions between 640X480 & 1024X768. Below is what I have in xorg.conf to login at 1080 and then I have login script running to add more modes via xrandr but not switching to any of them.

> Section "Monitor"
    Identifier "DP-1"
    Modeline   "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
EndSection 

---

