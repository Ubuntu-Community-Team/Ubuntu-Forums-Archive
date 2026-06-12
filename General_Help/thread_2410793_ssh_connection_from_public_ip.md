---
title: "ssh connection from public ip"
date: 2019-01-20
forum: General Help
---

### Post by vernies on 2019-01-20
I am trying to set up a ssh server in home and I don't understand what's wrong.

When I try to ssh with public ip adress, it says operation timed out:
```

$ ssh -v user@10.10.10.10
penSSH_7.8p1, LibreSSL 2.6.2debug1: Reading configuration data /Users/vernies/.ssh/config
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 48: Applying options for *
debug1: Connecting to 10.10.10.10 [10.10.10.10] port 22.
debug1: connect to address 10.10.10.10 port 22: Operation timed out
ssh: connect to host 10.10.10.10 port 22: Operation timed out
```

From the start, I downloaded with:
```
$ sudo apt-get openssh-server
```

Looked up internal address with ifconfig:
```
lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 4845  bytes 408407 (408.4 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 4845  bytes 408407 (408.4 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


wlp2s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.103  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::dc50:4a9:682e:53a1  prefixlen 64  scopeid 0x20<link>
        ether 18:3d:a2:d9:62:78  txqueuelen 1000  (Ethernet)
        RX packets 252529  bytes 349248542 (349.2 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 131359  bytes 14560696 (14.5 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```

In my case 192.168.1.103, then added my router's NAT forwarding-Virtual Servers:
[ATTACH=CONFIG]282252[/ATTACH]


Then allowed port on firewall:
```

$ sudo ufw enable
$ sudo ufw allow ssh
# and
$ sudo ufw allow 22
$ sudo ufw status
Status: active


To                         Action      From
--                         ------      ----
22/tcp                     ALLOW       Anywhere
22                         ALLOW       Anywhere
22/tcp (v6)                ALLOW       Anywhere (v6)
22 (v6)                    ALLOW       Anywhere (v6)

```

Service status:
```

$ sudo service ssh status
&#9679; ssh.service - OpenBSD Secure Shell server   Loaded: loaded (/lib/systemd/system/ssh.service; enabled; vendor preset: enabled)
   Active: active (running) since Mon 2019-01-21 03:05:21 +03; 1min 4s ago
     Docs: man:sshd(8)
           man:sshd_config(5)
  Process: 32365 ExecStartPre=/usr/sbin/sshd -t (code=exited, status=0/SUCCESS)
 Main PID: 32374 (sshd)
    Tasks: 1 (limit: 2050)
   Memory: 2.7M
   CGroup: /system.slice/ssh.service
           &#9492;&#9472;32374 /usr/sbin/sshd -D


Jan 21 03:05:21 lubuntu systemd[1]: Starting OpenBSD Secure Shell server...
Jan 21 03:05:21 lubuntu sshd[32374]: Server listening on 0.0.0.0 port 22.
Jan 21 03:05:21 lubuntu sshd[32374]: Server listening on :: port 22.
Jan 21 03:05:21 lubuntu systemd[1]: Started OpenBSD Secure Shell server.
```

I can ssh with internal adress:
```
$ ssh 192.168.1.103
```

---

### Post by vernies on 2019-01-20
I learned that my ISP is using Carrier-grade NAT, so my WAN IP and Public IP are not the same. I have to buy static IP to port-forward.

This was the problem.

Edit: Yep, now that I bought static IP, I can use it.

---

