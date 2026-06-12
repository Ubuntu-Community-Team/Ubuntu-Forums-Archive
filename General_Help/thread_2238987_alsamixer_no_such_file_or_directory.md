---
title: "alsamixer: no such file or directory"
date: 2014-08-11
forum: General Help
---

### Post by Robert Finley on 2014-08-11
I am trying to setup a minimal system from the Ubuntu 14.04 netboot iso.   I installed the system using defaults only (exept partitioning).  After the install was finished I restarted, edited sources.list to add extras and partners, fetched key for partners, updated apt and installed xorg slim alsa-base alsa-utils i3.  After it was finished installing I added myself to audio group and rebooted.  After the reboot I logged in with slim, did the first-run i3 config, did an apt-get update and apt-get dist-upgrade just for fun (of course nothing had changed) and verified that I was in the audio group with "groups".  Then I type "alsamixer" and get "cannot open mixer: no such file or directory"

I tried this yesterday and installing pulseaudio fixed it but I don't want pulseaudio as this is a pretty old box and I am trying to conserve resources.  Any help greatly appreciated.  I have googled for a couple days trying, and now I'm here.  I hope that someone recognizes what might be wrong here.

---

### Post by steeldriver on 2014-08-11
Are you able to see your sound device(s) with

```

aplay -l

```
and/or
```

ls /proc/asound

```

What about modules

```

lsmod | grep ^snd

```

---

### Post by Robert Finley on 2014-08-11
Yes, it sees the device.  aplay -l produces:

**** List of PLAYBACK Hardware Devices ****
card 1: Set [USB Headphone Set], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

lsmod | grep ^snd produces:

snd_usb_audio         127638  0 
snd_usbmidi_lib        24367  1 snd_usb_audio
snd_hwdep              13272  1 snd_usb_audio
snd_pcm                85501  1 snd_usb_audio
snd_page_alloc         14230  1 snd_pcm
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25135  2 snd_usbmidi_lib,snd_seq_midi
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              28584  2 snd_pcm,snd_seq
snd                    60871  9 snd_usb_audio,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_usbmidi_lib,snd_seq_device,snd_seq_midi

---

### Post by Robert Finley on 2014-08-11
I have found a solution for this problem.

Appearantly, ALSA did not  like the USB sound device that I was using. It is one of the cheap $2  ones that look like a USB stick w/headphone jack.  Either way, I  attached an old SB Live! PCI card I had laying around, booted up the  machine and alsamixer worked with no problem. I can switch between the 2  devices and the USB headphone thingy works just fine now.

So anyone  that may read this with a similar problem: the device was the problem.

---

