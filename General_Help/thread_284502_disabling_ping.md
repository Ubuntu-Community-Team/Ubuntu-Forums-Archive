---
title: "disabling ping"
date: 2006-10-25
forum: General Help
---

### Post by melbogia on 2006-10-25
hello, I have set these in my sysctl.conf file..

net.ipv4.icmp_echo_ignore_broadcasts = 1
net.ipv4.icmp_echo_ignore_all = 1

and did a "sysctl -p" but I can still ping the machine. Does this require a reboot? If not, why am I still able to ping? How can I disable it? Thanks

-Mel

---

### Post by po0f on 2006-10-25
melbogia,

What happens when you:
```
# echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts
# echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_all
```

[EDIT]

And as long as you have waited for an answer, I'm sure you could have rebooted a couple of times.  ;)

---

### Post by DaveBorealis on 2006-10-25
> **melbogia said:**
> 
net.ipv4.icmp_echo_ignore_broadcasts = 1
net.ipv4.icmp_echo_ignore_all = 1


Are those spaces before and after the '='?  That I believe would be a showstopper.

Here's what I tried in a terminal:
```
$ sudo sysctl -w net.ipv4.icmp_echo_ignore_broadcasts=1
net.ipv4.icmp_echo_ignore_broadcasts = 1
$ sudo sysctl -w net.ipv4.icmp_echo_ignore_all=1
net.ipv4.icmp_echo_ignore_all = 1

```

And it stopped my machine from recieving pings.

Best regards,
Dave

P.S.  Any specific reason for stopping pings via /etc/sysctl.conf rather than using your firewall?  (Just curious.)

---

### Post by melbogia on 2006-10-25
Thanks for the reply, I will get a firewall soon or maybe configure iptables myself. Just trying to figure out what all system configuration files are so I know whats going on where..

---

