---
title: "Website not opening"
date: 2014-05-03
forum: General Help
---

### Post by diptendu-bt19 on 2014-05-03
I have a long time issue with opening India Rail Info on Ubuntu. When I started using Ubuntu with 12.04 LTS, indiarailinfo.com was opening fine. But after few days it was not opening. I then Upgraded it to 12.10, now 13.10.  But the issue failed to resolve. What to do?

---

### Post by bapoumba on 2014-05-03
```
ping indiarailinfo.com 
PING indiarailinfo.com (208.86.251.18) 56(84) bytes of data.
64 bytes from 208.86.251.18: icmp_seq=1 ttl=53 time=129 ms
64 bytes from 208.86.251.18: icmp_seq=2 ttl=53 time=128 ms
64 bytes from 208.86.251.18: icmp_seq=3 ttl=53 time=127 ms
64 bytes from 208.86.251.18: icmp_seq=4 ttl=53 time=128 ms
^C
--- indiarailinfo.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 12139ms
rtt min/avg/max/mdev = 127.796/128.415/129.453/0.723 ms
```
Can you ping it ?

---

### Post by LastDino on 2014-05-03
It was running fine on my Ubuntu 13.10 and is running fine on my 14.04 Xubuntu as well. Are you sure it is not problem with connection or maybe browser?

---

### Post by albert19 on 2014-08-28
The website is pinging with a different ip address. You may need to check your *hosts* file. Please read this on how to edit hosts file in Ubuntu.
[http://www.knotrick.com/edit-hosts-file-windows-xpvista78/](http://www.knotrick.com/edit-hosts-file-windows-xpvista78/)

---

