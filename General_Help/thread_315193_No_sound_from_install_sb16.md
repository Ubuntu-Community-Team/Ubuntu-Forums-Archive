---
title: "No sound from install sb16"
date: 2006-12-08
forum: General Help
---

### Post by jeeptime1 on 2006-12-08
I am trying to configure my sound card.  I don't know how.  I don't think my card was [not] recognized.  It is a Creative Labs Sound Blaster 16 (ct2290 printed on the board)

I don't know if ant of this helps.  I'm guessing I have to load my driver into a alsa module, that stuff is really confusing me.

 
```

bob@ubuntu-silver:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
0000:00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:00:0b.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev 01)
0000:00:13.0 Mass storage controller: Triones Technologies, Inc. HPT366/368/370/370A/372/372N (rev 01)
0000:00:13.1 Mass storage controller: Triones Technologies, Inc. HPT366/368/370/370A/372/372N (rev 01)
0000:01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 86C326 5598/6326 (rev 0b)
bob@ubuntu-silver:~$
```

```
bob@ubuntu-silver:~$ lsmod
Module                  Size  Used by
nls_utf8                2240  1
nls_cp437               5888  1
vfat                   14496  1
fat                    55548  1 vfat
sg                     40160  0
sd_mod                 20448  2
usb_storage            79648  1
scsi_mod              145960  3 sg,sd_mod,usb_storage
rfcomm                 43604  0
l2cap                  28192  5 rfcomm
bluetooth              54212  4 rfcomm,l2cap
apm                    22768  1
ppdev                   9668  0
cpufreq_userspace       6496  0
cpufreq_stats           6688  0
freq_table              4928  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        7752  0
cpufreq_conservative     9000  0
ipv6                  286976  20
dm_mod                 63256  1
md_mod                 76052  0
af_packet              24520  2
lp                     12356  0
tsdev                   8032  0
e100                   40964  0
mii                     6176  1 e100
floppy                 64676  0
parport_pc             37988  1
parport                39400  3 ppdev,lp,parport_pc
pcspkr                  2244  0
psmouse                40004  0
i2c_piix4               9168  0
serio_raw               7748  0
intel_agp              24700  1
agpgart                36784  1 intel_agp
i2c_core               22848  1 i2c_piix4
shpchp                 49504  0
pci_hotplug            30788  1 shpchp
evdev                  10176  1
ext3                  148296  1
jbd                    65876  1 ext3
ide_generic             1504  0
uhci_hcd               35536  0
usbcore               139172  3 usb_storage,uhci_hcd
hpt366                 20832  2
ide_cd                 35780  0
cdrom                  41408  1 ide_cd
ide_disk               19136  3
piix                   11652  1
generic                 5124  0
processor              26888  0
capability              4968  0
commoncap               7328  1 capability
vga16fb                13992  1
vgastate               10208  1 vga16fb
fbcon                  43904  72
tileblit                2784  1 fbcon
font                    8320  1 fbcon
bitblit                 6464  1 fbcon
softcursor              2304  1 bitblit
bob@ubuntu-silver:~$
```


bo```
b@ubuntu-silver:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device
bob@ubuntu-silver:~$

```

---

### Post by budgie9 on 2006-12-08
Take a look here it may help
[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Vibra16X.&chip=sb16&module=sb16](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Vibra16X.&chip=sb16&module=sb16)

---

