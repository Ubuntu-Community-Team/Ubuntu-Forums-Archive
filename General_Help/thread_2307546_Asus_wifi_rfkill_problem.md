---
title: "Asus wifi rfkill problem"
date: 2015-12-26
forum: General Help
---

### Post by dracoborg on 2015-12-26
Hi guys,
I have this problem for a while. I found simple "solution" which is suspend my laptop and turn if on again. But I'm not happy with that. Problem is my WIFI card not working due to RFKILL (fn + f2 not working).

```

rfkill list 1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
2: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: asus-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
4: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

``` 

I googled that and found some tips, but none of them worked. I've tried to block asus-wmi, add option to asus.conf file (found here: [http://askubuntu.com/questions/351594/wireless-disabled-by-hardware-switch-on-an-asus-x550v](http://askubuntu.com/questions/351594/wireless-disabled-by-hardware-switch-on-an-asus-x550v)), and also rfkill unblock. Problem remain. Anyone had similar problem? 

```

sudo dmidecode | grep "System Information" -A 2System Information
    Manufacturer: ASUSTeK COMPUTER INC.
    Product Name: X75VB

```

```

lspci
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1c.3 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 3D controller: NVIDIA Corporation GK208M [GeForce GT 740M] (rev a1)
03:00.0 Network controller: Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01)
04:00.0 Ethernet controller: Qualcomm Atheros AR8161 Gigabit Ethernet (rev 10)

```

```

lsmod | grep asus
asus_nb_wmi            21128  0 
asus_wmi               24094  1 asus_nb_wmi
sparse_keymap          13948  1 asus_wmi
wmi                    19193  3 mxm_wmi,nouveau,asus_wmi
video                  20128  3 i915,nouveau,asus_wmi

```

