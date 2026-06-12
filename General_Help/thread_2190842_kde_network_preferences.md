---
title: "kde network preferences?"
date: 2013-11-29
forum: General Help
---

### Post by princeofnam on 2013-11-29
I'm currently thinking about using a USB wifi device because it has better range.  Unfortunately when I plug it in I can't disable the built in wifi receiver through Kubuntu 13.04.  I'm currently running a HP g7-1070us.  I tried to look in Network Preferences but I couldn't find out how to disable the built in adapter. The keyboard shortcut to do so on my laptop also doesn't work in Kubuntu for whatever reason.  I only want to do this because when I try to connect to any network they both try to connect simultaneously for whatever reason.

for the record> 

$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:1483]
    Kernel driver in use: wl
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Hewlett-Packard Company Device [103c:166a]
    Kernel driver in use: r8169
> 
 lsmod
Module                  Size  Used by
nls_iso8859_1          12713  1 
mmc_block              31626  2 
michael_mic            12612  0 
arc4                   12608  0 
rtl8187                64909  0 
mac80211              596969  1 rtl8187
eeprom_93cx6           13344  1 rtl8187
pci_stub               12622  1 
vboxpci                23194  0 
vboxnetadp             25670  0 
vboxnetflt             27613  0 
vboxdrv               320455  3 vboxnetadp,vboxnetflt,vboxpci
parport_pc             32701  0 
ppdev                  17671  0 
rfcomm                 69070  0 
bnep                   19564  2 
binfmt_misc            17468  1 
joydev                 17377  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm                   431315  0 
hp_wmi                 14062  0 
sparse_keymap          13948  1 hp_wmi
snd_hda_codec_hdmi     41276  1 
btusb                  28267  0 
snd_hda_codec_idt      50341  1 
bluetooth             371874  12 bnep,btusb,rfcomm
snd_hda_intel          48171  3 
microcode              23518  0 
snd_hda_codec         188738  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102033  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
lib80211_crypt_tkip    17619  0 
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
psmouse                97626  0 
snd_rawmidi            30095  1 snd_seq_midi
serio_raw              13413  0 
intel_ips              18470  0 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
wl                   4207474  0 
lib80211               14352  2 wl,lib80211_crypt_tkip
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29433  2 snd_pcm,snd_seq
rtsx_pci_ms            18151  0 
memstick               16760  1 rtsx_pci_ms
lpc_ich                21080  0 
cfg80211              479757  3 wl,mac80211,rtl8187
mei_me                 18421  0 
snd                    69141  17 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
mei                    77692  1 mei_me
soundcore              12680  1 snd
mac_hid                13205  0 
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
rtsx_pci_sdmmc         23527  0 
i915                  655752  10 
i2c_algo_bit           13413  1 i915
drm_kms_helper         52651  1 i915
drm                   296739  6 i915,drm_kms_helper
rtsx_pci               45546  2 rtsx_pci_ms,rtsx_pci_sdmmc
ahci                   25819  6 
libahci                31898  1 ahci
r8169                  67341  0 
mii                    13934  1 r8169
wmi                    19070  1 hp_wmi
video                  19318  1 i915

---

### Post by varunendra on 2013-12-01
I'm not sure but perhaps the "Device MAC address" field in Network Manager settings for the wifi does nicely what you exactly want. It 'Binds' the connection to the device whose MAC address is saved in that field.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=248250[/IMG]

Some other, a bit crude but sure shot workarounds may be :

[LIST=1]
[*]Disable your internal adapter from the BIOS itself when you do not want it to kick in.
[*]Disable it using command ```
rfkill block wifi
``` You may also use your internal wifi's index number instead of "wifi" (post the output of "rfkill list all" to show us its index no. in your system). Plug in your USB adapter after doing that.
[*]Try removing the "wl" driver with ```
sudo modprobe -rv wl
``` command, assuming your USB adapter uses a different driver. No driver=no active device, but the "wl" driver you are currently using sometimes gets stuck so can't always be removed so easily.
[*]Lastly, you can automate the above action by creating a udev rule to automatically disable the internal wifi (using a script containing the above commands) as soon as you plug in the USB adapter.
[/LIST]

