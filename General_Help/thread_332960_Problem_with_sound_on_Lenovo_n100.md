---
title: "Problem with sound on Lenovo n100"
date: 2007-01-06
forum: General Help
---

### Post by ecimon on 2007-01-06
Hi,

I've installed kubuntu a few weeks ago on a Lenovo 3000 N100 laptop. Following this thread
[http://www.ubuntuforums.org/showthread.php?t=179685&highlight=lenovo](http://www.ubuntuforums.org/showthread.php?t=179685&highlight=lenovo)
I got sound working by adding **option snd-hda-intel model=laptop-eapd** to **/etc/modprobe.d/options**. Everything worked fine until recent upgrade of dbus and avahi-daemon.

My sound card is recognized (snd-hda-intel is loaded), amarok plays tracks without warnings, but the speakers stay mute (alsamixer/kmix settings are ok). I've tried restarting artsd/dbus with no luck. After that I checked /etc/modprobe.d/options and noticed that the &#8220;option&#8221; line for snd-hda-intel was missing. I put it back there and rebooted, but it didn't help.

Also putting garbage into /dev/audio has no effect.

Any help would be appreciated. :)

Here is the insteresting part of lspci -v :
```

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Lenovo Unknown device 2066
        Flags: bus master, fast devsel, latency 0, IRQ 233
        Memory at d0340000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Unknown type IRQ 0
        Capabilities: [100] Virtual Channel
        Capabilities: [130] Unknown (5)

```

Here is my lsmod:
```

ecimon@sigonmobile:/$ lsmod | grep snd
snd_hda_intel            20116  2
snd_hda_codec         164608  1 snd_hda_intel
snd_pcm_oss            47360  0
snd_mixer_oss          19584  1 snd_pcm_oss
snd_pcm                    84612  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer                  25348  1 snd_pcm
snd                             58372  10 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore                11232  1 snd
snd_page_alloc       11400  2 snd_hda_intel,snd_pcm

```

Here is /etc/modprobe.d/options
```

# Enable double-buffering so gstreamer et. al. work
options quickcam compatible=2

# Default hostap to managed mode
options hostap_pci iw_mode=2
options hostap_cs iw_mode=2

options snd-hda-intel model=laptop-eapd
#options snd-hda-intel model=3stack
#options snd-hda-intel model=laptop

```

Here is alsa-conf
```

ecimon@sigonmobile:/$ cat /etc/modprobe.d/alsa-base
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

```

And the uname
```

Linux sigonmobile 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686 GNU/Linux

```

---

### Post by Killerah on 2007-01-07
I'm having a similar problem with my Audigy 2 value. I was using it just fine and then something updated or something and it broke. Now it shows up in the sound mixer, and amarok plays songs without giving me errors, but my speakers stay mute. I'm interested to see the solution to this problem, but I can't really give any help as I don't know what I'm doing :).

---

