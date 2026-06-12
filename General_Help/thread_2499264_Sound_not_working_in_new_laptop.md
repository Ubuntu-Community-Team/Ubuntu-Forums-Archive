---
title: "Sound not working in new laptop"
date: 2024-07-20
forum: General Help
---

### Post by bedafa on 2024-07-20
Hi, 
I bought recently a new laptop (Lenovo Ideapad Slim 3, with a n305) and Ubuntu 24.04LTS seems to work ok except for the sound. Tested also kernel 6.9.
Those are the details of the sound card:

```

me@lnv:~$ lspci -nnk | grep -i audio -A2


00:1f.3 Audio device [0403]: Intel Corporation Alder Lake-N PCH High Definition Audio Controller [8086:54c8]
    Subsystem: Lenovo Device [17aa:3801]
    Kernel driver in use: sof-audio-pci-intel-tgl
    Kernel modules: snd_hda_intel, snd_soc_avs, snd_sof_pci_intel_tgl
00:1f.4 SMBus [0c05]: Intel Corporation Device [8086:54a3]

```

and the dmesg

```

me@lnv:~$ sudo dmesg | grep snd


[   11.672051] snd_hda_intel 0000:00:1f.3: DSP detected with PCI class/subclass/prog-if info 0x040380
[   11.672083] snd_hda_intel 0000:00:1f.3: SoundWire enabled on CannonLake+ platform, using SOF driver
[   11.709800] snd_soc_avs 0000:00:1f.3: DSP detected with PCI class/subclass/prog-if info 0x040380
[   11.709827] snd_soc_avs 0000:00:1f.3: SoundWire enabled on CannonLake+ platform, using SOF driver
[   12.818319] snd_hda_intel 0000:00:1f.3: DSP detected with PCI class/subclass/prog-if info 0x040380
[   12.818358] snd_hda_intel 0000:00:1f.3: SoundWire enabled on CannonLake+ platform, using SOF driver
[   12.818374] snd_soc_avs 0000:00:1f.3: DSP detected with PCI class/subclass/prog-if info 0x040380
[   12.818389] snd_soc_avs 0000:00:1f.3: SoundWire enabled on CannonLake+ platform, using SOF driver
[   13.111817] sof-audio-pci-intel-tgl 0000:00:1f.3: ASoC: error at snd_soc_component_probe on 0000:00:1f.3: -22
[   13.111899] sof_sdw sof_sdw: error -EINVAL: snd_soc_register_card failed -22



```

any suggestion?

---

### Post by bedafa on 2024-07-20
For reference, sound seems to work when applying the solution at [https://bbs.archlinux.org/viewtopic.php?id=294840](https://bbs.archlinux.org/viewtopic.php?id=294840)
but I think it is mono (better than nothing). However it does strange beeps every 5min-10min, a bit annoying.

---

### Post by Bashing-om on 2024-07-20
bedafa - Hello

In Ubuntu 24.04 it is pipewire that is the sound service frontend.
It will be instructive to see what the kernel thinks:
post back:
```

dpkg -l pipewire
pactl info
systemctl --user status pipewire
systemctl --user status wireplumber

```

-see here what condition the condition is in-

---

