---
title: "insmod: ERROR: could not insert module &amp;&amp; Invalid module format"
date: 2014-11-06
forum: General Help
---

### Post by michael210 on 2014-11-06
Hallo every one, i just tryed to compile a Kernel module and after i issue this command:
```

sudo insmod $HOME/Kernel-Modules/Kernel-Build/drivers/net/wireless/ath/ath9k/ath9k.ko

```
i got the following:
> 
insmod: ERROR: could not insert module /home/michi/Kernel-Modules/Kernel-Build/drivers/net/wireless/ath/ath9k/ath9k.ko: Invalid module format

.
Here is what i did:
1
```

currentkernel="-"$(uname -r|sed 's/[0-9].[0-9].[0-9]-//' )

```
2
```

newkernel="NEW=$currentkernel"

```
3
```

mkdir -p $HOME/Kernel-Modules/{Kernel-Build,Kernel-Source}

```
4
```

cd $HOME/Kernel-Modules/Kernel-Build/

```
5
```

cp /boot/config-`uname -r`  .config

```
6
```

cp /usr/src/linux-headers$currentkernel*/Module.symvers ./

```
7
```

Downloading Kernel-3.17.2 >> $HOME/Kernel-Modules/Kernel-Source

```
8
```

cd $HOME/Kernel-Modules/Kernel-Source

```
9
```

tar -xJvf linux*.tar.xz

```
10
```

cd linux*

```
11
```

yes "" | make $newkernel O=$HOME/Kernel-Modules/Kernel-Build oldconfig

```
12
```

make $newkernel O=$HOME/Kernel-Modules/Kernel-Build prepare

```
13
```

make $newkernel O=$HOME/Kernel-Modules/Kernel-Build outputmakefile

```
14
```

make $newkernel O=$HOME/Kernel-Modules/Kernel-Build archprepare

```
15
```

make $newkernel O=$HOME/Kernel-Modules/Kernel-Build modules SUBDIRS=scripts

```
16
```

make $newkernel O=$HOME/Kernel-Modules/Kernel-Build modules SUBDIRS=drivers/net/wireless/ath

```
17
```

cd $HOME/Kernel-Modules/Kernel-Build/drivers/net/wireless/ath/ath9k && ls

```
.
> 
hb.o         ath9k_common.mod.c  calib.o           htc_drv_init.o
ani.o         ath9k_common.mod.o  channel.o           htc_drv_main.o
antenna.o     ath9k_common.o      common-beacon.o   htc_drv_txrx.o
ar5008_phy.o     ath9k_htc.ko         common-debug.o    htc_hst.o
ar9002_calib.o     ath9k_htc.mod.c     common-init.o     hw.o
ar9002_hw.o     ath9k_htc.mod.o     common.o           init.o
ar9002_mac.o     ath9k_htc.o         debug.o           link.o
ar9002_phy.o     ath9k_hw.ko         eeprom_4k.o       mac.o
ar9003_calib.o     ath9k_hw.mod.c      eeprom_9287.o     main.o
ar9003_eeprom.o  ath9k_hw.mod.o      eeprom_def.o      modules.order
ar9003_hw.o     ath9k_hw.o         eeprom.o           pci.o
ar9003_mac.o     **ath9k.ko**         gpio.o           recv.o
ar9003_paprd.o     ath9k.mod.c         hif_usb.o           spectral.o
ar9003_phy.o     ath9k.mod.o         htc_drv_beacon.o  wmi.o
ar9003_rtt.o     ath9k.o         htc_drv_debug.o   xmit.o
ath9k_common.ko  beacon.o         htc_drv_gpio.o


