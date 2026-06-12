---
title: "Crash of Ubuntu Server 12.10 - unable to handle kernel paging request"
date: 2013-04-04
forum: General Help
---

### Post by stando007 on 2013-04-04
Hi,
I have Ubuntu Server edition 12.10 installed on Intel D525MW Mount Washington main board, 2x 2GB of SODIMM DDR3 (Zeppelin brand), 1x SATA 1.5TB HDD. I use the server as home NAS, router (wifi+lan), apache server, etc. I have these network adapters there:
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
02:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8169 PCI Gigabit Ethernet Controller (rev 10)

Couple of times the server crashed - no response, with need of hard reset.

Yesterday I made upgrade of the packages, because there were some critical updates listed. I do not know if this could cause the crash, but later after upgrade and restart of the server, I noticed there is a loadavg of ~60.
I checked with top, free and did not notice anything suspicious there.
I checked dmesg and found this:
```
Apr  3 21:29:02 sagittarius kernel: [30045.027992] BUG: unable to handle kernel paging request at ffff8801a9194300
Apr  3 21:29:02 sagittarius kernel: [30045.028161] IP: [<ffffffff81154f50>] anon_vma_fork+0xf0/0x140
Apr  3 21:29:02 sagittarius kernel: [30045.028268] PGD 1c0c063 PUD 0 
Apr  3 21:29:02 sagittarius kernel: [30045.028330] Oops: 0002 [#1] SMP 
Apr  3 21:29:02 sagittarius kernel: [30045.028393] CPU 0 
Apr  3 21:29:02 sagittarius kernel: [30045.028428] Modules linked in: 8021q garp bridge stp llc iptable_mangle iptable_nat nf_nat xt_tcpudp nf_conntrack_ipv4 nf_defrag_ipv4 xt_state nf_conntrack xt_multiport iptable_filter ip_tables x_tables arc4 ath9k i915 mac80211 ath9k_common ath9k_hw ath drm_kms_helper drm cfg80211 psmouse nfsd coretemp mac_hid microcode ppdev lpc_ich serio_raw i2c_algo_bit parport_pc nfs video lockd fscache auth_rpcgss nfs_acl lp parport sunrpc r8169
Apr  3 21:29:02 sagittarius kernel: [30045.029269] 
Apr  3 21:29:02 sagittarius kernel: [30045.029278] Pid: 2190, comm: console-kit-dae Not tainted 3.5.0-17-generic #28-Ubuntu                  /D525MW
Apr  3 21:29:02 sagittarius kernel: [30045.029446] RIP: 0010:[<ffffffff81154f50>]  [<ffffffff81154f50>] anon_vma_fork+0xf0/0x140
Apr  3 21:29:02 sagittarius kernel: [30045.029581] RSP: 0018:ffff880125b83d60  EFLAGS: 00010246
Apr  3 21:29:02 sagittarius kernel: [30045.029666] RAX: ffff8801a9194300 RBX: ffff8801291942d0 RCX: ffff880129194300
Apr  3 21:29:02 sagittarius kernel: [30045.029778] RDX: ffff880117dfb650 RSI: 00000000000000d0 RDI: ffff8801258ab560
Apr  3 21:29:02 sagittarius kernel: [30045.029890] RBP: ffff880125b83d80 R08: 0000000000016ea0 R09: 00007f2152b86000
Apr  3 21:29:02 sagittarius kernel: [30045.030001] R10: 00007f2152b86000 R11: ffff880126e1b4a8 R12: ffff880117dfb630
Apr  3 21:29:02 sagittarius kernel: [30045.030021] R13: ffff8801261438f0 R14: ffff8801259200b0 R15: ffff8801261438f0
Apr  3 21:29:02 sagittarius kernel: [30045.030021] FS:  00007f21554c07c0(0000) GS:ffff88012fc00000(0000) knlGS:0000000000000000
Apr  3 21:29:02 sagittarius kernel: [30045.030021] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Apr  3 21:29:02 sagittarius kernel: [30045.030021] CR2: ffff8801a9194300 CR3: 0000000125b73000 CR4: 00000000000007f0
Apr  3 21:29:02 sagittarius kernel: [30045.030021] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Apr  3 21:29:02 sagittarius kernel: [30045.030021] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Apr  3 21:29:02 sagittarius kernel: [30045.030021] Process console-kit-dae (pid: 2190, threadinfo ffff880125b82000, task ffff88012594ae00)
Apr  3 21:29:02 sagittarius kernel: [30045.030021] Stack:
Apr  3 21:29:02 sagittarius kernel: [30045.030021]  ffff880126c79180 ffff8801259200b0 ffff8801261439a0 0000000000000001
Apr  3 21:29:02 sagittarius kernel: [30045.030021]  ffff880125b83e00 ffffffff8104f47e 0000000000000000 ffff880126c791e0
Apr  3 21:29:02 sagittarius kernel: [30045.030021]  ffff88012695d560 ffff88012695d500 ffff8801261439e0 ffff8801261439d8
Apr  3 21:29:02 sagittarius kernel: [30045.030021] Call Trace:
Apr  3 21:29:02 sagittarius kernel: [30045.030021]  [<ffffffff8104f47e>] dup_mm+0x24e/0x610
Apr  3 21:29:02 sagittarius kernel: [30045.030021]  [<ffffffff81050590>] copy_process.part.22+0xd10/0x1520
Apr  3 21:29:02 sagittarius kernel: [30045.030021]  [<ffffffff812ec60c>] ? apparmor_file_alloc_security+0x2c/0x60
Apr  3 21:29:02 sagittarius kernel: [30045.030021]  [<ffffffff812b3456>] ? security_file_alloc+0x16/0x20
Apr  3 21:29:02 sagittarius kernel: [30045.030021]  [<ffffffff81050f25>] do_fork+0x135/0x390
Apr  3 21:29:02 sagittarius kernel: [30045.030021]  [<ffffffff81681aae>] ? _raw_spin_lock+0xe/0x20
Apr  3 21:29:02 sagittarius kernel: [30045.030021]  [<ffffffff8118bd89>] ? do_pipe_flags+0xb9/0x130
Apr  3 21:29:02 sagittarius kernel: [30045.030021]  [<ffffffff8101c2e8>] sys_clone+0x28/0x30
Apr  3 21:29:02 sagittarius kernel: [30045.030021]  [<ffffffff8168a033>] stub_clone+0x13/0x20
Apr  3 21:29:02 sagittarius kernel: [30045.030021]  [<ffffffff81689d29>] ? system_call_fastpath+0x16/0x1b
Apr  3 21:29:02 sagittarius kernel: [30045.030021] Code: 42 08 49 89 54 24 10 49 8d 55 70 49 89 54 24 18 49 89 45 70 49 8d 54 24 20 48 8b 43 38 48 89 53 38 49 89 4c 24 20 49 89 44 24 28 <48> 89 10 48 8b 3b 48 83 c7 08 e8 51 a4 52 00 31 d2 89 d0 48 8b 
Apr  3 21:29:02 sagittarius kernel: [30045.030021] RIP  [<ffffffff81154f50>] anon_vma_fork+0xf0/0x140
Apr  3 21:29:02 sagittarius kernel: [30045.030021]  RSP <ffff880125b83d60>
Apr  3 21:29:02 sagittarius kernel: [30045.030021] CR2: ffff8801a9194300
Apr  3 21:29:02 sagittarius kernel: [30045.030021] ---[ end trace 42a06201f35825b4 ]---

```

SSH still worked. I decided to reboot the server. Reboot took at least 5 minutes (shut down was very slow). Then after rebooting, http server was working, internet connection from local LAN pcs via this router worked, but SSH was not working. I was not at home, so I asked for power cycle the server. Then after the startup, all is working again, also ssh.

Any ideas what could cause this? HW issue? SW issue? Basicaly I use there these services/daemons: apache, mysql, hostapd, minidlna, transmission-daemon, open ssh daemon, smbd. All the most recent version from default 12.10 repositories.
I would like to prevent such crashes because this machine is my home server/router and I would like to keep it running safe. Before, when I used ubuntu 11.x no such problems occured.

---

