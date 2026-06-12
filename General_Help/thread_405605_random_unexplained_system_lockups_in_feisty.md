---
title: "random unexplained system lockups in feisty"
date: 2007-04-10
forum: General Help
---

### Post by zorkerz on 2007-04-10
Since upgrading to feisty about a month ago i have experienced about 5 system freezes. It happens so infrequently i have not been able to locate a cause. When it freezes the mouse does not move and the keyboard is unresponsive. I tried ctrl + alt + backspace with no luck. I was forced to hold the power button down to restart.

One time it locked up except the mouse. This time ctrl + alt + backspace threw it first into a command line except all of the text was blurred as if there were to sets of the same page set about an 1/8th of a character off from each other, then the gnome login screen comes back up. I think this freeze is a separate issue as it only involves an x lockup.

Back to the other complete system freezes.  I do not get any error messages on startup and to not know where to look for appropriate logs. I do not remember exactly what apps i was running on each lockup. Generally i run firefox, gaim, gmail notify, beagle search, and all else is defaults. 

Im not sure what else will be helpful. If/when it happens again i will report back.
any ideas?
thanks

---

### Post by moffa on 2007-04-10
Have you made sure your cpu / video card / motherboard is not overheating?  Are the fans operating normally?

---

### Post by funpop on 2007-04-10
you can run a memtest (choose this option in grub and let it run overnight)
you can check for badblocks on your HD: in a terminal type: 
```
badblocks -vs /dev/[disc, for example hda1]
```
note badblocks needs some hours too, especially if you got a large HD.
and i dont get errors in these tests and still have some freezes. 

i got much more freezes with firefox, with swiftfox they didnt appear so often.

at the moment i only get freezes if i download several large files at the same time, but i can avoid that.

you also can check your syslog for errors.

---

### Post by caryb on 2007-04-10
I have only experienced this with Beryl enabled, is this a possibility for you?

---

### Post by allforcarrie on 2007-04-10
sounds like my problem [http://ubuntuforums.org/showthread.php?t=405993](http://ubuntuforums.org/showthread.php?t=405993)

---

### Post by ElVirolo on 2007-04-10
I have the same problem here...

---

### Post by zorkerz on 2007-04-10
Hi all thanks for the responses. I will run memcheck tonight and check the hard drive with badblocks as soon as possible

How would i check to make sure my cpu and nvidia card are not overheating? oh mobo to?
The fan runs the same as always. In fact once months ago i remember the cpu overheating because the comp was on my bed with no ventilation but ubuntu told me and immediately shut the computer off.

I am not using beryl at the moment I was using desktop effects at one point (compiz i think) but i believe it has frozen either way.

I am currently using fasterfox but don't really see the benefits and have been planning on ditching it.

I see an update to nvidia-glx today if its graphics card related maybe this will help or hurt guess you never know.

Think that covers my bases for now thanks again.

---

### Post by zorkerz on 2007-04-11
Weird experience with memtest.  I use grub to boot into the ubuntu memtest that is installed by default. It starts running fun but after only a short time the computer shuts down. I have not seen any errors but have been away from the comp when it shut down each time.

I am running  "sudo badblocks -vs /dev/sda3" right now and will report back with errors. I am only doing my ext3 partition im hoping it is not necissary to do the fat32 or windows' ntfs.

I have not had a freeze in a couple day so maybe this will just disappear? knock on wood

Any ideas about memtest what could cause it to just shut off? something overheating the fan was running pretty heavily during testing.

Thanks as alway

update: This appears not to be a harddrive issue. I tested sda1, 2, and 3 (my ext3, vfat, and ntfs partitions) all with no errors.

i guess now i will keep attempting to get memtest to work and wait for another freeze.

---

### Post by zorkerz on 2007-04-15
Just had another freeze.
This time gaim, firefox, and rhythmbox were running. I was not at the computer and the allman brothers were playing. At the freeze the music stopped and screen saver froze in place with a little white line running horizontally across the center of the screen. ctrl + alt + backspace did not work again.

Not sure if anyone has any ideas here where can i look to find out more about what is going on. Without any error i don't know where to go.

---

### Post by Spectre5 on 2007-04-17
I am having similar problems (in edgy)...I often run the same programs and have not been able to find a solution myself yet....any ideas?

Edit:  I don't think it is an overheating problem (for me anyways) because I can run the comp for a few days with no problems....then other times I get like 4 freezes in one day.

---

### Post by john_brown_jr on 2007-04-17
You might try posting the output of "lspci" here, most likely there is a problem with a driver for your hardware. 

I had the same problem because of bugs in wireless card (RT61) drivers.

---

### Post by Spectre5 on 2007-04-17
These freezes happen randomly for me and I am using xubuntu 6.10. The only way I have been able to replicate these reliably is via Scite...load a .c file, click compile, then try to resize the scite window = freeze. It freezes as soon as I click the resize corner thing....I was unable to get useful help regarding this at the scite bug reporting site. Although it may be a scite problem, I still get these freezes with scite not installed...


Here is my lspci -v


00:00.0 Host bridge: Intel Corporation 82810E DC-133 GMCH [Graphics Memory Controller Hub] (rev 03)
Flags: bus master, fast devsel, latency 0

00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller] (rev 03) (prog-if 00 [VGA])
Subsystem: Compaq Computer Corporation Unknown device b165
Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 3
Memory at 44000000 (32-bit, prefetchable) [size=64M]
Memory at 40100000 (32-bit, non-prefetchable) [size=512K]
Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02) (prog-if 00 [Normal decode])
Flags: bus master, fast devsel, latency 0
Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
I/O behind bridge: 00001000-00001fff
Memory behind bridge: 40000000-400fffff
Prefetchable memory behind bridge: 20000000-200fffff

