---
title: "ADB/MTP not working on android device/won't connect at all"
date: 2013-09-23
forum: General Help
---

### Post by ryan36 on 2013-09-23
I'm on Ubuntu 13.04, I'm trying to connect my HTC One (m7att) to my laptop. The problem is, it won't register at all. If I've freshly restarted my phone, Ubuntu gives me an error about MTP not mounting with the usb device. adb (installed and configured correctly) never returns anything but a blank line when running adb devices. I've tried multiple tools/scripts found on xda (such as Android Forks and Knives) and I've tried creating/editing the xx-android.rules file at /etc/udev/rules.d/
Restarting udev doesn't work, killing the adb server and restarting it, as root or not, doesn't work. It's driving me crazy because I can't think of why else this wouln't be working. Last bit of information is if my phone hasn't been freshly rebooted, connecting it to the laptop's usb does nothing. No dialogue box popping up, no error about MTP, no sound confirmation. Phone doesn't even charge while it's connected. If anyone at all could help me with this I'd be deeply grateful..I'm trying to teach myself how to build android from source, and I've been good until now, the one thing getting in my way is the phone I'm trying to build for not connecting to my computer. bummer huh?

---

### Post by ronnoc on 2013-10-15
> **ryan36 said:**
> I'm on Ubuntu 13.04, I'm trying to connect my HTC One (m7att) to my laptop. The problem is, it won't register at all. If I've freshly restarted my phone, Ubuntu gives me an error about MTP not mounting with the usb device. adb (installed and configured correctly) never returns anything but a blank line when running adb devices. I've tried multiple tools/scripts found on xda (such as Android Forks and Knives) and I've tried creating/editing the xx-android.rules file at /etc/udev/rules.d/
Restarting udev doesn't work, killing the adb server and restarting it, as root or not, doesn't work. It's driving me crazy because I can't think of why else this wouln't be working. Last bit of information is if my phone hasn't been freshly rebooted, connecting it to the laptop's usb does nothing. No dialogue box popping up, no error about MTP, no sound confirmation. Phone doesn't even charge while it's connected. If anyone at all could help me with this I'd be deeply grateful..I'm trying to teach myself how to build android from source, and I've been good until now, the one thing getting in my way is the phone I'm trying to build for not connecting to my computer. bummer huh?

FWIW I'm running Kubutnu 13.10 Beta 2 with KIO-MTP 0.75 and I can not get MTP to work with my Android LG smart phone (Android 4.2). Similar issue however in my case, even when I can connect, it is only temporary since I will get an error about the process dying unexpectedly. Real drag since I need this to work for...well...work.

---

### Post by gigabz666 on 2013-11-05
I'm having issues with ADB on Ubuntu 13.10 as well. I'm unable to get either my Galaxy Nexus or my Asus Transformer Pad TF300 to show. I just keep getting blank under List of devices attached using adb devices or error: device not found with adb usb. I'm using the latest adb 1.0.31 and I too have messed around with the android rules file. Funnily enough, fastboot does work at bootloader which kind of rules out an issue with the usb port/cable. But no luck at all with adb during recovery, or while the phone is running and usb debugging enabled.

---

