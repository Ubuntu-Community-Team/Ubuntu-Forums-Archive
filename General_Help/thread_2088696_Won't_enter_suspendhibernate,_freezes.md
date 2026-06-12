---
title: "Won't enter suspend/hibernate, freezes"
date: 2012-11-27
forum: General Help
---

### Post by NertSkull on 2012-11-27
So, I know there are a ton of threads on suspend/hibernate issues, and I swear I've tried them all.  Even to the point I've broken things and had to re-install twice now. 

The problem:  My computer won't suspend or hibernate at all.  Its NOT a "resume"/"wake-from" suspend issue.  It doesn't even get there.  When I try to suspend/hibernate it blacks the monitor but both the monitor and the computer stay on.  It never actually gets to suspend/hibernate.  Then, I can't do anything to get out of that.  So I have to force power-off the computer and restart.

I'm running Kubuntu 12.04 64-bit.  I know it can work, because my home computer running the same will suspend/hibernate fine.  But its different hardware.

Hardware is a Intel i5 with the Asus P8Z68-V motherboard and the GeForce GTX 550 Ti.  I'm using the nvidia drivers with that.  (I'm also using nvidia drivers at home, with a different card, but it works.  Also, my home computer is a AMD chip and board).

So, here's where it gets a little complicated (but I know you people can help with complicate).  I actually have full disk encryption set up.  Again, I have full disk encryption on my home computer, so I know this can work, I just can't get it working here.  So I have the system encrypted EXCEPT for the /boot partition and my swap space.  I leave my swap un-encrypted (we can talk security issues another time) to make hibernate work at home.  Same here, except it doesn't work.

I've tried many different things.  I've tried the nvida suggestions from [here]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia?action=show&redirect=NvidiaLaptopBinaryDriverSuspend#Suspend.2BAC8-Hibernation"). I've tried messing with mem > /sys/power/state type of things from [here]("http://superuser.com/questions/391053/difference-between-suspend-to-mem-and-pm-suspend") and [here]("http://ubuntuforums.org/showthread.php?t=1428249"). I've tried messing with disable USB devices as suggested [here]("http://ubuntuforums.org/showthread.php?t=1969615"). I've tried all the possible quirks options from pm-suspend.  I've tried doing it before I installed virtualbox (read that somewhere).  I've tried it with the proprietary nvida driver uninstalled, and still no go.  I've tried the uswusp stuff, and that ends up making my computer not happy, it gives me errors when I update-initramfs.

Anyway, I've tried a bunch more than that, but I should end this wall of text before people refuse to read.  

This is my most recent pm-suspend.log doing a hibernate

```
Initial commandline parameters: 
Mon Nov 26 14:27:46 EST 2012: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux IDPNux 3.2.0-32-generic #51-Ubuntu SMP Wed Sep 26 21:33:09 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
ip6t_LOG               16974  0 
xt_hl                  12521  0 
ip6t_rt                12558  0 
nf_conntrack_ipv6      13906  0 
nf_defrag_ipv6         13368  1 nf_conntrack_ipv6
ipt_REJECT             12576  0 
ipt_LOG                12919  0 
xt_limit               12711  0 
xt_tcpudp              12603  0 
xt_addrtype            12713  0 
xt_state               12578  0 
nf_conntrack_netbios_ns    12665  0 
nf_conntrack_broadcast    12589  1 nf_conntrack_netbios_ns
nf_nat_ftp             12704  0 
nf_nat                 25891  1 nf_nat_ftp
nf_conntrack_ipv4      19716  2 nf_nat
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
nf_conntrack_ftp       13452  1 nf_nat_ftp
nf_conntrack           81926  8 nf_conntrack_ipv6,xt_state,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter         12810  1 
ip_tables              27473  1 iptable_filter
ip6table_filter        12815  1 
ip6_tables             27864  3 ip6t_LOG,ip6t_rt,ip6table_filter
x_tables               29846  13 ip6t_LOG,xt_hl,ip6t_rt,ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,xt_addrtype,xt_state,iptable_filter,ip_tables,ip6table_filter,ip6_tables
nls_iso8859_1          12713  0 
nls_cp437              16991  0 
vfat                   17585  0 
fat                    61512  1 vfat
usb_storage            49198  0 
uvcvideo               72627  0 
snd_usb_audio         122982  1 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
snd_usbmidi_lib        25395  1 snd_usb_audio
xts                    12756  4 
gf128mul               14951  1 xts
snd_hda_codec_hdmi     32474  5 
snd_hda_codec_realtek   224173  1 
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             25670  0 
vboxnetflt             23441  0 
vboxdrv               320210  3 vboxpci,vboxnetadp,vboxnetflt
bnep                   18281  2 
parport_pc             32866  0 
ppdev                  17113  0 
rfcomm                 47604  0 
bluetooth             180104  10 bnep,rfcomm
ext2                   73795  1 
nvidia              11257276  66 
joydev                 17693  0 
eeepc_wmi              13109  0 
asus_wmi               24456  1 eeepc_wmi
sparse_keymap          13890  1 asus_wmi
mxm_wmi                12979  0 
snd_hda_intel          33773  7 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  2 snd_usb_audio,snd_hda_codec
snd_pcm                97188  5 snd_usb_audio,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
psmouse                97443  0 
serio_raw              13211  0 
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78855  27 snd_usb_audio,snd_usbmidi_lib,snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mei                    41616  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mac_hid                13253  0 
wmi                    19256  2 asus_wmi,mxm_wmi
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
dm_crypt               23125  2 
vesafb                 13844  1 
i915                  473298  0 
drm_kms_helper         46978  1 i915
drm                   241921  2 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
usbhid                 47199  0 
hid                    99559  1 usbhid
video                  19596  1 i915
e1000e                156715  0 
             total       used       free     shared    buffers     cached
Mem:      16341412   12186860    4154552          0    4145980    4379652
-/+ buffers/cache:    3661228   12680184
Swap:     36585468        244   36585224

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

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

/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:

/etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: success.
Mon Nov 26 14:27:47 EST 2012: performing hibernate
```

And here is one from suspend

```
Initial commandline parameters: 
Wed Nov  7 10:41:16 EST 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux IDPNux 3.2.0-32-generic #51-Ubuntu SMP Wed Sep 26 21:33:09 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
snd_hda_codec_hdmi     32474  5 
snd_hda_codec_realtek   224173  1 
bnep                   18281  2 
rfcomm                 47604  0 
bluetooth             180104  10 bnep,rfcomm
parport_pc             32866  0 
ppdev                  17113  0 
nvidia              11257276  54 
ext2                   73795  1 
mxm_wmi                12979  0 
eeepc_wmi              13109  0 
asus_wmi               24456  1 eeepc_wmi
sparse_keymap          13890  1 asus_wmi
snd_hda_intel          33773  7 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
psmouse                97443  0 
serio_raw              13211  0 
joydev                 17693  0 
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
wmi                    19256  2 mxm_wmi,asus_wmi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78855  23 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mei                    41616  0 
mac_hid                13253  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
dm_crypt               23125  1 
vesafb                 13844  1 
usbhid                 47199  0 
hid                    99559  1 usbhid
i915                  473298  0 
e1000e                156715  0 
drm_kms_helper         46978  1 i915
drm                   241921  2 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19596  1 i915
             total       used       free     shared    buffers     cached
Mem:      16341412    1592672   14748740          0      33584     563528
-/+ buffers/cache:     995560   15345852
Swap:     36585468          0   36585468

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /etc/pm/sleep.d/20_sleep suspend suspend:
Unbinding 0000:00:1a.0
Unbinding 0000:00:1d.0

/etc/pm/sleep.d/20_sleep suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
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
Wed Nov  7 10:41:17 EST 2012: performing suspend
```

I would REALLY like to figure this out, even if it takes a few days.  Does anyone have any idea of what I may be missing or what I can do next to figure this out?  I mean I know this configuration can work, because it works at home.  So I have to assume its some sort of different hardware issue here.

HELP!

:)

---

### Post by Toz on 2012-11-27
I wonder if it has something to do with [this]("http://www.phoronix.com/scan.php?page=news_item&px=MTA0NDE"):

> There's also a fix that will allow some new motherboards (select P67/H67/Z68 motherboards) that can suspend but are not able to wake-up on Linux 3.2 and earlier, to now wake-up properly. 

---

### Post by NertSkull on 2012-11-27
I guess it may have something to do.  I know I have the latest kernel from the repositories installed, but it still doesn't work.

