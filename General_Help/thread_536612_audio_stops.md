---
title: "audio stops"
date: 2007-08-27
forum: General Help
---

### Post by Dirk Lately on 2007-08-27
Every once in a while, my sound stops working. I think it happens after the screensaver or sleep, but I'm not sure.

It's a laptop, HP/Compaq NC6000 running Feisty. I'd love to fix the problem, of course, but lacking that, perhaps someone could show me a way to restart the sound easily? The only way I know to do it right now is to restart.


douglas@douglas-nc6000:~$ lspci
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
02:06.0 CardBus bridge: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller
02:06.1 CardBus bridge: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller
02:06.2 System peripheral: O2 Micro, Inc. OZ711Mx 4-in-1 MemoryCardBus Accelerator
02:06.3 CardBus bridge: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller
02:0e.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M_2 Gigabit Ethernet (rev 03)

douglas@douglas-nc6000:~$ lsmod
Module                  Size  Used by
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25856  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0 
radeon                124576  3 
drm                    81044  4 radeon
speedstep_centrino      9920  0 
cpufreq_powersave       2688  0 
cpufreq_userspace       5408  0 
cpufreq_conservative     8200  0 
cpufreq_stats           7360  0 
cpufreq_ondemand        9228  1 
freq_table              5792  3 speedstep_centrino,cpufreq_stats,cpufreq_ondemand
dev_acpi               12292  0 
sony_acpi               6284  0 
pcc_acpi               13184  0 
tc1100_wmi              8068  0 
dock                   10268  0 
sbs                    15652  0 
asus_acpi              17308  0 
button                  8720  0 
battery                10756  0 
backlight               7040  1 asus_acpi
container               5248  0 
ac                      6020  0 
video                  16388  0 
i2c_ec                  6016  1 sbs
i2c_core               22656  1 i2c_ec
ipv6                  268960  156 
lp                     12452  0 
fuse                   46612  1 
aes                    28608  1 
airo_cs                 7168  1 
airo                   74400  1 airo_cs
snd_intel8x0           34332  3 
snd_ac97_codec         98464  1 snd_intel8x0
pcmcia                 39212  1 airo_cs
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
irtty_sir               9600  0 
sir_dev                17156  1 irtty_sir
smsc_ircc2             23324  0 
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
irda                  201276  3 irtty_sir,sir_dev,smsc_ircc2
joydev                 10816  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  3 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
crc_ccitt               3072  1 irda
yenta_socket           27532  5 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40852  4 airo_cs,pcmcia,yenta_socket,rsrc_nonstatic
snd                    54020  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcspkr                  4224  0 
soundcore               8672  1 snd
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc
iTCO_wdt               11812  0 
iTCO_vendor_support     4868  1 iTCO_wdt
snd_page_alloc         10888  2 snd_intel8x0,snd_pcm
psmouse                38920  0 
serio_raw               7940  0 
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
intel_agp              25244  1 
agpgart                35400  2 drm,intel_agp
af_packet              23816  6 
evdev                  11008  4 
tsdev                   8768  0 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
sr_mod                 17060  0 
cdrom                  37664  1 sr_mod
sd_mod                 23428  3 
ata_generic             9092  0 
usbhid                 26592  0 
hid                    27392  1 usbhid
ata_piix               15492  2 
libata                125720  2 ata_generic,ata_piix
scsi_mod              142348  4 sg,sr_mod,sd_mod,libata
floppy                 59524  0 
tg3                   109700  0 
generic                 5124  0 [permanent]
ehci_hcd               34188  0 
uhci_hcd               25360  0 
usbcore               134280  4 usbhid,ehci_hcd,uhci_hcd
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
douglas@douglas-nc6000:~$ 
douglas@douglas-nc6000:~$ 


Any ideas how to fix?

---

### Post by tCarls on 2007-08-27
Does anything useful show up in /var/log/messages around the time that the sound stops? I had a similar problem a while ago. There were error lines in /var/log/messages saying things about an IRQ. I disabled that IRQ in the BIOS and it solved the problem.

---

### Post by Dirk Lately on 2007-08-28
Thanks for the advice! The problem definitely is related to suspend mode. When I wake it up, the sound doesn't work.

Here is a section of my /var/log/messages file with the appropriate timestamp. I don't know what I'm looking at here, can anyone help transliterate?

Thanks!

