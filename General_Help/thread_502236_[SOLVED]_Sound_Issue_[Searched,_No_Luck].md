---
title: "[SOLVED] Sound Issue [Searched, No Luck]"
date: 2007-07-16
forum: General Help
---

### Post by Skrypt on 2007-07-16
I've installed Ubuntu 7.04 w/ Feisty Fawn x86 Desktop.

At first, the sounds didn't work at all. After just a little bit of tinkering in System>Preferences>Sound I got some sound but not all. I had to change from 'Autodetect' to 'NVidia CK8S - IEC958' and the test worked.

I don't get startup/shutdown sounds or any other system sounds. I also don't receive any sound from Flash videos inside of Firefox.

aplay -l
```
skrypt@Eos:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CK8S [NVidia CK8S], device 0: Intel ICH [NVidia CK8S]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK8S [NVidia CK8S], device 2: Intel ICH - IEC958 [NVidia CK8S - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

lspci -v
```
skrypt@Eos:~$ lspci -v
00:00.0 Host bridge: nVidia Corporation nForce3 250Gb Host Bridge (rev a1)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 0300
        Flags: bus master, 66MHz, fast devsel, latency 0
        Memory at e0000000 (32-bit, prefetchable) [size=256M]
        Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation nForce3 250Gb LPC Bridge (rev a2)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 0300
        Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 SMBus: nVidia Corporation nForce 250Gb PCI System Management (rev a1)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 0300
        Flags: 66MHz, fast devsel, IRQ 10
        I/O ports at fc00 [size=32]
        I/O ports at 4c00 [size=64]
        I/O ports at 4c40 [size=64]
        Capabilities: <access denied>

00:02.0 USB Controller: nVidia Corporation CK8S USB Controller (rev a1) (prog-if 10 [OHCI])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 0300
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
        Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:02.1 USB Controller: nVidia Corporation CK8S USB Controller (rev a1) (prog-if 10 [OHCI])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 0300
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
        Memory at fe02e000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:02.2 USB Controller: nVidia Corporation nForce3 EHCI USB 2.0 Controller (rev a2) (prog-if 20 [EHCI])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 0300
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
        Memory at fe02d000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:05.0 Bridge: nVidia Corporation CK8S Ethernet Controller (rev a2)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 0300
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 19
        Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at f000 [size=8]
        Capabilities: <access denied>

00:06.0 Multimedia audio controller: nVidia Corporation nForce3 250Gb AC'97 Audio Controller (rev a1)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7585
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
        I/O ports at ec00 [size=256]
        I/O ports at e800 [size=128]
        Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:08.0 IDE interface: nVidia Corporation CK8S Parallel ATA Controller (v2.5) (rev a2) (prog-if 8a [Master SecP PriP])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 0300
        Flags: bus master, 66MHz, fast devsel, latency 0
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at dc00 [size=16]
        Capabilities: <access denied>

00:09.0 IDE interface: nVidia Corporation CK8S Serial ATA Controller (v2.5) (rev a2) (prog-if 85 [Master SecO PriO])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 0300
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
        I/O ports at 09e0 [size=8]
        I/O ports at 0be0 [size=4]
        I/O ports at 0960 [size=8]
        I/O ports at 0b60 [size=4]
        I/O ports at c800 [size=16]
        I/O ports at c400 [size=128]
        Capabilities: <access denied>

00:0a.0 IDE interface: nVidia Corporation CK8S Serial ATA Controller (v2.5) (rev a2) (prog-if 85 [Master SecO PriO])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 0300
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
        I/O ports at 09f0 [size=8]
        I/O ports at 0bf0 [size=4]
        I/O ports at 0970 [size=8]
        I/O ports at 0b70 [size=4]
        I/O ports at b000 [size=16]
        I/O ports at ac00 [size=128]
        Capabilities: <access denied>

00:0b.0 PCI bridge: nVidia Corporation nForce3 250Gb AGP Host to PCI Bridge (rev a2) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 16
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=10
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: fa000000-fcffffff
        Prefetchable memory behind bridge: d0000000-dfffffff

