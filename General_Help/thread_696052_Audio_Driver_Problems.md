---
title: "Audio Driver Problems"
date: 2008-02-13
forum: General Help
---

### Post by Djinndrache on 2008-02-13
I got a laptop with Windows Vista. Sound works well on this OS.

Then I installed Ubuntu as 2nd OS. But sound doesnt work at al in ubuntul! Not even in system,options,audio the testing works.
My laptop is a MEDION MD96290.
As device I can choose 2 things: "HDA Intel (Alsa mixer)" and "Realtek ALC883 (OSS Mixer)". None of those can even do a "beep".


Couldn't find out more information about my audio-hardware as I'm a newbie at ubuntu.


Please help me, I dont like to work on a system without sound :(


Er, if anyone should need that info: I'm using gnome (not kde).

---

### Post by Djinndrache on 2008-02-13
Nobody can help me? :(

---

### Post by y-lee on 2008-02-13
Open up a terminal and type

 ```
aplay -l
```

and post the result here.

---

### Post by Djinndrache on 2008-02-14
**** Liste von PLAYBACK Geräten ****
Karte 0: Intel [HDA Intel], Gerät 0: ALC883 Analog [ALC883 Analog]
  Untergeordnete Geräte: 1/1
  Untergeordnetes Gerät '0: subdevice #0
Karte 0: Intel [HDA Intel], Gerät 1: ALC883 Digital [ALC883 Digital]
  Untergeordnete Geräte: 1/1
  Untergeordnetes Gerät '0: subdevice #0
Karte 0: Intel [HDA Intel], Gerät 6: Si3054 Modem [Si3054 Modem]
  Untergeordnete Geräte: 1/1
  Untergeordnetes Gerät '0: subdevice #0


Er.. this is German ubuntu version ^^

---

### Post by Djinndrache on 2008-02-14
Er.. and now? :(

---

### Post by Djinndrache on 2008-02-14
Still need help :'(

---

### Post by Crafty Kisses on 2008-02-14
Sorry about these outputs, can you post one more?
```
lspci
```
Thanks!

---

### Post by y-lee on 2008-02-14
Ok that was a check to see if your audio devices are properly recognized/

Now lets see if you are in the audio group, try

```
grep 'audio' /etc/group
```

You should see a line similar to


```
audio:x:29:username
```


Where *username* is your username, if you see something else like

```
audio:x:29:root
```

then you need to add your username to the file by doing


 ```
sudo nano /etc/group
```

Now find the line that looks like

```
audio:x:29:root
```

and change it to
Code:

```
audio:x:29:root:username
```

only replacing username with your real username.

Hit CTRL + 0 to save, then CTRL + X to exit. Now try and seeif you have any sound.

If this isn't the problem then We need to check the sound mixer

```
alsamixer
```

You will now see what appears to be a graphical equalizer. It is more like ten different volume controls in the sample place.

 To navigate around:
          [LIST]
[*]Left and Right Arrow Keys - Move left and right 
[*]Up and Down Arrow Keys - Increase and decrease volume respectively.
[*]Letter M Key - Mutes/unmutes. If a channel is unmuted, then there is a green box underneath the volume slider. If the channel is muted, the box is grey.
[/LIST]

Make sure everything is unmuted and the volume is up.

Now we saving these Sound Settings
Do this step to ensure that your alsamixer settings are reloaded with each boot. First make sure you have your settings just the way you like them in alsamixer. Then do

```
sudo alsactl store 0
```

or if this is your nth sound card (where n is the number of soundcards in your computer) replace 0 with n-1.

If none of this works there is along list of things you can do at [Comprehensive Sound Problem Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449").

---

### Post by Djinndrache on 2008-02-14
First of all the lspci-result:
> 00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
0a:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
0a:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
0a:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
0a:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
0a:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)


Then i tried out the steps y-lee told me. The username in the "grep"-step was already mine (djinndrache). So I didn't nano anything. I went to alsamixer made sure all is unmuted and turned to max, saved settings and tried again, still no sound.

I already read the linked guide, but it couldnt help me too. Even the compiling my own driver didn't work!


I start to dislike ubuntu :( HEEELP

---

### Post by y-lee on 2008-02-14
> I start to dislike ubuntu  HEEELP

Ah no use to panic . I help people on a windows spyware forum too and lots of hard problems there too. Computers not working right can be tricky to figure out :confused:

Anyway if you go to preferences and then sound is your card listed as the default sound card? Do you have more  than one choice there? Have you tried all the choices listed there?

---

### Post by Djinndrache on 2008-02-15
There is

1. HDA Intel (Alsa mixer) <-- this is default
2. Realtek ALC883 (OSS Mixer)



No more.

I tried both, no sound :(

---

### Post by goodbye on 2008-02-15
Hi 
I tired the guide given in the post, and it worked for me. The only problem that I have now is, I need to access the terminal to change the sound options rather than the volume control. Any suggestions?

---

### Post by y-lee on 2008-02-15
Your sound card is definitely being recognized but something still is not right.

Could you reboot and then post the output of  dmesg  here:

```
dmesg 
```

---

### Post by y-lee on 2008-02-15
> **irfanmalick said:**
> Hi 
I tired the guide given in the post, and it worked for me. The only problem that I have now is, I need to access the terminal to change the sound options rather than the volume control. Any suggestions?

What exactly do you mean by sound options? Is this it :

```
gnome-sound-properties
```

---

### Post by Djinndrache on 2008-02-15
Here result for dmesg:

> [   19.386403] CPU: L2 cache: 1024K
[   19.386409] CPU: Physical Processor ID: 0
[   19.386413] CPU: Processor Core ID: 0
[   19.386417] CPU: After all inits, caps: bfe9fbff 00000000 00000000 00002940 0000c189 00000000 00000000
[   19.386434] Compat vDSO mapped to ffffe000.
[   19.386458] Checking 'hlt' instruction... OK.
[   19.402267] SMP alternatives: switching to UP code
[   19.403116] Early unpacking initramfs... done
[   20.122691] ACPI: Core revision 20070126
[   20.122810] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   20.152913] CPU0: Intel Genuine Intel(R) CPU           T2130  @ 1.86GHz stepping 0c
[   20.152944] SMP alternatives: switching to SMP code
[   20.153114] Booting processor 1/1 eip 3000
[   20.163344] Initializing CPU#1
[   20.240593] Calibrating delay using timer specific routine.. 3724.21 BogoMIPS (lpj=7448436)
[   20.240605] CPU: After generic identify, caps: bfe9fbff 00000000 00000000 00000000 0000c189 00000000 00000000
[   20.240615] monitor/mwait feature present.
[   20.240622] CPU: L1 I cache: 32K, L1 D cache: 32K
[   20.240626] CPU: L2 cache: 1024K
[   20.240631] CPU: Physical Processor ID: 0
[   20.240634] CPU: Processor Core ID: 1
[   20.240637] CPU: After all inits, caps: bfe9fbff 00000000 00000000 00002940 0000c189 00000000 00000000
[   20.241294] CPU1: Intel Genuine Intel(R) CPU           T2130  @ 1.86GHz stepping 0c
[   20.241335] Total of 2 processors activated (7453.44 BogoMIPS).
[   20.241543] ENABLING IO-APIC IRQs
[   20.241793] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   20.388493] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   20.408489] Brought up 2 CPUs
[   20.507903] migration_cost=67
[   20.508126] Booting paravirtualized kernel on bare hardware
[   20.508253] Time: 16:48:03  Date: 01/15/108
[   20.508288] NET: Registered protocol family 16
[   20.508465] EISA bus registered
[   20.508473] ACPI: bus type pci registered
[   20.508646] PCI: PCI BIOS revision 2.10 entry at 0xfd695, last bus=10
[   20.508651] PCI: Using configuration type 1
[   20.508655] Setting up standard PCI resources
[   20.516133] ACPI: EC: Look up EC in DSDT
[   20.518364] ACPI: EC: GPE=0x17, ports=0x66, 0x62
[   20.524040] ACPI: Interpreter enabled
[   20.524046] ACPI: (supports S0 S3 S4 S5)
[   20.524081] ACPI: Using IOAPIC for interrupt routing
[   20.539071] ACPI: EC: GPE=0x17, ports=0x66, 0x62
[   20.539185] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   20.539201] PCI: Probing PCI hardware (bus 00)
[   20.540238] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   20.540246] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[   20.542074] PCI: Transparent bridge - 0000:00:1e.0
[   20.542178] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   20.542857] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[   20.543128] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[   20.543400] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[   20.543698] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   20.574479] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *7
[   20.574680] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *3
[   20.574877] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 *11)
[   20.575072] ACPI: PCI Interrupt Link [LNKD] (IRQs *10 11)
[   20.575266] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[   20.575462] ACPI: PCI Interrupt Link [LNKF] (IRQs *10 11)
[   20.575656] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[   20.575853] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *5
[   20.576808] ACPI: Power Resource [PUBS] (on)
[   20.576854] Linux Plug and Play Support v0.97 (c) Adam Belay
[   20.576874] pnp: PnP ACPI init
[   20.576894] ACPI: bus type pnp registered
[   20.582263] pnp: PnP ACPI: found 11 devices
[   20.582269] ACPI: ACPI bus type pnp unregistered
[   20.582277] PnPBIOS: Disabled by ACPI PNP
[   20.582373] PCI: Using ACPI for IRQ routing
[   20.582378] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   20.621168] NET: Registered protocol family 8
[   20.621173] NET: Registered protocol family 20
[   20.621273] pnp: 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[   20.621281] pnp: 00:01: iomem range 0xfed14000-0xfed17fff could not be reserved
[   20.621289] pnp: 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
[   20.621296] pnp: 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
[   20.621311] pnp: 00:04: iomem range 0xfed00000-0xfed003ff could not be reserved
[   20.621327] pnp: 00:07: ioport range 0x6a0-0x6af has been reserved
[   20.621333] pnp: 00:07: ioport range 0x6b0-0x6ff has been reserved
[   20.623937] Time: tsc clocksource has been installed.
[   20.623960] Switched to high resolution mode on CPU 0
[   20.624110] Switched to high resolution mode on CPU 1
[   20.651924] PCI: Bridge: 0000:00:1c.0
[   20.651931]   IO window: 2000-2fff
[   20.651941]   MEM window: d4000000-d5ffffff
[   20.651950]   PREFETCH window: d0000000-d1ffffff
[   20.651961] PCI: Bridge: 0000:00:1c.1
[   20.651967]   IO window: 3000-3fff
[   20.651976]   MEM window: d6000000-d7ffffff
[   20.651985]   PREFETCH window: d2000000-d3ffffff
[   20.651994] PCI: Bridge: 0000:00:1c.3
[   20.651997]   IO window: disabled.
[   20.652006]   MEM window: disabled.
[   20.652012]   PREFETCH window: disabled.
[   20.652022] PCI: Bridge: 0000:00:1e.0
[   20.652026]   IO window: disabled.
[   20.652035]   MEM window: d8000000-d80fffff
[   20.652042]   PREFETCH window: disabled.
[   20.652086] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 16
[   20.652098] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   20.652133] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 17
[   20.652144] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   20.652178] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 18
[   20.652189] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   20.652210] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   20.652232] NET: Registered protocol family 2
[   20.699797] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   20.699898] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   20.702104] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   20.702876] TCP: Hash tables configured (established 131072 bind 65536)
[   20.702881] TCP reno registered
[   20.715994] checking if image is initramfs... it is
[   22.153301] Freeing initrd memory: 7064k freed
[   22.153465] Simple Boot Flag at 0x36 set to 0x1
[   22.154391] audit: initializing netlink socket (disabled)
[   22.154416] audit(1203094084.672:1): initialized
[   22.154599] highmem bounce pool size: 64 pages
[   22.158565] VFS: Disk quotas dquot_6.5.1
[   22.158668] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   22.158844] io scheduler noop registered
[   22.158849] io scheduler anticipatory registered
[   22.158853] io scheduler deadline registered
[   22.158885] io scheduler cfq registered (default)
[   22.158909] Boot video device is 0000:00:02.0
[   22.159174] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   22.159250] assign_interrupt_mode Found MSI capability
[   22.159257] Allocate Port Service[0000:00:1c.0:pcie00]
[   22.159335] Allocate Port Service[0000:00:1c.0:pcie02]
[   22.159489] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   22.159565] assign_interrupt_mode Found MSI capability
[   22.159570] Allocate Port Service[0000:00:1c.1:pcie00]
[   22.159633] Allocate Port Service[0000:00:1c.1:pcie02]
[   22.159797] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   22.159873] assign_interrupt_mode Found MSI capability
[   22.159878] Allocate Port Service[0000:00:1c.3:pcie00]
[   22.159941] Allocate Port Service[0000:00:1c.3:pcie02]
[   22.160213] isapnp: Scanning for PnP cards...
[   22.514080] isapnp: No Plug & Play device found
[   22.562603] Real Time Clock Driver v1.12ac
[   22.562996] hpet_resources: 0xfed00000 is busy
[   22.563044] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   22.565332] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   22.565748] input: Macintosh mouse button emulation as /class/input/input0
[   22.565901] PNP: PS/2 Controller [PNP0303:KBD0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   22.567008] i8042.c: Detected active multiplexing controller, rev 1.1.
[   22.567099] serio: i8042 KBD port at 0x60,0x64 irq 1
[   22.567108] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   22.567114] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   22.567119] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   22.567125] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   22.567490] mice: PS/2 mouse device common for all mice
[   22.567866] EISA: Probing bus 0 at eisa.0
[   22.567878] Cannot allocate resource for EISA slot 1
[   22.567885] Cannot allocate resource for EISA slot 2
[   22.567890] Cannot allocate resource for EISA slot 3
[   22.567925] EISA: Detected 0 cards.
[   22.568086] TCP cubic registered
[   22.568111] NET: Registered protocol family 1
[   22.568152] Using IPI No-Shortcut mode
[   22.568485]   Magic number: 12:585:843
[   22.568612]   hash matches device ptyu9
[   22.568628]   hash matches device ptyrc
[   22.568996] Freeing unused kernel memory: 364k freed
[   22.577242] input: AT Translated Set 2 keyboard as /class/input/input1
[   24.000214] AppArmor: AppArmor initialized<5>audit(1203094086.172:2):  type=1505 info="AppArmor initialized" pid=1237
[   24.012619] fuse init (API version 7.8)
[   24.021821] Failure registering capabilities with primary security module.
[   24.056524] ACPI: SSDT 7F691AF0, 022C (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
[   24.056969] ACPI: SSDT 7F6918A0, 01CB (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[   24.057567] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   24.058078] ACPI: SSDT 7F691D1C, 0089 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
[   24.058503] ACPI: SSDT 7F691A6B, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
[   24.059157] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    4.616000] Marking TSC unstable due to: possible TSC halt in C2.
[    4.616000] ACPI: Thermal Zone [TZS0] (34 C)
[    4.620000] Time: hpet clocksource has been installed.
[    4.620000] ACPI: Thermal Zone [TZS1] (44 C)
[    5.440000] usbcore: registered new interface driver usbfs
[    5.440000] usbcore: registered new interface driver hub
[    5.440000] usbcore: registered new device driver usb
[    5.440000] USB Universal Host Controller Interface driver v3.0
[    5.440000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
[    5.440000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    5.440000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    5.440000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    5.440000] uhci_hcd 0000:00:1d.0: irq 19, io base 0x00001820
[    5.440000] usb usb1: configuration #1 chosen from 1 choice
[    5.440000] hub 1-0:1.0: USB hub found
[    5.440000] hub 1-0:1.0: 2 ports detected
[    5.540000] SCSI subsystem initialized
[    5.548000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 16
[    5.548000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    5.548000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    5.548000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    5.548000] uhci_hcd 0000:00:1d.1: irq 16, io base 0x00001840
[    5.552000] usb usb2: configuration #1 chosen from 1 choice
[    5.552000] hub 2-0:1.0: USB hub found
[    5.552000] hub 2-0:1.0: 2 ports detected
[    5.552000] libata version 2.21 loaded.
[    5.656000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 20
[    5.656000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    5.656000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    5.656000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    5.656000] uhci_hcd 0000:00:1d.2: irq 20, io base 0x00001860
[    5.656000] usb usb3: configuration #1 chosen from 1 choice
[    5.656000] hub 3-0:1.0: USB hub found
[    5.656000] hub 3-0:1.0: 2 ports detected
[    5.760000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 19 (level, low) -> IRQ 18
[    5.760000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    5.760000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    5.760000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    5.760000] uhci_hcd 0000:00:1d.3: irq 18, io base 0x00001880
[    5.760000] usb usb4: configuration #1 chosen from 1 choice
[    5.760000] hub 4-0:1.0: USB hub found
[    5.760000] hub 4-0:1.0: 2 ports detected
[    5.868000] r8169 Gigabit Ethernet driver 2.2LK loaded
[    5.868000] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 17 (level, low) -> IRQ 16
[    5.868000] PCI: Setting latency timer of device 0000:04:00.0 to 64
[    5.868000] eth0: RTL8101e at 0xf8866000, 00:16:d3:83:09:cf, XID 34000000 IRQ 16
[    5.868000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
[    5.868000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    5.868000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    5.868000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    5.868000] ehci_hcd 0000:00:1d.7: debug port 1
[    5.868000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    5.868000] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xd8444000
[    5.872000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    5.872000] usb usb5: configuration #1 chosen from 1 choice
[    5.872000] hub 5-0:1.0: USB hub found
[    5.872000] hub 5-0:1.0: 8 ports detected
[    5.976000] ata_piix 0000:00:1f.1: version 2.11
[    5.976000] ACPI: PCI Interrupt 0000:00:1f.1[B] -> GSI 19 (level, low) -> IRQ 18
[    5.976000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    5.976000] scsi0 : ata_piix
[    5.976000] scsi1 : ata_piix
[    5.976000] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011810 irq 14
[    5.976000] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011818 irq 15
[    6.004000] Clocksource tsc unstable (delta = -64124695 ns)
[    6.220000] usb 5-6: new high speed USB device using ehci_hcd and address 2
[    6.312000] ata1.00: ATAPI: TSSTcorp CDDVDW SN-S082H, SB00, max UDMA/33
[    6.364000] usb 5-6: configuration #1 chosen from 1 choice
[    6.500000] ata1.00: configured for UDMA/33
[    6.500000] ata2: port disabled. ignoring.
[    6.500000] scsi 0:0:0:0: CD-ROM            TSSTcorp CDDVDW SN-S082H  SB00 PQ: 0 ANSI: 5
[    6.500000] ahci 0000:00:1f.2: version 2.2
[    6.500000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 18
[    6.604000] usb 5-8: new high speed USB device using ehci_hcd and address 3
[    6.740000] usb 5-8: configuration #1 chosen from 1 choice
[    7.508000] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 1.5 Gbps 0xf impl SATA mode
[    7.508000] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part 
[    7.508000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    7.508000] scsi2 : ahci
[    7.508000] scsi3 : ahci
[    7.508000] scsi4 : ahci
[    7.508000] scsi5 : ahci
[    7.508000] ata3: SATA max UDMA/133 cmd 0xf8872500 ctl 0x00000000 bmdma 0x00000000 irq 18
[    7.508000] ata4: SATA max UDMA/133 cmd 0xf8872580 ctl 0x00000000 bmdma 0x00000000 irq 18
[    7.508000] ata5: SATA max UDMA/133 cmd 0xf8872600 ctl 0x00000000 bmdma 0x00000000 irq 18
[    7.508000] ata6: SATA max UDMA/133 cmd 0xf8872680 ctl 0x00000000 bmdma 0x00000000 irq 18
[    7.992000] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    8.028000] ata3.00: ATA-7: WDC WD1600BEVS-22RST0, 04.01G04, max UDMA/133
[    8.028000] ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    8.028000] ata3.00: configured for UDMA/133
[    8.340000] ata4: SATA link down (SStatus 0 SControl 0)
[    8.652000] ata5: SATA link down (SStatus 0 SControl 300)
[    8.964000] ata6: SATA link down (SStatus 0 SControl 0)
[    8.964000] scsi 2:0:0:0: Direct-Access     ATA      WDC WD1600BEVS-2 04.0 PQ: 0 ANSI: 5
[    8.964000] ACPI: PCI Interrupt 0000:0a:09.0[A] -> GSI 16 (level, low) -> IRQ 17
[    9.020000] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    9.020000] sd 2:0:0:0: [sda] Write Protect is off
[    9.020000] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    9.020000] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    9.020000] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    9.020000] sd 2:0:0:0: [sda] Write Protect is off
[    9.020000] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    9.020000] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    9.020000]  sda:<6>ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[d8000000-d80007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    9.056000] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    9.056000] Uniform CD-ROM driver Revision: 3.20
[    9.056000] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    9.064000]  sda1 < sda5 sda6 > sda2 sda3
[    9.092000] sd 2:0:0:0: [sda] Attached SCSI disk
[    9.104000] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    9.104000] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    9.580000] Attempting manual resume
[    9.580000] swsusp: Resume From Partition 8:6
[    9.580000] PM: Checking swsusp image.
[    9.580000] PM: Resume from disk failed.
[    9.620000] kjournald starting.  Commit interval 5 seconds
[    9.620000] EXT3-fs: mounted filesystem with ordered data mode.
[   10.300000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[07e40a006f0d7027]
[   19.124000] intel_rng: FWH not detected
[   19.176000] iTCO_vendor_support: vendor-support=0
[   19.176000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   19.176000] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   19.176000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   19.248000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   19.252000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   19.600000] Linux agpgart interface v0.102 (c) Dave Jones
[   19.600000] agpgart: Detected an Intel 945GM Chipset.
[   19.604000] agpgart: Detected 7932K stolen memory.
[   19.624000] agpgart: AGP aperture is 256M @ 0xc0000000
[   20.208000] sdhci: Secure Digital Host Controller Interface driver
[   20.208000] sdhci: Copyright(c) Pierre Ossman
[   20.208000] sdhci: SDHCI controller found at 0000:0a:09.1 [1180:0822] (rev 19)
[   20.208000] ACPI: PCI Interrupt 0000:0a:09.1[B] -> GSI 18 (level, low) -> IRQ 20
[   20.208000] mmc0: SDHCI at 0xd8000800 irq 20 DMA
[   20.284000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x23aeb3, caps: 0xa04713/0x10008
[   20.312000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[   20.824000] Linux video capture interface: v2.00
[   20.960000] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (064e:a100)
[   20.964000] usbcore: registered new interface driver uvcvideo
[   20.964000] USB Video Class driver (v0.1.0)
[   21.380000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 21
[   21.380000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   21.412000] ALSA /usr/src/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:698: codec_mask = 0x3
[   21.588000] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:1810: hda_codec: model '3stack-dig' is selected
[   22.248000] lp: driver loaded but no devices found
[   22.376000] ndiswrapper version 1.45 loaded (smp=yes)
[   22.572000] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[   22.736000] ndiswrapper: driver net8187b (Realtek Semiconductor Corp.,04/06/2007,5.1074.0406.2007) loaded
[   27.408000] wlan0: ethernet device 00:07:ca:05:cd:75 using NDIS driver: net8187b, version: 0x1, NDIS version: 0x500, vendor: 'Realtek Wireless LAN', 0BDA:8189.F.conf
[   27.408000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   27.408000] usbcore: registered new interface driver ndiswrapper
[   27.484000] QEMU Accelerator Module version 1.3.0, Copyright (c) 2005-2007 Fabrice Bellard
[   27.484000] KQEMU installed, max_locked_mem=1033204kB.
[   27.556000] Adding 1694784k swap on /dev/sda6.  Priority:-1 extents:1 across:1694784k
[   28.084000] EXT3 FS on sda3, internal journal
[   30.104000] ACPI: Battery Slot [BAT0] (battery present)
[   30.192000] No dock devices found.
[   30.260000] ACPI: AC Adapter [ADP1] (off-line)
[   30.400000] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   30.460000] input: Power Button (FF) as /class/input/input3
[   30.460000] ACPI: Power Button (FF) [PWRF]
[   30.464000] input: Lid Switch as /class/input/input4
[   30.464000] ACPI: Lid Switch [LID0]
[   30.464000] input: Sleep Button (CM) as /class/input/input5
[   30.464000] ACPI: Sleep Button (CM) [SLPB]
[   31.900000] ppdev: user-space parallel port driver
[   32.084000] audit(1203090513.653:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5138 profile="/usr/sbin/cupsd"
[   32.156000] apm: BIOS not found.
[   32.160000] r8169: eth0: link down
[   33.080000] Failure registering capabilities with primary security module.
[   33.352000] Bluetooth: Core ver 2.11
[   33.352000] NET: Registered protocol family 31
[   33.352000] Bluetooth: HCI device and connection manager initialized
[   33.352000] Bluetooth: HCI socket layer initialized
[   33.368000] Bluetooth: L2CAP ver 2.8
[   33.368000] Bluetooth: L2CAP socket layer initialized
[   33.444000] Bluetooth: RFCOMM socket layer initialized
[   33.444000] Bluetooth: RFCOMM TTY layer initialized
[   33.444000] Bluetooth: RFCOMM ver 1.8
[   37.036000] ALSA /usr/src/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:1188: azx_pcm_prepare: bufsize=0x10000, fragsize=0x1000, format=0x11
[   37.044000] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:631: hda_codec_setup_stream: NID=0x6, stream=0x5, channel=0, format=0x11
[   37.052000] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:631: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x11
[   37.060000] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:631: hda_codec_setup_stream: NID=0x4, stream=0x5, channel=0, format=0x11
[   37.072000] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:631: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x11
[   37.080000] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:631: hda_codec_setup_stream: NID=0x5, stream=0x5, channel=0, format=0x11
[   37.188000] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:631: hda_codec_setup_stream: NID=0x2, stream=0x0, channel=0, format=0x0
[   37.196000] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:631: hda_codec_setup_stream: NID=0x4, stream=0x0, channel=0, format=0x0
[   37.204000] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:631: hda_codec_setup_stream: NID=0x3, stream=0x0, channel=0, format=0x0
[   37.212000] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:631: hda_codec_setup_stream: NID=0x5, stream=0x0, channel=0, format=0x0
[   37.220000] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:631: hda_codec_setup_stream: NID=0x6, stream=0x0, channel=0, format=0x0
[   38.640000] [drm] Initialized drm 1.1.0 20060810
[   38.640000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
[   38.640000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   45.452000] ALSA /usr/src/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:1188: azx_pcm_prepare: bufsize=0x10000, fragsize=0x1000, format=0x11
[   45.460000] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:631: hda_codec_setup_stream: NID=0x6, stream=0x5, channel=0, format=0x11
[   45.468000] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:631: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x11
[   45.476000] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:631: hda_codec_setup_stream: NID=0x4, stream=0x5, channel=0, format=0x11
[   45.484000] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:631: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x11
[   45.492000] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:631: hda_codec_setup_stream: NID=0x5, stream=0x5, channel=0, format=0x11
[   45.944000] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:631: hda_codec_setup_stream: NID=0x2, stream=0x0, channel=0, format=0x0
[   45.952000] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:631: hda_codec_setup_stream: NID=0x4, stream=0x0, channel=0, format=0x0
[   45.964000] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:631: hda_codec_setup_stream: NID=0x3, stream=0x0, channel=0, format=0x0
[   45.972000] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:631: hda_codec_setup_stream: NID=0x5, stream=0x0, channel=0, format=0x0
[   45.980000] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:631: hda_codec_setup_stream: NID=0x6, stream=0x0, channel=0, format=0x0
[   87.480000] ALSA /usr/src/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:1188: azx_pcm_prepare: bufsize=0x10000, fragsize=0x1000, format=0x11
[   87.488000] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:631: hda_codec_setup_stream: NID=0x6, stream=0x5, channel=0, format=0x11
[   87.496000] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:631: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x11
[   87.504000] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:631: hda_codec_setup_stream: NID=0x4, stream=0x5, channel=0, format=0x11
[   87.512000] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:631: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x11
[   87.520000] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:631: hda_codec_setup_stream: NID=0x5, stream=0x5, channel=0, format=0x11
[   95.848000] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:631: hda_codec_setup_stream: NID=0x2, stream=0x0, channel=0, format=0x0
[   95.856000] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:631: hda_codec_setup_stream: NID=0x4, stream=0x0, channel=0, format=0x0
[   95.864000] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:631: hda_codec_setup_stream: NID=0x3, stream=0x0, channel=0, format=0x0
[   95.872000] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:631: hda_codec_setup_stream: NID=0x5, stream=0x0, channel=0, format=0x0
[   95.880000] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:631: hda_codec_setup_stream: NID=0x6, stream=0x0, channel=0, format=0x0
[  107.348000] NET: Registered protocol family 17
[  126.244000] NET: Registered protocol family 10
[  126.244000] lo: Disabled Privacy Extensions
[  126.244000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  126.244000] ADDRCONF(NETDEV_UP): wlan0: link is not ready

---

### Post by goodbye on 2008-02-15
> **y-lee said:**
> What exactly do you mean by sound options? Is this it :

```
gnome-sound-properties
```

I meant the volume in the top task bar. If I reduce the volume over there nothing happens to the sound. If I reduce the volume from the mixer then obviously the sound turns off. 

Thanks

---

### Post by y-lee on 2008-02-15
Ok I was looking for a specific error message in dmesg and it is not there. But I also I don't see any strings like "snd_", hmm

Could you post the file **alsa-base** found I think at **/etc/modprobe.d**?

Also note use the tag code instead of quote  for terminal outputs or long files makes thing easier, it is the **# **button at the top of the text area here :)

I don't recall you saying but has the sound ever worked and suddenly stopped or have you never had sound since you installed?

---

### Post by y-lee on 2008-02-15
> **irfanmalick said:**
> I meant the volume in the top task bar. If I reduce the volume over there nothing happens to the sound. If I reduce the volume from the mixer then obviously the sound turns off. 

Thanks

```
gnome-volume-control
```

is the volume control found in your panel (task bar),

I'm not sure what is going on with volume in task bar not working. But a true command line tool to control volume is aumix. If you don't have it,  it is in the repos. Look for it in Synaptic :)

```
aumix
```

**EDIT:** If you give aumix a try **man aumix** for information on it and note** q **exits the man page and **Ctrl + C** exits aumix.

---

### Post by goodbye on 2008-02-16
> **y-lee said:**
> ```
gnome-volume-control
```

is the volume control found in your panel (task bar),

I'm not sure what is going on with volume in task bar not working. But a true command line tool to control volume is aumix. If you don't have it,  it is in the repos. Look for it in Synaptic :)

```
aumix
```

**EDIT:** If you give aumix a try **man aumix** for information on it and note** q **exits the man page and **Ctrl + C** exits aumix.

Hi,

I have shortcut keys on the keyboard, like every other laptop keyboard. When I try to adjust the volume from there nothing happens. I goto the volume icon on the top task bar and adjust it from there nothing happens. What I mean by nothing happens, is that no effect on volume.
If I goto the command you wrote earlier right, and change the volume from there, THEN the volume is adjusted according to my desired level.

That is the problem.

Thanks

---

### Post by y-lee on 2008-02-16
> **irfanmalick said:**
> 
I have shortcut keys on the keyboard, like every other laptop keyboard. When I try to adjust the volume from there nothing happens. I goto the volume icon on the top task bar and adjust it from there nothing happens. What I mean by nothing happens, is that no effect on volume.
If I goto the command you wrote earlier right, and change the volume from there, THEN the volume is adjusted according to my desired level.



In other words the command  **gnome-volume-control** works for you?

 BTW this should be found in your menu under   **Sound and Video**, if not open your Alacarte Menu editor and be sure it is checked if you want to use it from the menu.

I'm not sure what version of Ubuntu you are running, so I'm assuming Gusty tho I myself have Dapper. (In other words things may be a* little different* on your system but this is the basic idea) So anyway there are 2 things I know you  can try if you haven't already

[LIST]
[*]Go to System/Preferences/Sound and in the bottom of the Devices-tab there's section called 'Default Mixer Tracks'. Set there the sound card you want to use and select the tracks you want to control with your volume keys (you can select multiple tracks using Ctrl).
[*]Rick click the gnome panel volume control and click preferences.  In preferences be sure the right audio device (sound card) is selected. And to control volume for your system make  sure Master is selected.
[/LIST]

As to the volume control button on you laptop not working What laptop do you have?  I'll look around and see what I can find out :)

Let us know if any of the above works for you or not.

---

### Post by goodbye on 2008-02-16
> **y-lee said:**
> In other words the command  **gnome-volume-control** works for you?

 BTW this should be found in your menu under   **Sound and Video**, if not open your Alacarte Menu editor and be sure it is checked if you want to use it from the menu.

I'm not sure what version of Ubuntu you are running, so I'm assuming Gusty tho I myself have Dapper. (In other words things may be a* little different* on your system but this is the basic idea) So anyway there are 2 things I know you  can try if you haven't already

[LIST]
[*]Go to System/Preferences/Sound and in the bottom of the Devices-tab there's section called 'Default Mixer Tracks'. Set there the sound card you want to use and select the tracks you want to control with your volume keys (you can select multiple tracks using Ctrl).
[*]Rick click the gnome panel volume control and click preferences.  In preferences be sure the right audio device (sound card) is selected. And to control volume for your system make  sure Master is selected.
[/LIST]

As to the volume control button on you laptop not working What laptop do you have?  I'll look around and see what I can find out :)

Let us know if any of the above works for you or not.

Hi y-lee

No not the gnome-volume-options but this one **alsamixer** If I edit the volume here it would change, otherwise it would not change. I am using Ubuntu 7.10 I couldn't attach the picture of the alsamixer because it required a website. I just don' know how to do it.

I would tell you the important information though.

Card: HDA Intel
Chip: Realtek ALC883
View; Playback
I think that really is the important information. In my sound options from the system menu I have everything as ALC 883 analogue.


Thanks in advance. Wouldn't have come so far with out .

---

### Post by y-lee on 2008-02-16
Is ALC 883 analogue.set as the sound card in gnome-volume control?

---

### Post by goodbye on 2008-02-17
> **y-lee said:**
> Is ALC 883 analogue.set as the sound card in gnome-volume control?

Hi y-lee,

ALC 883 analogue is selected as the sound card.

---

### Post by goodbye on 2008-02-17
Hi y-lee

Figured out my problem.

All I needed to do was select ALSA as my driver in the sound control options and the volume options. Then I could control the voice form my key board.

Thanks.

---

### Post by Djinndrache on 2008-02-21
> **y-lee said:**
> Ok I was looking for a specific error message in dmesg and it is not there. But I also I don't see any strings like "snd_", hmm

Could you post the file **alsa-base** found I think at **/etc/modprobe.d**?

Also note use the tag code instead of quote  for terminal outputs or long files makes thing easier, it is the **# **button at the top of the text area here :)

I don't recall you saying but has the sound ever worked and suddenly stopped or have you never had sound since you installed?

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
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
options snd-hda-codec
options snd-hda-intel model=3stack-dig

---

### Post by Djinndrache on 2008-02-21
I put headset-cable into external audio slot and the sound worked well.

But still there's no way to get sound through the notebook-speakers.



So I just need to set them as default, right? Where can I do it? In preferences/sound-settings it isn't possible :(

---

### Post by Djinndrache on 2008-02-21
Any suggestions?

Just need to activate the notebook-intern speakers and don't know how... (at least I think so ;))

---

### Post by Djinndrache on 2008-02-21
Still waiting for support.. :)

---

### Post by y-lee on 2008-02-21
Sometimes checking "Surround" channel in the volume control
will send audio to the notebook's speaker. Just check out the Preferences in volume control and place a check mark at [ ] Surround.

If that doesn't work I'm trying to catch up on what we've tried and googling  around hunting for answers. :)

**Edit:**

go System->Preferences->Sound

Load up preferences and make sure that each item is checked to appear in the mixer. Make sure none of them are muted.

Then click on the "Switches" tab. At the bottom of the list is an "External Amplifier" switch. Toggle that to off, see if you now have sound.

---

### Post by Djinndrache on 2008-02-22
> **y-lee said:**
> Sometimes checking "Surround" channel in the volume control
will send audio to the notebook's speaker. Just check out the Preferences in volume control and place a check mark at [ ] Surround.

If that doesn't work I'm trying to catch up on what we've tried and googling  around hunting for answers. :)

**Edit:**

go System->Preferences->Sound

Load up preferences and make sure that each item is checked to appear in the mixer. Make sure none of them are muted.

Then click on the "Switches" tab. At the bottom of the list is an "External Amplifier" switch. Toggle that to off, see if you now have sound.


Neither Surround nor External Amplifier can be found at the called places..

---

### Post by y-lee on 2008-02-22
> **Djinndrache said:**
> Neither Surround nor External Amplifier can be found at the called places..

What version of ubuntu do you have?

```
amixer set Surround unmute
```

```
amixer set 'External Amplifier' toggle
```

If this doesn't work, please run:

```
amixer scontrols > temporary_file
```

and post the contents of temporary-file here. To make it easier to read place the CODE tags around these results...highlight it and hit the** #** button above.

---

### Post by Djinndrache on 2008-02-22
Hi,


my ubuntu is "Ubuntu 7.10, kernel 2.6.22-14-generic".


Tried to do the posted commands, but got just errors in terminal:

"amixer: unable to find simple control 'Surround',0"

and same with "External Amplifier".


And the last of the posted commands didn't do any reply. Not even a error or a success report.. just jumped to next line for input.




So..?

---

### Post by y-lee on 2008-02-22
the best I can determine is the driver for your card is not installed :confused:

What does

```
lspci -s 00:1b.0 -n
```

give you?

And also post 

```
amixer
```

---

### Post by Djinndrache on 2008-02-22
First is

```
00.1b.0 0403: 8086:27d8 (rev 02)
```


Second one is too long to retype it. I will post it when I'm online with linux system next time. (I'm currently using other pc to go to internet and just have notebook beside me)

