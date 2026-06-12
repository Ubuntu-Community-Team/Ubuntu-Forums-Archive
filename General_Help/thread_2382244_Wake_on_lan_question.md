---
title: "Wake on lan question"
date: 2018-01-10
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2018-01-10
I know i have WOL enabled, i use it every day to wake from sleep mode
this morning i shut the system down cause of the kernel update i just received (cause it has the meltdown patch)
i just tried to use WOL to boot and nope...
my power did not go out, according to my alarm clock
```
lspci | grep Gigabit
05:00.0 Ethernet controller: Intel Corporation 82572EI Gigabit Ethernet Controller (Copper) (rev 06)
sudo ethtool eth3
Settings for eth3:
    Supported ports: [ TP ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Advertised pause frame use: No
    Advertised auto-negotiation: Yes
    Speed: 1000Mb/s
    Duplex: Full
    Port: Twisted Pair
    PHYAD: 1
    Transceiver: internal
    Auto-negotiation: on
    MDI-X: on (auto)
    Supports Wake-on: pumbg
    Wake-on: g
    Current message level: 0x00000007 (7)
                   drv probe link
    Link detected: yes
```
this card is on a PCIe slot (my onboard LAN only supports WOL on windows...)

is there a reason it would not work if i use shutdown instead of suspend

the only thing making this a big deal is i have not gotten around to adding a toggle switch to my case to toggle the front panel buttons (my cats like to press buttons) so i have the buttons unplugged in the case

EDIT: found a option to enable power on by PCIe Devices that was off, guess it was not needed for sleep mode

---