00:0e.0 PCI bridge: nVidia Corporation nForce3 250Gb PCI-to-PCI Bridge (rev a2) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=128
        I/O behind bridge: 00008000-00008fff
        Memory behind bridge: fdf00000-fdffffff
        Prefetchable memory behind bridge: fde00000-fdefffff

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel

01:00.0 VGA compatible controller: nVidia Corporation NV40 [GeForce 6800 Ultra] (rev a1) (prog-if 00 [VGA])
        Subsystem: nVidia Corporation Unknown device 0205
        Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 21
        Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
        [virtual] Expansion ROM at fc000000 [disabled] [size=128K]
        Capabilities: <access denied>

02:0c.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46) (prog-if 10 [OHCI])
        Subsystem: Unknown device 0574:086c
        Flags: bus master, stepping, medium devsel, latency 32, IRQ 20
        Memory at fdfff000 (32-bit, non-prefetchable) [size=2K]
        I/O ports at 8c00 [size=128]
        Capabilities: <access denied>

```

As far as hardware, i'm running the integrated sound card on the MSI K8Neo motherboard w/ an AMD 3400+

---

### Post by Skrypt on 2007-07-16
Linux gods, hearken my desperate plea!

---

### Post by expatCM on 2007-07-17
As a first step you may want to have a look round alsamixer (launch from the command line) but if that does not work things out this link is a lot of fun
[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)

---

### Post by Skrypt on 2007-07-18
Here's what tsalsa output....

```

.....tsalsa info..Wed Jul 18 10:32:12 EDT 2007....... 	
.....laptop/motheboard/desktop......         MSI K8Neo	
        plugs: 7	
        spdif: y	
        model options: n	
        number of speakers... 6 	
.....distro............... Ubuntu 7.04 \n \lDISTRIB_ID=UbuntuDISTRIB_DESCRIPTION="Ubuntu 7.04"	
.....release.............. lsb-release	
.....System.............. Linux Eos 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux	
.....vendor/dev id.......	
        10de 00ea	
.....vendor/dev module...	
        	
.....vendor/device: 10de:00ea Subsystem: Micro-Star International Co., Ltd. Unknown device 7585	
.....lspci info.........	
	00:06.0 Multimedia audio controller: nVidia Corporation nForce3 250Gb AC'97 Audio Controller (rev a1)	
.....alsa driver........ 1.0.14rc1	
.....alsa lib........... 	
.....alsa utils......... 1.0.13	
.....alsa modules.......	
        snd_intel8x0	
.....snd/soundcore........	
        snd                    54020  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device	
soundcore               8672  1 snd	
.....alsa cards.........	
	 0 [CK8S           ]: NFORCE - NVidia CK8S	
	                      NVidia CK8S with ALC850 at 0xfe02b000, irq 18	
.....codec..............	
0-0/0: Realtek ALC850 rev 0	

PCI Subsys Vendor: 0x1462	
PCI Subsys Device: 0x7585	

.....asoundrc.........	
-rw-r--r-- 1 root root 190 2007-07-17 16:42 /home/skrypt/.asoundrc	
.....lsof output...... 	
	COMMAND     PID   USER   FD   TYPE DEVICE SIZE  NODE NAME	
	mixer_app 17934 skrypt   18u   CHR  116,8      13594 /dev/snd/controlC0	
	mixer_app 22664 skrypt   18u   CHR  116,8      13594 /dev/snd/controlC0	

cardcnt: 0 	
.....amixer item options for card 0 [CK8S]	
  	
'Surround Jack Mode'  ; Item #0 'Shared'  ; Item #1 'Independent'--  : values=off	
'Mic Select'  ; Item #0 'Mic1'  ; Item #1 'Mic2'--  	
'Mono Output Select'  ; Item #0 'Mix'  ; Item #1 'Mic'  : values=0	
'Capture Source'  ; Item #0 'Mic'  ; Item #1 'CD'  ; Item #2 'Video'  ; Item #3 'Aux'  ; Item #4 'Line'  ; Item #5 'Mix'  ; Item #6 'Mix Mono'  ; Item #7 'Phone'--  : values=?	
'IEC958 Playback Source'  ; Item #0 'PCM'  ; Item #1 'Analog In'  ; Item #2 'IEC958 In'--  : values=off	
'Channel Mode'  ; Item #0 '2ch'  ; Item #1 '4ch'  ; Item #2 '6ch'	

