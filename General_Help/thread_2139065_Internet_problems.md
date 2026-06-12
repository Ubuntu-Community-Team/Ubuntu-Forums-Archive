---
title: "Internet problems"
date: 2013-04-25
forum: General Help
---

### Post by Sam Mills on 2013-04-25
I'm running Xubuntu 13.04, (fresh install) but the problem started with 12.10 about 3 weeks ago. It says I'm connected, but web pages load very slowly, if at all. Firefox and Chrome both act the same way. Funny thing is, I've been using this laptop for 2 years without any issues in linux. Has always ran perfectly. It's a Dell Latitude E5520 with all Intel chipsets. I know Intel is very linux friendly and should work well.

Btw, I dual boot with windows and when I went into windows to check if there was any problems there, internet worked perfectly and fast. Are there any .config files I can delete and regenerate? Seems strange that all of a sudden internet is so spotty.

---

### Post by Sam Mills on 2013-04-26
I just tried a live USB with Lubuntu 13.04 on it, and the problem still persists. Sometimes it is quick, other times it is very slow or can't load the page at all. Here is the output of lspci:
```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b4)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b4)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b4)
00:1c.6 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 7 (rev b4)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
02:00.0 Network controller: Intel Corporation Centrino Ultimate-N 6300 (rev 35)
09:00.0 FireWire (IEEE 1394): O2 Micro, Inc. 1394 OHCI Compliant Host Controller (rev 05)
09:00.1 SD Host controller: O2 Micro, Inc. Integrated MMC/SD controller (rev 05)
09:00.2 Mass storage controller: O2 Micro, Inc. O2 Flash Memory Card (rev 05)
0a:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5761 Gigabit Ethernet PCIe (rev 10)



```

---

### Post by Sam Mills on 2013-04-26
It seems that other people have had this problem too, using -

Network controller: Intel Corporation Centrino Ultimate-N 6300 (rev 35)

I'm searching for an answer, but still no luck.

---

### Post by varunendra on 2013-04-26
> **Sam Mills said:**
> It seems that other people have had this problem too..

Any links you might have found and followed instructions from?

Please follow the "Wireless Script" link in my signature and post back the diagnostics report using any of the methods in the linked post.

---

### Post by Sam Mills on 2013-04-27
Here it is

