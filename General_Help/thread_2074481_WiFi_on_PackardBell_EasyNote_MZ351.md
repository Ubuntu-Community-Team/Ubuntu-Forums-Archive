---
title: "WiFi on PackardBell EasyNote MZ351"
date: 2012-10-21
forum: General Help
---

### Post by acostaisasmendi on 2012-10-21
Hello. I'm having some trouble. I already searched and copied/pasted many commands from here, but still not working.

The problem is that it recognizes every single wifi connection perfectly but it won't connect to any WiFi.

It's my dad's computer, he needs it for working so it's kinda urgent. Thank you all in advance for taking the time!

Can someone please help me?

---

### Post by wildmanne39 on 2012-10-21
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

---

### Post by acostaisasmendi on 2012-10-21
Umm, the computer that runs linux doesn't have internet (That's exactly the problem). Can I just copy/paste it in notepad (Windows) and save it as a .txt so then I'll transfer it with a pendrive to the other computer and run the second part of the command?

---

### Post by wildmanne39 on 2012-10-21
Hi, just use a flash drive to transfer the results of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

### Post by acostaisasmendi on 2012-10-21
Hello, these are the results:

```
autofranc@autofranc:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10"
Linux autofranc 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:32:08 UTC 2012 i686 i686 i686 GNU/Linux
autofranc@autofranc:~$ lspci -nnk | grep -iA2 net
09:02.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
	Subsystem: Packard Bell B.V. Device [1631:c101]
	Kernel driver in use: 8139too
--
09:04.0 Network controller [0280]: Ralink corp. RT2561/RT61 rev B 802.11g [1814:0302]
	Subsystem: Device [18e8:6194]
	Kernel driver in use: rt61pci
autofranc@autofranc:~$ lsusb
Bus 002 Device 002: ID 0566:3107 Monterey International Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
autofranc@autofranc:~$ iwconfig
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.

eth0      no wireless extensions.

autofranc@autofranc:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
autofranc@autofranc:~$ lsmod
Module                  Size  Used by
coretemp               13168  0 
snd_hda_codec_realtek    63356  1 
snd_hda_intel          32515  4 
snd_hda_codec         111547  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80163  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25382  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51255  2 snd_seq_midi,snd_seq_midi_event
arc4                   12473  2 
microcode              18209  0 
radeon                820703  2 
snd_timer              24411  2 snd_pcm,snd_seq
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    61991  17 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                84843  0 
rt61pci                27074  0 
crc_itu_t              12627  1 rt61pci
rt2x00pci              14116  1 rt61pci
ttm                    75534  1 radeon
drm_kms_helper         45271  1 radeon
rt2x00lib              48562  2 rt61pci,rt2x00pci
serio_raw              13031  0 
soundcore              14599  1 snd
parport_pc             31968  0 
drm                   230463  4 radeon,ttm,drm_kms_helper
eeprom_93cx6           13134  1 rt61pci
rfcomm                 37276  4 
snd_page_alloc         14036  2 snd_hda_intel,snd_pcm
ppdev                  12817  0 
bnep                   17707  2 
i2c_algo_bit           13197  1 radeon
bluetooth             183228  10 rfcomm,bnep
joydev                 17161  0 
ati_agp                13177  0 
i2c_piix4              12983  0 
shpchp                 32189  0 
video                  18847  0 
mac_hid                13037  0 
ath                    19187  0 
mac80211              461161  2 rt2x00pci,rt2x00lib
cfg80211              175375  3 rt2x00lib,ath,mac80211
lp                     13299  0 
parport                40753  3 parport_pc,ppdev,lp
hid_generic            12445  0 
usbhid                 41702  0 
hid                    82142  2 hid_generic,usbhid
8139too                23071  0 
8139cp                 26619  0 
pata_atiixp            12999  2 

```

I honestly thank you for taking the time!

---

### Post by wildmanne39 on 2012-10-21
Hi, please do:
```
echo "options rt61pci nohwcrypt=1" | sudo tee /etc/modprobe.d/rt61pci.conf
sudo modprobe -rfv rt61pci
sudo modprobe -v rt61pci
```
Thanks

---

