---
title: "Ubuntu 13.04 Won't Suspend - Screen Goes Dark, System Still Running but Frozen"
date: 2013-08-10
forum: General Help
---

### Post by fortitude on 2013-08-10
Hi again everyone!

I'm here with another nagging issue with the core functionality of Ubuntu.

**I can't get my computer to suspend properly.** It used to work fine with the same hardware.

What happens is, I'll go to the power button on the upper right of the screen and select Suspend from the menu. Next, the screen will go black, and the hard drives, fans and mouse lights will turn off as expected. Then, about one second later, the computer fans and lights come back on again but the screen stays dark and there is no way to get any response from the system, forcing a hard reset.

I'm on a fresh install of Ubuntu 13.04 AMD64.

System type: desktop workstation
Processor: quad core AMD
Ram : 4 GB
Video card: Nvidia GT 545 GDDR5 with the recommended proprietary driver from System Software & Updates/Additional Drivers (310.44).
Hard disks: Samsung SSD, Samsung 7200 RPM storage drive (not mounted),  Seagate 7200 RPM storage drive (mounted with fstab at boot).
Network: static internal network IP assigned to system.
User accounts: Only one account.

Things I have tried: Testing with open source driver prior to installing the proprietary driver or any packages or patches, Fresh install of Ubuntu 12.04 LTS, similar issue. I once tried enabling hibernation by altering some settings and that worked fine most of the time even though suspend would not.

---

### Post by fortitude on 2013-08-10
Just thought I'd add that about one minute after the improper suspend, the video card fan cranks to maximum speed until the system is turned off manually.

---

### Post by fortitude on 2013-08-10
/var/log/pm-suspend.log
> 
Initial commandline parameters: 
Sat Aug 10 12:14:08 PDT 2013: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:

/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux [hostname] 3.8.0-27-generic #40-Ubuntu SMP Tue Jul 9 00:17:05 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
ext2                   72837  1 
pci_stub               12622  1 
vboxpci                23194  0 
vboxnetadp             25670  0 
vboxnetflt             27613  0 
vboxdrv               320461  3 vboxnetadp,vboxnetflt,vboxpci
parport_pc             28152  0 
ppdev                  17073  0 
bnep                   18036  2 
rfcomm                 42641  0 
bluetooth             228667  10 bnep,rfcomm
binfmt_misc            17500  1 
joydev                 17377  0 
hid_generic            12540  0 
snd_hda_codec_hdmi     36913  4 
usbhid                 47074  1 
hid                   101002  2 hid_generic,usbhid
usb_storage            57204  1 
kvm_amd                59717  0 
kvm                   443165  1 kvm_amd
microcode              22881  0 
snd_hda_codec_realtek    78399  1 
k10temp                13126  0 
nvidia               9410995  38 
serio_raw              13215  0 
edac_core              62003  0 
edac_mce_amd           23114  0 
snd_hda_intel          39619  5 
snd_hda_codec         136453  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
sp5100_tco             13735  0 
i2c_piix4              13266  0 
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  1 snd_seq_midi
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29425  2 snd_pcm,snd_seq
snd                    68876  20 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
wmi                    19070  0 
soundcore              12680  1 snd
mac_hid                13205  0 
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
floppy                 69449  0 
pata_acpi              13038  0 
pata_atiixp            13242  1 
r8169                  67466  0 
ahci                   25731  3 
libahci                31364  1 ahci
             total       used       free     shared    buffers     cached
Mem:       4049004    1511188    2537816          0      43004    1164564
-/+ buffers/cache:     303620    3745384
Swap:      4194300          0    4194300

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
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
/usr/lib/pm-utils/sleep.d/99video: 22: /usr/lib/pm-utils/sleep.d/99video: shopt: not found
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Sat Aug 10 12:14:09 PDT 2013: performing suspend
Sat Aug 10 12:14:36 PDT 2013: Awake.
Sat Aug 10 12:14:36 PDT 2013: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
/usr/lib/pm-utils/sleep.d/99video: 22: /usr/lib/pm-utils/sleep.d/99video: shopt: not found

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

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
Sat Aug 10 12:14:37 PDT 2013: Finished.

---

### Post by fortitude on 2013-08-10
Updated to version [1.4.1-11]("https://launchpad.net/ubuntu/saucy/amd64/pm-utils/1.4.1-11") of pm-utils (as you know, Ubuntu 13.04 ships with pm-utils 1.4.1-9). /var/log/pm-suspend.log is slightly different now but the symptoms are the same.

> Initial commandline parameters: 
Sat Aug 10 12:36:36 PDT 2013: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:

/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux [hostname] 3.8.0-27-generic #40-Ubuntu SMP Tue Jul 9 00:17:05 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
ext2                   72837  1 
pci_stub               12622  1 
vboxpci                23194  0 
vboxnetadp             25670  0 
vboxnetflt             27613  0 
vboxdrv               320461  3 vboxnetadp,vboxnetflt,vboxpci
parport_pc             28152  0 
ppdev                  17073  0 
rfcomm                 42641  0 
bnep                   18036  2 
bluetooth             228667  10 bnep,rfcomm
binfmt_misc            17500  1 
snd_hda_codec_hdmi     36913  4 
joydev                 17377  0 
hid_generic            12540  0 
kvm_amd                59717  0 
kvm                   443165  1 kvm_amd
usbhid                 47074  1 
microcode              22881  0 
hid                   101002  2 hid_generic,usbhid
usb_storage            57204  1 
snd_hda_codec_realtek    78399  1 
serio_raw              13215  0 
snd_hda_intel          39619  5 
k10temp                13126  0 
snd_hda_codec         136453  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
edac_core              62003  0 
edac_mce_amd           23114  0 
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
nvidia               9410995  38 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  1 snd_seq_midi
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29425  2 snd_pcm,snd_seq
sp5100_tco             13735  0 
i2c_piix4              13266  0 
snd                    68876  20 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
wmi                    19070  0 
mac_hid                13205  0 
soundcore              12680  1 snd
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
floppy                 69449  0 
pata_acpi              13038  0 
ahci                   25731  3 
libahci                31364  1 ahci
r8169                  67466  0 
pata_atiixp            13242  1 
             total       used       free     shared    buffers     cached
Mem:       4049004    1933316    2115688          0      72300    1411096
-/+ buffers/cache:     449920    3599084
Swap:      4194300          0    4194300

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
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
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Sat Aug 10 12:36:37 PDT 2013: performing suspend
\00\00 [repeat with a lot more slashes and zeros, gedit can't read whatever this is due to chracter set issues]

---

### Post by fortitude on 2013-08-10
Tried [this fix]("http://ubuntuforums.org/showthread.php?t=1596545&page=4&p=9992908#post9992908") (adding "acpi_sleep=nonvs" to grub) and it made no difference.

---

### Post by fortitude on 2013-08-10
Added [this script]("http://ubuntuforums.org/showthread.php?t=1969615&p=11904554#post11904554") to /etc/pm/sleep.d to disable echi / ohci / uhci ports on suspend and reenable them on resume, but it did not help me.

---

### Post by fortitude on 2013-08-10
Output of cat /proc/acpi/wakeup
> Device    S-state      Status   Sysfs node
PCE2      S4    *disabled  pci:0000:00:02.0
PCE3      S4    *disabled
PCE4      S4    *disabled  pci:0000:00:04.0
PCE5      S4    *disabled  pci:0000:00:05.0
PCE6      S4    *disabled
PCE7      S4    *disabled
PCE9      S4    *disabled
PCEA      S4    *disabled
PCEB      S4    *disabled
PCEC      S4    *disabled
SBAZ      S4    *disabled  pci:0000:00:14.2
PS2K      S3    *enabled   pnp:00:09
P0PC      S4    *disabled  pci:0000:00:14.4
UHC1      S4    *enabled   pci:0000:00:12.0
UHC2      S4    *enabled   pci:0000:00:12.1
UHC3      S4    *enabled   pci:0000:00:12.2
USB4      S4    *enabled   pci:0000:00:13.0
UHC5      S4    *enabled   pci:0000:00:13.1
UHC6      S4    *enabled   pci:0000:00:13.2
UHC7      S4    *enabled   pci:0000:00:14.5
PWRB      S3    *disabled

Tried the script from [here]("http://ubuntuforums.org/showthread.php?t=1969615&p=11931813#post11931813") which claims to disable USB devices so that systems can suspend properly. Seems it's worked for several people.

Installed it with sudo install -o root -g root -m 755 8_disable_USB.sh /etc/pm/sleep.d/ 

No difference.

Edited the regex to match pretty much everything except PS2K and no luck either.

grep -o -P '^USB[0-9](?=.*\*enabled)' /proc/acpi/wakeup

to

grep -o -P '^[a-zA-Z]{1,4}[0-9](?=.*\*enabled)' /proc/acpi/wakeup

No difference.

---

### Post by fortitude on 2013-08-11
Hibernation works fine when [enabled]("https://help.ubuntu.com/12.04/ubuntu-help/power-hibernate.html"). It's just slower. If anyone has any ideas on how to troubleshoot suspend, please let me know. :)

---

### Post by fortitude on 2013-08-12
I tried adding SUSPEND_MODULES="xhci" to /etc/pm/config.d/unload_module but that did nothing.

---

