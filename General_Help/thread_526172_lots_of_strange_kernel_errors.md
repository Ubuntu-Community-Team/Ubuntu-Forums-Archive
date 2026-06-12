---
title: "lots of strange kernel errors"
date: 2007-08-15
forum: General Help
---

### Post by supermihi on 2007-08-15
Hi,

on a kubuntu dapper machine running fine since roughly a year, yesterday it crashed, leaving lots of this stuff in /var/log/messages:

```
Aug 14 18:18:06 cardassia kernel: [17289535.116000]  [bad_page+135/192] bad_page+0x87/0xc0
Aug 14 18:18:06 cardassia kernel: [17289535.116000]  [free_hot_cold_page+76/320] free_hot_cold_page+0x4c/0x140
Aug 14 18:18:06 cardassia kernel: [17289535.116000]  [zap_pte_range+600/784] zap_pte_range+0x258/0x310
Aug 14 18:18:06 cardassia kernel: [17289535.116000]  [unmap_page_range+246/304] unmap_page_range+0xf6/0x130
Aug 14 18:18:06 cardassia kernel: [17289535.116000]  [unmap_vmas+208/592] unmap_vmas+0xd0/0x250
Aug 14 18:18:06 cardassia kernel: [17289535.116000]  [unmap_region+178/352] unmap_region+0xb2/0x160
Aug 14 18:18:06 cardassia kernel: [17289535.116000]  [do_munmap+265/336] do_munmap+0x109/0x150
Aug 14 18:18:06 cardassia kernel: [17289535.116000]  [sys_munmap+81/128] sys_munmap+0x51/0x80
Aug 14 18:18:06 cardassia kernel: [17289535.116000]  [syscall_call+7/11] syscall_call+0x7/0xb
Aug 14 18:18:06 cardassia kernel: [17289535.116000]  [bad_page+135/192] bad_page+0x87/0xc0
Aug 14 18:18:06 cardassia kernel: [17289535.116000]  [free_hot_cold_page+76/320] free_hot_cold_page+0x4c/0x140
Aug 14 18:18:06 cardassia kernel: [17289535.116000]  [zap_pte_range+600/784] zap_pte_range+0x258/0x310
Aug 14 18:18:06 cardassia kernel: [17289535.116000]  [unmap_page_range+246/304] unmap_page_range+0xf6/0x130
Aug 14 18:18:06 cardassia kernel: [17289535.116000]  [unmap_vmas+208/592] unmap_vmas+0xd0/0x250
Aug 14 18:18:06 cardassia kernel: [17289535.116000]  [unmap_region+178/352] unmap_region+0xb2/0x160
Aug 14 18:18:06 cardassia kernel: [17289535.116000]  [do_munmap+265/336] do_munmap+0x109/0x150
Aug 14 18:18:06 cardassia kernel: [17289535.116000]  [sys_munmap+81/128] sys_munmap+0x51/0x80
Aug 14 18:18:06 cardassia kernel: [17289535.116000]  [syscall_call+7/11] syscall_call+0x7/0xb
Aug 14 18:18:06 cardassia kernel: [17289535.116000]  [bad_page+135/192] bad_page+0x87/0xc0
Aug 14 18:18:06 cardassia kernel: [17289535.116000]  [free_hot_cold_page+76/320] free_hot_cold_page+0x4c/0x140
Aug 14 18:18:06 cardassia kernel: [17289535.116000]  [zap_pte_range+600/784] zap_pte_range+0x258/0x310
Aug 14 18:18:06 cardassia kernel: [17289535.116000]  [unmap_page_range+246/304] unmap_page_range+0xf6/0x130
Aug 14 18:18:06 cardassia kernel: [17289535.116000]  [unmap_vmas+208/592] unmap_vmas+0xd0/0x250
Aug 14 18:18:06 cardassia kernel: [17289535.116000]  [unmap_region+178/352] unmap_region+0xb2/0x160
Aug 14 18:18:06 cardassia kernel: [17289535.116000]  [do_munmap+265/336] do_munmap+0x109/0x150
Aug 14 18:18:06 cardassia kernel: [17289535.116000]  [sys_munmap+81/128] sys_munmap+0x51/0x80
Aug 14 18:18:06 cardassia kernel: [17289535.116000]  [syscall_call+7/11] syscall_call+0x7/0xb
Aug 14 18:18:06 cardassia kernel: [17289535.116000]  [bad_page+135/192] bad_page+0x87/0xc0
Aug 14 18:18:06 cardassia kernel: [17289535.116000]  [free_hot_cold_page+76/320] free_hot_cold_page+0x4c/0x140
Aug 14 18:18:06 cardassia kernel: [17289535.116000]  [zap_pte_range+600/784] zap_pte_range+0x258/0x310
Aug 14 18:18:06 cardassia kernel: [17289535.116000]  [unmap_page_range+246/304] unmap_page_range+0xf6/0x130
Aug 14 18:18:06 cardassia kernel: [17289535.116000]  [unmap_vmas+208/592] unmap_vmas+0xd0/0x250
Aug 14 18:18:06 cardassia kernel: [17289535.116000]  [unmap_region+178/352] unmap_region+0xb2/0x160
Aug 14 18:18:06 cardassia kernel: [17289535.116000]  [do_munmap+265/336] do_munmap+0x109/0x150
Aug 14 18:18:06 cardassia kernel: [17289535.116000]  [sys_munmap+81/128] sys_munmap+0x51/0x80
Aug 14 18:18:06 cardassia kernel: [17289535.116000]  [syscall_call+7/11] syscall_call+0x7/0xb
Aug 14 18:18:06 cardassia kernel: [17289535.116000]  [bad_page+135/192] bad_page+0x87/0xc0
Aug 14 18:18:06 cardassia kernel: [17289535.116000]  [free_hot_cold_page+76/320] free_hot_cold_page+0x4c/0x140
Aug 14 18:18:06 cardassia kernel: [17289535.116000]  [zap_pte_range+600/784] zap_pte_range+0x258/0x310
Aug 14 18:18:06 cardassia kernel: [17289535.116000]  [unmap_page_range+246/304] unmap_page_range+0xf6/0x130
Aug 14 18:18:06 cardassia kernel: [17289535.116000]  [unmap_vmas+208/592] unmap_vmas+0xd0/0x250
Aug 14 18:18:06 cardassia kernel: [17289535.116000]  [unmap_region+178/352] unmap_region+0xb2/0x160
Aug 14 18:18:06 cardassia kernel: [17289535.116000]  [do_munmap+265/336] do_munmap+0x109/0x150
Aug 14 18:18:06 cardassia kernel: [17289535.116000]  [sys_munmap+81/128] sys_munmap+0x51/0x80
Aug 14 18:18:06 cardassia kernel: [17289535.116000]  [syscall_call+7/11] syscall_call+0x7/0xb
Aug 14 18:18:06 cardassia kernel: [17289535.116000]  [bad_page+135/192] bad_page+0x87/0xc0
Aug 14 18:18:06 cardassia kernel: [17289535.116000]  [free_hot_cold_page+76/320] free_hot_cold_page+0x4c/0x140
Aug 14 18:18:06 cardassia kernel: [17289535.116000]  [zap_pte_range+600/784] zap_pte_range+0x258/0x310
Aug 14 18:18:06 cardassia kernel: [17289535.116000]  [unmap_page_range+246/304] unmap_page_range+0xf6/0x130 
```

