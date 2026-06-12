---
title: "Always rapid-fire USB gamepad"
date: 2007-06-29
forum: General Help
---

### Post by Clerical Apathy on 2007-06-29
I own a Gamemon Universal USB Converter  [ Located Here]("http://www.chinagameware.com/display/ft8d91_ps2_xbox_gc_to_pc-usb_converter.shtml")

I'm trying to use it with the a PS2 Dual Shock controller.

Under dmesg it comes up as USB HID v1.10 Joystick [HID 19fa:8d91] under both /js0 and /js1, with only /js0 allowing input (Testing with jstest, jscalibrator, and kcontroller)

It accepts input fine from the standard D-Pad, but with all the other inputs, it's on a persistent auto-fire.

I've searched both google and the forums and to no avail can I find a solution.

I'm running on a DELL Inspiron 9300 Laptop, fairly new to Ubuntu, though it's growing fast on me.

Here's my lsmod

Module                  Size  Used by
xpad                    9988  0 
analog                 12832  0 
gameport               16520  1 analog
arc4                    2944  2 
ecb                     4480  2 
blkcipher               6784  1 ecb
ieee80211_crypt_wep     6144  1 
ipv6                  268960  8 
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25856  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0 
speedstep_centrino      9920  0 
cpufreq_userspace       5408  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9228  1 
cpufreq_stats           7360  0 
freq_table              5792  3 speedstep_centrino,cpufreq_ondemand,cpufreq_stats
cpufreq_conservative     8200  0 
dev_acpi               12292  0 
tc1100_wmi              8068  0 
sony_acpi               6284  0 
pcc_acpi               13184  0 
container               5248  0 
button                  8720  0 
sbs                    15652  0 
dock                   10268  0 
video                  16388  0 
asus_acpi              17308  0 
backlight               7040  1 asus_acpi
battery                10756  0 
i2c_ec                  6016  1 sbs
ac                      6020  0 
nls_utf8                3072  3 
ntfs                  107764  3 
sbp2                   23812  0 
parport_pc             36388  0 
lp                     12452  0 
parport                36936  3 ppdev,parport_pc,lp
fuse                   46612  0 
snd_intel8x0           34332  3 
snd_ac97_codec         98464  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
joydev                 10816  0 
pcmcia                 39212  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
nvidia               4713780  50 
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  3 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ipw2200               148040  0 
pcspkr                  4224  0 
i2c_core               22656  2 i2c_ec,nvidia
usbhid                 26592  0 
hid                    27392  1 usbhid
serio_raw               7940  0 
yenta_socket           27532  1 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40852  3 pcmcia,yenta_socket,rsrc_nonstatic
sdhci                  18700  0 
ieee80211              34760  1 ipw2200
snd                    54020  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_intel8x0,snd_pcm
psmouse                38920  0 
mmc_core               26756  1 sdhci
ieee80211_crypt         7040  2 ieee80211_crypt_wep,ieee80211
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
iTCO_wdt               11812  0 
iTCO_vendor_support     4868  1 iTCO_wdt
intel_agp              25244  1 
agpgart                35400  2 nvidia,intel_agp
af_packet              23816  8 
evdev                  11008  6 
tsdev                   8768  0 
usb_storage            72256  2 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
libusual               17936  1 usb_storage
sg                     36252  0 
sd_mod                 23428  8 
sr_mod                 17060  1 
cdrom                  37664  1 sr_mod
generic                 5124  0 [permanent]
ata_piix               15492  4 
ata_generic             9092  0 
ahci                   22020  0 
libata                125720  3 ata_piix,ata_generic,ahci
scsi_mod              142348  6 sbp2,usb_storage,sg,sd_mod,sr_mod,libata
ohci1394               36528  0 
ieee1394              299448  2 sbp2,ohci1394
b44                    28044  0 
mii                     6528  1 b44
ehci_hcd               34188  0 
uhci_hcd               25360  0 
usbcore               134280  7 xpad,usbhid,usb_storage,libusual,ehci_hcd,uhci_hcd
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

Been trying to find a Radio Shack converter, but it's been a no show in 5 stores now, so my options are limited.

Any help would be appreciated.

---

### Post by El Flavio on 2007-07-02
I'm having a similar problem with my USB gamepad (I am using a NES to PC adapter to use my NES controller). I don't understand why it is doing this. I'm starting to think maybe it is USB controller adapters (I am basing this on similar problems i have read in the fourms).

---

### Post by StateS on 2007-07-04
I am having the same problem as well, my gamepad is a Trust GM-1500 a.k.a. Predator, it connects to the PC via USB but it can also connect to the PS2, it has a turbo and macro function. When I plug the controller into the PC nothing special happens, but when I start a program that uses the controller the Turbo button light turns on right away. I go to configure the keys and I have no problems whatsoever, but when I try to enter a game and try to play it goes bonkers, in an RPG that I tried to play the message screens just flew by... It's then that I noticed that I could not move, the D-Pad doesn't work when this happens. I tried ZSNES with the controller, configured the keys and when I tried to use the gamepad as the standard input for the program I could not move the cursor with the gamepad.

---

