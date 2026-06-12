---
title: "No sound in Hardy"
date: 2008-04-26
forum: General Help
---

### Post by IgnacioMiller on 2008-04-26
Hey all,

I just did a fresh install of Ubuntu 8.04 (64-bit) on my computer. Everything works save for the sound on my system. I changed the device to my soundcard, a Soundblaster Live! 24 bit, but it still had no playback. I then selected every track/channel and unmuted/raised the volume on each one. I turned the IEC958 switch on too. I also went into alsamixer, selected my card and tried to see if there were any channels still muted and there were not.

Here is my output of lspci -v:
```
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
	Subsystem: ASUSTeK Computer Inc. A8N-VM CSM Mainboard
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
	Subsystem: ASUSTeK Computer Inc. A8N-VM CSM Mainboard
	Flags: 66MHz, fast devsel

00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
	Subsystem: ASUSTeK Computer Inc. A8N-VM CSM Mainboard
	Flags: 66MHz, fast devsel

00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
	Subsystem: ASUSTeK Computer Inc. A8N-VM CSM Mainboard
	Flags: 66MHz, fast devsel

00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
	Subsystem: ASUSTeK Computer Inc. A8N-VM CSM Mainboard
	Flags: bus master, 66MHz, fast devsel, latency 0

00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
	Subsystem: ASUSTeK Computer Inc. A8N-VM CSM Mainboard
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
	Subsystem: ASUSTeK Computer Inc. A8N-VM CSM Mainboard
	Flags: 66MHz, fast devsel

00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
	Subsystem: ASUSTeK Computer Inc. A8N-VM CSM Mainboard
	Flags: 66MHz, fast devsel

00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Capabilities: <access denied>

00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Capabilities: <access denied>

00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: fa900000-fe9fffff
	Prefetchable memory behind bridge: 00000000bff00000-00000000dfefffff
	Capabilities: <access denied>

00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
	Subsystem: ASUSTeK Computer Inc. A8N-VM CSM Mainboard
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a2)
	Subsystem: ASUSTeK Computer Inc. A8N-VM CSM Mainboard
	Flags: bus master, 66MHz, fast devsel, latency 0

00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a2)
	Subsystem: ASUSTeK Computer Inc. A8N-VM CSM Mainboard
	Flags: 66MHz, fast devsel, IRQ 5
	I/O ports at 0600 [size=64]
	I/O ports at 0700 [size=64]
	Capabilities: <access denied>

00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2) (prog-if 10 [OHCI])
	Subsystem: ASUSTeK Computer Inc. A8N-VM CSM Mainboard
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at febbe000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2) (prog-if 20 [EHCI])
	Subsystem: ASUSTeK Computer Inc. A8N-VM CSM Mainboard
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at febbfc00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1) (prog-if 8a [Master SecP PriP])
	Subsystem: Unknown device f043:81bc
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at ffa0 [size=16]
	Capabilities: <access denied>

00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
	Subsystem: ASUSTeK Computer Inc. A8N-VM CSM Mainboard
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	I/O ports at e800 [size=8]
	I/O ports at e480 [size=4]
	I/O ports at e400 [size=8]
	I/O ports at e080 [size=4]
	I/O ports at e000 [size=16]
	Memory at febbd000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
	Subsystem: ASUSTeK Computer Inc. A8N-VM CSM Mainboard
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	I/O ports at dc00 [size=8]
	I/O ports at d880 [size=4]
	I/O ports at d800 [size=8]
	I/O ports at d480 [size=4]
	I/O ports at d400 [size=16]
	Memory at febbc000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=64
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: fea00000-feafffff
	Capabilities: <access denied>

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
	Subsystem: nVidia Corporation A8N-VM CSM Mainboard
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at febb8000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a1)
	Subsystem: ASUSTeK Computer Inc. A8N-VM CSM Mainboard
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at febb7000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at d080 [size=8]
	Capabilities: <access denied>

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel

03:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7900 GS] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: eVga.com. Corp. Unknown device c624
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Memory at fc000000 (64-bit, non-prefetchable) [size=16M]
	I/O ports at bc00 [size=128]
	[virtual] Expansion ROM at fe9e0000 [disabled] [size=128K]
	Capabilities: <access denied>

04:05.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80) (prog-if 10 [OHCI])
	Subsystem: ASUSTeK Computer Inc. A8V Deluxe or A8N-VM CSM Mainboard
	Flags: bus master, medium devsel, latency 64, IRQ 19
	Memory at feaff800 (32-bit, non-prefetchable) [size=2K]
	I/O ports at cc00 [size=128]
	Capabilities: <access denied>

04:08.0 FireWire (IEEE 1394): NEC Corporation uPD72874 IEEE1394 OHCI 1.1 3-port PHY-Link Ctrlr (rev 01) (prog-if 10 [OHCI])
	Subsystem: NEC Corporation uPD72874 IEEE1394 OHCI 1.1 3-port PHY-Link Ctrlr
	Flags: bus master, medium devsel, latency 64, IRQ 18
	Memory at feafe000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

04:09.0 Multimedia audio controller: Creative Labs SB Audigy LS
	Subsystem: Creative Labs SB0410 SBLive! 24-bit
	Flags: bus master, medium devsel, latency 64, IRQ 17
	I/O ports at c880 [size=32]
	Capabilities: <access denied>

```

Here is my output of aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Thanks for the help!

---

### Post by Sleaka J on 2008-04-26
I had an extremely similar problem when I installed 8.04.

As I own a Creative Audigy card, by default the digital output on the card is enabled. Once I disabled the digital output, I got sound.