.....amixer contents for card 0 [CK8S]	
amixer set 'Master',0 100%,100% on	
amixer set 'Master Mono',0 100% on	
amixer set 'PCM',0 100%,94% on	
amixer set 'Surround',0 100%,100% on	
amixer set 'Surround Jack Mode',0 Items: 'Shared' 'Independent' Item0: 'Shared'	
amixer set 'Center',0 100% on	
amixer set 'LFE',0 100% on	
amixer set 'Line',0 100%,100% on Capture off	
amixer set 'CD',0 100%,100% on Capture off	
amixer set 'Mic',0 100%,Capture off	
amixer set 'Mic Boost (+20dB)',0 off	
amixer set 'Mic Front Input',0 off	
amixer set 'Mic Select',0 Items: 'Mic1' 'Mic2' Item0: 'Mic1'	
amixer set 'Video',0 Capture on	
amixer set 'Phone',0 100%,Capture off	
amixer set 'IEC958',0 on Capture off	
amixer set 'IEC958 Playback AC97-SPSA',0 Mono: 3 100%	
amixer set 'IEC958 Playback Source',0 Items: 'PCM' 'Analog In' 'IEC958 In' Item0: 'PCM'	
amixer set 'PC Speaker',0 100% on	
amixer set 'Aux',0 100%,100% on Capture off	
amixer set 'Mono Output Select',0 Items: 'Mix' 'Mic' Item0: 'Mix'	
amixer set 'Capture',0 Capture 15 100%,Capture 15 100% on	
amixer set 'Mix',0 Capture off	
amixer set 'Mix Mono',0 Capture off	
amixer set 'Channel Mode',0 Items: '2ch' '4ch' '6ch' Item0: '4ch'	
amixer set 'Duplicate Front',0 off	
amixer set 'External Amplifier',0 on	

.....lspci -vn.........	
00:00.0 0600: 10de:00e1 (rev a1)	
	Subsystem: 1462:0300	
	Flags: bus master, 66MHz, fast devsel, latency 0	
	Memory at e0000000 (32-bit, prefetchable) [size=256M]	
	Capabilities: <access denied>	

00:01.0 0601: 10de:00e0 (rev a2)	
	Subsystem: 1462:0300	
	Flags: bus master, 66MHz, fast devsel, latency 0	

00:01.1 0c05: 10de:00e4 (rev a1)	
	Subsystem: 1462:0300	
	Flags: 66MHz, fast devsel, IRQ 10	
	I/O ports at fc00 [size=32]	
	I/O ports at 4c00 [size=64]	
	I/O ports at 4c40 [size=64]	
	Capabilities: <access denied>	

00:02.0 0c03: 10de:00e7 (rev a1) (prog-if 10 [OHCI])	
	Subsystem: 1462:0300	
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16	
	Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]	
	Capabilities: <access denied>	

00:02.1 0c03: 10de:00e7 (rev a1) (prog-if 10 [OHCI])	
	Subsystem: 1462:0300	
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17	
	Memory at fe02e000 (32-bit, non-prefetchable) [size=4K]	
	Capabilities: <access denied>	

00:02.2 0c03: 10de:00e8 (rev a2) (prog-if 20 [EHCI])	
	Subsystem: 1462:0300	
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18	
	Memory at fe02d000 (32-bit, non-prefetchable) [size=256]	
	Capabilities: <access denied>	

00:05.0 0680: 10de:00df (rev a2)	
	Subsystem: 1462:0300	
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 19	
	Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]	
	I/O ports at f000 [size=8]	
	Capabilities: <access denied>	

00:06.0 0401: 10de:00ea (rev a1)	
	Subsystem: 1462:7585	
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18	
	I/O ports at ec00 [size=256]	
	I/O ports at e800 [size=128]	
	Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]	
	Capabilities: <access denied>	

00:08.0 0101: 10de:00e5 (rev a2) (prog-if 8a [Master SecP PriP])	
	Subsystem: 1462:0300	
	Flags: bus master, 66MHz, fast devsel, latency 0	
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]	
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]	
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]	
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]	
	I/O ports at dc00 [size=16]	
	Capabilities: <access denied>	