As you can see there are hundreds of messages per second. After half a minute the system must have crashed, there are no more messages logged:

```
Aug 14 18:18:36 cardassia kernel: [17289566.664000]  [zap_pte_range+600/784] zap_pte_range+0x258/0x310
Aug 14 18:18:36 cardassia kernel: [17289566.664000]  [unmap_page_range+246/304] unmap_page_range+0xf6/0x130
Aug 14 18:18:36 cardassia kernel: [17289566.664000]  [unmap_vmas+208/592] unmap_vmas+0xd0/0x250
Aug 14 18:18:36 cardassia kernel: [17289566.664000]  [unmap_region+178/352] unmap_region+0xb2/0x160
Aug 14 18:18:36 cardassia kernel: [17289566.664000]  [do_munmap+265/336] do_munmap+0x109/0x150
Aug 14 18:18:36 cardassia kernel: [17289566.664000]  [sys_munmap+81/128] sys_munmap+0x51/0x80
Aug 14 18:18:36 cardassia kernel: [17289566.664000]  [syscall_call+7/11] syscall_call+0x7/0xb
Aug 14 18:18:36 cardassia kernel: [17289566.664000]  [bad_page+135/192] bad_page+0x87/0xc0
Aug 14 18:18:36 cardassia kernel: [17289566.664000]  [free_hot_cold_page+76/320] free_hot_cold_page+0x4c/0x140
Aug 14 18:18:36 cardassia kernel: [17289566.664000]  [zap_pte_range+600/784] zap_pte_range+0x258/0x310
Aug 14 18:18:36 cardassia kernel: [17289566.664000]  [unmap_page_range+246/304] unmap_page_range+0xf6/0x130
Aug 14 18:18:36 cardassia kernel: [17289566.664000]  [unmap_vmas+208/592] unmap_vmas+0xd0/0x250
Aug 14 18:18:36 cardassia kernel: [17289566.664000]  [unmap_region+178/352] unmap_region+0xb2/0x160
Aug 14 18:18:36 cardassia kernel: [17289566.668000]  [do_munmap+265/336] do_munmap+0x109/0x150
Aug 14 18:18:36 cardassia kernel: [17289566.668000]  [sys_munmap+81/128] sys_munmap+0x51/0x80
Aug 14 18:18:36 cardassia kernel: [17289566.668000]  [syscall_call+7/11] syscall_call+0x7/0xb
Aug 15 09:55:10 cardassia syslogd 1.4.1#17ubuntu7.1: restart.

```

The only similar problems I found so far are caused by some ATI driver, but this system has a Nvidia card, so that can't be it.

---

