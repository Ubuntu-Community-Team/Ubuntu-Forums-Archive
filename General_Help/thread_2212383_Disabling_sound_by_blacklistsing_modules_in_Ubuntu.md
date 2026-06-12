---
title: "Disabling sound by blacklistsing modules in Ubuntu 13.10 on Macbook Pro 4,1"
date: 2014-03-20
forum: General Help
---

### Post by Chris Calderon on 2014-03-20
I have broken speakers, and they constantly let out static. I have done similar things before when I had ubuntu on a powermac, but I don't remember how to proceed. That and there are quite a few modules listed in lsmod that have snd infront.

this is the output of lsmod
Module                  Size  Used by
parport_pc             32701  0 
ppdev                  17671  0 
bnep                   19564  2 
rfcomm                 69070  12 
nvidia               9451814  41 
coretemp               13435  0 
kvm_intel             138538  0 
kvm                   431315  1 kvm_intel
joydev                 17377  0 
hid_apple              13244  0 
hid_appleir            13010  0 
applesmc               19308  0 
input_polldev          13896  1 applesmc
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40469  1 uvcvideo
videodev              133390  2 uvcvideo,videobuf2_core
bcm5974                17589  0 
usbhid                 53014  0 
hid                   101512  3 usbhid,hid_appleir,hid_apple
microcode              23518  0 
lpc_ich                21080  0 
snd_hda_codec_realtek    51465  1 
snd_hda_intel          48171  3 
snd_hda_codec         188738  2 snd_hda_codec_realtek,snd_hda_intel
btusb                  28267  0 
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102033  2 snd_hda_codec,snd_hda_intel
bluetooth             371874  22 bnep,btusb,rfcomm
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30095  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29433  2 snd_pcm,snd_seq
snd                    69141  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
soundcore              12680  1 snd
drm                   296739  2 nvidia
video                  19318  0 
apple_bl               13993  0 
mac_hid                13205  0 
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
firewire_ohci          40060  0 
firewire_core          64476  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
sky2                   58057  0 
ahci                   25819  0 
libahci                31898  1 ahci

Again, I am trying to turn sound off altogether, or only let it work through the audio jack and not the internal speakers. MY priority is just to get the annoying static to stop :p

---

### Post by Dreamer Fithp Apprentice on 2014-03-21
Look in synaptic for some audio control programs. I'm pretty sure you can do this with pavucontrol. Just set it to not use the speakers but the jack instead.  Or mute everything if you prefer. If this proves to be more trouble than it seems worth, just snip the wires to the speakers.

---

