---
title: "Access problems &amp; more"
date: 2007-12-18
forum: General Help
---

### Post by gomezc on 2007-12-18
Hello.  I am new to these threads but have been using Ubuntu for a little while and have overcome a number of problems on my own.  Unfortunately I have finally hit a brick wall.

It all began when I began fiddling with audio software.  I was trying to get my mic to work on 7.10 (Dell Inspiron E1405 Gutsy Gibbon) and I did, though it was glitchy.  Then yesterday I bridged my wireless network settings so that I could get wireless to work on my XP through VMware.  I shut down last night and this morning when I booted up, my sound card wouldn't work at all.  I tried googling for various solutions and found others with similar problems, none of their solutions worked.  Here's the bottom line:

No sound card was detected when I scanned using a terminal using lspci.  I did another scan (forgot which specific code I used) but the system reads my Intel HD card, which is good.  

To top the cake, I cannot access any sudo functions through terminal anymore.  Anything I do registers absolutely nothing.  I can type "sudo "anything" and nothing happens, I can't even access nautilus, it doesn't even prompt me for a password.  When I go to the menu "System->Administration->" the menu has become extremely limited to only 6 menu items.  Yesterday I had full access to all administrative items.  Someone please help...I would prefer my administrative privileges restored before I resolved the sound issue.  Thank you.

---

### Post by taurus on 2007-12-18
Did you change your groups when you tried to install mic or wireless thing?  What's the output of this command from a terminal?

```
id
```

---

### Post by gomezc on 2007-12-18
uid=1000(charlie) gid=1000(charlie) groups=29(audio),1000(charlie)

Nope, I haven't tried to change any groups, nor do I know how.  I was the only user on my laptop.

---

### Post by taurus on 2007-12-18
Boot into recovery mode from GRUB menu and at the prompt, run

```
adduser charlie adm,admin
shutdown -r now
```
Now, see if you can run sudo again.

---

### Post by gomezc on 2007-12-18
Wow, thanks a lot taurus, that has successfully launched me back into admin mode, you've been a great help so far (Ive been toiling at this for a frustrating 2 hours).

Thanks to going into recovery mode however, I noticed as one of the speeding lines went past, one of them mentioned "no sound cards found (fail [in red text])"

Any solutions for the found problem?

---

### Post by taurus on 2007-12-18
What kind of soundcard do you have?  See if there is any driver loading at boot?

```
lspci 
lsmod
```

---

### Post by gomezc on 2007-12-18
charlie@GOMEZ:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
02:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
02:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
02:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
02:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

lsmod

Module                  Size  Used by
i915                   25856  2 
drm                    83348  3 i915
vmnet                  44596  13 
vmblock                16288  3 
vmmon                 945260  0 
binfmt_misc            12936  1 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
ipv6                  273892  10 
acpi_cpufreq           10568  0 
af_packet              24840  2 
cpufreq_userspace       5280  0 
cpufreq_conservative     8072  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9612  2 
cpufreq_stats           7232  0 
freq_table              5792  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
video                  18060  0 
button                  8976  0 
battery                11012  0 
sbs                    19592  0 
container               5504  0 
dock                   10656  0 
ac                      6148  0 
arc4                    2944  2 
ecb                     4608  2 
blkcipher               7556  1 ecb
ieee80211_crypt_wep     6272  1 
sbp2                   24072  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
loop                   19076  0 
joydev                 11328  0 
snd_pcm_oss            44800  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                81028  1 snd_pcm_oss
snd_seq_dummy           4996  0 
snd_seq_oss            35328  0 
snd_seq_midi            9728  0 
snd_rawmidi            26112  1 snd_seq_midi
snd_seq_midi_event      8576  2 snd_seq_oss,snd_seq_midi
snd_seq                54256  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ipw3945               119840  1 
snd_timer              24452  2 snd_pcm,snd_seq
snd_seq_device          9740  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iTCO_wdt               11940  0 
iTCO_vendor_support     4868  1 iTCO_wdt
sdhci                  18828  0 
ieee80211              35656  1 ipw3945
ieee80211_crypt         7040  2 ieee80211_crypt_wep,ieee80211
serio_raw               8068  0 
snd                    56580  9 snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
mmc_core               28420  1 sdhci
pcspkr                  4224  0 
psmouse                39952  0 
snd_page_alloc         11272  1 snd_pcm
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
intel_agp              25620  1 
agpgart                35016  3 drm,intel_agp
evdev                  11136  5 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sr_mod                 17828  0 
cdrom                  37536  1 sr_mod
sd_mod                 30336  3 
ata_generic             8452  0 
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
b44                    28300  0 
mii                     6528  1 b44
ehci_hcd               36492  0 
ata_piix               17540  2 
libata                125168  2 ata_generic,ata_piix
scsi_mod              147084  5 sbp2,sg,sr_mod,sd_mod,libata
uhci_hcd               26640  0 
usbcore               138632  3 ehci_hcd,uhci_hcd
thermal                14344  0 
processor              32072  2 acpi_cpufreq,thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor

---

### Post by gomezc on 2007-12-18
I went ahead and reinstalled ALSA, recompiled the kernel and everything, as mentioned in another forum to try and fix the sound issue myself but it still tells me the same thing, that the sound card doesn't exist.  There is a hda-intel file so I'm puzzled why the sound continues to not work.  If anyone has further advice it would be much appreciated, thanks in advance.

---

### Post by gomezc on 2007-12-19
I solved the problem.  It all revolves around find out what your sound card's name is.  Mine was the Intel HD 82801G Audio Card for Inspiron E1405, found using lspci and looking under the audio card information.  Once I found that, googled my card type with the cooresponding OS (Ubuntu 7.10) and ALSA, I found this:

[http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/](http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/)

This was a very quick fix that only took 5 minutes to complete, now I can use sound again on Ubuntu and VMware Windows XP.  Today's efforts have not gone to waste.  I give thanks to the staff member who helped me in the beginning.  He gave me the information I needed to fix the problem on my own.

---

