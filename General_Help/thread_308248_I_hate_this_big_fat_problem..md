---
title: "I hate this big fat problem."
date: 2006-11-27
forum: General Help
---

### Post by jleemc44 on 2006-11-27
Real sound issues.

Having problems with my sound system. No problems or errors are shown in the os but no sound is played.

I checked volume, connections and power.
I checked Alsa mixer and settings.
I Checked to see the device and driver listed in device manager.
Per other suggestions I tried command "sudo totem".
Tried the "Run alsamixer and turn off IEC related options" fix. No IEC options to be found.

Output of aplay --list-devices is:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

lspci shows:

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)


I have a dual boot system, in windows there are no issues, this tells me all connections are correct.

Any help?

Thanks!

---

### Post by ReaderRat on 2006-11-27
I have 82801 ICH7 Intel HDA on both my desktop & my laptop. Desktop was okay out-of-the-box, but the laptop (dual-boot Windoze/Ubuntu), I had to load the driver for sound in Ubuntu 9Win was okay). This is the sound Comprehensive Guide, and all I know about AC'97 ICH6 &7 sound...
[**AC'97 ICH6 Audio**](http://ubuntuforums.org/showpost.php?p=1733758&postcount=3)
Sound Solutions - Comprehensive Guide
       **[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)**

I believe there is an easier way (alsamixer in the repos ?) to do this, but I don't know how.

---

