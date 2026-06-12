---
title: "Bluetooth Intel 7260 not pairing with Microsoft 3600 mouse on Ubuntu 16.04"
date: 2017-02-12
forum: General Help
---

### Post by joaofl on 2017-02-12
I've been trying to find the answer to my problem for a month now.. There are MANY posts all around, but none solved my problem, which I still could not understand why (reason why I come here). Here it is:

My laptop has an Intel 7260 wifi+bluetooth. Wifi works fine, but I can not pair my Microsoft 3600 bluetootth mouse with it on Ubuntu 16.04... However It **does** work with Ubuntu 16.10!

Because of that, I immediately tough that by upgrading to kernel 4.8 on Ubuntu 16.04,  that I would solve my issue, but it **did not solve**.

Tried using the UI, and blurtoothctl. None works. The process of pairing seems to go fine, the mouse LEDs blink as if it was normally paired, but in the end it doesnt move. What I've noticed is that dmesg shows this error after it fails to pair: 

**Bluetooth: SMP security requested but not available**

So I guess it may be related to that. I also tried to compare the versions of drivers between 16.10 and 16.04, but they are all the same. Have no clue what to do. Follows some logs:

Now I'm running kernel 4.8.0-36 on Ubuntu 16.04

Thanks in advance!

```
lspci
08:00.0 Network controller: Intel Corporation Wireless 7260 (rev 73)
```

```
dmesg | grep Bluetooth
[   12.756322] toshiba_bluetooth: Toshiba ACPI Bluetooth device driver
[   12.817046] Bluetooth: Core ver 2.21
[   12.817059] Bluetooth: HCI device and connection manager initialized
[   12.817062] Bluetooth: HCI socket layer initialized
[   12.817064] Bluetooth: L2CAP socket layer initialized
[   12.817069] Bluetooth: SCO socket layer initialized
[   12.843287] Bluetooth: hci0: read Intel version: 370710018002030d00
[   12.848185] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.2.3.d.bseq
[   13.024080] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[   13.251153] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   13.251154] Bluetooth: BNEP filters: protocol multicast
[   13.251157] Bluetooth: BNEP socket layer initialized
[   32.186991] Bluetooth: RFCOMM TTY layer initialized
[   32.186995] Bluetooth: RFCOMM socket layer initialized
[   32.186998] Bluetooth: RFCOMM ver 1.11
[  735.389939] Bluetooth: SMP security requested but not available
```


```
 modinfo bluetooth
filename:       /lib/modules/4.8.0-36-generic/kernel/net/bluetooth/bluetooth.ko
alias:          net-pf-31
license:        GPL
version:        2.21
description:    Bluetooth Core ver 2.21
author:         Marcel Holtmann <marcel@holtmann.org>
srcversion:     25829AB27583956CC53D583
depends:        
intree:         Y
vermagic:       4.8.0-36-generic SMP mod_unload modversions 
parm:           disable_esco:Disable eSCO connection creation (bool)
parm:           disable_ertm:Disable enhanced retransmission mode (bool)
```



```
modinfo iwlwifi
filename:       /lib/modules/4.8.0-36-generic/kernel/drivers/net/wireless/intel/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <linuxwifi@intel.com>
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-IWL6000G2B_UCODE_API_MAX.ucode
firmware:       iwlwifi-6000g2a-6.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-6.ucode
firmware:       iwlwifi-7265D-24.ucode
firmware:       iwlwifi-7265-17.ucode
firmware:       iwlwifi-3168-24.ucode
firmware:       iwlwifi-3160-17.ucode
firmware:       iwlwifi-7260-17.ucode
firmware:       iwlwifi-8265-24.ucode
firmware:       iwlwifi-8000C--24.ucode
firmware:       iwlwifi-9260-th-a0-lc-a0--24.ucode
firmware:       iwlwifi-9260-th-a0-jf-a0--24.ucode
firmware:       iwlwifi-9000-pu-a0-lc-a0--24.ucode
firmware:       iwlwifi-Qu-a0-jf-b0--24.ucode
srcversion:     E7651FD3D9AF45F96CD8B2E
.....
depends:        cfg80211
intree:         Y
vermagic:       4.8.0-36-generic SMP mod_unload modversions 
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size:amsdu size 0: 12K for multi Rx queue devices, 4K for other devices 1:4K 2:8K 3:12K (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (default: 0 dB) (int)
parm:           nvm_file:NVM file name (charp)
parm:           d0i3_disable:disable d0i3 functionality (default: Y) (bool)
parm:           lar_disable:disable LAR functionality (default: N) (bool)
parm:           uapsd_disable:disable U-APSD functionality bitmap 1: BSS 2: P2P Client (default: 3) (uint)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)
parm:           d0i3_timeout:Timeout to D0i3 entry when idle (ms) (uint)
parm:           disable_11ac:Disable VHT capabilities (default: false) (bool)
```

---

### Post by joaofl on 2017-02-13
[TABLE]
[TR]
[TD="class: votecell"][/TD]
[TD="class: answercell"]I've managed to make it work. It is simular to [this]("http://askubuntu.com/questions/636712/logitech-mx-anywhere-2-mouse-pairs-but-doesnt-do-anything/660918#660918") but it did not work with sspmode at first. So I tried doing this before pairing using the GUI, and it worked.

  ```
$ sudo hciconfig hci0 down
$ sudo hciconfig hci0 up
$ sudo hciconfig hci0 noauth 
     
[/TD]
[/TR]
[/TABLE]

```

---

