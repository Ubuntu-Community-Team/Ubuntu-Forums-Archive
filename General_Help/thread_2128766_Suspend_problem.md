---
title: "Suspend problem"
date: 2013-03-24
forum: General Help
---

### Post by 0xc0de on 2013-03-24
Hello! I have problem with suspend on my ASUS X55VD.
It suspend only one time after reboot.
Here the pm-suspend.log
```
Initial commandline parameters: 
&#1042;&#1089;&#1082; &#1052;&#1072;&#1088; 24 13:40:26 EET 2013: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:

/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Starfire 3.5.0-26-generic #42-Ubuntu SMP Fri Mar 8 23:18:20 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
ath9k                 131317  0 
mac80211              540032  1 ath9k
ath9k_common           14056  1 ath9k
ath9k_hw              395357  2 ath9k,ath9k_common
ath                    23828  3 ath9k,ath9k_common,ath9k_hw
cfg80211              206797  3 ath9k,mac80211,ath
nfnetlink_log          17846  0 
nfnetlink              14328  1 nfnetlink_log
bbswitch               13469  0 
bnep                   18141  2 
rfcomm                 46620  16 
parport_pc             32689  0 
ppdev                  17074  0 
dm_crypt               23012  0 
nls_iso8859_1          12714  1 
reiserfs              246448  2 
snd_hda_codec_hdmi     32049  1 
snd_hda_codec_via      46676  1 
joydev                 17458  0 
snd_hda_intel          33492  3 
uvcvideo               76750  0 
snd_hda_codec         134213  3 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel
videobuf2_core         32852  1 uvcvideo
videodev              120310  2 uvcvideo,videobuf2_core
coretemp               13401  0 
kvm_intel             132760  0 
videobuf2_vmalloc      12861  1 uvcvideo
snd_hwdep              17699  1 snd_hda_codec
videobuf2_memops       13405  1 videobuf2_vmalloc
arc4                   12530  2 
kvm                   414071  1 kvm_intel
snd_pcm                96668  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13325  0 
psmouse                95595  0 
btusb                  22475  0 
snd_rawmidi            30513  1 snd_seq_midi
snd_seq_midi_event     14900  1 snd_seq_midi
bluetooth             209249  22 bnep,rfcomm,btusb
asus_nb_wmi            12711  0 
snd_seq                61555  2 snd_seq_midi,snd_seq_midi_event
alx                    68240  0 
asus_wmi               24089  1 asus_nb_wmi
sparse_keymap          13891  1 asus_wmi
snd_timer              29426  2 snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
microcode              22804  0 
snd                    78921  16 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mdio                   13808  1 alx
mxm_wmi                13022  0 
wmi                    19071  2 asus_wmi,mxm_wmi
soundcore              15048  1 snd
mei                    40691  0 
snd_page_alloc         18485  2 snd_hda_intel,snd_pcm
lpc_ich                17062  0 
serio_raw              13216  0 
mac_hid                13206  0 
lp                     17760  0 
parport                46346  3 parport_pc,ppdev,lp
ghash_clmulni_intel    13221  0 
cryptd                 20404  1 ghash_clmulni_intel
ahci                   25721  6 
libahci                31192  1 ahci
i915                  520615  3 
drm_kms_helper         49113  1 i915
drm                   288721  4 i915,drm_kms_helper
i2c_algo_bit           13414  1 i915
video                  19391  1 i915
             total       used       free     shared    buffers     cached
Mem:       8061604    3598044    4463560          0     159816    2087296
-/+ buffers/cache:    1350932    6710672
Swap:     15999996          0   15999996

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
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
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
&#1042;&#1089;&#1082; &#1052;&#1072;&#1088; 24 13:40:26 EET 2013: performing suspend
&#1042;&#1089;&#1082; &#1052;&#1072;&#1088; 24 13:40:29 EET 2013: Awake.
&#1042;&#1089;&#1082; &#1052;&#1072;&#1088; 24 13:40:29 EET 2013: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

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
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
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
&#1042;&#1089;&#1082; &#1052;&#1072;&#1088; 24 13:40:29 EET 2013: Finished.


```
Some from dmesg
```
[15347.741818] Suspending console(s) (use no_console_suspend to debug)
[15347.765929] alx 0000:04:00.0: shutdown fail in suspend -5
[15347.765940] pci_pm_suspend(): alx_suspend+0x0/0x90 [alx] returns -5
[15347.765944] dpm_run_callback(): pci_pm_suspend+0x0/0x140 returns -5
[15347.765946] PM: Device 0000:04:00.0 failed to suspend async: error -5
[15348.270000] PM: suspend of drv:sd dev:0:0:0:0 complete after 520.030 msecs
[15348.270153] PM: Some devices failed to suspend


```
I have this problem before, but i forgot how i solve it :) (It seems need to unload one module before suspend)

---

### Post by 0xc0de on 2013-03-24
Here the solution:
Create **/etc/pm/sleep.d/40_custom** with this content
```

#!/bin/sh

# Fix ASUS X55 "only one time suspend" issue.
# Problem in atheros network driver (eth0).

case $1 in
     suspend|suspend_hybrid|hibernate)
        modprobe -r alx
        ;;
     resume|thaw)
        modprobe alx
        ;;
esac

```
Make it executable by ```
chmod +x /etc/pm/sleep.d/40_custom
```
That's it! Suspend now works. :)
Change thread to SOLVED.

---

### Post by Toz on 2013-03-24
Thanks for posting back the solution. 
To mark the thread as SOLVED, edit your first post, click on the "Go Advanced" button, then select [SOLVED] from the Prefix dropdown.

---