One other thing I should mention, is that in order to boot, I have to have nomodeset selected (even though I'm using the nvidia drivers) in the grub boot.  

I don't know if that plays a role or not.

---

### Post by Toz on 2012-11-27
According to your logs, you are running kernel version:
> Linux IDPNux **3.2.0-32**-generic #51-Ubuntu SMP Wed Sep 26 21:33:09 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

The article notes that the fix applies to kernel version 3.3.

---

### Post by NertSkull on 2012-11-27
Sorry, I missed that.  I was running 3.2.  I have updated to 3.3.6 now, but still no suspend. 

Here is the most recent log after suspend failure with the 3.3.6

```
Initial commandline parameters: 
Tue Nov 27 13:42:02 EST 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux IDPNux 3.3.6-030306-generic #201205121335 SMP Sat May 12 17:36:12 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
xts                    12880  4 
gf128mul               14951  1 xts
pci_stub               12622  0 
vboxpci                23200  14533189972450961432 [permanent]
vboxnetadp             25670  697528381364887362 [permanent]
vboxnetflt             23441  18444713374491574863 [permanent]
vboxdrv               320232  7661533975373763634 vboxpci,vboxnetadp,vboxnetflt,[permanent]
snd_hda_codec_hdmi     32111  5 
snd_hda_codec_realtek   128189  1 
nvidia              11257720  1110884700136963 [permanent]
rfcomm                 47013  0 
bnep                   18190  2 
bluetooth             188048  10 rfcomm,bnep
parport_pc             32734  0 
ppdev                  17180  0 
snd_hda_intel          33332  5 
snd_hda_codec         122839  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_seq_midi           13324  0 
snd_hwdep              13652  1 snd_hda_codec
snd_pcm                96984  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_rawmidi            30655  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
ext2                   73217  1 
snd_seq                61538  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29708  2 snd_pcm,snd_seq
snd_seq_device         14490  3 snd_seq_midi,snd_rawmidi,snd_seq
eeepc_wmi              12826  0 
asus_wmi               24281  1 eeepc_wmi
psmouse                87507  0 
sparse_keymap          13890  1 asus_wmi
snd                    78595  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mxm_wmi                12979  0 
wmi                    19141  2 asus_wmi,mxm_wmi
soundcore              14996  1 snd
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
lp                     17789  0 
mei                    40904  0 
joydev                 17597  0 
serio_raw              13211  0 
mac_hid                13205  0 
parport                46360  3 parport_pc,ppdev,lp
dm_crypt               22908  2 
usbhid                 46836  0 
hid                    99668  1 usbhid
i915                  475716  0 
drm_kms_helper         42475  1 i915
e1000e                154395  0 
drm                   253084  2 i915,drm_kms_helper
i2c_algo_bit           13368  1 i915
video                  19280  1 i915
             total       used       free     shared    buffers     cached
Mem:      16341440    1307100   15034340          0      39892     595384
-/+ buffers/cache:     671824   15669616
Swap:     36585468          0   36585468

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /etc/pm/sleep.d/20_custom-ehci_hcd suspend suspend:

/etc/pm/sleep.d/20_custom-ehci_hcd suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
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
Tue Nov 27 13:42:03 EST 2012: performing suspend

```

---

### Post by Toz on 2012-11-27
I found this thread: [http://www.tomshardware.com/forum/293182-30-asus-p8z68-wake-sleep-graphics-card-installed]("http://www.tomshardware.com/forum/293182-30-asus-p8z68-wake-sleep-graphics-card-installed"). One of the posts suggests:
> Try the following:

ASUS EFI BIOS Utility - Advanced Mode

AI Tweaker tab page

Change the Internal PLL Overvoltage option to Disabled to get Resume from S3 working 

Anything interesting coming back with:
```
cat /var/log/syslog | grep PM:
```

Barring that, you may want to try this procedure ([https://wiki.ubuntu.com/DebuggingKernelSuspend]("https://wiki.ubuntu.com/DebuggingKernelSuspend")) to see if you can identify the offending module.

---

### Post by NertSkull on 2012-11-28
So I changed the BIOS settings, and that didn't help.

I tried to do the debugging stuff from that page, but I doesn't really tell me anything because its all about resuming from suspend.  My computer never suspends.  It doesn't ever turn off.  So when I tried the debugging stuff it doesn't give a "hash matches" line in dmesg.

I do, however, get some info here.  This is the output of the syslog

```
Nov 28 09:56:37 IDPNux kernel: [    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
Nov 28 09:56:37 IDPNux kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Nov 28 09:56:37 IDPNux kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Nov 28 09:56:37 IDPNux kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Nov 28 09:56:37 IDPNux kernel: [    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000020200000
Nov 28 09:56:37 IDPNux kernel: [    0.000000] PM: Registered nosave memory: 0000000040000000 - 0000000040200000
Nov 28 09:56:37 IDPNux kernel: [    0.000000] PM: Registered nosave memory: 00000000ba829000 - 00000000ba87e000
Nov 28 09:56:37 IDPNux kernel: [    0.000000] PM: Registered nosave memory: 00000000ba87e000 - 00000000bad81000
Nov 28 09:56:37 IDPNux kernel: [    0.000000] PM: Registered nosave memory: 00000000bad81000 - 00000000bad84000
Nov 28 09:56:37 IDPNux kernel: [    0.000000] PM: Registered nosave memory: 00000000bad84000 - 00000000bada4000
Nov 28 09:56:37 IDPNux kernel: [    0.000000] PM: Registered nosave memory: 00000000bada4000 - 00000000badb5000
Nov 28 09:56:37 IDPNux kernel: [    0.000000] PM: Registered nosave memory: 00000000badb5000 - 00000000badcc000
Nov 28 09:56:37 IDPNux kernel: [    0.000000] PM: Registered nosave memory: 00000000badce000 - 00000000badd6000
Nov 28 09:56:37 IDPNux kernel: [    0.000000] PM: Registered nosave memory: 00000000badd6000 - 00000000bade1000
Nov 28 09:56:37 IDPNux kernel: [    0.000000] PM: Registered nosave memory: 00000000bade1000 - 00000000bae3d000
Nov 28 09:56:37 IDPNux kernel: [    0.000000] PM: Registered nosave memory: 00000000bae3d000 - 00000000bae80000
Nov 28 09:56:37 IDPNux kernel: [    0.000000] PM: Registered nosave memory: 00000000bb000000 - 00000000bb800000
Nov 28 09:56:37 IDPNux kernel: [    0.000000] PM: Registered nosave memory: 00000000bb800000 - 00000000bfa00000
Nov 28 09:56:37 IDPNux kernel: [    0.000000] PM: Registered nosave memory: 00000000bfa00000 - 00000000fed1c000
Nov 28 09:56:37 IDPNux kernel: [    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
Nov 28 09:56:37 IDPNux kernel: [    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000ff000000
Nov 28 09:56:37 IDPNux kernel: [    0.000000] PM: Registered nosave memory: 00000000ff000000 - 0000000100000000
Nov 28 09:56:37 IDPNux kernel: [    0.572231] PM: Registering ACPI NVS region at ba829000 (348160 bytes)
Nov 28 09:56:37 IDPNux kernel: [    0.572236] PM: Registering ACPI NVS region at bad81000 (12288 bytes)
Nov 28 09:56:37 IDPNux kernel: [    0.572237] PM: Registering ACPI NVS region at bada4000 (69632 bytes)
Nov 28 09:56:37 IDPNux kernel: [    0.572239] PM: Registering ACPI NVS region at badd6000 (45056 bytes)
Nov 28 09:56:37 IDPNux kernel: [    0.572241] PM: Registering ACPI NVS region at bae3d000 (274432 bytes)
Nov 28 09:56:37 IDPNux kernel: [    1.191138] PM: Hibernation image not present or could not be loaded.

```

So apparently it claims there is no hibernation image.  I've looked stuff up on that now, and everything talks about resuming.  But I can't even get to the point to try and resume, because it never sleeps in the first place.  

Thanks for the continued help

---

### Post by NertSkull on 2012-11-28
So, I checked on my home computer to see if there is a difference, and there is not.

It also has the same Hibernation image not present or could not be loaded.

So, I don't think that is the problem, since it works at home.

---

### Post by NertSkull on 2012-11-28
I found you can turn on debugging for pm-suspend by logging in as root, and running the following
```
PM_DEBUG=true pm-suspend
```

So I thought I would include the more verbose log file in case that helps

```
+ log Initial commandline parameters: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Initial commandline parameters:  = -n ]
+ printf %s\n Initial commandline parameters: 
Initial commandline parameters: 
+ load_hook_blacklist
+ [  ]
+ return
+ load_hook_parameters
+ [  ]
+ [  ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ date
+ log Wed Nov 28 10:29:23 EST 2012: Running hooks for suspend.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Wed Nov 28 10:29:23 EST 2012: Running hooks for suspend. = -n ]
+ printf %s\n Wed Nov 28 10:29:23 EST 2012: Running hooks for suspend.
Wed Nov 28 10:29:23 EST 2012: Running hooks for suspend.
+ run_hooks sleep suspend suspend
+ _run_hooks sleep suspend suspend
+ local syshooks=/etc/pm/sleep.d
+ local phooks=/usr/lib/pm-utils/sleep.d
+ command_exists before_hooks
+ type before_hooks
+ return 0
+ before_hooks
+ [ -z  ]
+ return 0
+ local sort=sort
+ local base
+ local hook
+ local oifs= 	

+ local nifs=

+ IFS=

+ [  = reverse ]
+ IFS= 	

+ sort
+ uniq
+ [ -O /etc/pm/sleep.d/10_grub-common ]
+ echo 10_grub-common
+ [ -O /etc/pm/sleep.d/10_unattended-upgrades-hibernate ]
+ echo 10_unattended-upgrades-hibernate
+ [ -O /etc/pm/sleep.d/novatel_3g_suspend ]
+ echo novatel_3g_suspend
+ [ -O /usr/lib/pm-utils/sleep.d/000kernel-change ]
+ echo 000kernel-change
+ [ -O /usr/lib/pm-utils/sleep.d/00logging ]
+ echo 00logging
+ [ -O /usr/lib/pm-utils/sleep.d/00powersave ]
+ echo 00powersave
+ [ -O /usr/lib/pm-utils/sleep.d/01PulseAudio ]
+ echo 01PulseAudio
+ [ -O /usr/lib/pm-utils/sleep.d/55NetworkManager ]
+ echo 55NetworkManager
+ [ -O /usr/lib/pm-utils/sleep.d/60_wpa_supplicant ]
+ echo 60_wpa_supplicant
+ [ -O /usr/lib/pm-utils/sleep.d/75modules ]
+ echo 75modules
+ [ -O /usr/lib/pm-utils/sleep.d/90clock ]
+ echo 90clock
+ [ -O /usr/lib/pm-utils/sleep.d/94cpufreq ]
+ echo 94cpufreq
+ [ -O /usr/lib/pm-utils/sleep.d/95anacron ]
+ echo 95anacron
+ [ -O /usr/lib/pm-utils/sleep.d/95hdparm-apm ]
+ echo 95hdparm-apm
+ [ -O /usr/lib/pm-utils/sleep.d/95led ]
+ echo 95led
+ [ -O /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler ]
+ echo 98video-quirk-db-handler
+ [ -O /usr/lib/pm-utils/sleep.d/99video ]
+ echo 99video
+ IFS= 	

+ [  -a  = reverse -a  ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/000kernel-change ]
+ [ -f /usr/lib/pm-utils/sleep.d/000kernel-change ]
+ hook=/usr/lib/pm-utils/sleep.d/000kernel-change
+ run_hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/000kernel-change
+ local hook=000kernel-change
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:000kernel-change ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:0kernel-change ]
+ [ -x /usr/lib/pm-utils/sleep.d/000kernel-change ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: 
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=000kernel-change
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 000kernel-change ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/00logging ]
+ [ -f /usr/lib/pm-utils/sleep.d/00logging ]
+ hook=/usr/lib/pm-utils/sleep.d/00logging
+ run_hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/00logging
+ local hook=00logging
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:00logging ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:logging ]
+ [ -x /usr/lib/pm-utils/sleep.d/00logging ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/00logging suspend suspend
+ [ -n /var/log/pm-suspend.log ]
+ /bin/uname -a
Linux IDPNux 3.2.0-33-generic #52-Ubuntu SMP Thu Oct 18 16:29:15 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
+ lsmod
Module                  Size  Used by
xts                    12756  4 
gf128mul               14951  1 xts
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             25670  0 
vboxnetflt             23441  0 
vboxdrv               320210  3 vboxpci,vboxnetadp,vboxnetflt
snd_hda_codec_hdmi     32474  5 
snd_hda_codec_realtek   224173  1 
parport_pc             32866  0 
ppdev                  17113  0 
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
ext2                   73795  1 
ip6t_LOG               16974  4 
xt_hl                  12521  6 
ip6t_rt                12558  3 
nf_conntrack_ipv6      13906  7 
nf_defrag_ipv6         13368  1 nf_conntrack_ipv6
ipt_REJECT             12576  1 
ipt_LOG                12919  5 
xt_limit               12711  12 
xt_tcpudp              12603  18 
xt_addrtype            12713  4 
xt_state               12578  14 
ip6table_filter        12815  1 
ip6_tables             27864  3 ip6t_LOG,ip6t_rt,ip6table_filter
nf_conntrack_netbios_ns    12665  0 
nf_conntrack_broadcast    12589  1 nf_conntrack_netbios_ns
nf_nat_ftp             12704  0 
nf_nat                 25891  1 nf_nat_ftp
nf_conntrack_ipv4      19716  9 nf_nat
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
nf_conntrack_ftp       13452  1 nf_nat_ftp
uvcvideo               72627  0 
nf_conntrack           81926  8 nf_conntrack_ipv6,xt_state,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter         12810  1 
ip_tables              27473  1 iptable_filter
snd_usb_audio         122982  1 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
snd_usbmidi_lib        25395  1 snd_usb_audio
joydev                 17693  0 
nvidia              11257276  54 
x_tables               29846  13 ip6t_LOG,xt_hl,ip6t_rt,ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,xt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
snd_hda_intel          33773  5 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  2 snd_usb_audio,snd_hda_codec
snd_pcm                97188  4 snd_hda_codec_hdmi,snd_usb_audio,snd_hda_intel,snd_hda_codec
eeepc_wmi              13109  0 
psmouse                97443  0 
asus_wmi               24456  1 eeepc_wmi
sparse_keymap          13890  1 asus_wmi
snd_seq_midi           13324  0 
snd_rawmidi            30748  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
mxm_wmi                12979  0 
serio_raw              13211  0 
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
mac_hid                13253  0 
snd                    78855  24 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_usb_audio,snd_usbmidi_lib,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15091  1 snd
wmi                    19256  2 asus_wmi,mxm_wmi
mei                    41616  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
dm_crypt               23125  2 
vesafb                 13844  1 
usbhid                 47199  0 
hid                    99592  1 usbhid
i915                  473298  0 
e1000e                156715  0 
drm_kms_helper         46978  1 i915
drm                   241921  2 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19596  1 i915
+ free
             total       used       free     shared    buffers     cached
Mem:      16341412    1614948   14726464          0      43512     488904
-/+ buffers/cache:    1082532   15258880
Swap:     36585468          0   36585468
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/00logging suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/00logging suspend suspend: 
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=00logging
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 00logging ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/00powersave ]
+ [ -f /usr/lib/pm-utils/sleep.d/00powersave ]
+ hook=/usr/lib/pm-utils/sleep.d/00powersave
+ run_hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/00powersave
+ local hook=00powersave
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:00powersave ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:powersave ]
+ [ -x /usr/lib/pm-utils/sleep.d/00powersave ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/00powersave suspend suspend
+ command_exists pm-powersave
+ type pm-powersave
+ return 0
+ pm-powersave false
+ set -a
+ PM_UTILS_LIBDIR=/usr/lib/pm-utils
+ PM_UTILS_ETCDIR=/etc/pm
+ PM_UTILS_RUNDIR=/var/run/pm-utils
+ PATH=/sbin:/usr/sbin:/bin:/usr/bin:/usr/lib/pm-utils/bin
+ PM_LOGFILE=/var/log/pm-powersave.log
+ TEMPORARY_CPUFREQ_GOVERNOR=performance
+ LOCKDIR=/var/run/pm-utils/locks
+ STORAGEDIR=/var/run/pm-utils/pm-powersave/storage
+ NA=254
+ NX=253
+ DX=252
+ PM_FUNCTIONS=/usr/lib/pm-utils/functions
+ PM_QUIRKDB=/usr/lib/pm-utils/video-quirks
+ PM_LKW_QUIRKS=/var/cache/pm-utils/last_known_working.quirkdb
+ LC_COLLATE=C
+ HIBERNATE_MODE=
+ HIBERNATE_RESUME_POST_VIDEO=no
+ SLEEP_MODULE=auto
+ SUSPEND_MODULES=
+ HOOK_BLACKLIST=
+ ADD_PARAMETERS=
+ DROP_PARAMETERS=
+ PARAMETERS=/var/run/pm-utils/pm-powersave/storage/parameters
+ INHIBIT=/var/run/pm-utils/pm-powersave/storage/inhibit
+ PM_CMDLINE=false
+ BEFORE_HOOKS=
+ MODULE_HELP=
+ SUSPEND_MODULE=
+ HIBERNATE_MODULE=
+ SUSPEND_HYBRID_MODULE=
+ PM_HIBERNATE_DELAY=900
+ PM_RTC=/sys/class/rtc/rtc0
+ [ -f /usr/lib/pm-utils/defaults ]
+ . /usr/lib/pm-utils/defaults
+ [ -f /usr/lib/pm-utils/pm-powersave.defaults ]
+ set +a
+ [ -f /etc/pm/config.d/*[!~] ]
+ continue
+ [ -f /etc/pm/pm-powersave.config.d/*[!~] ]
+ continue
+ . /usr/lib/pm-utils/functions
+ is_set true
+ return 0
+ set -x
+ profiling
+ [  = true ]
+ profiling
+ [  = true ]
+ profiling
+ [  = true ]
+ [ auto = auto ]
+ SLEEP_MODULE=tuxonice uswsusp
+ mod=/usr/lib/pm-utils/module.d/tuxonice
+ [ -f /usr/lib/pm-utils/module.d/tuxonice ]
+ . /usr/lib/pm-utils/module.d/tuxonice
+ export TUXONICE_LOC
+ [ -d /sys/power/tuxonice ]
+ [ -d /sys/power/suspend2 ]
+ [ -n  ]
+ [ -z  -a -n  ]
+ [ -z  -a -n  ]
+ mod=/usr/lib/pm-utils/module.d/uswsusp
+ [ -f /usr/lib/pm-utils/module.d/uswsusp ]
+ . /usr/lib/pm-utils/module.d/uswsusp
+ [ -z  ]
+ command_exists s2ram
+ type s2ram
+ return 127
+ [ -z  ]
+ [ -f /sys/power/disk ]
+ grep -q disk /sys/power/state
+ [ -c /dev/snapshot ]
+ command_exists s2disk
+ type s2disk
+ return 127
+ [ -z  ]
+ grep -q mem /sys/power/state
+ command_exists s2both
+ type s2both
+ return 127
+ [ -z  ]
+ grep -q mem /sys/power/state
+ SUSPEND_MODULE=kernel
+ [ -z  ]
+ [ -f /sys/power/disk ]
+ grep -q disk /sys/power/state
+ HIBERNATE_MODULE=kernel
+ [ -z  -a -w /sys/class/rtc/rtc0/wakealarm ]
+ check_suspend
+ [ -n kernel ]
+ check_hibernate
+ [ -n kernel ]
+ is_set no
+ return 1
+ SUSPEND_HYBRID_MODULE=kernel
+ lock_and_load
+ try_lock pm-powersave.lock
+ local lock=/var/run/pm-utils/locks/pm-powersave.lock
+ mkdir -p /var/run/pm-utils/locks
+ touch /var/run/pm-utils/locks/pm-powersave.lock
+ exec
+ flock -x -n 3
+ return 0
+ trap remove_powersave_lock 0
+ mkdir -p /var/run/pm-utils/pm-powersave/storage
+ rm -f /var/run/pm-utils/pm-powersave/storage/inhibit
+ load_hook_blacklist
+ [  ]
+ return
+ init_logfile /var/log/pm-powersave.log
+ [ -z /var/log/pm-powersave.log ]
+ [ -h /var/log/pm-powersave.log ]
+ [ -f /var/log/pm-powersave.log -a ! -O /var/log/pm-powersave.log ]
+ export LOGGING=true
+ exec
+ exit 0
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/00powersave suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/00powersave suspend suspend: 
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=00powersave
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 00powersave ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/01PulseAudio ]
+ [ -f /usr/lib/pm-utils/sleep.d/01PulseAudio ]
+ hook=/usr/lib/pm-utils/sleep.d/01PulseAudio
+ run_hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/01PulseAudio
+ local hook=01PulseAudio
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:01PulseAudio ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:PulseAudio ]
+ [ -x /usr/lib/pm-utils/sleep.d/01PulseAudio ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend
+ suspend_pulse
+ get_pulse_users
+ test_pulse_system
+ getent passwd pulse
+ awk -F: {print $3}
+ PULSE_SYSTEM_USER=108
+ [ -z 108 ]
+ ps -C pulseaudio -o uid=
+ tr -d  
+ sed s/108//
+ getent passwd 1000
+ cut -f1 -d:
+ THIS_USER=dan
+ save_pulse_state sink dan
+ su dan -c -- pacmd list-sinks+ 
sed+  -n s/^[[:space:]*]*//; /\(index\|mute\)/p
index=
+ read field value
+ [ index = index ]
+ index=0
+ read field value
+ [ muted = index ]
+ savestate pulse:dan:sink0 no
+ [ -n no ]
+ echo no
+ read field value
+ [ index = index ]
+ index=1
+ read field value
+ [ muted = index ]
+ savestate pulse:dan:sink1 no
+ [ -n no ]
+ echo no
+ read field value
+ save_pulse_state source dan
+ + index=
+ readsed field -n value
 s/^[[:space:]*]*//; /\(index\|mute\)/p
+ su dan -c -- pacmd list-sources
+ [ index = index ]
+ index=0
+ read field value
+ [ muted = index ]
+ savestate pulse:dan:source0 yes
+ [ -n yes ]
+ echo yes
+ read field value
+ [ index = index ]
+ index=1
+ read field value
+ [ muted = index ]
+ savestate pulse:dan:source1 no
+ [ -n no ]
+ echo no
+ read field value
+ [ index = index ]
+ index=2
+ read field value
+ [ muted = index ]
+ savestate pulse:dan:source2 yes
+ [ -n yes ]
+ echo yes
+ read field value
+ [ index = index ]
+ index=3
+ read field value
+ [ muted = index ]
+ savestate pulse:dan:source3 no
+ [ -n no ]
+ echo no
+ read field value
+ su dan -c -- pacmd suspend true
+ get_pulse_users
+ test_pulse_system
+ getent passwd pulse
+ awk -F: {print $3}
+ PULSE_SYSTEM_USER=108
+ [ -z 108 ]
+ ps -C pulseaudio -o uid=
+ tr -d  
+ sed s/108//
+ getent passwd 1000
+ cut -f1 -d:
+ THIS_USER=dan
+ su dan -c -- ck-list-sessions | grep "active = TRUE"
+ mute_pulse sink dan
+ su dan -c -- pacmd list-sinks
+ index=
+ read field value
+ sed -n s/^[[:space:]*]*//; /\(index\|mute\)/p
+ [ index = index ]
+ index=0
+ su dan -c -- pacmd                         set-sink-mute 0 yes
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> + read field value
+ [ muted = index ]
+ read field value
+ [ index = index ]
+ index=1
+ su dan -c -- pacmd                         set-sink-mute 1 yes
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> + read field value
+ [ muted = index ]
+ read field value
+ mute_pulse source dan
+ su dan -c -- pacmd list-sources
+ sed -n s/^[[:space:]*]*//; /\(index\|mute\)/p
+ index=
+ read field value
+ [ index = index ]
+ index=0
+ su dan -c -- pacmd                         set-source-mute 0 yes
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> + read field value
+ [ muted = index ]
+ read field value
+ [ index = index ]
+ index=1
+ su dan -c -- pacmd                         set-source-mute 1 yes
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> + read field value
+ [ muted = index ]
+ read field value
+ [ index = index ]
+ index=2
+ su dan -c -- pacmd                         set-source-mute 2 yes
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> + read field value
+ [ muted = index ]
+ read field value
+ [ index = index ]
+ index=3
+ su dan -c -- pacmd                         set-source-mute 3 yes
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> + read field value
+ [ muted = index ]
+ read field value
+ break
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=01PulseAudio
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 01PulseAudio ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/10_grub-common ]
+ hook=/etc/pm/sleep.d/10_grub-common
+ run_hook /etc/pm/sleep.d/10_grub-common suspend suspend
+ _run_hook /etc/pm/sleep.d/10_grub-common suspend suspend
+ log Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /etc/pm/sleep.d/10_grub-common suspend suspend: = -n ]
+ printf %s\n Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
+ hook_ok /etc/pm/sleep.d/10_grub-common
+ local hook=10_grub-common
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:10_grub-common ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:_grub-common ]
+ [ -x /etc/pm/sleep.d/10_grub-common ]
+ return 0
+ /etc/pm/sleep.d/10_grub-common suspend suspend
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /etc/pm/sleep.d/10_grub-common suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /etc/pm/sleep.d/10_grub-common suspend suspend: 
/etc/pm/sleep.d/10_grub-common suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=10_grub-common
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 10_grub-common ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/10_unattended-upgrades-hibernate ]
+ hook=/etc/pm/sleep.d/10_unattended-upgrades-hibernate
+ run_hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend
+ _run_hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend
+ log Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: = -n ]
+ printf %s\n Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
+ hook_ok /etc/pm/sleep.d/10_unattended-upgrades-hibernate
+ local hook=10_unattended-upgrades-hibernate
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:10_unattended-upgrades-hibernate ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:_unattended-upgrades-hibernate ]
+ [ -x /etc/pm/sleep.d/10_unattended-upgrades-hibernate ]
+ return 0
+ /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: 
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=10_unattended-upgrades-hibernate
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 10_unattended-upgrades-hibernate ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/55NetworkManager ]
+ [ -f /usr/lib/pm-utils/sleep.d/55NetworkManager ]
+ hook=/usr/lib/pm-utils/sleep.d/55NetworkManager
+ run_hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/55NetworkManager
+ local hook=55NetworkManager
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:55NetworkManager ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:NetworkManager ]
+ [ -x /usr/lib/pm-utils/sleep.d/55NetworkManager ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend
+ suspend_nm
+ printf Having NetworkManager put all interaces to sleep...
Having NetworkManager put all interaces to sleep...+ dbus_send --print-reply --system --dest=org.freedesktop.NetworkManager /org/freedesktop/NetworkManager org.freedesktop.NetworkManager.sleep
+ command dbus-send --print-reply --system --dest=org.freedesktop.NetworkManager /org/freedesktop/NetworkManager org.freedesktop.NetworkManager.sleep
+ return 254
+ echo Failed.
Failed.
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: 
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=55NetworkManager
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 55NetworkManager ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/60_wpa_supplicant ]
+ [ -f /usr/lib/pm-utils/sleep.d/60_wpa_supplicant ]
+ hook=/usr/lib/pm-utils/sleep.d/60_wpa_supplicant
+ run_hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/60_wpa_supplicant
+ local hook=60_wpa_supplicant
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:60_wpa_supplicant ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:_wpa_supplicant ]
+ [ -x /usr/lib/pm-utils/sleep.d/60_wpa_supplicant ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: 
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=60_wpa_supplicant
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 60_wpa_supplicant ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/75modules ]
+ [ -f /usr/lib/pm-utils/sleep.d/75modules ]
+ hook=/usr/lib/pm-utils/sleep.d/75modules
+ run_hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/75modules
+ local hook=75modules
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:75modules ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:modules ]
+ [ -x /usr/lib/pm-utils/sleep.d/75modules ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/75modules suspend suspend
+ suspend_modules
+ [ -z  ]
+ return 254
+ local status=254
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/75modules suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/75modules suspend suspend: 
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: + hook_exit_status 254
+ log not applicable.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ not applicable. = -n ]
+ printf %s\n not applicable.
not applicable.
+ LAST_HOOK=75modules
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 75modules ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/90clock ]
+ [ -f /usr/lib/pm-utils/sleep.d/90clock ]
+ hook=/usr/lib/pm-utils/sleep.d/90clock
+ run_hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/90clock
+ local hook=90clock
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:90clock ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:clock ]
+ [ -x /usr/lib/pm-utils/sleep.d/90clock ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/90clock suspend suspend
+ is_set 
+ return 2
+ exit 254
+ local status=254
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/90clock suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/90clock suspend suspend: 
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: + hook_exit_status 254
+ log not applicable.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ not applicable. = -n ]
+ printf %s\n not applicable.
not applicable.
+ LAST_HOOK=90clock
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 90clock ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/94cpufreq ]
+ [ -f /usr/lib/pm-utils/sleep.d/94cpufreq ]
+ hook=/usr/lib/pm-utils/sleep.d/94cpufreq
+ run_hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/94cpufreq
+ local hook=94cpufreq
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:94cpufreq ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:cpufreq ]
+ [ -x /usr/lib/pm-utils/sleep.d/94cpufreq ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend
+ [ -d /sys/devices/system/cpu/ ]
+ hibernate_cpufreq
+ cd /sys/devices/system/cpu/
+ [ -L cpu0/cpufreq ]
+ gov=cpu0/cpufreq/scaling_governor
+ [ -f cpu0/cpufreq/scaling_governor ]
+ grep -q performance cpu0/cpufreq/scaling_available_governors
+ savestate cpu0_governor
+ [ -n  ]
+ cat
+ echo performance
+ [ -L cpu1/cpufreq ]
+ gov=cpu1/cpufreq/scaling_governor
+ [ -f cpu1/cpufreq/scaling_governor ]
+ grep -q performance cpu1/cpufreq/scaling_available_governors
+ savestate cpu1_governor
+ [ -n  ]
+ cat
+ echo performance
+ [ -L cpu2/cpufreq ]
+ gov=cpu2/cpufreq/scaling_governor
+ [ -f cpu2/cpufreq/scaling_governor ]
+ grep -q performance cpu2/cpufreq/scaling_available_governors
+ savestate cpu2_governor
+ [ -n  ]
+ cat
+ echo performance
+ [ -L cpu3/cpufreq ]
+ gov=cpu3/cpufreq/scaling_governor
+ [ -f cpu3/cpufreq/scaling_governor ]
+ grep -q performance cpu3/cpufreq/scaling_available_governors
+ savestate cpu3_governor
+ [ -n  ]
+ cat
+ echo performance
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: 
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=94cpufreq
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 94cpufreq ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/95anacron ]
+ [ -f /usr/lib/pm-utils/sleep.d/95anacron ]
+ hook=/usr/lib/pm-utils/sleep.d/95anacron
+ run_hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/95anacron
+ local hook=95anacron
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:95anacron ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:anacron ]
+ [ -x /usr/lib/pm-utils/sleep.d/95anacron ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/95anacron suspend suspend
stop: Unknown instance: 
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/95anacron suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/95anacron suspend suspend: 
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=95anacron
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 95anacron ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/95hdparm-apm ]
+ [ -f /usr/lib/pm-utils/sleep.d/95hdparm-apm ]
+ hook=/usr/lib/pm-utils/sleep.d/95hdparm-apm
+ run_hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/95hdparm-apm
+ local hook=95hdparm-apm
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:95hdparm-apm ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:hdparm-apm ]
+ [ -x /usr/lib/pm-utils/sleep.d/95hdparm-apm ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend
+ local status=254
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: 
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: + hook_exit_status 254
+ log not applicable.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ not applicable. = -n ]
+ printf %s\n not applicable.
not applicable.
+ LAST_HOOK=95hdparm-apm
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 95hdparm-apm ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/95led ]
+ [ -f /usr/lib/pm-utils/sleep.d/95led ]
+ hook=/usr/lib/pm-utils/sleep.d/95led
+ run_hook /usr/lib/pm-utils/sleep.d/95led suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/95led suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/95led
+ local hook=95led
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:95led ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:led ]
+ [ -x /usr/lib/pm-utils/sleep.d/95led ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/95led suspend suspend
+ local status=254
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/95led suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/95led suspend suspend: 
/usr/lib/pm-utils/sleep.d/95led suspend suspend: + hook_exit_status 254
+ log not applicable.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ not applicable. = -n ]
+ printf %s\n not applicable.
not applicable.
+ LAST_HOOK=95led
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 95led ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/98video-quirk-db-handler ]
+ [ -f /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler ]
+ hook=/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler
+ run_hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler
+ local hook=98video-quirk-db-handler
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:98video-quirk-db-handler ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:video-quirk-db-handler ]
+ [ -x /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend
+ [[ -n true ]]
+ export 'PS4=${BASH_SOURCE}@${LINENO}(${FUNCNAME[0]}): '
+ PS4='${BASH_SOURCE}@${LINENO}(${FUNCNAME[0]}): '
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@10(): set -x
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@25(): possible_video_quirks=' --quirk-dpms-on
	   --quirk-dpms-suspend
	   --quirk-s3-mode
	   --quirk-s3-bios
	   --quirk-vbe-post
	   --quirk-vbe-post
	   --quirk-vga-mode-3
	   --quirk-vbemode-restore
	   --quirk-vbestate-restore
	   --quirk-reset-brightness
	   --quirk-radeon-off
	   --quirk-no-fb
	   --quirk-save-pci'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@40(): possible_system_properties='system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@343(): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@347(): precache_dmivars
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@170(precache_dmivars): local p q f
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.firmware.version
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.firmware.version* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_firmware_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_firmware_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.firmware.version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@107(dmisysget): _dmisysget bios_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/bios_version ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=0301
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=0301
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_firmware_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.firmware.vendor
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.vendor =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.firmware.vendor* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_firmware_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_firmware_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.firmware.vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@106(dmisysget): _dmisysget bios_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/bios_vendor ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES='American Megatrends Inc.'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES='American Megatrends Inc.'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_firmware_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.firmware.release_date
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.release_date =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.firmware.release_date* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_firmware_release_date
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_firmware_release_date
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.firmware.release_date
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@108(dmisysget): _dmisysget bios_date
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/bios_date ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=09/16/2011
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=09/16/2011
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_firmware_release_date
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.hardware.vendor
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.hardware.vendor =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.hardware.vendor* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_hardware_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_hardware_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.hardware.vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@109(dmisysget): _dmisysget sys_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/sys_vendor ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES='System manufacturer'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES='System manufacturer'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_hardware_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.hardware.product
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.hardware.product =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.hardware.product* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_hardware_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_hardware_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.hardware.product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@110(dmisysget): _dmisysget product_name
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/product_name ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES='System Product Name'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES='System Product Name'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_hardware_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.hardware.version
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.hardware.version =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.hardware.version* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_hardware_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_hardware_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.hardware.version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@111(dmisysget): _dmisysget product_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/product_version ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES='System Version'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES='System Version'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_hardware_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.board.product
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.board.product =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.board.product* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_board_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_board_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.board.product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@112(dmisysget): _dmisysget board_name
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/board_name ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES='P8Z68-V GEN3'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES='P8Z68-V GEN3'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_board_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.board.version
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.board.version =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.board.version* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_board_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_board_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.board.version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@113(dmisysget): _dmisysget board_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/board_version ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES='Rev 1.xx'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES='Rev 1.xx'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_board_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.board.vendor
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.board.vendor =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.board.vendor* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_board_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_board_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.board.vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@114(dmisysget): _dmisysget board_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/board_vendor ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES='ASUSTeK Computer INC.'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES='ASUSTeK Computer INC.'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_board_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.hardware.primary_video.vendor
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.hardware.primary_video.vendor =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.hardware.primary_video.vendor* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_hardware_primary_video_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_hardware_primary_video_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.hardware.primary_video.vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@115(dmisysget): videoget vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@65(videoget): local dev pci
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@66(videoget): pci=/sys/bus/pci/devices
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:00.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:00.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:01.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:01.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:02.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:02.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x038000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:16.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:16.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x078000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:19.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:19.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x020000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1a.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1a.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0320 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1b.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1b.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x040300 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.2/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.2/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.3/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.3/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.6/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.6/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060401 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.7/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.7/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1d.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1d.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0320 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1f.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1f.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060100 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1f.2/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1f.2/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x010601 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1f.3/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1f.3/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0500 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:01:00.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:01:00.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x030000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@70(videoget): case $1 in
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@71(videoget): cat /sys/bus/pci/devices/0000:01:00.0/vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@71(videoget): RES=0x10de
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@91(videoget): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=0x10de
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=0x10de
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_hardware_primary_video_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.hardware.primary_video.product
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.hardware.primary_video.product =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.hardware.primary_video.product* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_hardware_primary_video_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_hardware_primary_video_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.hardware.primary_video.product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@116(dmisysget): videoget device
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@65(videoget): local dev pci
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@66(videoget): pci=/sys/bus/pci/devices
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:00.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:00.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:01.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:01.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:02.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:02.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x038000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:16.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:16.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x078000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:19.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:19.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x020000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1a.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1a.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0320 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1b.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1b.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x040300 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.2/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.2/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.3/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.3/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.6/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.6/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060401 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.7/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.7/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1d.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1d.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0320 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1f.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1f.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060100 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1f.2/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1f.2/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x010601 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1f.3/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1f.3/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0500 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:01:00.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:01:00.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x030000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@70(videoget): case $1 in
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@72(videoget): cat /sys/bus/pci/devices/0000:01:00.0/device
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@72(videoget): RES=0x1244
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@91(videoget): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=0x1244
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=0x1244
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_hardware_primary_video_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.hardware.primary_video.driver
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.hardware.primary_video.driver =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.hardware.primary_video.driver* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_hardware_primary_video_driver
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_hardware_primary_video_driver
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.hardware.primary_video.driver
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@117(dmisysget): videoget driver
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@65(videoget): local dev pci
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@66(videoget): pci=/sys/bus/pci/devices
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:00.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:00.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:01.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:01.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:02.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:02.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x038000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:16.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:16.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x078000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:19.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:19.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x020000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1a.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1a.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0320 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1b.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1b.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x040300 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.2/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.2/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.3/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.3/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.6/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.6/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060401 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.7/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.7/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1d.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1d.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0320 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1f.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1f.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060100 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1f.2/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1f.2/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x010601 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1f.3/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1f.3/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0500 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:01:00.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:01:00.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x030000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@70(videoget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@74(videoget): [[ -L /sys/bus/pci/devices/0000:01:00.0/driver ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@75(videoget): readlink /sys/bus/pci/devices/0000:01:00.0/driver
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@75(videoget): RES=../../../../bus/pci/drivers/nvidia
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@76(videoget): RES=nvidia
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@91(videoget): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=nvidia
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=nvidia
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_hardware_primary_video_driver
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.hardware.primary_video.using_kms
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.hardware.primary_video.using_kms =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.hardware.primary_video.using_kms* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_hardware_primary_video_using_kms
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_hardware_primary_video_using_kms
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.hardware.primary_video.using_kms
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@118(dmisysget): videoget using_kms
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@65(videoget): local dev pci
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@66(videoget): pci=/sys/bus/pci/devices
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:00.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:00.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:01.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:01.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:02.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:02.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x038000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:16.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:16.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x078000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:19.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:19.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x020000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1a.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1a.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0320 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1b.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1b.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x040300 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.2/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.2/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.3/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.3/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.6/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.6/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060401 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.7/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.7/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1d.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1d.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0320 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1f.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1f.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060100 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1f.2/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1f.2/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x010601 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1f.3/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1f.3/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0500 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:01:00.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:01:00.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x030000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@70(videoget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@84(videoget): using_kms
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@60(using_kms): grep -q -E '(nouveau|drm)fb' /proc/fb
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@87(videoget): RES=false
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@91(videoget): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=false
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=false
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_hardware_primary_video_using_kms
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.kernel.version
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.kernel.version =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.kernel.version* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_kernel_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_kernel_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.kernel.version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@119(dmisysget): uname -r
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@119(dmisysget): RES=3.2.0-33-generic
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=3.2.0-33-generic
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=3.2.0-33-generic
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_kernel_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@181(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@352(): has_parameter --quirk-test
//usr/lib/pm-utils/functions@239(has_parameter): get_parameters
//usr/lib/pm-utils/functions@234(get_parameters): cat /var/run/pm-utils/pm-suspend/storage/parameters
/usr/lib/pm-utils/functions@243(has_parameter): return 1
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@358(): using_kms
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@60(using_kms): grep -q -E '(nouveau|drm)fb' /proc/fb
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@363(): using_nvidia
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@54(using_nvidia): [[ -d /sys/module/nvidia ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@365(): remove_parameters --quirk-dpms-on --quirk-dpms-suspend --quirk-s3-mode --quirk-s3-bios --quirk-vbe-post --quirk-vbe-post --quirk-vga-mode-3 --quirk-vbemode-restore --quirk-vbestate-restore --quirk-reset-brightness --quirk-radeon-off --quirk-no-fb --quirk-save-pci
/usr/lib/pm-utils/functions@210(remove_parameters): local p
/usr/lib/pm-utils/functions@211(remove_parameters): '[' --quirk-dpms-on = all ']'
/usr/lib/pm-utils/functions@214(remove_parameters): echo ''
/usr/lib/pm-utils/functions@215(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@216(remove_parameters): echo --quirk-dpms-on
/usr/lib/pm-utils/functions@215(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@216(remove_parameters): echo --quirk-dpms-suspend
/usr/lib/pm-utils/functions@215(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@216(remove_parameters): echo --quirk-s3-mode
/usr/lib/pm-utils/functions@215(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@216(remove_parameters): echo --quirk-s3-bios
/usr/lib/pm-utils/functions@215(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@216(remove_parameters): echo --quirk-vbe-post
/usr/lib/pm-utils/functions@215(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@216(remove_parameters): echo --quirk-vbe-post
/usr/lib/pm-utils/functions@215(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@216(remove_parameters): echo --quirk-vga-mode-3
/usr/lib/pm-utils/functions@215(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@216(remove_parameters): echo --quirk-vbemode-restore
/usr/lib/pm-utils/functions@215(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@216(remove_parameters): echo --quirk-vbestate-restore
/usr/lib/pm-utils/functions@215(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@216(remove_parameters): echo --quirk-reset-brightness
/usr/lib/pm-utils/functions@215(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@216(remove_parameters): echo --quirk-radeon-off
/usr/lib/pm-utils/functions@215(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@216(remove_parameters): echo --quirk-no-fb
/usr/lib/pm-utils/functions@215(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@216(remove_parameters): echo --quirk-save-pci
/usr/lib/pm-utils/functions@219(remove_parameters): grep -vxFf /var/run/pm-utils/pm-suspend/storage/parameters.rm /var/run/pm-utils/pm-suspend/storage/parameters
/usr/lib/pm-utils/functions@221(remove_parameters): cp -f /var/run/pm-utils/pm-suspend/storage/parameters.new /var/run/pm-utils/pm-suspend/storage/parameters
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@366(): echo 'nVidia binary video drive detected, not using quirks.'
nVidia binary video drive detected, not using quirks.
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: 
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=98video-quirk-db-handler
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 98video-quirk-db-handler ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ get_parameters
+ cat /var/run/pm-utils/pm-suspend/storage/parameters
+ export PM_CMDLINE=
+ rm -f /var/run/pm-utils/pm-suspend/storage/parameters.new
+ [ -f /etc/pm/sleep.d/99video ]
+ [ -f /usr/lib/pm-utils/sleep.d/99video ]
+ hook=/usr/lib/pm-utils/sleep.d/99video
+ run_hook /usr/lib/pm-utils/sleep.d/99video suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/99video suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/99video
+ local hook=99video
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:99video ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:video ]
+ [ -x /usr/lib/pm-utils/sleep.d/99video ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/99video suspend suspend
+ command_exists vbetool
+ type vbetool
+ return 0
+ command_exists radeontool
+ type radeontool
+ return 0
+ maybe_chvt
+ is_set 
+ return 2
+ fgconsole
+ savestate console
+ [ -n  ]
+ cat
+ chvt 63
+ suspend_video
+ local acpi_flag=0
+ quirk 
+ is_set 
+ return 2
+ quirk 
+ is_set 
+ return 2
+ sysctl -w kernel.acpi_video_flags=0
kernel.acpi_video_flags = 0
+ quirk 
+ is_set 
+ return 2
+ quirk 
+ is_set 
+ return 2
+ quirk 
+ is_set 
+ return 2
+ quirk 
+ is_set 
+ return 2
+ quirk 
+ is_set 
+ return 2
+ quirk 
+ is_set 
+ return 2
+ quirk 
+ is_set 
+ return 2
+ save_fbcon
+ local con
+ [ -f /sys/class/graphics/fb0/state ]
+ echo 1
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/99video suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/99video suspend suspend: 
/usr/lib/pm-utils/sleep.d/99video suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=99video
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 99video ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/novatel_3g_suspend ]
+ hook=/etc/pm/sleep.d/novatel_3g_suspend
+ run_hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend
+ _run_hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend
+ log Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend: = -n ]
+ printf %s\n Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
+ hook_ok /etc/pm/sleep.d/novatel_3g_suspend
+ local hook=novatel_3g_suspend
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:novatel_3g_suspend ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:novatel_3g_suspend ]
+ [ -x /etc/pm/sleep.d/novatel_3g_suspend ]
+ return 0
+ /etc/pm/sleep.d/novatel_3g_suspend suspend suspend
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /etc/pm/sleep.d/novatel_3g_suspend suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /etc/pm/sleep.d/novatel_3g_suspend suspend suspend: 
/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=novatel_3g_suspend
+ IFS=

+ IFS= 	

+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ return 0
+ date
+ log Wed Nov 28 10:29:24 EST 2012: performing suspend
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Wed Nov 28 10:29:24 EST 2012: performing suspend = -n ]
+ printf %s\n Wed Nov 28 10:29:24 EST 2012: performing suspend
Wed Nov 28 10:29:24 EST 2012: performing suspend
+ sync
+ do_suspend
+ echo -n mem

```

---

### Post by Toz on 2012-11-28
I'm not seeing anything wrong with this last log file. I'm going to suggest a couple of things to try (might be a long shot, but won't hurt to try). Note: I see you are back on kernel 3.2. Good. Lets work with it since the newer kernel didn't solve the problem.

1. Can you try the **acpi_sleep=nonvs** kernel parameter. This parameter is known to get some systems to enter sleep mode by not saving the ACPI NONVS memory.

2. You stated in your original post that you tried the suggestion [here]("http://ubuntuforums.org/showthread.php?t=1969615") to unload the USB 3 drivers before and after suspend. Can you try this one again (file from post #4)? (make sure the file you create is executable). Post back the contents of the file your created and the contents of /var/log/pm-suspend.log after an attempt at suspending using this.

3. Here is another script that you can try: [http://ubuntuforums.org/showpost.php?p=9475037&postcount=18]("http://ubuntuforums.org/showpost.php?p=9475037&postcount=18")

---

### Post by NertSkull on 2012-11-28
I did the acpi_sleep (by adding it to the grub.cfg) and rebooted.  Still no luck.

I have tried the post in your #2.  But I tried it again.  This is my script file

```
#!/bin/bash
# Disables echi / ohci / uhci ports on suspend and reenables them on resume. 
# Place this script in /etc/pm/sleep.d


function unbind_usb {
    for driver in ehci ohci uhci; do
        cd "/sys/bus/pci/drivers/${driver}_hcd";
        ids=$(ls | grep :);
        echo $ids > /tmp/DISABLED_$driver;
        for id in $ids; do
            echo "Unbinding $id";
            echo -n "$id" > unbind;
            disabled="$disabled $id";
        done;
    done;
}

function bind_usb {
    for driver in ehci ohci uhci; do
        cd "/sys/bus/pci/drivers/${driver}_hcd";
        for id in $(cat /tmp/DISABLED_$driver); do
            echo "Binding $id";
            echo -n "$id" > bind;
        done;
        rm /tmp/DISABLED_$driver;
    done;
}

case "$1" in
    hibernate|suspend)
        unbind_usb;
    ;;
    thaw|resume)
        bind_usb;
        # Uncomment the following two lines if USB devices stutter after resume
        # unbind_usb;
        # bind_usb;
    ;;
    *)
    exit 1;
    ;;
esac;
exit 0;

```

I named that /etc/pm/sleep.d/20_sleep_fix.sh and I did a chmod of 777 on it.

This is the output of cat /proc/acpi/wakeup  BEFORE changing them
 
```
Device  S-state   Status   Sysfs node
BR20      S3    *disabled  
USBE      S4    *enabled   pci:0000:00:1a.0
P0P3      S4    *disabled  
P0P4      S4    *disabled  
P0P1      S4    *disabled  pci:0000:00:01.0
P0P2      S4    *disabled  
PEX0      S4    *disabled  pci:0000:00:1c.0
PEX1      S4    *disabled  
PEX2      S4    *disabled  pci:0000:00:1c.2
PEX3      S4    *disabled  pci:0000:00:1c.3
PEX4      S4    *disabled  
PEX5      S4    *disabled  
PEX6      S4    *disabled  pci:0000:00:1c.6
BR24      S4    *disabled  pci:0000:05:00.0
PEX7      S4    *disabled  pci:0000:00:1c.7
GBE       S4    *enabled   pci:0000:00:19.0
EUSB      S4    *enabled   pci:0000:00:1d.0
PWRB      S4    *enabled   


```

And here is the result of cat /proc/acpi/wakeup AFTER changing

```
Device  S-state   Status   Sysfs node
BR20      S3    *disabled  
USBE      S4    *disabled  pci:0000:00:1a.0
P0P3      S4    *disabled  
P0P4      S4    *disabled  
P0P1      S4    *disabled  pci:0000:00:01.0
P0P2      S4    *disabled  
PEX0      S4    *disabled  pci:0000:00:1c.0
PEX1      S4    *disabled  
PEX2      S4    *disabled  pci:0000:00:1c.2
PEX3      S4    *disabled  pci:0000:00:1c.3
PEX4      S4    *disabled  
PEX5      S4    *disabled  
PEX6      S4    *disabled  pci:0000:00:1c.6
BR24      S4    *disabled  pci:0000:05:00.0
PEX7      S4    *disabled  pci:0000:00:1c.7
GBE       S4    *disabled  pci:0000:00:19.0
EUSB      S4    *disabled  pci:0000:00:1d.0
PWRB      S4    *disabled  
```

And here is the log of pm-suspend again after that.

```
Initial commandline parameters: 
Wed Nov 28 16:03:45 EST 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux IDPNux 3.2.0-33-generic #52-Ubuntu SMP Thu Oct 18 16:29:15 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
xts                    12756  4 
gf128mul               14951  1 xts
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             25670  0 
vboxnetflt             23441  0 
snd_hda_codec_hdmi     32474  5 
snd_hda_codec_realtek   224173  1 
vboxdrv               320210  3 vboxpci,vboxnetadp,vboxnetflt
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
parport_pc             32866  0 
ppdev                  17113  0 
ext2                   73795  1 
ip6t_LOG               16974  4 
xt_hl                  12521  6 
ip6t_rt                12558  3 
nf_conntrack_ipv6      13906  7 
nf_defrag_ipv6         13368  1 nf_conntrack_ipv6
ipt_REJECT             12576  1 
ipt_LOG                12919  5 
xt_limit               12711  12 
xt_tcpudp              12603  18 
xt_addrtype            12713  4 
xt_state               12578  14 
ip6table_filter        12815  1 
ip6_tables             27864  3 ip6t_LOG,ip6t_rt,ip6table_filter
nf_conntrack_netbios_ns    12665  0 
nf_conntrack_broadcast    12589  1 nf_conntrack_netbios_ns
nf_nat_ftp             12704  0 
nf_nat                 25891  1 nf_nat_ftp
nf_conntrack_ipv4      19716  9 nf_nat
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
nf_conntrack_ftp       13452  1 nf_nat_ftp
nf_conntrack           81926  8 nf_conntrack_ipv6,xt_state,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
joydev                 17693  0 
uvcvideo               72627  0 
eeepc_wmi              13109  0 
asus_wmi               24456  1 eeepc_wmi
sparse_keymap          13890  1 asus_wmi
videodev               98259  1 uvcvideo
iptable_filter         12810  1 
mxm_wmi                12979  0 
ip_tables              27473  1 iptable_filter
v4l2_compat_ioctl32    17128  1 videodev
snd_hda_intel          33773  5 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_usb_audio         122982  1 
snd_pcm                97188  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_usb_audio
snd_hwdep              13668  2 snd_hda_codec,snd_usb_audio
x_tables               29846  13 ip6t_LOG,xt_hl,ip6t_rt,ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,xt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
snd_usbmidi_lib        25395  1 snd_usb_audio
snd_seq_midi           13324  0 
snd_rawmidi            30748  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
nvidia              11257276  54 
psmouse                97443  0 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
mac_hid                13253  0 
mei                    41616  0 
serio_raw              13211  0 
wmi                    19256  2 asus_wmi,mxm_wmi
snd                    78855  24 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_pcm,snd_hwdep,snd_usbmidi_lib,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
dm_crypt               23125  2 
vesafb                 13844  1 
usbhid                 47199  0 
hid                    99592  1 usbhid
i915                  473298  0 
e1000e                156715  0 
drm_kms_helper         46978  1 i915
drm                   241921  2 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19596  1 i915
             total       used       free     shared    buffers     cached
Mem:      16341412    1527520   14813892          0      42892     506664
-/+ buffers/cache:     977964   15363448
Swap:     36585468          0   36585468

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /etc/pm/sleep.d/20_sleep_fix.sh suspend suspend:
Unbinding 0000:00:1a.0
Unbinding 0000:00:1d.0

/etc/pm/sleep.d/20_sleep_fix.sh suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
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
Wed Nov 28 16:03:46 EST 2012: performing suspend

```

I have noticed that my /proc/acpi/wakeup does look different than eveyone elses.  I don't have any USB2 type looking entries.  I don't know what that means.

I haven't tried your script from #3 yet, but I will first thing in the morning when I'm back here.

Thanks for the help.

---

### Post by NertSkull on 2012-11-29
Ok, so I tried the suggestion in your #3.  I put this into /etc/pm/sleep.d/05_disable_usb3 and made it executable

```
#!/bin/bash

## Unload USB 3 module before sleep

case "$1" in
    suspend)
        /sbin/modprobe -r xhci
        ;;
    hibernate)
        /sbin/modprobe -r xhci
        ;;
    thaw)
        /sbin/modprobe xhci
        ;;
    resume)
        /sbin/modprobe xhci
        ;;
esac
```

Now, it doesn't do anything when trying to pm-suspend.  It just sites there.  But now the log in pm-suspend is different.  It gets "inhibited".  Here is the log.

```
Initial commandline parameters: 
Thu Nov 29 08:55:39 EST 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux IDPNux 3.2.0-33-generic #52-Ubuntu SMP Thu Oct 18 16:29:15 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
xts                    12756  4 
gf128mul               14951  1 xts
snd_hda_codec_hdmi     32474  5 
snd_hda_codec_realtek   224173  1 
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             25670  0 
vboxnetflt             23441  0 
vboxdrv               320210  3 vboxpci,vboxnetadp,vboxnetflt
rfcomm                 47604  0 
parport_pc             32866  0 
bnep                   18281  2 
ppdev                  17113  0 
bluetooth             180104  10 rfcomm,bnep
ip6t_LOG               16974  4 
xt_hl                  12521  6 
ip6t_rt                12558  3 
nf_conntrack_ipv6      13906  7 
snd_hda_intel          33773  5 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
nf_defrag_ipv6         13368  1 nf_conntrack_ipv6
ipt_REJECT             12576  1 
ipt_LOG                12919  5 
ext2                   73795  1 
xt_limit               12711  12 
xt_tcpudp              12603  18 
xt_addrtype            12713  4 
psmouse                97443  0 
xt_state               12578  14 
ip6table_filter        12815  1 
ip6_tables             27864  3 ip6t_LOG,ip6t_rt,ip6table_filter
snd_usb_audio         122982  1 
snd_pcm                97188  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_usb_audio
nf_conntrack_netbios_ns    12665  0 
nf_conntrack_broadcast    12589  1 nf_conntrack_netbios_ns
nf_nat_ftp             12704  0 
snd_hwdep              13668  2 snd_hda_codec,snd_usb_audio
snd_usbmidi_lib        25395  1 snd_usb_audio
nf_nat                 25891  1 nf_nat_ftp
nf_conntrack_ipv4      19716  9 nf_nat
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_rawmidi            30748  2 snd_usbmidi_lib,snd_seq_midi
uvcvideo               72627  0 
nf_conntrack_ftp       13452  1 nf_nat_ftp
nf_conntrack           81926  8 nf_conntrack_ipv6,xt_state,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter         12810  1 
joydev                 17693  0 
eeepc_wmi              13109  0 
asus_wmi               24456  1 eeepc_wmi
sparse_keymap          13890  1 asus_wmi
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
mxm_wmi                12979  0 
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_seq,snd_rawmidi
ip_tables              27473  1 iptable_filter
mac_hid                13253  0 
x_tables               29846  13 ip6t_LOG,xt_hl,ip6t_rt,ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,xt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
nvidia              11257276  54 
wmi                    19256  2 asus_wmi,mxm_wmi
snd                    78855  24 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_pcm,snd_hwdep,snd_usbmidi_lib,snd_seq,snd_rawmidi,snd_timer,snd_seq_device
serio_raw              13211  0 
mei                    41616  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
dm_crypt               23125  2 
vesafb                 13844  1 
usbhid                 47199  0 
hid                    99592  1 usbhid
i915                  473298  0 
drm_kms_helper         46978  1 i915
drm                   241921  2 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
e1000e                156715  0 
video                  19596  1 i915
             total       used       free     shared    buffers     cached
Mem:      16341412    1491776   14849636          0      39260     503804
-/+ buffers/cache:     948712   15392700
Swap:     36585468          0   36585468

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/05_disable_usb3 suspend suspend:
FATAL: Module xhci not found.

/etc/pm/sleep.d/05_disable_usb3 suspend suspend: Returned exit code 1.
Thu Nov 29 08:55:40 EST 2012: Inhibit found, will not perform suspend
Thu Nov 29 08:55:40 EST 2012: Running hooks for resume
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.

```

So, I don't know what all that means, but it appears that there is something wrong with usb stuff?  Is that right?

Or this xhci module, its not there?  Is that something I'm supposed to install?

---

### Post by Toz on 2012-11-29
I just realized that you don't have an xhci module loaded, so this script won't work. Please delete the script. 

Can you post back the listing of loaded modules:
```
lsmod
```

Does the following command return anything:
```
sudo cat /sys/kernel/debug/suspend_stats
```

Here are couple of more basic suggestions:

1. Try unloading the nvidia drivers and running suspend with the open source nouveau drivers instead.

2. Boot your computer into single-user mode (add "single" to the grub boot parameter during the boot cycle) and try a suspend from there via:
```
pm-suspend
```

Resources: 
- [https://wiki.ubuntu.com/UnderstandingSuspend]("https://wiki.ubuntu.com/UnderstandingSuspend")
- [http://www.mjmwired.net/kernel/Documentation/power/basic-pm-debugging.txt#178]("http://www.mjmwired.net/kernel/Documentation/power/basic-pm-debugging.txt#178")

---

### Post by NertSkull on 2012-11-29
K, script is deleted.  Here is the output from lsmod

```
Module                  Size  Used by
xts                    12756  4 
gf128mul               14951  1 xts
snd_hda_codec_hdmi     32474  5 
snd_hda_codec_realtek   224173  1 
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             25670  0 
vboxnetflt             23441  0 
vboxdrv               320210  3 vboxpci,vboxnetadp,vboxnetflt
rfcomm                 47604  0 
parport_pc             32866  0 
ppdev                  17113  0 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
ip6t_LOG               16974  0 
xt_hl                  12521  0 
ip6t_rt                12558  0 
nf_conntrack_ipv6      13906  0 
nf_defrag_ipv6         13368  1 nf_conntrack_ipv6
ipt_REJECT             12576  0 
ipt_LOG                12919  0 
joydev                 17693  0 
snd_seq_midi           13324  0 
xt_limit               12711  0 
snd_rawmidi            30748  1 snd_seq_midi
xt_tcpudp              12603  0 
xt_addrtype            12713  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
nvidia              11257276  54 
ext2                   73795  1 
xt_state               12578  0 
eeepc_wmi              13109  0 
asus_wmi               24456  1 eeepc_wmi
sparse_keymap          13890  1 asus_wmi
mxm_wmi                12979  0 
ip6table_filter        12815  1 
ip6_tables             27864  3 ip6t_LOG,ip6t_rt,ip6table_filter
nf_conntrack_netbios_ns    12665  0 
nf_conntrack_broadcast    12589  1 nf_conntrack_netbios_ns
nf_nat_ftp             12704  0 
nf_nat                 25891  1 nf_nat_ftp
nf_conntrack_ipv4      19716  2 nf_nat
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
nf_conntrack_ftp       13452  1 nf_nat_ftp
nf_conntrack           81926  8 nf_conntrack_ipv6,xt_state,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter         12810  1 
ip_tables              27473  1 iptable_filter
snd_hda_intel          33773  5 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
psmouse                97443  0 
serio_raw              13211  0 
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
x_tables               29846  13 ip6t_LOG,xt_hl,ip6t_rt,ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,xt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd_timer              29990  2 snd_seq,snd_pcm
wmi                    19256  2 asus_wmi,mxm_wmi
snd                    78855  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_rawmidi,snd_seq,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_device,snd_timer
mac_hid                13253  0 
mei                    41616  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
dm_crypt               23125  2 
vesafb                 13844  1 
usbhid                 47199  0 
hid                    99592  1 usbhid
i915                  473298  0 
drm_kms_helper         46978  1 i915
drm                   241921  2 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19596  1 i915
e1000e                156715  0 

```

And here is the output of the suspend_stats command

```
success: 0
fail: 0
failed_freeze: 0
failed_prepare: 0
failed_suspend: 0
failed_suspend_noirq: 0
failed_resume: 0
failed_resume_noirq: 0
failures:
  last_failed_dev:	
			
  last_failed_errno:	0
			0
  last_failed_step:	
			

```

I then complete purged the nvidia drivers (nvidia-common, nvidia-current-updates, nvidia-settings-updates).  So they are completely gone. 

I'm not familiar with the nouveau drivers, but my understanding is they are the default, and I don't actually install them.  I do have the "xserver-xorg-video-nouveau" package installed though, so I think that is them.  Let me know if its not.

So I removed the nvidia drivers, and tried suspend, and still nothing.  

I then tried the single command.  Which took me straight to a root prompt, and tried suspend, and still nothing.

Should I leave the nvidia drivers uninstalled?  Or can I re-install them since that doesn't appear to be the problem.

Also, thanks for the help.  Hopefully we'll get this figured out.

And here is the most recent pm-suspend.log using the nouveau drivers.

```
Initial commandline parameters: 
Thu Nov 29 11:49:29 EST 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux IDPNux 3.2.0-33-generic #52-Ubuntu SMP Thu Oct 18 16:29:15 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
xts                    12756  4 
gf128mul               14951  1 xts
snd_hda_codec_hdmi     32474  5 
snd_hda_codec_realtek   224173  1 
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             25670  0 
vboxnetflt             23441  0 
vboxdrv               320210  3 vboxpci,vboxnetadp,vboxnetflt
bnep                   18281  2 
rfcomm                 47604  0 
bluetooth             180104  10 bnep,rfcomm
parport_pc             32866  0 
ppdev                  17113  0 
ext2                   73795  1 
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
joydev                 17693  0 
eeepc_wmi              13109  0 
asus_wmi               24456  1 eeepc_wmi
sparse_keymap          13890  1 asus_wmi
snd_hda_intel          33773  5 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
psmouse                97443  0 
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
serio_raw              13211  0 
snd_timer              29990  2 snd_seq,snd_pcm
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78855  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_rawmidi,snd_seq,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_device,snd_timer
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mei                    41616  0 
mac_hid                13253  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
dm_crypt               23125  2 
usbhid                 47199  0 
hid                    99592  1 usbhid
nouveau               774641  0 
ttm                    76949  1 nouveau
i915                  473298  0 
drm_kms_helper         46978  2 nouveau,i915
mxm_wmi                12979  1 nouveau
drm                   241921  4 nouveau,ttm,i915,drm_kms_helper
wmi                    19256  2 asus_wmi,mxm_wmi
i2c_algo_bit           13423  2 nouveau,i915
e1000e                156715  0 
video                  19596  2 nouveau,i915
             total       used       free     shared    buffers     cached
Mem:      16341412    1722244   14619168          0      41008     538080
-/+ buffers/cache:    1143156   15198256
Swap:     36585468          0   36585468

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
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
No quirk database entry for this system, using default.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0
Allocated buffer at 0x11000 (base is 0x0)
ES: 0x1100 EBX: 0x0000

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Thu Nov 29 11:49:31 EST 2012: performing suspend

```

---

### Post by Toz on 2012-11-29
Well, it looks like it wasn't the nvidia drivers. This is a tough one.

Can you take a look in your bios to see if there are any acpi sleep state settings? Maybe making an adjustment there might help???

And you may also want to give the debugging procedures [here]("http://www.mjmwired.net/kernel/Documentation/power/basic-pm-debugging.txt#178") a try to see if they can yield some information.

---

### Post by NertSkull on 2012-12-06
Alright, I have finally made some progress.

First, I have changed nearly every setting in my BIOS I can think of and nothing seems to work.

So then I went through that debugging stuff you linked to, and most of it didn't work.

BUT

Some did work.  First, I tried a bunch of commands using the "init=/bin/bash" at boot.  The following commands would make my computer suspend, but NOT wake from suspend.

```
s2ram -f -m
s2ram -f -s
s2ram -f -p -m
s2ram -f -p -s
s2ram -f -a 1 -m
s2ram -f -a 1 -s
```

So, that was good.  Because up until now, the computer NEVER would even turn off to suspend.  But, using those, it would not wake.  So I still had to force restart.

But I decided to try them booted into my normal desktop.  Now suspend AND wake works.  I don't know why.  But only the following ones worked in my desktop.

```
sudo s2ram -f -m
sudo s2ram -f -s
sudo s2ram -f -p -m
```

So, I can make my computer suspend using those.  And it will wake from suspend.  So should I just do it that way??  I feel like its not quite where it should be still.  But hopefully that helps point to where the problem may be.

I tried learning more about those switches, but "man s2ram" doesn't define any of them.

So where should I go next? Thanks for the help.  I'm feeling like I'm getting places now.

---

### Post by Toz on 2012-12-06
If s2ram works, try this ([clicky]("http://ubuntuforums.org/showpost.php?p=10961829&postcount=2")) to set it as the default suspend method. I haven't used this in a while so I'm not exactly sure it still works, but it may be worth a try.

Here is a link with more information about uswusp: [http://en.opensuse.org/SDB:Suspend_to_RAM]("http://en.opensuse.org/SDB:Suspend_to_RAM")

---

### Post by NertSkull on 2012-12-07
So is that ok?  I feel like I haven't really "solved the problem" just found something that works.

I mean if my best option is just to use s2ram, then I'm okay with that.  

So should I just use s2ram and forget about things?  Or should I still try to figure out why pm-suspend doesn't work?

Not trying to be difficult, just don't want to unnecessarily leave loose ends.

---

### Post by Toz on 2012-12-07
If s2ram works, then I say use it. I have an old Toshiba laptop here that only suspends with s2ram.

If you want to try to get pm-utils to work, it may be best now to create a bug report against pm-utils:
```
ubuntu-bug pm-utils
```
...and have one of the developers look into it.

---

### Post by NertSkull on 2012-12-08
No, I think I'm fine use s2ram.  I just wanted to make sure I'm doing something legit, and not settling for something "hackish" that isn't good long term.

But if s2ram is okay as a permanent solution, I can handle that.  In the end I just want my system to suspend and wake.  So if that is best, I can handle that.

Thanks for all the help.

---

### Post by NertSkull on 2012-12-08
Also, I guess I'm marking this thread as "solved".  Even though its not really solved in the sense of figuring out what was wrong with pm-utils, but solved in the sense I've found a way to make it work.

I assume that's the thing to do.

---

### Post by ivotkl on 2012-12-29
> **Toz said:**
> I wonder if it has something to do with [this]("http://www.phoronix.com/scan.php?page=news_item&px=MTA0NDE"):

My GF's PC will suspend and hibernate but has AMD chipsets on motherboard and processor. I Believe MoBo is MSI K9  or something alike. 1 module of DDR2 2GB Kingston and 200ish HDD, Western Digital.

---

