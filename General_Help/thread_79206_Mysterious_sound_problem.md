---
title: "Mysterious sound problem"
date: 2005-10-19
forum: General Help
---

### Post by WiLLiE on 2005-10-19
I just reinstalled Ubuntu a couple a days ago (5.10).
Everything worked smoothly as expected.

Today I thought about getting VLC to pump out the sound on my DVD's on the SPDIF.
I installed vlc-plugin-alsa, and it worked right away.
Then I noticed that totem didnt like any of my wma files, so I downloaded
[ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.0_i386.deb](ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.0_i386.deb)
and installed it.

Everything was working great. ...I thought.

Now I have absolutely no sound, except for DVD's in VLC.

I've scratched my head for a few hours now, and everything looks the same as before.

Motherboard: Asus a8v
CPU: amd64
Sound: onboard, Via chipset 8233
Ubuntu: 5.10,  i386 version

```
mikie@ubuntu:~$ lspci | grep -i audio
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
```

My /etc/asound.conf:  (device 3 = I use a toslink cable)
```
pcm.via82xx {
    type hw
    card 0
    device 3
}
ctl.via82xx {
    type hw
    card 0
}
```


```
mikie@ubuntu:~$ lsmod
Module                  Size  Used by
isofs                  32824  0
udf                    75524  0
binfmt_misc            10888  1
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
cpufreq_userspace       4444  0
cpufreq_stats           5124  0
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
video                  16004  0
tc1100_wmi              6916  0
sony_acpi               5516  0
pcc_acpi               11392  0
hotkey                  9508  0
dev_acpi               11396  0
i2c_acpi_ec             5760  0
button                  6672  0
battery                 9604  0
container               4608  0
ac                      4996  0
ipv6                  217408  546
floppy                 52692  0
pcspkr                  3652  0
rtc                    11832  0
snd_seq_dummy           3844  0
snd_seq_oss            29440  0
snd_seq_midi            8608  0
snd_seq_midi_event      6656  2 snd_seq_oss,snd_seq_midi
snd_seq                44688  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_via82xx            25792  2
gameport               14472  1 snd_via82xx
snd_ac97_codec         72188  1 snd_via82xx
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  2 snd_seq,snd_pcm
snd_page_alloc         10120  2 snd_via82xx,snd_pcm
snd_mpu401_uart         6784  1 snd_via82xx
snd_rawmidi            22816  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          8204  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd                    48644  15 snd_seq_oss,snd_seq,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9184  1 snd
ohci1394               30644  0
shpchp                 80612  0
pci_hotplug            24628  1 shpchp
amd64_agp              11464  1
dm_mod                 50364  1
tsdev                   7616  0
evdev                   9088  0
w83627hf               26792  0
eeprom                  7184  0
i2c_sensor              3456  2 w83627hf,eeprom
i2c_isa                 2176  0
i2c_viapro              7696  0
i2c_core               19728  6 i2c_acpi_ec,w83627hf,eeprom,i2c_sensor,i2c_isa,i2c_viapro
nvidia               3711364  20
agpgart                32328  2 amd64_agp,nvidia
sr_mod                 15652  0
sbp2                   21128  0
ieee1394               90936  2 ohci1394,sbp2
psmouse                26116  0
mousedev               10912  1
parport_pc             31812  1
lp                     11460  0
parport                32072  2 parport_pc,lp
md                     40656  0
ext3                  115976  2
jbd                    48536  1 ext3
thermal                13192  0
processor              23100  1 thermal
fan                     4740  0
sd_mod                 17424  5
ehci_hcd               29448  0
uhci_hcd               28048  0
usbcore               104188  3 ehci_hcd,uhci_hcd
sata_via                8836  6
skge                   33040  0
sata_promise           10756  0
libata                 47876  2 sata_via,sata_promise
scsi_mod              124872  5 sr_mod,sbp2,sd_mod,sata_promise,libata
ide_cd                 36996  1
cdrom                  33952  2 sr_mod,ide_cd
ide_generic             1664  0
via82cxxx              12188  1
ide_core              125268  3 ide_cd,ide_generic,via82cxxx
unix                   24624  718
vesafb                  8088  0
capability              5000  0
commoncap               6784  1 capability
vga16fb                12232  1
vgastate                8320  1 vga16fb
softcursor              2432  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3840  2 vesafb,vga16fb
cfbcopyarea             4480  2 vesafb,vga16fb
fbcon                  34176  72
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon
```

I only use digital sound thru my toslink cabel (to my 7.1-reciever), no analog sound.

Any ideas? (I really want to avoid to reinstall ubuntu again)

---

### Post by WiLLiE on 2005-10-20
Nothing to suggest? Reinstall Alsa? Manually download and compile/install Alsa?

---

### Post by poptones on 2005-10-20
Did you try removing the codecs? It seems sorta obvious although that may not fix it.

I do know some of the codecs in that pack suck. The wav pcm codec (for example) sucks and needs to be removed as it actually  makes mplayer and xine sound worse.

---

### Post by WiLLiE on 2005-10-22
Yeah, I did, but not at first though. That solution seemed really far fetched.
And that did'nt help neither.

I really hate these unexplainable unlogical problems.

Oh well, nothing to do but reinstall I suppose.
A few hours lost forever.


I would REALLY like to know what the damn problem is though.

---