00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801AA IDE (rev 02) (prog-if 80 [Master])
Subsystem: Intel Corporation 82801AA IDE
Flags: bus master, medium devsel, latency 0
I/O ports at 2020 [size=16]

00:1f.2 USB Controller: Intel Corporation 82801AA USB (rev 02) (prog-if 00 [UHCI])
Subsystem: Intel Corporation 82801AA USB
Flags: bus master, medium devsel, latency 0, IRQ 11
I/O ports at eec0 [size=32]

00:1f.3 SMBus: Intel Corporation 82801AA SMBus (rev 02)
Subsystem: Intel Corporation 82801AA SMBus
Flags: medium devsel, IRQ 5
I/O ports at eee0 [size=16]

01:05.0 Multimedia audio controller: ESS Technology ES1988 Allegro-1 (rev 10)
Subsystem: Compaq Computer Corporation Unknown device b19d
Flags: bus master, medium devsel, latency 64, IRQ 5
I/O ports at 1000 [size=256]
Capabilities: <access denied>

01:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
Subsystem: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet
Flags: bus master, 66MHz, medium devsel, latency 66, IRQ 3
I/O ports at 1400 [size=256]
Memory at 40000000 (32-bit, non-prefetchable) [size=256]
[virtual] Expansion ROM at 20000000 [disabled] [size=128K]
Capabilities: <access denied>

01:0a.0 Modem: PCTel Inc HSP MicroModem 56 (rev 02) (prog-if 01 [Hayes/16450])
Subsystem: PCTel Inc Unknown device 0001
Flags: medium devsel, IRQ 11
I/O ports at 1800 [size=64]
Capabilities: <access denied>

---

