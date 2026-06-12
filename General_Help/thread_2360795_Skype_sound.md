---
title: "Skype sound"
date: 2017-05-08
forum: General Help
---

### Post by glendavee on 2017-05-08
Not sure if this is correct forum, but here goes. I am running 17.04, 64bit. Trying to use Skype 4.3, with Logitechc200 webcam. When I make a test call I hear nothing. I have pulseaudio installed, also libpulse0:i386. On sound settings I can hear test sounds on speakers. I have had Skype working in past, but not sure which version and with which version of ubuntu. I looked all over internet and tried all sorts of solutions, but no joy. Help please

---

### Post by #&amp;thj^% on 2017-05-08
Have a look here: [https://support.skype.com/en/faq/FA10964/how-do-i-adjust-the-sound-settings-on-my-computer-and-in-skype-for-linux](https://support.skype.com/en/faq/FA10964/how-do-i-adjust-the-sound-settings-on-my-computer-and-in-skype-for-linux)

---

### Post by glendavee on 2017-05-09
Had a look, no success

---

### Post by pruda on 2017-05-09
What I needed was to switch from default mic to webcam mic.

From terminal run:
```
pacmd list-sources
pacmd set-default-source "name of your webcam device"
```

Then it worked fine. It is also good idea to use second line as startup script (or better yet udev rule), because whenever you will disconnect webcam, mic device resets back to soundard mic.

---

### Post by glendavee on 2017-05-09
When I  pacmd list-sources  My device shows up as 
3 source(s) available.
  * index: 0
	name: <alsa_input.usb-046d_0802_64159F50-02.analog-mono>
	driver: <module-alsa-card.c>
	flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
	state: SUSPENDED
	suspend cause: IDLE 
	priority: 9049
	volume: mono: 65536 / 100% / 0.00 dB
	        balance 0.00
	base volume: 20724 /  32% / -30.00 dB
	volume steps: 65537
	muted: no
	current latency: 0.00 ms
	max rewind: 0 KiB
	sample spec: s16le 1ch 48000Hz
	channel map: mono
	             Mono
	used by: 0
	linked by: 0
	configured latency: 0.00 ms; range is 0.50 .. 2000.00 ms
	card: 0 <alsa_card.usb-046d_0802_64159F50-02>
	module: 6
	properties:
		alsa.resolution_bits = "16"
		device.api = "alsa"
		device.class = "sound"
		alsa.class = "generic"
		alsa.subclass = "generic-mix"
		alsa.name = "USB Audio"
		alsa.id = "USB Audio"
		alsa.subdevice = "0"
		alsa.subdevice_name = "subdevice #0"
		alsa.device = "0"
		alsa.card = "1"
		alsa.card_name = "USB Device 0x46d:0x802"
		alsa.long_card_name = "USB Device 0x46d:0x802 at usb-0000:00:1a.0-1.1, high speed"
		alsa.driver_name = "snd_usb_audio"
		device.bus_path = "pci-0000:00:1a.0-usb-0:1.1:1.2"
		sysfs.path = "/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.2/sound/card1"
		udev.id = "usb-046d_0802_64159F50-02"
		device.bus = "usb"
		device.vendor.id = "046d"
		device.vendor.name = "Logitech, Inc."
		device.product.id = "0802"
		device.product.name = "Webcam C200"
		device.serial = "046d_0802_64159F50"
		device.form_factor = "webcam"
		device.string = "hw:1"
		device.buffering.buffer_size = "192000"
		device.buffering.fragment_size = "96000"
		device.access_mode = "mmap+timer"
		device.profile.name = "analog-mono"
		device.profile.description = "Analogue Mono"
		device.description = "Webcam C200 Analogue Mono"
		alsa.mixer_name = "USB Mixer"
		alsa.components = "USB046d:0802"
		module-udev-detect.discovered = "1"
		device.icon_name = "camera-web-usb"
	ports:
		analog-input-mic: Microphone (priority 8700, latency offset 0 usec, available: unknown)
			properties:
				device.icon_name = "audio-input-microphone"
	active port: <analog-input-mic>

When I then use  <alsa_input.usb-046d_0802_64159F50-02.analog-mono> as device name in  pacmd set-default-source   I get the following
 :bash: syntax error near unexpected token `newline'

Tried a couple of times, same result

---

### Post by #&amp;thj^% on 2017-05-09
Have you tried this yet?
```
pacmd set-default-source "Webcam C200 Analogue Mono"
```

---

### Post by glendavee on 2017-05-09
Yes - I get     Source Webcam C200 Analogue Mono does not exist. Don't understand this as it is clearly listed

---

### Post by #&amp;thj^% on 2017-05-09
I think we just have to list the right device.
What dose this show from the terminal:
```
inxi -Axx
```

---

### Post by glendavee on 2017-05-09
Output from inxi Axx

CPU~Dual core Intel Core i3-2120 (-HT-MCP-) speed/max~1599/3300 MHz Kernel~4.10.0-20-generic x86_64 Up~7:04 Mem~2160.0/3866.4MB HDD~2000.4GB(3.7% used) Procs~219 Client~Shell inxi~2.3.8

---

### Post by #&amp;thj^% on 2017-05-09
Nope not what I needed.
The code is "inxi -Axx" your missing the "-"

---

### Post by glendavee on 2017-05-09
Audio:     Card-1 Intel 6 Series/C200 Series Family High Definition Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0 chip-ID: 8086:1c20
           Card-2 Logitech Webcam C200
           driver: USB Audio usb-ID: 001-003 chip-ID: 046d:0802
           Sound: Advanced Linux Sound Architecture v: k4.10.0-20-generic

---

### Post by #&amp;thj^% on 2017-05-09
Well it looks to me like we have only 2 choices here:
1):```

pacmd set-default-source "Webcam C200"
```
or 2):
```
pacmd set-default-source "USB Audio"
```
Fingers crossed...and the force be with you.

---

### Post by glendavee on 2017-05-09
Thanks for your efforts, but neither worked - Source USB Audio does not exist. and Source Webcam C200 does not exist.
I will be offline for a couple of days

---

### Post by #&amp;thj^% on 2017-05-09
> **glendavee said:**
> Thanks for your efforts, but neither worked - Source USB Audio does not exist. and Source Webcam C200 does not exist.
I will be offline for a couple of days

No Worries...we have a couple more things we can check when you return.
when you get back lets see if we can poke it a bit:
```
sudo modprobe snd_usb_audio
```
Make sure volume levels are good..._**and if this works for you,**_
To load the module automatically at boot, add a single line containing the name of the module to /etc/modules

```
sudo tee -a /etc/modules <<< "snd_usb_audio"
```

---

### Post by pruda on 2017-05-09
> **glendavee said:**
> When I then use  <alsa_input.usb-046d_0802_64159F50-02.analog-mono> as device name in  pacmd set-default-source   I get the following
 :bash: syntax error near unexpected token `newline'

Tried a couple of times, same result

You are almost there, just use
```
pacmd set-default-source alsa_input.usb-046d_0802_64159F50-02.analog-mono
```

(lt and gt signs are there just to confuse the enemy, they have special meaning in bash, which explains the token error ;-) )

