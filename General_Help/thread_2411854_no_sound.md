---
title: "no sound"
date: 2019-02-04
forum: General Help
---

### Post by jgw on 2019-02-04
I have been having a problem with my sound for about 2 days.  Its strange.  I got sound from audacious (music player) by changing the output plugin from pulsaudio to alsa.  I just checked it again and, this time, both function but pulsaudio is has about half the volume of alsa.  When in settings/sound I have found that even though I have sound from Audacious there is no sound when testing the line out speakers.  If I move from line out to digital output the sound from  Audacious goes away.  When in  settings/sound/sound effects/ I can play the sound effects regardless of sound settings.  So, right now, I am playing music in Audacious but cannot test the speakers - even if Audacious is paused (no music)  

Anyway, I have had a number of things like "alsa link refused".  My sound was working fine when I shut this machine down last night.  Seems every morning there is a problem.  At one point I removed pulseaudio and re-installed it (made no difference).  There was also a suggestion to # out last few lines in /etc/pulse/default.pa but the lines were different so I left that file alone.  I have also tried a couple other suggestions to no avail.  I wonder, is there a way to just start the entire sound thing over (remove everything and reinstall or just reinstall?)

Here is some info on my sound stuff:
greg@gregdown:~$ pacmd list-cards
2 card(s) available.
    index: 0
	name: <alsa_card.usb-046d_0809_A5B94E6F-02>
	driver: <module-alsa-card.c>
	owner module: 7
	properties:
		alsa.card = "1"
		alsa.card_name = "USB Device 0x46d:0x809"
		alsa.long_card_name = "USB Device 0x46d:0x809 at usb-0000:02:00.0-4.1, full speed"
		alsa.driver_name = "snd_usb_audio"
		device.bus_path = "pci-0000:02:00.0-usb-0:4.1:1.2"
		sysfs.path = "/devices/pci0000:00/0000:00:04.0/0000:02:00.0/usb8/8-4/8-4.1/8-4.1:1.2/sound/card1"
		udev.id = "usb-046d_0809_A5B94E6F-02"
		device.bus = "usb"
		device.vendor.id = "046d"
		device.vendor.name = "Logitech, Inc."
		device.product.id = "0809"
		device.product.name = "Webcam Pro 9000"
		device.serial = "046d_0809_A5B94E6F"
		device.form_factor = "webcam"
		device.string = "1"
		device.description = "Webcam Pro 9000"
		module-udev-detect.discovered = "1"
		device.icon_name = "camera-web-usb"
	profiles:
		input:analog-mono: Analog Mono Input (priority 2, available: unknown)
		off: Off (priority 0, available: unknown)
	active profile: <input:analog-mono>
	sources:
		alsa_input.usb-046d_0809_A5B94E6F-02.analog-mono/#0: Webcam Pro 9000 Analog Mono
	ports:
		analog-input-mic: Microphone (priority 8700, latency offset 0 usec, available: unknown)
			properties:
				device.icon_name = "audio-input-microphone"
    index: 1
	name: <alsa_card.pci-0000_00_14.2>
	driver: <module-alsa-card.c>
	owner module: 8
	properties:
		alsa.card = "0"
		alsa.card_name = "HDA ATI SB"
		alsa.long_card_name = "HDA ATI SB at 0xf9ff4000 irq 16"
		alsa.driver_name = "snd_hda_intel"
		device.bus_path = "pci-0000:00:14.2"
		sysfs.path = "/devices/pci0000:00/0000:00:14.2/sound/card0"
		device.bus = "pci"
		device.vendor.id = "1002"
		device.vendor.name = "Advanced Micro Devices, Inc. [AMD/ATI]"
		device.product.id = "4383"
		device.product.name = "SBx00 Azalia (Intel HDA)"
		device.form_factor = "internal"
		device.string = "0"
		device.description = "Built-in Audio"
		module-udev-detect.discovered = "1"
		device.icon_name = "audio-card-pci"
	profiles:
		input:analog-stereo: Analog Stereo Input (priority 60, available: no)
		output:analog-stereo: Analog Stereo Output (priority 6000, available: unknown)
		output:analog-stereo+input:analog-stereo: Analog Stereo Duplex (priority 6060, available: unknown)
		output:iec958-stereo: Digital Stereo (IEC958) Output (priority 5500, available: unknown)
		output:iec958-stereo+input:analog-stereo: Digital Stereo (IEC958) Output + Analog Stereo Input (priority 5560, available: unknown)
		off: Off (priority 0, available: unknown)
	active profile: <output:analog-stereo>
	sinks:
		alsa_output.pci-0000_00_14.2.analog-stereo/#0: Built-in Audio Analog Stereo
	sources:
		alsa_output.pci-0000_00_14.2.analog-stereo.monitor/#1: Monitor of Built-in Audio Analog Stereo
	ports:
		analog-input-front-mic: Front Microphone (priority 8500, latency offset 0 usec, available: no)
			properties:
				device.icon_name = "audio-input-microphone"
		analog-input-rear-mic: Rear Microphone (priority 8200, latency offset 0 usec, available: no)
			properties:
				device.icon_name = "audio-input-microphone"
		analog-input-linein: Line In (priority 8100, latency offset 0 usec, available: no)
			properties:
				
		analog-output-lineout: Line Out (priority 9900, latency offset 0 usec, available: yes)
			properties:
				
		analog-output-headphones: Headphones (priority 9000, latency offset 0 usec, available: no)
			properties:
				device.icon_name = "audio-headphones"
		iec958-stereo-output: Digital Output (S/PDIF) (priority 0, latency offset 0 usec, available: unknown)
			properties:

greg@gregdown:~$ pacmd
Welcome to PulseAudio 11.1! Use "help" for usage information.

I had to start pulseaudio with "pulseaudio --start"
>>> 

I have no idea what to do next.  I fear that if I keep on trying stuff I will, eventually, wreck my computer.

Thank you..............

---

### Post by #&amp;thj^% on 2019-02-04
Hi jgw, can you also show us this:
```
inxi -A
```
Also you show 2 cards available which card are you using as default?

---

### Post by jgw on 2019-02-04
thanks for the reply!

greg@gregdown:~$ inxi -A
Audio:     Card Advanced Micro Devices [AMD/ATI] SBx00 Azalia (Intel HDA)
           driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.15.0-45-generic

I know that it says 2 cards but the only one is the one built into my motherboard (ASUS M5A78L-M PLUS/usb3 with Realtek ® ALC 887 Audio CODEC for sound)
It also tells me that one is a usb plugin.  The only things plugged into usb are: wireless thingy, mouse, camera (probably other card - has microphone), labelwriter, and 2 hubs (4 and 7 ports)

I wonder, however, the camera microphone seems to always be on.  I don't know about default as one is for output and the other is for the microphone (source).  Then there is the fact that I must start pulsaudio after every boot.

---

### Post by #&amp;thj^% on 2019-02-04
For some reason yours wants to default to card "1" :confused:
Here's a workaround to try:**BTW if you get no sound or a dummy device, don't worry this can be easily fixed.:)**
```

sudo touch /etc/asound.conf
sudo nano /etc/asound.conf
```

Add the following into the bottom of that file:
```
defaults.ctl.card 0
defaults.pcm.card 0
defaults.timer.card 0
```
Reboot to see if this helped.
Mine shows as:
```
# Use PulseAudio by default
pcm.!default {
  type pulse
  fallback "sysdefault"
  hint {
    show on
    description "Default ALSA Output (currently PulseAudio Sound Server)"
  }
}

ctl.!default {
  type pulse
  fallback "sysdefault"
defaults.ctl.card 1
defaults.pcm.card 1
defaults.timer.card 1

}


```

---

### Post by jgw on 2019-02-05
Thank you for the reply.

Little problem.  This file didn't exist in /etc  At first I thought to just create the file and enter but then I took a look at yours and there is a lot more than that in there.  That being the case I have not done anything although I was tempted to just use yours except that you have assigned eat one with a '1' and the suggestion assigned '0' so I thought I had better ask first.  

Oh, this morning I started with pulseaudio --start and then pavucontrol.  Before that I tried Audacity and got nothing, afterwards I got sound for Audacity but cannot test speakers with settings.  This is very strange.

---

### Post by benbrockn on 2019-02-05
I have a workaround for this but I think an update uninstalled pulseaudio. I had to re-install pulseaudio & reboot my system (Xubuntu 18.04.1 LTS). Now, when I start my computer I still have that "volume X" notification on my notification bar, so I have to go to the terminal and manually start it via "pulseaudio --start" and then it works again. Maybe the mods/devs can figure it out, but I hope that helps you.

---

### Post by jgw on 2019-02-06
Thanks for the reply.

I too have to pulseaudio --start every morning.  The system thinks I should be using alsa but I have to then change it to pulseaudio.  In settings, however, I remain unable to test the speakers (I think its trying to use alsa but have no idea how or why....

---

### Post by jgw on 2019-02-06
I seem to have fixed it.  First I did a  "sudo apt-get install --reinstall pulseaudio pulseaudio-module-x11"  Then I checked my startup programs - no pulseaudio!  So, I entered pulseadio -D  Then I re-booted. I can now test my speakers AND run audacious.  As far as I can tell its all working!  I will mark this one as solved................

---

