---
title: "No sound.  Tried several things.  It worked before."
date: 2015-09-15
forum: General Help
---

### Post by Nixarter on 2015-09-15
SOLVED!!! See [ This post for a simple breakdown](http://ubuntuforums.org/showthread.php?t=2294972&p=13357689#post13357689), for those who would like a quick solution.

My sound in a fresh install of Mint 17 doesn't work right now (though the solutions should be the same or similar as with Ubuntu).  I've also had this issue with my ubuntu installs.  I just lived without it... never really put in the effort to troubleshoot it.


The Tahiti (HDMI output via graphics card) works great... but I  don't want to move my computer to the theater room to have my receiver output my computer sound :o   (Unless I'm watching a movie, of course).  I just want my headphones and desktop speakers to work.


I've been searching for quite a while.  It worked out-of-the-box with one version of linux (either an ubuntu or mint version, but I can't remember which).

I've tried:

force-restarting alsa

adding in the following to my conf file ```
options snd-hda-intel model=generic
``` (and also "auto")

reinstalling the extras.

computer sees sound device correctly, both the digital and analog outputs.  But I can't get any sound out at all.

other info:

```
mint@local ~ $ aplay -l | grep card
card 0: HDMI [HDA Intel HDMI], device 3: HDMI 0 [HDMI 0]
card 0: HDMI [HDA Intel HDMI], device 7: HDMI 1 [HDMI 1]
card 0: HDMI [HDA Intel HDMI], device 8: HDMI 2 [HDMI 2]
card 1: PCH [HDA Intel PCH], device 0: CA0132 Analog [CA0132 Analog]
card 1: PCH [HDA Intel PCH], device 1: CA0132 Digital [CA0132 Digital]
card 2: HDMI_1 [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
card 2: HDMI_1 [HDA ATI HDMI], device 7: HDMI 1 [HDMI 1]
card 2: HDMI_1 [HDA ATI HDMI], device 8: HDMI 2 [HDMI 2]
card 2: HDMI_1 [HDA ATI HDMI], device 9: HDMI 3 [HDMI 3]
card 2: HDMI_1 [HDA ATI HDMI], device 10: HDMI 4 [HDMI 4]
card 2: HDMI_1 [HDA ATI HDMI], device 11: HDMI 5 [HDMI 5]

```  It's card 1, and it is selected as active in the sound options.  :/

No idea what this next bit means, but have at it if it helps: ```
mint@local ~ $ sudo lsmod | grep snd
[sudo] password for mint: 
snd_seq_midi           13564  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                63074  2 snd_seq_midi_event,snd_seq_midi
snd_rawmidi            30876  1 snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_hda_intel          30469  7 
snd_hda_controller     30228  1 snd_hda_intel
snd_hda_codec_ca0132    53571  1 
snd_hda_codec_hdmi     47548  2 
snd_hda_codec         139682  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_controller,snd_hda_codec_ca0132
snd_hwdep              17698  1 snd_hda_codec
snd_pcm               104112  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
snd_timer              29562  2 snd_pcm,snd_seq
snd                    79468  24 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_hda_codec_ca0132
soundcore              15047  2 snd,snd_hda_codec

```

I've tried every combination of devices and settings for outputs... nothing.  tried all ports.  headphones, speakers.  nothing.

---

### Post by Nixarter on 2015-09-15
I've attached 2 images.  one is the alsamixer once I navigate to the sound devices.  The other (SP DIF) is what I see when I open alsamixer in terminal.

It almost looks like SP DIF is default and it is trying to output the sound through that.  But I don't want that.  I want just regular stereo for my headphones and desktop speakers.  I've disabled both the SP DIF and HDMI (tahiti) outputs... but I get the same results in alsamixer at startup.  it says SP DIF is off... but still seems to default to output through it.

I'm SO confused right now.

---

### Post by Nixarter on 2015-09-15
down the rabbit hole I go...

so I found this command to list active sound modules (devices?):  ```
mint@local ~ $ cat /proc/asound/modules
 0 snd_hda_intel
 1 snd_hda_intel
 2 snd_hda_intel

```

At first I thought these were all 3 names for one device (as I thought I had disabled 2 of my 3 sound devices).  I thought this meant analog audio, pcm, and some other option/output method from my device.  Then I found this:

[https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/209892](https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/209892)

rand the command, and I had similar permission issues, and I used his workaround.  It turns out that all those "snd_hda_intel" modules are actually the 3 different devices.  

