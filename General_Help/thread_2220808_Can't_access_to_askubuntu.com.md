---
title: "Can't access to askubuntu.com"
date: 2014-04-29
forum: General Help
---

### Post by Ashfaqur Rahman on 2014-04-29
I can't access to askubuntu.com . Actually no stack exchange sites. Tried with both firefox and chromium. Same result!
Any suggestion will be appreciated.

Distribution: Ubuntu 14.04
Thanks!

---

### Post by Warren Hill on 2014-04-29
Do all other sites work OK?

I'm assuming you can get to this site OK or you wouldn't have been able to post: unless you are using a different computer.

Does [http://198.252.206.24](http://198.252.206.24) get you to a stack exchange site with a panda on it?

Just trying to establish whether the problem might be DNS related or something blocking traffic.

---

### Post by Ashfaqur Rahman on 2014-04-29
All others sites work OK!
No, can't access to this IP too.

---

### Post by Warren Hill on 2014-04-29
As the IP address doesn't work it looks probable that something is blocking traffic and DNS is not the problem.

To check open a terminal and enter

```
ping -c5 198.252.206.24
```

I see this

```
warren@dell:~$ ping -c5 198.252.206.24
PING 198.252.206.24 (198.252.206.24) 56(84) bytes of data.
64 bytes from 198.252.206.24: icmp_req=1 ttl=51 time=109 ms
64 bytes from 198.252.206.24: icmp_req=2 ttl=51 time=110 ms
64 bytes from 198.252.206.24: icmp_req=3 ttl=51 time=113 ms
64 bytes from 198.252.206.24: icmp_req=4 ttl=51 time=110 ms
64 bytes from 198.252.206.24: icmp_req=5 ttl=51 time=127 ms

--- 198.252.206.24 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4006ms
rtt min/avg/max/mdev = 109.479/114.403/127.923/6.918 ms
warren@dell:~$ 

```

Post what you get.  It may give someone a clue

---

### Post by Ashfaqur Rahman on 2014-04-29
```

~$ ping -c5 198.252.206.24

```

Result:

```

PING 198.252.206.24 (198.252.206.24) 56(84) bytes of data.

--- 198.252.206.24 ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 3999ms

```

:(

---

### Post by pfeiffep on 2014-04-29
since other sites seem to work - is it possible that your ISP is blocking?

---

