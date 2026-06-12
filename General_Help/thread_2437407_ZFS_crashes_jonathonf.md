---
title: "ZFS crashes jonathonf"
date: 2020-02-23
forum: General Help
---

### Post by BatteryKing on 2020-02-23
I have been trying out the Jonathonf based PPA for OpenZFS 8.x under Ubuntu MATE 18.04 LTS.  After installing both the utils and the kernel DKMS packages and rebooting everything looks good.  For example running `zpool --version` returns:
zfs-0.8.3-1ubuntu3~18.04.york1.0
zfs-kmod-0.8.3-1ubuntu3~18.04.york1.0

Systems:
1. Xeon E5-1650v4, X99 WS board, 128 GB ECC RDIMMs.
2. Core i7-7700K, Z270 board, 32 GB non-ECC RAM.
3. Both systems are using the Nvidia 440.59 proprietary graphics driver.

So I created a RAIDZ level 2 zpool and an encrypted dataset on top and used the zfs commands to decrypt and mount the array / dataset on somewhat unreliable drives as I am seeing how much ZFS can take.  All is good so far.  No I start writing to the array.  Somewhere in the 900 GB to 1.5 TB range in my Xorg server crashes.  The first time all of the drives stayed in the array.  The second time a drive popped out of the zpool (want to make sure it can handle failures after all, which is why the somewhat unreliable drives are being used), but still had enough stay in the zpool drives to maintain integrity and zpool reports good stats on the remaining drives.  I can still remote in and see the system is still running and even still doing the data transfer.  The first time this happened on my main Linux box, which has been a super reliable system and has an Intel Xeon processor and ECC RAM in it, the system crashed while POSTing on reboot.  I had to flip the switch in the back (let the bad bits drain out), and then power back on to get it to come all the way back up again.  Seeing this seemed to have crashed my main Linux box and having the box go down like that caused a lot of problems, I booted up my dual boot Windows box in Linux mode and setup and repeated the test.  The dual boot system had the Xorg server crash in about the same place of the same transfer, except this time I was transfering over the network to the disk array attached to the dual boot system instead of direct attached to my main Linux box.  Here is a snippet I got out of the syslog file from the dual boot system:

```

Feb 23 08:11:19 Velnecious kernel: [74772.894428] Xorg: page allocation failure: order:4, mode:0x14040c0(GFP_KERNEL|__GFP_COMP), nodemask=(null)
Feb 23 08:11:19 Velnecious kernel: [74772.894429] Xorg cpuset=/ mems_allowed=0
Feb 23 08:11:19 Velnecious kernel: [74772.894431] CPU: 2 PID: 1207 Comm: Xorg Tainted: P           OE    4.15.0-88-generic #88-Ubuntu
Feb 23 08:11:19 Velnecious kernel: [74772.894431] Hardware name: System manufacturer System Product Name/TUF Z270 MARK 1, BIOS 1301 03/14/2018
Feb 23 08:11:19 Velnecious kernel: [74772.894432] Call Trace:
Feb 23 08:11:19 Velnecious kernel: [74772.894435]  dump_stack+0x6d/0x8e
Feb 23 08:11:19 Velnecious kernel: [74772.894437]  warn_alloc+0xff/0x1a0
Feb 23 08:11:19 Velnecious kernel: [74772.894438]  ? __alloc_pages_direct_compact+0x51/0x100
Feb 23 08:11:19 Velnecious kernel: [74772.894439]  __alloc_pages_slowpath+0xdc5/0xe00
Feb 23 08:11:19 Velnecious kernel: [74772.894441]  ? __wake_up_common+0x73/0x130
Feb 23 08:11:19 Velnecious kernel: [74772.894442]  __alloc_pages_nodemask+0x29a/0x2c0
Feb 23 08:11:19 Velnecious kernel: [74772.894443]  alloc_pages_current+0x6a/0xe0
Feb 23 08:11:19 Velnecious kernel: [74772.894445]  kmalloc_order+0x18/0x40
Feb 23 08:11:19 Velnecious kernel: [74772.894446]  kmalloc_order_trace+0x24/0xb0
Feb 23 08:11:19 Velnecious kernel: [74772.894453]  ? _nv000491kms+0x50/0x50 [nvidia_modeset]
Feb 23 08:11:19 Velnecious kernel: [74772.894455]  __kmalloc+0x209/0x220
Feb 23 08:11:19 Velnecious kernel: [74772.894460]  ? _nv000491kms+0x50/0x50 [nvidia_modeset]
Feb 23 08:11:19 Velnecious kernel: [74772.894465]  nvkms_alloc+0x25/0x60 [nvidia_modeset]
Feb 23 08:11:19 Velnecious kernel: [74772.894473]  _nv002520kms+0x16/0x30 [nvidia_modeset]
Feb 23 08:11:19 Velnecious kernel: [74772.894474] WARNING: kernel stack frame pointer at 000000000bdd39ad in Xorg:1207 has bad value 000000001800d573
Feb 23 08:11:19 Velnecious kernel: [74772.894475] unwind stack type:0 next_sp:          (null) mask:0x2 graph_idx:0
Feb 23 08:11:19 Velnecious kernel: [74772.894475] 00000000058c2212: ffffaf934411f870 (0xffffaf934411f870)
Feb 23 08:11:19 Velnecious kernel: [74772.894477] 00000000fe69ff28: ffffffffb5031b53 (show_trace_log_lvl+0x223/0x3d0)
Feb 23 08:11:19 Velnecious kernel: [74772.894477] 00000000411f001c: 0000000000000000 ...
Feb 23 08:11:19 Velnecious kernel: [74772.894479] 00000000fd75a8ac: ffffffffb60b78f0 (.LC0+0x4d0/0x670)
Feb 23 08:11:19 Velnecious kernel: [74772.894479] 000000008db46139: ffff9d730f974680 (0xffff9d730f974680)
Feb 23 08:11:19 Velnecious kernel: [74772.894486] 00000000b626e54d: ffffffffc1815a56 (_nv002520kms+0x16/0x30 [nvidia_modeset])
Feb 23 08:11:19 Velnecious kernel: [74772.894487] 00000000e9ff8aa9: 00000000014040c0 (0x14040c0)
Feb 23 08:11:19 Velnecious kernel: [74772.894487] 00000000ccc502a4: 0000000000000002 (0x2)
Feb 23 08:11:19 Velnecious kernel: [74772.894487] 0000000059891b24: 0000000000000001 (0x1)
Feb 23 08:11:19 Velnecious kernel: [74772.894488] 000000004e26ad16: ffffaf934411c000 (0xffffaf934411c000)
Feb 23 08:11:19 Velnecious kernel: [74772.894488] 000000004f444576: ffffaf9344120000 (0xffffaf9344120000)
Feb 23 08:11:19 Velnecious kernel: [74772.894488] 00000000c66958d8: 0000000000000000 ...
Feb 23 08:11:19 Velnecious kernel: [74772.894488] 000000005df6809e: ffffaf934411c000 (0xffffaf934411c000)
Feb 23 08:11:19 Velnecious kernel: [74772.894489] 0000000097f83e19: ffffaf9344120000 (0xffffaf9344120000)
Feb 23 08:11:19 Velnecious kernel: [74772.894489] 000000000b8b153b: 0000000000000000 ...
Feb 23 08:11:19 Velnecious kernel: [74772.894489] 000000009b2ddfd3: 0000000000000002 (0x2)
Feb 23 08:11:19 Velnecious kernel: [74772.894489] 00000000fc00c864: ffff9d730f974680 (0xffff9d730f974680)
Feb 23 08:11:19 Velnecious kernel: [74772.894490] 00000000ddb7a454: 0000010100000000 (0x10100000000)
Feb 23 08:11:19 Velnecious kernel: [74772.894490] 0000000028da6fab: ffffaf934411fba0 (0xffffaf934411fba0)
Feb 23 08:11:19 Velnecious kernel: [74772.894490] 000000001c6d8f2b: ffffaf934411f780 (0xffffaf934411f780)
Feb 23 08:11:19 Velnecious kernel: [74772.894497] 0000000039a20b68: ffffffffc1815a56 (_nv002520kms+0x16/0x30 [nvidia_modeset])
Feb 23 08:11:19 Velnecious kernel: [74772.894497] 0000000027455b2d: 0000000000000000 ...
Feb 23 08:11:19 Velnecious kernel: [74772.894497] 000000006bbea814: 3d6c0a3135a13700 (0x3d6c0a3135a13700)
Feb 23 08:11:19 Velnecious kernel: [74772.894498] 00000000c35d7e41: 0000000000000286 (0x286)
Feb 23 08:11:19 Velnecious kernel: [74772.894498] 0000000062b7f2f8: 0000000000000000 ...
Feb 23 08:11:19 Velnecious kernel: [74772.894498] 0000000012dfb8c0: 00000000014040c0 (0x14040c0)
Feb 23 08:11:19 Velnecious kernel: [74772.894499] 00000000d15ff423: ffffaf934411fa68 (0xffffaf934411fa68)
Feb 23 08:11:19 Velnecious kernel: [74772.894499] 0000000027d92715: ffffaf934411fa68 (0xffffaf934411fa68)
Feb 23 08:11:19 Velnecious kernel: [74772.894499] 000000008de9822b: ffffaf934411f880 (0xffffaf934411f880)
Feb 23 08:11:19 Velnecious kernel: [74772.894500] 00000000c861cf33: ffffffffb5031d34 (show_stack+0x34/0x50)
Feb 23 08:11:19 Velnecious kernel: [74772.894500] 000000006aeb9603: ffffaf934411f8a0 (0xffffaf934411f8a0)
Feb 23 08:11:19 Velnecious kernel: [74772.894501] 00000000c1092b94: ffffffffb599b8ef (dump_stack+0x6d/0x8e)
Feb 23 08:11:19 Velnecious kernel: [74772.894501] 00000000e525deeb: 0000000000000000 ...
Feb 23 08:11:19 Velnecious kernel: [74772.894501] 000000008427aced: ffff9d730f974680 (0xffff9d730f974680)
Feb 23 08:11:19 Velnecious kernel: [74772.894501] 000000006b5a96aa: ffffaf934411f950 (0xffffaf934411f950)
Feb 23 08:11:19 Velnecious kernel: [74772.894502] 000000009bda3422: ffffffffb51e27df (warn_alloc+0xff/0x1a0)
Feb 23 08:11:19 Velnecious kernel: [74772.894503] 00000000125fd009: 0000000000000000 ...
Feb 23 08:11:19 Velnecious kernel: [74772.894503] 00000000befb85be: ffffaf934411f960 (0xffffaf934411f960)
Feb 23 08:11:19 Velnecious kernel: [74772.894504] 000000001da58d95: ffffffffb60e7c28 (.LC15+0x68/0x930)
Feb 23 08:11:19 Velnecious kernel: [74772.894504] 000000009fcdbe09: 014040c0b520d579 (0x14040c0b520d579)
Feb 23 08:11:19 Velnecious kernel: [74772.894505] 000000006e21ff14: ffffffffb60e7c28 (.LC15+0x68/0x930)
Feb 23 08:11:19 Velnecious kernel: [74772.894505] 000000008da1772e: ffffaf934411f8e0 (0xffffaf934411f8e0)
Feb 23 08:11:19 Velnecious kernel: [74772.894505] 00000000ee6681fd: 0000000000000018 (0x18)
Feb 23 08:11:19 Velnecious kernel: [74772.894506] 00000000532c9b25: ffffaf934411f960 (0xffffaf934411f960)
Feb 23 08:11:19 Velnecious kernel: [74772.894506] 0000000014638ada: ffffaf934411f900 (0xffffaf934411f900)
Feb 23 08:11:19 Velnecious kernel: [74772.894506] 0000000032636b0f: 3d6c0a3135a13700 (0x3d6c0a3135a13700)
Feb 23 08:11:19 Velnecious kernel: [74772.894507] 00000000c235bfe6: 0000000000000040 (0x40)
Feb 23 08:11:19 Velnecious kernel: [74772.894507] 0000000090681890: ffffaf934411f950 (0xffffaf934411f950)
Feb 23 08:11:19 Velnecious kernel: [74772.894508] 0000000059d681b0: ffffffffb51e2551 (__alloc_pages_direct_compact+0x51/0x100)
Feb 23 08:11:19 Velnecious kernel: [74772.894508] 00000000ce57df46: 0000000000000004 (0x4)
Feb 23 08:11:19 Velnecious kernel: [74772.894508] 000000008d16e978: 0000000000000080 (0x80)
Feb 23 08:11:19 Velnecious kernel: [74772.894509] 000000004b4b6dc1: 0000000000000f83 (0xf83)
Feb 23 08:11:19 Velnecious kernel: [74772.894509] 00000000d9e40f52: 0000000000000001 (0x1)
Feb 23 08:11:19 Velnecious kernel: [74772.894509] 00000000273897ef: ffffaf934411f8d0 (0xffffaf934411f8d0)
Feb 23 08:11:19 Velnecious kernel: [74772.894509] 0000000057fa7a88: 0000000000000040 (0x40)
Feb 23 08:11:19 Velnecious kernel: [74772.894510] 000000005477fa66: 00000000014040c0 (0x14040c0)
Feb 23 08:11:19 Velnecious kernel: [74772.894510] 00000000416011f1: ffffaf934411fa58 (0xffffaf934411fa58)
Feb 23 08:11:19 Velnecious kernel: [74772.894511] 00000000c668c6fb: ffffffffb51e3645 (__alloc_pages_slowpath+0xdc5/0xe00)
Feb 23 08:11:19 Velnecious kernel: [74772.894511] 00000000ea74388d: 0000005000000001 (0x5000000001)
Feb 23 08:11:19 Velnecious kernel: [74772.894512] 00000000af26b423: 0000004000000004 (0x4000000004)
Feb 23 08:11:19 Velnecious kernel: [74772.894512] 000000004cb0d743: 0000001000000000 (0x1000000000)
Feb 23 08:11:19 Velnecious kernel: [74772.894512] 0000000070149ad4: 0000000000000000 ...
Feb 23 08:11:19 Velnecious kernel: [74772.894512] 0000000000eeb322: 00000000010240c0 (0x10240c0)
Feb 23 08:11:19 Velnecious kernel: [74772.894513] 000000006a1362f1: 0040000001000000 (0x40000001000000)
Feb 23 08:11:19 Velnecious kernel: [74772.894513] 00000000312044cb: 0000000000000290 (0x290)
Feb 23 08:11:19 Velnecious kernel: [74772.894513] 000000000450a685: 0000000000000260 (0x260)
Feb 23 08:11:19 Velnecious kernel: [74772.894514] 0000000028e032e7: 0000000000000000 ...
Feb 23 08:11:19 Velnecious kernel: [74772.894514] 000000005c3e9e7a: 0000000000000585 (0x585)
Feb 23 08:11:19 Velnecious kernel: [74772.894514] 00000000b1e1de40: 0000000000000001 (0x1)
Feb 23 08:11:19 Velnecious kernel: [74772.894514] 00000000d5a1ee8b: ffff9d7300000040 (0xffff9d7300000040)
Feb 23 08:11:19 Velnecious kernel: [74772.894515] 0000000021847bf0: 00000040014040c0 (0x40014040c0)
Feb 23 08:11:19 Velnecious kernel: [74772.894515] 00000000f51fe627: ffff9d7336bd5f28 (0xffff9d7336bd5f28)
Feb 23 08:11:19 Velnecious kernel: [74772.894515] 00000000126d6a29: 00000010014040c0 (0x10014040c0)
Feb 23 08:11:19 Velnecious kernel: [74772.894516] 000000008a1df664: ffff9d7336bd5d00 (0xffff9d7336bd5d00)
Feb 23 08:11:19 Velnecious kernel: [74772.894516] 000000002e0448cb: 0000000000000004 (0x4)
Feb 23 08:11:19 Velnecious kernel: [74772.894516] 000000001e6eaf41: 0000000236bd5ef8 (0x236bd5ef8)
Feb 23 08:11:19 Velnecious kernel: [74772.894516] 00000000d0ed8422: 0000000000000000 ...
Feb 23 08:11:19 Velnecious kernel: [74772.894517] 000000009d27c014: 0000000000000004 (0x4)
Feb 23 08:11:19 Velnecious kernel: [74772.894517] 000000003e98e976: ffffffff00000000 (0xffffffff00000000)
Feb 23 08:11:19 Velnecious kernel: [74772.894517] 000000005e55782d: ffff9d7336bd70b0 (0xffff9d7336bd70b0)
Feb 23 08:11:19 Velnecious kernel: [74772.894518] 000000000a00d670: ffffaf9300000001 (0xffffaf9300000001)
Feb 23 08:11:19 Velnecious kernel: [74772.894519] 00000000458ba6a4: ffffffffb50d68d3 (__wake_up_common+0x73/0x130)
Feb 23 08:11:19 Velnecious kernel: [74772.894519] 000000006960e3fb: 3d6c0a3135a13700 (0x3d6c0a3135a13700)
Feb 23 08:11:19 Velnecious kernel: [74772.894519] 00000000e52456b7: 00000000014040c0 (0x14040c0)
Feb 23 08:11:19 Velnecious kernel: [74772.894519] 00000000609f7130: 0000000000000004 (0x4)
Feb 23 08:11:19 Velnecious kernel: [74772.894520] 000000009a564607: 00000000014040c0 (0x14040c0)
Feb 23 08:11:19 Velnecious kernel: [74772.894520] 000000001e2ec76d: 0000000000000000 ...
Feb 23 08:11:19 Velnecious kernel: [74772.894520] 000000001c7dfceb: ffffaf934411fac0 (0xffffaf934411fac0)
Feb 23 08:11:19 Velnecious kernel: [74772.894521] 000000008f45fac4: ffffffffb51e391a (__alloc_pages_nodemask+0x29a/0x2c0)
Feb 23 08:11:19 Velnecious kernel: [74772.894521] 00000000b7f1c1aa: ffff9d7336bd7080 (0xffff9d7336bd7080)
Feb 23 08:11:19 Velnecious kernel: [74772.894522] 00000000a794ff9c: 0000000000000000 ...
Feb 23 08:11:19 Velnecious kernel: [74772.894522] 00000000c22a9ff8: ffff9d7336bd7080 (0xffff9d7336bd7080)
Feb 23 08:11:19 Velnecious kernel: [74772.894522] 000000005f8e1b64: 0000000200000000 (0x200000000)
Feb 23 08:11:19 Velnecious kernel: [74772.894522] 00000000fecfe854: 0000000000000000 ...
Feb 23 08:11:19 Velnecious kernel: [74772.894523] 000000005fcf0b8d: 3d6c0a3135a13700 (0x3d6c0a3135a13700)
Feb 23 08:11:19 Velnecious kernel: [74772.894524] 000000009449fd97: ffffffffb6a7e4c0 (policy_zone+0x20/0x20)
Feb 23 08:11:19 Velnecious kernel: [74772.894524] 000000001df1ea5d: 00000000014040c0 (0x14040c0)
Feb 23 08:11:19 Velnecious kernel: [74772.894525] 000000004dd1f0bb: 0000000000000004 (0x4)
Feb 23 08:11:19 Velnecious kernel: [74772.894525] 00000000d815347c: 0000000000000000 ...
Feb 23 08:11:19 Velnecious kernel: [74772.894525] 000000009b4f5a74: ffffaf934411faf0 (0xffffaf934411faf0)
Feb 23 08:11:19 Velnecious kernel: [74772.894526] 000000009df2a1d2: ffffffffb52421da (alloc_pages_current+0x6a/0xe0)
Feb 23 08:11:19 Velnecious kernel: [74772.894527] 00000000af76492b: 000000000000ec10 (0xec10)
Feb 23 08:11:19 Velnecious kernel: [74772.894527] 00000000f5908ae4: 000000000000ec10 (0xec10)
Feb 23 08:11:19 Velnecious kernel: [74772.894527] 00000000ac8c037e: 00000000014000c0 (0x14000c0)
Feb 23 08:11:19 Velnecious kernel: [74772.894528] 000000002a48e833: 000000000000ec10 (0xec10)
Feb 23 08:11:19 Velnecious kernel: [74772.894528] 0000000018f3e9ba: ffffaf934411fb00 (0xffffaf934411fb00)
Feb 23 08:11:19 Velnecious kernel: [74772.894529] 00000000eb2845ff: ffffffffb5207808 (kmalloc_order+0x18/0x40)
Feb 23 08:11:19 Velnecious kernel: [74772.894529] 0000000092d42fe1: ffffaf934411fb40 (0xffffaf934411fb40)
Feb 23 08:11:19 Velnecious kernel: [74772.894530] 000000006bc5977f: ffffffffb5207854 (kmalloc_order_trace+0x24/0xb0)
Feb 23 08:11:19 Velnecious kernel: [74772.894530] 00000000aab07bea: 0000000000005c27 (0x5c27)
Feb 23 08:11:19 Velnecious kernel: [74772.894530] 0000000063bf330f: 000000000000ec10 (0xec10)
Feb 23 08:11:19 Velnecious kernel: [74772.894531] 000000000044e0f3: 0000000000000001 (0x1)
Feb 23 08:11:19 Velnecious kernel: [74772.894531] 0000000040696567: 00000000014000c0 (0x14000c0)
Feb 23 08:11:19 Velnecious kernel: [74772.894531] 000000008c1a7758: 000000000000ec10 (0xec10)
Feb 23 08:11:19 Velnecious kernel: [74772.894536] 00000000e0f21a9a: ffffffffc17dad60 (_nv000491kms+0x50/0x50 [nvidia_modeset])
Feb 23 08:11:19 Velnecious kernel: [74772.894537] 00000000bab84129: ffffaf934411fb80 (0xffffaf934411fb80)
Feb 23 08:11:19 Velnecious kernel: [74772.894538] 00000000d25788d8: ffffffffb5251c79 (__kmalloc+0x209/0x220)
Feb 23 08:11:19 Velnecious kernel: [74772.894538] 0000000073a3e037: ffff9d7336bd5f38 (0xffff9d7336bd5f38)
Feb 23 08:11:19 Velnecious kernel: [74772.894538] 000000007e401aea: 000000000000ec10 (0xec10)
Feb 23 08:11:19 Velnecious kernel: [74772.894539] 0000000043524d71: 0000000000000001 (0x1)
Feb 23 08:11:19 Velnecious kernel: [74772.894539] 000000003bdb053c: ffff9d6d651d8008 (0xffff9d6d651d8008)
Feb 23 08:11:19 Velnecious kernel: [74772.894539] 00000000c945f471: ffff9d7306eea008 (0xffff9d7306eea008)
Feb 23 08:11:19 Velnecious kernel: [74772.894544] 00000000d5b1e496: ffffffffc17dad60 (_nv000491kms+0x50/0x50 [nvidia_modeset])
Feb 23 08:11:19 Velnecious kernel: [74772.894545] 000000000b663295: ffffaf934411fba0 (0xffffaf934411fba0)
Feb 23 08:11:19 Velnecious kernel: [74772.894550] 000000000fb33deb: ffffffffc17d8375 (nvkms_alloc+0x25/0x60 [nvidia_modeset])
Feb 23 08:11:19 Velnecious kernel: [74772.894550] 0000000036bdd4df: 000000000000ec10 (0xec10)
Feb 23 08:11:19 Velnecious kernel: [74772.894550] 0000000080db2769: ffff9d7311278e08 (0xffff9d7311278e08)
Feb 23 08:11:19 Velnecious kernel: [74772.894550] 000000000bdd39ad: 0000000000000009 (0x9)
Feb 23 08:11:19 Velnecious kernel: [74772.894557] 00000000e2e45fd8: ffffffffc1815a56 (_nv002520kms+0x16/0x30 [nvidia_modeset])
Feb 23 08:11:19 Velnecious kernel: [74772.894557] 00000000fda2d2a2: ffff9d730a8b7008 (0xffff9d730a8b7008)
Feb 23 08:11:19 Velnecious kernel: [74772.894564] 0000000015e4d665: ffffffffc180bdb8 (_nv002627kms+0x68/0x1f70 [nvidia_modeset])
Feb 23 08:11:19 Velnecious kernel: [74772.894564] 00000000067d7f5a: ffff9d713ec30008 (0xffff9d713ec30008)
Feb 23 08:11:19 Velnecious kernel: [74772.894564] 00000000ea437e6f: ffff9d7336bd5ef8 (0xffff9d7336bd5ef8)
Feb 23 08:11:19 Velnecious kernel: [74772.894565] 00000000d5497405: ffff9d713ec35d60 (0xffff9d713ec35d60)
Feb 23 08:11:19 Velnecious kernel: [74772.894565] 0000000091783bc7: 0000000000000000 ...
Feb 23 08:11:19 Velnecious kernel: [74772.894565] 00000000fb3cbb98: 0000000000000003 (0x3)
Feb 23 08:11:19 Velnecious kernel: [74772.894565] 0000000021293940: 0001af9300000000 (0x1af9300000000)
Feb 23 08:11:19 Velnecious kernel: [74772.894566] 00000000efa5e9c9: ffff9d7336bd7080 (0xffff9d7336bd7080)
Feb 23 08:11:19 Velnecious kernel: [74772.894566] 00000000b8ab8293: 0000000000000001 (0x1)
Feb 23 08:11:19 Velnecious kernel: [74772.894566] 000000000ceb9eef: ffffaf934411fca0 (0xffffaf934411fca0)
Feb 23 08:11:19 Velnecious kernel: [74772.894567] 00000000cdfcc613: 3d6c0a3135a13700 (0x3d6c0a3135a13700)
Feb 23 08:11:19 Velnecious kernel: [74772.894567] 00000000e16f7c2e: 00000000014040c0 (0x14040c0)
Feb 23 08:11:19 Velnecious kernel: [74772.894567] 00000000127b7a65: 0000000000000003 (0x3)
Feb 23 08:11:19 Velnecious kernel: [74772.894567] 0000000002aa9646: 00000000014040c0 (0x14040c0)
Feb 23 08:11:19 Velnecious kernel: [74772.894568] 0000000072cc9cd3: ffff9d730a8b7008 (0xffff9d730a8b7008)
Feb 23 08:11:19 Velnecious kernel: [74772.894568] 00000000ac70f38a: 0000000000000001 (0x1)
Feb 23 08:11:19 Velnecious kernel: [74772.894568] 00000000d2b626e3: ffffaf934411fca0 (0xffffaf934411fca0)
Feb 23 08:11:19 Velnecious kernel: [74772.894569] 000000001462f718: ffffffffb51e379c (__alloc_pages_nodemask+0x11c/0x2c0)
Feb 23 08:11:19 Velnecious kernel: [74772.894570] 000000002e437ba2: ffff9d7336bd7080 (0xffff9d7336bd7080)
Feb 23 08:11:19 Velnecious kernel: [74772.894570] 00000000d7305693: 0000000000000000 ...
Feb 23 08:11:19 Velnecious kernel: [74772.894570] 000000002386eb34: ffff9d7336bd7080 (0xffff9d7336bd7080)
Feb 23 08:11:19 Velnecious kernel: [74772.894570] 000000005d75a6bf: 0000000200000000 (0x200000000)
Feb 23 08:11:19 Velnecious kernel: [74772.894571] 000000007934d2aa: 0000000000000000 ...
Feb 23 08:11:19 Velnecious kernel: [74772.894571] 00000000e063f093: 3d6c0a3135a13700 (0x3d6c0a3135a13700)
Feb 23 08:11:19 Velnecious kernel: [74772.894572] 00000000ca3cac09: ffffffffb6a7e4c0 (policy_zone+0x20/0x20)
Feb 23 08:11:19 Velnecious kernel: [74772.894572] 00000000696e523f: 00000000014040c0 (0x14040c0)
Feb 23 08:11:19 Velnecious kernel: [74772.894572] 000000007b43f035: 0000000000000003 (0x3)
Feb 23 08:11:19 Velnecious kernel: [74772.894572] 00000000b3d347f3: 0000000000000000 ...
Feb 23 08:11:19 Velnecious kernel: [74772.894573] 00000000ed195f7c: 0000000000000003 (0x3)
Feb 23 08:11:19 Velnecious kernel: [74772.894573] 00000000d16b812d: ffffaf934411fcd0 (0xffffaf934411fcd0)
Feb 23 08:11:19 Velnecious kernel: [74772.894574] 00000000f3a7be65: ffffffffb52421da (alloc_pages_current+0x6a/0xe0)
Feb 23 08:11:19 Velnecious kernel: [74772.894574] 00000000338b51f3: 0000000000005f88 (0x5f88)
Feb 23 08:11:19 Velnecious kernel: [74772.894574] 0000000093d325df: 0000000000005f88 (0x5f88)
Feb 23 08:11:19 Velnecious kernel: [74772.894575] 000000002dbf05f3: 00000000014000c0 (0x14000c0)
Feb 23 08:11:19 Velnecious kernel: [74772.894575] 000000002096cd8f: 0000000000005f88 (0x5f88)
Feb 23 08:11:19 Velnecious kernel: [74772.894575] 00000000d3db746f: ffffaf934411fce0 (0xffffaf934411fce0)
Feb 23 08:11:19 Velnecious kernel: [74772.894576] 00000000328d6311: ffffffffb5207808 (kmalloc_order+0x18/0x40)
Feb 23 08:11:19 Velnecious kernel: [74772.894577] 000000000f19c4c3: ffffaf934411fd20 (0xffffaf934411fd20)
Feb 23 08:11:19 Velnecious kernel: [74772.894577] 00000000215286c5: ffffffffb5207854 (kmalloc_order_trace+0x24/0xb0)
Feb 23 08:11:19 Velnecious kernel: [74772.894578] 00000000fd12f4c3: 00007fff14ba7180 (0x7fff14ba7180)
Feb 23 08:11:19 Velnecious kernel: [74772.894578] 000000009ce38d41: 0000000000005f88 (0x5f88)
Feb 23 08:11:19 Velnecious kernel: [74772.894578] 00000000e9440041: 0000000000000001 (0x1)
Feb 23 08:11:19 Velnecious kernel: [74772.894579] 000000007bbdd6c4: 00000000014000c0 (0x14000c0)
Feb 23 08:11:19 Velnecious kernel: [74772.894579] 00000000a8031aaf: 0000000000005f88 (0x5f88)
Feb 23 08:11:19 Velnecious kernel: [74772.894584] 00000000f50a5f48: ffffffffc17dad60 (_nv000491kms+0x50/0x50 [nvidia_modeset])
Feb 23 08:11:19 Velnecious kernel: [74772.894584] 00000000dbbcd4bc: 0000000000000000 ...
Feb 23 08:11:19 Velnecious kernel: [74772.894584] 000000006bb8f40c: 0000000000000003 (0x3)
Feb 23 08:11:19 Velnecious kernel: [74772.894585] 000000005fa79edf: ffff9d713ec35b90 (0xffff9d713ec35b90)
Feb 23 08:11:19 Velnecious kernel: [74772.894590] 00000000da74dd04: ffffffffc17db271 (_nv000620kms+0x31/0xe0 [nvidia_modeset])
Feb 23 08:11:19 Velnecious kernel: [74772.894590] 00000000e1934422: 00000008b54adc2e (0x8b54adc2e)
Feb 23 08:11:19 Velnecious kernel: [74772.894590] 00000000253c9d28: ffff9d713ec30008 (0xffff9d713ec30008)
Feb 23 08:11:19 Velnecious kernel: [74772.894591] 00000000124a64cd: 0000000000005d58 (0x5d58)
Feb 23 08:11:19 Velnecious kernel: [74772.894591] 00000000c3145d0a: 0000000000000001 (0x1)
Feb 23 08:11:19 Velnecious kernel: [74772.894591] 000000007a8a817a: 0000000000000009 (0x9)
Feb 23 08:11:19 Velnecious kernel: [74772.894592] 0000000036ca0763: ffff9d7311278e08 (0xffff9d7311278e08)
Feb 23 08:11:19 Velnecious kernel: [74772.894592] 0000000047143ded: 00007fff14b9eae0 (0x7fff14b9eae0)
Feb 23 08:11:19 Velnecious kernel: [74772.894599] 000000007989a74a: ffffffffc1892220 (_nv002113kms+0x80/0xfffffffffffe2e60 [nvidia_modeset])
Feb 23 08:11:19 Velnecious kernel: [74772.894605] 000000006f5f93e7: ffffffffc17dad60 (_nv000491kms+0x50/0x50 [nvidia_modeset])
Feb 23 08:11:19 Velnecious kernel: [74772.894610] 0000000061eae871: ffffffffc17dc6b6 (nvKmsIoctl+0x96/0x1d0 [nvidia_modeset])
Feb 23 08:11:19 Velnecious kernel: [74772.894610] 00000000ab0ed470: ffff9d713ec30008 (0xffff9d713ec30008)
Feb 23 08:11:19 Velnecious kernel: [74772.894610] 00000000f790fd55: 0000000000005f80 (0x5f80)
Feb 23 08:11:19 Velnecious kernel: [74772.894611] 00000000b9d889b9: 0000000000000292 (0x292)
Feb 23 08:11:19 Velnecious kernel: [74772.894611] 0000000066fdc65d: ffff9d730b2e0a80 (0xffff9d730b2e0a80)
Feb 23 08:11:19 Velnecious kernel: [74772.894611] 0000000044bacdf4: ffffaf934411fe10 (0xffffaf934411fe10)
Feb 23 08:11:19 Velnecious kernel: [74772.894612] 00000000b20312b3: 0000000000000009 (0x9)
Feb 23 08:11:19 Velnecious kernel: [74772.894612] 00000000d95bffc1: 00007fff14b9eae0 (0x7fff14b9eae0)
Feb 23 08:11:19 Velnecious kernel: [74772.894612] 00000000bc1a81f4: 0000000000005f80 (0x5f80)
Feb 23 08:11:19 Velnecious kernel: [74772.894612] 000000009bd25998: 00007fff14b98b20 (0x7fff14b98b20)
Feb 23 08:11:19 Velnecious kernel: [74772.894618] 00000000dcc1da6f: ffffffffc17d8f32 (nvkms_ioctl_common+0x42/0x80 [nvidia_modeset])
Feb 23 08:11:19 Velnecious kernel: [74772.894624] 0000000033a2fa4e: ffffffffc18cbce0 (nvkms_kthread_q+0x40/0xfffffffffffa9360 [nvidia_modeset])
Feb 23 08:11:19 Velnecious kernel: [74772.894624] 000000005a0109a5: ffff9d730b2e0a80 (0xffff9d730b2e0a80)
Feb 23 08:11:19 Velnecious kernel: [74772.894625] 000000005f972fad: ffff9d730b34fa00 (0xffff9d730b34fa00)
Feb 23 08:11:19 Velnecious kernel: [74772.894625] 00000000104e3c72: 00000000c0106d00 (0xc0106d00)
Feb 23 08:11:19 Velnecious kernel: [74772.894625] 00000000e9e56501: ffffaf934411fe50 (0xffffaf934411fe50)
Feb 23 08:11:19 Velnecious kernel: [74772.894631] 000000008df2ede3: ffffffffc17d9037 (nvkms_ioctl+0xc7/0x100 [nvidia_modeset])
Feb 23 08:11:19 Velnecious kernel: [74772.894631] 000000008195a2af: 0000000000000040 (0x40)
Feb 23 08:11:19 Velnecious kernel: [74772.894631] 0000000063acd3a6: 00005f8000000009 (0x5f8000000009)
Feb 23 08:11:19 Velnecious kernel: [74772.894632] 000000005c5b7abe: 00007fff14b9eae0 (0x7fff14b9eae0)
Feb 23 08:11:19 Velnecious kernel: [74772.894632] 000000001ed7a34b: 3d6c0a3135a13700 (0x3d6c0a3135a13700)
Feb 23 08:11:19 Velnecious kernel: [74772.894632] 00000000c9c7d703: ffff9d7308d2ce50 (0xffff9d7308d2ce50)
Feb 23 08:11:19 Velnecious kernel: [74772.894632] 000000000f497590: 00007fff14b98b20 (0x7fff14b98b20)
Feb 23 08:11:19 Velnecious kernel: [74772.894633] 0000000094a3091e: ffffaf934411fe60 (0xffffaf934411fe60)
Feb 23 08:11:19 Velnecious kernel: [74772.894718] 00000000f5b7ddbc: ffffffffc0300082 (nvidia_frontend_unlocked_ioctl+0x42/0x50 [nvidia])
Feb 23 08:11:19 Velnecious kernel: [74772.894718] 00000000bed3dcf7: ffffaf934411fee8 (0xffffaf934411fee8)
Feb 23 08:11:19 Velnecious kernel: [74772.894719] 00000000060f69ca: ffffffffb52974b8 (do_vfs_ioctl+0xa8/0x630)
Feb 23 08:11:19 Velnecious kernel: [74772.894720] 000000007c6e2ae7: 0000000000000000 ...
Feb 23 08:11:19 Velnecious kernel: [74772.894720] 00000000a1658616: ffff9d730813d080 (0xffff9d730813d080)
Feb 23 08:11:19 Velnecious kernel: [74772.894720] 00000000d24db145: ffffaf934411ff18 (0xffffaf934411ff18)
Feb 23 08:11:19 Velnecious kernel: [74772.894721] 000000002e9f94e8: ffffffffb584caa0 (__sys_recvmsg+0x80/0x90)
Feb 23 08:11:19 Velnecious kernel: [74772.894722] 000000002dda534d: 0000002000000001 (0x2000000001)
Feb 23 08:11:19 Velnecious kernel: [74772.894722] 000000004015bcce: 0000000000000000 ...
Feb 23 08:11:19 Velnecious kernel: [74772.894722] 000000006fb5503f: ffffffff00000000 (0xffffffff00000000)
Feb 23 08:11:19 Velnecious kernel: [74772.894722] 000000003fbe7ae9: 0000000000000000 ...
Feb 23 08:11:19 Velnecious kernel: [74772.894723] 0000000056cba5de: 3d6c0a3135a13700 (0x3d6c0a3135a13700)
Feb 23 08:11:19 Velnecious kernel: [74772.894723] 0000000072c16c50: ffff9d730b34fa01 (0xffff9d730b34fa01)
Feb 23 08:11:19 Velnecious kernel: [74772.894723] 00000000079d9b52: ffff9d730b34fa00 (0xffff9d730b34fa00)
Feb 23 08:11:19 Velnecious kernel: [74772.894724] 000000003bd91a57: 0000000000000012 (0x12)
Feb 23 08:11:19 Velnecious kernel: [74772.894724] 000000009fb9fcfd: 00000000c0106d00 (0xc0106d00)
Feb 23 08:11:19 Velnecious kernel: [74772.894724] 0000000042f8ba4f: 00007fff14b98b20 (0x7fff14b98b20)
Feb 23 08:11:19 Velnecious kernel: [74772.894725] 00000000eb692a02: ffffaf934411ff28 (0xffffaf934411ff28)
Feb 23 08:11:19 Velnecious kernel: [74772.894725] 0000000031170d1c: ffffffffb5297ab9 (SyS_ioctl+0x79/0x90)
Feb 23 08:11:19 Velnecious kernel: [74772.894726] 00000000f654baa5: 3d6c0a3135a13700 (0x3d6c0a3135a13700)
Feb 23 08:11:19 Velnecious kernel: [74772.894726] 000000007dcb98b4: ffffaf934411ff58 (0xffffaf934411ff58)
Feb 23 08:11:19 Velnecious kernel: [74772.894726] 000000009d1de263: 0000000000000000 ...
Feb 23 08:11:19 Velnecious kernel: [74772.894726] 000000005b2e901a: ffffaf934411ff48 (0xffffaf934411ff48)
Feb 23 08:11:19 Velnecious kernel: [74772.894727] 0000000056514aea: ffffffffb5003bb3 (do_syscall_64+0x73/0x130)
Feb 23 08:11:19 Velnecious kernel: [74772.894728] 00000000f68890a0: 0000000000000000 ...
Feb 23 08:11:19 Velnecious kernel: [74772.894729] 00000000a539d6e5: ffffffffb5a00081 (entry_SYSCALL_64_after_hwframe+0x3d/0xa2)
Feb 23 08:11:19 Velnecious kernel: [74772.894729] 0000000028b30bc1: 0000000000000000 ...
Feb 23 08:11:19 Velnecious kernel: [74772.894730] 00000000b3095ac4: 0000000000000001 (0x1)
Feb 23 08:11:19 Velnecious kernel: [74772.894730] 000000003d56d7e9: 0000000000000800 (0x800)
Feb 23 08:11:19 Velnecious kernel: [74772.894730] 000000001277e0e0: 0000563149bb1930 (0x563149bb1930)
Feb 23 08:11:19 Velnecious kernel: [74772.894730] 0000000062306da3: 0000000000000012 (0x12)
Feb 23 08:11:19 Velnecious kernel: [74772.894731] 000000000e82f56d: 00007fff14b9eae0 (0x7fff14b9eae0)
Feb 23 08:11:19 Velnecious kernel: [74772.894731] 00000000f540ff70: 0000000000003246 (0x3246)
Feb 23 08:11:19 Velnecious kernel: [74772.894731] 00000000ddb69075: 0000000000000000 ...
Feb 23 08:11:19 Velnecious kernel: [74772.894732] 000000008eb78176: ffffffffffffffda (0xffffffffffffffda)
Feb 23 08:11:19 Velnecious kernel: [74772.894732] 000000009c38177a: 00007fc0d36b65d7 (0x7fc0d36b65d7)
Feb 23 08:11:19 Velnecious kernel: [74772.894732] 000000007bc078dd: 00007fff14b98b20 (0x7fff14b98b20)
Feb 23 08:11:19 Velnecious kernel: [74772.894732] 00000000564140ee: 00000000c0106d00 (0xc0106d00)
Feb 23 08:11:19 Velnecious kernel: [74772.894733] 000000008ef43beb: 0000000000000012 (0x12)
Feb 23 08:11:19 Velnecious kernel: [74772.894733] 00000000577022fb: 0000000000000010 (0x10)
Feb 23 08:11:19 Velnecious kernel: [74772.894733] 000000008f674d97: 00007fc0d36b65d7 (0x7fc0d36b65d7)
Feb 23 08:11:19 Velnecious kernel: [74772.894734] 00000000c1bc73ea: 0000000000000033 (0x33)
Feb 23 08:11:19 Velnecious kernel: [74772.894734] 00000000e2d4e912: 0000000000003246 (0x3246)
Feb 23 08:11:19 Velnecious kernel: [74772.894734] 0000000067cad63b: 00007fff14b98b18 (0x7fff14b98b18)
Feb 23 08:11:19 Velnecious kernel: [74772.894734] 000000007abd9b28: 000000000000002b (0x2b)
Feb 23 08:11:19 Velnecious kernel: [74772.894743]  ? _nv002627kms+0x68/0x1f70 [nvidia_modeset]
Feb 23 08:11:19 Velnecious kernel: [74772.894745]  ? __alloc_pages_nodemask+0x11c/0x2c0
Feb 23 08:11:19 Velnecious kernel: [74772.894747]  ? alloc_pages_current+0x6a/0xe0
Feb 23 08:11:19 Velnecious kernel: [74772.894748]  ? kmalloc_order+0x18/0x40
Feb 23 08:11:19 Velnecious kernel: [74772.894749]  ? kmalloc_order_trace+0x24/0xb0
Feb 23 08:11:19 Velnecious kernel: [74772.894754]  ? _nv000491kms+0x50/0x50 [nvidia_modeset]
Feb 23 08:11:19 Velnecious kernel: [74772.894759]  ? _nv000620kms+0x31/0xe0 [nvidia_modeset]
Feb 23 08:11:19 Velnecious kernel: [74772.894765]  ? _nv000491kms+0x50/0x50 [nvidia_modeset]
Feb 23 08:11:19 Velnecious kernel: [74772.894770]  ? nvKmsIoctl+0x96/0x1d0 [nvidia_modeset]
Feb 23 08:11:19 Velnecious kernel: [74772.894775]  ? nvkms_ioctl_common+0x42/0x80 [nvidia_modeset]
Feb 23 08:11:19 Velnecious kernel: [74772.894780]  ? nvkms_ioctl+0xc7/0x100 [nvidia_modeset]
Feb 23 08:11:19 Velnecious kernel: [74772.894861]  ? nvidia_frontend_unlocked_ioctl+0x42/0x50 [nvidia]
Feb 23 08:11:19 Velnecious kernel: [74772.894862]  ? do_vfs_ioctl+0xa8/0x630
Feb 23 08:11:19 Velnecious kernel: [74772.894863]  ? __sys_recvmsg+0x80/0x90
Feb 23 08:11:19 Velnecious kernel: [74772.894864]  ? SyS_ioctl+0x79/0x90
Feb 23 08:11:19 Velnecious kernel: [74772.894865]  ? do_syscall_64+0x73/0x130
Feb 23 08:11:19 Velnecious kernel: [74772.894866]  ? entry_SYSCALL_64_after_hwframe+0x3d/0xa2
Feb 23 08:11:19 Velnecious kernel: [74772.894867] Mem-Info:
Feb 23 08:11:19 Velnecious kernel: [74772.894869] active_anon:63153 inactive_anon:68834 isolated_anon:0
Feb 23 08:11:19 Velnecious kernel: [74772.894869]  active_file:202085 inactive_file:4532631 isolated_file:0
Feb 23 08:11:19 Velnecious kernel: [74772.894869]  unevictable:18478 dirty:270 writeback:0 unstable:0
Feb 23 08:11:19 Velnecious kernel: [74772.894869]  slab_reclaimable:104222 slab_unreclaimable:50834
Feb 23 08:11:19 Velnecious kernel: [74772.894869]  mapped:72308 shmem:26547 pagetables:7161 bounce:0
Feb 23 08:11:19 Velnecious kernel: [74772.894869]  free:152875 free_pcp:0 free_cma:0
Feb 23 08:11:19 Velnecious kernel: [74772.894870] Node 0 active_anon:252612kB inactive_anon:275336kB active_file:808340kB inactive_file:18130524kB unevictable:73912kB isolated(anon):0kB isolated(file):0kB mapped:289232kB dirty:1080kB writeback:0kB shmem:106188kB shmem_thp: 0kB shmem_pmdmapped: 0kB anon_thp: 0kB writeback_tmp:0kB unstable:0kB all_unreclaimable? no
Feb 23 08:11:19 Velnecious kernel: [74772.894870] Node 0 DMA free:15884kB min:32kB low:44kB high:56kB active_anon:0kB inactive_anon:0kB active_file:0kB inactive_file:0kB unevictable:0kB writepending:0kB present:15988kB managed:15892kB mlocked:0kB kernel_stack:0kB pagetables:0kB bounce:0kB free_pcp:0kB local_pcp:0kB free_cma:0kB
Feb 23 08:11:19 Velnecious kernel: [74772.894872] lowmem_reserve[]: 0 1858 31891 31891 31891
Feb 23 08:11:19 Velnecious kernel: [74772.894873] Node 0 DMA32 free:123796kB min:3936kB low:5836kB high:7736kB active_anon:600kB inactive_anon:0kB active_file:1752kB inactive_file:117176kB unevictable:0kB writepending:8kB present:2038708kB managed:1972852kB mlocked:0kB kernel_stack:16kB pagetables:0kB bounce:0kB free_pcp:0kB local_pcp:0kB free_cma:0kB
Feb 23 08:11:19 Velnecious kernel: [74772.894875] lowmem_reserve[]: 0 0 30032 30032 30032
Feb 23 08:11:19 Velnecious kernel: [74772.894875] Node 0 Normal free:471820kB min:63612kB low:94364kB high:125116kB active_anon:252012kB inactive_anon:275336kB active_file:806588kB inactive_file:18013476kB unevictable:73912kB writepending:1072kB present:31305728kB managed:30759508kB mlocked:73912kB kernel_stack:9248kB pagetables:28644kB bounce:0kB free_pcp:0kB local_pcp:0kB free_cma:0kB
Feb 23 08:11:19 Velnecious kernel: [74772.894877] lowmem_reserve[]: 0 0 0 0 0
Feb 23 08:11:19 Velnecious kernel: [74772.894878] Node 0 DMA: 1*4kB (U) 3*8kB (U) 3*16kB (U) 0*32kB 3*64kB (U) 2*128kB (U) 0*256kB 0*512kB 1*1024kB (U) 1*2048kB (M) 3*4096kB (M) = 15884kB
Feb 23 08:11:19 Velnecious kernel: [74772.894881] Node 0 DMA32: 341*4kB (UM) 660*8kB (UM) 822*16kB (UM) 700*32kB (UM) 591*64kB (UM) 2*128kB (UE) 134*256kB (UM) 18*512kB (U) 0*1024kB 0*2048kB 0*4096kB = 123796kB
Feb 23 08:11:19 Velnecious kernel: [74772.894883] Node 0 Normal: 3518*4kB (UM) 14508*8kB (UME) 21111*16kB (UME) 109*32kB (UMH) 1*64kB (H) 1*128kB (H) 0*256kB 0*512kB 1*1024kB (H) 0*2048kB 0*4096kB = 472616kB
Feb 23 08:11:19 Velnecious kernel: [74772.894886] Node 0 hugepages_total=0 hugepages_free=0 hugepages_surp=0 hugepages_size=1048576kB
Feb 23 08:11:19 Velnecious kernel: [74772.894887] Node 0 hugepages_total=0 hugepages_free=0 hugepages_surp=0 hugepages_size=2048kB
Feb 23 08:11:19 Velnecious kernel: [74772.894887] 4762561 total pagecache pages
Feb 23 08:11:19 Velnecious kernel: [74772.894890] 1 pages in swap cache
Feb 23 08:11:19 Velnecious kernel: [74772.894890] Swap cache stats: add 25, delete 24, find 0/0
Feb 23 08:11:19 Velnecious kernel: [74772.894891] Free swap  = 31998204kB
Feb 23 08:11:19 Velnecious kernel: [74772.894891] Total swap = 31999996kB
Feb 23 08:11:19 Velnecious kernel: [74772.894891] 8340106 pages RAM
Feb 23 08:11:19 Velnecious kernel: [74772.894891] 0 pages HighMem/MovableOnly
Feb 23 08:11:19 Velnecious kernel: [74772.894892] 153043 pages reserved
Feb 23 08:11:19 Velnecious kernel: [74772.894892] 0 pages cma reserved
Feb 23 08:11:19 Velnecious kernel: [74772.894892] 0 pages hwpoisoned
Feb 23 08:11:19 Velnecious kernel: [74772.894895] BUG: unable to handle kernel paging request at 0000000000006f80
Feb 23 08:11:19 Velnecious kernel: [74772.894906] IP: _nv002475kms+0x60/0x100 [nvidia_modeset]
Feb 23 08:11:19 Velnecious kernel: [74772.894907] PGD 0 P4D 0 
Feb 23 08:11:19 Velnecious kernel: [74772.894908] Oops: 0000 [#1] SMP PTI
Feb 23 08:11:19 Velnecious kernel: [74772.894909] Modules linked in: uas usb_storage rfcomm cmac bnep binfmt_misc zfs(POE) zunicode(POE) zavl(POE) icp(POE) zlua(POE) zcommon(POE) znvpair(POE) spl(OE) nls_iso8859_1 snd_hda_codec_hdmi eeepc_wmi asus_wmi wmi_bmof sparse_keymap intel_wmi_thunderbolt mxm_wmi intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm irqbypass crct10dif_pclmul crc32_pclmul ghash_clmulni_intel pcbc aesni_intel aes_x86_64 crypto_simd glue_helper cryptd intel_cstate snd_hda_codec_realtek intel_rapl_perf snd_hda_codec_generic snd_hda_intel snd_usb_audio snd_hda_codec snd_hda_core snd_usbmidi_lib snd_hwdep snd_pcm snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq btusb btrtl snd_seq_device btbcm btintel snd_timer bluetooth snd mei_me input_leds joydev soundcore ecdh_generic mei shpchp wmi acpi_pad
Feb 23 08:11:19 Velnecious kernel: [74772.894923]  mac_hid nvidia_uvm(OE) sch_fq_codel parport_pc ppdev lp parport ip_tables x_tables autofs4 btrfs xor zstd_compress raid6_pq hid_generic usbhid hid nvidia_drm(POE) nvidia_modeset(POE) nvidia(POE) drm_kms_helper igb syscopyarea e1000e sysfillrect sysimgblt dca i2c_algo_bit fb_sys_fops nvme drm ptp nvme_core pps_core ipmi_devintf ipmi_msghandler video
Feb 23 08:11:19 Velnecious kernel: [74772.894930] CPU: 2 PID: 1207 Comm: Xorg Tainted: P           OE    4.15.0-88-generic #88-Ubuntu
Feb 23 08:11:19 Velnecious kernel: [74772.894931] Hardware name: System manufacturer System Product Name/TUF Z270 MARK 1, BIOS 1301 03/14/2018
Feb 23 08:11:19 Velnecious kernel: [74772.894939] RIP: 0010:_nv002475kms+0x60/0x100 [nvidia_modeset]
Feb 23 08:11:19 Velnecious kernel: [74772.894940] RSP: 0018:ffffaf934411fb80 EFLAGS: 00010202
Feb 23 08:11:19 Velnecious kernel: [74772.894941] RAX: 0000000000000004 RBX: 0000000000006f80 RCX: 0000000000000004
Feb 23 08:11:19 Velnecious kernel: [74772.894941] RDX: 0000000000000060 RSI: 0000000000006f80 RDI: ffff9d7306eea008
Feb 23 08:11:19 Velnecious kernel: [74772.894942] RBP: 0000000000000000 R08: 0000000000000000 R09: 0000000000000000
Feb 23 08:11:19 Velnecious kernel: [74772.894943] R10: 0000000000000004 R11: 0000000000000001 R12: 0000000000006f80
Feb 23 08:11:19 Velnecious kernel: [74772.894943] R13: 0000000000006f80 R14: ffff9d7306eea008 R15: 0000000000000001
Feb 23 08:11:19 Velnecious kernel: [74772.894944] FS:  00007fc0d62b7600(0000) GS:ffff9d7336880000(0000) knlGS:0000000000000000
Feb 23 08:11:19 Velnecious kernel: [74772.894945] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Feb 23 08:11:19 Velnecious kernel: [74772.894945] CR2: 0000000000006f80 CR3: 0000000848c0a006 CR4: 00000000003606e0
Feb 23 08:11:19 Velnecious kernel: [74772.894946] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Feb 23 08:11:19 Velnecious kernel: [74772.894946] DR3: 0000000000000000 DR6: 00000000fffe0ff0 DR7: 0000000000000400
Feb 23 08:11:19 Velnecious kernel: [74772.894947] Call Trace:
Feb 23 08:11:19 Velnecious kernel: [74772.894954]  ? _nv002627kms+0x3aa/0x1f70 [nvidia_modeset]
Feb 23 08:11:19 Velnecious kernel: [74772.894956]  ? __alloc_pages_nodemask+0x11c/0x2c0
Feb 23 08:11:19 Velnecious kernel: [74772.894957]  ? alloc_pages_current+0x6a/0xe0
Feb 23 08:11:19 Velnecious kernel: [74772.894958]  ? kmalloc_order+0x18/0x40
Feb 23 08:11:19 Velnecious kernel: [74772.894960]  ? kmalloc_order_trace+0x24/0xb0
Feb 23 08:11:19 Velnecious kernel: [74772.894965]  ? _nv000491kms+0x50/0x50 [nvidia_modeset]
Feb 23 08:11:19 Velnecious kernel: [74772.894971]  ? _nv000620kms+0x31/0xe0 [nvidia_modeset]
Feb 23 08:11:19 Velnecious kernel: [74772.894976]  ? _nv000491kms+0x50/0x50 [nvidia_modeset]
Feb 23 08:11:19 Velnecious kernel: [74772.894982]  ? nvKmsIoctl+0x96/0x1d0 [nvidia_modeset]
Feb 23 08:11:19 Velnecious kernel: [74772.894987]  ? nvkms_ioctl_common+0x42/0x80 [nvidia_modeset]
Feb 23 08:11:19 Velnecious kernel: [74772.894993]  ? nvkms_ioctl+0xc7/0x100 [nvidia_modeset]
Feb 23 08:11:19 Velnecious kernel: [74772.895057]  ? nvidia_frontend_unlocked_ioctl+0x42/0x50 [nvidia]
Feb 23 08:11:19 Velnecious kernel: [74772.895058]  ? do_vfs_ioctl+0xa8/0x630
Feb 23 08:11:19 Velnecious kernel: [74772.895059]  ? __sys_recvmsg+0x80/0x90
Feb 23 08:11:19 Velnecious kernel: [74772.895060]  ? SyS_ioctl+0x79/0x90
Feb 23 08:11:19 Velnecious kernel: [74772.895061]  ? do_syscall_64+0x73/0x130
Feb 23 08:11:19 Velnecious kernel: [74772.895062]  ? entry_SYSCALL_64_after_hwframe+0x3d/0xa2
Feb 23 08:11:19 Velnecious kernel: [74772.895063] Code: 2a eb 40 0f 1f 84 00 00 00 00 00 48 c7 03 00 00 00 00 c6 43 08 00 41 8b 86 d8 00 00 00 83 c5 01 48 81 c3 d0 03 00 00 39 e8 76 18 <48> 8b 3b 48 85 ff 74 ea 80 7b 08 00 75 d2 e8 ed d2 ff ff eb cb 
Feb 23 08:11:19 Velnecious kernel: [74772.895078] RIP: _nv002475kms+0x60/0x100 [nvidia_modeset] RSP: ffffaf934411fb80
Feb 23 08:11:19 Velnecious kernel: [74772.895079] CR2: 0000000000006f80
Feb 23 08:11:19 Velnecious kernel: [74772.895080] ---[ end trace 9a7d8b55c14bc4ed ]---

```