As a side note, **the "wl" driver is usually not as good as the native "brcmsmac" driver for your particular card (14e4:4727)**. You may try the native one instead and see if it may improve the range/performance significantly enough to not need above suggestions at all. To try it, simply purge the proprietary driver that you are currently using -
```
sudo apt-get purge bcmwl-kernel-source
```
..and reboot. On next boot, check -
```
lsmod | egrep 'wl|brcm'
```
You should only see "brcmsmac" (and its supporting drivers), not "wl" in the output. If so, does it connect any better?

**PS:**
Terminal commands & outputs should always be posted within '**Code**' tags to preserve their formatting and make the post compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature. You are currently using 'Quote' tags, not 'Code' tags.

---

### Post by princeofnam on 2013-12-10
sorry for the delayed reply.  I didn't get a notification that you responded.  I've actually been upset with my internal wifi's driver issues.  I know it works well because while on Windows I can receive signal from my desk without issues.  However in ubuntu the signal is weak and cuts off frequently. I tried your advice and ran   >   lsmod | egrep 'wl|brcm' brcmsmac              562767  0  cordic                 12574  1 brcmsmac brcmutil               15618  1 brcmsmac mac80211              596969  2 b43,brcmsmac cfg80211              479757  3 b43,brcmsmac,mac80211 bcma                   46670  3 b43,brcmsmac   I still find the connection to be spotty.  Do you think I did something wrong?  I'll respond soon as to whether it's gotten any better.

---

### Post by princeofnam on 2013-12-10
okay it's still considerably weaker.  Are there any other options for my wifi card? i'm never even sure whether my usb alfa wireless device has worked from the first place either.

---

### Post by varunendra on 2013-12-11
Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

And please use code tags for posting the outputs this time (if posting them here), as recommended in my first post. :)

---

### Post by princeofnam on 2013-12-20
Thanks! I ran the script.  The output is below