.
```

hexdump -C ath9k.ko | tail

```
> 
0056d5e0  61 63 68 65 73 00 61 74  68 39 6b 5f 68 77 5f 69  |aches.ath9k_hw_i|
0056d5f0  6e 69 74 00 61 74 68 5f  63 68 61 6e 63 74 78 5f  |nit.ath_chanctx_|
0056d600  63 68 65 63 6b 5f 61 63  74 69 76 65 00 69 65 65  |check_active.iee|
0056d610  65 38 30 32 31 31 5f 63  73 61 5f 66 69 6e 69 73  |e80211_csa_finis|
0056d620  68 00 61 74 68 39 6b 5f  68 77 5f 73 65 74 5f 74  |h.ath9k_hw_set_t|
0056d630  78 71 5f 70 72 6f 70 73  00 61 72 39 30 30 33 5f  |xq_props.ar9003_|
0056d640  70 61 70 72 64 5f 69 73  5f 64 6f 6e 65 00 61 74  |paprd_is_done.at|
0056d650  68 5f 69 6e 69 74 5f 6c  65 64 73 00 61 74 68 5f  |h_init_leds.ath_|
0056d660  63 68 61 6e 63 74 78 5f  69 6e 69 74 00           |chanctx_init.|
0056d66d


.
as you can see i succeded to compile the new Module.
.
Helping Infos..
```

lsb_release -a

```

> 
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

.
```
uname -a
```
> Linux Michael 3.17.2 #2 SMP Wed Nov 5 13:34:57 CET 2014 x86_64 x86_64 x86_64 GNU/Linux
The kernel i compilled my self [using this method.]("http://ubuntuforums.org/showthread.php?t=2247673&p=13139619#post13139619")
Linux Headers:
```
ls /usr/src/
```
> linux-headers-3.17.2-031702  linux-headers-3.17.2-031702-generic.
.
As you can see i use Kernel 3.17.2, i downloaded kernel3.17.2 Source code...and i use kernel-headers-3.17.2.
please help me to understand whats wrong here.
.

