---
title: "Weird Sound Problem"
date: 2004-10-25
forum: General Help
---

### Post by Tux234 on 2004-10-25
When I boot, I get the drum sound when GDM starts up but I get no login sound, or any sound events while as a user. I get no sound from games (Armegetron, Pingus, etc.), or XMMS but I get sound from rhythm box and totem. Help please! Thx in advance. BTW could it be Gnome trumping the other apps?

---

### Post by FLeiXiuS on 2004-10-25
Try disabling GDM sound events, then post again.

---

### Post by Tux234 on 2004-10-25
nope didn't work. I'm usin ALSA BTW

---

### Post by FLeiXiuS on 2004-10-25
Perhaps paste feedback from, 

lspci
lsmod

---

### Post by Tux234 on 2004-10-25
lspci
0000:00:00.0 Host bridge: Intel Corp. 82810 GMCH [Graphics Memory Controller Hub] (rev 03)
0000:00:01.0 VGA compatible controller: Intel Corp. 82810 CGC [Chipset Graphics Controller] (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801AA PCI Bridge (rev 02)
0000:00:1f.0 ISA bridge: Intel Corp. 82801AA ISA Bridge (LPC) (rev 02)
0000:00:1f.1 IDE interface: Intel Corp. 82801AA IDE (rev 02)
0000:00:1f.2 USB Controller: Intel Corp. 82801AA USB (rev 02)
0000:00:1f.3 SMBus: Intel Corp. 82801AA SMBus (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801AA AC'97 Audio (rev 02)
0000:01:0b.0 VGA compatible controller: nVidia Corporation NV11DDR [GeForce2 MX 100 DDR/200 DDR] (rev b2)
0000:01:0d.0 Ethernet controller: Accton Technology Corporation SMC2-1211TX (rev 10)
0000:01:0e.0 Modem: PCTel Inc HSP MicroModem 56 (rev 02)

 lsmod
Module                  Size  Used by
proc_intf               3776  0
freq_table              4196  0
cpufreq_userspace       5240  0
cpufreq_powersave       1728  0
ds                     18436  0
yenta_socket           20992  0
pcmcia_core            68404  2 ds,yenta_socket
button                  6584  0
ac                      4812  0
battery                 9388  0
ipv6                  256996  8
af_packet              22088  2
8139too                25568  0
mii                     5056  1 8139too
crc32                   4288  1 8139too
snd_intel8x0           35468  2
snd_ac97_codec         67844  1 snd_intel8x0
snd_pcm                95140  1 snd_intel8x0
snd_timer              24900  1 snd_pcm
snd_page_alloc         11432  2 snd_intel8x0,snd_pcm
gameport                4608  1 snd_intel8x0
snd_mpu401_uart         7776  1 snd_intel8x0
snd_rawmidi            24704  1 snd_mpu401_uart
snd_seq_device          8040  1 snd_rawmidi
snd                    55300  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore              10112  1 snd
joydev                  9728  0
usbhid                 31392  0
uhci_hcd               31952  0
usbcore               115684  4 usbhid,uhci_hcd
shpchp                 99340  0
pciehp                 96108  0
pci_hotplug            33680  2 shpchp,pciehp
hw_random               5364  0
intel_agp              22112  1
agpgart                33640  1 intel_agp
parport_pc             34752  1
nls_cp437               5696  1
ntfs                  100276  1
md                     48552  0
dm_mod                 57308  1
capability              4520  0
commoncap               7072  1 capability
nvidia               4821300  12
lp                     10724  0
parport                40712  2 parport_pc,lp
tsdev                   7232  0
evdev                   9440  0
ide_cd                 41572  0
cdrom                  39392  1 ide_cd
mousedev               10220  2
psmouse                19720  0
ext3                  123880  1
jbd                    60824  1 ext3
mbcache                 9092  1 ext3
ide_generic             1408  0
piix                   13088  1
ide_disk               18752  4
ide_core              136120  4 ide_cd,ide_generic,piix,ide_disk
unix                   28080  696
fan                     3980  0
thermal                12976  0
processor              17392  1 thermal
font                    8352  0
vesafb                  6560  0
cfbcopyarea             3712  1 vesafb
cfbimgblt               3072  1 vesafb
cfbfillrect             3616  1 vesafb

---

### Post by Tux234 on 2004-10-25
now I'm not getting any sound at all!
nm: It was on mute hehe :Embarrassed:
Still no sound from games though :(

---

### Post by FLeiXiuS on 2004-10-25
[QUOTE=Tux234]now I'm not getting any sound at all!
nm: It was on mute hehe :Embarrassed:
Still no sound from games though :([/QUOTE]

Seeing how the small problems are over looked, check if the games have audio settings, some do, some don't.  I will look at your modules in a second!

Alright, I didn't see anything wrong there.  

So your SOUND is working though correct?

---

### Post by Tux234 on 2004-10-26
[QUOTE=FLeiXiuS]Seeing how the small problems are over looked, check if the games have audio settings, some do, some don't.  I will look at your modules in a second!

Alright, I didn't see anything wrong there.  

So your SOUND is working though correct?[/QUOTE]
 Yes My sound is still working. I'm pretty sure that armagetron and tuxracer comes with sounds already. Also besides the drums with GDM I get no other sound events even though they are activated. 
PS: sorry it took me so long to reply.

---

### Post by Tux234 on 2004-11-02
Bump

---

### Post by mercurus on 2004-11-02
[QUOTE=Tux234]Bump[/QUOTE]
 Is the ubuntu-sounds package installed ?

---

### Post by Tux234 on 2004-11-03
[QUOTE=mercurus]Is the ubuntu-sounds package installed ?[/QUOTE]
 Yes

---

### Post by Tux234 on 2004-11-04
Bump

---

