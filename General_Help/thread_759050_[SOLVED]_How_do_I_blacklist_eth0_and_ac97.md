---
title: "[SOLVED] How do I blacklist eth0 and ac97?"
date: 2008-04-18
forum: General Help
---

### Post by ibuclaw on 2008-04-18
Hi all.

I have two motherboard devices that I want to** unload** and **blacklist**.
One is the onboard Ethernet Port and the other is the onboard AC97 Audio port.

On reason is to declunk my log files to I can get a good debug of my system if anything is going/goes wrong.
This is what my log is filled with at the moment.
```

Apr 18 14:08:04 fredbuntu kernel: [  817.058006] eth0: PHY reset until link up.
Apr 18 14:08:05 fredbuntu kernel: [  827.079994] eth0: PHY reset until link up.
Apr 18 14:08:06 fredbuntu kernel: [  837.101978] eth0: PHY reset until link up.
Apr 18 14:08:07 fredbuntu kernel: [  423.969104] eth0: PHY reset until link up.
Apr 18 14:08:08 fredbuntu kernel: [  861.612088] eth0: PHY reset until link up.
Apr 18 14:08:09 fredbuntu kernel: [  874.105180] eth0: PHY reset until link up.
Apr 18 14:09:10 fredbuntu kernel: [  884.127174] eth0: PHY reset until link up.
Apr 18 14:09:11 fredbuntu kernel: [  894.149142] eth0: PHY reset until link up.
Apr 18 14:09:12 fredbuntu kernel: [  904.171126] eth0: PHY reset until link up.
Apr 18 14:09:13 fredbuntu kernel: [  914.193111] eth0: PHY reset until link up.
Apr 18 14:09:14 fredbuntu kernel: [  924.215094] eth0: PHY reset until link up.
Apr 18 14:09:15 fredbuntu kernel: [  934.237074] eth0: PHY reset until link up.
Apr 18 14:10:16 fredbuntu kernel: [  944.259064] eth0: PHY reset until link up.
Apr 18 14:10:17 fredbuntu kernel: [  954.281043] eth0: PHY reset until link up.
Apr 18 14:10:18 fredbuntu kernel: [  481.882586] eth0: PHY reset until link up.
Apr 18 14:10:19 fredbuntu kernel: [  982.746803] eth0: PHY reset until link up.
Apr 18 14:10:20 fredbuntu kernel: [  992.768784] eth0: PHY reset until link up.
Apr 18 14:10:21 fredbuntu kernel: [ 1002.790772] eth0: PHY reset until link up.

```
etc, etc...

Now I have a small idea what my AC97 soundcard is, but I need confirmation. (To make sure I'm doing the right thing)
I think that it is **ac97_bus**...
```
:~$ lsmod | grep ac97
snd_ac97_codec        101028  1 snd_intel8x0
ac97_bus                3072  1 snd_ac97_codec
snd_pcm                78596  4 snd_usb_audio,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd                    56996  24 snd_rtctimer,snd_usb_audio,snd_usb_lib,snd_hwdep,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

```

As for my ethernet, I'm not too sure.
My wireless comes up:
```
:~$ lsmod | grep ath
ath_rate_sample        14336  1 
ath_pci               101024  0 
wlan                  207728  5 wlan_tkip,wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               192592  3 ath_rate_sample,ath_pci

```
But apparantly ethernet comes under a different naming convention
```
:~$ lsmod | grep eth
:~$

```

Any help would be great.

Thanks.
With Regards
Iain

---

### Post by eriqjaffe on 2008-04-18
If they're on the motherboard, why not just disable them in the BIOS?

---

### Post by unutbu on 2008-04-18
eriqjaffe's suggestion sounds good, but just to help you find out more about your hardware, here are some commands:

```
sudo lshw
lspci | grep -i audio
```

---

### Post by ibuclaw on 2008-04-18
> **eriqjaffe said:**
> If they're on the motherboard, why not just disable them in the BIOS?

I've generally nerver use my BIOS, so that didn't really come across to me as a solution.

I didn't know that you could control devices either!

So thanks for that one, it's better now.

Regards
Iain

---