```
!!################################
!!ALSA Information Script v 0.4.64
!!################################

!!Script ran on: Tue Sep 15 17:10:57 UTC 2015


!!Linux Distribution
!!------------------

Linux Mint 17.2 Rafaela \n \l DISTRIB_ID=LinuxMint DISTRIB_DESCRIPTION="Linux Mint 17.2 Rafaela" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu 14.04.2 LTS" HOME_URL="http://www.ubuntu.com/" SUPPORT_URL="http://help.ubuntu.com/" BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"


!!DMI Information
!!---------------

Manufacturer:      Gigabyte Technology Co., Ltd.
Product Name:      G1.Sniper Z87
Product Version:   To be filled by O.E.M.
Firmware Version:  F4


!!Kernel Information
!!------------------

Kernel release:    3.16.0-38-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         x86_64
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     k3.16.0-38-generic
Library version:    
Utilities version:  1.0.27.2


!!Loaded ALSA modules
!!-------------------

snd_hda_intel
snd_hda_intel
snd_hda_intel


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xf7e10000 irq 47
 1 [HDMI_1         ]: HDA-Intel - HDA Intel HDMI
                      HDA Intel HDMI at 0xf7e14000 irq 46
 2 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xf7d60000 irq 48


!!PCI Soundcards installed in the system
!!--------------------------------------

00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Tahiti XT HDMI Audio [Radeon HD 7970 Series]


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------

00:03.0 0403: 8086:0c0c (rev 06)
    Subsystem: 8086:2010
--
00:1b.0 0403: 8086:8c20 (rev 05)
    Subsystem: 1458:a026
--
01:00.1 0403: 1002:aaa0
    Subsystem: 1043:aaa0


!!Modprobe options (Sound related)
!!--------------------------------

snd_atiixp_modem: index=-2
snd_intel8x0m: index=-2
snd_via82xx_modem: index=-2
snd_usb_audio: index=-2
snd_usb_caiaq: index=-2
snd_usb_ua101: index=-2
snd_usb_us122l: index=-2
snd_usb_usx2y: index=-2
snd_cmipci: mpu_port=0x330 fm_port=0x388
snd_pcsp: index=-2
snd_usb_audio: index=-2
snd_hda_intel: index=1,0
```

That is the important bit, though.  The Gigabyte model is my motherboard (this is a gaming rig I built- not an off-the-shelf desktop).

OK, I think the problem is that something is defaulted to use either one of the HDMI outputs, OR the digital (SP_DIF) from my onboard card (that also has analog outputs to the headphone port up front and in back).  I need to somehow override the defaults, or disable other options, to force ONLY the analog outputs.  First step would be to somehow force hda_sda_intel device 0.  Also, i would probably have to force device 0 to be in analog mode.  Maybe the device itself is defaulted to digital, and I have to change something at device startup?

Any idea how to do this?  Any other ideas in general?

The search continues :o

ATM, the sound output is static (which could mean muted, just electronic noise from the computer).  It could also mean that the correct output device is being used... just outputting a low-level digital signal, which would sound like static if played through my analog speaker system.  I'm not sure which is the case just yet.

---

### Post by QDR06VV9 on 2015-09-15
See if this helps.
[http://ubuntu4me.blogspot.com/2012/03/ubuntu-default-sound-card-select.html](http://ubuntu4me.blogspot.com/2012/03/ubuntu-default-sound-card-select.html)

And in case you did not know this already The MM in your picture of alsamixer down at the bottom.
You can unmute them by sliding over to the ones that have no values set by pressing keyboard>m by using the right and left arrow key's
Then increase the volumes.
You also could install (pavucontrol)
> PulseAudio Volume Control (pavucontrol) is a simple GTK+ based volumecontrol tool (mixer) for the PulseAudio sound server. In contrast to
classic mixer tools this one allows you to control both the volume of
hardware devices and of each playback stream separately. It also allows
you to redirect a playback stream to another output device without
interrupting playback.
But I agree it shows HDMI as default.
Kind regards

---

### Post by Nixarter on 2015-09-17
> **runrickus said:**
> 

And in case you did not know this already The MM in your picture of alsamixer down at the bottom.
You can unmute them by sliding over to the ones that have no values set by pressing keyboard>m by using the right and left arrow key's
Then increase the volumes.

thank you!!!!!!!!!!!!!!!!!!!!

So everything was working (probably since the very beginning... sigh). However, the most common outputs are muted by default (for whatever reason).  So I muted all channels, and unmuted them one-by-one to find out which was the one.  It was "HP/Speaker" that was the analog output (ie headphones).  I unmuted both of them (assuming front and back panels.  front for headphones, and I use back for speakers).  For whatever reason, the optical output doesn't seem to work, but that is fine for me. I'd rather not have to rely on a receiver for my computer speakers :p


Hopefully I can save lots of others from the hours and hours of hell I had to endure to get to the bottom of this.

For those following along at home:

```
alsamixer
```

this brings up alsamixer.  Anything "mm" is MUTED.  headphone outputs on mine were "HP/Speaker".

To unmute, simply use left/right arrow keys to select an output.  Then type "m" to toggle mute/unmute.  If a number value is shown, it is unmuted.  Then use up/down arrow keys to adjust volume.

You should be set!

I did NOT have to reset, or log in/out for changes to take effect.  they were immediate.  I had a long youtube video playing in the background to hear sound as it came on and off.

You may need to use the process of elimination to find all the outputs you plan to use, and unmute them.  As far as I can tell, this will make it output on all unmuted channels simultaneously all the time until muted again (from within alsamixer, or otherwise).

Happy trails!

Computer specs:  gigabyte G1 Sniper z87 (probably same story for G1 Sniper z97, or any Gigabyte Soundcore motherboard).

---

