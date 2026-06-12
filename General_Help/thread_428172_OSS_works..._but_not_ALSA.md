---
title: "OSS works... but not ALSA?"
date: 2007-04-30
forum: General Help
---

### Post by Ububurns on 2007-04-30
Just got an external sound card.

Volume Control (ALSA) and alsamixer only recognise it as having an audio out.

However I am able to record with OSS-using programs, using /dev/dsp1.

Why would OSS work fine, but ALSA ignore inputs completely?

---

### Post by zvacet on 2007-05-01
**programs>sound&video>sound control>edit**

---

### Post by Ububurns on 2007-05-01
Thanks for the help, but I think it's a bit further than that.

It's not that it just doesn't appear in the Volume Control - there is no recording device found, or registered, by ALSA.

Yet OSS picks it up fine...

---

### Post by zvacet on 2007-05-01
Go to the synaptic and chek do you have** linux-sound-base** installed.Other packages I have are :alsa-base,alsa-oss,alsa-utilis,gstreamer.10-alsa,libsound2,libesd-alsa0,libpt-plugins-alsa,libsdl1.2debian-alsa.Go to the system>settings<multimedia system and chek there if alsa works.

---

### Post by josephus on 2007-05-02
can you post 

```
more /proc/asound/*
sudo lshw -C multimedia

```

---

### Post by Ububurns on 2007-05-02
[SIZE="1"][FONT="System"]$ more /proc/asound/*

*** /proc/asound/card0: directory ***


*** /proc/asound/card1: directory ***

::::::::::::::
/proc/asound/cards
::::::::::::::
 0 [Tumbler        ]: PMac Tumbler - PowerMac Tumbler
                      PowerMac Tumbler (Dev 15) Sub-frame 0
 1 [default        ]: USB-Audio - USB Audio CODEC 
                      Burr-Brown from TI               USB Audio CODEC  at usb-0
001:10:19.0-1, full s

*** /proc/asound/default: directory ***

::::::::::::::
/proc/asound/devices
::::::::::::::
  2:        : timer
  3:        : sequencer
  4: [ 0- 0]: digital audio playback
  5: [ 0]   : control
  6: [ 1- 0]: digital audio playback
  7: [ 1- 0]: digital audio capture
  8: [ 1]   : control
::::::::::::::
/proc/asound/hwdep
::::::::::::::
::::::::::::::
/proc/asound/modules
::::::::::::::
 0 snd_powermac
 1 snd_usb_audio

*** /proc/asound/oss: directory ***

::::::::::::::
/proc/asound/pcm
::::::::::::::
00-00: PMac Tumbler : PowerMac Tumbler : playback 1
01-00: USB Audio : USB Audio : playback 1 : capture 1

*** /proc/asound/seq: directory ***

::::::::::::::
/proc/asound/timers
::::::::::::::
G0: system timer : 4000.000us (10000000 ticks)
P0-0-0: PCM playback 0-0-0 : SLAVE
P1-0-0: PCM playback 1-0-0 : SLAVE
P1-0-1: PCM capture 1-0-1 : SLAVE

*** /proc/asound/Tumbler: directory ***

::::::::::::::
/proc/asound/version
::::::::::::::
Advanced Linux Sound Architecture Driver Version 1.0.14rc1 (Tue Jan 09 09:56:17 
2007 UTC).


and

$ sudo lshw -C multimedia

  *-usb                   
       description: Audio device
       product: USB Audio CODEC
       vendor: Burr-Brown from TI
       physical id: 1
       bus info: usb@2:1
       version: 1.00
       capabilities: usb-1.10 audio-control
       configuration: driver=usbhid maxpower=100mA speed=12.0MB/s
[/FONT][/SIZE]

---

### Post by josephus on 2007-05-02
which sound device are we trying to get recognized for capture? usb or powermac?

---

### Post by Ububurns on 2007-05-02
Usb.

---

### Post by josephus on 2007-05-02
you can try editing /etc/modprobe.d/alsa-base

```
options snd-usb-audio index=-2
```

change the -2 to a 0

restart

---

### Post by Ububurns on 2007-05-02
Tried your suggestion - all it has seemed to do is swap the two around.

Now the usb sound card is hw:0, and the PowerMac Tumbler card is hw:1.

[IMG]http://filexoom.com/view/2007/5/2/72892/UbuntuPPC/USB-audio.png[/IMG]

---

### Post by josephus on 2007-05-02
what is the output of 
```

arecord --list-devices


```

---

### Post by josephus on 2007-05-03
you can try adding the vendor id number and product id number to the modprobe.d/alsa-base

options snd-usb-audio vid=<vid> pid=<pid>

you can find the actual numbers using lsusb.

also you can try disabling os s module, sometimes alsa and oss don't play nice with each other.

beyond that i don't i'm not sure what to suggest.

---

### Post by Ububurns on 2007-05-03
[FONT="Fixedsys"][SIZE="1"]$ arecord --list-devices
**** List of CAPTURE Hardware Devices ****
card 0: default [USB Audio CODEC ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0[/SIZE][/FONT]

I thank you all for your time and suggestions.

Unfortunately, I have to return the sound card to its owner now.

Maybe next time - when I buy my own!

---