### Post by zorkerz on 2007-04-17
lspci =
> lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation NV41.8 [GeForce Go 6800] (rev a2)
06:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705_2 Gigabit Ethernet (rev 03)
06:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
06:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:09.4 Generic system peripheral [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller


---

### Post by rplantz on 2007-04-17
I have been getting random system freezes since upgrading to:
```

bob@ubuntu:~$ uname -a
Linux ubuntu 2.6.20-15-generic #2 SMP Sun Apr 15 06:17:24 UTC 2007 x86_64 GNU/Linux

```
This was occurring a few weeks ago. It stopped when I cleaned large amounts of dust from my fans, heat sinks, etc. :oops: But this latest upgrade has brought it back. It started when I left for a while. I came back into the room to see the screen saver frozen on my screen. (Thus, not "saving" my screen.) Just this morning, it occurred when I was running Firefox and clicked on the link to get me to the Feisty Fawn discussion forum. Had to restart my system.

My pci devices are:
```

bob@ubuntu:~$ lspci
00:00.0 Host bridge: nVidia Corporation nForce3 250Gb Host Bridge (rev a1)
00:01.0 ISA bridge: nVidia Corporation nForce3 250Gb LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation nForce 250Gb PCI System Management (rev a1)
00:02.0 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
00:02.2 USB Controller: nVidia Corporation nForce3 EHCI USB 2.0 Controller (rev a2)
00:05.0 Bridge: nVidia Corporation CK8S Ethernet Controller (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce3 250Gb AC'97 Audio Controller (rev a1)
00:08.0 IDE interface: nVidia Corporation CK8S Parallel ATA Controller (v2.5) (rev a2)
00:0a.0 IDE interface: nVidia Corporation CK8S Serial ATA Controller (v2.5) (rev a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 250Gb AGP Host to PCI Bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation nForce3 250Gb PCI-to-PCI Bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
02:07.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)
02:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

---

### Post by dafrabbit on 2007-04-17
Also been having these problems, feisty blew up on me last night and I haven't had a chance to reinstall, can one of you disable DRI in your xorg.conf and see if that helps? At least that would help to narrow down the possibilities? To disable DRI, simply open a terminal and type:

sudo gedit /etc/X11/xorg.conf

And scroll to the bottom there should be a section for DRI that's about 3 lines long, just comment out each one.

---

### Post by Digitallysick on 2007-04-17
I have random freezing in feisty fawn, its driving me nuts

00:00.0 Host bridge: Intel Corporation 82925X/XE Memory Controller Hub (rev 0e)
        Subsystem: ABIT Computer Corp. Unknown device 103e
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82925X/XE PCI Express Root Port (rev 0e) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: fa000000-fcffffff
        Prefetchable memory behind bridge: c0000000-dfffffff
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
        Subsystem: ABIT Computer Corp. Unknown device 103e
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at fdff8000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04) (prog-if 00 [UHCI])
        Subsystem: ABIT Computer Corp. Unknown device 103e
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at ff00 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04) (prog-if 00 [UHCI])
        Subsystem: ABIT Computer Corp. Unknown device 103e
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at fe00 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04) (prog-if 00 [UHCI])
        Subsystem: ABIT Computer Corp. Unknown device 103e
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at fd00 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04) (prog-if 00 [UHCI])
        Subsystem: ABIT Computer Corp. Unknown device 103e
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at fc00 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04) (prog-if 20 [EHCI])
        Subsystem: ABIT Computer Corp. Unknown device 103e
        Flags: bus master, medium devsel, latency 0, IRQ 18
        Memory at fdfff000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d4) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: fdd00000-fddfffff
        Prefetchable memory behind bridge: 00000000fde00000-00000000fdefffff
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 04)
        Subsystem: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge
        Flags: bus master, medium devsel, latency 0

00:1f.2 IDE interface: Intel Corporation 82801FR/FRW (ICH6R/ICH6RW) SATA Controller (rev 04) (prog-if 80 [Master])
        Subsystem: Intel Corporation 82801FR/FRW (ICH6R/ICH6RW) SATA Controller
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 17
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at fb00 [size=16]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
        Subsystem: ABIT Computer Corp. Unknown device 103e
        Flags: medium devsel, IRQ 11
        I/O ports at 0500 [size=32]

01:00.0 VGA compatible controller: nVidia Corporation NV42 [Geforce 6800 XT] (rev a2) (prog-if 00 [VGA])
        Subsystem: XFX Pine Group Inc. Unknown device 2177
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
        Memory at c0000000 (64-bit, prefetchable) [size=512M]
        Memory at fb000000 (64-bit, non-prefetchable) [size=16M]
        [virtual] Expansion ROM at fc000000 [disabled] [size=128K]
        Capabilities: <access denied>

02:01.0 Ethernet controller: Intel Corporation 82541GI Gigabit Ethernet Controller (rev 05)
        Subsystem: ABIT Computer Corp. Unknown device 103e
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 16
        Memory at fdda0000 (32-bit, non-prefetchable) [size=128K]
        Memory at fddc0000 (32-bit, non-prefetchable) [size=128K]
        I/O ports at ef00 [size=64]
        [virtual] Expansion ROM at fde00000 [disabled] [size=128K]
        Capabilities: <access denied>

02:02.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10 [OHCI])
        Subsystem: ABIT Computer Corp. Unknown device 103e
        Flags: bus master, medium devsel, latency 32, IRQ 21
        Memory at fddff000 (32-bit, non-prefetchable) [size=2K]
        Memory at fddf8000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

02:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE Ethernet Controller (rev 04)
        Subsystem: ABIT Computer Corp. Unknown device 103e
        Flags: bus master, medium devsel, latency 32, IRQ 20
        Memory at fddfe000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at ee00 [size=64]
        Capabilities: <access denied>

---

### Post by Spectre5 on 2007-04-18
I tried turning off DRI, but I still get the freezes :(

Any other ideas dafrabbit?

---

### Post by sgt-pluck on 2007-04-18
I had a few freezes - probably about 3 over the space of a month - I also put it down to the beta status.  Same symptoms - everything justs locks up, no response from anything other than holding down the power button.  ATI graphix with 'radeon' generic driver, unhacked install of Ubuntu.  Last time it happened I was clicking a link in Firefox.

I don't think it's got anything to do with overheating because my laptop generally runs very cool, plus I've noticed the fan coming on more with Ubuntu than it does with windows.

I'll wait for it to happen again and see if I can figure out scenarios in which it occurrs.  I'll run that badlock thing also.

---

### Post by zorkerz on 2007-04-18
Well im glad there are at least a few of us experiencing similar problems. That may we are more likely to find a solution. Not that we are very close yet without any serious leads or even a way to see if we are all having the same problem.

Im worried that if this is a feisty beta bug it will also be a final bug. Seeing as feisty is due tomorrow now and we have not figured out a solution let alone a cause.

Oh well. It will go away or get solved at  some point.

gnight all

---

### Post by meteorain on 2007-04-18
I'm experiencing a lot of freezes in Feisty too. I had no problems in Edgy. This is the output of lspci: 
```

00:00.0 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. PT894 I/O APIC Interrupt Controller
00:00.7 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. PT890 PCI to PCI Bridge Controller
00:0c.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 06)
00:0c.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 06)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
02:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 GT] (rev a2)

