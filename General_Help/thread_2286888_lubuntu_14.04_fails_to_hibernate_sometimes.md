---
title: "lubuntu 14.04 fails to hibernate sometimes"
date: 2015-07-15
forum: General Help
---

### Post by Jose_H_G on 2015-07-15
My computer fails to hibernate sometimes, so i'm trying to figure out what is the problem.
I'm using lubuntu 14.04 amd64 on my computer and it has 4GB RAM, my swap partition is active and it has a size of 8GB.

I've created an entry for both upower and systemd in my polkit (/etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla)
```
[Re-enable hibernate by default in upower]
Identity=unix-user:*
Action=org.freedesktop.upower.hibernate
ResultActive=yes

[Re-enable hibernate by default in logind]
Identity=unix-user:*
Action=org.freedesktop.login1.hibernate
ResultActive=yes
```

Actually everything seems to be fine because, in fact, sometimes hibernation works successfully.
Looking for errors in /var/log/suspend.log, i found this:
    Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
    Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
    /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.

it seems to be a result af the execution of this command: wpa_cli suspend without privileges

Here is cut of my suspend.log for the last performing hibernate that wasn't finished:

```
Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:
/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status hibernate hibernate:
/usr/lib/pm-utils/sleep.d/000record-status hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux higar-lab 3.13.0-55-generic #94-Ubuntu SMP Thu Jun 18 00:27:10 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
pci_stub               12622  1 
vboxpci                23194  0 
vboxnetadp             25670  0 
vboxnetflt             27613  0 
vboxdrv               339502  3 vboxnetadp,vboxnetflt,vboxpci
bnep                   19624  2 
rfcomm                 69160  8 
uvcvideo               80885  0 
samsung_laptop         14486  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
videodev              134688  2 uvcvideo,videobuf2_core
kvm_amd                60026  0 
kvm                   455794  1 kvm_amd
snd_hda_codec_realtek    65626  1 
btusb                  32412  0 
bluetooth             391136  22 bnep,btusb,rfcomm
wl                   6367819  0 
snd_hda_codec_hdmi     46368  1 
snd_hda_intel          56531  5 
snd_hda_codec         192980  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_seq_midi           13324  0 
snd_hwdep              13602  1 snd_hda_codec
snd_seq_midi_event     14899  1 snd_seq_midi
joydev                 17381  0 
serio_raw              13462  0 
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_rawmidi            30144  1 snd_seq_midi
k10temp                13126  0 
cfg80211              484040  1 wl
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
i2c_piix4              22155  0 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
snd                    69322  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
soundcore              12680  1 snd
shpchp                 37032  0 
parport_pc             32701  0 
ppdev                  17671  0 
mac_hid                13205  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
hid_generic            12548  0 
usbhid                 52659  0 
hid                   106148  2 hid_generic,usbhid
psmouse               106590  0 
r8169                  67581  0 
mii                    13934  1 r8169
radeon               1522664  2 
ahci                   29915  3 
libahci                32716  1 ahci
i2c_algo_bit           13413  1 radeon
video                  19476  1 samsung_laptop
ttm                    93424  1 radeon
drm_kms_helper         55071  1 radeon
drm                   303102  4 ttm,drm_kms_helper,radeon
             total       used       free     shared    buffers     cached
Mem:       3786540    2920756     865784      40184     466984    1013628
-/+ buffers/cache:    1440144    2346396
Swap:      8388604       8260    8380344
/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:
/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/01laptop-mode hibernate hibernate:
/usr/lib/pm-utils/sleep.d/01laptop-mode hibernate hibernate: success.

Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:
/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.

Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/50unload_alx hibernate hibernate:
/usr/lib/pm-utils/sleep.d/50unload_alx hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:
/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:
/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:
/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:
stop: Unknown instance: 
/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:
/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:
/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:
/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
Kernel modesetting video driver detected, not using quirks.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:
/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.

CEST 2015: performing hibernate
```

So my question is am i in the right direction? if so how can i avoid this error?
Thanks in advance.

---