Aug 28 12:31:21 douglas-nc6000 gnome-power-manager: (douglas) Suspending computer because the DBUS method Suspend() was invoked
Aug 28 12:31:23 douglas-nc6000 kernel: [ 7577.060000] pccard: card ejected from slot 1
Aug 28 12:31:24 douglas-nc6000 kernel: [ 7578.064000] ACPI: PCI interrupt for device 0000:02:0e.0 disabled
Aug 28 12:31:46 douglas-nc6000 kernel: [ 7583.444000] Disabling non-boot CPUs ...
Aug 28 12:31:46 douglas-nc6000 kernel: [ 7583.444000] Stopping tasks ... done.
Aug 28 12:31:46 douglas-nc6000 kernel: [ 7583.668000] Suspending console(s)
Aug 28 12:31:46 douglas-nc6000 kernel: [ 7585.496000] pnp: Device 00:05 disabled.
Aug 28 12:31:46 douglas-nc6000 kernel: [ 7585.496000] pnp: Device 00:02 disabled.
Aug 28 12:31:46 douglas-nc6000 kernel: [ 7585.496000] ACPI: PCI interrupt for device 0000:00:1f.5 disabled
Aug 28 12:31:46 douglas-nc6000 kernel: [ 7585.500000] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
Aug 28 12:31:46 douglas-nc6000 kernel: [ 7585.500000] ACPI: PCI interrupt for device 0000:00:1d.7 disabled
Aug 28 12:31:46 douglas-nc6000 kernel: [ 7585.516000] ACPI: PCI interrupt for device 0000:00:1d.2 disabled
Aug 28 12:31:46 douglas-nc6000 kernel: [ 7585.516000] ACPI: PCI interrupt for device 0000:00:1d.1 disabled
Aug 28 12:31:46 douglas-nc6000 kernel: [ 7585.516000] ACPI: PCI interrupt for device 0000:00:1d.0 disabled
Aug 28 12:31:46 douglas-nc6000 kernel: [ 7590.524000] ACPI: Transitioning device [C207] to D3
Aug 28 12:31:46 douglas-nc6000 kernel: [ 7590.524000] ACPI: Transitioning device [C207] to D3
Aug 28 12:31:46 douglas-nc6000 kernel: [ 7590.524000] ACPI: Transitioning device [C208] to D3
Aug 28 12:31:46 douglas-nc6000 kernel: [ 7590.524000] ACPI: Transitioning device [C208] to D3
Aug 28 12:31:46 douglas-nc6000 kernel: [ 7590.524000] ACPI: Transitioning device [C209] to D3
Aug 28 12:31:46 douglas-nc6000 kernel: [ 7590.524000] ACPI: Transitioning device [C209] to D3
Aug 28 12:31:46 douglas-nc6000 kernel: [ 7590.524000] ACPI: Transitioning device [C20A] to D3
Aug 28 12:31:46 douglas-nc6000 kernel: [ 7590.524000] ACPI: Transitioning device [C20A] to D3
Aug 28 12:31:46 douglas-nc6000 kernel: [ 7590.528000] ACPI: Transitioning device [C20A] to D0
Aug 28 12:31:46 douglas-nc6000 kernel: [ 7590.528000] ACPI: Transitioning device [C20A] to D0
Aug 28 12:31:46 douglas-nc6000 kernel: [ 7590.528000] ACPI: Unable to turn cooling device [deb37eb4] 'on'
Aug 28 12:31:46 douglas-nc6000 kernel: [ 7590.536000] PCI: Enabling device 0000:00:1d.0 (0000 -> 0001)
Aug 28 12:31:46 douglas-nc6000 kernel: [ 7590.536000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [C0C3] -> GSI 10 (level, low) -> IRQ 10
Aug 28 12:31:46 douglas-nc6000 kernel: [ 7590.536000] usb usb1: root hub lost power or was reset
Aug 28 12:31:46 douglas-nc6000 kernel: [ 7590.536000] PCI: Enabling device 0000:00:1d.1 (0000 -> 0001)
Aug 28 12:31:46 douglas-nc6000 kernel: [ 7590.536000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [C0C6] -> GSI 10 (level, low) -> IRQ 10
Aug 28 12:31:46 douglas-nc6000 kernel: [ 7590.536000] usb usb2: root hub lost power or was reset
Aug 28 12:31:46 douglas-nc6000 kernel: [ 7590.536000] PCI: Enabling device 0000:00:1d.2 (0000 -> 0001)
Aug 28 12:31:46 douglas-nc6000 kernel: [ 7590.536000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [C0C5] -> GSI 10 (level, low) -> IRQ 10
Aug 28 12:31:46 douglas-nc6000 kernel: [ 7590.536000] usb usb3: root hub lost power or was reset
Aug 28 12:31:46 douglas-nc6000 kernel: [ 7590.552000] PCI: Enabling device 0000:00:1d.7 (0000 -> 0002)
Aug 28 12:31:46 douglas-nc6000 kernel: [ 7590.552000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [C0CA] -> GSI 10 (level, low) -> IRQ 10
Aug 28 12:31:46 douglas-nc6000 kernel: [ 7590.552000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [C0C5] -> GSI 10 (level, low) -> IRQ 10
Aug 28 12:31:46 douglas-nc6000 kernel: [ 7590.552000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [C0C4] -> GSI 11 (level, low) -> IRQ 11
Aug 28 12:31:46 douglas-nc6000 kernel: [ 7591.556000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [C0C3] -> GSI 10 (level, low) -> IRQ 10
Aug 28 12:31:46 douglas-nc6000 kernel: [ 7591.556000] Yenta O2: res at 0x94/0xD4: ea/00
Aug 28 12:31:46 douglas-nc6000 kernel: [ 7591.556000] Yenta O2: enabling read prefetch/write burst
Aug 28 12:31:46 douglas-nc6000 kernel: [ 7591.572000] pnp: Device 00:02 activated.
Aug 28 12:31:46 douglas-nc6000 kernel: [ 7591.580000] pnp: Device 00:05 activated.
Aug 28 12:31:46 douglas-nc6000 kernel: [ 7591.580000] pnp: Device 00:0a does not support activation.
Aug 28 12:31:46 douglas-nc6000 kernel: [ 7591.580000] pnp: Device 00:0b does not support activation.
Aug 28 12:31:46 douglas-nc6000 kernel: [ 7592.432000] ata2: soft resetting port
Aug 28 12:31:46 douglas-nc6000 kernel: [ 7592.612000] ata1: EH pending after completion, repeating EH (cnt=4)
Aug 28 12:31:46 douglas-nc6000 kernel: [ 7592.612000] ata1: soft resetting port
Aug 28 12:31:46 douglas-nc6000 kernel: [ 7592.776000] ata1.00: ata_hpa_resize 1: sectors = 78140160, hpa_sectors = 78140160
Aug 28 12:31:46 douglas-nc6000 kernel: [ 7592.776000] ata1.00: limited to UDMA/33 due to 40-wire cable
Aug 28 12:31:46 douglas-nc6000 kernel: [ 7592.804000] ata1.00: ata_hpa_resize 1: sectors = 78140160, hpa_sectors = 78140160
Aug 28 12:31:46 douglas-nc6000 kernel: [ 7592.804000] ata1.00: configured for UDMA/33
Aug 28 12:31:46 douglas-nc6000 kernel: [ 7592.804000] ata1: EH complete
Aug 28 12:31:46 douglas-nc6000 kernel: [ 7592.804000] SCSI device sda: 78140160 512-byte hdwr sectors (40008 MB)
Aug 28 12:31:46 douglas-nc6000 kernel: [ 7592.804000] sda: Write Protect is off
Aug 28 12:31:46 douglas-nc6000 kernel: [ 7592.804000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 28 12:31:46 douglas-nc6000 kernel: [ 7592.916000] ata2.00: configured for MWDMA2
Aug 28 12:31:46 douglas-nc6000 kernel: [ 7592.916000] ata2: EH complete
Aug 28 12:31:46 douglas-nc6000 kernel: [ 7597.808000] Restarting tasks ... done.
Aug 28 12:31:46 douglas-nc6000 kernel: [ 7598.104000] Enabling non-boot CPUs ...
Aug 28 12:31:47 douglas-nc6000 kernel: [ 7599.028000] tg3.c:v3.72 (January 8, 2007)
Aug 28 12:31:47 douglas-nc6000 kernel: [ 7599.028000] ACPI: PCI Interrupt 0000:02:0e.0[A] -> Link [C0C7] -> GSI 11 (level, low) -> IRQ 11
Aug 28 12:31:47 douglas-nc6000 kernel: [ 7599.080000] eth0: Tigon3 [partno(BMC5705mA3) rev 3003 PHY(5705)] (PCI:33MHz:32-bit) 10/100/1000Base-T Ethernet 00:08:02:d9:b6:ef
Aug 28 12:31:47 douglas-nc6000 kernel: [ 7599.080000] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] Split[0] WireSpeed[0] TSOcap[1] 
Aug 28 12:31:47 douglas-nc6000 kernel: [ 7599.080000] eth0: dma_rwctrl[763f0000] dma_mask[64-bit]
Aug 28 12:31:48 douglas-nc6000 kernel: [ 7599.448000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 28 12:31:48 douglas-nc6000 dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Aug 28 12:31:48 douglas-nc6000 gnome-power-manager: (douglas) DBUS timed out, but recovering
Aug 28 12:31:48 douglas-nc6000 gnome-power-manager: (douglas) Resuming computer
Aug 28 12:31:48 douglas-nc6000 kernel: [ 7600.276000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 28 12:31:49 douglas-nc6000 kernel: [ 7600.644000] pccard: PCMCIA card inserted into slot 1
Aug 28 12:31:49 douglas-nc6000 kernel: [ 7600.644000] pcmcia: registering new device pcmcia1.0
Aug 28 12:31:50 douglas-nc6000 kernel: [ 7601.868000] airo(eth1): WPA is supported.
Aug 28 12:31:50 douglas-nc6000 kernel: [ 7601.872000] airo(eth1): MAC enabled 0:e:84:b4:5e:e
Aug 28 12:31:50 douglas-nc6000 kernel: [ 7601.876000] eth1: index 0x05: , Vpp 5.0, irq 3, io 0x4100-0x413f
Aug 28 12:31:49 douglas-nc6000 kernel: [ 7602.432000] input: Power Button (FF) as /class/input/input8
Aug 28 12:31:49 douglas-nc6000 kernel: [ 7602.432000] ACPI: Power Button (FF) [PWRF]
Aug 28 12:31:49 douglas-nc6000 kernel: [ 7602.436000] input: Sleep Button (CM) as /class/input/input9
Aug 28 12:31:49 douglas-nc6000 kernel: [ 7602.436000] ACPI: Sleep Button (CM) [C13B]
Aug 28 12:31:49 douglas-nc6000 kernel: [ 7602.436000] input: Lid Switch as /class/input/input10
Aug 28 12:31:49 douglas-nc6000 kernel: [ 7602.436000] ACPI: Lid Switch [C13A]
Aug 28 12:31:49 douglas-nc6000 kernel: [ 7602.556000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Aug 28 12:31:49 douglas-nc6000 kernel: [ 7602.556000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
Aug 28 12:31:49 douglas-nc6000 kernel: [ 7602.556000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
Aug 28 12:31:49 douglas-nc6000 kernel: [ 7602.556000] [drm] Loading R300 Microcode
Aug 28 12:31:50 douglas-nc6000 kernel: [ 7603.484000] ACPI: Transitioning device [C207] to D3
Aug 28 12:31:50 douglas-nc6000 kernel: [ 7603.484000] ACPI: Transitioning device [C207] to D3
Aug 28 12:31:50 douglas-nc6000 kernel: [ 7603.484000] ACPI: Fan [C207] (off)
Aug 28 12:31:50 douglas-nc6000 kernel: [ 7603.484000] ACPI: Transitioning device [C208] to D3
Aug 28 12:31:50 douglas-nc6000 kernel: [ 7603.484000] ACPI: Transitioning device [C208] to D3
Aug 28 12:31:50 douglas-nc6000 kernel: [ 7603.484000] ACPI: Fan [C208] (off)
Aug 28 12:31:50 douglas-nc6000 kernel: [ 7603.484000] ACPI: Transitioning device [C209] to D3
Aug 28 12:31:50 douglas-nc6000 kernel: [ 7603.484000] ACPI: Transitioning device [C209] to D3
Aug 28 12:31:50 douglas-nc6000 kernel: [ 7603.484000] ACPI: Fan [C209] (off)
Aug 28 12:31:50 douglas-nc6000 kernel: [ 7603.488000] ACPI: Transitioning device [C20A] to D3
Aug 28 12:31:50 douglas-nc6000 kernel: [ 7603.488000] ACPI: Transitioning device [C20A] to D3
Aug 28 12:31:50 douglas-nc6000 kernel: [ 7603.488000] ACPI: Fan [C20A] (off)
Aug 28 12:31:50 douglas-nc6000 kernel: [ 7603.520000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Aug 28 12:31:50 douglas-nc6000 kernel: [ 7603.520000] ACPI: Processor [CPU0] (supports 8 throttling states)
Aug 28 12:31:50 douglas-nc6000 kernel: [ 7603.536000] ACPI: Thermal Zone [TZ1] (41 C)
Aug 28 12:31:50 douglas-nc6000 kernel: [ 7603.548000] ACPI: Thermal Zone [TZ2] (51 C)
Aug 28 12:31:50 douglas-nc6000 kernel: [ 7603.556000] ACPI: Thermal Zone [TZ3] (16 C)
Aug 28 12:31:50 douglas-nc6000 kernel: [ 7603.620000] ACPI: AC Adapter [C136] (on-line)
Aug 28 12:31:50 douglas-nc6000 kernel: [ 7603.644000] ACPI: Battery Slot [C139] (battery absent)
Aug 28 12:31:50 douglas-nc6000 kernel: [ 7603.644000] ACPI: Battery Slot [C138] (battery absent)
Aug 28 12:32:29 douglas-nc6000 kernel: [ 7642.704000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Aug 28 12:33:15 douglas-nc6000 kernel: [ 7688.724000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready

---

### Post by Dirk Lately on 2007-09-01
Anyone have any thoughts on this? Particularly, how might I restart the sound without restarting the entire PC?

---

### Post by Dirk Lately on 2007-09-02
aw

---

### Post by Hexydes on 2007-09-03
Same thing happens to me. If I restart X (Ctrl + Alt + Backspace), and log back in, the sound works.

Oddly enough, audio in Flash videos works no matter what. The problem seems to only occur with local sounds (WAV, MP3, etc).

---

