---
title: "Cisco VPN Client + Ubuntu ="
date: 2005-04-10
forum: General Help
---

### Post by joshmachine on 2005-04-10
I was wondering if anyone could help me out here.

Scenario:
Cisco VPNClient 4.6
Ubuntu Hoary w/ stock kernel and headers

I have no problem compiling installing and loading the cisco_ipsec module.  when I try to use the client to connect It fails with the message "disconnected by the client"   I did a tail on /var/log/messages and got some output that I'm not savvy enough to interpret.

Note that the badness doesn't instart until I invoke the client.

Apr 10 20:57:55 localhost kernel: Cisco Systems VPN Client Version 4.6.00 (0045) kernel module loaded
Apr 10 20:58:08 localhost kernel: Badness in local_bh_enable at kernel/softirq.c:140
Apr 10 20:58:08 localhost kernel:  [local_bh_enable+130/132] local_bh_enable+0x82/0x84
Apr 10 20:58:08 localhost kernel:  [pg0+990113549/1069941760] handle_vpnup+0x9d/0x1e0 [cisco_ipsec]
Apr 10 20:58:08 localhost kernel:  [pg0+990112956/1069941760] interceptor_ioctl+0x15c/0x160 [cisco_ipsec]
Apr 10 20:58:08 localhost kernel:  [dev_ifsioc+874/980] dev_ifsioc+0x36a/0x3d4
Apr 10 20:58:08 localhost kernel:  [dev_ioctl+417/730] dev_ioctl+0x1a1/0x2da
Apr 10 20:58:08 localhost kernel:  [sock_ioctl+558/573] sock_ioctl+0x22e/0x23d
Apr 10 20:58:08 localhost kernel:  [sys_ioctl+217/542] sys_ioctl+0xd9/0x21e
Apr 10 20:58:08 localhost kernel:  [sysenter_past_esp+82/117] sysenter_past_esp+0x52/0x75
Apr 10 20:58:08 localhost kernel: Badness in local_bh_enable at kernel/softirq.c:140
Apr 10 20:58:08 localhost kernel:  [local_bh_enable+130/132] local_bh_enable+0x82/0x84
Apr 10 20:58:08 localhost kernel:  [dev_remove_pack+15/23] dev_remove_pack+0xf/0x17
Apr 10 20:58:08 localhost kernel:  [pg0+990113636/1069941760] handle_vpnup+0xf4/0x1e0 [cisco_ipsec]
Apr 10 20:58:08 localhost kernel:  [pg0+990112956/1069941760] interceptor_ioctl+0x15c/0x160 [cisco_ipsec]
Apr 10 20:58:08 localhost kernel:  [dev_ifsioc+874/980] dev_ifsioc+0x36a/0x3d4
Apr 10 20:58:08 localhost kernel:  [dev_ioctl+417/730] dev_ioctl+0x1a1/0x2da
Apr 10 20:58:08 localhost kernel:  [sock_ioctl+558/573] sock_ioctl+0x22e/0x23d
Apr 10 20:58:08 localhost kernel:  [sys_ioctl+217/542] sys_ioctl+0xd9/0x21e
Apr 10 20:58:08 localhost kernel:  [sysenter_past_esp+82/117] sysenter_past_esp+0x52/0x75
Apr 10 20:58:08 localhost kernel:  [schedule+1327/1332] schedule+0x52f/0x534
Apr 10 20:58:08 localhost kernel:  [wait_for_completion+118/202] wait_for_completion+0x76/0xca
Apr 10 20:58:08 localhost kernel:  [default_wake_function+0/18] default_wake_function+0x0/0x12
Apr 10 20:58:08 localhost kernel:  [vprintk+267/357] vprintk+0x10b/0x165
Apr 10 20:58:08 localhost kernel:  [default_wake_function+0/18] default_wake_function+0x0/0x12
Apr 10 20:58:08 localhost kernel:  [__kernel_text_address+46/55] __kernel_text_address+0x2e/0x37
Apr 10 20:58:08 localhost kernel:  [synchronize_kernel+52/63] synchronize_kernel+0x34/0x3f
Apr 10 20:58:08 localhost kernel:  [dump_stack+28/32] dump_stack+0x1c/0x20
Apr 10 20:58:08 localhost kernel:  [wakeme_after_rcu+0/12] wakeme_after_rcu+0x0/0xc
Apr 10 20:58:08 localhost kernel:  [dev_remove_pack+15/23] dev_remove_pack+0xf/0x17
Apr 10 20:58:08 localhost kernel:  [pg0+990113636/1069941760] handle_vpnup+0xf4/0x1e0 [cisco_ipsec]
Apr 10 20:58:08 localhost kernel:  [pg0+990112956/1069941760] interceptor_ioctl+0x15c/0x160 [cisco_ipsec]
Apr 10 20:58:08 localhost kernel:  [dev_ifsioc+874/980] dev_ifsioc+0x36a/0x3d4
Apr 10 20:58:08 localhost kernel:  [dev_ioctl+417/730] dev_ioctl+0x1a1/0x2da
Apr 10 20:58:08 localhost kernel:  [sock_ioctl+558/573] sock_ioctl+0x22e/0x23d
Apr 10 20:58:08 localhost kernel:  [sys_ioctl+217/542] sys_ioctl+0xd9/0x21e
Apr 10 20:58:08 localhost kernel:  [sysenter_past_esp+82/117] sysenter_past_esp+0x52/0x75

My last distro setup was Debian with 2.6.8 custom built kernel.

I have tried building custom kernels (with Ubuntu sources for 2.6.8, 2.6.10, and 2.6.11) and get the same failure.

Does anyone have *any* idea wth is going on?

Cheers

---

### Post by joshmachine on 2005-04-16
No love for us cisco suckers?

---

### Post by dejitarob on 2005-04-20
Version 4.0.4B works great on the 2.6.10 kernel for me. I have gotten this error message before, but fixed it by releasing my IP and receiving a new one.

---

### Post by joshmachine on 2005-04-20
[QUOTE=dejitarob]Version 4.0.4B works great on the 2.6.10 kernel for me. I have gotten this error message before, but fixed it by releasing my IP and receiving a new one.[/QUOTE]
 Yay! Somebody out there answered me.  OK, I'll give 4.0.4B a shot.  Do you use it with a regular ethernet card?  wireless?

Also do you know where i can get my hands on that version?

Thanks dejitarob.

---