edit: btw. I know it's hard to convince people around, but have you ever considered switching to some free linux friendly alternative? Skype for linux 4.3 is soon to be dead anyway. MS is on the path which will probably kill the windows version too :-( And the new 64-bit-only linux version is a chrome powered whatever sucks your memory. Sorry for off topic...

---

### Post by glendavee on 2017-05-11
sudo modprobe snd_usb_audio didn't show anything.  I also tried 
 pacmd set-default-source alsa_input.usb-046d_0802_64159F50-02.analog-mono   as suggested by pruda. Still no joy, although the microphone shows up in sound settings

---

### Post by pruda on 2017-05-11
I'd try some other application like audacity and/or test the camera mic on other PC. But that's all that I can suggest.

---

### Post by #&amp;thj^% on 2017-05-11
> **glendavee said:**
> sudo modprobe snd_usb_audio didn't show anything.  I also tried 
 pacmd set-default-source alsa_input.usb-046d_0802_64159F50-02.analog-mono   as suggested by pruda. Still no joy, although the microphone shows up in sound settings

Now I'm pulling the last trick I can remember from my notes:  :)
just start skype with the following command line:

```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype

```

---

### Post by kjaspan on 2017-10-22
I also have not been able to use Skype since upgrading to Ubuntu 17.04 64 bit AMD. It is not recognizing my Webcam C310 mic. I do not have pulseaudio running but lsusb gives: Bus 001 Device 004: ID 046d:081b Logitech, Inc. Webcam C310
and inxi -Axx gives:
Audio:     Card-1 Advanced Micro Devices [AMD] FCH Azalia Controller
           driver: snd_hda_intel bus-ID: 00:14.2 chip-ID: 1022:780d
           Card-2 Logitech Webcam C310
           driver: USB Audio usb-ID: 001-004 chip-ID: 046d:081b
           Sound: Advanced Linux Sound Architecture v: k4.10.0-37-generic
In my pavucontrol I see, under Input Devices,  Webcam C310 Analog Mono listed with port Microphone.
I can see my microphone working when watching input devices while making a test call but Skype does not seem to receive the input. If I use headphones the mic works.

---

### Post by kjaspan on 2017-10-27
> **kjaspan said:**
> I also have not been able to use Skype since upgrading to Ubuntu 17.04 64 bit AMD. It is not recognizing my Webcam C310 mic. I do not have pulseaudio running but lsusb gives: Bus 001 Device 004: ID 046d:081b Logitech, Inc. Webcam C310
and inxi -Axx gives:
Audio:     Card-1 Advanced Micro Devices [AMD] FCH Azalia Controller
           driver: snd_hda_intel bus-ID: 00:14.2 chip-ID: 1022:780d
           Card-2 Logitech Webcam C310
           driver: USB Audio usb-ID: 001-004 chip-ID: 046d:081b
           Sound: Advanced Linux Sound Architecture v: k4.10.0-37-generic
In my pavucontrol I see, under Input Devices,  Webcam C310 Analog Mono listed with port Microphone.
I can see my microphone working when watching input devices while making a test call but Skype does not seem to receive the input. If I use headphones the mic works.

Well, I'll be darned: I switched the UI to Ubuntu (was Xubuntu) after upgrading to 17.10 and, voila, Skype audio works!! Go figure.

---

