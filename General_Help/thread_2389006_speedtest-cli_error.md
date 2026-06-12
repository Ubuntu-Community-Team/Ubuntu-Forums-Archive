---
title: "speedtest-cli error"
date: 2018-04-10
forum: General Help
---

### Post by ardouronerous on 2018-04-10
I'm running Lubuntu 16.04.

```
speedtest-cli
Retrieving speedtest.net configuration...
Retrieving speedtest.net server list...
Traceback (most recent call last):
  File "/usr/bin/speedtest-cli", line 9, in <module>
    load_entry_point('speedtest-cli==0.3.4', 'console_scripts', 'speedtest-cli')()
  File "/usr/lib/python2.7/dist-packages/speedtest_cli.py", line 790, in main
    speedtest()
  File "/usr/lib/python2.7/dist-packages/speedtest_cli.py", line 641, in speedtest
    servers = closestServers(config['client'])
  File "/usr/lib/python2.7/dist-packages/speedtest_cli.py", line 436, in closestServers
    serversxml.append(uh.read(10240))
  File "/usr/lib/python2.7/socket.py", line 384, in read
    data = self._sock.recv(left)
  File "/usr/lib/python2.7/httplib.py", line 612, in read
    s = self.fp.read(amt)
  File "/usr/lib/python2.7/socket.py", line 384, in read
    data = self._sock.recv(left)
socket.timeout: timed out
```

---

### Post by mc4man on 2018-04-10
While the 16.04 version is old it works fine here. Maybe try raising the timeout (default is 10 sec., 1 sec works here as i've a very good connection

```
speedtest-cli --timeout 30
```
If that also fails try 60
If desired you can install the 2.0 version from 18.04 in 16.04, get here, install the downloaded .deb with apt
[https://packages.ubuntu.com/bionic/speedtest-cli](https://packages.ubuntu.com/bionic/speedtest-cli)

---

### Post by ardouronerous on 2018-04-11
I've re-tired speedtest-cli and it works now.

I must've had lousy internet connection the other day.

Thanks for your help! :)

---

