---
title: "Wired and Wireless internet not working in Ubuntu 14.04"
date: 2015-09-12
forum: General Help
---

### Post by vaibhav8 on 2015-09-12
[COLOR=#111111][FONT=Ubuntu]I have a Windows 7 machine along with with Ubuntu 14.04 installed on it. The wired and wireless internet both don't seem to be working on Ubuntu. I am pasting the outputs of few commands.

[/FONT][/COLOR]1. uname-a 
    
    Linux vaibhav-HP-Compaq-dc7900-Convertible-Minitower 3.16.0-30-generic #40~14.04.1-Ubuntu SMP Thu Jan 15 17:43:14 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
    
    
    2. lspci -nnk | grep -iA2 net
    
    00:19.0 Ethernet controller [0200]: Intel Corporation 82567LM-3 Gigabit Network Connection [8086:10de] (rev 02)
    	Subsystem: Hewlett-Packard Company Device [103c:3035]
    	Kernel driver in use: e1000e
    
    
    3. lsusb
    
    Bus 002 Device 002: ID 7392:7811 Edimax Technology Co., Ltd EW-7811Un 802.11n Wireless Adapter [Realtek RTL8188CUS]
    Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
    Bus 008 Device 002: ID 046d:c534 Logitech, Inc. 
    Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 001 Device 003: ID 1871:0142 Aveo Technology Corp. 
    Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
    Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 004 Device 002: ID 046d:c247 Logitech, Inc. 
    Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    
    4. lsmod
    Module                  Size  Used by
    ctr                    13049  1 
    ccm                    17773  1 
    bnep                   19624  2 
    rfcomm                 69509  0 
    bluetooth             446409  10 bnep,rfcomm
    6lowpan_iphc           18702  1 bluetooth
    arc4                   12608  2 
    rtl8192cu              67741  0 
    rtl_usb                18448  1 rtl8192cu
    rtlwifi                64255  2 rtl_usb,rtl8192cu
    rtl8192c_common        53172  1 rtl8192cu
    mac80211              652718  3 rtl_usb,rtlwifi,rtl8192cu
    cfg80211              494330  2 mac80211,rtlwifi
    uvcvideo               81073  0 
    videobuf2_vmalloc      13216  1 uvcvideo
    videobuf2_memops       13362  1 videobuf2_vmalloc
    videobuf2_core         59104  1 uvcvideo
    v4l2_common            15681  1 videobuf2_core
    joydev                 17393  0 
    videodev              153793  3 uvcvideo,v4l2_common,videobuf2_core
    snd_usb_audio         161350  1 
    media                  21903  2 uvcvideo,videodev
    snd_usbmidi_lib        29828  1 snd_usb_audio
    snd_hda_codec_analog    15049  1 
    snd_hda_codec_generic    68937  1 snd_hda_codec_analog
    snd_hda_codec_hdmi     47548  1 
    gpio_ich               13586  0 
    hp_wmi                 14109  0 
    sparse_keymap          13948  1 hp_wmi
    dm_multipath           22843  0 
    coretemp               13441  0 
    scsi_dh                14882  1 dm_multipath
    kvm                   452043  0 
    serio_raw              13483  0 
    snd_hda_intel          30469  5 
    snd_hda_controller     31056  1 snd_hda_intel
    snd_hda_codec         139682  5 snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller,snd_hda_codec_analog
    snd_seq_midi           13564  0 
    snd_seq_midi_event     14899  1 snd_seq_midi
    snd_hwdep              17698  2 snd_usb_audio,snd_hda_codec
    lpc_ich                21093  0 
    snd_rawmidi            30876  2 snd_usbmidi_lib,snd_seq_midi
    snd_pcm               104112  5 snd_usb_audio,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
    snd_seq                63074  2 snd_seq_midi_event,snd_seq_midi
    snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
    snd_timer              29562  2 snd_pcm,snd_seq
    snd                    79468  25 snd_usb_audio,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_hda_codec_analog
    soundcore              15047  2 snd,snd_hda_codec
    mei_me                 19696  0 
    mei                    87875  1 mei_me
    shpchp                 37047  0 
    wmi                    19193  1 hp_wmi
    tpm_infineon           17131  0 
    mac_hid                13227  0 
    parport_pc             32741  0 
    ppdev                  17671  0 
    lp                     17759  0 
    parport                42348  3 lp,ppdev,parport_pc
    hid_generic            12559  0 
    usbhid                 52616  0 
    hid                   110426  2 hid_generic,usbhid
    psmouse               106561  0 
    ahci                   34062  2 
    libahci                32424  1 ahci
    e1000e                226396  0 
    ptp                    19395  1 e1000e
    pps_core               19382  1 ptp
    dm_mirror              22135  0 
    pata_acpi              13053  0 
    dm_region_hash         20862  1 dm_mirror
    floppy                 69662  0 
    dm_log                 18411  2 dm_region_hash,dm_mirror
    
    5. iwconfig
    eth0      no wireless extensions.
    
    lo        no wireless extensions.
    
    wlan1     IEEE 802.11bgn  ESSID:"Vaibhavs1985"  
              Mode:Managed  Frequency:2.437 GHz  Access Point: 0C:47:3D:73:E9:28   
              Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
              Retry short limit:7   RTS thr=2347 B   Fragment thr:off
              Encryption key:off
              Power Management:off
              Link Quality=70/70  Signal level=-32 dBm  
              Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
              Tx excessive retries:0  Invalid misc:1   Missed beacon:0
    
    6. ifconfig -a
    eth0      Link encap:Ethernet  HWaddr 18:a9:05:f1:9f:9c  
              UP BROADCAST MULTICAST  MTU:1500  Metric:1
              RX packets:0 errors:0 dropped:0 overruns:0 frame:0
              TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:1000 
              RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
              Interrupt:19 Memory:f3100000-f3120000 
    
    lo        Link encap:Local Loopback  
              inet addr:127.0.0.1  Mask:255.0.0.0
              inet6 addr: ::1/128 Scope:Host
              UP LOOPBACK RUNNING  MTU:65536  Metric:1
              RX packets:265 errors:0 dropped:0 overruns:0 frame:0
              TX packets:265 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:0 
              RX bytes:19609 (19.6 KB)  TX bytes:19609 (19.6 KB)
    
    wlan1     Link encap:Ethernet  HWaddr 74:da:38:3b:45:f6  
              inet addr:192.168.0.13  Bcast:192.168.0.255  Mask:255.255.255.0
              inet6 addr: 2604:2d80:4018:c070:76da:38ff:fe3b:45f6/64 Scope:Global
              inet6 addr: fe80::76da:38ff:fe3b:45f6/64 Scope:Link
              inet6 addr: 2604:2d80:4018:c070:6cea:fc5d:a0dc:c17e/64 Scope:Global
              UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
              RX packets:464 errors:0 dropped:0 overruns:0 frame:0
              TX packets:219 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:1000 
              RX bytes:65281 (65.2 KB)  TX bytes:33895 (33.8 KB)
    
    7. cat /etc/resolv.conf
    # Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
    #     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
    nameserver 127.0.1.1
    search hitronhub.home


Can anybody help me resolve this issue?


Thanks

---

### Post by nknwn on 2015-09-12
Have you tried connecting wifi from the command line?

eg
sudo nmcli dev wifi connect yournetworkssid password yourwifipassword

---

### Post by SeijiSensei on 2015-09-12
Are you trying to connect both the wireless and Ethernet interfaces at the same time?  Often that generates routing problems, so the network fails to work properly.  Try disabling the wireless adapter, rebooting, and connecting only over the Ethernet cable.  Does that work?  If so, try the reverse.

The Intel Ethernet adapter is well-supported in Linux so it isn't a driver issue.

Also, according to this entry, your wifi connection works fine:
```

wlan1 Link encap:Ethernet HWaddr 74:da:38:3b:45:f6
inet addr:192.168.0.13 Bcast:192.168.0.255 Mask:255.255.255.0

```

---

### Post by grahammechanical on 2015-09-12
Let us go through some of that information.

eth0 = ethernet adapter when connected to the router it would be called a wired connection. wlan1 = WiFi adapter.

iwconfig shows wlan1 connected to wireless access point  Vaibhavs1985 with a transmission (tx) strength of 20dBm and a signal strength of -32dBM. So, the WiFi adapter is working, it has a driver and it is connected to a wireless access point (your router?).

ifconfig -a shows eth0 as UP BROADCAST MULTICAST. Which means that the ethernet adapter is switched and working but not connected to the router.

ifconfig -a shows wlan1 as UP BROADCAST RUNNING MULTICAST. Which means that the Wireless (WiFi) adapter is switched on; it has a driver and it is connected to a wireless access point (router?). At the time that ifconfig -a was run wlan1 had received (RX) 65281 bytes and transmitted (TX) 33895 bytes of data to and from the wireless access point.

I would conclude that wired/ethernet adapter is working but not connected and the wireless adapter is also working and connected in Ubuntu. So, the problems is elsewhere. Is the wireless access point connected to an ISP?

There is something that is confusing me. Why is the wireless adapter labelled wlan1. If it is the only wireless adapter it should be labelled wlan0. By naming it wlan1 it might indicate that there are two wireless adapters and one of them (wlan0) is switched off completely.

Regards.

---

