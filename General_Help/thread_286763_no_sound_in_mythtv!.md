---
title: "no sound in mythtv!"
date: 2006-10-28
forum: General Help
---

### Post by ramiro on 2006-10-28
I've currently got MythTV 0.20 set up on ubuntu edgy. Video works perfectly but there is no sound! There's definitely sound coming into the video capture card, since when I plug my speakers directly into the video capture card audio out I get the sound.

I tried tvtime as well, using every different setting I could think of, but no sound. 

The picture is from a digital cable box, sent via RF cable. I tried sending with other modes but I couldn't even get sound out of the audio out.

I can get sound with ubuntu's sound test if I set it to the analog audio but it's really distorted. Nothing I can do seems to get me any sound with tvtime or with mythtv. 

below is the output of lspci:

```
00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8235 PCI Bridge
00:08.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
00:0a.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
00:0a.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: nVidia Corporation NV25 [GeForce4 Ti 4200] (rev a3)

```

the Bt878 is the video capture card. 

here's the output of dmesg | grep bt

```
[17179586.076000] bttv: driver version 0.9.16 loaded
[17179586.076000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[17179586.076000] bttv: Bt8xx card found (0).
[17179586.076000] bttv0: Bt878 (rev 17) at 0000:00:0a.0, irq: 10, latency: 32, mmio: 0xea022000
[17179586.076000] bttv0: detected: Leadtek WinFast TV 2000 [card=34], PCI subsystem ID is 107d:6606
[17179586.076000] bttv0: using: Leadtek WinFast 2000/ WinFast 2000 XP [card=34,autodetected]
[17179586.076000] bttv0: gpio: en=00000000, out=00000000 in=00bff707 [init]
[17179586.076000] bttv0: using tuner=5
[17179586.076000] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[17179586.080000] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[17179586.080000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[17179586.084000] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[17179586.128000] tuner 1-0061: chip found @ 0xc2 (bt878 #0 [sw])
[17179586.156000] bttv0: registered device video0
[17179586.156000] bttv0: registered device vbi0
[17179586.156000] bttv0: registered device radio0
[17179586.160000] bttv0: PLL: 28636363 => 35468950 .. ok
[17179586.192000] input: bttv IR (card=34) as /class/input/input3
[17179586.192000] bttv-input: bttv IR (card=34) detected at pci-0000:00:0a.0/ir0
[17179587.200000] bt878: AUDIO driver version 0.0.0 loaded

```

please help!

---

### Post by AusIV4 on 2006-10-28
I see you're trying to use btaudio drivers. Are you sure your card supports them? I know mine does not, so I have to run a line from the output on my tuner to the line in of my sound card. Not pretty, but it works.

---

### Post by ramiro on 2006-10-28
well this is the drivers that ubuntu picked for me. It detected my tuner card with no issue (it's a leadtek WinFast TV 2000) so I assume it's picked the right drivers, but I can't be sure of that

If I have to run a line from the output of the tuner to the input of the sound card then that will probably be good enough, although of course it would be better if I could get it direct from the tv tuner. How do I get mythtv to recognise that the sound is coming from the line in?

---

### Post by clayton on 2006-10-29
If you have the the snd_bt87x loaded, it should create /dev/dsp1 (given that your sound card uses /dev/dsp). Try setting your recording device as dsp1 in mythtv-setup. Here's a good link to testing the driver:
[http://www.mythtv.org/wiki/index.php/Snd-bt87x](http://www.mythtv.org/wiki/index.php/Snd-bt87x)

clayton

---

### Post by ramiro on 2006-10-29
yeah I tried both /dev/dsp and /dev/dsp1 as my audio input devices (they are the only ones mythtv has available). no luck. I followed the link and the module is definitely loaded. Everything they say on that site is happening except the line where I'm actually supposed to get sound (copying from /dev/dsp1 to /dev/dsp)

however, in ubuntu's sound preferences I'm able to get the sound when I test the "Bt87x Analog" input device (although it is very poor quality sound, unfortunately). I can't seem to find any way of figuring out what device node it's using to get that but mythtv certainly can't access whatever it is.

---

### Post by superm1 on 2006-10-30
Ramiro,

You can query the devices and what they are assigned to through aplay.

```
aplay -l
```

Once you identify which device is actually being used for audio input, you have to change it in mythtv-setup.  If it doesn't immediately work in mythfrontend, try playing a movie file recorded in another media playback app (totem, vlc, mplayer etc).  This way you can identify where the problem is - recording or playback.

Once its correct in the recording, you can try going into Setup -> General -> Audio

Set the audio output devcie to ```
ALSA:default
```

This isn't an option on the list by default, so type it in.  Set the mixer to the same thing.

---

### Post by eblanton on 2006-11-03
> **ramiro said:**
> I've currently got MythTV 0.20 set up on ubuntu edgy. Video works perfectly but there is no sound! There's definitely sound coming into the video capture card, since when I plug my speakers directly into the video capture card audio out I get the sound.

I tried tvtime as well, using every different setting I could think of, but no sound. 


I have the same problem, ubuntu edgy with a BT878 capture card for which snd-bt87x *does* work (I used it in dapper).  I have as yet to find a solution to this, but I'm still looking.

(To answer the questions posed to ramiro: I have loaded the snd-bt87x module, I have queried it via various alsa commands, and it seems to be working -- I have ensured that capture is turned on in alsamixer.  Sound output for previously recorded video works fine.  xawtv also does not produce sound, and it does not even use btaudio, but I am not 100% sure the internal audio cable is hooked to the sound card.  I believe that it is, in which case this sounds like a mixer problem to me, but I have not had time to check.)

Ethan

---

### Post by eblanton on 2006-11-04
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/29789](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/29789)

Seems to discuss this issue.

---

