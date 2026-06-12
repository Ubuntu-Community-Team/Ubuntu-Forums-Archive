---
title: "Unable to boot in normal mode"
date: 2023-08-10
forum: General Help
---

### Post by thowisk on 2023-08-10
I have Ubuntu 22.04 alongside Windows 10 with a dual boot. I rarely use Windows and I didn't use it between the instance where Ubuntu worked perfectly fine and the one where it spotted working.

After picking Ubuntu from the grub boot selector I am left with these logs

```

[ 8.167925] amdgpu 0000:04:00.0: amdgpu: ring comp_1.3.0 uses VM inv eng 8 on hub 0
[ 8.167928] amdgpu 0000:04:00.0: amdgpu: ring comp_1.0.1 uses VM inv eng 9 on hub 0
[ 8.167931] amdgpu 0000:04:00.0: amdgpu: ring comp_1.1.1 uses VM inv eng 10 on hub 0
[ 8.167934] amdgpu 0000:04:00.0: amdgpu: ring comp_1.2.1 uses VM inv eng 11 on hub 0
[ 8.167937] amdgpu 0000:04:00.0: amdgpu: ring comp_1.3.1 uses VM inv eng 12 on hub 0
[ 8.167940] amdgpu 0000:04:00.0: amdgpu: ring kiq_2.1.0 uses VM inv eng 13 on hub 0
[ 8.167943] amdgpu 0000:04:00.0: amdgpu: ring sdma0 uses VM inv eng 0 on hub 1
[ 8.167946] amdgpu 0000:04:00.0: amdgpu: ring vcn_dec uses VM inv eng 1 on hub 1
[ 8.167949] amdgpu 0000:04:00.0: amdgpu: ring vcn_enc0 uses VM inv eng 4 on hub 1
[ 8.167951] amdgpu 0000:04:00.0: amdgpu: ring vcn_enc1 uses VM inv eng 5 on hub 1
[ 8.167954] amdgpu 0000:04:00.0: amdgpu: ring jpeg_dec uses VM inv eng 6 on hub 1
[ 8.169665] [drm] Initialized amdgpu 3.49.0 20150101 for 0000:04:00.0 on minor 1
[ 8.174552] fbcon: amdgpudrmfb (fb0) is primary device
[ 8.174775] [drm] DSC precompute is not needed.
[ 8.237198] Console: switching to colour frame buffer device 240x67
[ 8.256536] amdgpu 0000:04:00.0: [drm] fb0: amdgpudrmfb frame buffer device
[ 9.320876] loop31: detected capacity change from 0 to 8
[10.258347] usb 3-4: reset full-speed USB device number 4 using xhci_hcd 
[10.430882] kauditd_printk_skb: 60 callbacks suppressed
[10.430885] audit: type=1326 audit(1691679128.508:94): auid-4294967295 uid=0 gid=0 ses=4294967295 subj=snap.cups.cupsd pid=1516 conn="cupsd" exe="/snap/cups/980/sbin/cupsd" sig=0 arch=c000003e syscall=93 compat=0 ip=0x7f5f43385c4b code=0x50000
[11.171856] wlp2s0: authenticate with dc:f8:b9:a2:ad:43 
[11.171939] wlp2s0: 80 MHz not supported, disabling VHT 
[11.181422] wlp2s0: send auth to dc:f8:b9:a2:ad:43 (try 1/3) 
[11.255007] wlp2s0: authenticated
[11.258014] wlp2s0: associate with dc:f8:b9:a2:ad:43 (try 1/3) 
[11.318996] wlp2s0: RX AssocResp from dc:f8:b9:a2:ad:43 (capab=0x1411 status=0 aid=5)
[11.328802] w1p2s0: associated         
[11.332901] wlp2s0: Liniting IX power to 30 (30 - 0) dBm as advertised by dc:f8:b9:02:ad:43
[11.459354] iwlwifi 0000:02:00.0: Unhandled alg: 0x707
[11.459660] iwlwifi 0000:02:00.0: Unhandled alg: 0x707
[11.459910] iwlwifi 0000:02:00.0: Unhandled alg: 0x707
[11.466049] audit: type=1326 audit(1691679129.544:95): auid=4294967295 uid=0 gid=0 ses=4294967295 subj=snap.cups.cupsd pid-1517 comm="cups-proxyd" exe="/snap/cups/980/sbin/cups-proxyd" sig=0 arch=c000003e syscall=314 compat=0 ip=0x7f1f6cee1a3d code=0x50000
[11.517401] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready
[11.902349] audit: type=1400 audit(1691679129.980:96): apparmor="STATUS" operation="profile_load" profile="unconfined" name="docker-default" pid=1722 conn="apparmor_parser"
[11.988534] bridge: filtering via arp/ip/ip6tables is no longer available by default. Update your scripts to load br_netfilter if you need this. 
[11.990428] Bridge firewalling registered
[12.052595] Initializing XFRM netlink socket 
[12.695603] cups-proxyd[1517]: segfault at 18 ip 00005641bb32bd75 sp 00007fff8a8179b0 error 4 in cups-proxyd[5641bb328000+7000] 1ikely on CPU 10 (core 5, socket 0)
[12.695677] Code: 83 3d ee b2 00 00 00 41 54 55 48 89 fd 53 0f 85 f4 00 00 00 48 8d 1d 69 3d 00 00 48 63 45 1c 48 89 df 48 c1 e0 05 48 03 45 08 <48> 8b 50 18 8b 70 14 e8 0f d0 ff ff 44 8b 65 18 48 89 c7 45 85 e4 
[12.785310] br-cf334e67903c: port 1(veth281689e) entered blocking state
[12.785329] br-cf334e67903c: port 1(veth281689e) entered disabled state
[12.785406] device veth281689e entered promiscuous mode 
[12.785526] br-cf334e67903c: port 1(veth281689e) entered blocking state
[12.785541] br-cf334e67903c: port 1(veth281689e) entered forwarding state
[12.785603] br-cf334e67903c: port 1(veth281689e) entered disabled state 
[13.182677] eth0: renamed from veth570193c
[13.222484] IPv6: ADDRCONF(NETDEV_CHANGE): veth281689e: link becomes ready
[13.222522] br-cf334e67903c: port 1(veth281689e) entered blocking state
[13.222533] br-cf334e67903c: port 1(veth281689e) entered forwarding state      
[13.222620] IPv6: ADDRCONF(NETDEV_CHANGE): br-cf334e67903c: link becomes ready

```
[I]Done with GoogleLens so there may be some typos

