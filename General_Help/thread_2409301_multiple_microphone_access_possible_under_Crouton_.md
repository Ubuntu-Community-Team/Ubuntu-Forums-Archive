---
title: "multiple microphone access possible under Crouton on Chromebooks?"
date: 2018-12-31
forum: General Help
---

### Post by AR_Kozz on 2018-12-31
I am running kubuntu 16.04.5LTS on a Samsung chromebook 3 using chromeOS 70.0.3538.110 official 64 bit. 

I want to use it for a couple of multimedia applications, OBS and Audacity, where to be fully functional I need to mix audio inputs. However, the chroot doesn't seem to detect any audio hardware beyond a single device selected under ChromeOS and passed along to ubuntu as "cras." There is no option in ChromeOS to select more than one input. Under Ubuntu, both alsamixer and pavucontrol show only one input and one output, no matter how many devices actually exist. Each new device plugged in becomes the new "cras" device and the old one is forgotten.

Can I configure ALSA or pulse under the chroot to get past that bottleneck and use all the devices, instead of just seeing the one "cras" device?

---

### Post by Autodave on 2018-12-31
Hopefully I am wrong, but I doubt that you can get more than one working at a time.  The reason is not the operating system, but rather the sound mechanism in the Chromebook: it simply doesn't have the capability to run more than one input at a time.

---

### Post by AR_Kozz on 2019-01-02
I tried copying /dev/snd and manually inputting the PCM device locations in OBS, to no avail. 

After finding out ChromeOS includes alsamixer by default, I found that in in addition to "cras," the list of detected sound cards includes the non-configurable HDMI output ("HDA Intel PCH"), whatever usb devices are plugged in, and something called "chtrt5650." 

chtrt5650 goes from famine to feast with a studio-esque array of channels, gains, ins, outs, etc etc. It seems to be the real hardware under the "virtual" hardware designated "cras" by ChromeOS. But selecting chtrt5650 in alsamixer doesn't seem to affect the audio behavior of ChromeOS, and in Ubuntu alsamixer still sees only "cras." 

This could be as simple as forcing ALSA under ChromeOS to default to using chtrt5650. Even if it breaks sound in ChromeOS it would be worth it to get it working right under Ubuntu.

---

