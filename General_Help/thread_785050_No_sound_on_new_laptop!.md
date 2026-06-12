---
title: "No sound on new laptop!"
date: 2008-05-07
forum: General Help
---

### Post by LasseNC on 2008-05-07
Hello there guys!

I just installed Ubuntu on my new Asus X53S Series laptop. But theres no sound.

I've tried googling the topic but nothing really came up.

Help is very appreciated! 

Kind regards, Lasse

---

### Post by ayoung on 2008-05-07
Which version of Ubuntu did you install?  I'm assuming Hardy (8.04), given the sound issues.

Install the 'linux-rt' package from Synaptic or the command-line, ```
sudo apt-get install linux-rt
``` and reboot.  That should clear things up, since the Linux generic driver released with Hardy has sound issues.

---

### Post by LasseNC on 2008-05-07
Installed 7.10 Gutsy as it was the only one I had on cd, but upgraded it right away.

Will try and install what you say there!

---

### Post by kpkeerthi on 2008-05-07
This might help 
[http://ubuntuforums.org/showthread.php?t=776739](http://ubuntuforums.org/showthread.php?t=776739)

---

### Post by wizzent on 2008-05-07
you could also try by checking this out:
[http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")

---

### Post by LasseNC on 2008-05-07
> **wizzent said:**
> you could also try by checking this out:
[http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")

Will definitely try this out when I get home!

---

### Post by LasseNC on 2008-05-07
When I got home and booted computer, it worked, didn't do anything!

---

### Post by darkblane on 2008-07-02
Hi LasseNC,

I have the same model laptop and cannot get sound, although all devices appear to be detected correctly. Could you post the following output from your shell so I can compare as yours in now working?

aplay -l
lspci
uname -r

Also, could you specify which devices are set in your "Sound Preferences" and which output your volume control is set for?

Many thanks, Karl.

---

### Post by LasseNC on 2008-07-02
I just installed all the codecs and rebooted.

---

### Post by darkblane on 2008-07-02
> **LasseNC said:**
> I just installed all the codecs and rebooted.

Hi LasseNC, the reason I ask is cause I have all codecs installed and sound is working in a system sense. Media players such as Rhythmbox show output on visualisations etc but I just get no output from the speakers or headphones.
I just wanted to compare the outputs of those commands to mine to see if our chipsets and hardware matched exactly, as well as the running kernel.
Also I just wanted to verify that the sound preferences matched too. I appreciate that yours just started working and that you can't definitively explain *how* it did but the information would greatly assist me in ruling out certain issues.
I could re-install and *hope* that I get lucky but I'd much rather know why the fault exists and how to resolve it definitively rather than just hoping that it just fixes itself by chance.

If you could try running the commands below and posting the output as well as the default sound preferences I'd really appreciate it :)

uname -r
```
darkblane@darkblane-laptop:~$ uname -r
2.6.24-19-generic
```

aplay -l
```
darkblane@darkblane-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

lspci
```
darkblane@darkblane-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 2400
02:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
04:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
09:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
09:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
09:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
09:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
```

---

### Post by LasseNC on 2008-07-02
Uninstalled Ubuntu ages ago for various reason, so I can't do that

---

### Post by LasseNC on 2009-01-10
Back with Kubuntu, same problem, tried installing the RT packages like last time, didn't help.

Aplay -l tells me that I have the hardware installed, but I can't get it to work.

---

### Post by linux_tech on 2009-01-10
Please post output of
```


lshw

and

at /proc/asound/card0/codec#* | grep Codec


```

---

### Post by LasseNC on 2009-01-10
```
*-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
```

```
lasse@lassenc:~$ at /proc/asound/card0/codec#* | grep Codec
syntax error. Last token seen: /
Garbled time
```

```
root@lassenc:/home/lasse# /proc/asound/card0/codec#* | grep Codec
bash: /proc/asound/card0/codec#0: Permission denied
```

I tried installing the gnome things, but I run Kubuntu?

```
root@lassenc:/home/lasse# gnome-alsamixer
No protocol specified

(gnome-alsamixer:7672): Gtk-WARNING **: cannot open display: :0.0
```

Installed gnome-media

```
root@lassenc:/home/lasse# gnome-volume-control
No protocol specified
cannot open display:
Run 'gnome-volume-control --help' to see a full list of available command line options.
```

---

### Post by linux_tech on 2009-01-10
> **LasseNC said:**
> 
```
lasse@lassenc:~$ at /proc/asound/card0/codec#* | grep Codec

```

not "at" but 
```
cat /proc/asound/card0/codec#* | grep Codec
```

Sorry I guess I did not read your post correctly but if you have kubuntu , then gnome utils will not work correctly.

---

### Post by LasseNC on 2009-01-10
```
lasse@lassenc:~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC660-VD
```

Installed all the ones you mention, nothing is muted via alsamixer, it's set to autodetect.

---

### Post by darkblane on 2009-01-10
> **LasseNC said:**
> Back with Kubuntu, same problem, tried installing the RT packages like last time, didn't help.

Aplay -l tells me that I have the hardware installed, but I can't get it to work.

You need to edit the file....
```
sudo gedit /etc/modprode.d/asla-base
```

Add the follwing text at the bottom;
```
options snd-hda-intel model=lenovo
```

Save and close gedit, reboot and you'll have sound (Asus F3SR/X53series)

Hope this helps

---

### Post by LasseNC on 2009-01-10
```
lasse@lassenc:~$ sudo kate /etc/modprobe.d/asla-base
Error: "/var/tmp/kdecache-lasse" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-lasse" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-lasse" is owned by uid 1000 instead of uid 0.
```

Still opened the document, which was empty, did the save, doesn't work.

---

### Post by darkblane on 2009-01-10
[QUOTE=darkblane;6528599]You need to edit the file....
```
sudo gedit /etc/modprode.d/asla-base
```

Just realised your using Kubuntu. Use Kate instead of gedit;
```
sudo kate /etc/modprode.d/asla-base
```

:guitar:

---

### Post by LasseNC on 2009-01-10
It DID work, after I rebooted, thanks!

---

### Post by linux_tech on 2009-01-10
In terminal type:
```
gksudo gedit /etc/modprobe.d/alsa-base 
```

Try changing or adding the following sentence: options snd-hda-intel model=3stack 
to this
```

options snd-hda-intel model=hp
```
save file, exit editor
Reboot and check if your sound if working. Do not forget to check your mixer to see if (new) channels are muted

refer to this post-
[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

---

### Post by darkblane on 2009-01-10
> **LasseNC said:**
> ```
lasse@lassenc:~$ sudo kate /etc/modprobe.d/asla-base
Error: "/var/tmp/kdecache-lasse" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-lasse" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-lasse" is owned by uid 1000 instead of uid 0.
```

Still opened the document, which was empty, did the save, doesn't work.


Ok, the file certainly shouldn't be empty. I suspect it opened it as empty due to the process uid issue. Quite an odd error.
Is this a clean install of Kubuntu? If not what alterations have you made?
Best advice I can give and I'd bet my house on this is that if you are running a clean install, standard Kernel, not RT, then the previously mentioned edit should give you sound. It's simply a matter of letting asla.base know what generic model laptop it is in order for it to know how to output correctly.
The error your getting suggests that a process is preventing you from opening this file correctly therefore it is appearing as a blank text file hence your changes had no effect.
You can try 2 things;
1. Boot into the LiveCD and view the alsa.base file, if empty thats your problem. You may need to reconfigure ASLA in order to rectify this. If it has all expected content smply append the previous code and you should be ok. Save & reboot.
2. Reinstall, clean, and make the edit your first action. Save & reboot. You should get sound.

Let me know how you get on :)

---

### Post by darkblane on 2009-01-10
> **LasseNC said:**
> It DID work, after I rebooted, thanks!

Cool :)

Please ignore my last post!

---

### Post by LasseNC on 2009-01-10
Please check my other topics, my xserver is banjaxed, can't load 8.10

---

