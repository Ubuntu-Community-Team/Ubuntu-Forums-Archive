---
title: "Help getting Audio device to show up.."
date: 2015-10-04
forum: General Help
---

### Post by hopelessone on 2015-10-04
Hi,

```
blade@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 2: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
blade@ubuntu:~$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801JD/DO (ICH10 Family) HD Audio Controller (rev 02)
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Cedar HDMI Audio [Radeon HD 5400/6300 Series]
blade@ubuntu:~$ 
```

How can I get 00:1b.0 Audio device: Intel Corporation 82801JD/DO (ICH10 Family) HD Audio Controller (rev 02) to show up? (check screenshot)

---

### Post by tgalati4 on 2015-10-04
Is there a setting in BIOS that allows you to make the on-board, Intel sound the primary?  Are you running a proprietary ATI video driver?

---

### Post by grahammechanical on 2015-10-04
Plug in an audio cable into the motherboard line out port. If there is a headphone port then plug an audio cable in to that and then Sound Settings will show other audio devices that can be selected.

When we connect to the monitor using a HDMI connection with the graphic adapter then we get the HDMI/Display Port showing in Sound Settings but none of the other audio devices. I have the same situation with an Nvidia graphic adapter and a HDMI connection to the monitor. But I see other audio devices if I plug an audio cable into the revelant motherboard audio ports. Sound Settings will detect the audio device immediately the audio cable is connected to the port.

Regards.

---

### Post by hopelessone on 2015-10-04
Hi,

I've checked BIOS and onboard audio is enabled, the headphones are plugged in but still no output to headphones.. So weird.. Any other ideas I can try?

---

### Post by tgalati4 on 2015-10-04
Please post the output of:

```
lsmod | grep snd
```

A standard Linux Mint MATE (based on 14.04) Intel sound stack looks similar to:

> tgalati4@Mint17 ~ $ lsmod | grep snd
snd_hda_codec_realtek    61438  1 
snd_hda_intel          52355  3 
snd_hda_codec         192906  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
snd                    69238  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
soundcore              12680  1 snd


---

### Post by hopelessone on 2015-10-04
Hi,

Its Cinnamon! I logged out and back into unity and it works :)

Now to get cinnamon to play?

Hi,

Here is the output within cinnamon:

```
blade@ubuntu:~$ lsmod | grep snd
snd_hda_codec_analog    15049  1 
snd_hda_codec_generic    69011  1 snd_hda_codec_analog
snd_usb_audio         166168  2 
snd_usbmidi_lib        29828  1 snd_usb_audio
snd_hda_codec_hdmi     47548  1 
snd_hda_intel          30469  5 
snd_hda_controller     30228  1 snd_hda_intel
snd_hda_codec         139719  5 snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller,snd_hda_codec_analog
snd_hwdep              17698  2 snd_usb_audio,snd_hda_codec
snd_pcm               104112  5 snd_usb_audio,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
snd_seq_midi           13564  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30876  2 snd_usbmidi_lib,snd_seq_midi
snd_seq                63074  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29562  2 snd_pcm,snd_seq
snd                    79468  27 snd_usb_audio,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_hda_codec_analog
soundcore              15047  2 snd,snd_hda_codec
blade@ubuntu:~$ 

```

No, It's not Cinnamon... :(

```
blade@ubuntu:~$ sudo alsa force-reload
Terminating processes: 1732.
Unloading ALSA sound driver modules: snd-hda-codec-analog snd-hda-codec-generic snd-hda-codec-hdmi snd-hda-intel snd-hda-controller snd-usb-audio snd-hda-codec snd-usbmidi-lib snd-hwdep snd-seq-midi snd-seq-midi-event snd-pcm snd-rawmidi snd-seq snd-seq-device snd-timer (failed: modules still loaded: snd-hda-codec-analog snd-hda-codec-generic snd-hda-codec-hdmi snd-hda-codec snd-hwdep snd-pcm snd-timer).
Loading ALSA sound driver modules: snd-hda-codec-analog snd-hda-codec-generic snd-hda-codec-hdmi snd-hda-intel snd-hda-controller snd-usb-audio snd-hda-codec snd-usbmidi-lib snd-hwdep snd-seq-midi snd-seq-midi-event snd-pcm snd-rawmidi snd-seq snd-seq-device snd-timer.
blade@ubuntu:~$ 

```

looks like some modules refuse to load, how to sort this one?

---

### Post by Yellow Pasque on 2015-10-05
Give more info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

> looks like some modules refuse to load
From what I've seen, that's par for the course for that command. Some modules don't unload because they're still in use. I doubt it is related to your issue.

---

### Post by hopelessone on 2015-10-05
if I do:
```
sudo modprobe -v snd-hda-intel
sudo alsa force-reload
sudo modprobe -v snd-hda-intel
sudo alsa force-reload
```

it seems to work (until reboot)

hmm, suggestions?

---

### Post by Yellow Pasque on 2015-10-05
That probably means the upstart/systemd init script isn't running correctly. Again, get the detailed log (after you boot and before you un/load modules) to maybe find some clues: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by tgalati4 on 2015-10-05
It could be the order that the sound modules get loaded.  Because you have HDMI sound hardware, perhaps the order becomes important.

Put your *alsa force-reload* in /etc/rc.local (before the *exit 0* statement) and see if that works.

---

### Post by hopelessone on 2015-10-12
> **tgalati4 said:**
> It could be the order that the sound modules get loaded.  Because you have HDMI sound hardware, perhaps the order becomes important.

Put your *alsa force-reload* in /etc/rc.local (before the *exit 0* statement) and see if that works.

Yep! That did the trick! Many Thanks :)

---

### Post by tgalati4 on 2015-10-12
Because there are so many variations of PC hardware, it's hard to predict how modules will behave.  Your work-around using *alsa force-reload* is clever and sometimes the sledgehammer is the fix.  Otherwise you will spend a lot of time trying to find the one module and one Use Case why it is failing.  Your fix probably adds 2 seconds to your boot time, but the feeling of having working hardware is worth it.

I suspect you need a customized asound file and that will take some [troubleshooting]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure").

---

