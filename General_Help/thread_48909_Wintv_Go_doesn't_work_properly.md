---
title: "Wintv Go doesn't work properly"
date: 2005-07-14
forum: General Help
---

### Post by Holg on 2005-07-14
Hi there,

First of all:

I just switched to ubuntu and I must say that I really like it! Really good work!


I have ubuntu hoary running on a AMD 1.900+, Nvidia TNT2, Wintv Go,

Software:

Xawtv, TvTime, MythTv

My Problem:

The colour in Xawtv, TvTime and MythTv is not correct. It is more black & white with some colours - looks like a retro design  ;-) 

Sometimes - I can't excatly figure out at what point, but mostly after rebooting the system and running scantv - I have a normal picture in xawtv. Then after starting tvtime or mythtv the picture gets this strange colour again.

When the colour is correct (only in xawtv) I can stop and start xawtv as often as i want to and the colour is everytime correct... but as soon as i start tvtime or mythtv the colours mess up and I only see those strange colours...

2 Problem:
The only sound I get while watching TV is a rschhhhhrschhhhrschhhh  ;-)  - this happens in every application and is present over the soundcard and directly from the TV-Card (so I don't think it is a soundcard issue)

But - guess what - once I could hear the sound from the TV channel... in all applications, but then - I don't know why - the noise startet again.

I have set everything to PAL-N - I also tried PAL-NC. For the channels I use europe-west. With NexTViev I can get the whole Inormation about the channels...

Is there annother systemwide parameter wich says: PAL or NTSC ?

I've googled and googled but I couldn't find something.
Pleas help
Thanks in advance

Hog

I will post the lsmod and modprobe -l

---

### Post by Holg on 2005-07-14
like I said I have a Hauppauge Wintv Go 

lspci -video says:

0000:00:0a.0 Multimedia video controller: Conexant Winfast TV2000 XP (rev 03)
        Subsystem: Hauppauge computer works Inc.: Unknown device 3400
        Flags: bus master, medium devsel, latency 32, IRQ 11
        Memory at d4000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: [44] Vital Product Data
        Capabilities: [4c] Power Management version 2

0000:00:0a.1 Multimedia controller: Conexant: Unknown device 8811 (rev 03)
        Subsystem: Hauppauge computer works Inc.: Unknown device 3400
        Flags: bus master, medium devsel, latency 32, IRQ 11
        Memory at d5000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: [44] Vital Product Data
        Capabilities: [4c] Power Management version 2





lsmod says:

Module                  Size  Used by
------ snip -----
video                  15972  0
sony_acpi               5928  0
------ snip -----
ac                      4676  0
snd_via82xx            27520  1
snd_ac97_codec         74144  1 snd_via82xx
snd_pcm_oss            52132  0
snd_mixer_oss          19680  2 snd_pcm_oss
snd_pcm                94696  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              25060  1 snd_pcm
snd_page_alloc          9732  2 snd_via82xx,snd_pcm
snd_mpu401_uart         7680  1 snd_via82xx
snd_rawmidi            24480  1 snd_mpu401_uart
snd_seq_device          8460  1 snd_rawmidi
snd                    55012  9 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore              10016  2 snd
------ snip -----
8139cp                 20416  0
8139too                25856  0
mii                     4896  2 8139cp,8139too
tuner                  21796  0
cx8800                 30828  0
cx88xx                 49108  1 cx8800
i2c_algo_bit            9800  1 cx88xx
video_buf              21732  2 cx8800,cx88xx
i2c_core               22320  4 i2c_viapro,tuner,cx88xx,i2c_algo_bit
v4l1_compat            14244  1 cx8800
v4l2_common             5664  1 cx8800
btcx_risc               4712  2 cx8800,cx88xx
videodev                9792  2 cx8800,cx88xx
pci_hotplug            33488  0
via_agp                 9344  1
agpgart                33608  1 via_agp
analog                 11584  0
------ snip -----



modprobe -l | grep bttv
/lib/modules/2.6.10-5-686/kernel/drivers/media/video/bttv.ko

modprobe -l | grep media
----- snip ------
/lib/modules/2.6.10-5-686/kernel/drivers/media/video/cx88/cx88xx.ko
/lib/modules/2.6.10-5-686/kernel/drivers/media/video/cx88/cx8802.ko
/lib/modules/2.6.10-5-686/kernel/drivers/media/video/cx88/cx8800.ko
/lib/modules/2.6.10-5-686/kernel/drivers/media/video/cx88/cx88-blackbird.ko

dmesg | grep bttv      returns no result

dmesg | grep cx       returns a lot of

cx88[0]/0: AUD_STATUS: 0xfdb2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xfd72 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xfdb2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xfd32 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xfcf2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
(...)


one more thing... when I start xawtv it tells me 

This is xawtv-3.94, running on Linux/i686 (2.6.10-5-686)
WARNING: v4l-conf is compiled without DGA support.
/dev/video0 [v4l2]: no overlay support
v4l-conf had some trouble, trying to continue anyway
/root/.xawtv:120: syntax error
Xlib:  extension "GLX" missing on display ":0.0".

but it starts and I can watch tv (without sound and with strange colours)

Holg

---