A shorter snippet from my main computer as it seems to be showing the same thing:
```

Feb 17 16:48:45 tick kernel: [389781.803100] Xorg: page allocation failure: order:4, mode:0x14040c0(GFP_KERNEL|__GFP_COMP), nodemask=(null)
Feb 17 16:48:45 tick kernel: [389781.803101] Xorg cpuset=/ mems_allowed=0
Feb 17 16:48:45 tick kernel: [389781.803104] CPU: 7 PID: 6278 Comm: Xorg Tainted: P           OE    4.15.0-76-generic #86-Ubuntu
Feb 17 16:48:45 tick kernel: [389781.803105] Hardware name: ASUS All Series/X99-E WS/USB 3.1, BIOS 3502 03/09/2017
Feb 17 16:48:45 tick kernel: [389781.803105] Call Trace:
Feb 17 16:48:45 tick kernel: [389781.803110]  dump_stack+0x6d/0x8e
Feb 17 16:48:45 tick kernel: [389781.803113]  warn_alloc+0xff/0x1a0
Feb 17 16:48:45 tick kernel: [389781.803115]  ? __alloc_pages_direct_compact+0x51/0x100
Feb 17 16:48:45 tick kernel: [389781.803116]  __alloc_pages_slowpath+0xdc5/0xe00
Feb 17 16:48:45 tick kernel: [389781.803119]  ? ktime_get+0x43/0xb0
Feb 17 16:48:45 tick kernel: [389781.803120]  __alloc_pages_nodemask+0x29a/0x2c0
Feb 17 16:48:45 tick kernel: [389781.803123]  alloc_pages_current+0x6a/0xe0
Feb 17 16:48:45 tick kernel: [389781.803126]  kmalloc_order+0x18/0x40
Feb 17 16:48:45 tick kernel: [389781.803127]  kmalloc_order_trace+0x24/0xb0
Feb 17 16:48:45 tick kernel: [389781.803141]  ? _nv000491kms+0x50/0x50 [nvidia_modeset]
Feb 17 16:48:45 tick kernel: [389781.803143]  __kmalloc+0x209/0x220
Feb 17 16:48:45 tick kernel: [389781.803148]  ? _nv000491kms+0x50/0x50 [nvidia_modeset]
Feb 17 16:48:45 tick kernel: [389781.803152]  nvkms_alloc+0x25/0x60 [nvidia_modeset]
Feb 17 16:48:45 tick kernel: [389781.803160]  _nv002520kms+0x16/0x30 [nvidia_modeset]
Feb 17 16:48:45 tick kernel: [389781.803161] WARNING: kernel stack frame pointer at 000000008f3f9403 in Xorg:6278 has bad value 00000000499388dd
Feb 17 16:48:45 tick kernel: [389781.803162] unwind stack type:0 next_sp:          (null) mask:0x2 graph_idx:0

```

