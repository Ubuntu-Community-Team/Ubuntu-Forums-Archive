---
title: "wireless and flash player install."
date: 2013-06-02
forum: General Help
---

### Post by frankramiro on 2013-06-02
Hi guys good to join here greeting to everbody  i'm a fan of UBUNTU but infortunatly i can't install it on my sony ol vaio due to no  PAE conpatible. so i went with XUNBUNTU and i like it but i can't set up the wireless and install the Flash player and these items are very inportant to me otherwise i have to move to a Distro that can do the job, the cable ethernet connection is good.so i need you guys to help me to figuer this one out, i'm not very savey on this but i'm not damm eather,i run Unbuntu on a more powefull PC so i know some.

My Terminal info is this;

```
dmesg [options]

Options:
-C, --clear clear the kernel ring buffer
-c, --read-clear read and clear all messages
-D, --console-off disable printing messages to console
-d, --show-delta show time delta between printed messages
-E, --console-on enable printing messages to console
-f, --facility restrict output to defined facilities
-h, --help display this help and exit
-k, --kernel display kernel messages
-l, --level restrict output to defined levels
-n, --console-level set level of messages printed to console
-r, --raw print the raw message buffer
-s, --buffer-size buffer size to query the kernel ring buffer
-T, --ctime show human readable timestamp (could be
inaccurate if you have used SUSPEND/RESUME)
-t, --notime don't print messages timestamp
-u, --userspace display userspace messages
-V, --version output version information and exit
-x, --decode decode facility and level to readable string

Supported log facilities:
kern - kernel messages
user - random user-level messages
mail - mail system
daemon - system daemons
auth - security/authorization messages
syslog - messages generated internally by syslogd
lpr - line printer subsystem
news - network news subsystem

Supported log levels (priorities):
emerg - system is unusable
alert - action must be taken immediately
crit - critical conditions
err - error conditions
warn - warning conditions
notice - normal but significant condition
info - informational
debug - debug-level messages

frank@VGN-A195EP-PT:~$ lsmod
Module Size Used by
tifm_sd 17566 0
joydev 17393 0
snd_intel8x0 33455 3
snd_ac97_codec 110213 1 snd_intel8x0
ac97_bus 12642 1 snd_ac97_codec
snd_pcm 80916 2 snd_intel8x0,snd_ac97_codec
snd_seq_midi 13132 0
snd_rawmidi 25424 1 snd_seq_midi
snd_seq_midi_event 14475 1 snd_seq_midi
pcmcia 39826 0
radeon 733914 2
snd_seq 51592 2 snd_seq_midi,snd_seq_midi_event
snd_timer 28931 2 snd_pcm,snd_seq
snd_seq_device 14172 3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse 96718 0
tifm_7xx1 12937 0
snd 62218 13 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,sn d_seq,snd_timer,snd_seq_device
tifm_core 15040 2 tifm_sd,tifm_7xx1
ipw2200 146210 0
libipw 46732 1 ipw2200
cfg80211 178877 2 ipw2200,libipw
ttm 65344 1 radeon
soundcore 14635 1 snd
serio_raw 13027 0
yenta_socket 27428 0
pcmcia_rsrc 18367 1 yenta_socket
drm_kms_helper 45466 1 radeon
snd_page_alloc 14115 2 snd_intel8x0,snd_pcm
lib80211 14040 2 ipw2200,libipw
pcmcia_core 21511 3 pcmcia,yenta_socket,pcmcia_rsrc
drm 197641 4 radeon,ttm,drm_kms_helper
sony_laptop 39681 0
parport_pc 32114 0
mac_hid 13077 0
rfcomm 38139 4
bnep 17830 2
bluetooth 158479 10 rfcomm,bnep
ppdev 12849 0
i2c_algo_bit 13199 1 radeon
asus_laptop 23693 0
sparse_keymap 13658 1 asus_laptop
input_polldev 13648 1 asus_laptop
shpchp 32265 0
lp 17455 0
parport 40930 3 parport_pc,ppdev,lp
usbhid 41937 0
hid 77428 1 usbhid
firewire_ohci 40180 0
firewire_core 56940 1 firewire_ohci
e100 36289 0
crc_itu_t 12627 1 firewire_core
frank@VGN-A195EP-PT:~$ iwconfig
lo no wireless extensions.

eth1 IEEE 802.11bg ESSIDff/any
Mode:Managed Channel:0 Access Point: Not-Associated
Bit Rate:0 kb/s Tx-Power=20 dBm Sensitivity=8/0
Retry limit:7 RTS thrff Fragment thrff
Power Managementff
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

eth0 no wireless extensions.

frank@VGN-A195EP-PT:~     
```

---

### Post by cariboo on 2013-06-02
Moved to General help, as FF&H is for posting problems with the forum.

---

### Post by frankramiro on 2013-06-02
Thanks man i have solved the problem and everything is running great  including Flash Player, don't ask me how i done it ,all i know i have  downloaded restricted pakages from Ubuntu and went in the update  software  ticked some items the reloaded unloaded,  my finguers hurt of  some much tempering with it,the only thing i know i'm an happy camper 
i'm happy that tried so many distros and ended up with the better( for  me of course)  an easier and windows very alike for even easier to  navigate.
thanks for trying to help appreciate.

---

