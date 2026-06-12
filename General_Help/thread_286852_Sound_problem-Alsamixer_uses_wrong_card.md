---
title: "Sound problem-Alsamixer uses wrong card"
date: 2006-10-28
forum: General Help
---

### Post by jenik on 2006-10-28
Hi,

I can't get sound to work in Edgy (didn't work in Dapper either). My default sound card in Preferences/Sound is CA0106 but the Alsamixer uses SAA7134. What do I need to do to make alsa use the correct card/driver?

Thanks

J

---

### Post by jenik on 2006-10-28
just noticed my /proc/asound/cards file is empty, what should it look like? also, i don't seem to be able to run alsaconf, it doesn't exist...

---

### Post by jocko on 2006-10-28
> **jenik said:**
> Hi,

I can't get sound to work in Edgy (didn't work in Dapper either). My default sound card in Preferences/Sound is CA0106 but the Alsamixer uses SAA7134. What do I need to do to make alsa use the correct card/driver?

Thanks

J

If you know which driver module the different cards use, you can either prevent one from being loaded by:
```
sudo gedit /etc/modprobe.d/blacklist
```
and add the following line anywhere:
```
blacklist name_of _module
```
Or you can set one as secondary by:
```
sudo gedit /etc/modprobe.d/alsa-base
```
And add the following line to the bottom:
```
options name_of_module index=-2
```

Using the first method, you will not be able to use the blacklisted card at all (unless you load the module manually by 'sudo modprobe name_of_module'). With the second method I *think* you will still be able to select the secondary card in different apps.

---

### Post by jenik on 2006-10-28
this is my /etc/modprobe.d/alsa-base

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --Qb snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2

---

### Post by jocko on 2006-10-28
> # Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2

Try adding these lines below the last line in alsa-base:
```
options saa7134 index=-2
options saa7134-alsa index=-2
```

---

### Post by jenik on 2006-10-28
hm, that didn't work. nothing happened but can't start alsamixer at all. also the Preferences/sound test sounds don't even start, give error:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing.

but that happens even with the original setting. think alsa does not know which card/driver to use but i have no idea how to tell it to use the SB with ca0106

---

### Post by Badcel on 2006-10-29
If cat /proc/asound/modules shows your sound modules in wrong order just switch it in the alsa base to your prefered order, e.g.:

install sound-slot-0 /sbin/modprobe snd-card-1
install sound-slot-1 /sbin/modprobe snd-card-0

---

### Post by jenik on 2006-10-29
i managed to swap them around in alsa-base and in /proc/asound/modules but nothing really changed, alsamixer still uses sa7134_alsa and sound tests in GNOME give the same error...looks like alsa just doesn't want to use the snd_ca0106... very frustrating](*,)

---

### Post by joegiampaoli on 2006-11-18
I have exactly this same problem...:confused: :confused: :confused:

---

### Post by thorsten.scherler on 2007-03-08
I have the same problem here and it just occured.

Before I had no problems, but after a restart I have now the exact same problem.

The default input card is a TV capture card CX8801, but it should be SiS SI7012.

I tried all the workarounds here and non of them work for me neither. 

I am using 2.6.17-11-generic.

Any information about how to fix this are very welcome.

salu2

---

### Post by joegiampaoli on 2007-03-08
I completely solved my issue with this guide

[http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")

I hope it works for you too....

---

### Post by thorsten.scherler on 2007-03-09
Thanks a million joegiampaoli for the link. 

It is fixed now. :)

What I was missing all along was 
```
aplay -l
```

This showed me that I need to follow the tip from Badcel better. I just switch some cards around but the main one was not the first I found out by looking at the outcome of above command (something like):

```
**** List of PLAYBACK Hardware Devices ****
card 2: SI7012 [SiS SI7012], device 2: Intel ICH [SiS SI7012]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Now doing what Badcel told us to do I added the card to the first slot by altering the first line in /etc/modprobe.d/alsa-base:
```
...
install sound-slot-0 /sbin/modprobe snd-card-2
...
install sound-slot-2 /sbin/modprobe snd-card-0
```

After a restart my sound is back and my SiS is the first device. :) I verified with
```

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SI7012 [SiS SI7012], device 0: Intel ICH [SiS SI7012]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Thanks to everyone on this thread and joegiampaoli for the last missing piece in the puzzle. You :guitar:  

salu2

---

### Post by joegiampaoli on 2007-03-09
No problem, I'm glad you have your audio working....

---

