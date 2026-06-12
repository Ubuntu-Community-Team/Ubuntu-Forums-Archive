---
title: "Help investigate slow boot time after 24.10 upgrade"
date: 2024-10-13
forum: General Help
---

### Post by salty-horse on 2024-10-13
I upgraded from 24.04 to 24.10 and 2 minutes were added to the boot time.

This is what I see in dmesg:
```
[   13.746230] e1000e 0000:00:1f.6 eno1: NIC Link is Up 1000 Mbps Full Duplex, Flow Control: None
[  130.189559] kauditd_printk_skb: 203 callbacks suppressed
[  130.189562] audit: type=1400 audit(1728839659.646:215): apparmor="STATUS" operation="profile_load" profile="unconfined" name="docker-default" pid=2189 comm="apparmor_parser"
```

I'm trying to print the suppressed messages, which is supposedly controlled by the message_cost and message_burst system variables.
I created this file, and rebooted, but the messages are still suppressed.
```
$ cat /etc/sysctl.d/60-messages.conf 
net.core.message_cost=0
net.core.message_burst=0
```

Any idea how to force them to appear, or any other avenues I should investigate to find what's causing the boot delay?

---

### Post by salty-horse on 2024-10-14
Scanning syslog, this message appeared 1.5 minutes after the previous one:

```
 systemd-networkd-wait-online[1641]: Timeout occurred while waiting for network connectivity.
```

Following these steps helped (not sure which was the culprit)
[LIST]
[*][Disabled systemd-networkd.service]("https://askubuntu.com/a/1501504") 
[*][Manually executed the nm-online -s -q command in NetworkManager-wait-online.service]("https://askubuntu.com/a/1513188") (probably did nothing?)
[/LIST]

---

