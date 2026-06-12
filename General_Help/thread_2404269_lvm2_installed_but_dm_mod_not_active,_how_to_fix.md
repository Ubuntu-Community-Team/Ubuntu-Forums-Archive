---
title: "lvm2 installed but dm_mod not active, how to fix"
date: 2018-10-22
forum: General Help
---

### Post by bijaydeyp on 2018-10-22
I am using ubuntu 14.04 32-bit latest kernel.
when I run  
$ modinfo dm-mod
 its output:  ERROR: Module dm_mod not found
 I have already installed lvm2 package and read, it is into linux-kernel ([https://bugs.launchpad.net/ubuntu/+source/lvm2/+bug/343147](https://bugs.launchpad.net/ubuntu/+source/lvm2/+bug/343147)).

 $ uname -r
4.4.0-137-generic
---------------------------------------------------------------------------------------------------------
 $ lsmod | grep dm
dm_crypt               24576  0
------------------------------------------------------------------------------------------------------------
 $ lsmod
Module                  Size  Used by
rndis_host             16384  0 
cdc_ether              16384  1 rndis_host
usbnet                 45056  2 rndis_host,cdc_ether
mii                    16384  1 usbnet
drbg                   28672  1 
ansi_cprng             16384  0 
ctr                    16384  0 
ccm                    20480  0 
pci_stub               16384  1 
vboxpci                24576  0 
vboxnetadp             28672  0 
vboxnetflt             28672  0 
vboxdrv               339968  3 vboxnetadp,vboxnetflt,vboxpci
bnep                   20480  2 
rfcomm                 65536  0 
dm_crypt               24576  0 
ip6t_REJECT            16384  1 
nf_reject_ipv6         16384  1 ip6t_REJECT
nf_log_ipv6            16384  5 
xt_hl                  16384  6 
ip6t_rt                16384  3 
nf_conntrack_ipv6      20480  8 
nf_defrag_ipv6         28672  1 nf_conntrack_ipv6
ipt_REJECT             16384  1 
nf_reject_ipv4         16384  1 ipt_REJECT
nf_log_ipv4            16384  5 
nf_log_common          16384  2 nf_log_ipv4,nf_log_ipv6
xt_LOG                 16384  10 
binfmt_misc            20480  1 
xt_limit               16384  13 
xt_tcpudp              16384  18 
xt_addrtype            16384  4 
nf_conntrack_ipv4      16384  8 
nf_defrag_ipv4         16384  1 nf_conntrack_ipv4
xt_conntrack           16384  16 
gpio_ich               16384  0 
ip6table_filter        16384  1 
arc4                   16384  2 
uvcvideo               73728  0 
ip6_tables             20480  1 ip6table_filter
nf_conntrack_netbios_ns    16384  0 
nf_conntrack_broadcast    16384  1 nf_conntrack_netbios_ns
ath9k                 135168  0 
nf_nat_ftp             16384  0 
nf_nat                 24576  1 nf_nat_ftp
videobuf2_vmalloc      16384  1 uvcvideo
nf_conntrack_ftp       16384  1 nf_nat_ftp
nf_conntrack           94208  8 nf_nat_ftp,nf_conntrack_netbios_ns,nf_nat,xt_conntrack,nf_conntrack_broadcast,nf_conntrack_ftp,nf_conntrack_ipv4,nf_conntrack_ipv6
videobuf2_memops       16384  1 videobuf2_vmalloc
iptable_filter         16384  1 
ip_tables              20480  1 iptable_filter
x_tables               24576  13 ip6table_filter,xt_hl,ip_tables,xt_tcpudp,xt_limit,xt_conntrack,xt_LOG,iptable_filter,ip6t_rt,ipt_REJECT,ip6_tables,xt_addrtype,ip6t_REJECT
videobuf2_v4l2         28672  1 uvcvideo
videobuf2_core         36864  2 uvcvideo,videobuf2_v4l2
v4l2_common            16384  1 videobuf2_v4l2
videodev              155648  4 uvcvideo,v4l2_common,videobuf2_core,videobuf2_v4l2
btusb                  36864  0 
ath9k_common           36864  1 ath9k
snd_hda_codec_realtek    73728  1 
snd_hda_codec_generic    69632  1 snd_hda_codec_realtek
btrtl                  16384  1 btusb
ath9k_hw              466944  2 ath9k_common,ath9k
snd_hda_intel          36864  3 
btbcm                  16384  1 btusb
btintel                16384  1 btusb
bluetooth             466944  14 bnep,btbcm,btrtl,btusb,rfcomm,btintel
media                  24576  2 uvcvideo,videodev
samsung_laptop         20480  0 
snd_hda_codec         114688  3 snd_hda_codec_realtek,snd_hda_codec_generic,snd_hda_intel
coretemp               16384  0 
snd_hda_core           61440  4 snd_hda_codec_realtek,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
ath                    24576  3 ath9k_common,ath9k,ath9k_hw
snd_hwdep              16384  1 snd_hda_codec
mac80211              651264  1 ath9k
joydev                 20480  0 
input_leds             16384  0 
snd_pcm                94208  3 snd_hda_codec,snd_hda_intel,snd_hda_core
serio_raw              16384  0 
snd_seq_midi           16384  0 
snd_seq_midi_event     16384  1 snd_seq_midi
cfg80211              487424  4 ath,ath9k_common,ath9k,mac80211
lpc_ich                20480  0 
snd_rawmidi            28672  1 snd_seq_midi
snd_seq                57344  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
snd                    69632  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              16384  1 snd
shpchp                 32768  0 
parport_pc             32768  0 
ppdev                  20480  0 
mac_hid                16384  0 
lp                     20480  0 
parport                49152  3 lp,ppdev,parport_pc
i915                 1138688  3 
hid_generic            16384  0 
usbhid                 49152  0 
hid                    98304  2 hid_generic,usbhid
i2c_algo_bit           16384  1 i915
drm_kms_helper        135168  1 i915
ahci                   36864  2 
psmouse               114688  0 
libahci                32768  1 ahci
syscopyarea            16384  1 drm_kms_helper
sky2                   53248  0 
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
drm                   307200  5 i915,drm_kms_helper
fjes                   28672  0 
video                  40960  2 i915,samsung_laptop

------------------------------------------------------------------------------------
 Why I am still unable to use dm-mod? and How to fix it ?

---

### Post by TheFu on 2018-10-23
I don't have 14.04, but in 16.04 that module isn't needed for using LVM or dm-crypt.

Is there something that isn't working?

---

### Post by bijaydeyp on 2018-10-23
@TheFu Thanks for help.
I am not much linux-savvy.
I was trying to build up 'LVM on LUKS'. I read on internet that dm-crypt & dm-mod are necessary to active.
 when I ask for $ sudo dmsetup status
got the output: device not found
 when run $ lsmod | grep dm
only show dm-crypt but not dm-mod.

---

### Post by TheFu on 2018-10-23
```
$ sudo dmsetup status
```
is not a complete command.  It is missing the device_name option. From the manpage:
>        dmsetup status [--target target_type] [--noflush] [device_name]

These commands are meant for Linux administrators or people willing to break their systems to learn by trial.  Be careful where you find how-to guides.  "on the internet" is not sufficient.  Don't assume that what you read is accurate unless it is from a reputable site and for the same OS release you are running.

dm-mod isn't needed. I didn't bother to see if it even exists.  I'm 100% positive that it isn't needed for 14.04 or 16.04 LUKS  with LVM2 added on top.

Perhaps if you clearly said what you were trying to accomplish **with details**, someone could help with the commands?  Also, for stuff like this, you'll want to read the manpages for each command BEFORE attempting to use them.  To start, saying which disk device you want to use and how much of it to be used is a start.  It would be best to show the information by using CLI commands, so we don't have to worry about misinterpreted details.

And please, please, when posting commands and output, use *code tags*, so the output lines up and is readable just like in a terminal.  We are used to seeing that output.

---

### Post by bijaydeyp on 2018-10-24
> is not a complete command.  It is missing the device_name option
I am sorry. I should have checked it before posting.:(
@TheFu thank you for saving my system from disaster.
>  Perhaps if you clearly said what you were trying to accomplish **with details**, someone could help with the commands?
 Actually I was trying to do this.... ([https://unix.stackexchange.com/questions/473969/how-to-boot-an-encrypted-debian-from-an-unencrypted-ubuntu](https://unix.stackexchange.com/questions/473969/how-to-boot-an-encrypted-debian-from-an-unencrypted-ubuntu))
I was not sure whether Device Mapper working or not. Now, I have successfully set up the system.:D

thanks again.

---