```
**** uname -a ****


Linux fake-name 3.8.0-19-generic #29-Ubuntu SMP Wed Apr 17 18:16:28 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


**** lsb-release ****


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=13.04
DISTRIB_CODENAME=raring
DISTRIB_DESCRIPTION="Ubuntu 13.04"


**** lspci ****


02:00.0 Network controller [0280]: Intel Corporation Centrino Ultimate-N 6300 [8086:422b] (rev 35)
    Subsystem: Intel Corporation Centrino Ultimate-N 6300 3x3 AGN [8086:1121]
    Kernel driver in use: iwlwifi
--
0a:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5761 Gigabit Ethernet PCIe [14e4:1681] (rev 10)
    Subsystem: Dell Device [1028:049a]
    Kernel driver in use: tg3


**** lsusb ****


Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 08ff:2810 AuthenTec, Inc. AES2810
Bus 002 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 004: ID 04d9:1603 Holtek Semiconductor, Inc. Keyboard
Bus 002 Device 005: ID 046d:c52f Logitech, Inc. Wireless Mouse M305


**** iwconfig ****


wlan0     IEEE 802.11abgn  ESSID:"HOME-2FF2"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC address removed>   
          Bit Rate=130 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=65/70  Signal level=-45 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:462  Invalid misc:0   Missed beacon:0



**** rfkill ****


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


**** lsmod ****


Module                  Size  Used by
pci_stub               12622  1 
vboxpci                23194  0 
vboxnetadp             25670  0 
vboxnetflt             23479  0 
vboxdrv               320372  3 vboxnetadp,vboxnetflt,vboxpci
rfcomm                 42641  0 
bnep                   18036  2 
bluetooth             228619  10 bnep,rfcomm
snd_hda_codec_hdmi     36913  1 
snd_hda_codec_idt      70256  1 
joydev                 17377  0 
arc4                   12615  2 
iwldvm                241834  0 
mac80211              606457  1 iwldvm
coretemp               13355  0 
kvm_intel             132891  0 
kvm                   443165  1 kvm_intel
snd_hda_intel          39619  3 
snd_hda_codec         136453  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
ghash_clmulni_intel    13259  0 
snd_hwdep              13602  1 snd_hda_codec
aesni_intel            55399  1 
aes_x86_64             17255  1 aesni_intel
xts                    12885  1 aesni_intel
lrw                    13257  1 aesni_intel
gf128mul               14951  2 lrw,xts
ablk_helper            13597  1 aesni_intel
cryptd                 20373  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
ppdev                  17073  0 
snd_seq_midi           13324  0 
parport_pc             28152  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  1 snd_seq_midi
wmi                    19070  1 dell_wmi
mac_hid                13205  0 
i915                  600351  2 
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29425  2 snd_pcm,snd_seq
video                  19390  1 i915
drm_kms_helper         49394  1 i915
snd                    68876  16 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
iwlwifi               173477  1 iwldvm
drm                   286313  3 i915,drm_kms_helper
dell_laptop            17369  0 
cfg80211              510937  3 iwlwifi,mac80211,iwldvm
dcdbas                 14397  1 dell_laptop
mei                    41158  0 
lpc_ich                17061  0 
i2c_algo_bit           13413  1 i915
soundcore              12680  1 snd
lp                     17759  0 
psmouse                95870  0 
parport                46345  3 lp,ppdev,parport_pc
serio_raw              13215  0 
microcode              22881  0 
hid_generic            12540  0 
usbhid                 47074  0 
hid                   101002  2 hid_generic,usbhid
firewire_ohci          40103  0 
tg3                   153796  0 
sdhci_pci              18590  0 
firewire_core          64508  1 firewire_ohci
sdhci                  32522  1 sdhci_pci
ahci                   25731  3 
libahci                31364  1 ahci
ptp                    18621  1 tg3
crc_itu_t              12707  1 firewire_core
pps_core               14080  1 ptp


**** nm-tool ****



NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [HOME-2FF2] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           130 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    DIRECT-BQ[BD]E5900: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 89 WPA2
    HOME-8742:       Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 79 WPA WPA2
    *HOME-2FF2:      Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 76 WPA WPA2
    cucinottanetwork:Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    Cisco13762:      Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 22
    WIN_e72d:        Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    HOME-D662:       Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA2
    get away from me:Infra, <MAC address removed>, Freq 2442 MHz, Rate 54 Mb/s, Strength 20 WPA

  IPv4 Settings:
    Address:         10.0.0.4
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.0.1

    DNS:             75.75.75.75
    DNS:             75.75.76.76




**** NetworkManager.state ****


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


**** NetworkManager.conf ****


[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false


**** NetworkManager.conf-10.04 ****




**** interfaces ****


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


**** iwlist ****


wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=65/70  Signal level=-45 dBm  
                    Encryption key:on
                    ESSID:"HOME-2FF2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000ecc10a113f
                    Extra: Last beacon: 100ms ago
                    IE: Unknown: 0009484F4D452D32464632
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0106
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A0C0016FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D1601000500000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0501002A127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: DD7D0050F204104A0001101044000102103B000103104700102880288028801880A880001DD4FB2FF010210005415252495310230006544738363247102400065254323836301042000831323334353637381054000800060050F204000110110012415252495320544738363220526F75746572100800020084103C000101
          Cell 02 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"DIRECT-BQ[BD]E5900"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000cd66bdc102
                    Extra: Last beacon: 4856ms ago
                    IE: Unknown: 00124449524543542D42515B42445D4535393030
                    IE: Unknown: 01088C1218243048606C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A2C1019FF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080000000000000000000000000000000000000000
                    IE: Unknown: DD09001018020100440000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD750050F204104A0001101044000102103B000103104700102221020304050607080932144A4A65891021000842726F6164636F6D10230006536F66744150102400013010420001301054000800060050F2040001101100095B42445D4535393030100800020188103C0001011049000600372A000120
          Cell 03 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"HOME-8742"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000ecd23101d7
                    Extra: Last beacon: 4832ms ago
                    IE: Unknown: 0009484F4D452D38373432
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0106
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A0C0016FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D1601000500000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0501002E127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: DD7D0050F204104A0001101044000102103B000103104700102880288028801880A880001DD649874010210005415252495310230006544738363247102400065254323836301042000831323334353637381054000800060050F204000110110012415252495320544738363220526F75746572100800020084103C000101
          Cell 04 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"HOME-AFB2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000066cb5f1a8b
                    Extra: Last beacon: 4284ms ago
                    IE: Unknown: 0009484F4D452D41464232
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A0C0016FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D160B000400000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05020076127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: DD7D0050F204104A0001101044000102103B000103104700102880288028801880A880001DD64BAFB010210005415252495310230006544738363247102400065254323836301042000831323334353637381054000800060050F204000110110012415252495320544738363220526F75746572100800020084103C000101
          Cell 05 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"cucinottanetwork"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000012c26dae1e6
                    Extra: Last beacon: 4288ms ago
                    IE: Unknown: 0010637563696E6F7474616E6574776F726B
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 32040C183060
                    IE: Unknown: 070C5553200101110209140B0111
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD270050F204104A0001101044000102104700102880288028801880A880001DCF3FCD10103C000101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A6C0017FFFFFF00000000000000000000000000000F0000000000
                    IE: Unknown: 3D160B000500000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101034003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0503004A127A
                    IE: Unknown: DD07000C4307000000



**** resolv ****


# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
search hsd1.ga.comcast.net


**** blacklist.conf ****


# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac


**** dmesg ****


[    0.524003] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: d490763cc418e29de79f40a5aa7d97747ec8882c'
[    0.578227] tg3.c:v3.128 (December 03, 2012)
[    0.612646] tg3 0000:0a:00.0 eth0: Tigon3 [partno(BCM95761) rev 5761100] (PCI Express) MAC address <MAC address removed>
[    0.612650] tg3 0000:0a:00.0 eth0: attached PHY is 5761 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
[    0.612652] tg3 0000:0a:00.0 eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    0.612654] tg3 0000:0a:00.0 eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   13.374253] iwlwifi 0000:02:00.0: irq 44 for MSI/MSI-X
[   13.396322] wmi: Mapper loaded
[   13.562667] iwlwifi 0000:02:00.0: loaded firmware version 9.221.4.1 build 25532
[   13.578552] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   13.578556] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   13.578558] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   13.578559] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TESTMODE enabled
[   13.578561] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_P2P disabled
[   13.578563] iwlwifi 0000:02:00.0: Detected Intel(R) Centrino(R) Ultimate-N 6300 AGN, REV=0x74
[   13.578620] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[   13.608483] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   21.689135] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[   21.696002] iwlwifi 0000:02:00.0: Radio type=0x0-0x3-0x1
[   22.059230] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[   22.066034] iwlwifi 0000:02:00.0: Radio type=0x0-0x3-0x1
[   22.318583] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.319053] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.321885] tg3 0000:0a:00.0: irq 47 for MSI/MSI-X
[   28.958915] wlan0: authenticate with <MAC address removed>
[   28.989897] wlan0: send auth to <MAC address removed> (try 1/3)
[   28.992977] wlan0: authenticated
[   28.994764] wlan0: associate with <MAC address removed> (try 1/3)
[   29.003812] wlan0: RX AssocResp from <MAC address removed> (capab=0xc11 status=0 aid=1)
[   29.008196] wlan0: associated
[   29.008233] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


**************** done ********************


```

