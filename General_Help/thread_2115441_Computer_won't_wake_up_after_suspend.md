---
title: "Computer won't wake up after suspend"
date: 2013-02-12
forum: General Help
---

### Post by xeitgeixt on 2013-02-12
I'd really like to make Ubuntu my primary OS- but I'm having so many challenges with it that its proving not worth my time.

The latest problem, when Ubuntu suspends, my computer won't wake up. 

Now wait, wait, wait...

Someone is going to tell me that dozens of other threads are devoted to this issue. Whilst this statement is correct, it negates a huge fact...

*there is no workable or common sense solution to the problem*

Could someone please help?

---

### Post by Toz on 2013-02-12
Could you provide some more information to help diagnose the problem?

1. The make and model of your computer.

2. The contents of your /var/log/pm-suspend.log file. Try this from a terminal window:
```
pastebinit /var/log/pm-suspend.log
```
...and post back the link that is generated.

3. Information about your video card. Run this in a terminal window and post back the results:
```
sudo lspci -vnn | grep -A12 VGA
```

4. And finally, your current kernel command line:
```
cat /proc/cmdline
```

---

### Post by tgalati4 on 2013-02-12
I had to upgrade the BIOS on my Acer Extensa 4620Z laptop.  None of the dozen suggestions that I searched for worked.  So consider a BIOS upgrade.

---

### Post by Smythe311 on 2013-04-05
Toz,

I am having a similar problem with my Dell Studio 1440 laptop. If I close the lid or click "Suspend" from the menu the laptop will go to sleep. The problem occurs when trying to use it again. The keyboard is active, the fan revs up, however the screen is completely dark, as if it never gets turned on. I've tried various keyboard combinations to "get the attention" of the screen to no avail. The only way out is a harsh reboot. Note that this problem isn't unique to Ubuntu, Linux or Dell. Having searched for several hours and trying various solutions, I'm at a loss. I'm including the information you requested below:

