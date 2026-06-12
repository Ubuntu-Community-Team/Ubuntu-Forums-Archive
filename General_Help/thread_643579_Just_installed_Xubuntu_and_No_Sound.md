---
title: "Just installed Xubuntu and No Sound?"
date: 2007-12-17
forum: General Help
---

### Post by alexv305 on 2007-12-17
Just installed Xubuntu and I love it. Its superfast and easy to use. I have no sound though, I have a DFI Lanparty SLI Expert mobo if that helps. I don't know what to do to enable sound..

Any suggestions?

---

### Post by mali2297 on 2007-12-18
Copy/paste this into the terminal:
```

aplay -vv /usr/share/firefox/res/samples/test.wav

```
Do you hear anything?

If not, post the output of
```

uname -a
aplay -l
lspci -v | grep -A 5 [Aa]udio

```

---

### Post by chrinabuntu on 2008-01-02
I have the same problem.  I did what the first guy was told to do...my output says no sound card found.  Of course, it worked before the X.

My output for the two things together seems to show that it cannot find my sound card:

chrinamint@ubuntudeliz:~$ aplay -vv /usr/share/firefox/res/samples/test.wav
ALSA lib confmisc.c:769:(parse_card) cannot find card ''
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3982:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM default
aplay: main:545: audio open error: No such device
chrinamint@ubuntudeliz:~$ uname -a
Linux ubuntudeliz 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux
chrinamint@ubuntudeliz:~$ aplay -l
aplay: device_list:204: no soundcards found...
chrinamint@ubuntudeliz:~$ lspci -v | grep -A 5 [Aa]udio

---

### Post by mali2297 on 2008-01-03
Hi.

Was there no output from the last command? In that case, check the output of
```

lspci -v

```
and see if you can find your sound card in the list.

From this [guide]("http://ubuntuforums.org/showthread.php?t=205449"),
> 
If it is not listed, then there are a few things that you can do.

    *      If your soundcard is an onboard sound card, then it might be disabled in the system's BIOS. You will have to reboot and hit the key that lets you enter into the BIOS (usually Delete, F2, or F8).
    *      If your soundcard is not onboard, make sure that it is properly seated in the PCI slot. If your card is working under Windows then this is not a problem.


---

### Post by chrinabuntu on 2008-01-03
Hey Mali...output of lspci -v is:

00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (AGP disabled) (rev 03)
	Subsystem: Compaq Computer Corporation Unknown device 0464
	Flags: bus master, medium devsel, latency 64
	Memory at 50000000 (32-bit, prefetchable) [size=256M]

00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
	Flags: bus master, medium devsel, latency 0

00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01) (prog-if 80 [Master])
	Flags: bus master, medium devsel, latency 64
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at 1020 [size=16]

00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01) (prog-if 00 [UHCI])
	Flags: bus master, medium devsel, latency 64, IRQ 11
	I/O ports at 1000 [size=32]

00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
	Flags: medium devsel, IRQ 9

00:08.0 VGA compatible controller: Chips and Technologies F69000 HiQVideo (rev 64) (prog-if 00 [VGA])
	Subsystem: Compaq Computer Corporation Unknown device b101
	Flags: stepping, medium devsel
	Memory at 40000000 (32-bit, non-prefetchable) [size=16M]
	[virtual] Expansion ROM at 20000000 [disabled] [size=256K]

00:11.0 CardBus bridge: Texas Instruments PCI1220 (rev 02)
	Subsystem: Compaq Computer Corporation Unknown device b047
	Flags: bus master, medium devsel, latency 168, IRQ 11
	Memory at 7fffe000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=00, secondary=01, subordinate=04, sec-latency=176
	Memory window 0: 10000000-13fff000 (prefetchable)
	Memory window 1: 14000000-17fff000
	I/O window 0: 00001400-000014ff
	I/O window 1: 00001800-000018ff
	16-bit legacy interface ports at 0001

00:11.1 CardBus bridge: Texas Instruments PCI1220 (rev 02)
	Subsystem: Compaq Computer Corporation Unknown device b047
	Flags: bus master, medium devsel, latency 168, IRQ 11
	Memory at 7ffff000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=00, secondary=05, subordinate=08, sec-latency=176
	Memory window 0: 18000000-1bfff000 (prefetchable)
	Memory window 1: 1c000000-1ffff000
	I/O window 0: 00001c00-00001cff
	I/O window 1: 00002000-000020ff
	16-bit legacy interface ports at 0001

05:00.0 Network controller: RaLink RT2561/RT61 802.11g PCI
	Subsystem: Belkin Unknown device 701e
	Flags: bus master, slow devsel, latency 64, IRQ 11
	Memory at 1c000000 (32-bit, non-prefetchable) [size=32K]
	Capabilities: <access denied>

I mean, it's an older Compaq Armada 3500 laptop...but it worked fine in Windows.  Well...when I say 'fine'...you know what I mean.  LOL!  As much as anything works "fine" in Windows!

---

### Post by mali2297 on 2008-01-03
These [specs]("http://h18000.www1.hp.com/products/quickspecs/10013_div/10013_div.html") say that you should have
> 
Integrated 16-bit Sound Blaster Pro-compatible audio

Does that seem right?

Did you check the BIOS settings as suggested in post #4?

---

### Post by chrinabuntu on 2008-01-04
I have tried and tried to get to the BIOS screen...I know I've done it before on this laptop, but nothing I hit has led me to the BIOS again.  I had another friend suggest I apt-get pnputils, and I did that, and restarted...but still no sound.

I will try again to get into the BIOS.  I don't know whether that sounds right or not, since it's a laptop and I can't really see the sound card...I also didn't have much luck finding out from Compaq.  Hmph!  

I've never had any trouble with it tho...only since this install of 'X'.  I checked other people's sound problem posts and a lot of them have sound accidentally muted or turned way down...mine actually gives error of no sound device, and movies won't even play because it says sound card is busy.  Weird, since it also says there is no card!

---

### Post by scizzo on 2008-01-04
Does it seem like the file is being played when you try to run it?

I mean is it only the sound that is not being heard and the file is being played?

If it does then maybe the soundcard does not like the fact that it is running a soundserver?

---

### Post by chrinabuntu on 2008-01-04
[SOLVED] (for me anyway)...my friend had me do another check of my installed devices since doing the pnputils install...found what the sound card was supposed to be and then edited the boot module to include the card. ('course, now the video is screwed up...but right now I don't even care!)

Now it's working!!  Woo-hoooo!!!  Kenny, you're the bomb!

Thank you all for your help!

---