```


*************** info trace ***************

***** uname -a *****

Linux Ragnarork 3.11.0-14-generic #21-Ubuntu SMP Tue Nov 12 17:04:55 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy

***** lspci *****

02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:1483]
    Kernel driver in use: bcma-pci-bridge
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Hewlett-Packard Company Device [103c:166a]
    Kernel driver in use: r8169

***** lsusb *****

Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0a5c:21b4 Broadcom Corp. BCM2070 Bluetooth 2.1 + EDR
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

***** PCMCIA Card Info *****


***** iwconfig *****

wlan0     IEEE 802.11bgn  ESSID:"NEWORLEANSHEALINGCENTER"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC address removed>   
          Bit Rate=65 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=54/70  Signal level=-56 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:37  Invalid misc:197   Missed beacon:0


***** rfkill *****

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

***** lsmod *****

brcmsmac              562767  0 
cordic                 12574  1 brcmsmac
brcmutil               15618  1 brcmsmac
b43                   387185  0 
mac80211              596969  2 b43,brcmsmac
cfg80211              479757  3 b43,brcmsmac,mac80211
ssb                    57932  1 b43
bcma                   46670  3 b43,brcmsmac

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [NEWORLEANSHEALINGCENTER] -------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           65 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    dlink-D83C:      Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 70 WPA WPA2
    AHA!:            Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 62 WPA2
    Epoch Gatherings:Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 60 WPA
    CORE USA:        Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 40 WPA2
    Fatoush 2:       Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 67
    Fatoush:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 39
    NOFC_CO:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WPA2
    NOHC_EXT:        Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 60
    IMAGINAL:        Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    cafe istanbul:   Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    Worldwide Concepts Vacations: Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 29 WPA
    cafe istanbul-guest: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 24
    MPT:             Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    NOHC:            Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 32
    *NEWORLEANSHEALINGCENTER: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 57
    Building Block : Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA2
    NETGEAR48:       Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA2
    NOHCO:           Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA2

  IPv4 Settings:
    Address:         192.168.1.169
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1



***** NetworkManager.state *****

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

***** interfaces *****

auto lo
iface lo inet loopback


***** iwlist *****

wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-33 dBm  
                    Encryption key:off
                    ESSID:"NEWORLEANSHEALINGCENTER"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000d7523f63
                    Extra: Last beacon: 172ms ago
                    IE: Unknown: 00174E45574F524C45414E534845414C494E4743454E544552
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1ABD191BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DDA90050F204104A0001101044000102103B0001031047001040C720E7318AEAB01D9E08F34E87E351102100154153555354654B20436F6D707574657220496E632E1023001C57692D46692050726F74656374656420536574757020526F757465721024000852542D41433636551042000C4341494141323030303030311054000800060050F20400011011000852542D4143363655100800022008103C0001031049000600372A000120
                    IE: Unknown: DD090010180209001C0000
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
          Cell 02 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"dlink-D83C"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000025b4e7663e
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 000A646C696E6B2D44383343
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1013FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1601000100000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B050000E1127A
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4303000000
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: DD870050F204104A0001101044000102103B00010310470010BC329E001DD811B28601C8BE196CD83C10210006442D4C696E6B1023000D442D4C696E6B20526F75746572102400084449522D3632364C1042000830303030303030301054000800060050F2040001101100084449522D3632364C10080002208C103C0001011049000600372A000120
          Cell 03 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:off
                    ESSID:"Fatoush"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    ESSID:""
                    ESSID:""
                    ESSID:""
                    ESSID:""
                    ESSID:""
                    Mode:Master
                    Extra:tsf=000000008e9271ea
                    Extra: Last beacon: 200ms ago
                    IE: Unknown: 00074661746F757368
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 05050001009007
                    IE: Unknown: 06555320010B1B1B2A010332043048602D1A0C011BFF0000000000000000000000000000000000000000000000331A0C011BFFFF0000000000000000000000000000000000000000003D16010413000000000000000000
                    IE: Unknown: 0000
                    IE: Unknown: 0000
                    IE: Unknown: 0000
                    IE: Unknown: 0000
                    IE: Unknown: 0000
                    IE: Unknown: 341616041300000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A2C0101C800000005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101860003A4000027A4000042435E0062622F00
                    IE: Unknown: DDDD00037F7F01000000001800158B00000000010000183942BDB100000000000000001000058B0000000001000000000000001000058B000000006C090000060000000C00018C000000002EC0004B10002B8B00000000000000080000000020001B8B00000000100001000000000045706F636820476174686572696E67734800218B0000000040420F000000000080841E000000000060EC530000000000C0D8A7000000000080A812010000000000366E0100000000005125020000000080F93703000000002800218B000000
          Cell 04 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"Epoch Gatherings"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000013ca1a1a70
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 001045706F636820476174686572696E6773
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F4000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC address removed>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"Worldwide Concepts Vacations"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002d2da002ba
                    Extra: Last beacon: 3116ms ago
                    IE: Unknown: 001C576F726C647769646520436F6E6365707473205661636174696F6E73
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030102
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000004000
                    IE: Unknown: DD260050F204104A0001101044000102104900140024E26002000101600000020001600100020001
          Cell 06 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"CORE USA"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002d2f206187
                    Extra: Last beacon: 972ms ago
                    IE: Unknown: 0008434F524520555341
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050401030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1ABD191BFFFFFF0001000000000000000000000000000000000000
                    IE: Unknown: 3D1601081500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD310050F204104A0001101044000102104700107CD534075490C393D91A9F51FC7D24EF103C0001031049000600372A000120
                    IE: Unknown: DD090010180201001C0000
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
          Cell 07 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"AHA!"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000026b16ff6b0
                    Extra: Last beacon: 3316ms ago
                    IE: Unknown: 000441484121
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1AAD511BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 33027E9D
                    IE: Unknown: 3D1606000400000000000000000000000000000000000000
                    IE: Unknown: 46050200010000
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0700039301750320
                    IE: Unknown: DD0E0017F20700010106B8C75D0C925D
          Cell 08 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"NOFC_CO"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002c4ac0c490
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 00074E4F46435F434F
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020004
          Cell 09 - Address: <MAC address removed>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"CORE USA SPRINT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000170b0153d3
                    Extra: Last beacon: 3728ms ago
                    IE: Unknown: 000F434F52452055534120535052494E54
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030102
                    IE: Unknown: 32040C183060
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: DD270050F204104A0001101044000102104700102880288028801880A88000304414BD46103C000101
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1AEC0117FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D1602010500000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05010091127A
                    IE: Unknown: DD07000C4307000000
          Cell 10 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"cafe istanbul"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002d2ffcbb1a
                    Extra: Last beacon: 3692ms ago
                    IE: Unknown: 000D6361666520697374616E62756C
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001300000000000000000000000000000000000000
                    IE: Unknown: DD310050F204104A000110104400010210470010D92A42D8D580A007C657CFCF66797B1C103C0001031049000600372A000120
                    IE: Unknown: DD090010180201F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 11 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:off
                    ESSID:"cafe istanbul-guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002d3014480c
                    Extra: Last beacon: 2152ms ago
                    IE: Unknown: 00136361666520697374616E62756C2D6775657374
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001300000000000000000000000000000000000000
                    IE: Unknown: DD090010180201F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 12 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"MPT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002d2f3c8235
                    Extra: Last beacon: 1140ms ago
                    IE: Unknown: 00034D5054
                    IE: Unknown: 010582848B960C
                    IE: Unknown: 030106
                    IE: Unknown: 050C000200000000000000000000
                    IE: Unknown: 2A0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"IMAGINAL"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002d2e6fd48c
                    Extra: Last beacon: 468ms ago
                    IE: Unknown: 0008494D4147494E414C
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 050401030000
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A0C501BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 33027E9D
                    IE: Unknown: 3D1601001100000000000000000000000000000000000000
                    IE: Unknown: 46050200010000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD07000393016D0320
                    IE: Unknown: DD0E0017F20700010106002436A767DA
          Cell 14 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:off
                    ESSID:"Fatoush 2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002d2d695218
                    Extra: Last beacon: 1132ms ago
                    IE: Unknown: 00094661746F7573682032
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050401030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1ABD191BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1606081100000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD310050F204104A000110104400010210470010CD4DA494B522B034ADBC582C4A39C5EF103C0001031049000600372A000120
                    IE: Unknown: DD090010180200001C0000
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
          Cell 15 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:off
                    ESSID:"NOHC_EXT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002b10284535
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 00084E4F48435F455854
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181FFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081500000000000000000000000000000000000000
                    IE: Unknown: DD7E0050F204104A00011010440001021041000100103B0001031047001078367F9FBFA93C0CFA1AD4B343E146EF1021000D4E4554474541522C20496E632E10230008574E33303030525010240008574E3330303052501042000230311054000800060050F204000110110008574E333030305250100800020084103C000101
                    IE: Unknown: DD090010180206F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 16 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:off
                    ESSID:"NOHC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002b1027fba7
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 00044E4F4843
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD6E0050F204104A00011010440001021041000100103B00010310470010BCFC50FA1AB2DAC28FA96685EE4E9F2610210005436973636F102300054531323030102400063132333435361042000234321054000800060050F2040001101100054531323030100800020084103C000101
                    IE: Unknown: DD090010180209F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 17 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"NOHCO"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002afb72d173
                    Extra: Last beacon: 404ms ago
                    IE: Unknown: 00054E4F48434F
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A2C181EFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C332C181EFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B000000000000000000000000000000000000000000
                    IE: Unknown: DD0600E04C020160
                    IE: Unknown: DD0E0050F204104A0001101044000102


***** resolv.conf *****

nameserver 127.0.1.1

***** blacklist *****

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

***** modinfo *****

filename:       /lib/modules/3.11.0-14-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
firmware:       brcm/bcm43xx_hdr-0.fw
firmware:       brcm/bcm43xx-0.fw
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     DB4E5CDF31AA9B12B2BA2C0
alias:          bcma:m04BFid0812rev18cl*
alias:          bcma:m04BFid0812rev17cl*
alias:          bcma:m04BFid0812rev11cl*
depends:        mac80211,bcma,brcmutil,cfg80211,cordic
intree:         Y
vermagic:       3.11.0-14-generic SMP mod_unload modversions 

filename:       /lib/modules/3.11.0-14-generic/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
srcversion:     E81EE4CBB6A7A689150D93D
depends:        
intree:         Y
vermagic:       3.11.0-14-generic SMP mod_unload modversions 

filename:       /lib/modules/3.11.0-14-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
license:        GPL
author:         Rafa&#322; Mi&#322;ecki
author:         Gábor Stefanik
author:         Michael Buesch
author:         Stefano Brivio
author:         Martin Langer
description:    Broadcom B43 wireless driver
srcversion:     9B797CFD1C70935B62C35EE
alias:          bcma:m04BFid0812rev1Dcl*
alias:          bcma:m04BFid0812rev18cl*
alias:          bcma:m04BFid0812rev17cl*
alias:          bcma:m04BFid0812rev11cl*
alias:          ssb:v4243id0812rev10*
alias:          ssb:v4243id0812rev0F*
alias:          ssb:v4243id0812rev0D*
alias:          ssb:v4243id0812rev0C*
alias:          ssb:v4243id0812rev0B*
alias:          ssb:v4243id0812rev0A*
alias:          ssb:v4243id0812rev09*
alias:          ssb:v4243id0812rev07*
alias:          ssb:v4243id0812rev06*
alias:          ssb:v4243id0812rev05*
depends:        ssb,bcma,mac80211,cfg80211
intree:         Y
vermagic:       3.11.0-14-generic SMP mod_unload modversions 
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)
parm:           allhwsupport:Enable support for all hardware (even it if overlaps with the brcmsmac driver) (int)

filename:       /lib/modules/3.11.0-14-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     78379A0109AF2689B4F6028
alias:          pci:v000014E4d00004350sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Csv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Bsv*sd*bc*sc*i*
alias:          pci:v000014E4d00004329sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004328sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004325sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004324sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000A8D6sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004322sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004321sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004320sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004319sv*sd*bc*sc*i*
alias:          pci:v000014A4d00004318sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004318sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004315sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004312sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004311sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004307sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004306sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004301sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.11.0-14-generic SMP mod_unload modversions 

filename:       /lib/modules/3.11.0-14-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     67ADEA6E309FDB9FC19CBCF
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004365sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004359sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004358sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004331sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000A8D8sv*sd*bc*sc*i*
alias:          pci:v000014E4d00000576sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.11.0-14-generic SMP mod_unload modversions 


***** udev rules *****

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# USB device 0x13b1:0x0020 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# USB device 0x050d:0x2103 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan2"

# USB device 0x0bda:0x8187 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan3"

# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:19.0 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"

# USB device 0x0bda:0x8189 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan4"

***** dmesg *****

[   13.779728] bcma: bus0: Found chip with id 0x4313, rev 0x01 and package 0x08
[   13.779783] bcma: bus0: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x24, class 0x0)
[   13.779824] bcma: bus0: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x18, class 0x0)
[   13.779905] bcma: bus0: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x11, class 0x0)
[   13.807397] bcma: bus0: Bus registered
[   14.305466] Support for cores revisions 0x17 and 0x18 disabled by module param allhwsupport=0. Try b43.allhwsupport=1
[   14.305481] b43: probe of bcma0:0 failed with error -524
[   14.329941] brcmsmac bcma0:0: mfg 4bf core 812 rev 24 class 0 irq 16
[   14.348755] ieee80211 phy0: registered radio enabled led device: brcmsmac-phy0:radio gpio: 243
[   20.459369] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   20.459381] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[   20.459528] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.459876] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   44.207815] wlan0: authenticate with <MAC address removed>
[   44.208616] wlan0: send auth to <MAC address removed> (try 1/3)
[   44.237069] wlan0: authenticated
[   44.238838] wlan0: associate with <MAC address removed> (try 1/3)
[   44.270754] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=8)
[   44.271506] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[   44.271511] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[   44.271521] wlan0: associated
[   44.271531] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   45.175454] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[  152.049094] brcmsmac bcma0:0: START: tid 1 is not agg'able
[  152.221114] brcmsmac bcma0:0: START: tid 1 is not agg'able
[  173.443723] brcmsmac bcma0:0: START: tid 1 is not agg'able
[  186.289379] brcmsmac bcma0:0: START: tid 1 is not agg'able
[  196.698539] brcmsmac bcma0:0: START: tid 1 is not agg'able
[  216.696958] brcmsmac bcma0:0: START: tid 1 is not agg'able
[  217.084969] brcmsmac bcma0:0: START: tid 1 is not agg'able
[  218.161131] brcmsmac bcma0:0: START: tid 1 is not agg'able
[  219.665322] brcmsmac bcma0:0: START: tid 1 is not agg'able
[  221.221567] brcmsmac bcma0:0: START: tid 1 is not agg'able
[  224.217868] brcmsmac bcma0:0: START: tid 1 is not agg'able
[  227.450318] brcmsmac bcma0:0: START: tid 1 is not agg'able
[  227.798262] brcmsmac bcma0:0: START: tid 1 is not agg'able
[  230.266676] brcmsmac bcma0:0: START: tid 1 is not agg'able
[  256.025726] brcmsmac bcma0:0: START: tid 1 is not agg'able
[  256.769852] brcmsmac bcma0:0: START: tid 1 is not agg'able
[  258.722096] brcmsmac bcma0:0: START: tid 1 is not agg'able
[  264.766809] brcmsmac bcma0:0: START: tid 1 is not agg'able
[  268.491261] brcmsmac bcma0:0: START: tid 1 is not agg'able
[  270.103504] brcmsmac bcma0:0: START: tid 1 is not agg'able
[  306.835884] brcmsmac bcma0:0: START: tid 1 is not agg'able
[  310.356003] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 0 addresses (implement)
[  310.357145] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  310.359395] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[  310.359413] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[  317.656443] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[  317.656463] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[  317.656665] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  319.637149] wlan0: authenticate with <MAC address removed>
[  319.637305] wlan0: send auth to <MAC address removed> (try 1/3)
[  319.638735] wlan0: authenticated
[  319.638989] wlan0: associating with AP with corrupt beacon
[  319.639228] wlan0: associate with <MAC address removed> (try 1/3)
[  319.647350] wlan0: RX AssocResp from <MAC address removed> (capab=0x421 status=0 aid=12)
[  319.647969] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[  319.647982] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[  319.648004] wlan0: associated
[  319.648063] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  344.472838] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  345.470478] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[  345.470496] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[  347.811756] wlan0: authenticate with <MAC address removed>
[  347.812388] wlan0: send auth to <MAC address removed> (try 1/3)
[  347.824770] wlan0: authenticated
[  347.826498] wlan0: associate with <MAC address removed> (try 1/3)
[  347.848033] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=8)
[  347.848640] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[  347.848645] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[  347.848659] wlan0: associated
[  347.972401] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[  817.502289] brcmsmac bcma0:0: START: tid 1 is not agg'able
[  946.699289] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  947.697486] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[  947.697504] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[  947.697509] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[  950.988489] wlan0: authenticate with <MAC address removed>
[  950.989416] wlan0: send auth to <MAC address removed> (try 1/3)
[  951.021338] wlan0: authenticated
[  951.023584] wlan0: associate with <MAC address removed> (try 1/3)
[  951.070462] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=8)
[  951.071034] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[  951.071040] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[  951.071054] wlan0: associated
[  958.354787] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[  994.962854] brcmsmac bcma0:0: START: tid 1 is not agg'able
[  995.754213] brcmsmac bcma0:0: START: tid 1 is not agg'able
[  999.115238] brcmsmac bcma0:0: START: tid 1 is not agg'able
[ 1032.437988] brcmsmac bcma0:0: START: tid 1 is not agg'able
[ 1032.497958] brcmsmac bcma0:0: START: tid 1 is not agg'able
[ 1076.523100] brcmsmac bcma0:0: START: tid 1 is not agg'able
[ 1076.934721] brcmsmac bcma0:0: START: tid 1 is not agg'able
[ 1082.302029] brcmsmac bcma0:0: START: tid 1 is not agg'able
[ 1083.553014] brcmsmac bcma0:0: START: tid 1 is not agg'able
[ 1127.482338] brcmsmac bcma0:0: START: tid 1 is not agg'able
[ 1139.991296] brcmsmac bcma0:0: START: tid 1 is not agg'able
[ 1145.174723] brcmsmac bcma0:0: START: tid 1 is not agg'able
[ 1247.193031] brcmsmac bcma0:0: START: tid 1 is not agg'able
[ 1261.672255] brcmsmac bcma0:0: START: tid 1 is not agg'able
[ 1262.587531] brcmsmac bcma0:0: START: tid 1 is not agg'able
[ 1300.980969] brcmsmac bcma0:0: START: tid 1 is not agg'able
[ 1315.735316] brcmsmac bcma0:0: START: tid 1 is not agg'able
[ 1809.304087] brcmsmac bcma0:0: START: tid 1 is not agg'able
[ 1922.825014] brcmsmac bcma0:0: START: tid 1 is not agg'able
[ 1923.732732] brcmsmac bcma0:0: START: tid 1 is not agg'able
[ 1997.856483] brcmsmac bcma0:0: START: tid 1 is not agg'able
[ 2022.772446] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2023.770693] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2023.770707] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[ 2023.770709] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2034.299438] wlan0: authenticate with <MAC address removed>
[ 2034.300470] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2034.309468] wlan0: authenticated
[ 2034.310564] wlan0: associate with <MAC address removed> (try 1/3)
[ 2034.314396] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=8)
[ 2034.315006] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2034.315014] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2034.315030] wlan0: associated
[ 2034.391675] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[ 2054.732085] brcmsmac bcma0:0: START: tid 1 is not agg'able
[ 2109.242774] brcmsmac bcma0:0: START: tid 1 is not agg'able
[ 2112.079114] brcmsmac bcma0:0: START: tid 1 is not agg'able
[ 2113.723300] brcmsmac bcma0:0: START: tid 1 is not agg'able
[ 2114.271333] brcmsmac bcma0:0: START: tid 1 is not agg'able

****************** done ******************


```

