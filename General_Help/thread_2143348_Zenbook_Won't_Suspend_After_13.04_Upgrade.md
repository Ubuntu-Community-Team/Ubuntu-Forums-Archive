---
title: "Zenbook Won't Suspend After 13.04 Upgrade"
date: 2013-05-08
forum: General Help
---

### Post by Dan Again on 2013-05-08
Title is pretty self-explanatory. Everything was working fine until I upgraded. Any ideas how to fix this?

---

### Post by Toz on 2013-05-08
What exactly happens when you try to suspend?

Can you show us:

1. The contents of /var/log/pm-suspend.log:
```
pastebinit /var/log/pm-suspend.log
```
...and post back the link that is generated.

2. The results of this command:
```
cat /var/log/syslog | grep PM:
```

3. Your current kernel boot line:
```
cat /proc/cmdline
```

4. Info about your video cards and drivers:
```
sudo lspci -vnn | grep -A12 VGA
```

5. The model of the Zenbook:
```
sudo dmidecode -s system-product-name
```

---

### Post by Dan Again on 2013-05-08
> The contents of /var/log/pm-suspend.log:
```
You have exceeded the maximum file size of 500 kilobytes per paste.
```

> The results of this command:
```
NULL
```

> Your current kernel boot line:
```
BOOT_IMAGE=/boot/vmlinuz-3.8.0-19-generic root=UUID=b1b470ab-0ae4-487d-8676-042bcb459fda ro quiet splash pcie_aspm=force vt.handoff=7
```

> Info about your video cards and drivers:
```
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09) (prog-if 00 [VGA controller])
	Subsystem: ASUSTeK Computer Inc. Device [1043:1427]
	Flags: bus master, fast devsel, latency 0, IRQ 52
	Memory at ddc00000 (64-bit, non-prefetchable) [size=4M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at e000 [size=64]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [d0] Power Management version 2
	Capabilities: [a4] PCI Advanced Features
	Kernel driver in use: i915

00:16.0 Communication controller [0780]: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)

```

> The model of the Zenbook:
```
UX31E
```

---

### Post by Toz on 2013-05-08
Lets make /var/log/pm-suspend.log shorter:

```
sudo rm /var/log/pm-suspend.log
```
...then try a suspend again. When you recover:
```
pastebinit /var/log/pm-suspend.log
```
...and post back the link that is generated.

BTW, what exactly happens when you try to suspend?

---

### Post by Dan Again on 2013-05-08
```
cat /var/log/pm-suspend.log
Initial commandline parameters: 
Wed May  8 18:49:43 CDT 2013: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:

/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Zenbook 3.8.0-19-generic #30-Ubuntu SMP Wed May 1 16:35:23 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
parport_pc             28152  0 
ppdev                  17073  0 
vesafb                 13828  0 
rfcomm                 42641  12 
bnep                   18036  2 
snd_hda_codec_hdmi     36913  1 
snd_hda_codec_realtek    78399  1 
binfmt_misc            17500  1 
ath3k                  12918  0 
btusb                  22474  0 
bluetooth             228619  23 bnep,ath3k,btusb,rfcomm
kvm_intel             132891  0 
kvm                   443165  1 kvm_intel
joydev                 17377  0 
ghash_clmulni_intel    13259  0 
hid_generic            12540  0 
rts5139               352481  0 
aesni_intel            55399  0 
aes_x86_64             17255  1 aesni_intel
xts                    12885  1 aesni_intel
lrw                    13257  1 aesni_intel
gf128mul               14951  2 lrw,xts
ablk_helper            13597  1 aesni_intel
cryptd                 20373  3 ghash_clmulni_intel,aesni_intel,ablk_helper
uvcvideo               80847  0 
videobuf2_vmalloc      13056  1 uvcvideo
usbhid                 47074  0 
videobuf2_memops       13202  1 videobuf2_vmalloc
videobuf2_core         40513  1 uvcvideo
videodev              129260  2 uvcvideo,videobuf2_core
hid                   101002  2 hid_generic,usbhid
asus_nb_wmi            12854  0 
asus_wmi               24213  1 asus_nb_wmi
sparse_keymap          13890  1 asus_wmi
snd_hda_intel          39619  3 
snd_hda_codec         136453  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
arc4                   12615  2 
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
ath9k                 149924  0 
snd_rawmidi            30180  1 snd_seq_midi
ath9k_common           14055  1 ath9k
ath9k_hw              413680  2 ath9k_common,ath9k
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29425  2 snd_pcm,snd_seq
ath                    23827  3 ath9k_common,ath9k,ath9k_hw
microcode              22881  0 
snd                    68876  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
mac80211              606457  1 ath9k
psmouse                95870  0 
serio_raw              13215  0 
soundcore              12680  1 snd
i915                  600351  3 
cfg80211              510937  3 ath,ath9k,mac80211
drm_kms_helper         49394  1 i915
drm                   286313  4 i915,drm_kms_helper
mei                    41158  0 
video                  19390  2 i915,asus_wmi
lpc_ich                17061  0 
i2c_algo_bit           13413  1 i915
wmi                    19070  1 asus_wmi
mac_hid                13205  0 
coretemp               13355  0 
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
ahci                   25731  2 
libahci                31364  1 ahci
             total       used       free     shared    buffers     cached
Mem:       3948064     842816    3105248          0      58812     422600
-/+ buffers/cache:     361404    3586660
Swap:      4092924          0    4092924

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /etc/pm/sleep.d/20_zenbook suspend suspend:
/etc/pm/sleep.d/20_zenbook: 6: /etc/pm/sleep.d/20_zenbook: cannot create /sys/bus/pci/drivers/ehci_hcd/unbind: Directory nonexistent
/etc/pm/sleep.d/20_zenbook: 6: /etc/pm/sleep.d/20_zenbook: cannot create /sys/bus/pci/drivers/ehci_hcd/unbind: Directory nonexistent

/etc/pm/sleep.d/20_zenbook suspend suspend: Returned exit code 2.
Wed May  8 18:49:43 CDT 2013: Inhibit found, will not perform suspend
Wed May  8 18:49:43 CDT 2013: Running hooks for resume
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

```

The system just doesn't suspend. When I shut the lid, the screen turns off, but the system doesn't suspend.

---

### Post by Toz on 2013-05-08
> Running hook /etc/pm/sleep.d/20_zenbook suspend suspend:
/etc/pm/sleep.d/20_zenbook: 6: /etc/pm/sleep.d/20_zenbook: cannot create /sys/bus/pci/drivers/ehci_hcd/unbind: Directory nonexistent
/etc/pm/sleep.d/20_zenbook: 6: /etc/pm/sleep.d/20_zenbook: cannot create /sys/bus/pci/drivers/ehci_hcd/unbind: Directory nonexistent

/etc/pm/sleep.d/20_zenbook suspend suspend: Returned exit code 2.
Wed May  8 18:49:43 CDT 2013: Inhibit found, will not perform suspend

Delete /etc/pm/sleep.d/20_zenbook. Its no longer required for 13.04.

---

### Post by Dan Again on 2013-05-08
Worked like a charm! Mare see bo koo!

---

### Post by Toz on 2013-05-08
> **Dan Again said:**
> Mare see bo koo!
lol.

If you don't mind, can you mark this thread as Solved so that others can benefit? To mark the thread as Solved, select "Edit" on your original first post, click "Go Advanced", change the Prefix to "[SOLVED]" and Save.

---

