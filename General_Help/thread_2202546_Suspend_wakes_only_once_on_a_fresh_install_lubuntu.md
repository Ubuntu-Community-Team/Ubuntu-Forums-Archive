---
title: "Suspend wakes only once on a fresh install lubuntu 13.10"
date: 2014-01-29
forum: General Help
---

### Post by shaggyz9 on 2014-01-29
On a fresh install of lubuntu 13.10 I was able to use suspend and wake once but then I'm not able to suspend, reboot or shutdown from the menu until reboot. At the bottom of the shutdown menu it gives an error
```
gdbus.error:org.freedesktop.dbus.errorfailed: operation already in progress
```
I just reboot using the terminal. 

After a reboot if I suspend from the menu I get a black screen on wake. Monitor is on but just blank black screen. I've tried using sudo pm-suspend but it freezes on wake. The screen comes up but its frozen where I left off. 

Heres is the pm-suspend log
```
Initial commandline parameters: 
Wed Jan 29 12:19:52 PST 2014: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux xbmc-box 3.11.0-15-generic #23-Ubuntu SMP Mon Dec 9 18:16:27 UTC 2013 i686 i686 i686 GNU/Linux
Module                  Size  Used by
zram                   18070  2 
parport_pc             31981  0 
ppdev                  17391  0 
bnep                   18959  2 
rfcomm                 53664  0 
bluetooth             323656  10 bnep,rfcomm
x86_pkg_temp_thermal    13810  0 
intel_powerclamp       14239  0 
coretemp               13195  0 
kvm_intel             128218  0 
kvm                   368949  1 kvm_intel
crc32_pclmul           12967  0 
gpio_ich               13229  0 
ir_lirc_codec          12869  0 
snd_hda_codec_hdmi     40373  1 
ir_sony_decoder        12625  0 
ir_rc6_decoder         12754  0 
ir_mce_kbd_decoder     13030  0 
ir_nec_decoder         12787  0 
lirc_dev               19324  1 ir_lirc_codec
ir_rc5_decoder         12622  0 
ir_sanyo_decoder       12727  0 
ir_jvc_decoder         12655  0 
snd_hda_codec_realtek    45592  1 
rc_rc6_mce             12454  0 
snd_hda_intel          42658  1 
snd_hda_codec         164003  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
mceusb                 17580  0 
snd_hwdep              13272  1 snd_hda_codec
rc_core                26398  11 ir_lirc_codec,ir_rc5_decoder,ir_nec_decoder,ir_sony_decoder,mceusb,ir_mce_kbd_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_sanyo_decoder,rc_rc6_mce
snd_pcm                89488  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
joydev                 17097  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25094  1 snd_seq_midi
i915                  594380  5 
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              24447  2 snd_pcm,snd_seq
video                  18777  1 i915
snd                    60790  13 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
drm_kms_helper         46867  1 i915
drm                   242400  6 i915,drm_kms_helper
soundcore              12600  1 snd
i2c_algo_bit           13197  1 i915
microcode              18830  0 
psmouse                90642  0 
serio_raw              13189  0 
mei_me                 13933  0 
lpc_ich                16864  0 
mei                    66411  1 mei_me
mac_hid                13037  0 
lp                     13299  0 
parport                40795  3 lp,ppdev,parport_pc
hid_generic            12492  0 
usbhid                 47361  0 
hid                    87370  2 hid_generic,usbhid
r8169                  61562  0 
mii                    13654  1 r8169
             total       used       free     shared    buffers     cached
Mem:       4041408     515612    3525796          0     102856     303404
-/+ buffers/cache:     109352    3932056
Swap:      6308180          0    6308180
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
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
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

Wed Jan 29 12:19:53 PST 2014: performing suspend
Wed Jan 29 12:20:08 PST 2014: Awake.
Wed Jan 29 12:20:08 PST 2014: Running hooks for resume
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
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sdb:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sdb:
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
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
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

Wed Jan 29 12:20:08 PST 2014: Finished.
Initial commandline parameters: 
Wed Jan 29 12:47:51 PST 2014: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux xbmc-box 3.11.0-15-generic #23-Ubuntu SMP Mon Dec 9 18:16:27 UTC 2013 i686 i686 i686 GNU/Linux
Module                  Size  Used by
zram                   18070  2 
parport_pc             31981  0 
ppdev                  17391  0 
rfcomm                 53664  0 
bnep                   18959  2 
bluetooth             323656  10 bnep,rfcomm
x86_pkg_temp_thermal    13810  0 
intel_powerclamp       14239  0 
coretemp               13195  0 
kvm_intel             128218  0 
kvm                   368949  1 kvm_intel
crc32_pclmul           12967  0 
gpio_ich               13229  0 
ir_lirc_codec          12869  0 
lirc_dev               19324  1 ir_lirc_codec
ir_mce_kbd_decoder     13030  0 
ir_sony_decoder        12625  0 
ir_sanyo_decoder       12727  0 
ir_jvc_decoder         12655  0 
ir_rc6_decoder         12754  0 
ir_rc5_decoder         12622  0 
ir_nec_decoder         12787  0 
joydev                 17097  0 
rc_rc6_mce             12454  0 
mceusb                 17580  0 
rc_core                26398  11 ir_lirc_codec,ir_rc5_decoder,ir_nec_decoder,ir_sony_decoder,mceusb,ir_mce_kbd_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_sanyo_decoder,rc_rc6_mce
snd_hda_codec_hdmi     40373  1 
snd_hda_codec_realtek    45592  1 
snd_hda_intel          42658  1 
snd_hda_codec         164003  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                89488  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25094  1 snd_seq_midi
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
microcode              18830  0 
psmouse                90642  0 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              24447  2 snd_pcm,snd_seq
i915                  594380  5 
snd                    60790  13 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
serio_raw              13189  0 
video                  18777  1 i915
drm_kms_helper         46867  1 i915
drm                   242400  6 i915,drm_kms_helper
i2c_algo_bit           13197  1 i915
mei_me                 13933  0 
mei                    66411  1 mei_me
soundcore              12600  1 snd
lpc_ich                16864  0 
mac_hid                13037  0 
lp                     13299  0 
parport                40795  3 lp,ppdev,parport_pc
hid_generic            12492  0 
usbhid                 47361  0 
hid                    87370  2 hid_generic,usbhid
r8169                  61562  0 
mii                    13654  1 r8169
             total       used       free     shared    buffers     cached
Mem:       4041408     346172    3695236          0      30668     208052
-/+ buffers/cache:     107452    3933956
Swap:      6308180          0    6308180
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
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
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

Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0
/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.

Wed Jan 29 12:47:52 PST 2014: performing suspend
Initial commandline parameters: 
Wed Jan 29 12:54:06 PST 2014: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux xbmc-box 3.11.0-15-generic #23-Ubuntu SMP Mon Dec 9 18:16:27 UTC 2013 i686 i686 i686 GNU/Linux
Module                  Size  Used by
zram                   18070  2 
parport_pc             31981  0 
ppdev                  17391  0 
rfcomm                 53664  0 
bnep                   18959  2 
bluetooth             323656  10 bnep,rfcomm
x86_pkg_temp_thermal    13810  0 
intel_powerclamp       14239  0 
coretemp               13195  0 
kvm_intel             128218  0 
kvm                   368949  1 kvm_intel
crc32_pclmul           12967  0 
gpio_ich               13229  0 
ir_lirc_codec          12869  0 
lirc_dev               19324  1 ir_lirc_codec
ir_mce_kbd_decoder     13030  0 
ir_sanyo_decoder       12727  0 
ir_sony_decoder        12625  0 
ir_jvc_decoder         12655  0 
ir_rc6_decoder         12754  0 
ir_nec_decoder         12787  0 
ir_rc5_decoder         12622  0 
joydev                 17097  0 
rc_rc6_mce             12454  0 
mceusb                 17580  0 
rc_core                26398  11 ir_lirc_codec,ir_rc5_decoder,ir_nec_decoder,ir_sony_decoder,mceusb,ir_mce_kbd_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_sanyo_decoder,rc_rc6_mce
snd_hda_codec_hdmi     40373  1 
snd_hda_codec_realtek    45592  1 
microcode              18830  0 
snd_hda_intel          42658  1 
psmouse                90642  0 
snd_hda_codec         164003  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
mei_me                 13933  0 
snd_pcm                89488  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
serio_raw              13189  0 
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25094  1 snd_seq_midi
mei                    66411  1 mei_me
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              24447  2 snd_pcm,snd_seq
lpc_ich                16864  0 
snd                    60790  13 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
i915                  594380  2 
soundcore              12600  1 snd
video                  18777  1 i915
drm_kms_helper         46867  1 i915
drm                   242400  3 i915,drm_kms_helper
mac_hid                13037  0 
i2c_algo_bit           13197  1 i915
lp                     13299  0 
parport                40795  3 lp,ppdev,parport_pc
hid_generic            12492  0 
usbhid                 47361  0 
hid                    87370  2 hid_generic,usbhid
r8169                  61562  0 
mii                    13654  1 r8169
             total       used       free     shared    buffers     cached
Mem:       4041408     512688    3528720          0      38752     290644
-/+ buffers/cache:     183292    3858116
Swap:      6308180          0    6308180
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
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
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

Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0
/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.

Wed Jan 29 12:54:07 PST 2014: performing suspend
```

