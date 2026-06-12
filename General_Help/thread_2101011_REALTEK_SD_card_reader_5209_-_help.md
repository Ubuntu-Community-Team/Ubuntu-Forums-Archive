---
title: "REALTEK SD card reader 5209 - help"
date: 2013-01-03
forum: General Help
---

### Post by ranjan_mg on 2013-01-03
I am using ubuntu 12.10 - My SD card reader does not work at all. When I insert SD card nothing happens. 

Here is the lspci output
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader (rev 01)
05:00.0 USB controller: Etron Technology, Inc. EJ168 USB 3.0 Host Controller (rev 01)
06:00.0 Network controller: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe


It looks I am using rts_pstor module ..

lsmod | grep rts
rts_pstor             433804  0 



modinfo rts_pstor
filename:       /lib/modules/3.5.0-17-generic/kernel/drivers/staging/rts_pstor/rts_pstor.ko
version:        v1.10
license:        GPL
description:    Realtek PCI-Express card reader driver
srcversion:     9C23B27E4677E61398C0251
alias:          pci:v000010ECd00005288sv*sd*bcFFsc*i*
alias:          pci:v000010ECd00005209sv*sd*bcFFsc*i*
alias:          pci:v000010ECd00005208sv*sd*bcFFsc*i*
depends:        
staging:        Y
intree:         Y
vermagic:       3.5.0-17-generic SMP mod_unload modversions 
parm:           delay_use:seconds to delay before using a new device (uint)
parm:           ss_en:enable selective suspend (int)
parm:           ss_interval:Interval to enter ss state in seconds (int)
parm:           auto_delink_en:enable auto delink (int)
parm:           aspm_l0s_l1_en:enable device aspm (byte)
parm:           msi_en:enable msi (int)



From kernel log

Jan  3 11:24:22 ubuntu kernel: [ 1445.939271] rtsx_acquire_irq: chip->msi_en = 0, pci->irq = 17
Jan  3 11:24:22 ubuntu kernel: [ 1446.137688] scsi11 : SCSI emulation for PCI-Express Mass Storage devices
Jan  3 11:24:22 ubuntu kernel: [ 1446.137847] rts_pstor: waiting for device to settle before scanning
Jan  3 11:24:23 ubuntu kernel: [ 1447.132633] rts_pstor: device scan complete
Jan  3 11:24:23 ubuntu kernel: [ 1447.132832] scsi 11:0:0:0: >Direct-Access     Generic- xD/SD/M.S.       1.00 PQ: 0 ANSI: 0 CCS
Jan  3 11:24:23 ubuntu kernel: [ 1447.133103] sd 11:0:0:0: >Attached scsi generic sg2 type 0
Jan  3 11:24:23 ubuntu kernel: [ 1447.134752] sd 11:0:0:0: >[sdb] Attached SCSI removable disk


It is as if the card was not insterted correctly but works fine on windows


Any help is greatly appreciated..

thanks

---

### Post by cptncatholic on 2013-02-27
I had this exact same problem.

Found this solution: [http://askubuntu.com/questions/258533/realtek-card-reader-not-working/261504#261504](http://askubuntu.com/questions/258533/realtek-card-reader-not-working/261504#261504)

Piece of cake!

TC

---

