---
title: "Sound Problem"
date: 2006-12-02
forum: General Help
---

### Post by koulanji on 2006-12-02
As I have stated before, I have a sound problem in edgey eft, where my soundcard (Soundblaster Audigy 2ZS) works half of the time. In other words, if I start my computer I may have sound (gdm sound, splash screen sound, xmms, and so on), or I may have no sound all together. 

I was told in a previous thread to enter this (the command below) in the terminal to see if my device was an OEM version of the audigy or not

lsmod | grep emu

snd_emu10k1_synth 7808 0
snd_emux_synth 37120 1 snd_emu10k1_synth
snd_seq_virmidi 7296 1 snd_emux_synth
snd_seq_midi_emul 7296 1 snd_emux_synth
snd_seq 53360 9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,s nd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi _event
snd_emu10k1 124576 2 snd_emu10k1_synth
snd_rawmidi 25600 3 snd_seq_virmidi,snd_seq_midi,snd_emu10k1
snd_ac97_codec 96672 2 snd_emu10k1,snd_intel8x0
emu10k1_gp 4096 0
gameport 15368 2 emu10k1_gp
snd_seq_device 8972 8 snd_emu10k1_synth,snd_emux_synth,snd_seq_dummy,snd _seq_oss,snd_seq_midi,snd_seq,snd_emu10k1,snd_rawm idi
snd_util_mem 5120 2 snd_emux_synth,snd_emu10k1
snd_hwdep 9860 2 snd_emux_synth,snd_emu10k1
snd_pcm 80520 4 snd_emu10k1,snd_intel8x0,snd_ac97_codec,snd_pcm_os s
snd_timer 23172 3 snd_seq,snd_emu10k1,snd_pcm
snd 55428 16 snd_emux_synth,snd_seq_virmidi,snd_seq_oss,snd_seq ,snd_emu10k1,snd_rawmidi,snd_intel8x0,snd_ac97_cod ec,snd_pcm_oss,snd_mixer_oss,snd_seq_device,snd_hw dep,snd_pcm,snd_timer
snd_page_alloc 10504 3 snd_emu10k1,snd_intel8x0,snd_pcm

Then I entered these other two codes like you suggested and I got this

axisaudio@axisaudio-desktop:~$ sudo modprobe -r emu10k1
Password:
axisaudio@axisaudio-desktop:~$ sudo modprobe emu10k1x
FATAL: Module emu10k1x not found.

I was told by poof that I have the non OEM version of the audigy, so if anyone knows how to get past this problem, I'd be grateful

---