00:09.0 0101: 10de:00ee (rev a2) (prog-if 85 [Master SecO PriO])	
	Subsystem: 1462:0300	
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16	
	I/O ports at 09e0 [size=8]	
	I/O ports at 0be0 [size=4]	
	I/O ports at 0960 [size=8]	
	I/O ports at 0b60 [size=4]	
	I/O ports at c800 [size=16]	
	I/O ports at c400 [size=128]	
	Capabilities: <access denied>	

00:0a.0 0101: 10de:00e3 (rev a2) (prog-if 85 [Master SecO PriO])	
	Subsystem: 1462:0300	
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17	
	I/O ports at 09f0 [size=8]	
	I/O ports at 0bf0 [size=4]	
	I/O ports at 0970 [size=8]	
	I/O ports at 0b70 [size=4]	
	I/O ports at b000 [size=16]	
	I/O ports at ac00 [size=128]	
	Capabilities: <access denied>	

00:0b.0 0604: 10de:00e2 (rev a2) (prog-if 00 [Normal decode])	
	Flags: bus master, 66MHz, medium devsel, latency 16	
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=10	
	I/O behind bridge: 00009000-00009fff	
	Memory behind bridge: fa000000-fcffffff	
	Prefetchable memory behind bridge: d0000000-dfffffff	

00:0e.0 0604: 10de:00ed (rev a2) (prog-if 00 [Normal decode])	
	Flags: bus master, 66MHz, fast devsel, latency 0	
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=128	
	I/O behind bridge: 00008000-00008fff	
	Memory behind bridge: fdf00000-fdffffff	
	Prefetchable memory behind bridge: fde00000-fdefffff	

00:18.0 0600: 1022:1100	
	Flags: fast devsel	
	Capabilities: <access denied>	

00:18.1 0600: 1022:1101	
	Flags: fast devsel	

00:18.2 0600: 1022:1102	
	Flags: fast devsel	

00:18.3 0600: 1022:1103	
	Flags: fast devsel	

01:00.0 0300: 10de:0040 (rev a1) (prog-if 00 [VGA])	
	Subsystem: 10de:0205	
	Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 21	
	Memory at fa000000 (32-bit, non-prefetchable) [size=16M]	
	Memory at d0000000 (32-bit, prefetchable) [size=256M]	
	Memory at fb000000 (32-bit, non-prefetchable) [size=16M]	
	[virtual] Expansion ROM at fc000000 [disabled] [size=128K]	
	Capabilities: <access denied>	

02:0c.0 0c00: 1106:3044 (rev 46) (prog-if 10 [OHCI])	
	Subsystem: 0574:086c	
	Flags: bus master, stepping, medium devsel, latency 32, IRQ 20	
	Memory at fdfff000 (32-bit, non-prefetchable) [size=2K]	
	I/O ports at 8c00 [size=128]	
	Capabilities: <access denied>	

.....codec info........	
1184681897 1184768882 1184769132 1184769132 1184769132 1184769132	
..........tsalsa end: Wed Jul 18 10:32:12 EDT 2007.....83..............	
```

---

### Post by Skrypt on 2007-07-21
I'm still in need of your assistance.

---

### Post by expatCM on 2007-07-21
What is it that is not working at present?   The sound mixer settings seem to suggest that there should be sound ....

---

### Post by Skrypt on 2007-07-24
[SIZE="6"][COLOR="Red"]Solution[/COLOR][/SIZE]

While ubuntuforums.org did not come to my rescue, a very kind gentlemen in #ubuntu on irc.ubuntu.com:6667 gave me this solution. First, make sure you have the ALSA drivers selected in 
System>Preferences>Sound. Also know that this is a digital setup, not analog. I've got a coaxial cable running into a receiver which handles a 5.1 surround sound.

Open a terminal and enter this:
```

sudo gedit ~/.asoundrc

```
Then enter this into the document (probably blank):
```

 pcm.dmixed {
   type dmix
   ipc_key 1234
   slave.pcm "hw:0,2"
 }
 pcm.!default {
   type plug
   slave.pcm "dmixed"
 }

```
Save it. I'd recommend restarting your computer as well just in case any programs are still running the old configuration.

---

