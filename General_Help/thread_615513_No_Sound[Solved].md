---
title: "No Sound[Solved]"
date: 2007-11-17
forum: General Help
---

### Post by Sef on 2007-11-17
I just built my computer and I have no sound.  I get this message when I click on the sound icon on the top bar:  > No volume control GStreamer plugins and/or devices found..   Since Gstreamer was installed, and I have installed the GStreamer plugins, it seems that my onboard sound cannot be found.   How can I find it?

When I do cat /proc/asound/cards, I get this message file or directory.   

Update: When checking out the [specs]("http://www.ciao.co.uk/ASUS_P5VD2_X__6574888"), I found this:

> Audio

Audio Output: Sound card

Audio Codec: Realtek ALC883

Sound Output Mode: 5.1 channel surround

Computer Specs:  

Motherboard: ASUS P5VD2-X

CPU: Intel Core 2 Duo E4500 (2.2G/FSB800/2MB)

Ram: Samsung 2 GB 240pin DDR2 SDRAM (PC6400) 

Power Supply: SolarMax 425 Watts

DVD-RW: DVD LG Super Multi

Case: G-Made 7-J

---

### Post by geirha on 2007-11-17
that chipset seem to be problematic. There's an open bug report which seems to be closely related to your issue. [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/39770](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/39770)

---

### Post by Sef on 2007-11-17
> hat chipset seem to be problematic. There's an open bug report which seems to be closely related to your issue. [https://bugs.launchpad.net/ubuntu/+s...ver/+bug/39770](https://bugs.launchpad.net/ubuntu/+s...ver/+bug/39770)

I found this post of 1007-11-12:

> This may be because I had the -386 kernel installed due to nvidia-glx-new drivers. After manually installing the "linux-ubuntu-modules-2.6.22-14-386" package, I had the necessary driver (snd-hda-intel.ko - /lib/modules/2.6.22-14-386/ubuntu/media/snd-hda-intel/snd-hda-intel.ko) and I could modprobe it and have a sound device.

How do I do that?  

My kernel is 2.6.22-14-386.

---

### Post by geirha on 2007-11-17
```
sudo aptitude install linux-ubuntu-modules-2.6.22-14-386
```

---

### Post by Sef on 2007-11-17
I got this message upon installing:  > dpkg: error processing ttf-opensymbol (--configure):
 subprocess post-installation script returned error exit status 22
Errors were encountered while processing:
 ttf-opensymbol


---

### Post by Sef on 2007-11-17
geirha: Thank you very, very much.  I got sound now after following your instructions.

---

### Post by PriceChild on 2007-11-17
Why are you using -386 anyway?

Get -generic!!! :)

---

### Post by Perfect Storm on 2007-11-17
Get a decent audio-card instead, Sef :mrgreen:

---

### Post by Sef on 2007-11-17
> Get a decent audio-card instead, Sef 

I will.  Just need to get some money together.   

> Why are you using -386 anyway?

That is what it defaulted to upon install.

---

### Post by PriceChild on 2007-11-18
> **Sef said:**
> That is what it defaulted to upon install.Well then get rid of it and install generic :)

---

### Post by Sef on 2007-11-19
> Well then get rid of it and install generic

1) How would I do that?

2) What are the advantages of using generic?

---

### Post by PriceChild on 2007-11-19
The way I understand it... -generic is the default kernel. Its what gets installed by default.

-386 is still around to give compatibility to older hardware and has some of the "better/newer" things turned off.

The only reason you've got -386 installed is because you weren't watching aptitude or apt properly when it told you it was about to swap -generic with -386 :P

and if you have -generic, you shouldn't have problems as stated in this thread.

To get -generic... sudo apt-get install linux-generic and then get rid of whatever -386 stuff you have (once you are sure that -generic is working)

---

### Post by Sef on 2007-11-19
> To get -generic... sudo apt-get install linux-generic and then get rid of whatever -386 stuff you have (once you are sure that -generic is working)

Says it is already the latest kernel.   Have to check GRUB when I reboot.

---

### Post by PriceChild on 2007-11-19
I guess you've got both installed then :)

---

### Post by Sef on 2007-11-19
They are both installed.  How do I change the default to generic from 386?

---

### Post by PriceChild on 2007-11-21
Just remove the 386 ones (search for linux*386 or something) if -generic works fine.

---

### Post by Sef on 2007-11-22
I just went into the GRUB menu and commented out all the 386 lines.  Rebooted and it worked: booted into generic.   Thank you for your help.

---

### Post by PriceChild on 2007-11-22
You really shouldn't edit the automatically generated parts of grub.conf... it even gives warnings :P

I suggest you put everything back, and then apt-get remove the -386 kernels.

---

### Post by Sef on 2007-11-22
It didn't give any warning.   

To remove by apt-get, I should do it this way:

```
sudo apt-get remove linux-i386
```?

---

### Post by PriceChild on 2007-11-22
> **Sef said:**
> It didn't give any warning.   My mistake, confused with something else.
[quote=Sef;3820392 To remove by apt-get, I should do it this way:

```
sudo apt-get remove linux-i386
```?[/quote]And also the packages like linux-image-<version>-386

---

