---
title: "Problem about sound driver"
date: 2012-10-25
forum: General Help
---

### Post by khoaprogramer on 2012-10-25
Hello

Sound Card on Board is not working, so I use Creative Sound Card, but i am not looking for driver for Ubuntu. I need help.

Thanks!

---

### Post by newb85 on 2012-10-25
If you open Sound Settings, is your sound card not listed?

Please give us more info on your card by posting the output of
```
sudo lshw -C multimedia
```

---

### Post by khoaprogramer on 2012-10-25
I think, there are 2 sound cards  and id of sound card on board is 1, how to set up id 1 for creative sound card. ?

Thanks
```
*-multimedia            
       description: Audio device
       product: N10/ICH 7 Family High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=snd_hda_intel latency=0
       resources: irq:40 memory:fea38000-fea3bfff
  *-multimedia
       description: Multimedia audio controller
       product: CA0106 Soundblaster
       vendor: Creative Labs
       physical id: 2
       bus info: pci@0000:01:02.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=snd_ca0106 latency=64 maxlatency=20 mingnt=2
       resources: irq:19 ioport:ec00(size=32)

```

---

### Post by newb85 on 2012-10-26
Please open Sound Settings by clicking the Sound menu in the system tray and clicking Sound Settings...

On the left side, it should say "Play sound through".  What options are listed below?

---

### Post by newb85 on 2012-10-26
*Disclaimer: I don't have experience with this method, and I'm adapting it from the way someone else disabled their network card.*

You should be able to disable that sound card by blacklisting it's drivers.

```
echo '' | sudo tee -a /etc/modprobe.d/blacklist.conf
echo '# On-board sound driver' | sudo tee -a /etc/modprobe.d/blacklist.conf
echo 'blacklist snd_hda_intel' | sudo tee -a /etc/modprobe.d/blacklist.conf
```

Edit: I think you'll have to reboot for these changes to take effect.

---

### Post by khoaprogramer on 2012-10-26
I followed to your instruction, and driver onboard don't exist "Play with through" in Sound setting. Although song in my music libary play but i dont listen sound, you have ways to fix. I dont know creative sound card is set up. How to know driver is set up.
Infor in terminal
```
 *-multimedia UNCLAIMED  
       description: Audio device
       product: N10/ICH 7 Family High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:fea38000-fea3bfff
  *-multimedia
       description: Multimedia audio controller
       product: CA0106 Soundblaster
       vendor: Creative Labs
       physical id: 2
       bus info: pci@0000:01:02.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=snd_ca0106 latency=64 maxlatency=20 mingnt=2
       resources: irq:19 ioport:ec00(size=32)

```
Thanks

---

### Post by newb85 on 2012-10-26
> **khoaprogramer said:**
> I followed to your instruction, and driver onboard don't exist "Play with through" in Sound setting. Although song in my music libary play but i dont listen sound, you have ways to fix. I dont know creative sound card is set up. How to know driver is set up.
Infor in terminal
```
 ***-multimedia UNCLAIMED**  
       description: Audio device
       product: N10/ICH 7 Family High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:fea38000-fea3bfff
  *-multimedia
       description: Multimedia audio controller
       product: **CA0106 Soundblaster**
       vendor: Creative Labs
       physical id: 2
       bus info: pci@0000:01:02.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: {b]driver=snd_ca0106[/b] latency=64 maxlatency=20 mingnt=2
       resources: irq:19 ioport:ec00(size=32)

```
Thanks

Looks to me like your second card is set up and using drivers designed specifically for it.  Meanwhile, your on-board card now has no drivers, so it shouldn't be functioning.

Run
```
alsamixer
```
and make sure the Master, Headphon, and Speaker are not muted.  (If they're muted, they will have "MM" below them.)

---

### Post by khoaprogramer on 2012-10-26
All is not "MM". What will i do ? please help you. Can creative sound driver turn on ? , how to turn on it ? 

Thanks.

---

### Post by newb85 on 2012-10-26
So far, it looks like the sound driver is already enabled.

Please post the output of

```
lsmod
```

---

### Post by khoaprogramer on 2012-10-26
Here 
```
Module                  Size  Used by
snd_ca0106             44727  2 
snd_ac97_codec        134826  1 snd_ca0106
ac97_bus               12730  1 snd_ac97_codec
snd_pcm                97188  2 snd_ca0106,snd_ac97_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  2 snd_ca0106,snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
rfcomm                 47604  0 
bnep                   18281  2 
parport_pc             32866  0 
bluetooth             180104  10 rfcomm,bnep
ppdev                  17113  0 
binfmt_misc            17540  1 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
serio_raw              13211  0 
snd                    78855  11 snd_ca0106,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  473298  3 
drm_kms_helper         46978  1 i915
soundcore              15091  1 snd
drm                   241921  4 i915,drm_kms_helper
snd_page_alloc         18529  2 snd_ca0106,snd_pcm
mac_hid                13253  0 
i2c_algo_bit           13423  1 i915
video                  19596  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47199  0 
hid                    99559  1 usbhid
8139too                32177  0 
8139cp                 27409  0 
```

---

### Post by newb85 on 2012-10-26
The first module listed is your sound driver.  It's running.

Try these steps [here]("http://ubuntuforums.org/showpost.php?p=11925986&postcount=9").

---

### Post by khoaprogramer on 2012-10-26
Thank you very much

I follow to you instruction, and my PC have had sound. I am very happy

Good luck.

---

### Post by newb85 on 2012-10-26
Glad to hear it.  Please mark this thread as Solved by clicking "Thread Tools" at the top of the thread.

---