One thing I noticed while doing the transfer is I saw RAM utilization increase a fair amount at first, but then it leveled off at a bit of a high level.  I checked memory usage of all running programs and it all looked to be very low, so I figured all of this memory must be going into kernel space or something.  As I don't have time to sit around and watch data move around, in both cases I was away from the computer when the Xorg server crashed and so don't know if there was another RAM utilization spike again or not.  However seeing the vastly different RAMs on these system, 128 GB on the first, 32 GB on the second, though the first had a whole bunch of other stuff running on it (which is why it has so much RAM as it kept thrashing with only 64 GBs) makes me somewhat skeptical of another quick jump in RAM utilization, but instead either just spiraled out of control or had a bad pointer in kernel space, especially as it looks like the Xorg crash is complaining about invalid data it seems.  I also spent some time reading the data off of the ZFS array and no problems happened except for a faulty disk dropping out of the array.  I was also able to do an array reconstruction without issue.  It is just when it comes to writing a bunch of data in the first place is when this crash occurs it seems.  Whether a drive was goofing up some even if it didn't register in the logs the first time around (or I overlooked it), well I was doing this for failure mode testing before trying anything real with OpenZFS.  Just didn't expect to see my Xorg server crash repeatedly under a particular test at about the same point in the test across two different computers.

