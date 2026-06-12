---
title: "Sound Stuttering When WiFi Enabled"
date: 2013-08-14
forum: General Help
---

### Post by mike16 on 2013-08-14
Hi,

I recently fixed my lack of WiFi buy installing new drivers from Realtek  (see thread here: [http://ubuntuforums.org/showthread.php?t=2166788&page=2](http://ubuntuforums.org/showthread.php?t=2166788&page=2))

Now I have another, possibly unrelated, problem.

The wireless is now working great, but whenever it's enabled, the sound  behaves badly - stuttering like a dirty CD.  From any source or  application its the same.

I've searched the threads and found nothing obvious except one user who had the same problem (unsolved).

Please help.

UBUNTU 12.04 AMD64 on a Toshiba Satellite Proo C850


gerald@GeraldLaptopLinux:~$ lsmod | grep snd
snd_hda_codec_hdmi     32476  1 
snd_hda_codec_realtek    79855  1 
snd_hda_intel          34063  5 
snd_hda_codec         135141  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              17765  1 snd_hda_codec
snd_pcm                97523  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13325  0 
snd_rawmidi            30750  1 snd_seq_midi
snd_seq_midi_event     14900  1 snd_seq_midi
snd_seq                61931  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    83674  19 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15092  1 snd
snd_page_alloc         18573  2 snd_hda_intel,snd_pcm
gerald@GeraldLaptopLinux:~$ dmesg | grep snd
[   15.018424] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
gerald@GeraldLaptopLinux:~$ ^C
gerald@GeraldLaptopLinux:~$ 


I'm trying to convince a friend that they're better off with Linux and replaced their Windows with it but I'm struggling here and in danger of looking silly.

Mike.

---