---

### Post by varunendra on 2013-12-20
Please try -
```
sudo rm /etc/udev/rules.d/70-persistent-net.rules
echo "blacklist b43" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Then reboot and check -
```
lsmod | egrep 'b43|brcm'
cat /etc/udev/rules.d/70-persistent-net.rules
```
You should see only "brcmsmac" in the output of first command, not "b43", and in the second command's output, you should see only two interfaces - eth0 and wlan0.

Does that help improving connectivity or making it more stable?

---

### Post by princeofnam on 2013-12-22
Connection is still a little screwy sadly, here's the output I received below:

```
xx:~$ lsmod | egrep 'b43|brcm'brcmsmac              562767  0 
cordic                 12574  1 brcmsmac
brcmutil               15618  1 brcmsmac
b43                   387185  0 
mac80211              596969  2 b43,brcmsmac
cfg80211              479757  3 b43,brcmsmac,mac80211
ssb                    57932  1 b43
bcma                   46670  3 b43,brcmsmac
xx:~$ cat /etc/udev/rules.d/70-persistent-net.rules
# This file was automatically generated by the /lib/udev/write_net_rules
# program, run by the persistent-net-generator.rules rules file.
#
# You can modify it, as long as you keep each rule on a single
# line, and change only the value of the NAME= key.


# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="98:4b:e1:c5:bc:6a", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x14e4:0x4727 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="cc:52:af:0d:10:d5", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

```

---

### Post by varunendra on 2013-12-22
> **princeofnam said:**
> Connection is still a little screwy sadly, here's the output I received below:

```
xx:~$ lsmod | egrep 'b43|brcm'brcmsmac              562767  0 
cordic                 12574  1 brcmsmac
brcmutil               15618  1 brcmsmac
**[COLOR="#FF0000"]b43[/COLOR]**                   387185  0 
mac80211              596969  2 b43,brcmsmac
cfg80211              479757  3 b43,brcmsmac,mac80211
ssb                    57932  1 b43
bcma                   46670  3 b43,brcmsmac

```

While the udev rules file is fixed, the b43 driver is still loading and conflicting with brcmsmac over resources. Have you manually added "b43" to some file to make it load? Please post back the outputs of -
```
egrep -v '#|^$' /etc/rc.local
egrep -v '#|^$' /etc/modules
grep b43 /etc/modprobe.d/blacklist.conf
```

---

### Post by princeofnam on 2013-12-22
I do remember editing a file when I tried to fix this ages ago.  Wish I could remember the exact edits.

Here's the output



```
 

dd:~$ egrep -v '#|^$' /etc/rc.local
exit 0
dd:~$ egrep -v '#|^$' /etc/modules
lp
rtc
dd:~$ grep b43 /etc/modprobe.d/blacklist.conf
# replaced by b43 and ssb.
blacklist amd76x_edacblacklist b43



 
```

---

### Post by varunendra on 2013-12-23
> **princeofnam said:**
> 
```