---

### Post by kevdog on 2020-02-23
I kind of skimmed your post. Alot of stuff in there.  Just curious why do you think its ZFS that's causing an Xorg crash?  Do you have to use a dkms kernel?  Can't you use a kernel specific to zfs?

---

### Post by BatteryKing on 2020-02-24
There are a few reasons.
1. My main computer had been more or less perfectly stable since the last major hardware update.  This is as in pulseaudio needs a periodic restart, especially when switching between users at the console and I keep losing g-sync support, but no Xorg crashes.  It is also a Xeon system with ECC RAM built to my specifications after doing this stuff professionally for a while, so I am pretty confident in the reliability of the underlying system.  (It is a custom built system and I worked directly with the motherboard manufacturer to resolve the stability issues I had with it early on and validated the issues have been fixed.)
2. The problem was replicated on my dual boot Windows box in pretty much the exact same spot it failed on my main Linux box.  This system has been perfectly stable since since swapping out a faulty power supply a few months back.
3. I did numerous other operations on both systems including a bunch of other ZFS operations such as resilvering and everything was fine.  It was just in about the same spot of the same copy to ZFS test did Xorg crash on the two different systems.  This seems very unlikely to be coincidence.
4. While not getting into too much detail (especially as I can tap a number of different examples), I have demonstrated that you can have things go wrong in kernel space and other applications seemingly unrelated can and will crash.  I have been able to reliably reproduce these sorts of issues and solve the problem in the past.  This is just the same do tests to show the system is reliable, then repeatedly do the thing that causes the failure to pop up elsewhere.

Have to use DKMS kernel due to licensing issues of CDDL vs GPLv2.

---

### Post by kevdog on 2020-02-24
Ok I get what you're saying with DKMS.  I'm using zfs on Arch Linux and they have a repository that you can download and use lts kernels with zfs backed in -- it's an unofficial repository and user created so hence it gets around licensing issues: [https://github.com/archzfs/archzfs/wiki](https://github.com/archzfs/archzfs/wiki).  Honestly I'm surprised debian/ubuntu doesn't have something like this setup (or third party since user base is so huge).  I've head zfs not really working real well with 5.5 kernels. Not sure the reason.  I'm currently using 5.4.21-1-lts.

---

