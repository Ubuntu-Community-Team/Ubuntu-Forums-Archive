---
title: "Soundcard not recognized."
date: 2007-05-20
forum: General Help
---

### Post by KillHartman on 2007-05-20
Hi all, im relativly new to linux but heres my deal;
I have everything working fine except for my sound, when i used windows 10 minutes before installing the sound worked fine but on the live cd and the actual installation the sound does not work and everything i try i get the "No device to control" error. I also tried switching the onboard sound ON but to no avail, it gave me a linux boot error and i had to turn it back off. Here later im gonig to remove it and move it to a new pci slot but if anyone knows of something that will help to get my card recognized it would be appreciated.

---

### Post by mbradlcu on 2007-05-21
it's a little strange that your machine won't boot with the on board sound card enabled,, anyway, 2 ways to check into this. First see if Linux recognizes you're sound card, either by using the gui "system" -> "preference" -> "hardware manager", or by running this cool command from the command line:
```
lshw
```
here's what I get:
 *-multimedia
             description: Multimedia audio controller
             product: SB Live! EMU10k1
             vendor: Creative Labs
             physical id: 7
             bus info: pci@00:07.0
             version: 08
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=EMU10K1_Audigy latency=32 maxlatency=20 mingnt=2
             resources: ioport:d000-d01f irq:18

if you do see your sound card then it's time to check out if the correct modules aka drivers are loaded, on the command like run:
l```
lsmod
```
here's the output of intrest on my system:
snd_emu10k1_synth       9216  0 
snd_emux_synth         39936  1 snd_emu10k1_synth
snd_seq_virmidi         9216  1 snd_emux_synth
snd_seq_midi_emul       8960  1 snd_emux_synth
snd_emu10k1           133024  2 snd_emu10k1_synth
snd_ac97_codec        117720  1 snd_emu10k1
joydev                 12928  0 
ac97_bus                3968  1 snd_ac97_codec
snd_pcm_oss            49536  0 
snd_mixer_oss          19840  1 snd_pcm_oss
snd_pcm                92808  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         11792  2 snd_emu10k1,snd_pcm
snd_util_mem            6656  2 snd_emux_synth,snd_emu10k1
snd_hwdep              12168  2 snd_emux_synth,snd_emu10k1
snd_seq_dummy           5380  0 
snd_seq_oss            36608  0 
usb_storage            80448  0 
snd_seq_midi           11008  0 
snd_rawmidi            29696  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event      9856  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi

another command to check what's going on is:
```
dmesg
```
it's the output of what the kernel sees at boot

---

