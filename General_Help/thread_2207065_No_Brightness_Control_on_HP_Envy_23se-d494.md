---
title: "No Brightness Control on HP Envy 23se-d494"
date: 2014-02-21
forum: General Help
---

### Post by lee-joshwa on 2014-02-21
As the title states, I have performed a clean install of 13.10 on an HP Envy 23se-d494.  I have no brightness slider and no key combos will adjust it either.  This appears to be the only issue I'm facing with the install...

Kernel boot line:
```

BOOT_IMAGE=/boot/vmlinuz-3.11.0-17-generic.efi.signed root=UUID=6946e2f7-431c-4348-a644-7f58fa552fa9 ro quiet splash vt.handoff=7

```

Video card info:
```

00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller (rev 06)
    Subsystem: Hewlett-Packard Company Device 2b04
    Kernel driver in use: i915

```

Backlight interfaces (I have none??):
```

/sys/class/backlight/*
cat: /sys/class/backlight/*/brightness: No such file or directory
cat: /sys/class/backlight/*/actual_brightness: No such file or directory
cat: /sys/class/backlight/*/max_brightness: No such file or directory

```

dmesg log file:
[http://paste.ubuntu.com/6974183/](http://paste.ubuntu.com/6974183/)

Xorg log file:
[http://paste.ubuntu.com/6974188/](http://paste.ubuntu.com/6974188/)

Kernel modules:
```

Module                  Size  Used by
usblp                  18746  0 
xt_tcpudp              12884  2 
iptable_filter         12810  1 
ip_tables              27239  1 iptable_filter
x_tables               34059  3 ip_tables,xt_tcpudp,iptable_filter
parport_pc             32701  0 
ppdev                  17671  0 
rfcomm                 69130  12 
bnep                   19704  2 
snd_hda_codec_idt      50341  1 
binfmt_misc            17468  1 
x86_pkg_temp_thermal    14162  0 
coretemp               13435  0 
kvm                   431720  0 
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
nls_iso8859_1          12713  1 
aesni_intel            55624  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
joydev                 17377  0 
hid_multitouch         17407  0 
hid_generic            12548  0 
hp_wmi                 14062  0 
sparse_keymap          13948  1 hp_wmi
snd_hda_intel          52267  6 
snd_hda_codec         188738  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102033  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30095  1 snd_seq_midi
lib80211_crypt_tkip    17619  0 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
btusb                  28267  0 
bluetooth             372041  22 bnep,btusb,rfcomm
microcode              23656  0 
serio_raw              13413  0 
rtsx_pci_ms            18151  0 
memstick               16760  1 rtsx_pci_ms
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
usbhid                 53014  0 
videobuf2_core         40499  1 uvcvideo
videodev              133509  2 uvcvideo,videobuf2_core
hid                   101762  3 hid_multitouch,hid_generic,usbhid
i915                  661339  3 
usb_storage            62062  1 
wl                   4207760  0 
snd_timer              29433  2 snd_pcm,snd_seq
lib80211               14381  2 wl,lib80211_crypt_tkip
snd                    69141  22 snd_hwdep,snd_timer,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
cfg80211              480503  1 wl
lpc_ich                21080  0 
drm_kms_helper         52710  1 i915
drm                   297056  4 i915,drm_kms_helper
i2c_algo_bit           13413  1 i915
mei_me                 18421  0 
mei                    77782  1 mei_me
soundcore              12680  1 snd
wmi                    19070  1 hp_wmi
video                  19318  1 i915
mac_hid                13205  0 
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
rtsx_pci_sdmmc         23527  0 
ahci                   25819  4 
r8169                  67581  0 
libahci                32009  1 ahci
mii                    13934  1 r8169
rtsx_pci               45546  2 rtsx_pci_ms,rtsx_pci_sdmmc

```



I'm hoping someone can provide some helpful insight to my issue.  Many thanks in advance!

---

### Post by Toz on 2014-02-21
Hello and welcome to the forums.

> **lee-joshwa said:**
> Backlight interfaces (I have none??):
```

/sys/class/backlight/*
cat: /sys/class/backlight/*/brightness: No such file or directory
cat: /sys/class/backlight/*/actual_brightness: No such file or directory
cat: /sys/class/backlight/*/max_brightness: No such file or directory

```
Indeed. Can you try booting with the **acpi_backlight=vendor** kernel parameter and see if this offers up a backlight interface. Information on how to boot with it temporarily to test, can be found by following the [Temporarily Add a Kernel Boot Parameter for Testing]("https://wiki.ubuntu.com/Kernel/KernelBootParameters") instructions. If you still get no backlight interfaces, try the **acpi_osi='!Windows 2012'** parameter. Post back the same results as your first post for each parameter.

---

### Post by lee-joshwa on 2014-02-22
I have already tried adding both of those to /etc/default/grub before my first post and had no results with either.  I will try them again in order to post results, but it will have to be tomorrow.  Thanks for your help, and I will have results up soon.

---

### Post by lee-joshwa on 2014-02-22
With **acpi_backlight=vendor **added:

Kernel boot line:
```

BOOT_IMAGE=/boot/vmlinuz-3.11.0-17-generic.efi.signed root=UUID=6946e2f7-431c-4348-a644-7f58fa552fa9 ro quiet splash acpi_backlight=vendor vt.handoff=7

```

Video card info:
```

00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller (rev 06)
    Subsystem: Hewlett-Packard Company Device 2b04
    Kernel driver in use: i915

```

[COLOR=#000000]Backlight interfaces:
[/COLOR]```
/sys/class/backlight/*
cat: /sys/class/backlight/*/brightness: No such file or directory
cat: /sys/class/backlight/*/actual_brightness: No such file or directory
cat: /sys/class/backlight/*/max_brightness: No such file or directory

```

dmesg log file:
[http://paste.ubuntu.com/6975229/](http://paste.ubuntu.com/6975229/)

Xorg log file:
[http://paste.ubuntu.com/6975233/](http://paste.ubuntu.com/6975233/)

Kernel modules:
```

Module                  Size  Used by
usblp                  18746  0 
xt_tcpudp              12884  2 
iptable_filter         12810  1 
ip_tables              27239  1 iptable_filter
x_tables               34059  3 ip_tables,xt_tcpudp,iptable_filter
parport_pc             32701  0 
ppdev                  17671  0 
rfcomm                 69130  12 
bnep                   19704  2 
binfmt_misc            17468  1 
snd_hda_codec_idt      50341  1 
nls_iso8859_1          12713  1 
x86_pkg_temp_thermal    14162  0 
coretemp               13435  0 
kvm                   431720  0 
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
aesni_intel            55624  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
hp_wmi                 14062  0 
sparse_keymap          13948  1 hp_wmi
snd_hda_intel          52267  3 
snd_hda_codec         188738  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102033  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30095  1 snd_seq_midi
microcode              23656  0 
lib80211_crypt_tkip    17619  0 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
serio_raw              13413  0 
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
videobuf2_core         40499  1 uvcvideo
videodev              133509  2 uvcvideo,videobuf2_core
usb_storage            62062  0 
joydev                 17377  0 
snd_timer              29433  2 snd_pcm,snd_seq
btusb                  28267  0 
bluetooth             372041  22 bnep,btusb,rfcomm
lpc_ich                21080  0 
wl                   4207760  0 
hid_multitouch         17407  0 
lib80211               14381  2 wl,lib80211_crypt_tkip
snd                    69141  16 snd_hwdep,snd_timer,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
cfg80211              480503  1 wl
rtsx_pci_ms            18151  0 
i915                  661339  3 
memstick               16760  1 rtsx_pci_ms
drm_kms_helper         52710  1 i915
drm                   297056  4 i915,drm_kms_helper
mei_me                 18421  0 
mei                    77782  1 mei_me
soundcore              12680  1 snd
i2c_algo_bit           13413  1 i915
wmi                    19070  1 hp_wmi
mac_hid                13205  0 
video                  19318  1 i915
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
hid_generic            12548  0 
usbhid                 53014  0 
hid                   101762  3 hid_multitouch,hid_generic,usbhid
rtsx_pci_sdmmc         23527  0 
ahci                   25819  4 
r8169                  67581  0 
libahci                32009  1 ahci
rtsx_pci               45546  2 rtsx_pci_ms,rtsx_pci_sdmmc
mii                    13934  1 r8169

```

---

### Post by lee-joshwa on 2014-02-22
With **acpi_osi='!Windows 2012'** added:

Kernel boot line:
```

BOOT_IMAGE=/boot/vmlinuz-3.11.0-17-generic.efi.signed root=UUID=6946e2f7-431c-4348-a644-7f58fa552fa9 ro quiet splash "acpi_osi=!Windows 2012" vt.handoff=7

```

Video card info:
```

00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller (rev 06)
	Subsystem: Hewlett-Packard Company Device 2b04
	Kernel driver in use: i915

```

Backlight interfaces:
```

/sys/class/backlight/*
cat: /sys/class/backlight/*/brightness: No such file or directory
cat: /sys/class/backlight/*/actual_brightness: No such file or directory
cat: /sys/class/backlight/*/max_brightness: No such file or directory

```

dmesg log file:
[http://paste.ubuntu.com/6975269/](http://paste.ubuntu.com/6975269/)

Xorg log file:
[http://paste.ubuntu.com/6975272/](http://paste.ubuntu.com/6975272/)

Kernel modules:
```

Module                  Size  Used by
usblp                  18746  0 
xt_tcpudp              12884  2 
iptable_filter         12810  1 
ip_tables              27239  1 iptable_filter
x_tables               34059  3 ip_tables,xt_tcpudp,iptable_filter
parport_pc             32701  0 
ppdev                  17671  0 
rfcomm                 69130  12 
bnep                   19704  2 
snd_hda_codec_idt      50341  1 
binfmt_misc            17468  1 
nls_iso8859_1          12713  1 
x86_pkg_temp_thermal    14162  0 
coretemp               13435  0 
kvm                   431720  0 
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
aesni_intel            55624  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
hp_wmi                 14062  0 
sparse_keymap          13948  1 hp_wmi
snd_hda_intel          52267  3 
snd_hda_codec         188738  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102033  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
lib80211_crypt_tkip    17619  0 
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30095  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
microcode              23656  0 
snd_timer              29433  2 snd_pcm,snd_seq
btusb                  28267  0 
bluetooth             372041  22 bnep,btusb,rfcomm
serio_raw              13413  0 
snd                    69141  16 snd_hwdep,snd_timer,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
hid_multitouch         17407  0 
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
wl                   4207760  0 
videobuf2_core         40499  1 uvcvideo
joydev                 17377  0 
videodev              133509  2 uvcvideo,videobuf2_core
lib80211               14381  2 wl,lib80211_crypt_tkip
usb_storage            62062  0 
cfg80211              480503  1 wl
lpc_ich                21080  0 
rtsx_pci_ms            18151  0 
memstick               16760  1 rtsx_pci_ms
soundcore              12680  1 snd
mei_me                 18421  0 
mei                    77782  1 mei_me
mac_hid                13205  0 
i915                  661339  3 
drm_kms_helper         52710  1 i915
video                  19318  1 i915
drm                   297056  4 i915,drm_kms_helper
lp                     17759  0 
wmi                    19070  1 hp_wmi
i2c_algo_bit           13413  1 i915
parport                42299  3 lp,ppdev,parport_pc
hid_generic            12548  0 
usbhid                 53014  0 
hid                   101762  3 hid_multitouch,hid_generic,usbhid
rtsx_pci_sdmmc         23527  0 
rtsx_pci               45546  2 rtsx_pci_ms,rtsx_pci_sdmmc
r8169                  67581  0 
ahci                   25819  4 
mii                    13934  1 r8169
libahci                32009  1 ahci

```

---

### Post by Toz on 2014-02-22
Hmmm, you're system isn't exposing a backlight interface. Looks like you're not the only one with this problem: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1152544]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1152544").

Have a quick look in your bios to see if there are any backlight-related options.

---

### Post by lee-joshwa on 2014-02-22
> **Toz said:**
> Hmmm, you're system isn't exposing a backlight interface. Looks like you're not the only one with this problem: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1152544](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1152544).

Have a quick look in your bios to see if there are any backlight-related options.

I've already hunted through bios.  There is nothing there.  I also tried an install disk for 13.04, but it does not display at all.

---

### Post by lee-joshwa on 2014-02-23
I hoped that a driver update may help out, but it has had no effect.

Installer: [https://01.org/linuxgraphics/downloads](https://01.org/linuxgraphics/downloads)

Result:
```

intel-gpu-tools:amd64 (from 1.3-0ubuntu2 to 1.4-0intel1)
    libva-x11-1:amd64 (from 1.1.1-3 to 1.2.1-1)
    libva1:amd64 (from 1.1.1-3 to 1.2.1-1)

```

---

### Post by lee-joshwa on 2014-03-02
Is there nothing else I can try in order to gain a backlight interface?

---

### Post by Toz on 2014-03-02
Your best bet would be to follow the exist bug report and add your information to it. This needs to be fixed at the kernel level.

If possible, try downloading the 14.04 beta cd and temporarily booting with it (don't install). It has a newer kernel version. See if it offers up a backlight interface for your system and whether brightness controls work.

---

### Post by lee-joshwa on 2014-03-05
Thank you for your help.  The bug which had been linked to was a year old and still held an incomplete status.  I commented with my machine info on that thread, but I also created a new bug report which may be located here:  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1287528](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1287528)

---

