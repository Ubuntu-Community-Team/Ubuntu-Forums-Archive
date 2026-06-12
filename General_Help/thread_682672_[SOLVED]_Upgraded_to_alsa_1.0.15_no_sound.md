---
title: "[SOLVED] Upgraded to alsa 1.0.15 no sound"
date: 2008-01-30
forum: General Help
---

### Post by Nepherte on 2008-01-30
I upgraded the alsa drivers from 1.0.14 to 1.0.15 because with the older drivers my internal micro doesn't work. I've done this upgrade before and it worked flawless using this guide: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto). Today I had to reinstall ubuntu, redid the upgrade process to 1.0.15 and now I don't have any sound at all. The card doesn't get reconized on booting.

This is some output of dmesg related to sound:
[   13.156000] snd_hda_intel: disagrees about version of symbol snd_ctl_add
[   13.156000] snd_hda_intel: Unknown symbol snd_ctl_add
[   13.156000] snd_hda_intel: disagrees about version of symbol snd_pcm_new
[   13.156000] snd_hda_intel: Unknown symbol snd_pcm_new
[   13.156000] snd_hda_intel: disagrees about version of symbol snd_pcm_limit_hw_rates
[   13.156000] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates
[   13.156000] snd_hda_intel: disagrees about version of symbol snd_card_register
[   13.156000] snd_hda_intel: Unknown symbol snd_card_register
[   13.156000] snd_hda_intel: disagrees about version of symbol snd_card_free
[   13.156000] snd_hda_intel: Unknown symbol snd_card_free
[   13.156000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all
[   13.156000] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[   13.156000] snd_hda_intel: disagrees about version of symbol snd_card_proc_new
[   13.156000] snd_hda_intel: Unknown symbol snd_card_proc_new
[   13.156000] snd_hda_intel: disagrees about version of symbol snd_ctl_find_id
[   13.156000] snd_hda_intel: Unknown symbol snd_ctl_find_id
[   13.156000] snd_hda_intel: disagrees about version of symbol snd_ctl_new1
[   13.156000] snd_hda_intel: Unknown symbol snd_ctl_new1
[   13.156000] snd_hda_intel: disagrees about version of symbol snd_component_add
[   13.156000] snd_hda_intel: Unknown symbol snd_component_add
[   13.156000] snd_hda_intel: disagrees about version of symbol snd_card_new
[   13.156000] snd_hda_intel: Unknown symbol snd_card_new
[   13.156000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_malloc_pages
[   13.156000] snd_hda_intel: Unknown symbol snd_pcm_lib_malloc_pages
[   13.156000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_ioctl
[   13.156000] snd_hda_intel: Unknown symbol snd_pcm_lib_ioctl
[   13.156000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_free_pages
[   13.156000] snd_hda_intel: Unknown symbol snd_pcm_lib_free_pages
[   13.156000] snd_hda_intel: Unknown symbol snd_ctl_elem_read
[   13.156000] snd_hda_intel: Unknown symbol snd_ctl_elem_write
[   13.156000] snd_hda_intel: disagrees about version of symbol snd_pcm_set_ops
[   13.156000] snd_hda_intel: Unknown symbol snd_pcm_set_ops
[   13.156000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_list
[   13.156000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_list
[   13.156000] snd_hda_intel: disagrees about version of symbol snd_device_new
[   13.156000] snd_hda_intel: Unknown symbol snd_device_new
[   13.156000] snd_hda_intel: disagrees about version of symbol snd_pcm_suspend_all
[   13.156000] snd_hda_intel: Unknown symbol snd_pcm_suspend_all
[   13.156000] snd_hda_intel: disagrees about version of symbol snd_card_disconnect
[   13.156000] snd_hda_intel: Unknown symbol snd_card_disconnect
[   13.156000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_integer
[   13.156000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer
[   13.156000] snd_hda_intel: disagrees about version of symbol snd_pcm_period_elapsed
[   13.156000] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed
[   13.156000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_step
[   13.156000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_step
[   13.652000] lp: driver loaded but no devices found

In /proc/asound there's no card0 listed either. The device is listed in lspci though. Any thoughts on this to fix it?

---

### Post by Nepherte on 2008-01-30
After googling a little more, I managed to fix the problem by running the following commands:
```

cp -v /lib/modules/2.6.22-*/kernel/sound/pci/hda/snd-hda-intel.ko /lib/modules/2.6.22-*/ubuntu/media/snd-hda-intel/snd-hda-intel.ko
cp -v /usr/src/alsa/alsa-driver*/modules/* /lib/modules/2.6.22-*/kernel/sound/
depmod -a
```
and restarting afterwards. I guess this makes sense.

---

### Post by b4silence on 2008-02-02
Thanks man...

This was just what I was looking for!

---

### Post by chokas on 2008-02-03
GREAT, THANK YOU... :guitar:anyways I dont understand why I had to do this... last time I installed the audio it just worked compiling and installing,=S.

---

### Post by Nepherte on 2008-02-10
Perhaps worth mentioning. When you upgrade your kernel, either manually or using automatic updates, you have to redo the whole process of compiling your alsa drivers.

---

