---
title: "No sound at all with Intel ICH5"
date: 2007-09-03
forum: General Help
---

### Post by Foged on 2007-09-03
I'm in desperat need of some help. I'm new to Ubunto (I'm using v. 7.04) and I've been trying to solve my problem for a few days now. I don't have any sound at all, not eaven at startup
I'm using an Intel onboard soundcard ( 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller)

I HAVE: 
Enabled it in BIOS
Set it as default (gksudo asoundconf list > gksudo asoundconf set-default-card ICH5)
Turned up the volume, and made sure that it's not muted
Installed the latest version of ALSA

Any help would be much appreciated  :)
(I also have the SB X-FI Platinum, but from what I've read, it's not supported)

---

### Post by mustali on 2007-09-03
You should try compiling and installing the ALSA drivers. Follow the instructions in this thread.
[http://ubuntuforums.org/showthread.php?t=540296](http://ubuntuforums.org/showthread.php?t=540296)

HTH

---

### Post by Foged on 2007-09-03
I'll give it a try, and post the result :)

---

### Post by Foged on 2007-09-03
Okay... I've downloaded and extracted the driver, lib and utils.
Now I'm not sure what to do, cause I'm VERY NEW at this. Please spell it out to me


(I have just run this comand > /home/foged/Desktop/alsa-lib-1.0.14a/configure)

---

### Post by mustali on 2007-09-03
Get the file
```

wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2
tar xvf alsa-driver-1.0.14.tar.bz2

```

change to the extracted directory
```

cd alsa-driver-1.0.14

```

prepare for compile
```

./configure --with-oss=yes --with-cards=hda-intel

```

compile
```

sudo make

```

install
```

sudo make install

```

Add module to the kernel
```

sudo modprobe snd-hda-intel

```

Restart sound
```

sudo /etc/init.d/alsasound restart
```

Log out and log back in to get the panel speaker icon to start working.

The speakers are muted by default.

HTH

---

### Post by Foged on 2007-09-03
Okay, there is only one thing that didn't run smoothly:
foged@foged-pc:~$ sudo /etc/init.d/alsasound restart
sudo: /etc/init.d/alsasound: command not found

foged@foged-pc:~$ /etc/init.d/
acpid                            mountall.sh
acpi-support                     mountdevsubfs.sh
alsa-utils                       mountkernfs.sh
anacron                          mountnfs-bootclean.sh
apmd                             mtab.sh
apport                           networking
atd                              nvidia-kernel
avahi-daemon                     pcmciautils
binfmt-support                   powernowd
bluetooth                        powernowd.early
bootclean                        pppd-dns
bootlogd                         procps.sh
bootmisc.sh                      rc
brltty                           rc.local
checkfs.sh                       rcS
checkroot.sh                     readahead
console-screen.sh                readahead-desktop
console-setup                    reboot
cron                             rmnologin
cupsys                           rsync
dbus                             screen

---

### Post by mustali on 2007-09-03
hmm. you probably don't have alsa package installed. try this

```

sudo apt-get install alsa alsa-utils

```

---

### Post by Foged on 2007-09-03
I'm sorry but that didn't do it, because I already have the latest version

Any other suggestions?

---

### Post by mustali on 2007-09-03
See if a reboot fixes the sound.

what does 'aplay -l' give you? This command displays information about the detected soundcards.

can you also post the output of
lsmod | grep snd

---

### Post by Foged on 2007-09-03
Now I have some kind of sound. I's quite low and with a lot of static noice

```
foged@foged-pc:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```
foged@foged-pc:~$ lsmod
Module                  Size  Used by
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25856  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0 
speedstep_lib           6148  0 
cpufreq_ondemand        9228  0 
cpufreq_stats           7360  0 
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
cpufreq_conservative     8200  0 
cpufreq_userspace       5408  0 
cpufreq_powersave       2688  0 
sony_acpi               6284  0 
pcc_acpi               13184  0 
tc1100_wmi              8068  0 
dev_acpi               12292  0 
asus_acpi              17308  0 
video                  16388  0 
ac                      6020  0 
dock                   10268  0 
sbs                    15652  0 
i2c_ec                  6016  1 sbs
button                  8720  0 
backlight               7040  1 asus_acpi
container               5248  0 
battery                10756  0 
nls_iso8859_1           5120  1 
nls_cp437               6784  1 
vfat                   14208  1 
fat                    53916  1 vfat
nls_utf8                3072  1 
ntfs                  107764  1 
ipv6                  268960  10 
lp                     12452  0 
fuse                   46612  0 
snd_intel8x0           34332  1 
snd_ac97_codec         98464  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
nvidia               4713780  32 
snd                    54020  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_rng               6528  0 
soundcore               8672  1 snd
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc
psmouse                38920  0 
iTCO_wdt               11812  0 
iTCO_vendor_support     4868  1 iTCO_wdt
snd_page_alloc         10888  2 snd_intel8x0,snd_pcm
i2c_core               22656  2 i2c_ec,nvidia
serio_raw               7940  0 
pcspkr                  4224  0 
intel_agp              26140  1 
agpgart                35400  2 nvidia,intel_agp
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
af_packet              23816  2 
tsdev                   8768  0 
evdev                  11008  3 
ext3                  133128  3 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
sr_mod                 17060  0 
cdrom                  37664  1 sr_mod
sd_mod                 23428  8 
ata_generic             9092  0 
ata_piix               15492  6 
libata                125720  2 ata_generic,ata_piix
scsi_mod              142348  4 sg,sr_mod,sd_mod,libata
e100                   36232  0 
mii                     6528  1 e100
ehci_hcd               34188  0 
floppy                 59524  0 
generic                 5124  0 [permanent]
uhci_hcd               25360  0 
usbcore               134280  3 ehci_hcd,uhci_hcd
thermal                14856  0 
processor              31048  1 thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability

```

```
foged@foged-pc:~$ grep snd


```
When I use this comand, nothing (visible) happens

---

### Post by Foged on 2007-09-03
I'm leaving for school in 6 hours, so I'd better get som some sleep. I'm looking forward to readig the replies (if any) whet I get home. When this problem is solved, I kan finally delete XP! 
Until then; thanks for all your help- it's much appreciated :)

Foged

---

### Post by mustali on 2007-09-03
the command i was referring to was ```
lsmod | grep snd
``` lsmod piped to the grep command.

if the sound working correctly in XP, I am not sure what is going on. Perhaps it is picking up the static from the mic input? I can only suggest checking the sound settings again.

nice to know you are getting close. I hope someone else can pick it up from here.

---

### Post by Foged on 2007-09-04
Arh okay, well this is what I get:

```
foged@foged-pc:~$ lsmod | grep snd
snd_intel8x0           34332  1 
snd_ac97_codec         98464  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_intel8x0,snd_pcm

```

The sound in XP is working fine! When i use the scroll button or any button on the keyboard, there comes a static "tic" sound. There is a constant static noise, that sounds almost as when cellphone is near the speaker?!

---

### Post by mustali on 2007-09-04
I am at my wit's end here.

You may want to check out some other threads related to poor sound.

[Bad sound? Try this...]("http://ubuntuforums.org/showthread.php?t=476146")

Official ubuntu sound [guide]("http://ubuntuforums.org/showthread.php?t=205449")

[nvidia driver makes ticking noise in my computer!]("http://ubuntuforums.org/showthread.php?t=184873")

---

### Post by Foged on 2007-09-04
Alright thanks. I'll give it a go, and post the result

---

### Post by Foged on 2007-09-04
After doing this:
[http://ubuntuforums.org/showthread.php?t=476146]](http://ubuntuforums.org/showthread.php?t=476146])

I get this message:
After doing this I get this message

"Please check that:
your soundcard is configured properly
you have the correct output selected
no other program is blocking the soundcard"

This message didn't show up before

---