```

---

### Post by Digitallysick on 2007-04-18
So far i have just turned off beryl , and im on day 2 with no freezes "yet"  I have an xfx6800 graphics card, dont know if its a beryl problem or what,im going to see how it goes for a few weeks without beryl

---

### Post by dafrabbit on 2007-04-18
Sorry spectre5, that was the one idea I was planning on trying. =(

In any case, it seems like there's a whole bunch of us with random freezes, and no real common cause? For some of us, freezes stop after turning off beryl/desktop effects, others freezes stop when turning off DRI, and some of us just get freezes all the time, regardless of computer temperature....What kinds of hardware are we all running?

---

### Post by zorkerz on 2007-04-18
I think thats what the lspci command does but im not sure anyone is looking at them or what we should be looking for. Possibly we all have something in common?

---

### Post by hollows2 on 2007-04-18
I have had the same problem - everything freezes then runs ok then freezes again etc. Try checking the /var/log/messages file for any relevant info.

My problem appears to be with acpi [ the fan will not turn off ].

If I run :-
                      sudo modprobe -r thermal
followed by
                      sudo modprobe thermal

everything resets and works ok.

Steve

---

### Post by Bill_Gates on 2007-04-18
Same here. I have hard lockups when i'm watching videos on kaffeine with beryl activated. My graphic card is an intel gma 950.

---

### Post by Toadmund on 2007-04-18
I just surf the net, no music, nothing else and I get 1 or 2 crashes a day or few as 5 crashes a week.
I either get a solid white screen when I go to another page, no borders, nothing but white, OR, I get Vertical 'Ubuntu Brown' bars across the screen.

CTRL+ALT+BackSpace doesn't work, must do a hard reset.

Just wondering if some of you get that.

---

### Post by m2.g5ru6y7s on 2007-04-18
I HAD the same issues as above
Al my problems disappeared when I bought a new pc. 
The laptop had thermal issues. Most laptops, when they become older are getting thermal issues. 
This is the main reason when I bought a desktop pc. Not the fastest, not the slowest (intel DQ965gf with Intel Dual Core 2,4 G ). Then you can work easily long and hard without thermal problems. As a matter of fact I never shut it down anymore. Only a new kernel release force me to reboot my friend.

---

### Post by Toadmund on 2007-04-18
Believe me, it's not thermal problems, my comp reads 19.5 Celsius, the air in the room is 9.9 Celsius. :shock: 
I can chill beer with my fingers, I can see my breath!
My comp. is a PC, not a laptop, MOBO MSI rs480 with ATI xpress200g integrated graphics.

---

### Post by m2.g5ru6y7s on 2007-04-18
> **Toadmund said:**
> Believe me, it's not thermal problems, my comp reads 19.5 Celsius, the air in the room is 9.9 Celsius. :shock: 
I can chill beer with my fingers, I can see my breath!
My comp. is a PC, not a laptop, MOBO MSI rs480 with ATI xpress200g integrated graphics.
Hmmm weird indeed.
Have you tried another pc?
I know it sounds simple, but then you compare hardware with hardware. You can rip piece by piece till you see the anomaly... Sorry cannot give anymore hints this time. 
Very good luck. ... May the Ubuntu gods with you ...

---

### Post by zorkerz on 2007-04-18
Do all pc/notebooks come with thermometers and if so how can i check my cpu's temperature?

---

### Post by m2.g5ru6y7s on 2007-04-18
> **zorkerz said:**
> Do all pc/notebooks come with thermometers and if so how can i check my cpu's temperature?

It is not easy to see the temperature but of you are lucky try the following:
 
find /proc -type f -iname '*term*' -exec cat {} \; 2>/dev/null
It print any temperature if found in /proc 

You can also try the package
lmsensors:

[http://ubuntuforums.org/showthread.php?t=2780](http://ubuntuforums.org/showthread.php?t=2780)

Good luck!

---

### Post by Toadmund on 2007-04-18
Just thinking, my Temp. probe reads (read) 19.5 around the vicinity of the CPU, but that's not to say that there may not be a nice insulating layer of dust somewhere blanketing in heat?
I guess I'll have to add 'blow out computer with canned air' to the list of 'to do' things this weekend.
Couldn't hurt.

---

### Post by Spectre5 on 2007-04-19
Everyone seems to have this problem with fiesty....but  I am on Edgy and have it!!

Anyways....maybe some people would like to try this.....(this makes my computer freeze EVERY time I do it....it happens at other times but randomly.,...like it  just happened a minute ago when I pressed a link in firefox)

Install Scite
Load a random .c file (don't care if it successfully compiles or not)
Compile it
Try to resize the window


That freezes my machine every time...if this also freezes EVERYONES machine that is experiencing this problem...then we can look into that source code and possibly find out what line(s) are causing the problem (perhaps a GTK bug or something)

I hope we can find this root of this problem..it is driving me nuts...

---

### Post by kingmob on 2007-04-19
Just like to say i have the same problem in edgy. Not running beryl.
Cost me an hour of work just now :|

I'd like to add that it seems rather random, often it happens when i'm not really doing anything at all. Mouse and keyboard freezes, amarok stops playing. It really just 'freezes'

---

### Post by zorkerz on 2007-05-01
Hey everyone I just noticed this thread has been closed for a while probably since feisty came out. Its been moved and reopened. Anyone still having freezes? I just did today except with a slight twist (possibly a lead to our problem?) that i made a new post [here.]("http://ubuntuforums.org/showthread.php?t=430162")

I have been thinking about filing some sort of bug but am unsure if we have anything to really report. Has anyone filed or found a related bug?

cheers all

---

### Post by skmassey on 2007-05-02
I've been having almost this exact problem.  My machine hangs often when there is 3D rendering.  I just installed feisty, I switched over from Arch to give ubuntu a go again.  The first few days I didn't crash.  But after some updates and I installed beryl, the crashing began on the screensaver.  Now I have noticed that when I'm running OpenGL applications, namely games, it hangs as well.  When these crashes occur I have noticed that I can SSH from my laptop and get a terminal.  When I run top, Xorg is using 99.9% of my CPU.  When I try to kill Xorg, it hangs my machine.  I have also tried:
```
sudo reboot
sudo shutdown now -h
```
when X is shutdown the machine hangs.  When Beryl is running, it seems like my machine locks up more.  I don't know what's going on :confused:

---

### Post by Digitallysick on 2007-05-02
I have just given up, and i turn beryl off, only way i can prevent a system freeze. Like everyone else the system keeps running (if im playing music etc) , but the screen is froze, i can move only the mouse.

---

### Post by skmassey on 2007-05-03
So not running beryl works for you?  I'm not running beryl atm but I still have it installed, I guess I'll try removing it and XGL.  Its too bad though, I rather like beryl.

---

### Post by Digitallysick on 2007-05-03
yeah if i just leave beryl off, i'm fine, and have no issues. What graphics card do you have?  I have a geforce 6800 xtreme

---

### Post by skmassey on 2007-05-05
Mine's a Radeon 9600XT.  No matter what I do I can't get rid of the lockups.  They only happen when I'm running 3d apps.  What sucks for me is that I'm a gamer =\.  Under Arch my video card ran just fine so I know it isn't hardware.  This is a really frustrating bug especially considering there seems to be nothing I can do about it.  :(

---

### Post by tetrisj on 2007-05-05
Hi,
I'm having the same problems in Feisty.
One thing I've noticed was that if i press the reboot button on the computer itself - i get the reboot dialog (the one with suspend, hibernate and all that)
I can't click on anything or press the keyboard but it still shows this dialog.
Another thing is that i can still see the cursor blinking in Eclipse.
This never happened in Edgy, and never happens in Windows.

btw. i think all of us have NVIDIA display adapters. did anyone encounter this problem with ATI?

my lscpi:
00:00.0 Host bridge: Intel Corporation 82946GZ/PL/GL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82946GZ/PL/GL PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 7300 LE (rev a1)
05:01.0 Multimedia audio controller: Creative Labs SB Audigy LS
05:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 01)

---

### Post by zorkerz on 2007-05-06
Just had another complete lockup requiring a hard reboot. This time i was playing an mkv file in totem. I don't think i have come across this formate before possibly it is related.

I am also using an nvidia card. Is there anyone experiencing system freezes that is not using an nvidia card. That would narrow down our problem drastically.

---

### Post by dav9000 on 2007-05-07
I have had the same problems since I installed Feisty (everything was running fine in Edgy). The system hangs but sometimes the mouse cursor can be moved, although the keyboard is completely locked, so I have to hold the power button down to restart. Even music continues to play with the system hung. I checked in our Spanish forum

[http://www.ubuntu-es.org/index.php?q=node/43592](http://www.ubuntu-es.org/index.php?q=node/43592)

and came across the solution from jolode (gracias, tío). Since then I have had no lockups. All I did was to switch off three services: apmd, acpid and powernowd. My system (ACER Aspire 1694 WLMi Centrino 2Ghz 1Gb RAM ATi Mobility X600) now is running like a charm even with Beryl, and do not know the effects of turning these services off, since the laptop makes CPU scaling and all the stuff right. However I did not try suspend, I guess it will not work but I don't need it. I suposse all these problems are kernel related, so we will have to wait for another revision of it.

By the way, other people managed to avoid lockups by disabling other services like vbesave.

Hope it helps.

---

### Post by zorkerz on 2007-05-07
Cool im going to start trying this out. What do these services do? Others had luck with this. Maybe we can narrow it down and see which one is causing th freezing.

---

### Post by Cappy on 2007-05-09
I had a similar problem so I'll add it to the list. I was going line by line through dmesg and I found a message when my computer first boots up:

[ 0.000000] Nvidia board detected. Ignoring ACPI timer override.
[ 0.000000] If you got timer trouble try acpi_use_timer_override

I used this acpi_use_timer_override on the kernel arguments and I havn't had a "lockup" in 24 hours. Sweet!
(I had tried every other solution in here and nothing helped)

---

### Post by mdkaneda55 on 2007-05-20
same crap happening here, glad i found this thread... going to try everything suggested, i was actually about to format and go back to dapper since that worked so well for me in the past. i'm actually in windows because it's WAY more stable than my fiesty install right now! & i can rule out overheating and all of that mumbo jumbo, because i can keep XP running for weeks at a time doing multipass xvid encodes n such (sometimes even WHILE using VLC to play movies on my tv) but fiesty crashes during common webbrowsing or watching a movie in totem, but its never consistant, sometimes things are working great, and when i least expect it.. boom, its froze... i really hope these solutions help, because i'm at my wit's end. thought it was my video drivers (even tho everything seemed to be fine) purged all related packages, deleted synaptic saved *.debs, redownloaded/reinstalled, but problems persist, thought it was my new wifi card, completely removed it from my system, didn't help. i even lost data on a fat32 partition because i guess it was being accessed at the time of a crash, that really sucked bad. Oh, and another bad thing... now my girlfriend hates linux. lol.

---

### Post by mdkaneda55 on 2007-05-20
Well, i thought things were solved w/ the solutions on this page. but less than 12hrs later, crash. this is getting sickening. everything worked great, but while encoding a movie using mencoder, 45% and it crashed. completely nonresponsive. i thought for sure that kernel option was doing the trick!! but i guess not.

---

### Post by zorkerz on 2007-05-23
Lockup again with frozen mouse requiring a hard restart. I just installed ubuntu fresh I was hoping these would go away. I was running firefox, the terminal, and nautilus in gnome only.

I think if there are no bug reports on this im going to file one anyway even though we have little info.

Update: launchpad [bug # 116456]("https://bugs.launchpad.net/ubuntu/+bug/116456") check it out maybe we can get some help

---

### Post by mdkaneda55 on 2007-05-24
alright! getting excited, hope something comes of the bug report! i thought i might be the only one still experiencing this, but its crazy, tried running Mandriva 2007.1 Spring and i had the same issues! i reinstalled Fiesty and got the same crap. its nuts though, its like i can get through everything (3 hours setting up/configuring system) and THEN it goes. i wonder if it has something to do with an update? i purposefully tried to avoid using the proprietary video driver, but even without installing it, i still get lockups! last thing i tried was switching to the linux-server package, haven't gotten a crash in it yet, but i'm afraid to use it too much in fear. it can happen at random for me, but much more frequently when doing video encoding / heavy processor-load... seems to be either during an encode, or at random soon after a reboot. I even tried updating my Bios to the latest Beta, but that had many more ill effects, heh.

---

### Post by meteorain on 2007-05-26
I solved my problems with the random freezes following this HOWTO: [http://ubuntuforums.org/showthread.php?t=75281](http://ubuntuforums.org/showthread.php?t=75281)

In my case adding the "noapic nolapic" options at boot did the trick.

Hope this helps somebody else

---

