---
title: "need a command to switching output mode like in alsamixer"
date: 2022-05-28
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2022-05-28
I have a sound card that the has a setting that switches between multichanel, stereo, and stereo (front panel) and i cam do this in alsamixer, how can i do this in a single command, i want to make a quick way to switch between front stereo and rear stereo, something i can put on a keyboard shortcut for example

---

### Post by TheFu on 2022-05-28
pacmd or pactl are the CLI tools for Pulse Audio. They can do anything that a GUI can do. Use xdotool and your Window Manager to connect the command/script to a specific key-chord.  The Window Manager used will determine how easy/hard this is to accomplish.  but start by getting the exact pacmd/pactl command you want to toggle between the three options.  You could make a single script with inputs of 1, 2, 3 or "mchan", "rear", "front" and have those options passed in using the WM xdotool key-chord.

BTW, I have no idea how to switch between front and rear stereo. I've not seen that.  So change between 5.1 and stereo would be either changing the track in a video file or changing the number of output channels. I don't know how to do it without deep looking in the manpages.  I figure you have the expertise to accomplish it.

---

### Post by pqwoerituytrueiwoq on 2022-05-28
"BTW, I have no idea how to switch between front and rear stereo."

not rear/front speakers, it toggle the rear ports and the case front panel output, cheap design on this card (ASUS XONAR DGX) uses what sounds like a relay to switch between the front port and the rear port, this is not a issue as long as i can switch on the fly in software and not a hardware level plug detection on the front port, the limitation is you can't use the front case audio header and the rear output at the same time

i need to be able to specify the correct sound card as i have 4 including hdmi

only tested the card on a diff board than it will go into, need to take the system apart to change the cooler and mod the PSU wiring (can you believe i ran out of molex plugs in 2022...)


did some more digging i think i need to use this, not sure

[FONT=courier new]amixer cset numid=XXX [0..2][/FONT]