---

### Post by varunendra on 2013-04-27
> **Sam Mills said:**
> ```

wlan0     IEEE 802.11abgn  ESSID:"HOME-2FF2"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC address removed>   
          Bit Rate=**[COLOR="#FF0000"]130 Mb/s[/COLOR]**   Tx-Power=15 dBm
...
...
                    ESSID:"HOME-2FF2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; **[COLOR="#000080"]54 Mb/s[/COLOR]**
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s

```

It seems your access point supports a maximum speed of 54Mbps ^^, so you don't need N-channel that your adapter supports (provides higher speeds, but is still buggy on Linux).

Accordingly, please try disabling N-Channel -
```
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi 11n_disable=1
```

It is a temporary change and will be lost at reboot. If it seems to help, we can make it permanent with -
```
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
```

---

### Post by HermanAB on 2013-04-27
Also test your DNS using dig. If slow, compare resolv.conf with Windows network settings.

---

### Post by Sam Mills on 2013-04-27
Thanks varunendra, but after doing

```
 sudo modprobe -rfv iwlwifi
```

I get

```
FATAL: Module iwlwifi is in use.
```

---

### Post by varunendra on 2013-04-28
> **Sam Mills said:**
> Thanks varunendra, but after doing

```
 sudo modprobe -rfv iwlwifi
```

I get

```
FATAL: Module iwlwifi is in use.
```

Then forget the modprobe commands and go ahead directly with the third command that makes it a permanent setting. Reboot and see if it helps. If not, we can either leave the configuration file as a measure to reduce an extra point of doubt, or delete it if you wish, to restore the original setting.

