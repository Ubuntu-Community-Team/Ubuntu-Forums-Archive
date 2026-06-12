---
title: "How to connect PC to HiFi amplifier"
date: 2024-11-25
forum: General Help
---

### Post by satimis on 2024-11-25
Hi all,

PC - Ubuntu 24.04 desktop
HiFi Amplifier - Denon Amplifier AVR2810

Please advise how to connect the PC to the HiFi Amplifier for playing music on PC?

I have tried connecting Sound Card Out of PC to HiFi Amplifier IN.  It works but the sound quality is not good.  I select "Phono In" on HiFi Amplifier,

Please advise.  Thanks

Regards

---

### Post by The Cog on 2024-11-25
The phono input is probably not a good idea. Vinyl records are recorded with much reduced bass and increased treble, to avoid groove skipping and overcome some scratchiness. They are therefore given a bass boost and treble cut after entering the amplifier, to compensate. I think any other input you can find would be better than that. Look for a tape, CD, radio or aux input to use instead.

---

### Post by satimis on 2024-11-25
> **The Cog said:**
> The phono input is probably not a good idea. Vinyl records are recorded with much reduced bass and increased treble, to avoid groove skipping and overcome some scratchiness. They are therefore given a bass boost and treble cut after entering the amplifier, to compensate. I think any other input you can find would be better than that. Look for a tape, CD, radio or aux input to use instead.
Hi The Cog,

Thanks for your advice.  The .wav files were digitized on CDs not on vinyl records.  I'll try your suggestion later.  There are many options on my Denon Amplifier for selection.

Besides can I play CD on PC DVD Writer and export the output to the input of Denon Amplifier?  If YES how to connect them PC and my Denon Amplifier ?  Thanks

A side question: recently Ubuntu org forum is very slow in response clickng it items..  I have to wait for a long time.  I'm running Google Chrome browser.

Regards

---

### Post by him610 on 2024-11-25
@satimis
It would have helped if you had provided some information about your PC ouputs including your sound card; the receiver can be researched on the web. As it is, we are guessing about your audio outs. You have over 4000 beans. Have you not learned to provide as much pertinent info as possible if you want good advice?

Here is what I found after a web search - > How do I get my computer to play sound through a receiver?
The best way to connect a PC to the receiver would be with HDMI - only if your PC has an HDMI output of course. Other than that - if you are just trying to get the audio from the PC to play through the receiver - you can just run the audio output of the laptop to an audio input on the receiver.

Search using this term -> denon amplifier avr2810 audio input from computer

---

### Post by satimis on 2024-11-26
> **him610 said:**
> @satimis
It would have helped if you had provided some information about your PC ouputs including your sound card; the receiver can be researched on the web.
 - snip -
Hereinbelow are some info:-

$ cat /proc/asound/devices```

  1:        : sequencer
  2: [ 0- 3]: digital audio playback
  3: [ 0- 7]: digital audio playback
  4: [ 0- 8]: digital audio playback
  5: [ 0- 0]: hardware dependent
  6: [ 0]   : control
  7: [ 1- 0]: digital audio playback
  8: [ 1- 0]: digital audio capture
  9: [ 1- 1]: digital audio playback
 10: [ 1- 2]: digital audio capture
 11: [ 1- 0]: hardware dependent
 12: [ 1]   : control
 33:        : timer

```

$ aplay --list-devices```

**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Generic [HD-Audio Generic], device 7: HDMI 1 [DELL U3219Q]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Generic [HD-Audio Generic], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic_1 [HD-Audio Generic], device 0: ALCS1200A Analog [ALCS1200A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic_1 [HD-Audio Generic], device 1: ALCS1200A Digital [ALCS1200A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```
  
  sudo dmidecode -t 2 ```

[sudo] password for satimis: 
# dmidecode 3.5
Getting SMBIOS data from sysfs.
SMBIOS 3.2.0 present.

Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
	Manufacturer: ASUSTeK COMPUTER INC.
	Product Name: PRIME X570-P
	Version: Rev X.0x
	Serial Number: 190753869002923
	Asset Tag: Default string
	Features:
		Board is a hosting board
		Board is replaceable
	Location In Chassis: Default string
	Chassis Handle: 0x0003
	Type: Motherboard
	Contained Object Handles: 0
	
```

Regards

---

### Post by satimis on 2024-11-30
Hi all,

I got my problem solved, connecting my desktop PC running Ubuntu 24.04 to Denon AVR-2810.

It is very easy just connecting the "EarPhone out" of desktop PC (for connecting PC loudspeakers) to Denon CD IN.  Setting on Denon - Direct CD.  It works seamlessly.  The sound is excellent similar to playing CDs on my Onkyo CD player which is not working any more.

I have digitized all my music CDs, about 500 CDs, to digital files in .wav format and stored them on a 4TB hard drive, solely for data storage, without OS running. The drive is on ext-4 format. The digital files are stored on folders specially created, retaining the name of musical piece as their folder names. Besides I have created a txt file consisting all their details, such as the full name of the music piece, the composer, the pianist or violinist, director of the orchestra etc. It would ease me making search.

Also I have created 7 folders on the working drive of the PC. I name them as "Monday_Folder, Tuesday_Folder, Wednesday_Folder etc. I copy the musical pieces, which I like to hear, as symbolic links on each folder from the storage drive. To play them I just run following command on Terminal of Ubuntu 24.04 Linux PC;

[COLOR="#FF0000"]$ vlc /path/to/Monday_Folder/*[/COLOR]

vlc is the name of a media player.

**[COLOR="#FF0000"]VLC media player[/COLOR]**
[https://www.videolan.org/](https://www.videolan.org/)

I have it installed on Ubuntu 24.04 desktop Linux. I trust other media players would also work as well. Also I believe that this setup will work on Windows as well.

The music files on each folder will be played automatically for a full day, without the need of changing CD. It is very convenient.

Regards

---

