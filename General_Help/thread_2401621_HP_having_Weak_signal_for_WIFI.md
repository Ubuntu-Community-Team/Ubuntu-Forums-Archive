---
title: "HP having Weak signal for WIFI"
date: 2018-09-20
forum: General Help
---

### Post by kanothsiraj on 2018-09-20
After updation signal losing..  how to fix it permanently


bagmo@bagmo-HP-Notebook:~$ sudo modprobe -r rtl8723be
bagmo@bagmo-HP-Notebook:~$ sudo modprobe rtl8723be ant_sel=1
bagmo@bagmo-HP-Notebook:~$ iwlist scan | egrep -i 'ssid|quality'
lo        Interface doesn't support scanning.


enp1s0    Interface doesn't support scanning.


virbr0    Interface doesn't support scanning.


virbr0-nic  Interface doesn't support scanning.


                    Quality=46/70  Signal level=-64 dBm  
                    ESSID:"BAGMO"
                    Quality=32/70  Signal level=-78 dBm  
                    ESSID:"ESP_82845A"
                    Quality=24/70  Signal level=-86 dBm  
                    ESSID:"NETGEAR20"
bagmo@bagmo-HP-Notebook:~$ sudo modprobe -r rtl8723be
bagmo@bagmo-HP-Notebook:~$ sudo modprobe rtl8723be ant_sel=2
bagmo@bagmo-HP-Notebook:~$ iwlist scan | egrep -i 'ssid|quality'
lo        Interface doesn't support scanning.


enp1s0    Interface doesn't support scanning.


virbr0    Interface doesn't support scanning.


virbr0-nic  Interface doesn't support scanning.


                    Quality=46/70  Signal level=-64 dBm  
                    ESSID:"BAGMO"
                    Quality=26/70  Signal level=-84 dBm  
                    ESSID:"ESP_82845A"
                    Quality=24/70  Signal level=-86 dBm  
                    ESSID:"NETGEAR20"




Sitting near by BAGMO router to post this thread
-----------------------------------------------------

$ modinfo rtl8723be; grep [[:alnum:]] /etc/modprobe.d/* | grep rtl8723be
filename:       /lib/modules/4.15.0-34-generic/updates/dkms/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw_36.bin
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         PageHe    <page_he@realsil.com.cn>
srcversion:     41E3D27D506CBEDC478A504
alias:          pci:v000010ECd0000B723sv*sd*bc*sc*i*
depends:        rtlwifi,rtl8723-common,rtl_pci,btcoexist,mac80211
retpoline:      Y
name:           rtl8723be
vermagic:       4.15.0-34-generic SMP mod_unload 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)
 (bool)
parm:           aspm:Set to 1 to enable ASPM (default 1)
 (int)
parm:           debug_level:Set debug level (0-5) (default 0) (int)
parm:           debug_mask:Set debug mask (default 0) (ullong)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)
parm:           ant_sel:Set to 1 or 2 to force antenna number (default 0)
 (int)
/etc/modprobe.d/50-rtl8723be.conf:options rtl8723be ant_sel=2
/etc/modprobe.d/rtl8723-ant-sel.conf:options rtl8723be ant_sel=2



PLEASE .. anyone help me to get WIFI signal

---

### Post by gpvagianas on 2018-09-21
Did you find the solution? I have the same issue. In addition the mchine will not go off when I am terminating the work. It gets stuck.

---

