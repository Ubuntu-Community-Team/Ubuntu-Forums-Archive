---
title: "'IP6 addrconf timed out or failed'"
date: 2014-01-23
forum: General Help
---

### Post by cybercity@localhost on 2014-01-23
```

Jan 23 09:33:59 cybercity ntpd[1705]: new interface(s) found: waking up resolver
Jan 23 09:34:17 cybercity pppd[3239]: CCP: timeout sending Config-Requests
Jan 23 09:34:32 cybercity kernel: [  261.035554] nouveau E[     DRM] cal_space: -16
Jan 23 09:34:41 cybercity pptp[3250]: nm-pptp-service-3234 log[logecho:pptp_ctrl.c:677]: Echo Reply received.
[COLOR=#ff0000][B]Jan 23 09:49:50 cybercity NetworkManager[1064]: <info> (eth0): IP6 addrconf timed out or failed.
Jan 23 09:49:50 cybercity NetworkManager[1064]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Jan 23 09:49:50 cybercity NetworkManager[1064]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Jan 23 09:49:50 cybercity NetworkManager[1064]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
[/B][/COLOR][COLOR=#ff8c00][B]Jan 23 09:35:23 cybercity kernel: [  312.288017] EXT4-fs (sdb1): error count: 1
Jan 23 09:35:23 cybercity kernel: [  312.288027] EXT4-fs (sdb1): initial error at 1390047125: __ext4_get_inode_loc:3677: inode 19009063: block 76022018[/B]
**Jan 23 09:35:23 cybercity kernel: [  312.288034] EXT4-fs (sdb1): last error at 1390047125: __ext4_get_inode_loc:3677: inode 19009063: block 76022018**[/COLOR]

```
i have no idea why this error is being logged but i think it causes a high communication delay between server and clients..

EDIT:- I have recently attached new 2 TB hard drive in my computer. and my isp doesn't run ipv6 service but ubuntu tries to retrieve the ipv6 connection information, is it possible that it could be the reason of high delay?

---

