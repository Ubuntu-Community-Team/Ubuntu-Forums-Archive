---
title: "Script does not run after returning from sleep state"
date: 2021-02-24
forum: General Help
---

### Post by raleigh3 on 2021-02-24
I have this in /usr/lib/pm-utils/sleep.d/ but it does not execute when returning from the sleep state.

```
#!/bin/sh

PATH=/usr/bin/:/usr/share/sounds/

case "$1" in
    resume|thaw)
       amixer -D pulse sset Master 60%
        cvlc --play-and-exit /usr/share/sounds/My_Sounds/Short_doorbell.wav
    ;;
    suspend|hibernate)
       
    ;;
esac

exit 0

```
I use the sleep key on my keyboard. (Half moon)

What am I doing wrong?

---

### Post by #&amp;thj^% on 2021-02-24
Show this as well please:
```
/var/log/pm-suspend.log
```
EDIT: Please do not forget to make the script executable.

---

### Post by raleigh3 on 2021-02-24
pm-suspend.log is a zero byte file.

I saw there is also pm-suspend.log.1 which is not empty.

---

### Post by #&amp;thj^% on 2021-02-24
Can we see it then? "pm-suspend.log.1 "

---

### Post by raleigh3 on 2021-02-24
```
Initial commandline parameters: 
Mon Aug 17 09:10:35 CDT 2020: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux 7 5.4.0-42-generic #46~18.04.1-Ubuntu SMP Fri Jul 10 07:21:24 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
edac_mce_amd           32768  0
kvm_amd                98304  0
ccp                    86016  1 kvm_amd
snd_hda_codec_realtek   122880  1
snd_hda_codec_generic    81920  1 snd_hda_codec_realtek
ath9k                 151552  0
kvm                   655360  1 kvm_amd
ledtrig_audio          16384  2 snd_hda_codec_generic,snd_hda_codec_realtek
ath9k_common           36864  1 ath9k
uvcvideo               94208  0
snd_hda_codec_hdmi     61440  1
crct10dif_pclmul       16384  1
crc32_pclmul           16384  0
snd_hda_intel          49152  5
ghash_clmulni_intel    16384  0
aesni_intel           372736  0
ath9k_hw              475136  2 ath9k_common,ath9k
snd_usb_audio         262144  1
crypto_simd            16384  1 aesni_intel
cryptd                 24576  2 crypto_simd,ghash_clmulni_intel
ath                    36864  3 ath9k_common,ath9k,ath9k_hw
input_leds             16384  0
snd_usbmidi_lib        36864  1 snd_usb_audio
serio_raw              20480  0
glue_helper            16384  1 aesni_intel
snd_intel_dspcfg       24576  1 snd_hda_intel
snd_seq_midi           20480  0
snd_seq_midi_event     16384  1 snd_seq_midi
videobuf2_vmalloc      20480  1 uvcvideo
videobuf2_memops       20480  1 videobuf2_vmalloc
videobuf2_v4l2         24576  1 uvcvideo
videobuf2_common       53248  2 videobuf2_v4l2,uvcvideo
snd_hda_codec         131072  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek
snd_hda_core           90112  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek
videodev              217088  3 videobuf2_v4l2,uvcvideo,videobuf2_common
mac80211              851968  1 ath9k
snd_seq                69632  2 snd_seq_midi,snd_seq_midi_event
snd_rawmidi            36864  2 snd_seq_midi,snd_usbmidi_lib
snd_hwdep              20480  2 snd_usb_audio,snd_hda_codec
mc                     53248  5 videodev,snd_usb_audio,videobuf2_v4l2,uvcvideo,videobuf2_common
snd_pcm               102400  5 snd_hda_codec_hdmi,snd_hda_intel,snd_usb_audio,snd_hda_codec,snd_hda_core
k10temp                16384  0
fam15h_power           16384  0
usblp                  24576  0
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
snd_timer              36864  2 snd_seq,snd_pcm
cfg80211              712704  4 ath9k_common,ath9k,ath,mac80211
snd                    86016  25 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_usb_audio,snd_usbmidi_lib,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_pcm,snd_rawmidi
libarc4                16384  1 mac80211
soundcore              16384  1 snd
mac_hid                16384  0
sch_fq_codel           20480  2
it87                   61440  0
hwmon_vid              16384  1 it87
parport_pc             40960  0
ppdev                  24576  0
lp                     20480  0
parport                53248  3 parport_pc,lp,ppdev
ip_tables              32768  0
x_tables               40960  1 ip_tables
autofs4                45056  2
amdgpu               4530176  0
amd_iommu_v2           20480  1 amdgpu
gpu_sched              32768  1 amdgpu
pata_acpi              16384  0
hid_logitech_hidpp     40960  0
hid_logitech_dj        28672  0
hid_generic            16384  0
usbhid                 53248  2 hid_logitech_dj
hid                   126976  4 usbhid,hid_generic,hid_logitech_dj,hid_logitech_hidpp
radeon               1454080  4
i2c_algo_bit           16384  2 amdgpu,radeon
ttm                   102400  2 amdgpu,radeon
drm_kms_helper        184320  2 amdgpu,radeon
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
i2c_piix4              28672  0
fb_sys_fops            16384  1 drm_kms_helper
ahci                   40960  3
r8169                  90112  0
pata_atiixp            16384  0
drm                   491520  8 gpu_sched,drm_kms_helper,amdgpu,radeon,ttm
libahci                32768  1 ahci
realtek                24576  1
video                  49152  0
              total        used        free      shared  buff/cache   available
Mem:        7064220      527188     5047060       16332     1489972     6222068
Swap:       2097148           0     2097148
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.

Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
/etc/pm/sleep.d/10_grub-common suspend suspend: success.

Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/40inputattach suspend suspend:
/usr/lib/pm-utils/sleep.d/40inputattach suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Selected interface 'wlp2s0'
OK
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
Warning: Stopping anacron.service, but it can still be activated by:
  anacron.timer
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

Mon Aug 17 09:10:36 CDT 2020: performing suspend
Mon Aug 17 09:10:43 CDT 2020: Awake.
Mon Aug 17 09:10:43 CDT 2020: Running hooks for resume
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
/usr/lib/pm-utils/sleep.d/99video resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254
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
Selected interface 'wlp2s0'
OK
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/40inputattach resume suspend:
/usr/lib/pm-utils/sleep.d/40inputattach resume suspend: success.

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

Mon Aug 17 09:10:51 CDT 2020: Finished.
```

---

### Post by #&amp;thj^% on 2021-02-24
I didn't see where you ran:
```
sudo chmod +x <name of your script>
```
I as a rule use this location for my scripts, "preferable to use **/lib/systemd/system-sleep/**"

---

### Post by raleigh3 on 2021-02-24
It has the exe bit set.

```
-rwxr-xr-x 1 root root   237 Feb 24 13:21 99_DoorBell.sh*
```

I put it in /lib/systemd/system-sleep/ also.

Still did not run?

---

### Post by ActionParsnip on 2021-02-24
[https://askubuntu.com/questions/226278/run-script-on-wakeup](https://askubuntu.com/questions/226278/run-script-on-wakeup)

Has a solution

---

### Post by raleigh3 on 2021-02-24
I tried it. 

Does not work for me.

---