```



	======== Wireless-Info START ========


System-Info ~~~~~~~~~~~~~~~~~~~~~~~~


dracoborg-X75VB 3.16.0-53-generic x86_64,  Ubuntu 14.04.3 LTS, trusty


CPU    : Intel(R) Core(TM) i5-3230M CPU @ 2.60GHz
Memory : 7870 MB
Uptime : 10:51:47 up 13 min,  2 users,  load average: 0,54, 0,97, 0,53




lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


03:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
	Subsystem: AzureWave Device [1a3b:2c97]
	Kernel driver in use: ath9k
04:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8161 Gigabit Ethernet [1969:1091] (rev 10)
	Subsystem: ASUSTeK Computer Inc. Device [1043:14c7]
	Kernel driver in use: alx




lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 04f2:b354 Chicony Electronics Co., Ltd 
Bus 001 Device 006: ID 13d3:3362 IMC Networks 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub




PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~






iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     IEEE 802.11bgn  ESSID:"Misia "  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC C-01 Misia >   
          Bit Rate=150 Mb/s   Tx-Power=16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-35 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:68   Missed beacon:0






rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


      Interface               Soft blocked  Hard blocked
1: phy0: Wireless LAN             no            no
2: asus-wlan: Wireless LAN        no            no
3: asus-bluetooth: Bluetooth      no            no
4: hci0: Bluetooth                no            no




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


asus_nb_wmi            21128  0 
asus_wmi               24094  1 asus_nb_wmi
sparse_keymap          13948  1 asus_wmi
ath9k                 141379  0 
ath9k_common           25638  1 ath9k
ath9k_hw              446521  2 ath9k_common,ath9k
ath                    29006  3 ath9k_common,ath9k,ath9k_hw
mac80211              652777  1 ath9k
cfg80211              498458  4 ath,ath9k_common,ath9k,mac80211
mxm_wmi                13021  1 nouveau
video                  20128  3 i915,nouveau,asus_wmi
wmi                    19193  3 mxm_wmi,nouveau,asus_wmi




module parameters ~~~~~~~~~~~~~~~~~~


asus_nb_wmi   (1): wapf=0
ath9k         (6): blink=0 | bt_ant_diversity=0 | btcoex_enable=0 | nohwcrypt=0 | ps_enable=0 | use_chanctx=0
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
video         (3): allow_duplicates=N | brightness_switch_enabled=Y | use_native_backlight=-1
wmi           (2): debug_dump_wdg=N | debug_event=N




nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


State: connected (global)
=================o=============o========o=========  ====o=========o===========o==============o========  ===
 Interface & ID  | Type        | Driver | State       | Default | Speed     | Support      | HW Addr   
=================o=============o========o=========  ====o=========o===========o==============o========  ===
 eth0            | Wired       | alx    | unavailable | no      |           |              | <MAC eth0>
-----------------+-------------+--------+-------------+---------+-----------+--------------+-----------
 wlan0  [Misia ] | 802.11 WiFi | ath9k  | connected   | yes     | 150 Mb/s  | WEP/WPA/WPA2 | <MAC wlan0>


    FOXNET8-tel.508549112: Infra, <MAC C-02 FOXNET8-tel.508549112>, Freq 2417 MHz, Rate 54 Mb/s, Strength 30
    *Misia :         Infra, <MAC C-01 Misia >, Freq 2437 MHz, Rate 54 Mb/s, Strength 83 WPA WPA2
    Livebox-ACC0:    Infra, <MAC C-03 Livebox-ACC0>, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    Orange_FunSpot:  Infra, <MAC C-04 Orange_FunSpot>, Freq 2412 MHz, Rate 54 Mb/s, Strength 20


    Address:         192.168.2.152
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1
    DNS:             192.168.2.1
-----------------+-------------+--------+-------------+---------+-----------+--------------+-----------




NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true




NetworkManager.conf ~~~~~~~~~~~~~~~~


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false




NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~


3SOFTRZESZOW         : ssid=3SOFTRZESZOW | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
BULAS                : ssid=BULAS | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
DANIO_siec           : ssid=DANIO_siec | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
eduroam              : ssid=eduroam | mac-address=<MAC wlan0> | ipv4=auto 
GAMEKEEPER           : ssid=GAMEKEEPER | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Hakiery              : ssid=Hakiery | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Hakiery 1            : ssid=Hakiery | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Misia                : ssid=Misia | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Misia  1             : ssid=Misia | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
NETIASPOT-AC9310     : ssid=NETIASPOT-AC9310 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
OlympiaSpodek        : ssid=OlympiaSpodek | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
OlympiaSpodek-guest  : ssid=OlympiaSpodek-guest | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Siec_domowa_14       : ssid=Siec_domowa_14 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
SPODEK               : ssid=SPODEK | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
TP-LINK_FA295C       : ssid=TP-LINK_FA295C | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
willawidokowa        : ssid=willawidokowa | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
www.ubnt.com         : ssid=www.ubnt.com | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 




interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~


nameserver 127.0.1.1




Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 wlan0
192.168.2.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


--- 192.168.2.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 2.251/2.295/2.339/0.044 ms


--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.022/0.027/0.033/0.007 ms




iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~


(Region : "pl_PL.UTF-8")
country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS




iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     14 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 14 (2.484 GHz)


          Current Frequency:2.437 GHz (Channel 6)




iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 Misia >
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-38 dBm  
                    Encryption key:on
                    ESSID:"Misia "
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000025804bea
                    Extra: Last beacon: 32ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 FOXNET8-tel.508549112>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:off
                    ESSID:"FOXNET8-tel.508549112"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000f5f303cd756
                    Extra: Last beacon: 32ms ago
          Cell 03 - Address: <MAC C-03 Livebox-ACC0>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"Livebox-ACC0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000001b9ff7f6
                    Extra: Last beacon: 32ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC C-04 Orange_FunSpot>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:off
                    ESSID:"Orange_FunSpot"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000001b9f3f1f
                    Extra: Last beacon: 32ms ago




blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist.conf]
blacklist asus-wmi
blacklist asus_wmi


[/etc/modprobe.d/osspd.conf]
blacklist snd-pcm-oss
blacklist snd-mixer-oss
blacklist snd-seq-oss




modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[asus_nb_wmi]
filename:       /lib/modules/3.16.0-53-generic/kernel/drivers/platform/x86/asus-nb-wmi.ko
srcversion:     F16297F4D8CE54489F3138B
depends:        asus-wmi
parm:           wapf:WAPF value (uint)


[asus_wmi]
filename:       /lib/modules/3.16.0-53-generic/kernel/drivers/platform/x86/asus-wmi.ko
srcversion:     B5FEEAA49A8BE4D7FB6ABFD
depends:        sparse-keymap,wmi,video


[ath9k]
filename:       /lib/modules/3.16.0-53-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
srcversion:     CED1D76477A777795A07D73
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_chanctx:Enable channel context for concurrency (int)


[ath9k_common]
filename:       /lib/modules/3.16.0-53-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
srcversion:     265A5990B1258ECC29235FC
depends:        cfg80211,ath9k_hw,ath


[ath9k_hw]
filename:       /lib/modules/3.16.0-53-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
srcversion:     0D1161FC3B202FBE214F25D
depends:        ath


[ath]
filename:       /lib/modules/3.16.0-53-generic/kernel/drivers/net/wireless/ath/ath.ko
srcversion:     165C1DF76AF8C8B6A45DA4F
depends:        cfg80211


[mac80211]
filename:       /lib/modules/3.16.0-53-generic/kernel/net/mac80211/mac80211.ko
srcversion:     477882071593B10E01388C8
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.16.0-53-generic/kernel/net/wireless/cfg80211.ko
srcversion:     046346857FD53951C911443
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


[mxm_wmi]
filename:       /lib/modules/3.16.0-53-generic/kernel/drivers/platform/x86/mxm-wmi.ko
srcversion:     D566C16ECB7E11FB9DF5C84
depends:        wmi


[video]
filename:       /lib/modules/3.16.0-53-generic/kernel/drivers/acpi/video.ko
srcversion:     2C29072BDC57BA9481E70D2
depends:        
parm:           brightness_switch_enabled:bool
parm:           allow_duplicates:bool
parm:           use_native_backlight:int


[wmi]
filename:       /lib/modules/3.16.0-53-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     347CF30B94B5549A75865A8
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)




udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~


# PCI device 0x1969:0x1091 (alx)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x168c:0x0032 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"




Custom files/entries ~~~~~~~~~~~~~~~


/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default


[/etc/modprobe.d]
asus.conf         : options asus_nb_wmi wapf=0
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en
modesetting.conf  : options cirrus modeset=1
                    options mgag200 modeset=1




Kernel boot line ~~~~~~~~~~~~~~~~~~~


BOOT_IMAGE=/boot/vmlinuz-3.16.0-53-generic root=UUID=091533e9-2c29-4cbb-9391-8a5eb9d04aac ro quiet splash vt.handoff=7




dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[    0.017210] Initializing cgroup subsys net_cls
[    0.017218] Initializing cgroup subsys net_prio
[    0.873876] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.874184] audit: initializing netlink subsys (disabled)
[    1.007377] alx 0000:04:00.0 eth0: Qualcomm Atheros AR816x/AR817x Ethernet [<MAC eth0>]
[    1.989476] psmouse serio4: elantech: assuming hardware version 4 (with firmware version 0x361f03)
[   19.116309] wmi: Mapper loaded
[   19.237935] ath: phy0: Disable PLL PowerSave
[   19.245310] ath: phy0: ASPM enabled: 0x42
[   19.245313] ath: EEPROM regdomain: 0x60
[   19.245315] ath: EEPROM indicates we should expect a direct regpair map
[   19.245317] ath: Country alpha2 being used: 00
[   19.245318] ath: Regpair used: 0x60
[   19.305642] asus_wmi: ASUS WMI generic driver loaded
[   19.317994] asus_wmi: Initialization: 0x1
[   19.318540] asus_wmi: BIOS WMI version: 7.9
[   19.349659] asus_wmi: SFUN value: 0x4a0877
[   19.453962] input: Asus WMI hotkeys as /devices/platform/asus-nb-wmi/input/input12
[   19.684281] asus_wmi: Backlight controlled by ACPI video driver
[   26.112484] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   27.846263] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  188.046003] ath: phy0: ASPM enabled: 0x42
[  188.367256] usb 1-1.1: device firmware changed
[  190.262034] alx 0000:04:00.0 eth0: Qualcomm Atheros AR816x/AR817x Ethernet [<MAC eth0>]
[  190.387341] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  191.426518] wlan0: authenticate with <MAC C-01 Misia >
[  191.433770] wlan0: send auth to <MAC C-01 Misia > (try 1/3)
[  191.436138] wlan0: authenticated
[  191.436979] wlan0: associate with <MAC C-01 Misia > (try 1/3)
[  191.441332] wlan0: RX AssocResp from <MAC C-01 Misia > (capab=0x431 status=0 aid=1)
[  191.441395] wlan0: associated
[  191.441406] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


	======== Done ========

```

---

### Post by jeremy31 on 2015-12-26
```
echo "options asus_nb_wmi wapf=4" | sudo tee /etc/modprobe.d/asus.conf
```

Reboot

---

### Post by grahammechanical on 2015-12-26
I see conflicting information

rfkill list printout says phy0: wireless LAN Hard blocked = yes

but Wireless - Info report of rfkill list says phy0: wireless LAN Hard blocked = no

There is also information from Wireless - Info report that shows phy0 is connected to a wireless access point called Misia with signal level = -35 dBm. And altogether 17 wireless access points being detected.

So, what is the problem? Faulty function keys on the keyboard that do not always switch on the WiFi adapter when pressed and are reset when the machine is suspended and resumed from suspension?

Regards.

---

### Post by dracoborg on 2015-12-26
Thanks jeremy31. That works for me.

grahammechanical sorry for that. rfkill list is printed after system startup, wireless info is printed after suspend and another startup (which as I wrote "solves" problem). Problem is that wireless is hard blocked after startup due to rfkill, but fn + f2 not working. jeremy31 already solved this issue:)

Thanks guys for your time.

---