[/I]After a few seconds the logs are gone and I only have a black screen with what it seems to be a frozen character cursor but I can't interact with it.

Booting in safe mode works (**nomodeset**) just fine but I suppose some features are disabled in this mode and even thought it runs smoothly, I would prefer to use the normal mode.
Apparently, it is related to the service **cups-proxyd** but once in safe mode this service is nowhere to be found on the system so I really don't know what to do.

If you have any ideas on how to solve this issue I'll be happy to know

Here is my system configuration in case it would be useful
Ref: ZEPHYRUS-G14-GA401IU-110T
GTX 1660Ti
Ryzen 7 4800HS
2x8Go 3200MHz
500Go NVMe

Thanks,

thows

---

### Post by Rubi1200 on 2023-08-17
Have you tried booting an older kernel to see if the issue persists?

---

### Post by MAFoElffen on 2023-08-18
You seem to have an AMD GPU that is having graphics driver challenges. While booted from using the "nomodeset" boot parameter, when you start "Software & Updates" and go to the "Additional Drivers" tab, what drivers does it show?

As other boot parameters, instead of using "nomodeset", what happens if you use "radeon.modeset=0 amdgpu.noretry=0 amdgpu.dc=1"... These options will try to clear the way for the amdgpu driver module to load.

---

### Post by #&amp;thj^% on 2023-08-18
OP has both GPU's
> Here is my system configuration in case it would be useful
GTX 1660Ti
We know the Nvidia Drivers on some wrecks the system ATM

---