This might be helpful. Intel celeron g550 no video card. HD graphics. Default drivers.
```
xbmc@xbmc-box:~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation H61 Express Chipset Family LPC Controller (rev 05)
00:1f.2 IDE interface: Intel Corporation 6 Series/C200 Series Chipset Family 4 port SATA IDE Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
00:1f.5 IDE interface: Intel Corporation 6 Series/C200 Series Chipset Family 2 port SATA IDE Controller (rev 05)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)

```


I've done four fresh install with the same results. Any help getting suspend to work properly is appreciated.

---

### Post by shaggyz9 on 2014-01-31
Anyone have any ideas? Any information I can provide to help? A Direction I can go to figure this out?

---

### Post by professor_universe on 2014-02-12
I'm experiencing similar suspend/resume errors with 13.10, and we're not the only ones. I'm still working on a solution, but no luck so far.

---

### Post by shaggyz9 on 2014-02-12
I've gone back to 12.10 for now because I couldn't find a solution for 13.04 or 13.10. In 12.10 suspend works perfectly as long as I add "i915.i915_enable_rc6=0" to the grub command line but that doesn't help in 13.10.  The intel HD graphics are better in 13.10 with the newer kernels so I would like to use that but I also need suspend. I've tried using the pm-suspend quirks and none of them worked as well as a bunch of different grub commands but nothing worked. I hope someone can find a solution to this problem for future releases.

---

### Post by syntaxerror74 on 2014-05-14
I can confirm this annoying behavior on latest Trusty (14.04).

So nothing has been done on this issue so far. First suspend works perfectly, but with every subsequent one, everything will freeze and I am forced to power cycle the machine.
It's a very important feature because it can reduce your electricity bill a LOT if you don't let the thing run in full glory for hours when you're not at home.

However, with the extremely buggy behavior it shows in suspend mode, I am forced to use the hibernation mode instead, which means the machine will go through the ENTIRE POST sequence, (re-)scanning your HDDs etc., so except for not having to relogin, time needed to boot up only differs by maybe 15 seconds in total.

---