dd:~$ grep b43 /etc/modprobe.d/blacklist.conf
# replaced by b43 and ssb.
**blacklist amd76x_edac[COLOR="#FF0000"]blacklist b43[/COLOR]**
```

Is above a copy-paste mistake or the part highlighted in red is actually appended with the part before it like above? Please open the file /etc/modprobe.d/blacklist.conf and confirm that.

Additionally, please post the outputs of (immediately after a fresh reboot) -
```
egrep -i 'b43|BOOT_IMAGE=' /var/log/syslog
grep -R b43 /etc/modprobe.d
```

If these don't give us the clue to why b43 is loading unnecessarily, we may have to take extreme measures like renaming the b43 and ssb driver files.

By the way, could you try a Live CD/USB and see how the wifi works with the native brcmsmac driver along (confirm with **lsmod** command that b43 isn't loading there too)? All the exercise we are doing is to make that driver work properly. The live session can confirm whether we are doing the right thing or not.

---

### Post by princeofnam on 2013-12-25
Yup.  The last paragraph reads ```
# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edacblacklist b43
```

here is the grep output ```


egrep -i 'b43|BOOT_IMAGE=' /var/log/syslog
Dec 25 12:00:26 Ragnarork kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.11.0-14-generic root=UUID=173cf438-c9f3-490a-a50e-aead4d1a09ab ro quiet splash vt.handoff=7
Dec 25 12:00:26 Ragnarork kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.11.0-14-generic root=UUID=173cf438-c9f3-490a-a50e-aead4d1a09ab ro quiet splash vt.handoff=7
Dec 25 12:00:26 Ragnarork kernel: [    1.449135] pci 0000:00:1c.2:   bridge window [mem 0xb3400000-0xb43fffff]
Dec 25 12:00:26 Ragnarork kernel: [    1.888256] pci 0000:00:1c.2:   bridge window [mem 0xb3400000-0xb43fffff]
Dec 25 12:00:26 Ragnarork kernel: [    1.888853] pci_bus 0000:04: resource 1 [mem 0xb3400000-0xb43fffff]
Dec 25 12:00:26 Ragnarork kernel: [   14.756318] Support for cores revisions 0x17 and 0x18 disabled by module param allhwsupport=0. Try b43.allhwsupport=1
Dec 25 12:00:26 Ragnarork kernel: [   14.756336] b43: probe of bcma0:0 failed with error -524
sushi@Ragnarork:~$ grep -R b43 /etc/modprobe.d
/etc/modprobe.d/blacklist.conf:# replaced by b43 and ssb.
/etc/modprobe.d/blacklist.conf:blacklist amd76x_edacblacklist b43
/etc/modprobe.d/blacklist.conf~:# replaced by b43 and ssb.




