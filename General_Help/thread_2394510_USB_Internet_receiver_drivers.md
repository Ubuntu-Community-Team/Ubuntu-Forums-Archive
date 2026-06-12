---
title: "USB Internet receiver drivers?"
date: 2018-06-17
forum: General Help
---

### Post by nutik on 2018-06-17
Hi! Sorry for being new to Linux. This old 2011 Gateway I've had has been acting very odd with Windows, recently, so I decided instead to use Linux. I previously had a USB Internet receiver (Only to increase download/upload speed, from 0.06 MB/s, same modem connection). I've looked around a bit and noticed the common command "lsusb" with similar issues, however what I had hasn't matched up with other forum posts.

[I]chase@chase-DX4860:~$ lsusb
Bus 002 Device 004: ID 046d:c534 Logitech, Inc. Unifying Receiver
Bus 002 Device 003: ID 0a48:4001 I/O Interconnect 
Bus 002 Device 005: ID 0846:9053 NetGear, Inc. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 03f0:0036 Hewlett-Packard 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/I]

I am currently using Ubuntu 18.04 (Bionic Beaver).

If there is any more information needed, just let me know. Thanks! :)

---

### Post by mörgæs on 2018-06-18
Hi, the ID of your device is 

> **nutik said:**
> 
```
chase@chase-DX4860:~$ lsusb
Bus 002 Device 004: ID 046d:c534 Logitech, Inc. Unifying Receiver
Bus 002 Device 003: ID 0a48:4001 I/O Interconnect 
Bus 002 Device 005: ID **0846:9053** NetGear, Inc. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 03f0:0036 Hewlett-Packard 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```


Googling indicates that it should be possible, for example according to this thread:
[https://ubuntuforums.org/showthread.php?t=2365574](https://ubuntuforums.org/showthread.php?t=2365574)

However, since you are 
> **nutik said:**
> 
currently using Ubuntu 18.04 (Bionic Beaver)

which could have better hardware support than what was the case in the thread mentioned above (17.04) I don't suggest that you follow the advice therein. 

Better to ask a moderator to move your thread to the networking forum where competent people might find it.

---

