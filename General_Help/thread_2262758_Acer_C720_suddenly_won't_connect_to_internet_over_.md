---
title: "Acer C720 suddenly won't connect to internet over WiFi or tether?"
date: 2015-01-27
forum: General Help
---

### Post by harry28 on 2015-01-27
I recently installed HugeGreensBugs Ubuntu 14.04 on my Acer C720 Chromebook since it fixes all of the problem Ubuntu has running on a Chromebook . It has been running great for the last week or so but today when I turned it on I cannot connect to my collrge s WiFi (the main one I need to use) ,over usb tether from my android tablet and my phones hotspot. When I click onto the colleges WiFi it connects fine however when going into the the browser it says 'Problem Loading Page' in the tab bar and loads a page saying server not found. It does the same thing when I tether my android tablet and try using my phones hotspot. Is there any way I can fix this?

---

### Post by kc1di on 2015-01-27
can you go to a terminal and type the following commands and post the outputs here.
```
rfkill list all
lspci
lsmod
```

---

### Post by harry28 on 2015-01-28
rfkill list all:

```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


```

lspci

```
00:00.0 Host bridge: Intel Corporation Haswell-ULT DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 09)
00:03.0 Audio device: Intel Corporation Haswell-ULT HD Audio Controller (rev 09)
00:14.0 USB controller: Intel Corporation Lynx Point-LP USB xHCI HC (rev 04)
00:15.0 DMA controller: Intel Corporation Lynx Point-LP Low Power Sub-System DMA (rev 04)
00:15.1 Serial bus controller [0c80]: Intel Corporation Lynx Point-LP I2C Controller #0 (rev 04)
00:15.2 Serial bus controller [0c80]: Intel Corporation Lynx Point-LP I2C Controller #1 (rev 04)
00:1b.0 Audio device: Intel Corporation Lynx Point-LP HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 1 (rev e4)
00:1d.0 USB controller: Intel Corporation Lynx Point-LP USB EHCI #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Lynx Point-LP LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Lynx Point-LP SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Lynx Point-LP SMBus Controller (rev 04)
00:1f.6 Signal processing controller: Intel Corporation Lynx Point-LP Thermal (rev 04)
01:00.0 Network controller: Qualcomm Atheros AR9462 Wireless Network Adapter (rev 01)


```

lsmod:

```
Module                  Size  Used by
hid_generic            12559  0 
usbhid                 52565  0 
hid                   110066  3 hid_generic,usbhid
ctr                    13049  2 
ccm                    17731  2 
zram                   24438  2 
lz4_compress           12529  1 zram
joydev                 17344  0 
isl29018               14337  0 
industrialio           54895  1 isl29018
cyapa                  13148  0 
chromeos_laptop        14304  0 
intel_rapl             18783  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       18786  0 
coretemp               13441  0 
dm_multipath           22843  0 
scsi_dh                14882  1 dm_multipath
kvm_intel             148273  0 
snd_seq_midi           13564  0 
snd_seq_midi_event     14899  1 snd_seq_midi
kvm                   466035  1 kvm_intel
snd_rawmidi            30876  1 snd_seq_midi
arc4                   12608  2 
crct10dif_pclmul       14307  0 
snd_hda_codec_hdmi     51974  1 
crc32_pclmul           13133  0 
snd_hda_codec_realtek    79613  1 
snd_hda_codec_generic    68875  1 snd_hda_codec_realtek
uvcvideo               81109  0 
ghash_clmulni_intel    13230  0 
cryptd                 20360  1 ghash_clmulni_intel
videobuf2_vmalloc      13216  1 uvcvideo
ath9k                 136715  0 
videobuf2_memops       13362  1 videobuf2_vmalloc
snd_hda_intel          30520  5 
snd_seq                67178  2 snd_seq_midi_event,snd_seq_midi
videobuf2_core         47079  1 uvcvideo
v4l2_common            15682  1 videobuf2_core
snd_hda_controller     31872  1 snd_hda_intel
ath9k_common           25638  1 ath9k
videodev              158682  3 uvcvideo,v4l2_common,videobuf2_core
ath9k_hw              455128  2 ath9k_common,ath9k
snd_hda_codec         139421  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
media                  21963  2 uvcvideo,videodev
ath                    29006  3 ath9k_common,ath9k,ath9k_hw
snd_hwdep              17698  1 snd_hda_codec
snd_pcm               105335  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
mac80211              674115  1 ath9k
serio_raw              13434  0 
cfg80211              513009  4 ath,ath9k_common,ath9k,mac80211
ath3k                  13331  0 
btusb                  32336  0 
lpc_ich                21093  0 
snd_timer              29458  2 snd_pcm,snd_seq
i2c_designware_pci     13100  0 
dw_dmac_pci            12817  0 
parport_pc             32741  0 
ppdev                  17635  0 
snd                    87611  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
dw_dmac                12835  0 
rfcomm                 69427  8 
bnep                   19543  2 
tpm_infineon           17131  0 
dw_dmac_core           24290  2 dw_dmac_pci,dw_dmac
bluetooth             461507  23 bnep,ath3k,btusb,rfcomm
i2c_designware_platform    12979  0 
spi_pxa2xx_platform    23033  0 
i2c_designware_core    14768  2 i2c_designware_pci,i2c_designware_platform
8250_dw                13516  0 
soundcore              15052  2 snd,snd_hda_codec
mac_hid                13227  0 
lp                     17759  0 
parport                42264  3 lp,ppdev,parport_pc
btrfs                 929321  0 
xor                    21411  1 btrfs
raid6_pq               97812  1 btrfs
dm_mirror              22040  0 
dm_region_hash         20850  1 dm_mirror
dm_log                 18411  2 dm_region_hash,dm_mirror
i915                  997306  6 
i2c_algo_bit           13406  1 i915
drm_kms_helper         98384  1 i915
sdhci_acpi             13502  0 
sdhci                  43270  1 sdhci_acpi
video                  20205  1 i915
drm                   317398  5 i915,drm_kms_helper
ahci                   34019  2 
libahci                32190  1 ahci


```