trying to setup a mpd server with speakers in multiple rooms this will let me use 1 card for 2 rooms by switching front panel and rear panel outputs (can't run both at once on this card)

---

### Post by TheFu on 2022-05-28
If the system has pulse audio, which firefox has required for a few years now, then you can get a list of cards using 
```
pactl list short sinks

```and set the default using something like
```
pactl set-default-sink alsa_output.pci-0000_0a_00.3.analog-stereo
```

The names don't usually change.

If you plug and unplug ports, then there is a module called "module-switch-on-connect" responsible for setting newly connected audio devices as the default device.
```
pacmd load-module module-switch-on-connect
```
will enable it.  I find it problematic and prefer to not allow that by default.
```
pacmd [COLOR="#FF0000"]un[/COLOR]load-module module-switch-on-connect
```

pacmd and pactl have lots and lots of options. Spending 20 minutes playing with them should help helpful.  BTW, Pulse is often just a layer over ALSA, so if you have an ALSA method, it can keep being used.

---

### Post by #&amp;thj^% on 2022-05-28
> **TheFu said:**
> BTW, Pulse is often just a layer over ALSA, so if you have an ALSA method, it can keep being used.

yep
```
pactl list short sinks
53	alsa_output.usb-DisplayLink_UOEOS_Laptop_Dock_4307293310436-02.iec958-stereo	PipeWire	s16le 2ch 48000Hz	SUSPENDED
55	alsa_output.pci-0000_04_00.6.analog-stereo	PipeWire	s32le 2ch 48000Hz	SUSPENDED
195	bluez_output.F8_DF_15_7F_64_73.a2dp-sink	PipeWire	s16le 2ch 48000Hz	RUNNING

```

---

### Post by pqwoerituytrueiwoq on 2022-05-29
amixer works (sudo is needed over ssh if there is not a local session active)

```
chad@niceServer:~$ sudo amixer contents
numid=16,iface=MIXER,name='Headphone Playback Switch'
  ; type=BOOLEAN,access=rw------,values=1
  : values=on
numid=15,iface=MIXER,name='Headphone Playback Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=255,step=0
  : values=241,240
  | dBminmax-min=-125.50dB,max=0.00dB
numid=18,iface=MIXER,name='Front Mic Capture Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=-24,max=24,step=0
  : values=0,0
  | dBminmax-min=-12.00dB,max=12.00dB
numid=19,iface=MIXER,name='Line Capture Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=-24,max=24,step=0
  : values=0,0
  | dBminmax-min=-12.00dB,max=12.00dB
numid=17,iface=MIXER,name='Mic Capture Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=-24,max=24,step=0
  : values=0,0
  | dBminmax-min=-12.00dB,max=12.00dB
numid=20,iface=MIXER,name='Aux Capture Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=-24,max=24,step=0
  : values=0,0
  | dBminmax-min=-12.00dB,max=12.00dB
numid=22,iface=MIXER,name='ADC High-pass Filter Capture Enum'
  ; type=ENUMERATED,access=rw------,values=1,items=2
  ; Item #0 'Active'
  ; Item #1 'Frozen'
  : values=0
numid=21,iface=MIXER,name='Capture Source'
  ; type=ENUMERATED,access=rw------,values=1,items=4
  ; Item #0 'Mic'
  ; Item #1 'Front Mic'
  ; Item #2 'Line'
  ; Item #3 'Aux'
  : values=0
numid=8,iface=MIXER,name='IEC958 Loopback Switch'
  ; type=BOOLEAN,access=rw------,values=1
  : values=off
numid=9,iface=MIXER,name='IEC958 Validity Check Capture Switch'
  ; type=BOOLEAN,access=rw------,values=1
  : values=off
numid=2,iface=MIXER,name='IEC958 Playback Switch'
  ; type=BOOLEAN,access=rw------,values=1
  : values=off
numid=10,iface=MIXER,name='Analog Input Monitor Playback Switch'
  ; type=BOOLEAN,access=rw------,values=1
  : values=off
numid=11,iface=MIXER,name='Analog Input Monitor Playback Volume'
  ; type=INTEGER,access=rw---R--,values=1,min=0,max=1,step=0
  : values=1
  | dBscale-min=-6.00dB,step=6.00dB,mute=0
numid=14,iface=MIXER,name='Analog Output Playback Enum'
  ; type=ENUMERATED,access=rw------,values=1,items=3
  ; Item #0 'Stereo Headphones'
  ; Item #1 'Stereo Headphones FP'
  ; Item #2 'Multichannel'
  : values=0
numid=12,iface=MIXER,name='Digital Input Monitor Playback Switch'
  ; type=BOOLEAN,access=rw------,values=1
  : values=off
numid=13,iface=MIXER,name='Digital Input Monitor Playback Volume'
  ; type=INTEGER,access=rw---R--,values=1,min=0,max=1,step=0
  : values=1
  | dBscale-min=-6.00dB,step=6.00dB,mute=0
numid=1,iface=MIXER,name='Stereo Upmixing'
  ; type=ENUMERATED,access=rw------,values=1,items=2
  ; Item #0 'Front'
  ; Item #1 'Front+Surround'
  : values=0
numid=7,iface=PCM,name='IEC958 Capture Default',device=1
  ; type=IEC958,access=r-------,values=1
  : values=[AES0=0x00 AES1=0x00 AES2=0x00 AES3=0x00]
numid=6,iface=PCM,name='IEC958 Capture Mask',device=1
  ; type=IEC958,access=r-------,values=1
  : values=[AES0=0xff AES1=0xff AES2=0xff AES3=0xff]
numid=4,iface=PCM,name='IEC958 Playback Con Mask',device=1
  ; type=IEC958,access=r-------,values=1
  : values=[AES0=0x3e AES1=0xff AES2=0x00 AES3=0x00]
numid=3,iface=PCM,name='IEC958 Playback Default',device=1
  ; type=IEC958,access=rw------,values=1
  : values=[AES0=0x04 AES1=0x82 AES2=0x00 AES3=0x00]
chad@niceServer:~$ sudo amixer cget numid=14
numid=14,iface=MIXER,name='Analog Output Playback Enum'
  ; type=ENUMERATED,access=rw------,values=1,items=3
  ; Item #0 'Stereo Headphones'
  ; Item #1 'Stereo Headphones FP'
  ; Item #2 'Multichannel'
  : values=0
chad@niceServer:~$ sudo amixer cset numid=14 1
numid=14,iface=MIXER,name='Analog Output Playback Enum'
  ; type=ENUMERATED,access=rw------,values=1,items=3
  ; Item #0 'Stereo Headphones'
  ; Item #1 'Stereo Headphones FP'
  ; Item #2 'Multichannel'
  : values=1
chad@niceServer:~$ sudo amixer cget numid=14
numid=14,iface=MIXER,name='Analog Output Playback Enum'
  ; type=ENUMERATED,access=rw------,values=1,items=3
  ; Item #0 'Stereo Headphones'
  ; Item #1 'Stereo Headphones FP'
  ; Item #2 'Multichannel'
  : values=1
chad@niceServer:~$
```

this box does not have pulse audio installed (it is a headless server running a mpd service)

edit: i can specify a card by using -c, 0 is the 1st card in alsamixer
 [FONT=courier new]amixer -c 0 cget numid=14[/FONT]

---

### Post by TheFu on 2022-05-30
You don't need to use sudo on the remote system. Just add your normal userid to the "audio" group and verify that the DSP devices in /dev/ allow the audio group write access.

I have a few mpd servers.  Let me check.
They all use the 'mpd' userid. 
```
$ id mpd
uid=127(mpd) gid=29(audio) groups=29(audio)
```

 In the mpd.conf file, I remember specifying the device as:
```
audio_output {
        type            "alsa"
        name            "istar ALSA Device"
        device          **[COLOR="#FF0000"]"hw:1,0"[/COLOR]**        # optional
        mixer_type      "software"      # optional
}

```

On another mpd server:
```
audio_output {
        type            "alsa"
        name            "My ALSA Device"
        mixer_type      "software"      # optional
}
```

Besides specifying the audio device on 1 system, I made the mixer as software on both.  My other mpd server isn't on the network now, so I can't check it easily.

I think I had to allow mpd networking in the mpd.conf file too. That setting is:
```
bind_to_address         "any"
```

A few of my Linux desktops are setup with scripts to do mpc or ncmpc connecting to any of the 3 mpd servers. In my office, there's 1. Another in the bedroom and another in the movie-room/den.  Letting each room have different audio playing keeps everyone happier.  If you need different cards from the same mpd server, I suppose you could use different mpd.conf files.  When starting mpd, the last option is the config file.  So if you needed multiple instances, just listen on different ports.

There's probably many other things that are too hard to share here in your setup.

---

### Post by pqwoerituytrueiwoq on 2022-05-30
did not realize you could do that, but i am just going for a 1 user setup, just wanted to be able to switch playback between multiple rooms and just need more outputs, this asus dgx allows software switching for it's front and rear panel so i can have 2 outs, but only 1 at a time, for my use case this is as good as using 2 sound cards

I may need a usb DAC or 2 (i ran out of PCIe slots; 2 sound cards, NIC, and a sata card)

regarding sudo, if do not have a active session on the TTY (logged in at the local box), this is what alsamizer gives me
```
$ alsamixer  
ALSA lib confmisc.c:855:(parse_card) cannot find card '0'
ALSA lib conf.c:5178:(_snd_config_evaluate) function snd_func_card_inum returned error: No such file or directory
ALSA lib confmisc.c:422:(snd_func_concat) error evaluating strings
ALSA lib conf.c:5178:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1334:(snd_func_refer) error evaluating name
ALSA lib conf.c:5178:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:5701:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib control.c:1528:(snd_ctl_open_noupdate) Invalid CTL default
cannot open mixer: No such file or directory
```

i do not really care, once i have this setup i will have a button i can press (for example on a joypad) to do the actions i want, if that does not workout i can just use a web ui i am gonna throw together

mpd has access to the audio devices, as for my mpd configs i have this stuff (do not really understand what all the these settings do, but it works so...)

```
audio_output {
       type            "alsa"
       name            "ASUS DGX"
       device          "hw:CARD=DGX,DEV=0"     # optional
##      mixer_type      "hardware"      # optional
##      mixer_device    "default"       # optional
       mixer_control   "PCM"           # optional
       mixer_index     "0"             # optional
       buffer_time     "5000000"       # optional
}
audio_output {
       type            "alsa"
       name            "SB Audigy 2 ZS Standard Playback"
       device          "hw:CARD=Audigy2,DEV=0" # optional
##      mixer_type      "hardware"      # optional
##      mixer_device    "default"       # optional
       mixer_control   "PCM"           # optional
       mixer_index     "0"             # optional
       buffer_time     "5000000"       # optional
}
audio_output {
       type            "alsa"
       name            "SB Audigy 2 ZS Multichannel PT Playback"
       device          "hw:CARD=Audigy2,DEV=2" # optional
##      mixer_type      "hardware"      # optional
##      mixer_device    "default"       # optional
       mixer_control   "PCM"           # optional
       mixer_index     "0"             # optional
       buffer_time     "5000000"       # optional
}
audio_output {
       type            "alsa"
       name            "SB Audigy 2 ZS Multichannel Playback"
       device          "hw:CARD=Audigy2,DEV=3" # optional
##      mixer_type      "hardware"      # optional
##      mixer_device    "default"       # optional
       mixer_control   "PCM"           # optional
       mixer_index     "0"             # optional
       buffer_time     "5000000"       # optional
}
audio_output {
       type            "alsa"
       name            "SB Audigy 2 ZS p16v"
       device          "hw:CARD=Audigy2,DEV=4" # optional
##      mixer_type      "hardware"      # optional
##      mixer_device    "default"       # optional
       mixer_control   "PCM"           # optional
       mixer_index     "0"             # optional
       buffer_time     "5000000"       # optional
}
audio_output {
       type            "alsa"
       name            "SB Audigy 2 ZS rear"
       device          "rear:CARD=Audigy2,DEV=0"       # optional
##      mixer_type      "hardware"      # optional
##      mixer_device    "default"       # optional
       mixer_control   "PCM"           # optional
       mixer_index     "0"             # optional
       buffer_time     "5000000"       # optional
}
audio_output {
       type            "alsa"
       name            "HDMI test 1"
       device          "hw:CARD=Generic,DEV=3" # optional
##      mixer_type      "hardware"      # optional
##      mixer_device    "default"       # optional
       mixer_control   "PCM"           # optional
       mixer_index     "0"             # optional
       buffer_time     "5000000"       # optional
}
audio_output {
       type            "alsa"
       name            "HDMI test 2"
       device          "hw:CARD=Generic,DEV=7" # optional
##      mixer_type      "hardware"      # optional
##      mixer_device    "default"       # optional
       mixer_control   "PCM"           # optional
       mixer_index     "0"             # optional
       buffer_time     "5000000"       # optional
}
audio_output {
       type            "alsa"
       name            "Onboard Analog Out"
       device          "hw:CARD=Generic_1,DEV=0"       # optional
##      mixer_type      "hardware"      # optional
##      mixer_device    "default"       # optional
       mixer_control   "PCM"           # optional
       mixer_index     "0"             # optional
       buffer_time     "5000000"       # optional
}

```
Using the one without software conversions will make it so other software can't access the speakers while they are being used, but the audio quality should be better
```
aplay -L | grep without -B2
hw:CARD=DGX,DEV=0
   Xonar DGX, Multichannel
   Direct hardware device without any conversions
hw:CARD=DGX,DEV=1
   Xonar DGX, Digital
   Direct hardware device without any conversions
-- 
hw:CARD=Audigy2,DEV=0
   SB Audigy 2 ZS [SB0350], ADC Capture/Standard PCM Playback
   Direct hardware device without any conversions
hw:CARD=Audigy2,DEV=2
   SB Audigy 2 ZS [SB0350], Multichannel Capture/PT Playback
   Direct hardware device without any conversions
hw:CARD=Audigy2,DEV=3
   SB Audigy 2 ZS [SB0350], Multichannel Playback
   Direct hardware device without any conversions
hw:CARD=Audigy2,DEV=4
   SB Audigy 2 ZS [SB0350], p16v
   Direct hardware device without any conversions
-- 
hw:CARD=Generic,DEV=3
   HD-Audio Generic, HDMI 0
   Direct hardware device without any conversions
hw:CARD=Generic,DEV=7
   HD-Audio Generic, HDMI 1
   Direct hardware device without any conversions
-- 
hw:CARD=Generic_1,DEV=0
   HD-Audio Generic, ALC887-VD Analog
   Direct hardware device without any conversions

```

---

