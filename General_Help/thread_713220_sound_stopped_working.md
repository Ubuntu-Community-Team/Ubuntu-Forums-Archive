---
title: "sound stopped working"
date: 2008-03-02
forum: General Help
---

### Post by amacheurworks on 2008-03-02
Yesterday my computer's sound stopped working. Thinking that maybe my sound card was broking I booted to my windows partition, but here sound worked fine. Even the sound that is played during the login screen doesn't work. 

I don't remember installing any updates, it just seemed to happen out of nowhere.

typing lspci -v into the terminal returns this for my sound card:
>  Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
        Subsystem: Dell Unknown device 01d1
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at febfc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

aplay -l returns this:
> **** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 2: Headset [Plantronics Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I have rebooted (needed to to load windows).

Any ideas at all?

Cheers!

---

### Post by amacheurworks on 2008-03-02
Having followed the instructions at this site:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

I now get the error message: 
> No volume control GStreamer plugins and/or devices found.
when clicking on the sound button on my desktop. 

and dmesg now returns this in relation to snd_hda_intel:
> [   31.542507] snd_hda_intel: disagrees about version of symbol snd_ctl_add
[   31.542512] snd_hda_intel: Unknown symbol snd_ctl_add
[   31.542563] snd_hda_intel: disagrees about version of symbol snd_pcm_new
[   31.542566] snd_hda_intel: Unknown symbol snd_pcm_new
[   31.542617] snd_hda_intel: disagrees about version of symbol snd_pcm_limit_hw_rates
[   31.542619] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates
[   31.542662] snd_hda_intel: disagrees about version of symbol snd_card_register
[   31.542665] snd_hda_intel: Unknown symbol snd_card_register
[   31.542703] snd_hda_intel: disagrees about version of symbol snd_card_free
[   31.542705] snd_hda_intel: Unknown symbol snd_card_free
[   31.542744] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all
[   31.542746] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[   31.542784] snd_hda_intel: disagrees about version of symbol snd_card_proc_new
[   31.542787] snd_hda_intel: Unknown symbol snd_card_proc_new
[   31.542943] snd_hda_intel: disagrees about version of symbol snd_ctl_find_id
[   31.542946] snd_hda_intel: Unknown symbol snd_ctl_find_id
[   31.543040] snd_hda_intel: disagrees about version of symbol snd_ctl_new1
[   31.543042] snd_hda_intel: Unknown symbol snd_ctl_new1
[   31.543127] snd_hda_intel: disagrees about version of symbol snd_component_add
[   31.543130] snd_hda_intel: Unknown symbol snd_component_add
[   31.543176] snd_hda_intel: disagrees about version of symbol snd_card_new
[   31.543178] snd_hda_intel: Unknown symbol snd_card_new
[   31.543257] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_malloc_pages
[   31.543259] snd_hda_intel: Unknown symbol snd_pcm_lib_malloc_pages
[   31.543311] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_ioctl
[   31.543313] snd_hda_intel: Unknown symbol snd_pcm_lib_ioctl
[   31.543355] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_free_pages
[   31.543357] snd_hda_intel: Unknown symbol snd_pcm_lib_free_pages
[   31.543410] snd_hda_intel: Unknown symbol snd_ctl_elem_read
[   31.543475] snd_hda_intel: Unknown symbol snd_ctl_elem_write
[   31.543511] snd_hda_intel: disagrees about version of symbol snd_pcm_set_ops
[   31.543514] snd_hda_intel: Unknown symbol snd_pcm_set_ops
[   31.543562] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_list
[   31.543565] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_list
[   31.543616] snd_hda_intel: disagrees about version of symbol snd_device_new
[   31.543619] snd_hda_intel: Unknown symbol snd_device_new
[   31.543676] snd_hda_intel: disagrees about version of symbol snd_pcm_suspend_all
[   31.543679] snd_hda_intel: Unknown symbol snd_pcm_suspend_all
[   31.543721] snd_hda_intel: disagrees about version of symbol snd_card_disconnect
[   31.543723] snd_hda_intel: Unknown symbol snd_card_disconnect
[   31.543758] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_integer
[   31.543761] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer
[   31.543951] snd_hda_intel: disagrees about version of symbol snd_pcm_period_elapsed
[   31.543954] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed
[   31.543987] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_step
[   31.543990] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_step


I don't really want to re-install ubuntu, so I'm hoping there's a way around this.

---

