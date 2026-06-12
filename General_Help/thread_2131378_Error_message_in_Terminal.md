---
title: "Error message in Terminal"
date: 2013-04-01
forum: General Help
---

### Post by SLarson07 on 2013-04-01
I am trying to get my wireless working, but when I put in commands to get it working I get error messages.

```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
``` 

```
sudo apt-get install linux-firmware-nonfree
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

      ```
sudo modprobe b43
WARNING: /etc/modprobe.d/blacklist.conf line 56: ignoring bad line starting with 'Ic3man07'
WARNING: /etc/modprobe.d/blacklist.conf line 57: ignoring bad line starting with 'sudo'
```

I thought maybe the software center or another terminal was causing a conflict so I rebooted then tried again. Unfortunately I am getting the same messages.

---

### Post by Impavidus on 2013-04-01
It seems that the lock hasn't been properly released. See [http://askubuntu.com/questions/15433/how-do-i-fix-a-could-not-get-lock-var-lib-dpkg-lock-problem](http://askubuntu.com/questions/15433/how-do-i-fix-a-could-not-get-lock-var-lib-dpkg-lock-problem) for a complete discussion of this problem.

---

### Post by SLarson07 on 2013-04-01
I am new to ubuntu, so I am not always sure what I am looking at. The first and second commands work now, but I am still getting the third error message. Any ideas?

---

### Post by cortman on 2013-04-01
Have you edited the file /etc/modprobe.d/blacklist.conf at all?
Please post the output of

```
cat /etc/modprobe.d/blacklist.conf
```

Just FYI the first two and the third problems are not connected in any way.

---

### Post by SLarson07 on 2013-04-01
Yeah, I thought it might not be, it just happened to be part of what I was doing at the time. I figured that I didn't want to leave anything out. I did edit the blacklist. I was following instructions on another thread about getting my wireless to work.

Per your request:
     ```
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
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

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

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
Ic3man07
sudo tee -a /etc/modprobe.d/blacklist.conf


```

---

### Post by cortman on 2013-04-01
I'm not sure what you were trying to accomplish by editing it, but the file is messed up- open it and remove the lines

```
[COLOR=#000000][FONT=Ubuntu Mono]Ic3man07
sudo tee -a /etc/modprobe.d/blacklist.conf
[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono]
[FONT=verdana]
Then try the modprobe command.[/FONT][/FONT][/COLOR]

---