---

### Post by Sam Mills on 2013-04-28
It seems to be OK now. Not lightning fast, but decent. Thanks for your help and we'll see if this holds up.

---

### Post by Sam Mills on 2013-04-28
Well, the joy only lasted a few minutes. It's back to where it was before. Sometimes it will be OK, and then slow to a crawl or not be able to load any web pages. I'm stuck.

---

### Post by varunendra on 2013-04-29
Please also try what HermanAB suggested. Recommended DNS for a test is google's 8.8.8.8 and 8.8.4.4

Although changing DNS only helps where page lookups are slow, not where entire loading is slow even after they are found.

If DNS changes don't help, let's try another parameter -
```
echo "options iwlwifi 11n_disable=1 **swcrypto=1**" | sudo tee /etc/modprobe.d/iwlwifi.conf
```
Reboot and see if things improve. If not, let's take a look at :
```
iwconfig
ifconfig
nm-tool
grep -R [0-9a-zA-Z] /sys/module/iwlwifi/parameters/
ping -c4 google.com
```

---

### Post by Sam Mills on 2013-05-02
I appreciate all of your help. Still having some issues. Internet works and sometimes fast, but is not consistant. Here is the output of all the commands you listed.

```
sam@sammills:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"HOME-2FF2"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1D:D4:FB:2F:F0   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=61/70  Signal level=-49 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:33   Missed beacon:0

sam@sammills:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr d0:67:e5:32:c0:72  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1867 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1867 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:188589 (188.5 KB)  TX bytes:188589 (188.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:24:d7:ea:ed:58  
          inet addr:10.0.0.4  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::224:d7ff:feea:ed58/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6717 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6973 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5511072 (5.5 MB)  TX bytes:1596502 (1.5 MB)

sam@sammills:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        D0:67:E5:32:C0:72

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [HOME-2FF2] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        00:24:D7:EA:ED:58

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    HOME-8742:       Infra, 00:1D:D6:49:87:40, Freq 2412 MHz, Rate 54 Mb/s, Strength 85 WPA WPA2
    DIRECT-BQ[BD]E5900: Infra, 32:14:4A:4A:65:89, Freq 2412 MHz, Rate 54 Mb/s, Strength 80 WPA2
    *HOME-2FF2:      Infra, 00:1D:D4:FB:2F:F0, Freq 2412 MHz, Rate 54 Mb/s, Strength 72 WPA WPA2
    HOME-6FD2:       Infra, 00:1D:D4:40:6F:D0, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    WIN_e72d:        Infra, 4C:17:EB:3B:E7:2C, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    Cisco13762:      Infra, C8:D7:19:75:EE:71, Freq 2437 MHz, Rate 54 Mb/s, Strength 22

  IPv4 Settings:
    Address:         10.0.0.4
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.0.1

    DNS:             75.75.75.75
    DNS:             75.75.76.76


sam@sammills:~$ grep -R [0-9a-zA-Z] /sys/module/iwlwifi/parameters/
/sys/module/iwlwifi/parameters/5ghz_disable:N
/sys/module/iwlwifi/parameters/swcrypto:1
/sys/module/iwlwifi/parameters/power_save:N
/sys/module/iwlwifi/parameters/auto_agg:Y
/sys/module/iwlwifi/parameters/led_mode:0
/sys/module/iwlwifi/parameters/amsdu_size_8K:1
/sys/module/iwlwifi/parameters/bt_ch_inhibition:Y
/sys/module/iwlwifi/parameters/fw_restart:1
/sys/module/iwlwifi/parameters/bt_coex_active:Y
/sys/module/iwlwifi/parameters/11n_disable:1
/sys/module/iwlwifi/parameters/antenna_coupling:0
/sys/module/iwlwifi/parameters/plcp_check:Y
/sys/module/iwlwifi/parameters/wd_disable:1
/sys/module/iwlwifi/parameters/power_level:0
sam@sammills:~$ ping -c4 google.com
PING google.com (74.125.134.113) 56(84) bytes of data.
64 bytes from gg-in-f113.1e100.net (74.125.134.113): icmp_req=1 ttl=48 time=16.2 ms
64 bytes from gg-in-f113.1e100.net (74.125.134.113): icmp_req=2 ttl=48 time=31.0 ms
64 bytes from gg-in-f113.1e100.net (74.125.134.113): icmp_req=3 ttl=48 time=20.1 ms
64 bytes from gg-in-f113.1e100.net (74.125.134.113): icmp_req=4 ttl=48 time=14.4 ms

--- google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3005ms
rtt min/avg/max/mdev = 14.480/20.465/31.060/6.448 ms


```

