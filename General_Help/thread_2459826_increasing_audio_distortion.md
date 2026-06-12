---
title: "increasing audio distortion"
date: 2021-03-26
forum: General Help
---

### Post by JamButty on 2021-03-26
In the past month or so, my audio output is increasingly distorted. Sound has the same distortion whether from speakers, headphone jacked into amp or jacked into desktop tower. The same recordings moved to my phone with the same headphones are crystal clear.
All the audio posts seem to be about no audio at all, so I have not found related info. There have been no hw changes to the system and no sw upgrades other than the standard updater feed
I am running 20.04.2 LTS 
> $ sudo lspci |grep Audio
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)


Drivers data in case that helps.
> $ /sbin/lsmod | grep snd
snd_hda_codec_realtek   131072  1
snd_hda_codec_generic    81920  1 snd_hda_codec_realtek
ledtrig_audio          16384  1 snd_hda_codec_generic
snd_hda_codec_hdmi     61440  1
snd_hda_intel          53248  6
snd_intel_dspcfg       24576  1 snd_hda_intel
snd_hda_codec         139264  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek
snd_hda_core           94208  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek
snd_hwdep              20480  1 snd_hda_codec
snd_pcm               114688  5 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_core
snd_seq_midi           20480  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            36864  1 snd_seq_midi
snd_seq                69632  2 snd_seq_midi,snd_seq_midi_event
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
snd_timer              40960  2 snd_seq,snd_pcm
snd                    94208  22 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_pcm,snd_rawmidi
soundcore              16384  1 snd



Any advice appreciated.

---

### Post by CatKiller on 2021-03-26
I would check in alsamixer that none of the channels' volumes (particularly any that are labelled as Boost) have been pushed up too far. Depending on the sound of the distortion I'd also check the sample rate of the files against the sample rate that they're being played at.

---

### Post by JamButty on 2021-03-27
Took me a while to understand anything about alsamixer, but it did not change it.Boost channels were at zero. After setting all normal channels to 50s (top of green range), the distortion was the same. Now I have an additional issue. I did not know how to check the sample rate/playback rates. Hoping to get some answers in Audacity, I started that. It asked me to enable Alsa for Audacity snap. It had never asked that before, but I had never used alsamixer before, so I thought was due to that. I enabled it as requested with
> sudo snap connect audacity:alsa

after which Audacity could no longer play back anything. I even pulled up an old project file from a couple of years ago - same problem. I get: (see attachment)
> Error opening sound device.
Try changing the audio host, playback device and the project sample rate.

none of those items have been changed, afaik, as I have no idea how to do that on the fly. 
Now I see the default playback sample rate stated in */etc/pulse/daemon.conf *is
> default-sample-rate = 44100
 alternate-sample-rate = 48000

the sample rate for the file I am testing with is also 44100.

---

### Post by Autodave on 2021-03-27
To get Audacity working again you probably need to go into Audacity -> Edit -> Preferences -> Devices

---

### Post by JamButty on 2021-03-28
Audacity working again after de/re-installing it. Alsa is the only host choice, so impossible to change that, playback device and sample rate were/are correct so something else was buggy. It asks me to issue that
sudo snap connect audacity:alsa
every time I start it now, but I can live with that.  Another option (I found too late) would have been deleting
/home/(account)/snap/audacity/common/Always use PulseAudio. I thought PulseAudio was a default app in the basic distro, but I do not have it installed, so that may have been the problem.

So, Audacity is ok, distortion remains. Maybe a stupid question but is it normal for onboard sound hardware to simply "go bad"? I am willing to buy a sound card if needed, but I don't know what the current issue is so that may not solve it.

---

### Post by CelticWarrior on 2021-03-28
> [COLOR=#000000]is it normal for onboard sound hardware to simply "go bad"?[/COLOR]
Yes, like everything else but if it's an hardware issue the chip itself is the least likely culprit. Other issues in the motherboard are more plausible, traces, capacitors, etc.

---

### Post by HermanAB on 2021-03-28
To determine whether it is HW or SW, boot from install media and play something.

---

### Post by JamButty on 2021-03-28
Installed pavucontrol and having sporadic success with that. Will continue to try to isolate why and when the distortion returns.

---

### Post by JamButty on 2021-03-30
Marking solved. Though over-amplification in the default prog settings/sound is not/was not enabled and though alsamixer did not indicate it, pavucontrol showed the analog line-out was set at 135%(+7.76Db). Returning to 100% or below eliminated distortion. It still jumps past that sometimes for reasons I have not tracked yet, but I can live with that now that I can correct it.
For 2 days, though, from the point I installed pavucontrol, my front headphone port was suddenly dead. This persisted through multiple reboots and nothing in alsamixer or pavucontrol gave any clues, but it worked fine using an install disk, then after suddenly ok again on the normal boot. Tangential weirdness I can ignore for now too.

---

### Post by CatKiller on 2021-03-30
> **JamButty said:**
> Though over-amplification in the default prog settings/sound is not/was not enabled and though alsamixer did not indicate it, pavucontrol showed the analog line-out was set at 135%(+7.76Db). Returning to 100% or below eliminated distortion. It still jumps past that sometimes for reasons I have not tracked yet, but I can live with that now that I can correct it.

There's a setting somewhere, although I can't remember exactly where I saw it, for whether you'll allow a volume to go above 100%. It's not generally a good idea, since it leads to distortion, but the option is there. If you can find it, you should be able to keep the volume below 100% always.

PulseAudio has an option for "flat volumes," which is kinda terrible and was enabled by default for a while. Having the option enabled means that some applications crank the volume up to full always.

---

### Post by JamButty on 2021-03-31
CatKiller - I think you talking about the settings/sound over-amplification option. When that first came out, I tried it once out of curiosity and never used it again. I have no idea how line-out got jacked up to 135%, but I'm just glad it's sorted now.

---

### Post by CatKiller on 2021-03-31
I'm talking about two things: how it was allowed to go over 100% at all, and why it gets put up that high without you deliberately doing it.

---

