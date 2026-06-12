---
title: "No sound of any sort"
date: 2018-12-30
forum: General Help
---

### Post by gunner220 on 2018-12-30
Ubuntu18.04 and am very pleased with the exception of there being no sound of any sort. No notifications, no sound with videos/YouTube, and no music. Just using the computer speaker. Bios shows it enabled. The sound level is not muted.

Just making me a little crazy cause I can't figure it out. Thanx in advance for any help.

---

### Post by Autodave on 2018-12-31
Some specs on your equipment would probably help us.

---

### Post by gunner220 on 2019-01-02
Autodave they would at that - Apologies, Dell XPS 8500 Desktop, Intel i5-3350P CPU @ 10 GHZx4, !8.04 LTS 64 bit,12 GB RAM. All sound info from PC below
[TABLE]
[TR]
[TD="class: field"]snd_hda_intel
[/TD]
[TD="class: value"]Intel HDA driver[/TD]
[/TR]
[TR]
[TD="class: field"]snd_hda_codec[/TD]
[TD="class: value"]HDA codec core[/TD]
[/TR]
[TR]
[TD="class: field"]snd_hda_core[/TD]
[TD="class: value"]HD-audio bus[/TD]
[/TR]
[TR]
[TD="class: field"]snd_hwdep[/TD]
[TD="class: value"]Hardware dependent layer[/TD]
[/TR]
[TR]
[TD="class: field"]snd_pcm[/TD]
[TD="class: value"]Midlevel PCM code for ALSA.[/TD]
[/TR]
[TR]
[TD="class: field"]ip6table_filter[/TD]
[TD="class: value"]ip6tables filter table[/TD]
[/TR]
[TR]
[TD="class: field"]snd_seq_midi[/TD]
[TD="class: value"]Advanced Linux Sound Architecture sequencer MIDI synth.[/TD]
[/TR]
[TR]
[TD="class: field"]snd_seq_midi_event[/TD]
[TD="class: value"]MIDI byte <-> sequencer event coder[TABLE]
[TR]
[TD="class: field"]snd_seq[/TD]
[TD="class: value"]Advanced Linux Sound Architecture sequencer.[/TD]
[/TR]
[TR]
[TD="class: field"]ecdh_generic[/TD]
[TD="class: value"]ECDH generic algorithm[/TD]
[/TR]
[TR]
[TD="class: field"]lpc_ich[/TD]
[TD="class: value"]LPC interface for Intel ICH[/TD]
[/TR]
[TR]
[TD="class: field"]snd_seq_device[/TD]
[TD="class: value"]ALSA sequencer device management[/TD]
[/TR]
[TR]
[TD="class: field"]snd_timer[/TD]
[TD="class: value"]ALSA timer interface[/TD]
[/TR]
[TR]
[TD="class: field"]snd[/TD]
[TD="class: value"]Advanced Linux Sound Architecture driver for soundcards.[/TD]
[/TR]
[TR]
[TD="class: field"]mei_me[/TD]
[TD="class: value"]Intel(R) Management Engine Interface[/TD]
[/TR]
[TR]
[TD="class: field"]soundcore[/TD]
[TD="class: value"]Core sound module[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
           
[TABLE]
[TR]
[TD="class: field"]                              Audio Adapter[/TD]
[TD="class: value"]HDA-Intel - HDA Intel PCH[/TD]
[/TR]
[TR]
[TD="class: field"]                              Audio Adapter[/TD]
[TD="class: value"]HDA-Intel - HDA ATI HDMI[/TD]
[/TR]
[/TABLE]

All necessary sound codecs are present as well


Thanks again for your time

---

### Post by clementc on 2019-01-02
Hi [**gunner220**]("https://ubuntuforums.org/member.php?u=2073409"),

Are you trying to get audio through HDMI or via your desktop PC's jack output?

Edit: looks like you are trying to use your computer's speakers which I would assume are plugged in through the jack audio output connector.

Can you please try the following steps:

1. In Terminal, run: sudo nano /etc/modprobe.d/alsa-base.conf
2. At the end of the file, paste the following line: options snd-hda-intel model=dell-m6
3. Reboot and check if the sound is now working

---

