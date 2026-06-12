---
title: "Ubuntu 14.04 first time hosting problems TS3"
date: 2018-06-23
forum: General Help
---

### Post by michalodzien on 2018-06-23
Hello I am trying to make a ts3 server on my VPS but I can't get it to work. I have created the server and installed ts3 and it says that it is running but I cannot connect to it using my external IP. I have followed this tutorial: [https://www.globo.tech/learning-cent...ver-ubuntu-14/](https://www.globo.tech/learning-cent...ver-ubuntu-14/)
This is my external ip.
Your External IP
88.198.50.201
Port Range
24100 to 24119
Here is my netstats. [https://gyazo.com/e1310ad9a8330c12849501a2c68e47b4](https://gyazo.com/e1310ad9a8330c12849501a2c68e47b4)
Any help is appreciated.

---

### Post by TheFu on 2018-06-23
I ran a scan against that IP.  There are a bunch of open ports (25+) - I'd think this machine had been hacked if I saw all those open ports.  None of them are in the ranges you list.
```
720/tcp   open  unknown
1000/tcp  open  cadlock
1047/tcp  open  neod1
1048/tcp  open  neod2
1049/tcp  open  td-postman
1107/tcp  open  isoipsigport-2
1301/tcp  open  ci3-software-1
1720/tcp  open  h323q931
1801/tcp  open  msmq
1805/tcp  open  enl-name
1839/tcp  open  netopia-vo1
1840/tcp  open  netopia-vo2
2020/tcp  open  xinupageserver
5120/tcp  open  unknown
7920/tcp  open  unknown
9220/tcp  open  unknown
9500/tcp  open  ismserver
10002/tcp open  documentum
18040/tcp open  unknown
19350/tcp open  unknown
20005/tcp open  btx

```
That is NOT the complete list, BTW.

I'd blow this system away and start over, with just ssh open to start.  ssh should only allow a password for the first connection, then a key should be swapped and passwords blocked forever.  Also, I'd block brute force ssh attempts using denyhosts or fail2ban.

All the other stuff that is running is odd to me.

Srsly,  if you didn't open all those services, wipe this server and start over with security from the bottom up.

---

### Post by michalodzien on 2018-06-23
I didn't open these ports and i can start over yes, i would however still like some help with setting up a ts3 server. Do you think you could help me with that via a live chat?

---

### Post by michalodzien on 2018-06-23
I have managed to get it working. close thread

---

### Post by michalodzien on 2018-06-23
How did you check for all those open ports? And what other signs do i look for it my server is hacked?

---

