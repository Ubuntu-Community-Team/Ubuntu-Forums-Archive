---
title: "Flickering of lines and icons in web browser"
date: 2022-12-08
forum: General Help
---

### Post by dwhitney67 on 2022-12-08
Hello,

OS: Kubuntu 22.04

Yesterday I installed "kept-back" packages using apt; the packages were: kubuntu-desktop libsmbclient libwbclient0 python3-samba samba samba-common samba-common-bin samba-dsdb-modules samba-libs samba-vfs-modules smbclient xserver-common xserver-xorg-core xserver-xorg-legacy

Following a reboot, and once logged back in, I noticed the desktop environment was slightly blurry and that when viewing a web browser there was the flickering of lines with certain color and, even while posting this thread, the flickering of icons in the tool bar.

Is there a way to resolve this issue or to revert the s/w updates which were installed?

Note: The very first video, of the first post, at this site, exhibits a similar issue to that I am witnessing: [https://github.com/LizardByte/Sunshine/issues/154](https://github.com/LizardByte/Sunshine/issues/154)

Attached is /var/log/gpu-manager.log (albeit renamed with a txt extension). I am unable to upload Xorg.0.log due to its size.

---

### Post by mIk3_08 on 2022-12-10
I also experience this kind of display when I try to force my display to a higher resolution using zrandr with additional new mode display. Forcing my display from 1366x768 to 1920x1080. The desktop display and text are blurry, text are not displaying even clearly. I did try to do a screenshot with the abnormal display system and viewing it with my normal system display and the image screenshot result looks really find. Looks so normal and the text are so clear. What i did is to return it back to the original display which is the 1366x768. Regards and cheers.

---

### Post by dwhitney67 on 2022-12-11
Thank you for the suggestion. I took it and applied it to my system (a laptop) that relies on an external monitor. The monitor is capable of 1920x1080, however I had to drop the resolution to 1680x1050.

All text and windows appear slightly larger, but at least there is no more flickering and the text is no longer blurry.

Again, thank you.

---

### Post by mIk3_08 on 2022-12-11
> **dwhitney67 said:**
> Thank you for the suggestion. I took it and applied it to my system (a laptop) that relies on an external monitor. The monitor is capable of 1920x1080, however I had to drop the resolution to 1680x1050.

All text and windows appear slightly larger, but at least there is no more flickering and the text is no longer blurry.

Again, thank you.

Also mine, my video card is capable of a high resolution but the monitor can only display 1366x768 and you are right text and windows appear slightly large. I just adjusted the font using GNOME Tweaks 42.
Under Fonts I just adjusted the scaling factor below 1. Maybe it might help you. see image below.

---

### Post by dwhitney67 on 2022-12-17
As a follow up, I fixed (sort of) the issue with the blurry text and flickering. I am now operating at 1920x1080 and the screen is stellar. Here's what I did:

Step 1: Identify the display causing the issue...
```
$ xrandr
```


In my case, it is HDMI-1.

Step 2: Modify the display with the desired refresh rate... in my case, I assumed it should be 60...
```
$ xrandr --output HDMI-1 --mode 1920x1080 --rate 60
```

I am not sure why the previous step is necessary. The video driver should have known which refresh rate to use.

Note, I need to repeat the second *xrandr* command when I reboot. Fortunately, that won't be necessary very often because I keep my laptop on for months at a time.

---

