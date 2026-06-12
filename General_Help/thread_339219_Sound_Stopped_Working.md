---
title: "Sound Stopped Working"
date: 2007-01-15
forum: General Help
---

### Post by OffHand on 2007-01-15
Hi All

My sound suddenly stopped working in Ubuntu and I could use some help because I do not have much experience troubleshooting sound issues. Sound works in XP so I know it's not a failing hardware problem.

Any help welcome.

---

### Post by smartbei on 2007-01-15
Try this:
In a terminal type:
```
alsamixer
```
And see if one of the bars that shows up is empty (not red green and white) if it is, use the left or right arrow keys to get to it, and the up key to raise the volume until the bar is full and it shows '100' below it.

Hope that helps.

---

### Post by OffHand on 2007-01-15
Thanks but I already checked that. The settings seem fine.

Some more technical info:

$ cat /proc/asound/cards
 0 [ICH            ]: NFORCE - Intel ICH
                      Intel ICH with ALC850 at 0xfebbc000, irq 58
 1 [U0x4710x310    ]: USB-Audio - USB Device 0x471:0x310
                      USB Device 0x471:0x310 at usb-0000:00:0b.0-4, full speed


cat /etc/modprobe.d/alsa-base
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

### Post by RikoW on 2007-01-15
I had a similar problem just now. Turns out esd, which allows several applications to access the sound device, was not starting anymore. I just reinstalled everything that looks like "esd" and, voila, it works again.

you can check, if you have a line reading something like:

```
/usr/bin/esd -terminate -nobeeps -as 1 -spawnfd 18

```

if you execute 

```
ps ax
```

on the command line.

if yes, forget my suggestion above :)

Cheers,

                 Riko

---

### Post by jordilin on 2007-01-15
sometimes, when you launch a kde app when using gnome, sound is taken over by the kde daemon sound which is arts. It interferes with gnome and can cause lack of sound. One solution is killing arts or just reboot the machine. I don't know if this is your problem, but just in case.

---

### Post by OffHand on 2007-01-15
> **jordilin said:**
> sometimes, when you launch a kde app when using gnome, sound is taken over by the kde daemon sound which is arts. It interferes with gnome and can cause lack of sound. One solution is killing arts or just reboot the machine. I don't know if this is your problem, but just in case.

That's not the case here.

---

### Post by OffHand on 2007-01-15
> **RikoW said:**
> I had a similar problem just now. Turns out esd, which allows several applications to access the sound device, was not starting anymore. I just reinstalled everything that looks like "esd" and, voila, it works again.

you can check, if you have a line reading something like:

```
/usr/bin/esd -terminate -nobeeps -as 1 -spawnfd 18

```

if you execute 

```
ps ax
```

on the command line.

if yes, forget my suggestion above :)

Cheers,

                 Riko

Could you be a bit more precise? How did you do this?

> I just reinstalled everything that looks like "esd" and, voila, it works again.

---

### Post by jordilin on 2007-01-15
I know this is the typical answer when dealing with ms windows, but sometimes rebooting solves these kinds of problems. If you have already rebooted, then take a look at /var/log/messages when trying to play some file. Do it always from the command line.

---

### Post by OffHand on 2007-01-15
A screenshot of my alsamixer. Looks fine to me...

---

### Post by RikoW on 2007-01-15
I just started synaptic and did a search on "esd". Everything that came up and was marked installed, I then marked for re-installation, did the same after searching  for "esound". After you marked these things for re-installation just hit the "apply" button.

After synaptic is done, you probably have to restart esd either by rebooting or by going to:

System -> Preferences p -> Sound and un-check and check the esd box.

Good luck,

                   Riko

---

### Post by OffHand on 2007-01-15
> **jordilin said:**
> I know this is the typical answer when dealing with ms windows, but sometimes rebooting solves these kinds of problems. If you have already rebooted, then take a look at /var/log/messages when trying to play some file. Do it always from the command line.

I thought I restarted already but decided to give it another try. Sound suddenly started working again  :S  :-k   :rolleyes:   :D 

Thanks for the help guys!

---

### Post by nrwilk on 2007-01-27
Thanks, this helped me as well.  My sound had just suddenly stopped working.  At first it was hit-or-miss, but then I never worked for a few bootups in a row.

Anyway, for those of you who would like to do this fix without using a bulky, slow UI, you can just issue this command to reinstall all currently installed packages with the letters "esd" in them:
```
sudo aptitude reinstall ~nesd
```

It will not install any packages that weren't already installed.

:) 

nrwilk

---

### Post by Goober on 2007-01-27
Just a note, I had this problem, and I restarted.  Worked fine.  I also apparently have 2 places to plug in my speakers, one at the bottom, and one near the top (Green Plug for me).  I found that the one at the bottom worked intermittedly, but the one at the top is working more regularly.  By that I mean when the speakers were plugged in at the bottom, the sound didn't always work upon startup.  At the top, the sound has worked flawlesly.

Probably just the nuances of my ancient computer.

---

### Post by getaboat on 2007-01-27
Occasionally real does'nt make any noise and a re-boot generally clears - one day I will work out what is going on - today a firefox update muddied the waters a bit.

---