### Post by acostaisasmendi on 2012-10-21
Still not working.
I tried booting it from the Live CD on other computer (The one I'm currently using with w7) and it didn't work either. Could it be a problem with Xubuntu itself?

Here's the command output:

```
autofranc@autofranc:~$ echo "options rt61pci nohwcrypt=1" | sudo tee /etc/modprobe.d/rt61pci.conf
[sudo] password for autofranc: 
options rt61pci nohwcrypt=1
autofranc@autofranc:~$ sudo modprobe -rfv rt61pci
rmmod /lib/modules/3.5.0-17-generic/kernel/drivers/net/wireless/rt2x00/rt61pci.ko
rmmod /lib/modules/3.5.0-17-generic/kernel/lib/crc-itu-t.ko
rmmod /lib/modules/3.5.0-17-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
rmmod /lib/modules/3.5.0-17-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
rmmod /lib/modules/3.5.0-17-generic/kernel/net/mac80211/mac80211.ko
rmmod /lib/modules/3.5.0-17-generic/kernel/drivers/misc/eeprom/eeprom_93cx6.ko
autofranc@autofranc:~$ sudo modprobe -v rt61pci
insmod /lib/modules/3.5.0-17-generic/kernel/drivers/misc/eeprom/eeprom_93cx6.ko 
insmod /lib/modules/3.5.0-17-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.5.0-17-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko 
insmod /lib/modules/3.5.0-17-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko 
insmod /lib/modules/3.5.0-17-generic/kernel/lib/crc-itu-t.ko 
insmod /lib/modules/3.5.0-17-generic/kernel/drivers/net/wireless/rt2x00/rt61pci.ko nohwcrypt=1
autofranc@autofranc:~$ 

```

---

### Post by acostaisasmendi on 2012-10-21
I even tried with a ubuntu 12.04 Live CD and it won't connect (With the w7 computer). It does recognize the name, though.

---

### Post by wildmanne39 on 2012-10-21
Hi, please post results of:
```
nm-tool
sudo iwlist scan
dmesg | egrep 'rt6|firm'
```
Thanks

---

### Post by acostaisasmendi on 2012-10-21
Results:

```
autofranc@autofranc:~$ nm-tool

NetworkManager Tool

State: connecting

- Device: wlan0  [casa] --------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt61pci
  State:             connecting (getting IP configuration)
  Default:           no
  HW Address:        00:0D:F0:33:DE:6C

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    Red inalamb CS:  Infra, D8:5D:4C:BA:79:9A, Freq 2437 MHz, Rate 54 Mb/s, Strength 57 WPA2
    casa:            Infra, 20:F3:A3:8B:97:32, Freq 2412 MHz, Rate 54 Mb/s, Strength 80 WPA WPA2


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             unavailable
  Default:           no
  HW Address:        00:16:36:E5:C0:E1

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


autofranc@autofranc:~$ sudo iwlist scan
[sudo] password for autofranc: 
wlan0     Scan completed :
          Cell 01 - Address: 20:F3:A3:8B:97:32
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"casa"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000030bea332
                    Extra: Last beacon: 20ms ago
                    IE: Unknown: 000463617361
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6C0017FF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601000700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05030007127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4300000000
                    IE: Unknown: 0706505920010D10
          Cell 02 - Address: D8:5D:4C:BA:79:9A
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"Red inalamb CS"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000000135eabb
                    Extra: Last beacon: 1196ms ago
                    IE: Unknown: 000E52656420696E616C616D62204353
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101070003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406071B00000000000000000000000000000000000000
                    IE: Unknown: 3D1606071B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010004000000

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

autofranc@autofranc:~$ dmesg | egrep 'rt6|firm'
[ 8285.600713] Registered led device: rt61pci-phy1::radio
[ 8285.600747] Registered led device: rt61pci-phy1::assoc
autofranc@autofranc:~$ 

```

---

### Post by wildmanne39 on 2012-10-21
Hi, which network are you trying to connect too?
Thanks

---

### Post by acostaisasmendi on 2012-10-21
I'm trying to connect to "casa"

---

### Post by wildmanne39 on 2012-10-21
Hi, go into your router settings and change encryption to just wpa2 if it has that option.
Thanks

---

### Post by acostaisasmendi on 2012-10-22
Hello.

That actually made my wifi stop working :P.

But I already contacted my ISP and solved the problem.

Thanks for the time anyway! :)

---

