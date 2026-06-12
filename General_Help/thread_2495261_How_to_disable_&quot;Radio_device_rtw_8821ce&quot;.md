---
title: "How to disable &quot;Radio device: rtw_8821ce&quot;"
date: 2024-02-13
forum: General Help
---

### Post by noko02 on 2024-02-13
Hello,
I use usb wifi adapter on my laptop with ubuntu 23.10, but "Radio device: rtw_8821ce" keeps turning on and drains my battery, I would like to completely disable it, since I dont need it and would like to reduce energy consumption and improve battery life. I tried to blacklist it in /etc/modprobe.d/blacklist.conf, bud it didnt help.
Thank you in advance for help!

---

### Post by MAFoElffen on 2024-02-13
How did you try to blacklist it? Show me the contents of the file...

---

### Post by noko02 on 2024-02-13
Thank you for your reply, this is the content of the file, I added the last three lines:

```
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp


# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

blacklist asus-nb-wmi

blacklist rtw_8821ce

blacklist r8169


```

---

### Post by MAFoElffen on 2024-02-14
Now, please post the output of these withi CODE Tags
```

lsmod | grep 'rtw_88\|rtx88'
grep . /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
find /etc/NetworkManager/system-connections/ -maxdepth 1 -type f -print0 | xargs -0 sudo grep . -1

```

---

### Post by noko02 on 2024-02-14
Thank you so much for your help, but I just decided to disable integrated wifi in BIOS. I would say its cleaner solution, since i dont need it anyway.

---

### Post by MAFoElffen on 2024-02-14
That works also.

FYI:
The reason for the other commands and to see what was loaded currently as kernel modules, is that there are a couple of different modules that that card uses, besides just rtw_8821ce.

The second command, because sometimes it hangs on until you turn off the power management to it.

The third, because sometimes the device will show up in some of the configs. 

If this has ended & solved, please use the "Thread Tools" link in the upper right of the page, and mark your thread as "Solved", so that others may find what worked for you.

---

### Post by noko02 on 2024-02-16
Okay, tysm once again!

---