Assuming you're using Gnome, right-click on your speaker icon and choose "Open Volume Control". The 2nd tab "Switches" is where the digital output is located. I had to turn mine off.

---

### Post by IgnacioMiller on 2008-04-26
Unfortunately the only switch I have is IEC958. Unless there is a way to enable the digital output switch I don't think I can disable it. Thanks for the reply though!

---

### Post by RainCT on 2008-04-26
I'm not sure if this will help but you could try changing the sound server in System -> Applications -> Sound to the different options available.

---

### Post by IgnacioMiller on 2008-04-26
I think you meant system>preferences>sound, and I tried changing the music movies to every device/sound server that was available and tested each one. OSS and ALSA threw this error:

```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Could not open audio device for playback. Device is being used by another application.
```

The various devices and the Pulseaudio sound server proceeded with no error, but also no sound.

Thanks for the reply!

---

### Post by IgnacioMiller on 2008-04-27
Bump! I can't seem to figure this one out.

---

### Post by IgnacioMiller on 2008-04-27
Interestingly enough, it plays the three drum beats when the login screen appears when turning the computer on, but no other sounds.

---

### Post by atomicscissors on 2008-04-27
I've just upgraded from 7.10 on a bone stock HP Pavilion a230n and am getting sound from embedded video on the Internet but no output from media files on my computer.  I've tried everything here but no dice.  :(

---

### Post by miwaypet on 2008-04-27
Make sure the package libflashsupport has been installed. Find out by checking in synaptic. Sometimes that is the problem. Hope it helps.

---

### Post by IgnacioMiller on 2008-04-27
I installed that package and I am still not getting any sound upon restart. Thanks for the reply!!

---

### Post by amirinamdar on 2008-05-03
IgnacioMiller, any progress on this? I have exactly the same problem since I upgraded to Hardy 2 days ago...looked at all posts on this topic, even though I am a newbie to linux, but no luck!

Cheers!

---

### Post by Happibun on 2008-05-03
My problem is that I have no sound playback from any of the multimedia programs. My sound chip is working, I can hear system beeps and stuff that is streamed online through firefox, though that suffers from drop outs and clicks that other users have reported elsewhere. If I try and play a CD or anything through Amarok or Rhythmbox or any of the other sound and video programs, I have no sound at all.

I've just upgraded to Hardy Heron 8.04 from Gutsy, and I had no problem like this in Gutsy.

I am using a Dell Latitude 120L laptop, so it's a really basic set up and I have no separate sound card.

If I 
> :~$ aplay -l

**** List of PLAYBACK Hardware Devices ****

card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]

  Subdevices: 1/1

  Subdevice #0: subdevice #0

and

> :~$ lspci -v


Amongst a whole lot of other things, brings up this :

00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)

	Subsystem: Dell Unknown device 01cb

	Flags: bus master, fast devsel, latency 0, IRQ 16

	Memory at dfebc000 (64-bit, non-prefetchable) [size=16K]

	Capabilities: <access denied>

Which to be honest, does not mean an awful lot to me. *Sigh* :confused:

I use Gnome as default because I'm still a wet behind the ears noob user trying to get used to one flavour of Linux before I branch out.

I've right clicked the speaker icon and enabled 'open volume control', I've downloaded and installed libflashsupport through the synaptic package manager, and that ain't fixed it. Alsamixer
 brings up 3 mixer controls, none of them muted..

My brain hurts. Can anyone help? 

Thanks

---

### Post by Black_Monkey on 2008-05-03
I'm having the same problem as the original poster - using the same motherboard. I did 'sudo alsa reload' then 'sudo /etc/init.d/alsa-utils restart', and sound worked fine. Then, after rebooting, sound is gone again, and those commands don't work - the first one tells me "(failed: modules still loaded: snd-hda-intel snd-hwdep snd-pcm snd-page-alloc snd-timer)". This reboot was after upgrading to 2.6.24-17 kernel, though I don't know if that affected it.

---

### Post by mormor on 2008-05-19
small bump. Suddenly my system joined in on this mess to. Will try poking blindly at settings etc, but if someone knows what may cause this and how to resolve it I would be thankfull as I doubt I will figure it out on my own. My system had sound last night btw. And I really dont know what I may have done to it? Last time I had sound where at some videosite at teh internet. ff3 btw. But it couldnt be... could it?

---

### Post by Happibun on 2008-05-25
> **Black_Monkey said:**
>  I did 'sudo alsa reload' then 'sudo /etc/init.d/alsa-utils restart', and sound worked fine. 

Thanks Black Monkey, that patch has sorted it out, though I've not seen if it carries on OK after a reboot. What would the permanent fix be if it didn't?

All the best. Jo

---

### Post by Black_Monkey on 2008-05-31
I haven't found a permanent solution, but after every boot, type
```
sudo /etc/init.d/alsa-utils reset
```
and it will work fine.

---

### Post by KuroYoma on 2008-10-27
My problem isn't exactly te same but when i use the alsa code above i get this

kuro@kuro-laptop:~$ sudo alsa reload
sudo: unable to resolve host kuro-laptop
[sudo] password for kuro: 
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/kuro/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: (none loaded).
Loading ALSA sound driver modules: (none to reload).
kuro@kuro-laptop:~$ sudo /etc/init.d/alsa-utils restart
sudo: unable to resolve host kuro-laptop
 * Shutting down ALSA...                                                 [ OK ] 
 * Setting up ALSA...                                                    [ OK ] 
kuro@kuro-laptop:~$

---

