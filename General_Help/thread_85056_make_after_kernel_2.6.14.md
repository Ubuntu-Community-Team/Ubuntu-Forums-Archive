---
title: "make after kernel 2.6.14"
date: 2005-11-01
forum: General Help
---

### Post by eraclito on 2005-11-01
I complie 2.6.14 Vanilla Kernel like in this howto [http://www.ubuntuforums.org/showthread.php?t=84174](http://www.ubuntuforums.org/showthread.php?t=84174)

no problem and all works well.
But i have problems compliling other programs (like ieee80211-1.0.3 and ipw2200-1.0.6 to make my wireless card) 

but make does not work... 

i compile the same source with ubuntu kernel... any idea to fix the problem??

eraclito

---

### Post by odin on 2005-11-01
what version of gcc are you using? It's a long time ago I compiled that so my wireless worked but I can remember that it didnt work with version 4.0 and I had to use an old one dont remember if 2.95 or 3.3.

To compile with another version of gcc I had to installed it and edit the "makefile" of the "ieee802..." and the ipw2200 and change the gcc you want to use.

---

### Post by eraclito on 2005-11-01
[QUOTE=odin]what version of gcc are you using? It's a long time ago I compiled that so my wireless worked but I can remember that it didnt work with version 4.0 and I had to use an old one dont remember if 2.95 or 3.3.

To compile with another version of gcc I had to installed it and edit the "makefile" of the "ieee802..." and the ipw2200 and change the gcc you want to use.[/QUOTE]

i think that i used gcc 4.0 to compile kernel source, can i compile ieee802 source with another gcc? and how to chose gcc to comipe? (i had installed more than one...)

---

### Post by Kyral on 2005-11-01
You have to compile Kernel Modules with the GCC Version that the Kernel you are compiling for was compiled with

---

### Post by eraclito on 2005-11-01
[QUOTE=Kyral]You have to compile Kernel Modules with the GCC Version that the Kernel you are compiling for was compiled with[/QUOTE]

two questions?

1) how to know the gcc version used with the kernel?
2) how can i chose the gcc whersion to use?

thx

eraclito

---

### Post by Kyral on 2005-11-01
in a terminal

```
gcc -v
```

For the GCC version right now.

For the Kernel I think its

```
cat /proc/version
```

If you didn't install GCC-3.4 then chances are you used GCC4

---

### Post by eraclito on 2005-11-01
ok, i download the lastes ipw2200 and ieee802 and copile that with gcc4.0

now i can modprobe module ipw2200 without error, but no wireless card...

:confused:

---

### Post by Kyral on 2005-11-01
hmm, can I see the output from lsmod and iwconfig?

---

### Post by eraclito on 2005-11-01
[QUOTE=Kyral]hmm, can I see the output from lsmod and iwconfig?[/QUOTE]

here they are:

Module                  Size  Used by
af_packet              20360  2
ipv6                  219520  6
binfmt_misc            10888  1
i915                   17920  1
drm                    64788  2 i915
cpufreq_powersave       1920  0
cpufreq_stats           5124  0
cpufreq_performance     2176  0
cpufreq_ondemand        6300  0
cpufreq_conservative     7076  0
video                  16388  0
battery                 9732  0
container               4608  0
button                  6672  0
ac                      4996  0
asus_acpi              11540  0
irtty_sir               7936  0
sir_dev                17324  1 irtty_sir
irda                  162236  2 irtty_sir,sir_dev
crc_ccitt               2176  1 irda
pcspkr                  3680  0
rtc                    11448  0
ohci1394               30516  0
yenta_socket           24460  0
rsrc_nonstatic         12416  1 yenta_socket
pcmcia_core            38160  2 yenta_socket,rsrc_nonstatic
ipw2200               163904  0
ieee80211              42344  1 ipw2200
ieee80211_crypt         5764  1 ieee80211
firmware_class          9984  1 ipw2200
snd_intel8x0           30816  1
snd_ac97_codec         83580  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            46112  0
snd_mixer_oss          16896  1 snd_pcm_oss
snd_pcm                78600  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              21892  1 snd_pcm
snd                    49252  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10376  2 snd_intel8x0,snd_pcm
tpm_nsc                 6528  0
tpm_atmel               5760  0
tpm                     9760  2 tpm_nsc,tpm_atmel
shpchp                 80868  0
pci_hotplug            25268  1 shpchp
xfs                   451832  1
exportfs                5504  1 xfs
sr_mod                 15396  0
sbp2                   21252  0
scsi_mod              126440  2 sr_mod,sbp2
ieee1394               88248  2 ohci1394,sbp2
psmouse                33412  0
mousedev               10528  1
parport_pc             32324  1
lp                     10820  0
parport                32072  2 parport_pc,lp
ext3                  118024  1
jbd                    47892  1 ext3
thermal                13704  0
processor              23100  1 thermal
fan                     4868  0
8139too                24960  0
8139cp                 19200  0
mii                     5120  2 8139too,8139cp
ehci_hcd               29960  0
uhci_hcd               28176  0
usbcore               106496  3 ehci_hcd,uhci_hcd
ide_cd                 37124  0
cdrom                  33696  2 sr_mod,ide_cd
ide_disk               16128  4
ide_generic             1408  0 [permanent]
piix                    9220  0 [permanent]
generic                 4612  0 [permanent]
ide_core              112608  5 ide_cd,ide_disk,ide_generic,piix,generic
unix                   24624  674
vga16fb                11720  1
vgastate                8320  1 vga16fb
fbcon                  35328  72
font                    8320  1 fbcon
bitblit                 4992  1 fbcon

----------------
iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

(usually ipw card is eth1)

---

### Post by Kyral on 2005-11-01
Hmm. You shouldn't have to do this...but

```
sudo remmod ipw2200
```

Yes we are removing the module, but hold on a sec.

```
sudo depmod -a
```

```
sudo modprobe ipw2200
```

This might work...

---

### Post by eraclito on 2005-11-01
i cannot do 

```
sudo remmod ipw2200
```

remmod: command not found

so i do modprobe -r ipw2200

then depmod -a and modprobe ipw2200

but nothing changes...:(

---

### Post by Kyral on 2005-11-01
My apologies, its "rmmod"

---

### Post by Drifter on 2005-11-02
I did this using the guide, everything seemed to work just fine.  I built the kernel and then rebooted.  I checked to see what version the kernel was, it said that I was using 2.6.12-9-386.  Why did it not install the new one.

---

### Post by Kyral on 2005-11-02
Oy that guide (Its good, but I don't like touching patchset that don't come from either Ubuntu or Kernel.org)

Can I see the output from both 

```
ls /boot
``` 
and also your /boot/grub/menu.lst?

and I'll take a look after class

Anyway, checkout 
[https://wiki.ubuntu.com/KernelHowTo]("https://wiki.ubuntu.com/KernelHowTo")

---

### Post by eraclito on 2005-11-02
[QUOTE=Kyral]Oy that guide (Its good, but I don't like touching patchset that don't come from either Ubuntu or Kernel.org)

Can I see the output from both 

```
ls /boot
``` 
and also your /boot/grub/menu.lst?

and I'll take a look after class

Anyway, checkout 
[https://wiki.ubuntu.com/KernelHowTo]("https://wiki.ubuntu.com/KernelHowTo")[/QUOTE]

probably i understod, the ipw2200 source 1.08 need a new firmware, different from that i had installed. This nigh i'll try to download the new firmware and i hope it'll be good...

by

eraclito

---

### Post by eraclito on 2005-11-02
[QUOTE=eraclito]probably i understod, the ipw2200 source 1.08 need a new firmware, different from that i had installed. This nigh i'll try to download the new firmware and i hope it'll be good...

by

eraclito[/QUOTE]


yes it's work!
so with  2.6.14 kernel  you need the ipw2200-fw-2.4.tgz firmware and nothing more (ipw2200 modules is in)

by

eraclito

---

