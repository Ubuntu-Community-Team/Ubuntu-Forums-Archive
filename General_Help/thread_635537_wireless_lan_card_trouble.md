---
title: "wireless lan card trouble"
date: 2007-12-08
forum: General Help
---

### Post by eipi1 on 2007-12-08
I have a Linksys WMP54G and I am running Ubuntu 7.10 (2.6.22.14).

I have downloaded the driver from Relink 
:[http://www.ralinktech.com.tw/data/drivers/2007_1003_RT61_Linux_STA_v1.1.1.0.tgz](http://www.ralinktech.com.tw/data/drivers/2007_1003_RT61_Linux_STA_v1.1.1.0.tgz)

and I have followed the directions in the readme which unzips (see listing at end)

MY PROBLEM is at step 7. ( $/sbin/insmod rt61.ko)

 I get:

'insmod: error inserting './rt61.ko': -1 Unknown symbol in module'

it seems similar to a post back in May 2006 (ubuntuforums.org/showthread.php?t=182009)

I don't know how to revert to an older Kernal (even if it would fix the problem) because this is a new install.

Please help.






====================

1> $tar -xvzf RT61_Linux_STA_Drv_x.x.x.x.tar.gz
    go to "./RT61_Linux_STA_Drv_x.x.x.x/Module" directory.
    
2> $cp Makefile.4  ./Makefile       # [kernel 2.4]
    or
   $cp Makefile.6  ./Makefile       # [kernel 2.6]
    or
   $cp Makefile.RTL865x ./Makefile  #  big endian platform
   
3> [kernel 2.4]
    $chmod 755 Configure
    $make config         # config build linux os version

4> $make all            # compile driver source code

5> $cp rt2561.bin /etc/Wireless/RT61STA/	# copy firmware
   $cp rt2561s.bin /etc/Wireless/RT61STA/
   $cp rt2661.bin /etc/Wireless/RT61STA/

6>  $dos2unix rt61sta.dat
    $cp rt61sta.dat  /etc/Wireless/RT61STA/rt61sta.dat       
    # !!!check if it is a binary file before loading !!!  
    
7> $load                
    #[kernel 2.4]
    #    $/sbin/insmod rt61.o
    #    $/sbin/ifconfig ra0 inet YOUR_IP up
        
    #[kernel 2.6]
    #    $/sbin/insmod rt61.ko
    #    $/sbin/ifconfig ra0 inet YOUR_IP up

        
Note: Script functionality:
load            load module to kernel
unload          unload module from kernel
Configure       retrieve linux version

---

### Post by bettlebrox on 2007-12-08
I think this module is already in the Ubuntu kernel?

[INDENT]$ modinfo rt61pci 
filename:       /lib/modules/2.6.22-14-generic/ubuntu/wireless/rt2x00/rt61pci.ko
license:        GPL
firmware:       rt2661.bin
firmware:       rt2561s.bin
firmware:       rt2561.bin
**description:    Ralink RT61 PCI & PCMCIA Wireless LAN driver.**
version:        2.0.4
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     916A8D32F139220D9CB02DA
alias:          pci:v00001814d00000401sv*sd*bc*sc*i*
alias:          pci:v00001814d00000302sv*sd*bc*sc*i*
alias:          pci:v00001814d00000301sv*sd*bc*sc*i*
depends:        rt2x00pci,rt2x00lib,mac80211,eeprom_93cx6
vermagic:       2.6.22-14-generic SMP mod_unload 586 
[/INDENT]

---

### Post by eipi1 on 2007-12-09
Right you are. I had seen some google material about the version in the package being buggy and I have been having a bad time with it so I thought I try a new driver fresh from Relink. But now I get this "Unknown symbol in module" problem.

My problem probably has nothing to do with the driver, but rather my stupidity. I am going to post a detailed description of the issue to the beginner's forum under "wireless woes".

---

### Post by bettlebrox on 2007-12-10
what does "modinfo rt61" or "modinfo rt61.ko" show?

This probably won't make any difference, but does "modporbe rt61" do?

---