The results of [COLOR=#000000][FONT=Ubuntu Mono]pastebinit /var/log/pm-suspend.log [/FONT][/COLOR]

[http://pastebin.com/5xkpucFy](http://pastebin.com/5xkpucFy)

The results of 
sudo lspci -vnn | grep -A12 VGA

01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI RV710 [Mobility Radeon HD 4500/5100 Series] [1002:9553] (prog-if 00 [VGA controller])
	Subsystem: Dell Device [1028:0414]
	Flags: bus master, fast devsel, latency 0, IRQ 43
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at 2000 [size=256]
	Memory at cfef0000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at cfe00000 [disabled] [size=128K]
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Legacy Endpoint, MSI 00
	Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
	Kernel driver in use: radeon
	Kernel modules: radeon


Results of 
cat /proc/cmdline

BOOT_IMAGE=/boot/vmlinuz-3.5.0-17-generic root=UUID=b30dcf90-3dd6-42ae-badb-3a64a72036ca ro quiet splash vt.handoff=7

Any assistance would be most appreciated.
Thx.

---

### Post by maglinu on 2013-04-05
I have a machine where I need to include 'noapic' in boot options to get some distro's to resume from suspend. Probably very harware specific, but may be worth a shot?

---

### Post by Toz on 2013-04-05
> **Smythe311 said:**
> Toz,

I am having a similar problem with my Dell Studio 1440 laptop. If I close the lid or click "Suspend" from the menu the laptop will go to sleep. The problem occurs when trying to use it again. The keyboard is active, the fan revs up, however the screen is completely dark, as if it never gets turned on. I've tried various keyboard combinations to "get the attention" of the screen to no avail. The only way out is a harsh reboot. Note that this problem isn't unique to Ubuntu, Linux or Dell. Having searched for several hours and trying various solutions, I'm at a loss. I'm including the information you requested below:

The results of [COLOR=#000000][FONT=Ubuntu Mono]pastebinit /var/log/pm-suspend.log [/FONT][/COLOR]

[http://pastebin.com/5xkpucFy](http://pastebin.com/5xkpucFy)
Whats interesting is that I don't see a successful suspend/resume in the log file at all. Are you sure the laptop is going to sleep on the first attempt? Can you post back a log file after a successful then unsuccessful suspend attempt?

> The results of 
sudo lspci -vnn | grep -A12 VGA

01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI RV710 [Mobility Radeon HD 4500/5100 Series] [1002:9553] (prog-if 00 [VGA controller])
	Subsystem: Dell Device [1028:0414]
	Flags: bus master, fast devsel, latency 0, IRQ 43
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at 2000 [size=256]
	Memory at cfef0000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at cfe00000 [disabled] [size=128K]
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Legacy Endpoint, MSI 00
	Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
	Kernel driver in use: radeon
	Kernel modules: radeon

You are using the radeon driver. Which version of Ubuntu are you running? 12.10? Do you have the ATI proprietary driver available in the additional drivers application? Sometimes the proprietary driver is better at suspending. 
> 
Results of 
cat /proc/cmdline

BOOT_IMAGE=/boot/vmlinuz-3.5.0-17-generic root=UUID=b30dcf90-3dd6-42ae-badb-3a64a72036ca ro quiet splash vt.handoff=7

Any assistance would be most appreciated.
Thx.
Nevermind about the proprietary video driver, ATI dropped support for this video card in kernel 3.5. (>12.04).

Two suggestions:
[LIST=1]
[*]Try booting with the **nomodeset** kernel parmeter (see the "Temporarily Add a Boot Kernel Parameter" section [here]("https://wiki.ubuntu.com/Kernel/KernelBootParameters") for more info)
[*]You could try doing a "resume trace debug" to see if you can identify the problem driver (in case its not the video card). See [here]("https://wiki.ubuntu.com/DebuggingKernelSuspend#A.22resume-trace.22_debugging_procedure_for_finding_buggy_drivers") for information on how to do it.
[/LIST]

---

### Post by knowNothing23 on 2013-06-21
This post is very relevant. Please, respond if you have solved the problem. 

Seriously, I agree with the OP. This problem has been persistent in my distributions of Ubuntu for at least 4 years. I can never suspend the pc for that reason.
Whenever I change to proprietary drivers my GUI just disappears from boot options and I have to use the terminal to re-establish the open source drivers. :/

I will try your approaches to the problem, thank you.

---

### Post by kurt18947 on 2013-06-21
The times I've had suspend/resume problems, it's been either the open video driver or *some* iterations of the proprietary driver.  I have an AMD MoBo - 785 chipset- and Nvidia PCIe video.  Presently on 13.10, I had issues with Nvidia 304 which was installed by default.   Nvidia 319 experimental has been fine.  Suspend/resume works, flash in Firefox behaves, life is good for the moment:cool:.

---

### Post by gp2x on 2013-11-20
What gets up my nose is that my suspend was working perfectly in 13.04, and now its broken again in 13.10. I think it has something to do with fglrx, but getting working gfx drivers is so painful I dont want to swap out to a different driver.....

bleh.

---

### Post by cr4bb4tt13 on 2013-12-09
What do you do if an acer aspire one doesn't ever turn back on after you, put it in suspend, find out it's not working, then manually turn off?

---

### Post by alexandercrfordyce on 2013-12-21
I'd really like some insight to this as well. I'm on an older iMac (2006). It seems to me that the computer just turns off rather than suspending. I can only bring it back by holding the power button down for about 5 seconds and then pressing it again. Any help would be greatly appreciated!

```
/var/log/pm-suspend.log

Initial commandline parameters:
Sat Dec 21 19:22:14 PST 2013: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux afordyce-iMac 3.11.0-14-generic #21-Ubuntu SMP Tue Nov 12 17:07:40 UTC 2013 i686 i686 i686 GNU/Linux
Module                  Size  Used by
parport_pc             31981  0
ppdev                  17391  0
bnep                   18893  2
rfcomm                 53664  16
nls_utf8               12493  3
hfsplus                92933  3
btusb                  23443  0
bluetooth             323622  22 bnep,btusb,rfcomm
rc_pinnacle_pctv_hd    12481  0
em28xx_rc              13145  0
rc_core                26398  3 em28xx_rc,rc_pinnacle_pctv_hd
lgdt330x               13780  1
em28xx_dvb             22703  0
dvb_core              101124  2 em28xx_dvb,lgdt330x
em28xx_alsa            17857  1
hid_generic            12492  0
coretemp               13195  0
kvm_intel             128218  0
kvm                   364766  1 kvm_intel
hid_apple              13052  0
tuner_xc2028           26614  2
tuner                  26740  1
hid_appleir            12866  0
tvp5150                21917  1
usbhid                 47361  0
em28xx                 93442  3 em28xx_dvb,em28xx_rc,em28xx_alsa
hid                    87370  4 hid_generic,usbhid,hid_appleir,hid_apple
tveeprom               16984  1 em28xx
v4l2_common            15812  3 tuner,em28xx,tvp5150
videobuf2_vmalloc      13048  1 em28xx
videobuf2_memops       13170  1 videobuf2_vmalloc
videobuf2_core         39125  1 em28xx
videodev              107508  5 tuner,em28xx,tvp5150,v4l2_common,videobuf2_core
applesmc               18772  0
input_polldev          13648  1 applesmc
firewire_sbp2          18017  2
microcode              18830  0
radeon               1307301  2
ttm                    71886  1 radeon
lib80211_crypt_tkip    17387  0
drm_kms_helper         46867  1 radeon
lpc_ich                16864  0
snd_hda_codec_idt      44605  1
drm                   242354  4 ttm,drm_kms_helper,radeon
snd_hda_intel          42658  3
wl                   3999432  0
lib80211               14040  2 wl,lib80211_crypt_tkip
cfg80211              401436  1 wl
snd_hda_codec         164003  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                89488  3 snd_hda_codec,snd_hda_intel,em28xx_alsa
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25094  1 snd_seq_midi
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              24447  2 snd_pcm,snd_seq
snd                    60790  19 snd_hwdep,snd_timer,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,em28xx_alsa,snd_seq_midi
video                  18777  0
apple_bl               13681  0
mac_hid                13037  0
i2c_algo_bit           13197  1 radeon
soundcore              12600  1 snd
lp                     13299  0
parport                40795  3 lp,ppdev,parport_pc
usb_storage            48294  0
firewire_ohci          35257  0
firewire_core          57656  2 firewire_ohci,firewire_sbp2
crc_itu_t              12627  1 firewire_core
sky2                   52910  0
             total       used       free     shared    buffers     cached
Mem:       3087448    2867188     220260          0       3304    2542536
-/+ buffers/cache:     321348    2766100
Swap:     31831036      13200   31817836
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
Kernel modesetting video driver detected, not using quirks.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0
/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.

Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.

Sat Dec 21 19:22:15 PST 2013: performing suspend
Initial commandline parameters:
Sat Dec 21 19:59:30 PST 2013: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux afordyce-iMac 3.11.0-14-generic #21-Ubuntu SMP Tue Nov 12 17:07:40 UTC 2013 i686 i686 i686 GNU/Linux
Module                  Size  Used by
parport_pc             31981  0
ppdev                  17391  0
bnep                   18893  2
rfcomm                 53664  16
nls_utf8               12493  3
hfsplus                92933  3
btusb                  23443  0
bluetooth             323622  22 bnep,btusb,rfcomm
rc_pinnacle_pctv_hd    12481  0
em28xx_rc              13145  0
rc_core                26398  3 em28xx_rc,rc_pinnacle_pctv_hd
lgdt330x               13780  1
em28xx_dvb             22703  0
dvb_core              101124  2 em28xx_dvb,lgdt330x
em28xx_alsa            17857  1
tuner_xc2028           26614  2
hid_generic            12492  0
coretemp               13195  0
kvm_intel             128218  0
kvm                   364766  1 kvm_intel
tuner                  26740  1
hid_apple              13052  0
hid_appleir            12866  0
tvp5150                21917  1
usbhid                 47361  0
hid                    87370  4 hid_generic,usbhid,hid_appleir,hid_apple
em28xx                 93442  3 em28xx_dvb,em28xx_rc,em28xx_alsa
tveeprom               16984  1 em28xx
v4l2_common            15812  3 tuner,em28xx,tvp5150
videobuf2_vmalloc      13048  1 em28xx
videobuf2_memops       13170  1 videobuf2_vmalloc
videobuf2_core         39125  1 em28xx
videodev              107508  5 tuner,em28xx,tvp5150,v4l2_common,videobuf2_core
applesmc               18772  0
input_polldev          13648  1 applesmc
microcode              18830  0
snd_hda_codec_idt      44605  1
firewire_sbp2          18017  2
snd_hda_intel          42658  3
snd_hda_codec         164003  2 snd_hda_codec_idt,snd_hda_intel
lib80211_crypt_tkip    17387  0
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                89488  3 snd_hda_codec,snd_hda_intel,em28xx_alsa
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25094  1 snd_seq_midi
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
wl                   3999432  0
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              24447  2 snd_pcm,snd_seq
lib80211               14040  2 wl,lib80211_crypt_tkip
cfg80211              401436  1 wl
lpc_ich                16864  0
radeon               1307301  2
snd                    60790  19 snd_hwdep,snd_timer,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,em28xx_alsa,snd_seq_midi
video                  18777  0
apple_bl               13681  0
ttm                    71886  1 radeon
mac_hid                13037  0
drm_kms_helper         46867  1 radeon
soundcore              12600  1 snd
drm                   242354  4 ttm,drm_kms_helper,radeon
i2c_algo_bit           13197  1 radeon
lp                     13299  0
parport                40795  3 lp,ppdev,parport_pc
usb_storage            48294  0
firewire_ohci          35257  0
firewire_core          57656  2 firewire_ohci,firewire_sbp2
crc_itu_t              12627  1 firewire_core
sky2                   52910  0
             total       used       free     shared    buffers     cached
Mem:       3087448    1075784    2011664          0     121064     710008
-/+ buffers/cache:     244712    2842736
Swap:     31831036          0   31831036
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
Kernel modesetting video driver detected, not using quirks.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0
/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.

Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.

Sat Dec 21 19:59:30 PST 2013: performing suspend
```

```
sudo lspci -vnn | grep -A12 VGA

01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RV530/M56-P [Mobility Radeon X1600] [1002:71c5] (prog-if 00 [VGA controller])
    Subsystem: Apple Inc. MacBook Pro [106b:0080]
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at c0000000 (32-bit, prefetchable) [size=128M]
    I/O ports at 2000 [size=256]
    Memory at c8400000 (32-bit, non-prefetchable) [size=64K]
    Expansion ROM at c8420000 [disabled] [size=128K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Express Legacy Endpoint, MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Kernel driver in use: radeon

02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller [11ab:4362] (rev 22)



```

```
cat /proc/cmdline

BOOT_IMAGE=/boot/vmlinuz-3.11.0-14-generic root=UUID=02b34210-633b-4539-b7e9-ecc71b309beb ro quiet splash vt.handoff=7

```

---

### Post by ahentschel.public on 2013-12-27
Hi, 

I am having the same problem. I found several descriptions of the wake problem after a suspend to ram but mostly for laptops. However, my system is a standard desktop with all components about 2 years old. 

I suspect, that the system does not go to sleep properly for the following reason:

[LIST]
[*]during normal boot, a motherboard LED is illuminated _only before_ the BIOS boot messages are displayed 
[*]however, after waking the system from a suspend to ram, the motherboard LED _stays_ _illuminated _ 
[*]no BIOS messages are displayed and the keyboard is inactive 
[/LIST]
 
As for my graphics cards, it is an Nvidia GeForce GTX 560. 
```

01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF114 [GeForce GTX 560] [10de:1201] (rev a1) (prog-if 00 [VGA controller])
        Subsystem: Gigabyte Technology Co., Ltd Device [1458:3527]
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at f6000000 (32-bit, non-prefetchable) [size=32M]
        Memory at e0000000 (64-bit, prefetchable) [size=128M]
        Memory at ec000000 (64-bit, prefetchable) [size=64M]
        I/O ports at cf00 [size=128]
        [virtual] Expansion ROM at e8000000 [disabled] [size=512K]
        Capabilities: [60] Power Management version 3
        Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
        Capabilities: [78] Express Endpoint, MSI 00
        Capabilities: [b4] Vendor Specific Information: Len=14 <?>
        Capabilities: [100] Virtual Channel
```

My kernel is
```
BOOT_IMAGE=/boot/vmlinuz-3.11.0-14-generic root=UUID=4159fc77-99e3-4b54-bde0-31ac6663236d ro quiet splash
```

---

### Post by 0N3 on 2013-12-28
I had this issue with 13.10 after upgrading the kernel I am pretty sure because after a fresh install it was perfectly fine ...... I tried 14.04 same thing won't wake from suspend straight after clean install its just a black screen with some form of light in the background but doesn't load the login screen. 13.04 this isn't a problem I can't duplicate the problem using open source or proprietary drivers AMD drivers. The issue happens with all drivers in 13.10 and 14.04 except the driver installed during the OS installation. The only problem with that driver is the fan never once stops no matter how cold the laptop is hence poor battery life. I hope this will be fixed by the release of 14.04 or I am stuck using 13.04 with no security updates till the issue is fixed :(

Laptop is Toshiba Satellite L855
Core i7 Quad
8GB DDR3 Ram
1GB Radeon HD 7650
256GB SSD 1TB SATA III HDD

---

### Post by alexf2 on 2014-01-19
I had the same problem until I updated the NVIDIA Accelerated graphic drivers to version 319 using  'system settings -> hardware -> additional driver'.
Previously, suspend would successfully work but once asleep, the display would not come back while clearly the rest of the laptop would be up (fan and HDD spinning, speakers up, keyboard leds up).

Laptop is a DELL D630 and I have Ubuntu Server Edition 12.04 64 bit. 

HTH
Alex

---

### Post by sgage on 2014-01-19
> **alexf2 said:**
> I had the same problem until I updated the NVIDIA Accelerated graphic drivers to version 319 using  'system settings -> hardware -> additional driver'.
Previously, suspend would successfully work but once asleep, the display would not come back while clearly the rest of the laptop would be up (fan and HDD spinning, speakers up, keyboard leds up).

Laptop is a DELL D630 and I have Ubuntu Server Edition 12.04 64 bit. 

HTH
Alex

Same thing here. My system would never come all the way back from suspend with the nouveau drivers, but has always worked fine with the nvidia drivers. I have a GeForce 8500 GT card. Evidently, not all nvidia cards have a problem, but some do.

Oddly enough, I never have problems resuming from suspend using Fedora, even with the nouveau drivers, so who knows what's going on. I just install the nvidia drivers as a routine part of any Ubuntu installation...

---

### Post by chickenlips3822 on 2014-09-13
temp fix but i disabled all sleep related things in settings manager then i entered
> sudo -H gedit /etc/systemd/logind.conf

srcoll down to #HandleLidSwitch= and type ignore save and exit + reboot

also i changed my driver to nivida legacy driver 304.117 but i dont know if that did anything except for give it a noisey boot and a nivida logo

---

### Post by highspl_145 on 2015-09-05
Dell Latitude E6330 with the same problem.  I changed from the Nouveau drivers to the Nvidia ones and it's fine now.  I'm running Linux Mint 17.2 and went to "Driver Manager", under Preferences, and chose Nvidia.  No other changes made.

---

### Post by mark268 on 2016-02-23
Had the same issue with a dell Inspiron (2016) with an AMD Radeon Video Card.
Changed from open source driver to the proprietary one (Settings - Software & Updates - Additional Drivers).
Problem Solved.

---

### Post by electrototo on 2016-03-29
Hello! I might be a little late for this but currently I have a lenovo y50-70 laptop with a GeForce GTX 860M. At first, the suspend button did nothing, I managed to fix it with the help of forums, later I realized I couldn't wake up my machine... Tired of searching and without finding anything I decided to look at the additional drivers, it was selected by default X.Org X server, I changed it to NVIDIA binary driver version 352.63, rebooted the machine, and tried again to send to sleep my machine, it slept and resumed just as expected. Hope it helps someone... 

P.S: Sorry for my bad English :(

---

### Post by chuwi3434 on 2016-04-05
Confirming that this is still an issue, running 14.04.4 LTS on a Thinkpad X60. This laptop might be 10 years old, but not being able to put it to sleep as well as not being connected to networks after hibernation are the only real problems I've experienced with it so far. If anyone can guide me along resolving the wake from suspend issue, thank you very much.

---

### Post by Brody_Payne on 2016-05-27
turning off 'require password when waking from suspend' in settings fixed this issue for me.

---

### Post by him610 on 2016-05-27
Not quite a solution, but a workaround,

If you are using the system the power is ON, if you are not using the system then power is OFF.

---

### Post by JoeDaddy on 2016-11-14
This is what I discovered on two computers, one with Ubuntu 14.04 and another with 16.04.  If there is a drive installed that is not enabled in the CMOS settings OR if there is a drive or *device* missing from the unit and it is enabled in the CMOS then Ubuntu will not recover fully from suspend. I have no idea why this happens but both computers would not recover.  One had a SATA drive installed and not enabled in CMOS while the other had an optical device enabled that was not installed.  Fixing the CMOS settings in both instances fixed the problem.

---

### Post by JoeDaddy on 2016-11-14
This is what I discovered on two computers, one with Ubuntu 14.04 and  another with 16.04.  If there is a drive installed that is not enabled  in the CMOS settings OR if there is a drive or *device* missing  from the unit and it is enabled in the CMOS then Ubuntu will not recover  fully from suspend. I have no idea why this happens but both computers  would not recover.  One had a SATA drive installed and not enabled in  CMOS while the other had an optical device enabled that was not  installed.  Fixing the CMOS settings in both instances fixed the  problem.

---

### Post by joannacw on 2017-01-28
For those of us who are more ignorant, would you be willing to post more about how you find and fix CMOS settings? (I'm running Xubuntu 16.04.1 on a [COLOR=#000000]partition on my [/COLOR][COLOR=#000000][COLOR=#000000]M[/COLOR][/COLOR]*acBook Pro 1,2 with a 2.16 GHz Intel Core Duo processor and 2GB 667 MHz DDR2 SDRAM)*

---

### Post by kurt18947 on 2017-01-29
> **joannacw said:**
> For those of us who are more ignorant, would you be willing to post more about how you find and fix CMOS settings? (I'm running Xubuntu 16.04.1 on a [COLOR=#000000]partition on my [/COLOR][COLOR=#000000][COLOR=#000000]M[/COLOR][/COLOR]*acBook Pro 1,2 with a 2.16 GHz Intel Core Duo processor and 2GB 667 MHz DDR2 SDRAM)*

CMOS=BIOS in the PC world. I presume there's something similar in MAC world but I have 0 Mac experience.

---

### Post by chemgrl08 on 2017-05-14
Here is the solution that worked for me, but I'm not sure WHY it worked, so I will list each action here. Perhaps someone who is better acquainted with linux will be able to figure out why it worked and offer a more direct solution as a line of code or something. I did it through the GUI rather than the command prompt. Again, I'm not sure each step is necessary, but I'm not sure which piece worked, so I listed everything here.
I am running lubuntu 17.04 i386 (desktop, 32 bit, Zesty Zapus) on an old Acer netbook with an Intel(R) Atom(TM) CPU N270 @ 1.60GHz
Following the above thread, I first tried to update my drivers. Preferences > Additional drivers. The update showed one "proprietary driver" that was not in use,  so I highlighted it to use it, applied, exited and tried to close my laptop and reopen it. This alone did not work; the computer was running (fans, disc spinning, etc) but showed a black screen.
Left the above as it was, without returning it to the normal setting. Opened Preferences > Power manager. **Changed "when sleep button is pressed" and "When hibernation button is pressed" to "ask" instead of "Do Nothing."** Changed "When laptop lid is closed 'on battery' and 'plugged in'" both to "Switch off display." Still within power options, click the "systems" tab. Changed "System Sleep Mode" for both "on battery" and "plugged in" to "Suspend." Under the "Security" tab, "Automatically lock the session" "when the screensaver is activated." Check the box for "Lock screen when system is going to sleep."
After this, I closed my laptop lid and let it stop running (fans were off, disc was not spinning.) Opened it up, pressed the power button once, and the screen turned on and asked me to log in. I SUSPECT that the key here was "when sleep button is pressed" "ask what to do." 
Hope this helps.

---

### Post by ab772 on 2017-06-24
Hi,
   I know this is a rather late response but I only recently started using Ubuntu and eventually upgraded to 16.0.4.

Anyway this hibernate/suspend issue is a kernel bug and so your best bet would be to update your kernel to something past 4.8 but make sure it is not a test version that you are downloading. 

This will give you the various kernel versions to download from:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

And this details the installation process basically you need to download the 5 debian files and then issue sudo dpkg -i *.deb

[https://askubuntu.com/questions/119080/how-to-update-kernel-to-the-latest-mainline-version-without-any-distro-upgrade](https://askubuntu.com/questions/119080/how-to-update-kernel-to-the-latest-mainline-version-without-any-distro-upgrade)

Also if you had installed any custom scripts to fix this issue do remove those. And if you had patched your wifi then you would have to do it again on the new kernel.

---

### Post by oldos2er on 2017-06-25
Old thread closed. Please don't bump old threads.

Anyone still experiencing problems should start a new thread. Thanks.

---

