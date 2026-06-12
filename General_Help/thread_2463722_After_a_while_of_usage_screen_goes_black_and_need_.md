---
title: "After a while of usage screen goes black and need to force restart"
date: 2021-06-17
forum: General Help
---

### Post by zacklife on 2021-06-17
Hi,

I installed Ubuntu 20.04 last week and ever since I have been dealing with my screen randomly going black and having to do a force restart each time. Every time I check the logs at /var/log/syslog this is what I find:

```
Jun 17 09:54:26 X550VX systemd-resolved[13917]: Negative trust anchors: 10.in-addr.arpa 16.172.in-addr.arpa 17.172.in-addr.arpa 18.172.in-addr.arpa 19.172.in-addr.arpa 20.172.in-addr.arpa 21.172.in-addr.arpa 22.172.in-addr.arpa 23.172.in-addr.arpa 24.172.in-addr.arpa 25.172.in-addr.arpa 26.172.in-addr.arpa 27.172.in-addr.arpa 28.172.in-addr.arpa 29.172.in-addr.arpa 30.172.in-addr.arpa 31.172.in-addr.arpa 168.192.in-addr.arpa d.f.ip6.arpa corp home internal intranet lan local private testJun 17 09:54:26 X550VX systemd-resolved[13917]: Using system hostname 'X550VX'.
Jun 17 09:54:26 X550VX systemd[1]: Started Network Name Resolution.
Jun 17 09:54:26 X550VX systemd-resolved[13917]: Flushed all caches.
Jun 17 09:54:31 X550VX systemd-resolved[13917]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
```

I did some research and found that these errors are harmless so I'm confused why they are always the last logs before my system crashes. 

I'm not sure if it's relevant, but I have an NVIDIA graphics card (GTX 950M), and the driver being used is nvidia-driver-460.

Any help would be greatly appreciated as I've been unable to find a solution for this. I have to do 4-5 force restarts everyday, so you can imagine the frustration :(!

---

### Post by zacklife on 2021-06-17
It seems to have just crashed again, these were my error logs. Any input would be appreciated it.

```
Jun 17 10:05:37 X550VX wpa_supplicant[798]: nl80211: send_and_recv->nl_recvmsgs failed: -33Jun 17 10:07:37 X550VX wpa_supplicant[798]: message repeated 2 times: [ nl80211: send_and_recv->nl_recvmsgs failed: -33]
Jun 17 10:09:01 X550VX CRON[5321]: (root) CMD (  [ -x /usr/lib/php/sessionclean ] && if [ ! -d /run/systemd/system ]; then /usr/lib/php/sessionclean; fi)
Jun 17 10:09:07 X550VX systemd[1]: Starting Clean php session files...
Jun 17 10:09:07 X550VX systemd[1]: phpsessionclean.service: Succeeded.
Jun 17 10:09:07 X550VX systemd[1]: Finished Clean php session files.
Jun 17 10:10:07 X550VX wpa_supplicant[798]: nl80211: send_and_recv->nl_recvmsgs failed: -33
Jun 17 10:10:13 X550VX systemd-resolved[673]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Jun 17 10:10:27 X550VX systemd[1]: Starting Cleanup of Temporary Directories...
Jun 17 10:10:27 X550VX systemd[1]: systemd-tmpfiles-clean.service: Succeeded.
Jun 17 10:10:27 X550VX systemd[1]: Finished Cleanup of Temporary Directories.
```

---