Thanks for the help

---

### Post by kc1di on 2015-01-28
try issuing this command in terminal and see if it makes any difference.
if so we will make it permanent.```
sudo modprobe -v ath9k nohwcrypt=1
```

---

### Post by harry28 on 2015-01-29
> **kc1di said:**
> try issuing this command in terminal and see if it makes any difference.
if so we will make it permanent.```
sudo modprobe -v ath9k nohwcrypt=1
```

Unfortunately after running that command (when connected to college wifi) it doesn't seem to do anything, I still get the page saying 'Problem connecting to the server'. However for some reason, before running that command, my phones hotspot decided to work but I would still like to get it working over wi-fi since I only have limited data on my phone and it tends to kill the battery very quickly. I spoke to the I.T technicians at college to see if they know whats wrong but they said they have no clue how to use Linux so don't want to look at it. Is there anything else I can try to get it working?

---

### Post by kc1di on 2015-01-29
The only other thing I can think of is what type of authentication encryption are they using. 
You might try running the wireless script found in this thread.  It may reveal the problem. 
you'll most likely have to use method # 2. 

[http://ubuntuforums.org/showthread.php?t=2082305&p=12350385#post12350385]("http://ubuntuforums.org/showthread.php?t=2082305&p=12350385#post12350385")
post the results of the script run here so others can look at it. 


Other than that I would go into network manager and set IPv6 to ignore and try that. 
good luck

---

### Post by harry28 on 2015-01-29
Thanks for your help. I first set IPv6 to ignore and, although it still  displayed Problem Connecting to Server page, it did take longer to  display and it did actually display the website I was on once after a couple minutes of waiting. However after  trying it again it now still displays the Problem Connecting to Server all the time. I  ran the script which said in the link and it generated a txt file which I cannot attach to this post since it is too big:

```

########## wireless info START ##########

Report from: 29 Jan 2015 12:18 GMT +0000

Booted last: 29 Jan 2015 12:08 GMT +0000

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.18.0-ctx.patch #3 SMP Wed Dec 10 15:36:38 MST 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, tpm_tis.interrupts=0, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Network controller [0280]: Qualcomm Atheros AR9462 Wireless Network Adapter [168c:0034] (rev 01)
    Subsystem: Foxconn International, Inc. Device [105b:e058]
    Kernel driver in use: ath9k

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 001 Device 004: ID 0489:e056 Foxconn / Hon Hai 
Bus 001 Device 002: ID 1bcf:2c67 Sunplus Innovation Technology Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no

##### lsmod #############################

ath9k                 136715  0 
ath9k_common           25638  1 ath9k
ath9k_hw              455128  2 ath9k_common,ath9k
ath                    29006  3 ath9k_common,ath9k,ath9k_hw
mac80211              674115  1 ath9k
ath3k                  13331  0 
cfg80211              513009  4 ath,ath9k_common,ath9k,mac80211
bluetooth             461507  23 bnep,ath3k,btusb,rfcomm

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.1.45  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::162d:27ff:fe4a:e8eb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11602 errors:0 dropped:2 overruns:0 frame:0
          TX packets:2374 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2694213 (2.6 MB)  TX bytes:311602 (311.6 KB)

##### iwconfig ##########################

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"HTC Hotspot "  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'HTC Hotspot ' [AC1]>   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=21 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:5  Invalid misc:7   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: wlan0  [HTC Hotspot ] ------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           1 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    HC: Infra, <MAC 'HC' [AC17]>, Freq 5180 MHz, Rate 54 Mb/s, Strength 94 WPA2
    HC-WiFi:         Infra, <MAC 'HC-WiFi' [AC9]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 54 WPA2 Enterprise
    HC: Infra, <MAC 'HC' [AC10]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 50 WPA2
    HC-WiFi:         Infra, <MAC 'HC-WiFi' [AC13]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 84 WPA2 Enterprise
    HC: Infra, <MAC 'HC' [AC8]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 85 WPA2
    HC-WiFi:         Infra, <MAC 'HC-WiFi' [AC14]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    HC: Infra, <MAC 'HC' [AC15]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA2
    HC-WiFi:         Infra, <MAC 'HC-WiFi' [AC18]>, Freq 5220 MHz, Rate 54 Mb/s, Strength 49 WPA2 Enterprise
    HC: Infra, <MAC 'HC' [AC19]>, Freq 5220 MHz, Rate 54 Mb/s, Strength 49 WPA2
    HC-WiFi:         Infra, <MAC 'HC-WiFi' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 65 WPA2 Enterprise
    HC: Infra, <MAC 'HC' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 65 WPA2
    HC: Infra, <MAC 'HC' [AC12]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 52 WPA2
    HC-WiFi:         Infra, <MAC 'HC-WiFi' [AN13]>, Freq 5240 MHz, Rate 54 Mb/s, Strength 22 WPA2 Enterprise
    HC: Infra, <MAC 'HC' [AN14]>, Freq 5240 MHz, Rate 54 Mb/s, Strength 22 WPA2
    HC-WiFi:         Infra, <MAC 'HC-WiFi' [AC4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 39 WPA2 Enterprise
    HC-WiFi:         Infra, <MAC 'HC-WiFi' [AN16]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 42 WPA2 Enterprise
    HC: Infra, <MAC 'HC' [AN17]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WPA2
    HC: Infra, <MAC 'HC' [AN18]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 54 WPA2
    HC-WiFi:         Infra, <MAC 'HC-WiFi' [AN19]>, Freq 5200 MHz, Rate 54 Mb/s, Strength 24 WPA2 Enterprise
    HC: Infra, <MAC 'HC' [AN20]>, Freq 5200 MHz, Rate 54 Mb/s, Strength 22 WPA2
    HC-WiFi:         Infra, <MAC 'HC-WiFi' [AC16]>, Freq 5180 MHz, Rate 54 Mb/s, Strength 75 WPA2 Enterprise
    HC-WiFi:         Infra, <MAC 'HC-WiFi' [AC11]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 52 WPA2 Enterprise
    HC-WiFi:         Infra, <MAC 'HC-WiFi' [AN23]>, Freq 5240 MHz, Rate 54 Mb/s, Strength 44 WPA2 Enterprise
    HC: Infra, <MAC 'HC' [AN24]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 39 WPA2
    HC-WiFi:         Infra, <MAC 'HC-WiFi' [AC20]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA2 Enterprise
    HC: Infra, <MAC 'HC' [AN26]>, Freq 5180 MHz, Rate 54 Mb/s, Strength 39 WPA2
    HC-WiFi:         Infra, <MAC 'HC-WiFi' [AN27]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 39 WPA2 Enterprise
    HC: Infra, <MAC 'HC' [AN28]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 39 WPA2
    HC: Infra, <MAC 'HC' [AC7]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 59 WPA2
    HC-WiFi:         Infra, <MAC 'HC-WiFi' [AC6]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 35 WPA2 Enterprise
    HC-WiFi:         Infra, <MAC 'HC-WiFi' [AN31]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 59 WPA2 Enterprise
    HC: Infra, <MAC 'HC' [AN32]>, Freq 5240 MHz, Rate 54 Mb/s, Strength 22 WPA2
    HC: Infra, <MAC 'HC' [AC5]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 39 WPA2
    HC-WiFi:         Infra, <MAC 'HC-WiFi' [AN34]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 50 WPA2 Enterprise
    HC-WiFi:         Infra, <MAC 'HC-WiFi' [AN35]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA2 Enterprise
    HC: Infra, <MAC 'HC' [AN36]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA2
    *HTC Hotspot :   Infra, <MAC 'HTC Hotspot ' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 98 WPA2
    HC: Infra, <MAC 'HC' [AC21]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WPA2

  IPv4 Settings:
    Address:         192.168.1.45
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Hub 2.0]] (600 root)
[connection] id=Hub 2.0 | type=802-11-wireless
[802-11-wireless] ssid=Hub 2.0 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/HTC Hotspot ]] (600 root)
[connection] id=HTC Hotspot  | type=802-11-wireless
[802-11-wireless] ssid=HTC Hotspot  | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/HC-WiFi]] (600 root)
[ipv6] method=auto
[connection] id=HC-WiFi | type=802-11-wireless
[802-11-wireless] ssid=HC-WiFi | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto

##### iw reg get ########################

Region: Europe/London (based on set time zone)

country GB:
    (2402 - 2482 @ 40), (N/A, 20)
    (5170 - 5250 @ 40), (N/A, 20)
    (5250 - 5330 @ 40), (N/A, 20), DFS
    (5490 - 5710 @ 40), (N/A, 27), DFS
    (57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR

##### iwlist channels ###################

lo        no frequency information.

wlan0     32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
          Current Frequency:2.437 GHz (Channel 6)

##### iwlist scan #######################

Channel occupancy:

      6   APs on   Frequency:2.412 GHz (Channel 1)
      9   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.462 GHz (Channel 11)
      2   APs on   Frequency:5.18 GHz (Channel 36)
      2   APs on   Frequency:5.22 GHz (Channel 44)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'HTC Hotspot ' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-17 dBm  
                    Encryption key:on
                    ESSID:"HTC Hotspot "
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000001c791ac3
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'HC-WiFi' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"HC-WiFi"
                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000f6216180
                    Extra: Last beacon: 25824ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 03 - Address: <MAC 'HC' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"HC"
                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000f621626e
                    Extra: Last beacon: 25824ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'HC-WiFi' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"HC-WiFi"
                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000057cb0180
                    Extra: Last beacon: 25792ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 05 - Address: <MAC 'HC' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"HC"
                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000057cb026d
                    Extra: Last beacon: 25792ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'HC-WiFi' [AC6]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"HC-WiFi"
                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000003a6dd180
                    Extra: Last beacon: 296ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 07 - Address: <MAC 'HC' [AC7]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"HC"
                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000003a69227b
                    Extra: Last beacon: 604ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'HC' [AC8]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"HC"
                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000006cb52ef2
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'HC-WiFi' [AC9]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"HC-WiFi"
                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000105b81f9
                    Extra: Last beacon: 240ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 10 - Address: <MAC 'HC' [AC10]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"HC"
                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000105b82e7
                    Extra: Last beacon: 240ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC 'HC-WiFi' [AC11]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"HC-WiFi"
                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000003a052180
                    Extra: Last beacon: 328ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 12 - Address: <MAC 'HC' [AC12]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"HC"
                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000003a05231a
                    Extra: Last beacon: 328ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC 'HC-WiFi' [AC13]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"HC-WiFi"
                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000006cb52c6c
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 14 - Address: <MAC 'HC-WiFi' [AC14]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-37 dBm  
                    Encryption key:on
                    ESSID:"HC-WiFi"
                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000003b196005
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 15 - Address: <MAC 'HC' [AC15]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-34 dBm  
                    Encryption key:on
                    ESSID:"HC"
                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000003b1962aa
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 16 - Address: <MAC 'HC-WiFi' [AC16]>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=65/70  Signal level=-45 dBm  
                    Encryption key:on
                    ESSID:"HC-WiFi"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000003755a03b
                    Extra: Last beacon: 5736ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 17 - Address: <MAC 'HC' [AC17]>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:on
                    ESSID:"HC"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000003755a231
                    Extra: Last beacon: 5736ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 18 - Address: <MAC 'HC-WiFi' [AC18]>
                    Channel:44
                    Frequency:5.22 GHz (Channel 44)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"HC-WiFi"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000e180203b
                    Extra: Last beacon: 5136ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 19 - Address: <MAC 'HC' [AC19]>
                    Channel:44
                    Frequency:5.22 GHz (Channel 44)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"HC"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000e1802231
                    Extra: Last beacon: 5136ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 20 - Address: <MAC 'HC-WiFi' [AC20]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"HC-WiFi"
                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000056d1180
                    Extra: Last beacon: 8224ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unlo        Interface doesn't support scanning.

known: 7F050100000000
          Cell 21 - Address: <MAC 'HC' [AC21]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"HC"
                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000056d126f
                    Extra: Last beacon: 8224ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[ath9k]
filename:       /lib/modules/3.18.0-ctx.patch/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     5CA20ABDB2778F3165E3ED9
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       3.18.0-ctx.patch SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        78:40:98:D9:99:62:AD:94:06:29:DB:7D:A4:37:97:3F:64:1B:F7:32
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)

[ath9k_common]
filename:       /lib/modules/3.18.0-ctx.patch/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     94B4F03FB0E70D4D2C6AD91
depends:        cfg80211,ath9k_hw,ath
intree:         Y
vermagic:       3.18.0-ctx.patch SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        78:40:98:D9:99:62:AD:94:06:29:DB:7D:A4:37:97:3F:64:1B:F7:32
sig_hashalgo:   sha512

[ath9k_hw]
filename:       /lib/modules/3.18.0-ctx.patch/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     715A6023A3AE8A8FB5869EF
depends:        ath
intree:         Y
vermagic:       3.18.0-ctx.patch SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        78:40:98:D9:99:62:AD:94:06:29:DB:7D:A4:37:97:3F:64:1B:F7:32
sig_hashalgo:   sha512

[ath]
filename:       /lib/modules/3.18.0-ctx.patch/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     0D7DE85EF15890F115735E2
depends:        cfg80211
intree:         Y
vermagic:       3.18.0-ctx.patch SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        78:40:98:D9:99:62:AD:94:06:29:DB:7D:A4:37:97:3F:64:1B:F7:32
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.18.0-ctx.patch/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     7EEF5988245D414BA91F27D
depends:        cfg80211
intree:         Y
vermagic:       3.18.0-ctx.patch SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        78:40:98:D9:99:62:AD:94:06:29:DB:7D:A4:37:97:3F:64:1B:F7:32
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[ath3k]
filename:       /lib/modules/3.18.0-ctx.patch/kernel/drivers/bluetooth/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     C337943CFD92B950F279B89
depends:        bluetooth
intree:         Y
vermagic:       3.18.0-ctx.patch SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        78:40:98:D9:99:62:AD:94:06:29:DB:7D:A4:37:97:3F:64:1B:F7:32
sig_hashalgo:   sha512

[cfg80211]
filename:       /lib/modules/3.18.0-ctx.patch/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C8543A08D2650C7BC1B7107
depends:        
intree:         Y
vermagic:       3.18.0-ctx.patch SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        78:40:98:D9:99:62:AD:94:06:29:DB:7D:A4:37:97:3F:64:1B:F7:32
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
nohwcrypt: 0
ps_enable: 0

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc
lp
rtc
lp
rtc
lp
rtc
lp
rtc
lp
rtc
lp
rtc
lp
rtc
lp
rtc
lp
rtc
lp
rtc
lp
rtc
lp
rtc
lp
rtc
lp
rtc
lp
rtc
lp
rtc
lp
rtc
lp
rtc
lp
rtc
lp
rtc
lp
rtc
lp
rtc
lp
rtc
lp
rtc
lp
rtc
lp
rtc

##### modprobe options ##################

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
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/snd-hda-intel.conf]
options snd-hda-intel model=,alc283-dac-wcaps

##### rc.local ##########################

chgrp plugdev /sys/class/backlight/intel_backlight/brightness
chmod 664 /sys/class/backlight/intel_backlight/brightness

exit 0

##### pm-utils ##########################

[/etc/pm/sleep.d/00_screen] (755 root)
getXuser() {
        export user=`pinky -fw | awk '{ if ($2 == ":'$displaynum'" || $(NF) == ":'$displaynum'" ) { print $1; exit; } }'`
}
for x in /tmp/.X11-unix/*; do
    displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
    getXuser;
    case "$1" in
    thaw|resume)
        getXuser;
        sudo -u $user env DISPLAY=":$displaynum" /usr/bin/xrandr --auto
            ;;
    *)
            ;;
    esac
done
exit 0

[/etc/pm/sleep.d/99wifi] (755 root)
case "${1}" in
        hibernate)
        sudo service network-manager stop
        /sbin/rmmod ath9k
                ;;
    resume|thaw)
                /sbin/modprobe ath9k
        sudo service network-manager restart
        ;;
esac
exit 0

[/etc/pm/sleep.d/99zcyapa] (755 root)
getXuser() {
        user=`pinky -fw | awk '{ if ($2 == ":'$displaynum'" || $(NF) == ":'$displaynum'" ) { print $1; exit; } }'`
        if [ x"$user" = x"" ]; then
                startx=`pgrep -n startx`
                if [ x"$startx" != x"" ]; then
                        user=`ps -o user --no-headers $startx`
                fi
        fi
        if [ x"$user" != x"" ]; then
                userhome=`getent passwd $user | cut -d: -f6`
                export XSESSIONRC=$userhome/.xsessionrc
        else
                export XSESSIONRC=""
        fi
}
case "${1}" in
    hibernate)
    /sbin/rmmod cyapa
        ;;
    resume|thaw)
        COUNTER=0
        while [  $COUNTER -lt 10 ]; do
            date >>/tmp/99_cyapa
            /sbin/modprobe cyapa
        sleep 1
        dmesg | grep cyapa | tail -1 | grep "\(error\|fail\)" >/dev/null
        RES=$?
        if [ ${RES} -ne 1 ] ; then
        /sbin/rmmod cyapa
        sleep 1
        else
        #done
        COUNTER=11
        fi
        
            COUNTER=`expr $COUNTER + 1`
        done
        ;;
esac
exit 0

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x168c:0x0034 (ath9k)
SUBSYSTEM=="net",  ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0'  [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*",  NAME="wlan0"

##### dmesg #############################

[  276.450015] wlan0: authenticate with <MAC 'HTC Hotspot ' [AC1]>
[  276.450025] wlan0: capabilities/regulatory prevented using AP HT/VHT configuration, downgraded
[  276.463509] wlan0: send auth to <MAC 'HTC Hotspot ' [AC1]> (try 1/3)
[  276.467405] wlan0: authenticated
[  276.467552] wlan0: AP has invalid WMM params (AIFSN=1 for ACI 2), disabling WMM
[  276.469216] wlan0: associate with <MAC 'HTC Hotspot ' [AC1]> (try 1/3)
[  276.472761] wlan0: RX AssocResp from <MAC 'HTC Hotspot ' [AC1]> (capab=0x411 status=0 aid=1)
[  276.472853] wlan0: associated
[  276.476193] ath: EEPROM regdomain: 0x833a
[  276.476198] ath: EEPROM indicates we should expect a country code
[  276.476200] ath: doing EEPROM country->regdmn map search
[  276.476202] ath: country maps to regdmn code: 0x37
[  276.476203] ath: Country alpha2 being used: GB
[  276.476205] ath: Regpair used: 0x37
[  276.476207] ath: regdomain 0x833a dynamically updated by country IE
[  276.554349] wlan0: Limiting TX power to 20 (20 - 0) dBm as advertised by <MAC 'HTC Hotspot ' [AC1]>
[  281.486889] wlan0: authenticate with <MAC 'HTC Hotspot ' [AC1]>
[  281.486900] wlan0: capabilities/regulatory prevented using AP HT/VHT configuration, downgraded
[  281.496333] wlan0: send auth to <MAC 'HTC Hotspot ' [AC1]> (try 1/3)
[  281.499632] wlan0: authenticated
[  281.499777] wlan0: AP has invalid WMM params (AIFSN=1 for ACI 2), disabling WMM
[  281.501762] wlan0: associate with <MAC 'HTC Hotspot ' [AC1]> (try 1/3)
[  281.504692] wlan0: RX AssocResp from <MAC 'HTC Hotspot ' [AC1]> (capab=0x411 status=0 aid=1)
[  281.504786] wlan0: associated
[  281.508165] ath: EEPROM regdomain: 0x833a
[  281.508169] ath: EEPROM indicates we should expect a country code
[  281.508171] ath: doing EEPROM country->regdmn map search
[  281.508173] ath: country maps to regdmn code: 0x37
[  281.508175] ath: Country alpha2 being used: GB
[  281.508176] ath: Regpair used: 0x37
[  281.508178] ath: regdomain 0x833a dynamically updated by country IE
[  281.574770] wlan0: Limiting TX power to 20 (20 - 0) dBm as advertised by <MAC 'HTC Hotspot ' [AC1]>
[  288.433940] wlan0: authenticate with <MAC 'HTC Hotspot ' [AC1]>
[  288.433950] wlan0: capabilities/regulatory prevented using AP HT/VHT configuration, downgraded
[  288.447298] wlan0: send auth to <MAC 'HTC Hotspot ' [AC1]> (try 1/3)
[  288.449334] wlan0: authenticated
[  288.450002] wlan0: AP has invalid WMM params (AIFSN=1 for ACI 2), disabling WMM
[  288.453158] wlan0: associate with <MAC 'HTC Hotspot ' [AC1]> (try 1/3)
[  288.456040] wlan0: RX AssocResp from <MAC 'HTC Hotspot ' [AC1]> (capab=0x411 status=0 aid=1)
[  288.456130] wlan0: associated
[  288.459608] ath: EEPROM regdomain: 0x833a
[  288.459612] ath: EEPROM indicates we should expect a country code
[  288.459615] ath: doing EEPROM country->regdmn map search
[  288.459616] ath: country maps to regdmn code: 0x37
[  288.459618] ath: Country alpha2 being used: GB
[  288.459619] ath: Regpair used: 0x37
[  288.459621] ath: regdomain 0x833a dynamically updated by country IE
[  288.533270] wlan0: Limiting TX power to 20 (20 - 0) dBm as advertised by <MAC 'HTC Hotspot ' [AC1]>

########## wireless info END ############


```

---

### Post by kc1di on 2015-01-30
Sorry for  the delayed reply , but was out of town on Business yesterday. 
I don't see anything that stands out in the script run. other that your card has been problematic for awhile in linux.
but you may want to take a look at some of the solutions fond on Ask ubuntu dealing with bad connection you can find it [here.]("http://askubuntu.com/questions/301442/atheros-ar9462-wifi-very-unstable-package-loss")
since I do not have a machine with your particular card , I can't test them myself. 
maybe others will chime in also. 
good luck

---

### Post by westie457 on 2015-01-30
Hi, I had a problem similar to yours a few days ago, cannot remember where  I found the fix for it.
The problem for me was a slightly wonky 'hosts' file.
The cure was to install libnss-myhostname.
The system has been working properly since then.

Hope this helps you.

---

### Post by harry28 on 2015-01-30
> **kc1di said:**
> Sorry for  the delayed reply , but was out of town on Business yesterday. 
I don't see anything that stands out in the script run. other that your card has been problematic for awhile in linux.
but you may want to take a look at some of the solutions fond on Ask ubuntu dealing with bad connection you can find it [here.]("http://askubuntu.com/questions/301442/atheros-ar9462-wifi-very-unstable-package-loss")
since I do not have a machine with your particular card , I can't test them myself. 
maybe others will chime in also. 
good luck

> **westie457 said:**
> Hi, I had a problem similar to yours a few days ago, cannot remember where  I found the fix for it.
The problem for me was a slightly wonky 'hosts' file.
The cure was to install libnss-myhostname.
The system has been working properly since then.

Hope this helps you.
Ok thank you [COLOR=#000000]kc1di for your help, will have a look at that link. I am not at college till Monday so will try it then. Also I will try what [/COLOR][COLOR=#000000]westie457 suggested in installing libnss-myhostname and see if that solves it. Thanks again for your help.[/COLOR]

---

### Post by kenneth15 on 2015-03-24
Did you ever resolve this?  I'm having the same issue using the same distro you mentioned.  Everything works fine for a few days and then suddenly wifi will no longer connect.  I suspect I'm installing a system update of some sort that's breaking it, but for the life of me I can't figure out which one.

---