```

Unfortunately I cant demo whether the Live CD version is working or not as I'm currently at home where the WiFi is quite ample.  I apologize for the inconvenience and I appreciate your help through this process.

---

### Post by varunendra on 2013-12-26
> **princeofnam said:**
> ```
blacklist amd76x_edac[COLOR="#FF0000"]**blacklist b43**[/COLOR]
```

Open the file with root access -
```
gksu gedit /etc/modprobe.d/blacklist.conf
```
*[NOTE: Replace 'gksu' with 'kdesudo' or simply 'sudo' if using KDE, also, 'gedit' with whatever text editor you are using]*
And edit the above quoted line to split it into two separate lines, so that it looks like -
```
blacklist amd76x_edac
blacklist b43
```
then save and close the file. Reboot and check -
```
lsmod | egrep 'b43|brcm'
```
You should see only brcmsmac and related drivers, but no b43 in the output. If so, is the connection any better?

---

### Post by princeofnam on 2014-01-10
```
brcmsmac              562767  0 
cordic                 12574  1 brcmsmac
brcmutil               15618  1 brcmsmac
mac80211              596969  1 brcmsmac
cfg80211              479757  2 brcmsmac,mac80211
bcma                   46670  2 brcmsmac


```

Yup! It's just as you described.  I think it worked.  It's hard to tell since connectivity can be subjective but I've felt good connectivity since I got back.

---

### Post by princeofnam on 2014-01-11
Checking again this morning.  Connectivity is definitely better.  Thanks for the help.  Can't believe it was as simple as that.

---

### Post by varunendra on 2014-01-13
If it is still serving you good, please mark the thread as [SOLVED]. Thanks! :)

---

### Post by princeofnam on 2014-02-22
Hi!  I just wanted to bump this thread as I'm still having trouble with my ubuntu wireless.  I had to boot into Windows to use the wifi.  Does anyone else have any suggestions? I noticed some error messages when I rebooted but I wasn't sure how to access them as they were only visible on the terminal right before reboot.  I did see the words "brms_mac" though which led me to suspect something was wrong

---

### Post by varunendra on 2014-02-24
princeofnam, just noticed your last post.

How long the solution worked? Did the problem return after some update?

Please show us a fresh report created by the "wireless_script", as well as the output of -
```
dmesg | egrep -i 'brms|error'
```

And take a look yourself at these logs and post back if you see any suspicious lines -
/var/log/syslog
/var/log/dmesg

---

