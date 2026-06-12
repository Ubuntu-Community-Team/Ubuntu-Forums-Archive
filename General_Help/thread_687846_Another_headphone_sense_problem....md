---
title: "Another headphone sense problem..."
date: 2008-02-04
forum: General Help
---

### Post by Dbugger on 2008-02-04
Hello! First post! (I think)

I've just installed Gutsy (great distribution) but I have a problem with headphone sense. Everytime I plug the headphones, I get sound from speaker too. I know there have been countless threads, and I followed them all, but I couldnt solve this. Somebody help me please? (Im a linux noobie, so please, be as clear as possible)

This is my lspci on audio:
```
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
```

Thank you!

---

### Post by Dbugger on 2008-02-05
Bump... Noone can help me? :(

---

### Post by Dbugger on 2008-02-06
Another bump.... It's a really important issue

---

### Post by VMan on 2008-02-07
Post the specs on your computer.  What make, model, etc.  If it is a Toshiba A135 series, I might be able to help.  I will be working on getting that done sometime in the next week or so.  Right now, I got it so it lowers the speaker volume (but doesn't mute) so low it might as well be muted.  You can only hear the speakers in a very quiet environment.  I'm not on my laptop right now, so can't look it up.

---

### Post by Dbugger on 2008-02-07
It's a SAMSUNG R40. Here is the output of lspci:

```
00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:07.0 Ethernet controller: Atheros Communications, Inc. AR2413 802.11bg NIC (rev 01)
02:09.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b4)
02:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 18)
02:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller
02:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 09)
02:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 04)

```

---

### Post by Dbugger on 2008-02-08
bump

---

### Post by Dbugger on 2008-02-09
last bump.... PLEASE SMEBODY!

---

### Post by happyhamster on 2008-02-09
Are you using the snd-hda-intel module? What is the output of:

aplay -l

cat /proc/asound/card0/codec#* | grep codec -i

---

### Post by Dbugger on 2008-02-11
> **happyhamster said:**
> Are you using the snd-hda-intel module? What is the output of:

aplay -l

cat /proc/asound/card0/codec#* | grep codec -i

for aplay -l

```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC262 Analog [ALC262 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

for cat /proc/asound/card0/codec#* | grep codec -i
```

Codec: Generic 11c1 Si3054
Codec: Realtek ALC262
```

I'm Ashamed I dont know what a module is... sorry. Linux newbie...

---

### Post by happyhamster on 2008-02-11
A module is a piece of software that is loaded to make specific hardware work. In your case: the module snd-hda-intel is loaded to take care of the soundcard. Unfortunately, snd-hda-intel has a few problems (to put it mildly). For detailed info, see:
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

Anyway, what you could try (also described in above link) is adding a model option in your sound configuration file. You'll have to edit a file manually, reboot, and test if sound works as it should. If not, repeat the process. (This is going to require some effort on your part I'm afraid. And there's no guarantee it'll work in the end.)

Now, if that didn't discourage you, let's get started :)

- The file you need to edit is alsa-base. First make a backup (just for safety). In a terminal:

sudo cp /etc/modprobe.d/alsa-base ~/alsa-base-backup
(It will put the backup in your home folder.)

- Open alsa-base in an editor (nano):

sudo nano /etc/modprobe.d/alsa-base

- At the end of that file add a line:

options snd-hda-intel model=hippo

- Save (ctrl-o), and exit the editor (ctrl-x). Reboot. Check if sound's ok. If not, try another model (change "hippo" into "hippo_1" for example. The available options are:
```

	  fujitsu	             Fujitsu Laptop
	  hp-bpc	           HP xw4400/6400/8400/9400 laptops
	  hp-bpc-d7000	      HP BPC D7000
	  benq		            Benq ED8
	  benq-t31	          Benq T31
	  hippo		             Hippo (ATI) with jack detection, Sony UX-90s
	  hippo_1	           Hippo (Benq) with jack detection
	  sony-assamd	       Sony ASSAMD
	  basic		              fixed pin assignment w/o SPDIF
	  auto		              auto-config reading BIOS (default)

```
- As you can see, your laptop isn't listed, but it's possible that one of those options will work nevertheless. Note that you can skip choosing "auto" (because that's what's set when you don't edit alsa-base at all).

- Also: there should only be 1 line in alsa-base talking about snd-hda-intel. So, if you try another model, edit that 1 line, don't keep adding new lines.

- When testing if sound works as it should, try unplugging and re-plugging the headphones. It might even help to mute sound altogether in between. What I mean is: unplug headphones, mute sound, plug in phones again, then unmute.

If something's unclear, or if there are any other problems; let us know. Good luck.

---

### Post by Dbugger on 2008-02-12
none of these are working! damm! :(:(

---

### Post by Jeztastic on 2008-02-24
I am having the same problem. Please help! This is a real pain for me, as I surf late at night when others are in bed.

---

