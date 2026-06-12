---
title: "[SOLVED] Apparmor module NOT installed in Gutsy."
date: 2007-11-03
forum: General Help
---

### Post by Stebalien on 2007-11-03
I had manually compiled and installed the apparmor module in feisty.  Before upgrading to gutsy, I removed Apparmor and its module.  Now, after upgrading to gutsy, I can't load install/load the apparmor module which is supposed to come with the gutsy kernel.  I have tried reinstalling the kernel and that did not work.
`sudo modprobe apparmor` outputs:
```
FATAL: Module apparmor not found.
```
`sudo lsmod` outputs:
```
Module                  Size  Used by
af_packet              21896  4 
binfmt_misc            11400  1 
ppdev                   9348  0 
ipv6                  257700  10 
speedstep_lib           5380  0 
cpufreq_userspace       4116  0 
cpufreq_stats           5508  0 
cpufreq_powersave       1792  0 
cpufreq_ondemand        8084  0 
freq_table              4740  2 cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     6560  0 
battery                10116  0 
wlan_wep                7040  1 
uinput                  9344  1 
lp                     11460  0 
snd_intel8x0           33564  0 
snd_ac97_codec         99492  1 snd_intel8x0
ac97_bus                2304  1 snd_ac97_codec
snd_seq_dummy           3844  0 
wlan_scan_sta          13696  1 
ath_rate_sample        13184  1 
snd_usb_audio          79872  0 
snd_pcm_oss            43264  0 
snd_mixer_oss          16640  1 snd_pcm_oss
snd_pcm                77320  4 snd_intel8x0,snd_ac97_codec,snd_usb_audio,snd_pcm_oss
snd_usb_lib            16768  1 snd_usb_audio
snd_seq_oss            31872  0 
nvidia               6218832  34 
snd_seq_midi            8704  0 
rndis_host              6912  0 
cdc_ether               6272  1 rndis_host
ath_pci                96288  0 
snd_seq_midi_event      7552  2 snd_seq_oss,snd_seq_midi
snd_rawmidi            24832  2 snd_usb_lib,snd_seq_midi
snd_hwdep               9220  1 snd_usb_audio
usbnet                 18696  2 rndis_host,cdc_ether
wlan                  205636  5 wlan_wep,wlan_scan_sta,ath_rate_sample,ath_pci
usbhid                 28384  0 
hid                    27008  1 usbhid
xpad                    9092  0 
parport_pc             36132  1 
parport                35656  3 ppdev,lp,parport_pc
psmouse                38672  0 
ath_hal               191696  3 ath_rate_sample,ath_pci
snd_seq                50416  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22916  2 snd_pcm,snd_seq
snd_seq_device          8332  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcspkr                  3072  0 
serio_raw               7044  0 
i2c_core               25104  1 nvidia
rtc                    13208  0 
snd                    52356  12 snd_intel8x0,snd_ac97_codec,snd_usb_audio,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_hwdep,snd_seq,snd_timer,snd_seq_device
soundcore               7520  1 snd
snd_page_alloc         10504  2 snd_intel8x0,snd_pcm
iTCO_wdt               10656  0 
iTCO_vendor_support     3972  1 iTCO_wdt
shpchp                 33556  0 
pci_hotplug            31288  1 shpchp
intel_agp              24596  1 
agpgart                33584  2 nvidia,intel_agp
evdev                  10240  4 
xt_tcpudp               3328  64 
nf_conntrack_ipv4      18060  44 
xt_state                2560  44 
ipt_REJECT              4736  4 
xt_limit                2688  6 
ipt_LOG                 6400  6 
nf_conntrack_irc        7192  0 
nf_conntrack_ftp        9856  0 
nf_conntrack           62424  4 nf_conntrack_ipv4,xt_state,nf_conntrack_irc,nf_conntrack_ftp
nfnetlink               6040  2 nf_conntrack_ipv4,nf_conntrack
iptable_filter          3072  1 
ip_tables              12232  1 iptable_filter
x_tables               14980  6 xt_tcpudp,xt_state,ipt_REJECT,xt_limit,ipt_LOG,ip_tables
ext3                  129928  3 
jbd                    53416  1 ext3
mbcache                 8324  1 ext3
sg                     36124  0 
sr_mod                 16548  0 
cdrom                  36512  1 sr_mod
sd_mod                 29200  8 
ata_piix               16644  6 
floppy                 58500  0 
e100                   36364  0 
mii                     5632  2 usbnet,e100
ata_generic             7556  0 
libata                125040  2 ata_piix,ata_generic
scsi_mod              146828  4 sg,sr_mod,sd_mod,libata
ehci_hcd               35084  0 
uhci_hcd               25232  0 
usbcore               136088  10 snd_usb_audio,snd_usb_lib,rndis_host,cdc_ether,usbnet,usbhid,xpad,ehci_hcd,uhci_hcd
thermal                13448  0 
processor              23984  1 thermal
fan                     4868  0 
fuse                   44948  7
```
Please help.

---

### Post by Stebalien on 2007-11-05
Solved:
A recent upgrade installed the 386 kernel.  Switching to the generic kernel solved my issue.

---

