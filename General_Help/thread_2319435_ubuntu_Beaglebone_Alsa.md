---
title: "ubuntu Beaglebone Alsa"
date: 2016-04-04
forum: General Help
---

### Post by fanny3 on 2016-04-04
hello, 
I have installed ubuntu 14.04.3 on my Beaglebone throught this link: 
[http://elinux.org/Beagleboard:Ubuntu_On_BeagleBone_Black#Ubuntu_Precise_On_Micro_SD](http://elinux.org/Beagleboard:Ubuntu_On_BeagleBone_Black#Ubuntu_Precise_On_Micro_SD)

But I didn't have alsa so I did: 
sudo apt-get install alsa-base 
but not each time i do any alsa command i have segmentation fault. 
Here is dmesg message :

[ 1699.742308] wlan0: deauthenticating from 14:dd:a9:c8:f1:58 by local choice (Reason: 3=DEAUTH_LEAVING)
[ 1700.058101] cfg80211: Exceeded CRDA call max attempts. Not calling CRDA
[ 1720.435658] rtl8192cu: MAC auto ON okay!
[ 1720.486419] rtl8192cu: Tx queue select: 0x05
[ 1721.182590] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1723.354679] wlan0: authenticate with 14:dd:a9:c8:f1:58
[ 1723.397876] wlan0: send auth to 14:dd:a9:c8:f1:58 (try 1/3)
[ 1723.425978] wlan0: authenticated
[ 1723.440315] wlan0: associate with 14:dd:a9:c8:f1:58 (try 1/3)
[ 1723.479635] wlan0: RX AssocResp from 14:dd:a9:c8:f1:58 (capab=0x1411 status=0 aid=10)
[ 1723.503656] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1723.509400] wlan0: associated
[ 1782.194046] Unable to handle kernel paging request at virtual address bf011098
[ 1782.194057] pgd = ddd50000
[ 1782.194076] [bf011098] *pgd=9cfce811, *pte=00000000, *ppte=00000000
[ 1782.194094] Internal error: Oops: 7 [#12] PREEMPT SMP ARM
[ 1782.194211] Modules linked in: snd_soc_tlv320aic3x(+) snd_soc_evm(+) spidev c_can_platform c_can can_dev spi_omap2_mcspi tieqep pwm_tiecap pwm_tiehrpwm ctr ccm usb_f_ecm g_ether usb_f_rndis u_ether libcomposite arc4 rtl8192cu rtl_usb rtl8192c_common rtlwifi pruss_remoteproc mac80211 cfg80211 rfkill omap_rng rng_core tilcdc snd_soc_davinci_mcasp snd_soc_edma tda998x binfmt_misc snd_soc_hdmi_codec uio_pdrv_genirq uio [last unloaded: snd_soc_tlv320aic3x]
[ 1782.194229] CPU: 0 PID: 5357 Comm: alsamixer Tainted: G      D W       4.1.15-ti-rt-r40 #1
[ 1782.194234] Hardware name: Generic AM33XX (Flattened Device Tree)
[ 1782.194241] task: dd8d5740 ti: dddfc000 task.ti: dddfc000
[ 1782.194276] PC is at try_module_get+0x2c/0x15c
[ 1782.194288] LR is at get_parent_ip+0x14/0x30
[ 1782.194298] pc : [<c00d4098>]    lr : [<c0070b64>]    psr: 600f0013
[ 1782.194298] sp : dddfdd08  ip : dddfdcd8  fp : dddfdd24
[ 1782.194304] r10: 00000000  r9 : 00000008  r8 : dc9b57d0
[ 1782.194310] r7 : 00000002  r6 : c084ed14  r5 : bf011098  r4 : dc16d000
[ 1782.194317] r3 : dd8d5740  r2 : dddfdcf0  r1 : c0c65504  r0 : 00000000
[ 1782.194326] Flags: nZCv  IRQs on  FIQs on  Mode SVC_32  ISA ARM  Segment user
[ 1782.194333] Control: 10c5387d  Table: 9dd50019  DAC: 00000015
[ 1782.194340] Process alsamixer (pid: 5357, stack limit = 0xdddfc218)
[ 1782.194347] Stack: (0xdddfdd08 to 0xdddfe000)
[ 1782.194360] dd00:                   dd8d5740 dc16d000 ddee1f00 dc085e00 dddfdd44 dddfdd28
[ 1782.194372] dd20: c084ed14 c00d4078 c0a7cf3c ddee1f00 dc085e00 00000002 dddfdd6c dddfdd48
[ 1782.194384] dd40: c0849398 c084ecc8 ddaa54c0 dc9b57d0 ddee1f00 c0a7cd4c dc12b380 00000000
[ 1782.194396] dd60: dddfdd94 dddfdd70 c01b4048 c08492f0 00000000 00000000 ddee1f00 dc9b57d0
[ 1782.194408] dd80: ddee1f08 c01b3f8c dddfddc4 dddfdd98 c01adc58 c01b3f98 dc12b380 ddee1f00
[ 1782.194420] dda0: dc9b57d0 dc12b380 dddfde88 00000000 dd62bf00 00000000 dddfdde4 dddfddc8
[ 1782.194432] ddc0: c01ae960 c01ada80 dd8d5740 dddfded0 dddfdf5c 00000000 dddfde5c dddfdde8
[ 1782.194444] dde0: c01bbe60 c01ae8fc 00000001 00000000 ddb7c010 dd62bf00 dcebd7d0 c05528bc
[ 1782.194456] de00: dddfde34 dddfde10 c05528bc dddfded0 00000000 00000000 00000000 00000024
[ 1782.194468] de20: ddee1f00 00000000 dddfde5c dc9b57d0 c01bd950 dddfded0 dddfdf5c dc017000
[ 1782.194480] de40: dddfde88 c00108c4 00000000 ddee1f00 dddfdec4 dddfde60 c01be618 c01bbaa4
[ 1782.194492] de60: dddfde84 dc017000 dc8b6240 dddfdee0 dc059540 dc8b6840 dddfde94 dddfde88
[ 1782.194504] de80: c015adac 00000000 ddb7c010 dd7e3780 c0070b64 c00930cc 00002384 dddfdf5c
[ 1782.194516] dea0: 00000001 dc017000 ffffff9c c00108c4 dddfc000 00000000 dddfdf4c dddfdec8
[ 1782.194528] dec0: c01bfc08 c01be594 00000041 dd8d5740 ddb7c010 dd7e3780 35c12985 00000009
[ 1782.194540] dee0: dc017019 c006f210 00000000 dd7596e0 dc9b57d0 00000101 00000004 00000176
[ 1782.194552] df00: 00000000 00000000 00000000 dde18540 00000000 00080000 ffffff9c dc017000
[ 1782.194563] df20: 00000005 c00108c4 dddfc000 00000000 00080000 ffffff9c dc017000 00000003
[ 1782.194575] df40: dddfdf94 dddfdf50 c01aecbc c01bfbd8 dddfdf6c dddfdf60 c0094fe0 00000000
[ 1782.194587] df60: dddf0000 00000024 00000100 00000001 0001a3a8 bedbace4 1dfa2f00 00000005
[ 1782.194599] df80: c00108c4 dddfc000 dddfdfa4 dddfdf98 c01aedac c01aebac 00000000 dddfdfa8
[ 1782.194611] dfa0: c0010720 c01aed8c 0001a3a8 bedbace4 bedbace4 00080000 00000280 1dfa2f00
[ 1782.194623] dfc0: 0001a3a8 bedbace4 1dfa2f00 00000005 01e863d8 b6efa7cc bedbaeec b6ef56b8
[ 1782.194635] dfe0: 00000000 bedbab2c b6e91a6d b6df2ea6 400f0030 bedbace4 00000000 00000000
[ 1782.194677] [<c00d4098>] (try_module_get) from [<c084ed14>] (snd_ctl_open+0x58/0x194)
[ 1782.194710] [<c084ed14>] (snd_ctl_open) from [<c0849398>] (snd_open+0xb4/0x158)
[ 1782.194738] [<c0849398>] (snd_open) from [<c01b4048>] (chrdev_open+0xbc/0x1a8)
[ 1782.194755] [<c01b4048>] (chrdev_open) from [<c01adc58>] (do_dentry_open+0x1e4/0x310)
[ 1782.194770] [<c01adc58>] (do_dentry_open) from [<c01ae960>] (vfs_open+0x70/0x78)
[ 1782.194789] [<c01ae960>] (vfs_open) from [<c01bbe60>] (do_last+0x3c8/0xf08)
[ 1782.194805] [<c01bbe60>] (do_last) from [<c01be618>] (path_openat+0x90/0x618)
[ 1782.194820] [<c01be618>] (path_openat) from [<c01bfc08>] (do_filp_open+0x3c/0x90)
[ 1782.194835] [<c01bfc08>] (do_filp_open) from [<c01aecbc>] (do_sys_open+0x11c/0x1e0)
[ 1782.194849] [<c01aecbc>] (do_sys_open) from [<c01aedac>] (SyS_open+0x2c/0x30)
[ 1782.194872] [<c01aedac>] (SyS_open) from [<c0010720>] (ret_fast_syscall+0x0/0x3c)
[ 1782.194887] Code: 03a04001 0a00002a e3a00001 ebfe72b9 (e5953000) 
[ 1782.623963] ---[ end trace 000000000000001a ]---
[ 1782.623981] note: alsamixer[5357] exited with preempt_count 1


Thank you for your help

---