---

### Post by y-lee on 2008-02-22
This appears to be similar to a reported bug, see [[gutsy] no sound with PCID ID 8086:27d8 (rev 02)]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/126157"), your hardware is not exactly the same tho. I'm working on finding a fix but I'm not sure I can tho :confused:

> Second one is too long to retype it. I will post it when I'm online with linux system next time.

Go ahead and post the other too, may or may not help.  I suspect I know about what it will say :(

---

### Post by tomsa on 2008-02-22
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/194253](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/194253) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				This sounds like the problem I am having with my new install on a gateway t-1625 laptop.  The audio device is a ati radeon x-1270.  I have started a bug report, but I may have started it in relation to alsa in error.  Maybe you could shed some additional light on this?  I've seen a lot of threads that have issues similar to mine, and not a whole lot of solutions.  I'm not terribly skilled with linux OS yet, but I'd rather use my limited knowledge to be part of the solution, rather than part of the problem.  Please let me know if there is anything I can do to help, or any information I can provide from my own machine that you want to look at to find similarities, if possible.

---

### Post by Djinndrache on 2008-02-25
Here's reply for "amixer":

```
Simple mixer control 'Headphone',0
  Capabilities: pswitch
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [on]
  Front Right: Playback [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Front Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [on]
  Front Right: Playback 31 [100%] [12.00dB] [on]
Simple mixer control 'Front Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 3 [100%]
  Front Right: 3 [100%]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [on]
  Front Right: Playback 31 [100%] [12.00dB] [on]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [on]
  Front Right: Playback 31 [100%] [12.00dB] [on]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [on]
  Front Right: Playback 31 [100%] [12.00dB] [on]
Simple mixer control 'Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 3 [100%]
  Front Right: 3 [100%]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined cswitch cswitch-joined
  Playback channels: Mono
  Capture channels: Mono
  Mono: Playback [on] Capture [off]
Simple mixer control 'PC Speaker',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [on]
  Front Right: Playback 31 [100%] [12.00dB] [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 31 [100%] [34.50dB] [on]
  Front Right: Capture 31 [100%] [34.50dB] [on]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 0 [0%] [-12.00dB] [off]
  Front Right: Capture 0 [0%] [-12.00dB] [off]
Simple mixer control 'Caller ID',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Digital',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 120
  Front Left: Capture 120 [100%] [30.00dB]
  Front Right: Capture 120 [100%] [30.00dB]
Simple mixer control 'Input Source',0
  Capabilities: enum
  Items: 'Mic' 'Front Mic' 'Line' 'CD'
  Item0: 'Mic'
Simple mixer control 'Input Source',1
  Capabilities: enum
  Items: 'Mic' 'Front Mic' 'Line' 'CD'
  Item0: 'Mic'
Simple mixer control 'Off-hook',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]

```

---

### Post by ThunderRd on 2008-02-25
I think that you have to install a realtek driver.  I had the same problem, so check out this thread that involved my [64 bit] machine:

[http://ubuntuforums.org/showthread.php?t=660806](http://ubuntuforums.org/showthread.php?t=660806)

I am running 7.04 but I would guess that it's quite possible the thread may help.  Read the whole thread; it began as another SATA problem but developed in to a sound fix.

This is an educated guess, but I believe this is the file you need; many sources if you search for it, including the realtek site.

realtek-linux-audiopack-4.07a.tar.bz2

EDIT:  I have checked and indeed, this is the correct driver package for ALC888 and ALC883

---

