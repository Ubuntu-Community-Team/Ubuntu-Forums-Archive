---
title: "Start a process at boot with systemd that needs networking running."
date: 2021-09-13
forum: General Help
---

### Post by drkirkby on 2021-09-13
I'm trying to start a process at boot on a Ubuntu 20.04 system. The process is called "ethminer" and connects to a "mining pool" for mining cryptocurrency. Obviously this needs the network running before it can connect to the pool. So I created a file to start a service with systemd. 

```
[Unit]
Description=Start mining ETH
After=network.target syslog.target NetworkManager.target sshd.target

[Service]
Type=simple
#RestartSec=60s
#Restart=always
ExecStart=/usr/local/bin/ethminer --failover-timeout 10 --farm-recheck 2000 -U -P stratum1+tcp://0x5080cbf66707F973ea1a28Ca842b49608339D8Db.Dell_7920_P2200@eth.2miners.com:2020 stratum1+tcp://0x5080cbf66707F973ea1a28Ca842b49608339D8Db.Dell_7920_P2200@us-eth.2miners.com:2020 stratum1+tcp://0x5080cbf66707F973ea1a28Ca842b49608339D8Db.Dell_7920_P2200@asia-eth.2miners.com:2020 2> /var/log/MEW.log &
ExecStop=/usr/bin/pkill ethminer

[Install]
WantedBy=multi-user.target
```

Notice the two lines 
```
#RestartSec=60s
#Restart=always
```
are commented out. With those lines commented out, the program exits after a reboot, after trying unsuccessfully to connect to a mining pool via the network. 

```
drkirkby@canary:~$ systemctl status mineETH
&#9679; mineETH.service - Start mining ETH
     Loaded: loaded (/etc/systemd/system/mineETH.service; enabled; vendor preset: enabled)
     Active: failed (Result: signal) since Mon 2021-09-13 19:20:23 BST; 52s ago
    Process: 1622 ExecStart=/usr/local/bin/ethminer --failover-timeout 10 --farm-recheck 2000 -U -P>
   Main PID: 1622 (code=killed, signal=ABRT)

Sep 13 19:20:22 canary ethminer[1622]:  i 19:20:22 ethminer No connection. Suspend mining ...
Sep 13 19:20:22 canary ethminer[1622]:  i 19:20:22 ethminer Selected pool asia-eth.2miners.com:2020
Sep 13 19:20:22 canary ethminer[1622]:  X 19:20:22 ethminer Could not resolve host asia-eth.2miners>
Sep 13 19:20:22 canary ethminer[1622]:  i 19:20:22 ethminer Disconnected from asia-eth.2miners.com:>
Sep 13 19:20:22 canary ethminer[1622]:  i 19:20:22 ethminer No connection. Suspend mining ...
Sep 13 19:20:22 canary ethminer[1622]:  i 19:20:22 ethminer Selected pool :0
Sep 13 19:20:22 canary ethminer[1622]: terminate called after throwing an instance of 'boost::excep>
Sep 13 19:20:22 canary ethminer[1622]:   what():  Invalid argument
Sep 13 19:20:23 canary systemd[1]: mineETH.service: Main process exited, code=killed, status=6/ABRT
Sep 13 19:20:23 canary systemd[1]: mineETH.service: Failed with result 'signal'.
lines 1-16/16 (END)
```
The software is configured to attempt to connect to 3 mining pools - one  in Europe, another in the USA and finally one is Asia. It attempts all  3. The output above shows it failing to connect to Asia, but it would  have already tried one in Europe and another in the USA, so I assume this must be a few tens of  seconds before the program finally gives up, having tried 3 different pools. 

I would have thought the line
```
After=network.target
```
would have been enough to get the program to wait for the networking to start, then operate correctly, but that does not appear to be the case. I tried adding a few more requirements - syslog.target NetworkManager.target and sshd.target, but they did not help. 

A hack to get the program running properly is to force the program to restart if it exits, by removing comments from two lines.  
```
RestartSec=60s
Restart=always
```
This causes the program to restart if it fails to run. Given the nature of the program, having it restart if it exits is a good ideas, but I can't understand why it will not work properly without having a restart. 

Looking on the web, at a URL I can't' seem to find now, I see someone else with the exact same issue. Someone suggested a real horrible hack, waiting in a loop until Google could be pinged, so the **ExecStart **line was most bizarre. 

I would have thought this a fairly easy task, to get a program to start with the network working properly, but that does not seem to be the case. The computer is on a router which will give it an IP address via DHCP, which might take some time, but I don't believe that can explain why the program gives up after trying 3 mining pools on 3 different continents.

---

### Post by &amp;KyT$0P# on 2021-09-13
Have you tried something involving [FONT=Courier New]network-online.target[/FONT] ?  Refer to [FONT=Courier New]man systemd.special[/FONT] for more info

---

### Post by drkirkby on 2021-09-13
> **halogen2 said:**
> Have you tried something involving [FONT=Courier New]network-online.target[/FONT] ?  Refer to [FONT=Courier New]man systemd.special[/FONT] for more info
I had not prior to seeing your post. Unfortunately it did not help, either having it in the **After **or **Wants **lines. However, the man page you referred me to, and the link to a website in that, did get me there eventually. 

First I tried this without success
```
[Unit]
After=network.target
Wants=network-online.target

```
However, reading the link given in the man page 
[https://www.freedesktop.org/wiki/Software/systemd/NetworkTarget/](https://www.freedesktop.org/wiki/Software/systemd/NetworkTarget/)
and the mention of 
```
NetworkManager-wait-online.service

```I tried the following in the [Unit] section of the file. 
```
[Unit]
Description=Start mining ETH
After=network.target 
Wants=network.target network-online.target NetworkManager-wait-online.service
```
But that did not work. Eventually I found this did. 
```
After=network.target network-online.target NetworkManager-wait-online.service
Wants=network.target network-online.target NetworkManager-wait-online.service
```

So the complete contents of the file, now **not **running as root is. 

```
[Unit]
Description=Start mining ETH
After=network.target network-online.target NetworkManager-wait-online.service
Wants=network.target network-online.target NetworkManager-wait-online.service

[Service]
Type=simple
User=drkirkby
Group=drkirkby
#RestartSec=60s
#Restart=always
ExecStart=/usr/local/bin/ethminer --failover-timeout 10 --farm-recheck 2000 -U -P stratum1+tcp://0x5080cbf66707F973ea1a28Ca842b49608339D8Db.Dell_7920_P2200@eth.2miners.com:2020 stratum1+tcp://0x5080cbf66707F973ea1a28Ca842b49608339D8Db.Dell_7920_P2200@us-eth.2miners.com:2020 stratum1+tcp://0x5080cbf66707F973ea1a28Ca842b49608339D8Db.Dell_7920_P2200@asia-eth.2miners.com:2020 2> /var/log/MEW.log &
ExecStop=/usr/bin/pkill ethminer

[Install]
WantedBy=multi-user.target
```

I will go back and ensure the process will restart if it dies. I should go back, and check if the lines in the [Unit] section of the file are slowing the boot process. If so, I might remove them, and let the program fail, then restart. At least I do have a way of starting the process properly. 

Thank you for your help. With the resources you pointed me to, a solution was found.

---

