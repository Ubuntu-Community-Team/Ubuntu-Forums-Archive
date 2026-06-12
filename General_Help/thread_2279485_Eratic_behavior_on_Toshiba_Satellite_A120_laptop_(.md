---
title: "Eratic behavior on Toshiba Satellite A120 laptop (NetworkManager call trace)"
date: 2015-05-23
forum: General Help
---

### Post by cronos6 on 2015-05-23
Hi,

 Since a couple of month, my wireless connection became unstable and sleep mode doesn't work anymore.
 What I changed a few month ago ? I've installed xubuntu 14.10 32b

 I decided to install xubuntu 15.04 32b to correct those issues : same problem.
 I tried Debian 8 : similar issues too. I even tried the latest OpenSuSE 13.x : others issues, especially with video card.
 Now, I'm running on Xubuntu 13.04 32b, I do remember it worked fine a couple of years ago : both wireless network and sleep mode. Well, I trough, I have the same problems.

 Here is more specific information :
 - computer boots normally.
 - Realtek RTL8192CU 802.11n WLAN Adapter can see my wireless SSID network and connect to it : got an IP from the DHCP server

```
May 23 15:29:36 carotoshi NetworkManager[897]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
May 23 15:29:36 carotoshi dhclient: Listening on LPF/wlan0/c4:6e:1f:13:b0:ec
May 23 15:29:36 carotoshi dhclient: Sending on   LPF/wlan0/c4:6e:1f:13:b0:ec
May 23 15:29:36 carotoshi dhclient: Sending on   Socket/fallback
May 23 15:29:36 carotoshi dhclient: DHCPREQUEST of 192.168.0.9 on wlan0 to 255.255.255.255 port 67 (xid=0x3f171780)
May 23 15:29:36 carotoshi dhclient: DHCPNAK from 192.168.0.254 (xid=0x3f171780)
May 23 15:29:36 carotoshi NetworkManager[897]: <info> (wlan0): DHCPv4 state changed preinit -> expire
May 23 15:29:36 carotoshi dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3 (xid=0x62db73cc)
May 23 15:29:36 carotoshi NetworkManager[897]: <info> (wlan0): DHCPv4 state changed expire -> preinit
May 23 15:29:36 carotoshi dhclient: DHCPREQUEST of 192.168.0.3 on wlan0 to 255.255.255.255 port 67 (xid=0x62db73cc)
May 23 15:29:36 carotoshi dhclient: DHCPOFFER of 192.168.0.3 from 192.168.0.254
May 23 15:29:36 carotoshi dhclient: DHCPACK of 192.168.0.3 from 192.168.0.254
May 23 15:29:36 carotoshi NetworkManager[897]: <info> (wlan0): DHCPv4 state changed preinit -> bound
May 23 15:29:36 carotoshi NetworkManager[897]: <info>   address 192.168.0.3
May 23 15:29:36 carotoshi NetworkManager[897]: <info>   prefix 24 (255.255.255.0)
May 23 15:29:36 carotoshi NetworkManager[897]: <info>   gateway 192.168.0.254
May 23 15:29:36 carotoshi NetworkManager[897]: <info>   hostname 'carotoshi'
May 23 15:29:36 carotoshi NetworkManager[897]: <info>   nameserver '192.168.0.254'
May 23 15:29:36 carotoshi NetworkManager[897]: <info>   domain name 'mynetwork.fr'
May 23 15:29:36 carotoshi NetworkManager[897]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
May 23 15:29:36 carotoshi NetworkManager[897]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
May 23 15:29:36 carotoshi avahi-daemon[796]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.3.
May 23 15:29:36 carotoshi avahi-daemon[796]: New relevant interface wlan0.IPv4 for mDNS.
May 23 15:29:36 carotoshi avahi-daemon[796]: Registering new address record for 192.168.0.3 on wlan0.IPv4.
May 23 15:29:36 carotoshi dhclient: bound to 192.168.0.3 -- renewal in 33474 seconds.
```

 After a few minutes :
 - I loose the internet connection :

```
May 23 22:42:23 carotoshi kernel: [  361.336065] INFO: task kworker/1:1:47 blocked for more than 120 seconds.
May 23 22:42:23 carotoshi kernel: [  361.336080] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
May 23 22:42:23 carotoshi kernel: [  361.336087] kworker/1:1     D 00000000     0    47      2 0x00000000
May 23 22:42:23 carotoshi kernel: [  361.336100]  f3b4dc50 00000046 c148cf0a 00000000 f3bc9050 f38c19a0 cf6b578c 0000002a
May 23 22:42:23 carotoshi kernel: [  361.336119]  c19d80c0 c19d80c0 f383e864 35e00c70 f64e50c0 f395e680 c1016650 35e00c70
May 23 22:42:23 carotoshi kernel: [  361.336135]  00000000 00000004 87dab000 f219d180 f3b7e800 c189c4c0 f3b4dc64 f3b7e800
May 23 22:42:23 carotoshi kernel: [  361.336150] Call Trace:
May 23 22:42:23 carotoshi kernel: [  361.336179]  [<c148cf0a>] ? ehci_urb_enqueue+0xea/0xda0
May 23 22:42:23 carotoshi kernel: [  361.336193]  [<c1016650>] ? nommu_map_page+0x50/0x90
May 23 22:42:23 carotoshi kernel: [  361.336207]  [<c1614453>] schedule+0x23/0x60
May 23 22:42:23 carotoshi kernel: [  361.336220]  [<c1612c05>] schedule_timeout+0x1c5/0x240
May 23 22:42:23 carotoshi kernel: [  361.336232]  [<c1478af2>] ? usb_hcd_submit_urb+0x82/0x6e0
May 23 22:42:23 carotoshi kernel: [  361.336244]  [<c105b0c1>] ? update_process_times+0x61/0x70
May 23 22:42:23 carotoshi kernel: [  361.336257]  [<c12ef360>] ? timerqueue_add+0x50/0xb0
May 23 22:42:23 carotoshi kernel: [  361.336267]  [<c109a203>] ? ktime_get+0x63/0x100
May 23 22:42:23 carotoshi kernel: [  361.336276]  [<c16142d1>] wait_for_common+0xa1/0x120
May 23 22:42:23 carotoshi kernel: [  361.336288]  [<c107c7c0>] ? try_to_wake_up+0x240/0x240
May 23 22:42:23 carotoshi kernel: [  361.336297]  [<c1614402>] wait_for_completion_timeout+0x12/0x20
May 23 22:42:23 carotoshi kernel: [  361.336308]  [<c147acd6>] usb_start_wait_urb+0x66/0xd0
May 23 22:42:23 carotoshi kernel: [  361.336317]  [<c147af43>] usb_control_msg+0xb3/0xf0
May 23 22:42:23 carotoshi kernel: [  361.336326]  [<c161531d>] ? _raw_spin_lock_irqsave+0x2d/0x40
May 23 22:42:23 carotoshi kernel: [  361.336354]  [<f90c70c0>] _usb_read_sync+0xc0/0x130 [rtlwifi]
May 23 22:42:23 carotoshi kernel: [  361.336371]  [<f90c7142>] _usb_read32_sync+0x12/0x20 [rtlwifi]
May 23 22:42:23 carotoshi kernel: [  361.336389]  [<f90973b6>] rtl92c_phy_query_bb_reg+0x16/0x50 [rtl8192c_common]
May 23 22:42:23 carotoshi kernel: [  361.336404]  [<f90983a6>] _rtl92c_phy_rf_serial_read+0x176/0x1d0 [rtl8192c_common]
May 23 22:42:23 carotoshi kernel: [  361.336419]  [<f91118f5>] rtl92cu_phy_query_rf_reg+0x25/0x50 [rtl8192cu]
May 23 22:42:23 carotoshi kernel: [  361.336432]  [<f9094d01>] rtl92c_dm_txpower_tracking_callback_thermalmeter+0x51/0xaa0 [rtl8192c_common]
May 23 22:42:23 carotoshi kernel: [  361.336449]  [<f90c7292>] ? _usbctrl_vendorreq_async_write.constprop.24+0x102/0x190 [rtlwifi]
May 23 22:42:23 carotoshi kernel: [  361.336463]  [<f9095776>] rtl92c_dm_check_txpower_tracking_thermal_meter+0x26/0x70 [rtl8192c_common]
May 23 22:42:23 carotoshi kernel: [  361.336476]  [<f9095aec>] rtl92c_dm_watchdog.part.12+0x24c/0xaf0 [rtl8192c_common]
May 23 22:42:23 carotoshi kernel: [  361.336488]  [<f910e90c>] ? rtl92cu_get_hw_reg+0x12c/0x170 [rtl8192cu]
May 23 22:42:23 carotoshi kernel: [  361.336501]  [<f9096417>] rtl92c_dm_watchdog+0x87/0x90 [rtl8192c_common]
May 23 22:42:23 carotoshi kernel: [  361.336514]  [<f90bd1d8>] rtl_watchdog_wq_callback+0xe8/0x2e0 [rtlwifi]
May 23 22:42:23 carotoshi kernel: [  361.336522]  [<c105ad00>] ? mod_timer+0x140/0x1a0
May 23 22:42:23 carotoshi kernel: [  361.336532]  [<c1065be5>] ? __queue_delayed_work+0xa5/0x1c0
May 23 22:42:23 carotoshi kernel: [  361.336542]  [<c1066005>] process_one_work+0x135/0x3e0
May 23 22:42:23 carotoshi kernel: [  361.336552]  [<c161ca33>] ? common_interrupt+0x33/0x38
May 23 22:42:23 carotoshi kernel: [  361.336560]  [<c1066cf9>] worker_thread+0x119/0x3b0
May 23 22:42:23 carotoshi kernel: [  361.336569]  [<c1066be0>] ? manage_workers+0x240/0x240
May 23 22:42:23 carotoshi kernel: [  361.336580]  [<c106b724>] kthread+0x94/0xa0
May 23 22:42:23 carotoshi kernel: [  361.336591]  [<c1070000>] ? __hrtimer_start_range_ns+0x1a0/0x470
May 23 22:42:23 carotoshi kernel: [  361.336600]  [<c161c477>] ret_from_kernel_thread+0x1b/0x28
May 23 22:42:23 carotoshi kernel: [  361.336609]  [<c106b690>] ? kthread_create_on_node+0xc0/0xc0
May 23 22:42:23 carotoshi kernel: [  361.336623] INFO: task kworker/1:2:243 blocked for more than 120 seconds.
May 23 22:42:23 carotoshi kernel: [  361.336627] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
May 23 22:42:23 carotoshi kernel: [  361.336632] kworker/1:2     D 00000000     0   243      2 0x00000000
May 23 22:42:23 carotoshi kernel: [  361.336640]  f59add5c 00000046 c148cf0a 00000000 f3bc9050 f38c19a0 f5d22000 0000002b
May 23 22:42:23 carotoshi kernel: [  361.336656]  c19d80c0 c19d80c0 ba3c2833 0000002b f64e50c0 f5f82670 c1016650 35e00c74
May 23 22:42:23 carotoshi kernel: [  361.336671]  00000000 00000001 00000000 f21a5c00 f3b7e800 c189c4c0 f59add70 f3b7e800
May 23 22:42:23 carotoshi kernel: [  361.336686] Call Trace:
May 23 22:42:23 carotoshi kernel: [  361.336696]  [<c148cf0a>] ? ehci_urb_enqueue+0xea/0xda0
May 23 22:42:23 carotoshi kernel: [  361.336706]  [<c1016650>] ? nommu_map_page+0x50/0x90
May 23 22:42:23 carotoshi kernel: [  361.336715]  [<c1614453>] schedule+0x23/0x60
May 23 22:42:23 carotoshi kernel: [  361.336726]  [<c1612c05>] schedule_timeout+0x1c5/0x240
May 23 22:42:23 carotoshi kernel: [  361.336735]  [<c1478af2>] ? usb_hcd_submit_urb+0x82/0x6e0
May 23 22:42:23 carotoshi kernel: [  361.336745]  [<c16142d1>] wait_for_common+0xa1/0x120
May 23 22:42:23 carotoshi kernel: [  361.336755]  [<c107c7c0>] ? try_to_wake_up+0x240/0x240
May 23 22:42:23 carotoshi kernel: [  361.336764]  [<c1614402>] wait_for_completion_timeout+0x12/0x20
May 23 22:42:23 carotoshi kernel: [  361.336773]  [<c147acd6>] usb_start_wait_urb+0x66/0xd0
May 23 22:42:23 carotoshi kernel: [  361.336783]  [<c147af43>] usb_control_msg+0xb3/0xf0
May 23 22:42:23 carotoshi kernel: [  361.336792]  [<c161531d>] ? _raw_spin_lock_irqsave+0x2d/0x40
May 23 22:42:23 carotoshi kernel: [  361.336808]  [<f90c70c0>] _usb_read_sync+0xc0/0x130 [rtlwifi]
May 23 22:42:23 carotoshi kernel: [  361.336824]  [<f90c7182>] _usb_read8_sync+0x12/0x20 [rtlwifi]
May 23 22:42:23 carotoshi kernel: [  361.336836]  [<f910fa12>] rtl92cu_gpio_radio_on_off_checking+0x82/0x2d0 [rtl8192cu]
May 23 22:42:23 carotoshi kernel: [  361.336850]  [<f90bf5b3>] rtl_op_rfkill_poll+0x53/0x90 [rtlwifi]
May 23 22:42:23 carotoshi kernel: [  361.336920]  [<f94b81fc>] ieee80211_rfkill_poll+0x2c/0x40 [mac80211]
May 23 22:42:23 carotoshi kernel: [  361.336983]  [<f9354912>] cfg80211_rfkill_poll+0x22/0x80 [cfg80211]
May 23 22:42:23 carotoshi kernel: [  361.336994]  [<c15f663f>] rfkill_poll+0x1f/0x40
May 23 22:42:23 carotoshi kernel: [  361.337002]  [<c1066005>] process_one_work+0x135/0x3e0
May 23 22:42:23 carotoshi kernel: [  361.337012]  [<c16156dc>] ? reschedule_interrupt+0x34/0x3c
May 23 22:42:23 carotoshi kernel: [  361.337021]  [<c1066cf9>] worker_thread+0x119/0x3b0
May 23 22:42:23 carotoshi kernel: [  361.337030]  [<c1066be0>] ? manage_workers+0x240/0x240
May 23 22:42:23 carotoshi kernel: [  361.337039]  [<c106b724>] kthread+0x94/0xa0
May 23 22:42:23 carotoshi kernel: [  361.337049]  [<c1070000>] ? __hrtimer_start_range_ns+0x1a0/0x470
May 23 22:42:23 carotoshi kernel: [  361.337058]  [<c161c477>] ret_from_kernel_thread+0x1b/0x28
May 23 22:42:23 carotoshi kernel: [  361.337068]  [<c106b690>] ? kthread_create_on_node+0xc0/0xc0
May 23 22:42:23 carotoshi kernel: [  361.337084] INFO: task NetworkManager:870 blocked for more than 120 seconds.
May 23 22:42:23 carotoshi kernel: [  361.337088] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
May 23 22:42:23 carotoshi kernel: [  361.337092] NetworkManager  D 00000000     0   870      1 0x00000000
May 23 22:42:23 carotoshi kernel: [  361.337101]  f30f9c6c 00000082 001e8096 00000000 f2e26680 c18991e0 f2d9a094 00000036
May 23 22:42:23 carotoshi kernel: [  361.337116]  c19d80c0 c19d80c0 f30f9c78 00000286 f64d70c0 f2e26680 80100010 f2b854c4
May 23 22:42:23 carotoshi kernel: [  361.337131]  00000036 c15278dd 00000286 00000004 00000001 f5bc3100 000102d0 0000000e
May 23 22:42:23 carotoshi kernel: [  361.337146] Call Trace:
May 23 22:42:23 carotoshi kernel: [  361.337157]  [<c15278dd>] ? __alloc_skb+0x6d/0x250
May 23 22:42:23 carotoshi kernel: [  361.337167]  [<c1614453>] schedule+0x23/0x60
May 23 22:42:23 carotoshi kernel: [  361.337176]  [<c161469d>] schedule_preempt_disabled+0xd/0x10
May 23 22:42:23 carotoshi kernel: [  361.337188]  [<c16133b6>] __mutex_lock_slowpath+0xc6/0x120
May 23 22:42:23 carotoshi kernel: [  361.337198]  [<c1612f44>] mutex_lock+0x24/0x40
May 23 22:42:23 carotoshi kernel: [  361.337209]  [<c1556012>] genl_lock+0x12/0x20
May 23 22:42:23 carotoshi kernel: [  361.337219]  [<c1556030>] genl_rcv+0x10/0x30
May 23 22:42:23 carotoshi kernel: [  361.337229]  [<c1555617>] netlink_unicast+0x167/0x1e0
May 23 22:42:23 carotoshi kernel: [  361.337239]  [<c15558b9>] netlink_sendmsg+0x229/0x3a0
May 23 22:42:23 carotoshi kernel: [  361.337250]  [<c151e56c>] sock_sendmsg+0x9c/0xd0
May 23 22:42:23 carotoshi kernel: [  361.337263]  [<c1170ec0>] ? __pollwait+0xd0/0xd0
May 23 22:42:23 carotoshi kernel: [  361.337272]  [<c1170ec0>] ? __pollwait+0xd0/0xd0
May 23 22:42:23 carotoshi kernel: [  361.337283]  [<c151e82a>] ___sys_sendmsg.part.13+0x28a/0x2a0
May 23 22:42:23 carotoshi kernel: [  361.337294]  [<c1083beb>] ? task_tick_fair+0x15b/0x6f0
May 23 22:42:23 carotoshi kernel: [  361.337309]  [<c160becb>] ? nohz_balance_exit_idle.part.41+0x10/0x2b
May 23 22:42:23 carotoshi kernel: [  361.337318]  [<c10875f3>] ? trigger_load_balance+0xc3/0x1c0
May 23 22:42:23 carotoshi kernel: [  361.337329]  [<c107b69a>] ? scheduler_tick+0xda/0x100
May 23 22:42:23 carotoshi kernel: [  361.337337]  [<c105b0c1>] ? update_process_times+0x61/0x70
May 23 22:42:23 carotoshi kernel: [  361.337347]  [<c12ef360>] ? timerqueue_add+0x50/0xb0
May 23 22:42:23 carotoshi kernel: [  361.337356]  [<c109a203>] ? ktime_get+0x63/0x100
May 23 22:42:23 carotoshi kernel: [  361.337367]  [<c12f3c61>] ? _copy_from_user+0x41/0x60
May 23 22:42:23 carotoshi kernel: [  361.337377]  [<c151fa3a>] __sys_sendmsg+0x4a/0x80
May 23 22:42:23 carotoshi kernel: [  361.337387]  [<c1520158>] sys_socketcall+0x268/0x2b0
May 23 22:42:23 carotoshi kernel: [  361.337397]  [<c12f3b41>] ? copy_to_user+0x41/0x60
May 23 22:42:23 carotoshi kernel: [  361.337406]  [<c106b0f8>] ? sys_clock_gettime+0x48/0x70
May 23 22:42:23 carotoshi kernel: [  361.337415]  [<c161c50d>] sysenter_do_call+0x12/0x28
May 23 22:42:23 carotoshi kernel: [  361.337430] INFO: task wpa_supplicant:1051 blocked for more than 120 seconds.
May 23 22:42:23 carotoshi kernel: [  361.337434] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
May 23 22:42:23 carotoshi kernel: [  361.337439] wpa_supplicant  D 00000000     0  1051      1 0x00000000
May 23 22:42:23 carotoshi kernel: [  361.337447]  f33439dc 00200086 c148cf0a 00000000 f3bc9050 c18991e0 f3a84000 00000035
May 23 22:42:23 carotoshi kernel: [  361.337462]  c19d80c0 c19d80c0 8d4f207a 00000035 f64d70c0 f3364010 c1016650 35e00c78
May 23 22:42:23 carotoshi kernel: [  361.337477]  00000000 00000004 00000000 f2b60780 f3b7e800 c189c4c0 f33439f0 f3b7e800
May 23 22:42:23 carotoshi kernel: [  361.337492] Call Trace:
May 23 22:42:23 carotoshi kernel: [  361.337502]  [<c148cf0a>] ? ehci_urb_enqueue+0xea/0xda0
May 23 22:42:23 carotoshi kernel: [  361.337512]  [<c1016650>] ? nommu_map_page+0x50/0x90
May 23 22:42:23 carotoshi kernel: [  361.337521]  [<c1614453>] schedule+0x23/0x60
May 23 22:42:23 carotoshi kernel: [  361.337532]  [<c1612c05>] schedule_timeout+0x1c5/0x240
May 23 22:42:23 carotoshi kernel: [  361.337541]  [<c1478af2>] ? usb_hcd_submit_urb+0x82/0x6e0
May 23 22:42:23 carotoshi kernel: [  361.337556]  [<c1010a5f>] ? __switch_to+0xaf/0x320
May 23 22:42:23 carotoshi kernel: [  361.337565]  [<c16142d1>] wait_for_common+0xa1/0x120
May 23 22:42:23 carotoshi kernel: [  361.337575]  [<c107c7c0>] ? try_to_wake_up+0x240/0x240
May 23 22:42:23 carotoshi kernel: [  361.337584]  [<c1614402>] wait_for_completion_timeout+0x12/0x20
May 23 22:42:23 carotoshi kernel: [  361.337593]  [<c147acd6>] usb_start_wait_urb+0x66/0xd0
May 23 22:42:23 carotoshi kernel: [  361.337603]  [<c147af43>] usb_control_msg+0xb3/0xf0
May 23 22:42:23 carotoshi kernel: [  361.337612]  [<c161531d>] ? _raw_spin_lock_irqsave+0x2d/0x40
May 23 22:42:23 carotoshi kernel: [  361.337629]  [<f90c70c0>] _usb_read_sync+0xc0/0x130 [rtlwifi]
May 23 22:42:23 carotoshi kernel: [  361.337644]  [<f90c7142>] _usb_read32_sync+0x12/0x20 [rtlwifi]
May 23 22:42:23 carotoshi kernel: [  361.337658]  [<f909863f>] rtl92c_phy_set_bb_reg+0x1f/0x70 [rtl8192c_common]
May 23 22:42:23 carotoshi kernel: [  361.337671]  [<f9094056>] rtl92c_dm_write_dig+0x56/0xb0 [rtl8192c_common]
May 23 22:42:23 carotoshi kernel: [  361.337684]  [<f90981b3>] rtl92c_phy_set_io+0x33/0x70 [rtl8192c_common]
May 23 22:42:23 carotoshi kernel: [  361.337697]  [<f9098223>] rtl92c_phy_set_io_cmd+0x33/0x40 [rtl8192c_common]
May 23 22:42:23 carotoshi kernel: [  361.337709]  [<f910ec8c>] rtl92cu_set_hw_reg+0x33c/0xc10 [rtl8192cu]
May 23 22:42:23 carotoshi kernel: [  361.337718]  [<c109a203>] ? ktime_get+0x63/0x100
May 23 22:42:23 carotoshi kernel: [  361.337732]  [<f9097d37>] rtl92c_phy_scan_operation_backup+0x37/0x50 [rtl8192c_common]
May 23 22:42:23 carotoshi kernel: [  361.337746]  [<f90bf748>] rtl_op_sw_scan_start+0x58/0x80 [rtlwifi]
May 23 22:42:23 carotoshi kernel: [  361.337793]  [<f94aa67d>] __ieee80211_start_scan+0x25d/0x470 [mac80211]
May 23 22:42:23 carotoshi kernel: [  361.337805]  [<c103cef8>] ? default_spin_lock_flags+0x8/0x10
May 23 22:42:23 carotoshi kernel: [  361.337815]  [<c161531d>] ? _raw_spin_lock_irqsave+0x2d/0x40
May 23 22:42:23 carotoshi kernel: [  361.337855]  [<f94ab30e>] ieee80211_request_scan+0x2e/0x50 [mac80211]
May 23 22:42:23 carotoshi kernel: [  361.337898]  [<f94b7425>] ieee80211_scan+0x85/0x90 [mac80211]
May 23 22:42:23 carotoshi kernel: [  361.337948]  [<f936bd6d>] nl80211_trigger_scan+0x56d/0x610 [cfg80211]
May 23 22:42:23 carotoshi kernel: [  361.337990]  [<f935f160>] ? __cfg80211_rdev_from_attrs+0x170/0x170 [cfg80211]
May 23 22:42:23 carotoshi kernel: [  361.338001]  [<c155627d>] genl_rcv_msg+0x22d/0x290
May 23 22:42:23 carotoshi kernel: [  361.338014]  [<c1556050>] ? genl_rcv+0x30/0x30
May 23 22:42:23 carotoshi kernel: [  361.338023]  [<c1555c76>] netlink_rcv_skb+0x86/0xa0
May 23 22:42:23 carotoshi kernel: [  361.338032]  [<c155603c>] genl_rcv+0x1c/0x30
May 23 22:42:23 carotoshi kernel: [  361.338042]  [<c1555617>] netlink_unicast+0x167/0x1e0
May 23 22:42:23 carotoshi kernel: [  361.338052]  [<c15558b9>] netlink_sendmsg+0x229/0x3a0
May 23 22:42:23 carotoshi kernel: [  361.338062]  [<c151e56c>] sock_sendmsg+0x9c/0xd0
May 23 22:42:23 carotoshi kernel: [  361.338074]  [<c10744e5>] ? __wake_up_common+0x45/0x70
May 23 22:42:23 carotoshi kernel: [  361.338086]  [<c151e82a>] ___sys_sendmsg.part.13+0x28a/0x2a0
May 23 22:42:23 carotoshi kernel: [  361.338095]  [<c151ea50>] ? ___sys_recvmsg.part.7+0x1c0/0x1c0
May 23 22:42:23 carotoshi kernel: [  361.338105]  [<c105c4a7>] ? recalc_sigpending+0x17/0x50
May 23 22:42:23 carotoshi kernel: [  361.338113]  [<c105cea5>] ? __set_task_blocked+0x35/0x80
May 23 22:42:23 carotoshi kernel: [  361.338123]  [<c105eec3>] ? __set_current_blocked+0x43/0x60
May 23 22:42:23 carotoshi kernel: [  361.338132]  [<c105efb3>] ? set_current_blocked+0x13/0x20
May 23 22:42:23 carotoshi kernel: [  361.338142]  [<c1019315>] ? fpu_finit+0x55/0x70
May 23 22:42:23 carotoshi kernel: [  361.338152]  [<c101a63b>] ? __restore_xstate_sig+0x36b/0x510
May 23 22:42:23 carotoshi kernel: [  361.338164]  [<c12f3c61>] ? _copy_from_user+0x41/0x60
May 23 22:42:23 carotoshi kernel: [  361.338173]  [<c151fa3a>] __sys_sendmsg+0x4a/0x80
May 23 22:42:23 carotoshi kernel: [  361.338183]  [<c1520158>] sys_socketcall+0x268/0x2b0
May 23 22:42:23 carotoshi kernel: [  361.338193]  [<c12f3b41>] ? copy_to_user+0x41/0x60
May 23 22:42:23 carotoshi kernel: [  361.338204]  [<c105185a>] ? sys_gettimeofday+0x2a/0x70
May 23 22:42:23 carotoshi kernel: [  361.338212]  [<c161c50d>] sysenter_do_call+0x12/0x28
May 23 22:44:23 carotoshi kernel: [  481.336069] INFO: task kworker/1:1:47 blocked for more than 120 seconds.
May 23 22:44:23 carotoshi kernel: [  481.336085] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
May 23 22:44:23 carotoshi kernel: [  481.336093] kworker/1:1     D 00000000     0    47      2 0x00000000
May 23 22:44:23 carotoshi kernel: [  481.336106]  f3b4dc50 00000046 c148cf0a 00000000 f3bc9050 f38c19a0 cf6b578c 0000002a
May 23 22:44:23 carotoshi kernel: [  481.336126]  c19d80c0 c19d80c0 f383e864 35e00c70 f64e50c0 f395e680 c1016650 35e00c70
May 23 22:44:23 carotoshi kernel: [  481.336141]  00000000 00000004 87dab000 f219d180 f3b7e800 c189c4c0 f3b4dc64 f3b7e800
May 23 22:44:23 carotoshi kernel: [  481.336157] Call Trace:
May 23 22:44:23 carotoshi kernel: [  481.336186]  [<c148cf0a>] ? ehci_urb_enqueue+0xea/0xda0
May 23 22:44:23 carotoshi kernel: [  481.336201]  [<c1016650>] ? nommu_map_page+0x50/0x90
May 23 22:44:23 carotoshi kernel: [  481.336215]  [<c1614453>] schedule+0x23/0x60
May 23 22:44:23 carotoshi kernel: [  481.336228]  [<c1612c05>] schedule_timeout+0x1c5/0x240
May 23 22:44:23 carotoshi kernel: [  481.336240]  [<c1478af2>] ? usb_hcd_submit_urb+0x82/0x6e0
May 23 22:44:23 carotoshi kernel: [  481.336250]  [<c105b0c1>] ? update_process_times+0x61/0x70
May 23 22:44:23 carotoshi kernel: [  481.336262]  [<c12ef360>] ? timerqueue_add+0x50/0xb0
May 23 22:44:23 carotoshi kernel: [  481.336272]  [<c109a203>] ? ktime_get+0x63/0x100
May 23 22:44:23 carotoshi kernel: [  481.336280]  [<c16142d1>] wait_for_common+0xa1/0x120
May 23 22:44:23 carotoshi kernel: [  481.336294]  [<c107c7c0>] ? try_to_wake_up+0x240/0x240
May 23 22:44:23 carotoshi kernel: [  481.336303]  [<c1614402>] wait_for_completion_timeout+0x12/0x20
May 23 22:44:23 carotoshi kernel: [  481.336313]  [<c147acd6>] usb_start_wait_urb+0x66/0xd0
May 23 22:44:23 carotoshi kernel: [  481.336323]  [<c147af43>] usb_control_msg+0xb3/0xf0
May 23 22:44:23 carotoshi kernel: [  481.336332]  [<c161531d>] ? _raw_spin_lock_irqsave+0x2d/0x40
May 23 22:44:23 carotoshi kernel: [  481.336360]  [<f90c70c0>] _usb_read_sync+0xc0/0x130 [rtlwifi]
May 23 22:44:23 carotoshi kernel: [  481.336377]  [<f90c7142>] _usb_read32_sync+0x12/0x20 [rtlwifi]
May 23 22:44:23 carotoshi kernel: [  481.336395]  [<f90973b6>] rtl92c_phy_query_bb_reg+0x16/0x50 [rtl8192c_common]
May 23 22:44:23 carotoshi kernel: [  481.336410]  [<f90983a6>] _rtl92c_phy_rf_serial_read+0x176/0x1d0 [rtl8192c_common]
May 23 22:44:23 carotoshi kernel: [  481.336426]  [<f91118f5>] rtl92cu_phy_query_rf_reg+0x25/0x50 [rtl8192cu]
May 23 22:44:23 carotoshi kernel: [  481.336439]  [<f9094d01>] rtl92c_dm_txpower_tracking_callback_thermalmeter+0x51/0xaa0 [rtl8192c_common]
May 23 22:44:23 carotoshi kernel: [  481.336455]  [<f90c7292>] ? _usbctrl_vendorreq_async_write.constprop.24+0x102/0x190 [rtlwifi]
May 23 22:44:23 carotoshi kernel: [  481.336470]  [<f9095776>] rtl92c_dm_check_txpower_tracking_thermal_meter+0x26/0x70 [rtl8192c_common]
May 23 22:44:23 carotoshi kernel: [  481.336483]  [<f9095aec>] rtl92c_dm_watchdog.part.12+0x24c/0xaf0 [rtl8192c_common]
May 23 22:44:23 carotoshi kernel: [  481.336494]  [<f910e90c>] ? rtl92cu_get_hw_reg+0x12c/0x170 [rtl8192cu]
May 23 22:44:23 carotoshi kernel: [  481.336507]  [<f9096417>] rtl92c_dm_watchdog+0x87/0x90 [rtl8192c_common]
May 23 22:44:23 carotoshi kernel: [  481.336520]  [<f90bd1d8>] rtl_watchdog_wq_callback+0xe8/0x2e0 [rtlwifi]
May 23 22:44:23 carotoshi kernel: [  481.336529]  [<c105ad00>] ? mod_timer+0x140/0x1a0
May 23 22:44:23 carotoshi kernel: [  481.336538]  [<c1065be5>] ? __queue_delayed_work+0xa5/0x1c0
May 23 22:44:23 carotoshi kernel: [  481.336548]  [<c1066005>] process_one_work+0x135/0x3e0
May 23 22:44:23 carotoshi kernel: [  481.336558]  [<c161ca33>] ? common_interrupt+0x33/0x38
May 23 22:44:23 carotoshi kernel: [  481.336567]  [<c1066cf9>] worker_thread+0x119/0x3b0
May 23 22:44:23 carotoshi kernel: [  481.336575]  [<c1066be0>] ? manage_workers+0x240/0x240
May 23 22:44:23 carotoshi kernel: [  481.336586]  [<c106b724>] kthread+0x94/0xa0
May 23 22:44:23 carotoshi kernel: [  481.336597]  [<c1070000>] ? __hrtimer_start_range_ns+0x1a0/0x470
May 23 22:44:23 carotoshi kernel: [  481.336606]  [<c161c477>] ret_from_kernel_thread+0x1b/0x28
May 23 22:44:23 carotoshi kernel: [  481.336615]  [<c106b690>] ? kthread_create_on_node+0xc0/0xc0
May 23 22:44:23 carotoshi kernel: [  481.336628] INFO: task kworker/1:2:243 blocked for more than 120 seconds.
May 23 22:44:23 carotoshi kernel: [  481.336632] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
May 23 22:44:23 carotoshi kernel: [  481.336637] kworker/1:2     D 00000000     0   243      2 0x00000000
May 23 22:44:23 carotoshi kernel: [  481.336645]  f59add5c 00000046 c148cf0a 00000000 f3bc9050 f38c19a0 f5d22000 0000002b
May 23 22:44:23 carotoshi kernel: [  481.336661]  c19d80c0 c19d80c0 ba3c2833 0000002b f64e50c0 f5f82670 c1016650 35e00c74
May 23 22:44:23 carotoshi kernel: [  481.336676]  00000000 00000001 00000000 f21a5c00 f3b7e800 c189c4c0 f59add70 f3b7e800
May 23 22:44:23 carotoshi kernel: [  481.336690] Call Trace:
May 23 22:44:23 carotoshi kernel: [  481.336701]  [<c148cf0a>] ? ehci_urb_enqueue+0xea/0xda0
May 23 22:44:23 carotoshi kernel: [  481.336710]  [<c1016650>] ? nommu_map_page+0x50/0x90
May 23 22:44:23 carotoshi kernel: [  481.336720]  [<c1614453>] schedule+0x23/0x60
May 23 22:44:23 carotoshi kernel: [  481.336730]  [<c1612c05>] schedule_timeout+0x1c5/0x240
May 23 22:44:23 carotoshi kernel: [  481.336739]  [<c1478af2>] ? usb_hcd_submit_urb+0x82/0x6e0
May 23 22:44:23 carotoshi kernel: [  481.336749]  [<c16142d1>] wait_for_common+0xa1/0x120
May 23 22:44:23 carotoshi kernel: [  481.336759]  [<c107c7c0>] ? try_to_wake_up+0x240/0x240
May 23 22:44:23 carotoshi kernel: [  481.336768]  [<c1614402>] wait_for_completion_timeout+0x12/0x20
May 23 22:44:23 carotoshi kernel: [  481.336778]  [<c147acd6>] usb_start_wait_urb+0x66/0xd0
May 23 22:44:23 carotoshi kernel: [  481.336787]  [<c147af43>] usb_control_msg+0xb3/0xf0
May 23 22:44:23 carotoshi kernel: [  481.336797]  [<c161531d>] ? _raw_spin_lock_irqsave+0x2d/0x40
May 23 22:44:23 carotoshi kernel: [  481.336813]  [<f90c70c0>] _usb_read_sync+0xc0/0x130 [rtlwifi]
May 23 22:44:23 carotoshi kernel: [  481.336829]  [<f90c7182>] _usb_read8_sync+0x12/0x20 [rtlwifi]
May 23 22:44:23 carotoshi kernel: [  481.336840]  [<f910fa12>] rtl92cu_gpio_radio_on_off_checking+0x82/0x2d0 [rtl8192cu]
May 23 22:44:23 carotoshi kernel: [  481.336854]  [<f90bf5b3>] rtl_op_rfkill_poll+0x53/0x90 [rtlwifi]
May 23 22:44:23 carotoshi kernel: [  481.336924]  [<f94b81fc>] ieee80211_rfkill_poll+0x2c/0x40 [mac80211]
May 23 22:44:23 carotoshi kernel: [  481.336983]  [<f9354912>] cfg80211_rfkill_poll+0x22/0x80 [cfg80211]
May 23 22:44:23 carotoshi kernel: [  481.336993]  [<c15f663f>] rfkill_poll+0x1f/0x40
May 23 22:44:23 carotoshi kernel: [  481.337002]  [<c1066005>] process_one_work+0x135/0x3e0
May 23 22:44:23 carotoshi kernel: [  481.337012]  [<c16156dc>] ? reschedule_interrupt+0x34/0x3c
May 23 22:44:23 carotoshi kernel: [  481.337021]  [<c1066cf9>] worker_thread+0x119/0x3b0
May 23 22:44:23 carotoshi kernel: [  481.337030]  [<c1066be0>] ? manage_workers+0x240/0x240
May 23 22:44:23 carotoshi kernel: [  481.337039]  [<c106b724>] kthread+0x94/0xa0
May 23 22:44:23 carotoshi kernel: [  481.337049]  [<c1070000>] ? __hrtimer_start_range_ns+0x1a0/0x470
May 23 22:44:23 carotoshi kernel: [  481.337058]  [<c161c477>] ret_from_kernel_thread+0x1b/0x28
May 23 22:44:23 carotoshi kernel: [  481.337068]  [<c106b690>] ? kthread_create_on_node+0xc0/0xc0
May 23 22:44:23 carotoshi kernel: [  481.337083] INFO: task NetworkManager:870 blocked for more than 120 seconds.
May 23 22:44:23 carotoshi kernel: [  481.337088] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
May 23 22:44:23 carotoshi kernel: [  481.337092] NetworkManager  D 00000000     0   870      1 0x00000000
May 23 22:44:23 carotoshi kernel: [  481.337101]  f30f9c6c 00000082 001e8096 00000000 f2e26680 c18991e0 f2d9a094 00000036
May 23 22:44:23 carotoshi kernel: [  481.337116]  c19d80c0 c19d80c0 f30f9c78 00000286 f64d70c0 f2e26680 80100010 f2b854c4
May 23 22:44:23 carotoshi kernel: [  481.337131]  00000036 c15278dd 00000286 00000004 00000001 f5bc3100 000102d0 0000000e
May 23 22:44:23 carotoshi kernel: [  481.337146] Call Trace:
May 23 22:44:23 carotoshi kernel: [  481.337157]  [<c15278dd>] ? __alloc_skb+0x6d/0x250
May 23 22:44:23 carotoshi kernel: [  481.337166]  [<c1614453>] schedule+0x23/0x60
May 23 22:44:23 carotoshi kernel: [  481.337175]  [<c161469d>] schedule_preempt_disabled+0xd/0x10
May 23 22:44:23 carotoshi kernel: [  481.337187]  [<c16133b6>] __mutex_lock_slowpath+0xc6/0x120
May 23 22:44:23 carotoshi kernel: [  481.337198]  [<c1612f44>] mutex_lock+0x24/0x40
May 23 22:44:23 carotoshi kernel: [  481.337209]  [<c1556012>] genl_lock+0x12/0x20
May 23 22:44:23 carotoshi kernel: [  481.337218]  [<c1556030>] genl_rcv+0x10/0x30
May 23 22:44:23 carotoshi kernel: [  481.337228]  [<c1555617>] netlink_unicast+0x167/0x1e0
May 23 22:44:23 carotoshi kernel: [  481.337238]  [<c15558b9>] netlink_sendmsg+0x229/0x3a0
May 23 22:44:23 carotoshi kernel: [  481.337250]  [<c151e56c>] sock_sendmsg+0x9c/0xd0
May 23 22:44:23 carotoshi kernel: [  481.337262]  [<c1170ec0>] ? __pollwait+0xd0/0xd0
May 23 22:44:23 carotoshi kernel: [  481.337271]  [<c1170ec0>] ? __pollwait+0xd0/0xd0
May 23 22:44:23 carotoshi kernel: [  481.337282]  [<c151e82a>] ___sys_sendmsg.part.13+0x28a/0x2a0
May 23 22:44:23 carotoshi kernel: [  481.337293]  [<c1083beb>] ? task_tick_fair+0x15b/0x6f0
May 23 22:44:23 carotoshi kernel: [  481.337307]  [<c160becb>] ? nohz_balance_exit_idle.part.41+0x10/0x2b
May 23 22:44:23 carotoshi kernel: [  481.337316]  [<c10875f3>] ? trigger_load_balance+0xc3/0x1c0
May 23 22:44:23 carotoshi kernel: [  481.337326]  [<c107b69a>] ? scheduler_tick+0xda/0x100
May 23 22:44:23 carotoshi kernel: [  481.337334]  [<c105b0c1>] ? update_process_times+0x61/0x70
May 23 22:44:23 carotoshi kernel: [  481.337344]  [<c12ef360>] ? timerqueue_add+0x50/0xb0
May 23 22:44:23 carotoshi kernel: [  481.337353]  [<c109a203>] ? ktime_get+0x63/0x100
May 23 22:44:23 carotoshi kernel: [  481.337365]  [<c12f3c61>] ? _copy_from_user+0x41/0x60
May 23 22:44:23 carotoshi kernel: [  481.337374]  [<c151fa3a>] __sys_sendmsg+0x4a/0x80
May 23 22:44:23 carotoshi kernel: [  481.337384]  [<c1520158>] sys_socketcall+0x268/0x2b0
May 23 22:44:23 carotoshi kernel: [  481.337394]  [<c12f3b41>] ? copy_to_user+0x41/0x60
May 23 22:44:23 carotoshi kernel: [  481.337404]  [<c106b0f8>] ? sys_clock_gettime+0x48/0x70
May 23 22:44:23 carotoshi kernel: [  481.337413]  [<c161c50d>] sysenter_do_call+0x12/0x28
May 23 22:44:23 carotoshi kernel: [  481.337426] INFO: task wpa_supplicant:1051 blocked for more than 120 seconds.
May 23 22:44:23 carotoshi kernel: [  481.337430] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
May 23 22:44:23 carotoshi kernel: [  481.337434] wpa_supplicant  D 00000000     0  1051      1 0x00000000
May 23 22:44:23 carotoshi kernel: [  481.337443]  f33439dc 00200086 c148cf0a 00000000 f3bc9050 c18991e0 f3a84000 00000035
May 23 22:44:23 carotoshi kernel: [  481.337458]  c19d80c0 c19d80c0 8d4f207a 00000035 f64d70c0 f3364010 c1016650 35e00c78
May 23 22:44:23 carotoshi kernel: [  481.337473]  00000000 00000004 00000000 f2b60780 f3b7e800 c189c4c0 f33439f0 f3b7e800
May 23 22:44:23 carotoshi kernel: [  481.337487] Call Trace:
May 23 22:44:23 carotoshi kernel: [  481.337498]  [<c148cf0a>] ? ehci_urb_enqueue+0xea/0xda0
May 23 22:44:23 carotoshi kernel: [  481.337507]  [<c1016650>] ? nommu_map_page+0x50/0x90
May 23 22:44:23 carotoshi kernel: [  481.337517]  [<c1614453>] schedule+0x23/0x60
May 23 22:44:23 carotoshi kernel: [  481.337526]  [<c1612c05>] schedule_timeout+0x1c5/0x240
May 23 22:44:23 carotoshi kernel: [  481.337536]  [<c1478af2>] ? usb_hcd_submit_urb+0x82/0x6e0
May 23 22:44:23 carotoshi kernel: [  481.337550]  [<c1010a5f>] ? __switch_to+0xaf/0x320
May 23 22:44:23 carotoshi kernel: [  481.337559]  [<c16142d1>] wait_for_common+0xa1/0x120
May 23 22:44:23 carotoshi kernel: [  481.337569]  [<c107c7c0>] ? try_to_wake_up+0x240/0x240
May 23 22:44:23 carotoshi kernel: [  481.337578]  [<c1614402>] wait_for_completion_timeout+0x12/0x20
May 23 22:44:23 carotoshi kernel: [  481.337587]  [<c147acd6>] usb_start_wait_urb+0x66/0xd0
May 23 22:44:23 carotoshi kernel: [  481.337597]  [<c147af43>] usb_control_msg+0xb3/0xf0
May 23 22:44:23 carotoshi kernel: [  481.337606]  [<c161531d>] ? _raw_spin_lock_irqsave+0x2d/0x40
May 23 22:44:23 carotoshi kernel: [  481.337622]  [<f90c70c0>] _usb_read_sync+0xc0/0x130 [rtlwifi]
May 23 22:44:23 carotoshi kernel: [  481.337638]  [<f90c7142>] _usb_read32_sync+0x12/0x20 [rtlwifi]
May 23 22:44:23 carotoshi kernel: [  481.337651]  [<f909863f>] rtl92c_phy_set_bb_reg+0x1f/0x70 [rtl8192c_common]
May 23 22:44:23 carotoshi kernel: [  481.337663]  [<f9094056>] rtl92c_dm_write_dig+0x56/0xb0 [rtl8192c_common]
May 23 22:44:23 carotoshi kernel: [  481.337676]  [<f90981b3>] rtl92c_phy_set_io+0x33/0x70 [rtl8192c_common]
May 23 22:44:23 carotoshi kernel: [  481.337689]  [<f9098223>] rtl92c_phy_set_io_cmd+0x33/0x40 [rtl8192c_common]
May 23 22:44:23 carotoshi kernel: [  481.337701]  [<f910ec8c>] rtl92cu_set_hw_reg+0x33c/0xc10 [rtl8192cu]
May 23 22:44:23 carotoshi kernel: [  481.337710]  [<c109a203>] ? ktime_get+0x63/0x100
May 23 22:44:23 carotoshi kernel: [  481.337724]  [<f9097d37>] rtl92c_phy_scan_operation_backup+0x37/0x50 [rtl8192c_common]
May 23 22:44:23 carotoshi kernel: [  481.337738]  [<f90bf748>] rtl_op_sw_scan_start+0x58/0x80 [rtlwifi]
May 23 22:44:23 carotoshi kernel: [  481.337784]  [<f94aa67d>] __ieee80211_start_scan+0x25d/0x470 [mac80211]
May 23 22:44:23 carotoshi kernel: [  481.337797]  [<c103cef8>] ? default_spin_lock_flags+0x8/0x10
May 23 22:44:23 carotoshi kernel: [  481.337806]  [<c161531d>] ? _raw_spin_lock_irqsave+0x2d/0x40
May 23 22:44:23 carotoshi kernel: [  481.337846]  [<f94ab30e>] ieee80211_request_scan+0x2e/0x50 [mac80211]
May 23 22:44:23 carotoshi kernel: [  481.337889]  [<f94b7425>] ieee80211_scan+0x85/0x90 [mac80211]
May 23 22:44:23 carotoshi kernel: [  481.337938]  [<f936bd6d>] nl80211_trigger_scan+0x56d/0x610 [cfg80211]
May 23 22:44:23 carotoshi kernel: [  481.337981]  [<f935f160>] ? __cfg80211_rdev_from_attrs+0x170/0x170 [cfg80211]
May 23 22:44:23 carotoshi kernel: [  481.337991]  [<c155627d>] genl_rcv_msg+0x22d/0x290
May 23 22:44:23 carotoshi kernel: [  481.338004]  [<c1556050>] ? genl_rcv+0x30/0x30
May 23 22:44:23 carotoshi kernel: [  481.338013]  [<c1555c76>] netlink_rcv_skb+0x86/0xa0
May 23 22:44:23 carotoshi kernel: [  481.338022]  [<c155603c>] genl_rcv+0x1c/0x30
May 23 22:44:23 carotoshi kernel: [  481.338032]  [<c1555617>] netlink_unicast+0x167/0x1e0
May 23 22:44:23 carotoshi kernel: [  481.338042]  [<c15558b9>] netlink_sendmsg+0x229/0x3a0
May 23 22:44:23 carotoshi kernel: [  481.338052]  [<c151e56c>] sock_sendmsg+0x9c/0xd0
May 23 22:44:23 carotoshi kernel: [  481.338065]  [<c10744e5>] ? __wake_up_common+0x45/0x70
May 23 22:44:23 carotoshi kernel: [  481.338076]  [<c151e82a>] ___sys_sendmsg.part.13+0x28a/0x2a0
May 23 22:44:23 carotoshi kernel: [  481.338086]  [<c151ea50>] ? ___sys_recvmsg.part.7+0x1c0/0x1c0
May 23 22:44:23 carotoshi kernel: [  481.338095]  [<c105c4a7>] ? recalc_sigpending+0x17/0x50
May 23 22:44:23 carotoshi kernel: [  481.338104]  [<c105cea5>] ? __set_task_blocked+0x35/0x80
May 23 22:44:23 carotoshi kernel: [  481.338114]  [<c105eec3>] ? __set_current_blocked+0x43/0x60
May 23 22:44:23 carotoshi kernel: [  481.338123]  [<c105efb3>] ? set_current_blocked+0x13/0x20
May 23 22:44:23 carotoshi kernel: [  481.338133]  [<c1019315>] ? fpu_finit+0x55/0x70
May 23 22:44:23 carotoshi kernel: [  481.338143]  [<c101a63b>] ? __restore_xstate_sig+0x36b/0x510
May 23 22:44:23 carotoshi kernel: [  481.338154]  [<c12f3c61>] ? _copy_from_user+0x41/0x60
May 23 22:44:23 carotoshi kernel: [  481.338164]  [<c151fa3a>] __sys_sendmsg+0x4a/0x80
May 23 22:44:23 carotoshi kernel: [  481.338174]  [<c1520158>] sys_socketcall+0x268/0x2b0
May 23 22:44:23 carotoshi kernel: [  481.338184]  [<c12f3b41>] ? copy_to_user+0x41/0x60
May 23 22:44:23 carotoshi kernel: [  481.338194]  [<c105185a>] ? sys_gettimeofday+0x2a/0x70
May 23 22:44:23 carotoshi kernel: [  481.338203]  [<c161c50d>] sysenter_do_call+0x12/0x28
May 23 22:46:23 carotoshi kernel: [  601.336091] INFO: task kworker/1:1:47 blocked for more than 120 seconds.
May 23 22:46:23 carotoshi kernel: [  601.336106] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
May 23 22:46:23 carotoshi kernel: [  601.336113] kworker/1:1     D 00000000     0    47      2 0x00000000
May 23 22:46:23 carotoshi kernel: [  601.336128]  f3b4dc50 00000046 c148cf0a 00000000 f3bc9050 f38c19a0 cf6b578c 0000002a
May 23 22:46:23 carotoshi kernel: [  601.336146]  c19d80c0 c19d80c0 f383e864 35e00c70 f64e50c0 f395e680 c1016650 35e00c70
May 23 22:46:23 carotoshi kernel: [  601.336162]  00000000 00000004 87dab000 f219d180 f3b7e800 c189c4c0 f3b4dc64 f3b7e800
May 23 22:46:23 carotoshi kernel: [  601.336178] Call Trace:
May 23 22:46:23 carotoshi kernel: [  601.336202]  [<c148cf0a>] ? ehci_urb_enqueue+0xea/0xda0
May 23 22:46:23 carotoshi kernel: [  601.336218]  [<c1016650>] ? nommu_map_page+0x50/0x90
May 23 22:46:23 carotoshi kernel: [  601.336231]  [<c1614453>] schedule+0x23/0x60
May 23 22:46:23 carotoshi kernel: [  601.336245]  [<c1612c05>] schedule_timeout+0x1c5/0x240
May 23 22:46:23 carotoshi kernel: [  601.336257]  [<c1478af2>] ? usb_hcd_submit_urb+0x82/0x6e0
May 23 22:46:23 carotoshi kernel: [  601.336268]  [<c105b0c1>] ? update_process_times+0x61/0x70
May 23 22:46:23 carotoshi kernel: [  601.336281]  [<c12ef360>] ? timerqueue_add+0x50/0xb0
May 23 22:46:23 carotoshi kernel: [  601.336291]  [<c109a203>] ? ktime_get+0x63/0x100
May 23 22:46:23 carotoshi kernel: [  601.336299]  [<c16142d1>] wait_for_common+0xa1/0x120
May 23 22:46:23 carotoshi kernel: [  601.336311]  [<c107c7c0>] ? try_to_wake_up+0x240/0x240
May 23 22:46:23 carotoshi kernel: [  601.336320]  [<c1614402>] wait_for_completion_timeout+0x12/0x20
May 23 22:46:23 carotoshi kernel: [  601.336331]  [<c147acd6>] usb_start_wait_urb+0x66/0xd0
May 23 22:46:23 carotoshi kernel: [  601.336340]  [<c147af43>] usb_control_msg+0xb3/0xf0
May 23 22:46:23 carotoshi kernel: [  601.336350]  [<c161531d>] ? _raw_spin_lock_irqsave+0x2d/0x40
May 23 22:46:23 carotoshi kernel: [  601.336377]  [<f90c70c0>] _usb_read_sync+0xc0/0x130 [rtlwifi]
May 23 22:46:23 carotoshi kernel: [  601.336395]  [<f90c7142>] _usb_read32_sync+0x12/0x20 [rtlwifi]
May 23 22:46:23 carotoshi kernel: [  601.336414]  [<f90973b6>] rtl92c_phy_query_bb_reg+0x16/0x50 [rtl8192c_common]
May 23 22:46:23 carotoshi kernel: [  601.336428]  [<f90983a6>] _rtl92c_phy_rf_serial_read+0x176/0x1d0 [rtl8192c_common]
May 23 22:46:23 carotoshi kernel: [  601.336443]  [<f91118f5>] rtl92cu_phy_query_rf_reg+0x25/0x50 [rtl8192cu]
May 23 22:46:23 carotoshi kernel: [  601.336456]  [<f9094d01>] rtl92c_dm_txpower_tracking_callback_thermalmeter+0x51/0xaa0 [rtl8192c_common]
May 23 22:46:23 carotoshi kernel: [  601.336473]  [<f90c7292>] ? _usbctrl_vendorreq_async_write.constprop.24+0x102/0x190 [rtlwifi]
May 23 22:46:23 carotoshi kernel: [  601.336487]  [<f9095776>] rtl92c_dm_check_txpower_tracking_thermal_meter+0x26/0x70 [rtl8192c_common]
May 23 22:46:23 carotoshi kernel: [  601.336500]  [<f9095aec>] rtl92c_dm_watchdog.part.12+0x24c/0xaf0 [rtl8192c_common]
May 23 22:46:23 carotoshi kernel: [  601.336512]  [<f910e90c>] ? rtl92cu_get_hw_reg+0x12c/0x170 [rtl8192cu]
May 23 22:46:23 carotoshi kernel: [  601.336525]  [<f9096417>] rtl92c_dm_watchdog+0x87/0x90 [rtl8192c_common]
May 23 22:46:23 carotoshi kernel: [  601.336538]  [<f90bd1d8>] rtl_watchdog_wq_callback+0xe8/0x2e0 [rtlwifi]
May 23 22:46:23 carotoshi kernel: [  601.336546]  [<c105ad00>] ? mod_timer+0x140/0x1a0
May 23 22:46:23 carotoshi kernel: [  601.336556]  [<c1065be5>] ? __queue_delayed_work+0xa5/0x1c0
May 23 22:46:23 carotoshi kernel: [  601.336566]  [<c1066005>] process_one_work+0x135/0x3e0
May 23 22:46:23 carotoshi kernel: [  601.336576]  [<c161ca33>] ? common_interrupt+0x33/0x38
May 23 22:46:23 carotoshi kernel: [  601.336586]  [<c1066cf9>] worker_thread+0x119/0x3b0
May 23 22:46:23 carotoshi kernel: [  601.336594]  [<c1066be0>] ? manage_workers+0x240/0x240
May 23 22:46:23 carotoshi kernel: [  601.336604]  [<c106b724>] kthread+0x94/0xa0
May 23 22:46:23 carotoshi kernel: [  601.336615]  [<c1070000>] ? __hrtimer_start_range_ns+0x1a0/0x470
May 23 22:46:23 carotoshi kernel: [  601.336624]  [<c161c477>] ret_from_kernel_thread+0x1b/0x28
May 23 22:46:23 carotoshi kernel: [  601.336634]  [<c106b690>] ? kthread_create_on_node+0xc0/0xc0
May 23 22:46:23 carotoshi kernel: [  601.336645] INFO: task kworker/1:2:243 blocked for more than 120 seconds.
May 23 22:46:23 carotoshi kernel: [  601.336650] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
May 23 22:46:23 carotoshi kernel: [  601.336654] kworker/1:2     D 00000000     0   243      2 0x00000000
May 23 22:46:23 carotoshi kernel: [  601.336664]  f59add5c 00000046 c148cf0a 00000000 f3bc9050 f38c19a0 f5d22000 0000002b
May 23 22:46:23 carotoshi kernel: [  601.336679]  c19d80c0 c19d80c0 ba3c2833 0000002b f64e50c0 f5f82670 c1016650 35e00c74
May 23 22:46:23 carotoshi kernel: [  601.336694]  00000000 00000001 00000000 f21a5c00 f3b7e800 c189c4c0 f59add70 f3b7e800
May 23 22:46:23 carotoshi kernel: [  601.336709] Call Trace:
May 23 22:46:23 carotoshi kernel: [  601.336720]  [<c148cf0a>] ? ehci_urb_enqueue+0xea/0xda0
May 23 22:46:23 carotoshi kernel: [  601.336729]  [<c1016650>] ? nommu_map_page+0x50/0x90
May 23 22:46:23 carotoshi kernel: [  601.336739]  [<c1614453>] schedule+0x23/0x60
May 23 22:46:23 carotoshi kernel: [  601.336749]  [<c1612c05>] schedule_timeout+0x1c5/0x240
May 23 22:46:23 carotoshi kernel: [  601.336758]  [<c1478af2>] ? usb_hcd_submit_urb+0x82/0x6e0
May 23 22:46:23 carotoshi kernel: [  601.336768]  [<c16142d1>] wait_for_common+0xa1/0x120
May 23 22:46:23 carotoshi kernel: [  601.336777]  [<c107c7c0>] ? try_to_wake_up+0x240/0x240
May 23 22:46:23 carotoshi kernel: [  601.336787]  [<c1614402>] wait_for_completion_timeout+0x12/0x20
May 23 22:46:23 carotoshi kernel: [  601.336796]  [<c147acd6>] usb_start_wait_urb+0x66/0xd0
May 23 22:46:23 carotoshi kernel: [  601.336805]  [<c147af43>] usb_control_msg+0xb3/0xf0
May 23 22:46:23 carotoshi kernel: [  601.336815]  [<c161531d>] ? _raw_spin_lock_irqsave+0x2d/0x40
May 23 22:46:23 carotoshi kernel: [  601.336830]  [<f90c70c0>] _usb_read_sync+0xc0/0x130 [rtlwifi]
May 23 22:46:23 carotoshi kernel: [  601.336846]  [<f90c7182>] _usb_read8_sync+0x12/0x20 [rtlwifi]
May 23 22:46:23 carotoshi kernel: [  601.336858]  [<f910fa12>] rtl92cu_gpio_radio_on_off_checking+0x82/0x2d0 [rtl8192cu]
May 23 22:46:23 carotoshi kernel: [  601.336871]  [<f90bf5b3>] rtl_op_rfkill_poll+0x53/0x90 [rtlwifi]
May 23 22:46:23 carotoshi kernel: [  601.336940]  [<f94b81fc>] ieee80211_rfkill_poll+0x2c/0x40 [mac80211]
May 23 22:46:23 carotoshi kernel: [  601.337000]  [<f9354912>] cfg80211_rfkill_poll+0x22/0x80 [cfg80211]
May 23 22:46:23 carotoshi kernel: [  601.337010]  [<c15f663f>] rfkill_poll+0x1f/0x40
May 23 22:46:23 carotoshi kernel: [  601.337018]  [<c1066005>] process_one_work+0x135/0x3e0
May 23 22:46:23 carotoshi kernel: [  601.337029]  [<c16156dc>] ? reschedule_interrupt+0x34/0x3c
May 23 22:46:23 carotoshi kernel: [  601.337038]  [<c1066cf9>] worker_thread+0x119/0x3b0
May 23 22:46:23 carotoshi kernel: [  601.337046]  [<c1066be0>] ? manage_workers+0x240/0x240
May 23 22:46:23 carotoshi kernel: [  601.337056]  [<c106b724>] kthread+0x94/0xa0
May 23 22:46:23 carotoshi kernel: [  601.337066]  [<c1070000>] ? __hrtimer_start_range_ns+0x1a0/0x470
May 23 22:46:23 carotoshi kernel: [  601.337075]  [<c161c477>] ret_from_kernel_thread+0x1b/0x28
May 23 22:46:23 carotoshi kernel: [  601.337084]  [<c106b690>] ? kthread_create_on_node+0xc0/0xc0
May 23 22:52:00 carotoshi kernel: [  938.200288] rtl8187: wireless radio switch turned off
May 23 22:52:04 carotoshi kernel: [  943.015272] rtl8187: wireless radio switch turned on
May 23 22:57:26 carotoshi kernel: [ 1264.384251] rtl8187: wireless radio switch turned off
May 23 22:57:27 carotoshi wpa_supplicant[1051]: rfkill: WLAN hard blocked
May 23 22:57:27 carotoshi wpa_supplicant[1051]: rfkill: WLAN hard blocked
May 23 22:57:27 carotoshi NetworkManager[870]: <info> WiFi now disabled by radio killswitch
May 23 22:57:27 carotoshi NetworkManager[870]: <info> (wlan0): device state change: activated -> unavailable (reason 'none') [100 20 0]
May 23 22:57:27 carotoshi NetworkManager[870]: <info> (wlan0): deactivating device (reason 'none') [0]
May 23 22:57:27 carotoshi wpa_supplicant[1051]: rfkill: WLAN unblocked
May 23 22:57:27 carotoshi wpa_supplicant[1051]: rfkill: WLAN unblocked
May 23 22:57:27 carotoshi wpa_supplicant[1051]: Could not set interface wlan1 flags: Operation not possible due to RF-kill
May 23 22:57:27 carotoshi wpa_supplicant[1051]: rfkill: WLAN hard blocked
May 23 22:57:27 carotoshi wpa_supplicant[1051]: rfkill: WLAN hard blocked
May 23 22:57:27 carotoshi NetworkManager[870]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 1565
May 23 22:57:27 carotoshi kernel: [ 1265.917476] wlan0: deauthenticating from 10:fe:ed:c3:47:b7 by local choice (reason=3)
May 23 22:57:27 carotoshi kernel: [ 1265.936897] cfg80211: Calling CRDA to update world regulatory domain
May 23 22:57:27 carotoshi kernel: [ 1265.937791] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
May 23 22:57:27 carotoshi avahi-daemon[708]: Withdrawing address record for 192.168.0.3 on wlan0.
May 23 22:57:27 carotoshi avahi-daemon[708]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.3.
May 23 22:57:27 carotoshi avahi-daemon[708]: Interface wlan0.IPv4 no longer relevant for mDNS.
May 23 22:57:27 carotoshi NetworkManager[870]: <warn> DNS: plugin dnsmasq update failed
May 23 22:57:27 carotoshi NetworkManager[870]: <info> Removing DNS information from /sbin/resolvconf
May 23 22:57:27 carotoshi dnsmasq[1572]: configuration des serveurs amonts à partir de DBus
May 23 22:57:27 carotoshi wpa_supplicant[1051]: wlan0: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=3
May 23 22:57:27 carotoshi kernel: [ 1265.966501] cfg80211: World regulatory domain updated:
May 23 22:57:27 carotoshi kernel: [ 1265.966527] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
May 23 22:57:27 carotoshi kernel: [ 1265.966535] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 23 22:57:27 carotoshi kernel: [ 1265.966542] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
May 23 22:57:27 carotoshi kernel: [ 1265.966548] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
May 23 22:57:27 carotoshi kernel: [ 1265.966554] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 23 22:57:27 carotoshi kernel: [ 1265.966561] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 23 22:57:27 carotoshi NetworkManager[870]: <info> (wlan0): taking down device.
May 23 22:57:27 carotoshi dbus[616]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
May 23 22:57:27 carotoshi dbus[616]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
May 23 22:57:28 carotoshi NetworkManager[870]: <info> (wlan1): device state change: disconnected -> unavailable (reason 'none') [30 20 0]
May 23 22:57:28 carotoshi NetworkManager[870]: <info> (wlan1): deactivating device (reason 'none') [0]
May 23 22:57:31 carotoshi NetworkManager[870]: <info> WiFi now enabled by radio killswitch
May 23 22:57:31 carotoshi NetworkManager[870]: <info> (wlan0): bringing up device.
May 23 22:57:31 carotoshi kernel: [ 1270.000874] rtl8187: wireless radio switch turned on
May 23 22:57:31 carotoshi kernel: [ 1270.007491] rtl8192cu: MAC auto ON okay!
May 23 22:57:31 carotoshi kernel: [ 1270.046275] rtl8192cu: Tx queue select: 0x05
May 23 22:57:32 carotoshi NetworkManager[870]: <info> (wlan1): bringing up device.
May 23 22:57:32 carotoshi kernel: [ 1270.425519] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
May 23 22:57:37 carotoshi kernel: [ 1275.349454] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
May 23 22:57:37 carotoshi NetworkManager[870]: <info> (wlan0) supports 4 scan SSIDs
May 23 22:57:37 carotoshi NetworkManager[870]: <warn> Trying to remove a non-existant call id.
May 23 22:57:37 carotoshi NetworkManager[870]: <info> (wlan0): supplicant interface state: starting -> ready
May 23 22:57:37 carotoshi NetworkManager[870]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
May 23 22:57:37 carotoshi NetworkManager[870]: <info> (wlan1) supports 4 scan SSIDs
May 23 22:57:37 carotoshi NetworkManager[870]: <warn> Trying to remove a non-existant call id.
May 23 22:57:37 carotoshi NetworkManager[870]: <info> (wlan1): supplicant interface state: starting -> ready
May 23 22:57:37 carotoshi NetworkManager[870]: <info> (wlan1): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
May 23 22:57:37 carotoshi NetworkManager[870]: <info> (wlan0): supplicant interface state: ready -> inactive
May 23 22:57:37 carotoshi NetworkManager[870]: <info> (wlan0) supports 4 scan SSIDs
May 23 22:57:37 carotoshi NetworkManager[870]: <info> (wlan1): supplicant interface state: ready -> inactive
May 23 22:57:37 carotoshi NetworkManager[870]: <info> (wlan1) supports 4 scan SSIDs
May 23 22:57:37 carotoshi NetworkManager[870]: <info> Auto-activating connection 'mynetwork 1'.
May 23 22:57:37 carotoshi NetworkManager[870]: <info> Activation (wlan0) starting connection 'mynetwork 1'
May 23 22:57:37 carotoshi NetworkManager[870]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
May 23 22:57:37 carotoshi NetworkManager[870]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
May 23 22:57:37 carotoshi NetworkManager[870]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
May 23 22:57:37 carotoshi NetworkManager[870]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
May 23 22:57:37 carotoshi NetworkManager[870]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
May 23 22:57:37 carotoshi NetworkManager[870]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
May 23 22:57:37 carotoshi NetworkManager[870]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
May 23 22:57:37 carotoshi NetworkManager[870]: <info> Activation (wlan0/wireless): connection 'mynetwork 1' has security, and secrets exist.  No new secrets needed.
May 23 22:57:37 carotoshi NetworkManager[870]: <info> Config: added 'ssid' value 'mynetwork'
May 23 22:57:37 carotoshi NetworkManager[870]: <info> Config: added 'scan_ssid' value '1'
May 23 22:57:37 carotoshi NetworkManager[870]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
May 23 22:57:37 carotoshi NetworkManager[870]: <info> Config: added 'auth_alg' value 'OPEN'
May 23 22:57:37 carotoshi NetworkManager[870]: <info> Config: added 'psk' value '<omitted>'
May 23 22:57:37 carotoshi NetworkManager[870]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
May 23 22:57:37 carotoshi NetworkManager[870]: <info> Config: set interface ap_scan to 1
May 23 22:57:38 carotoshi NetworkManager[870]: <info> (wlan0): supplicant interface state: inactive -> scanning
```


- Load average is high and I don't know why :
```
top - 23:18:23 up 42 min,  4 users,  load average: 5,00, 4,93, 4,22
Tasks: 154 total,   1 running, 153 sleeping,   0 stopped,   0 zombie
%Cpu(s):  2,0 us,  1,5 sy,  0,0 ni, 96,5 id,  0,0 wa,  0,0 hi,  0,0 si,  0,0 st
KiB Mem:   2971928 total,   447940 used,  2523988 free,    31060 buffers
KiB Swap:  2441876 total,        0 used,  2441876 free,   252328 cached

  PID USER      PR  NI  VIRT  RES  SHR S  %CPU %MEM    TIME+  COMMAND                           
 1117 root      20   0 77020  26m 8768 S   3,9  0,9   0:48.94 Xorg                              
 1992 caro      20   0  211m  14m  10m S   2,0  0,5   0:15.46 xfce4-terminal                    
 2112 caro      20   0  5464 1308  952 R   1,0  0,0   0:38.52 top  
```


- When I enter in sleep mode, when I log back, I definitely lost the network connection. I can't connect to internet, even if i plug a network cable !
 - If I wait too much, lshw hangs on "network", same with "sudo -i" : I can't ever enter my password...

Here is my questions :
 - What I could to get an usable laptop ? 
 - Why NetworkManager crashs ? 
 - Why sleep mode destroy any network connection ? 
 - Why I can't reboot my PC, it hangs also ?


 Thanks by advance for any lead.

[ATTACH]262159[/ATTACH]
[ATTACH]262160[/ATTACH]
[ATTACH]262161[/ATTACH]
[ATTACH]262163[/ATTACH]
[ATTACH]262162[/ATTACH]

---

### Post by cronos6 on 2015-05-26
Little up please

---

