---
title: "Laptop display fails to wake if suspended by closing lid, OK if suspended other ways"
date: 2014-02-21
forum: General Help
---

### Post by gm80 on 2014-02-21
Running Lubuntu 13.10 on a Nokia Booklet 3G, an unfriendly and low-specced laptop with a GMA500 (among other things). This is my first venture back into Linux since 1999, and I've already fixed a number of small issues on my hardware thanks to the helpful posts on the forums. In fact, I have just one lingering issue related to suspend and the built-in display.

If I suspend the system in any of these ways, everything works as expected: sudo pm-suspend (no special arguments needed), Shutdown->Suspend from the LXDE GUI, or Suspend from the xfce4-power-manager GUI. The sleep indicator lights up as expected, and everything resumes correctly after closing and opening the lid again.

If I suspend the system by closing the lid, which is how I have configured xfce4-power-manager, everything seems to suspend correctly and the sleep indicator lights up. When I open the lid, however, no power is restored to the display. It's not "on and showing black," but rather powered off. The wi-fi and other indicators return as expected, so I assume the rest of the system resumes correctly. Pressing the power button triggers a shutdown and the display wakes and shows the Lubuntu splash screen briefly before the system shuts down.

I've read about others' issues fixed by adding quirks/arguments to make pm-suspend work correctly, but mine already does and that hasn't helped, regardless. Others suggested moving various hooks out of sleep.d but I haven't found the correct one, if so. I have the identical issue on Fedora 20, as well, so I'm thinking it's related to something in my hardware's power management.

Here is pm-suspend.log from a successful attempt (using the xfce4-power-manager GUI):

```
 

Initial commandline parameters: 
Fri Feb 21 10:15:42 CST 2014: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Nokia-Booklet-3G 3.11.0-17-generic #31-Ubuntu SMP Mon Feb 3 21:53:31 UTC 2014 i686 i686 i686 GNU/Linux
Module                  Size  Used by
zram                   18070  2 
vesafb                 13500  0 
coretemp               13195  0 
kvm                   368949  0 
parport_pc             31981  0 
ppdev                  17391  0 
i2c_isch               13241  0 
joydev                 17097  0 
snd_hda_codec_hdmi     40373  1 
snd_hda_codec_realtek    50261  1 
snd_hda_intel          42658  1 
rfcomm                 53664  12 
bnep                   18959  2 
snd_hda_codec         164003  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                89488  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25094  1 snd_seq_midi
uvcvideo               71309  0 
videobuf2_vmalloc      13048  1 uvcvideo
videobuf2_memops       13170  1 videobuf2_vmalloc
videobuf2_core         39125  1 uvcvideo
hso                    33287  0 
arc4                   12536  2 
microcode              18894  0 
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
videodev              107508  2 uvcvideo,videobuf2_core
ath9k                 136257  0 
ath9k_common           13619  1 ath9k
ath9k_hw              429197  2 ath9k_common,ath9k
psmouse                90642  0 
serio_raw              13189  0 
ath                    19187  3 ath9k_common,ath9k,ath9k_hw
lpc_sch                12784  0 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
mac80211              517444  1 ath9k
gma500_gfx            173701  2 
snd_timer              24447  2 snd_pcm,snd_seq
btusb                  23443  0 
bluetooth             323656  22 bnep,btusb,rfcomm
drm_kms_helper         46867  1 gma500_gfx
cfg80211              401762  3 ath,ath9k,mac80211
snd                    60790  13 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
drm                   242400  3 drm_kms_helper,gma500_gfx
mac_hid                13037  0 
i2c_algo_bit           13197  1 gma500_gfx
soundcore              12600  1 snd
video                  18777  1 gma500_gfx
lp                     13299  0 
parport                40795  3 lp,ppdev,parport_pc
pata_acpi              12886  0 
sdhci_pci              18481  0 
sdhci                  37644  1 sdhci_pci
pata_sch               12711  2 
             total       used       free     shared    buffers     cached
Mem:       1016788     286512     730276          0      19824     167524
-/+ buffers/cache:      99164     917624
Swap:      1517028          0    1517028
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.

Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
/etc/pm/sleep.d/10_grub-common suspend suspend: success.

Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Selected interface 'wlan0'
OK
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0
/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.

Fri Feb 21 10:15:43 CST 2014: performing suspend
Fri Feb 21 10:15:58 CST 2014: Awake.
Fri Feb 21 10:15:58 CST 2014: Running hooks for resume
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
/usr/lib/pm-utils/sleep.d/99video resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sda:
 setting Advanced Power Management level to 0x80 (128)
 APM_level    = 128

/dev/sda:
 setting standby to 36 (3 minutes)
/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Selected interface 'wlan0'
OK
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.

Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.

Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
/etc/pm/sleep.d/10_grub-common resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.

Fri Feb 21 10:15:59 CST 2014: Finished.


```

