---
title: "DRI seems to conflict with madwifi"
date: 2006-07-24
forum: General Help
---

### Post by house on 2006-07-24
hi
lately i figured something very strange. i set up AIGLX with DRI and compiz etc. so after installing the dri-kernel package my wireless was gone. i rebootet to see wats gona hapen. 
ok .. there it was agen .. but DRI was broken. so i installed it again rebooted - then DRI worked but wlan was gone. cool. hehe. 
i use the madwifi driver. here is what i get when i try to modprobe ath_pci: 

modprobe ath_pci 
WARNING: Error inserting ath_rate_sample (/lib/modules/2.6.15-26-686/madwifi/ath_rate_sample.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting ath_pci (/lib/modules/2.6.15-26-686/madwifi/ath_pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)


so i checked the dmesg and it looked like this: 

[17179599.224000] ath_rate_sample: Unknown symbol ath_hal_computetxtime
[17179599.280000] ath_pci: Unknown symbol ath_rate_tx_complete
[17179599.280000] ath_pci: Unknown symbol _ath_hal_attach
[17179599.280000] ath_pci: Unknown symbol ath_rate_attach
[17179599.284000] ath_pci: Unknown symbol ath_rate_newassoc
[17179599.284000] ath_pci: Unknown symbol ath_hal_computetxtime
[17179599.284000] ath_pci: Unknown symbol ath_rate_dynamic_sysctl_register
[17179599.284000] ath_pci: Unknown symbol ath_hal_mhz2ieee
[17179599.284000] ath_pci: Unknown symbol ath_hal_detach
[17179599.284000] ath_pci: Unknown symbol ath_hal_probe
[17179599.284000] ath_pci: Unknown symbol ath_rate_node_cleanup
[17179599.284000] ath_pci: Unknown symbol ath_rate_detach
[17179599.288000] ath_pci: Unknown symbol ath_rate_node_init
[17179599.288000] ath_pci: Unknown symbol ath_rate_findrate
[17179599.288000] ath_pci: Unknown symbol ath_hal_init_channels
[17179599.288000] ath_pci: Unknown symbol ath_rate_newstate
[17179599.288000] ath_pci: Unknown symbol ath_rate_setupxtxdesc
[17179599.288000] ath_pci: Unknown symbol ath_hal_getwirelessmodes
[17179635.952000] bridge-ath0: peer interface ath0 not found, will wait for it to come up
[17179635.952000] bridge-ath0: attached
[17186646.680000] ath_rate_sample: Unknown symbol ath_hal_computetxtime
[17186646.684000] ath_pci: Unknown symbol ath_rate_tx_complete
[17186646.684000] ath_pci: Unknown symbol _ath_hal_attach
[17186646.688000] ath_pci: Unknown symbol ath_rate_attach
[17186646.688000] ath_pci: Unknown symbol ath_rate_newassoc
[17186646.688000] ath_pci: Unknown symbol ath_hal_computetxtime
[17186646.688000] ath_pci: Unknown symbol ath_rate_dynamic_sysctl_register
[17186646.692000] ath_pci: Unknown symbol ath_hal_mhz2ieee
[17186646.692000] ath_pci: Unknown symbol ath_hal_detach
[17186646.696000] ath_pci: Unknown symbol ath_hal_probe
[17186646.696000] ath_pci: Unknown symbol ath_rate_node_cleanup
[17186646.696000] ath_pci: Unknown symbol ath_rate_detach
[17186646.700000] ath_pci: Unknown symbol ath_rate_node_init
[17186646.700000] ath_pci: Unknown symbol ath_rate_findrate
[17186646.704000] ath_pci: Unknown symbol ath_hal_init_channels
[17186646.704000] ath_pci: Unknown symbol ath_rate_newstate
[17186646.704000] ath_pci: Unknown symbol ath_rate_setupxtxdesc
[17186646.704000] ath_pci: Unknown symbol ath_hal_getwirelessmodes

any ideas ? did anyone have something like that before ?

regards

---