** Modinfo on the new Module:**
> filename:       /home/michi/Kernel-Modules/Kernel-Build/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     E28224DE6671D5847096B45
alias:          pci:v0000168Cd00000036sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001028sd0000020Ebc*sc*i*
alias:          pci:v0000168Cd00000036sv00001043sd000085F2bc*sc*i*
alias:          pci:v0000168Cd00000036sv000017AAsd00004026bc*sc*i*
alias:          pci:v0000168Cd00000036sv000017AAsd00003026bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000105Bsd0000E081bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000105Bsd0000E07Fbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000185Fsd0000A120bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000185Fsd00003027bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001B9Asd000028A2bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001B9Asd00002810bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Fsd00007202bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001A3Bsd00002182bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001A3Bsd0000213Bbc*sc*i*
alias:          pci:v0000168Cd00000036sv00001A3Bsd00002130bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000692bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000832bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000612bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000652bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000642bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd0000302Cbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd00003027bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Dsd0000411Ebc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Dsd0000411Dbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Dsd0000411Cbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Dsd0000411Bbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Dsd0000411Abc*sc*i*
alias:          pci:v0000168Cd00000036sv00001028sd0000020Cbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000103Csd00002005bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000103Csd0000217Fbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000103Csd000018E3bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001A3Bsd0000213Abc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000682bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd000006A2bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000662bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000672bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000622bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000185Fsd00003028bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000105Bsd0000E069bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd0000302Bbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd00003026bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd00003025bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001A3Bsd0000218Abc*sc*i*
alias:          pci:v0000168Cd00000036sv00001B9Asd000028A1bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001B9Asd00002812bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001B9Asd00002811bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00006671bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000842bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd000006B2bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000632bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000185Fsd0000A119bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000105Bsd0000E068bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001A3Bsd00002176bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd00003028bc*sc*i*
alias:          pci:v0000168Cd00000037sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000034sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000030sv00001A56sd00002003bc*sc*i*
alias:          pci:v0000168Cd00000034sv000010CFsd00001783bc*sc*i*
alias:          pci:v0000168Cd00000034sv000014CDsd00000064bc*sc*i*
alias:          pci:v0000168Cd00000034sv000014CDsd00000063bc*sc*i*
alias:          pci:v0000168Cd00000034sv0000103Csd00001864bc*sc*i*
alias:          pci:v0000168Cd00000034sv000011ADsd00006641bc*sc*i*
alias:          pci:v0000168Cd00000034sv000011ADsd00006631bc*sc*i*
alias:          pci:v0000168Cd00000034sv00001043sd0000850Ebc*sc*i*
alias:          pci:v0000168Cd00000034sv00001A3Bsd00002110bc*sc*i*
alias:          pci:v0000168Cd00000034sv00001969sd00000091bc*sc*i*
alias:          pci:v0000168Cd00000034sv000017AAsd00003214bc*sc*i*
alias:          pci:v0000168Cd00000034sv0000168Csd00003117bc*sc*i*
alias:          pci:v0000168Cd00000034sv000011ADsd00006661bc*sc*i*
alias:          pci:v0000168Cd00000034sv00001A3Bsd00002116bc*sc*i*
alias:          pci:v0000168Cd00000033sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000032sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001043sd0000850Dbc*sc*i*
alias:          pci:v0000168Cd00000032sv00001B9Asd00001C01bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001B9Asd00001C00bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001F95bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001195bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001F86bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001186bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001B9Asd00002001bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001B9Asd00002000bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Fsd00007197bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000105Bsd0000E04Fbc*sc*i*
alias:          pci:v0000168Cd00000032sv0000105Bsd0000E04Ebc*sc*i*
alias:          pci:v0000168Cd00000032sv000011ADsd00006628bc*sc*i*
alias:          pci:v0000168Cd00000032sv000011ADsd00006627bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001C56sd00004001bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002100bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002C97bc*sc*i*
alias:          pci:v0000168Cd00000032sv000017AAsd00003219bc*sc*i*
alias:          pci:v0000168Cd00000032sv000017AAsd00003218bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000C708bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000C680bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000C706bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000410Fbc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000410Ebc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000410Dbc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd00004106bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd00004105bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000185Fsd00003027bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000185Fsd00003119bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000168Csd00003122bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000168Csd00003119bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000105Bsd0000E075bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002152bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd0000126Abc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002126bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001237bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002086bc*sc*i*
alias:          pci:v0000168Cd00000030sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000030sv00001A56sd00002001bc*sc*i*
alias:          pci:v0000168Cd00000030sv00001A56sd00002000bc*sc*i*
alias:          pci:v0000168Cd0000002Esv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Bsv00001A3Bsd00002C37bc*sc*i*
alias:          pci:v0000168Cd0000002Asv000010CFsd00001536bc*sc*i*
alias:          pci:v0000168Cd0000002Asv000010CFsd0000147Dbc*sc*i*
alias:          pci:v0000168Cd0000002Asv000010CFsd0000147Cbc*sc*i*
alias:          pci:v0000168Cd0000002Asv0000185Fsd0000309Dbc*sc*i*
alias:          pci:v0000168Cd0000002Asv00001A32sd00000306bc*sc*i*
alias:          pci:v0000168Cd0000002Asv000011ADsd00006642bc*sc*i*
alias:          pci:v0000168Cd0000002Asv000011ADsd00006632bc*sc*i*
alias:          pci:v0000168Cd0000002Asv0000105Bsd0000E01Fbc*sc*i*
alias:          pci:v0000168Cd0000002Asv00001A3Bsd00001C71bc*sc*i*
alias:          pci:v0000168Cd0000002Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000029sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000027sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
alias:          platform:qca953x_wmac
alias:          platform:qca955x_wmac
alias:          platform:ar934x_wmac
alias:          platform:ar933x_wmac
alias:          platform:ath9k
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
vermagic:       3.17.2 SMP mod_unload modversions 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_chanctx:Enable channel context for concurrency (int)


.
```
dmesg
```
> 
[ 3298.664696] ath9k: disagrees about version of symbol module_layout
[ 6238.991980] ath9k: disagrees about version of symbol module_layout
[ 7921.576676] ath9k: disagrees about version of symbol module_layout

Thank you all.

---