And here is pm-suspend.log from a falied attempt (simply shutting the lid):

```


Initial commandline parameters: 
Fri Feb 21 10:19:04 CST 2014: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Nokia-Booklet-3G 3.11.0-17-generic #31-Ubuntu SMP Mon Feb 3 21:53:31 UTC 2014 i686 i686 i686 GNU/Linux
Module                  Size  Used by
zram                   18070  2 
vesafb                 13500  0 
coretemp               13195  0 
kvm                   368949  0 
parport_pc             31981  0 
ppdev                  17391  0 
i2c_isch               13241  0 
joydev                 17097  0 
snd_hda_codec_hdmi     40373  1 
snd_hda_codec_realtek    50261  1 
snd_hda_intel          42658  1 
rfcomm                 53664  12 
bnep                   18959  2 
snd_hda_codec         164003  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                89488  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25094  1 snd_seq_midi
uvcvideo               71309  0 
videobuf2_vmalloc      13048  1 uvcvideo
videobuf2_memops       13170  1 videobuf2_vmalloc
videobuf2_core         39125  1 uvcvideo
hso                    33287  0 
arc4                   12536  2 
microcode              18894  0 
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
videodev              107508  2 uvcvideo,videobuf2_core
ath9k                 136257  0 
ath9k_common           13619  1 ath9k
ath9k_hw              429197  2 ath9k_common,ath9k
psmouse                90642  0 
serio_raw              13189  0 
ath                    19187  3 ath9k_common,ath9k,ath9k_hw
lpc_sch                12784  0 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
mac80211              517444  1 ath9k
gma500_gfx            173701  3 
snd_timer              24447  2 snd_pcm,snd_seq
btusb                  23443  0 
bluetooth             323656  22 bnep,btusb,rfcomm
drm_kms_helper         46867  1 gma500_gfx
cfg80211              401762  3 ath,ath9k,mac80211
snd                    60790  13 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
drm                   242400  4 drm_kms_helper,gma500_gfx
mac_hid                13037  0 
i2c_algo_bit           13197  1 gma500_gfx
soundcore              12600  1 snd
video                  18777  1 gma500_gfx
lp                     13299  0 
parport                40795  3 lp,ppdev,parport_pc
pata_acpi              12886  0 
sdhci_pci              18481  0 
sdhci                  37644  1 sdhci_pci
pata_sch               12711  2 
             total       used       free     shared    buffers     cached
Mem:       1016788     292052     724736          0      19984     169140
-/+ buffers/cache:     102928     913860
Swap:      1517028          0    1517028
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.

Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
/etc/pm/sleep.d/10_grub-common suspend suspend: success.

Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Selected interface 'wlan0'
OK
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0
/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.

Fri Feb 21 10:19:05 CST 2014: performing suspend
Fri Feb 21 10:19:21 CST 2014: Awake.
Fri Feb 21 10:19:21 CST 2014: Running hooks for resume
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
/usr/lib/pm-utils/sleep.d/99video resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sda:
 setting Advanced Power Management level to 0x80 (128)
 APM_level    = 128

/dev/sda:
 setting standby to 36 (3 minutes)
/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Selected interface 'wlan0'
OK
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.

Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.

Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
/etc/pm/sleep.d/10_grub-common resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.

Fri Feb 21 10:19:22 CST 2014: Finished.


```

Thanks in advance for any suggestions you might have. Looking forward to resolving this one remaining issue.

---

### Post by gm80 on 2014-03-11
Anyone? This is literally the only remaining issue I have with 13.10 on this difficult little laptop. It's frustrating that suspend works in nearly every way but the one I'm most likely to use.

Thanks.

---

### Post by evan8 on 2014-03-12
Yeah I get similiar issues. HIbernate works for me or shut down. Otherwise I have to drain my battery or take it out. Strange indeed

---

### Post by bapoumba on 2014-03-12
Have you tried the <spacebar> to wake it up ?
Works here (although network is down for good and I have not found yet a workaround).

---

### Post by mikewhatever on 2014-03-14
It's been suggested to move /usr/lib/pm-utils/sleep.d/99video out, not really sure what you mean by not finding it. That's the only way a Dell mini 10 with GMA500 here gets its screen back after suspending.

---