---

### Post by Sam Mills on 2013-05-03
Changing my DNS seems to have helped speed up the loading of web pages. But my resolv.conf file does not look right.
```
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 8.8.8.8
nameserver 8.8.4.4nameserver 127.0.1.1
search hsd1.ga.comcast.net


```
Should I leave it alone?

---

### Post by Sam Mills on 2013-05-03
After doing more research, it seems I'm not the only Comcast customer using Ubuntu that is experiencing this problem. Ubuntu Geek has an article about dnsmasq that should resolve any issues. [http://www.ubuntugeek.com/how-to-disable-dnsmasq-in-ubuntu-12-04precise.html](http://www.ubuntugeek.com/how-to-disable-dnsmasq-in-ubuntu-12-04precise.html)

I'm going to hold off marking as "solved", but everything is running much better. Thankfully, I can put windows back to sleep for now. Thank you very much for your help.

---

### Post by varunendra on 2013-05-03
> **Sam Mills said:**
> Changing my DNS seems to have helped speed up the loading of web pages. But my resolv.conf file does not look right.
```
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 8.8.8.8
nameserver 8.8.4.4nameserver 127.0.1.1
search hsd1.ga.comcast.net


```
Should I leave it alone?

It looks like you directly edited the /etc/resolv.conf file, which used to be the correct way in earlier versions, but not since 'resolvconf' package has been added by default with Network Manager.

As the header of the file says, it seems to have been overwritten by resolvconf program. You should -
(A) Either set the DNS in Network Manager itself (set the connection to "Automatic (DHCP) address only", so that you are allowed to set the DNS yourself), or
(B) Remove the resolvconf package to return to the traditional method of configuring DNS. That is, directly editing the /etc/resolv.conf file.

As an aside, set IPv6 to "Ignore" in Network Manager. To permanently disable it, add these lines to your /etc/sysctl.conf file -
> # disable IPv6
net.ipv6.conf.all.disable_ipv6=1
net.ipv6.conf.default.disable_ipv6=1
net.ipv6.conf.lo.disable_ipv6=1
..which, apart from gui, can also be done with a single command -
```
echo -e "\n# disable IPv6\nnet.ipv6.conf.all.disable_ipv6=1\nnet.ipv6.conf.default.disable_ipv6=1\nnet.ipv6.conf.lo.disable_ipv6=1" | sudo tee -a /etc/sysctl.conf
```

Once done, please post -
```
nm-tool
ifconfig
ping -c4 google.com
cat /etc/resolv.conf
```
The driver parameters seem okay to me, although we can do an experiment with "bt_coex_active" parameter if required.

**EDIT:** You're fast! (post #15, I didn't see it when started writing this one..:P)
It looks like the dnsmasq fix has more or less the same effect as removing the 'resolvconf' package. But I need to read it more carefully to be sure.

---

### Post by Sam Mills on 2013-05-03
Thanks, I did 
```

gksudo gedit /etc/resolvconf/resolv.conf.d/head
```
to make the dns changes. Was that not OK? I'll also try what you suggest above.

---

### Post by Sam Mills on 2013-05-03
After removing resolvconf, I tried manually, but internet was very bad. I went back and did what I posted in my previous post. My resolv.conf looks wonky, but it works well. Again, here is what it looks like:

```

# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8) #     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN nameserver 8.8.8.8 nameserver 8.8.4.4nameserver 127.0.1.1 search hsd1.ga.comcast.net


```
But it works great, so I'm leaving it. I'm running out of patience for now.

---

### Post by varunendra on 2013-05-03
> **Sam Mills said:**
> Thanks, I did 
```

gksudo gedit /etc/resolvconf/resolv.conf.d/head
```
to make the dns changes. Was that not OK?
Nope, it's just header. The DNS will be picked up from Network Manager, and will be used as Active DNS (it shows up in nm-tool output and in '/run/nm-dns-dnsmasq.conf' file, if resolvconf package is installed and active.)

That's why the DNS has to be defined in NM, not anywhere else if resolvconf is working.

The disabling of IPv6 will either have a good effect, or no effect at all, since you are using IPv4 to connect.

But of course you don't need to try any of these if you are getting satisfactory speeds with the dnsmasq fix :)

---

