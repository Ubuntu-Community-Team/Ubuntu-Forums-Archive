---
title: "Samba not working"
date: 2018-08-25
forum: General Help
---

### Post by sniper8752 on 2018-08-25
I am running Ubuntu server 16.04.  I've added these iptables rules:

```
iptables -A INPUT -i eth0 -s 10.1.1.0/24 -p udp --dport 137:138 -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -A OUTPUT -o eth0 -d 10.1.1.0/24 -p udp --sport 137:138 -m state --state ESTABLISHED -j ACCEPT
iptables -A INPUT -i eth0 -s 10.1.1.0/24 -p tcp --dport 139 -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -A OUTPUT -o eth0 -d 10.1.1.0/24 -p tcp --sport 139 -m state --state ESTABLISHED -j ACCEPT
```

The services, smbd.service and nmbd.service are running.

Running this on my samba server:
```
smbclient -L //10.1.1.5/share -U bob
```
Returns ```
Connection to 10.1.1.5 failed (Error NT_STATUS_IO_TIMEOUT)
```

nmap only returns 139 open.

Edit:
I notice in the log file these errors:
```
  Packet send failed to 10.1.1.255(138) ERRNO=Operation not permitted[2018/08/25 09:10:44.639080,  0] ../source3/libsmb/nmblib.c:873(send_udp)
  Packet send failed to 10.1.1.255(137) ERRNO=Operation not permitted
[2018/08/25 09:10:44.639155,  0] ../source3/nmbd/nmbd_packets.c:179(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 10.1.1.255 port 137 failed

```

---

### Post by SeijiSensei on 2018-08-25
Remove the "STATE" parameters and try again.  Any better?

I assume this is a local network.  Do you have such untrustworthy hosts on your network that you need a firewall just for local file sharing?

If this host is on the public Internet, most observers believe SMB is way too insecure to be exposed to public view.  SSHFS is a much better protocol for remote file access than SMB.

---

### Post by sniper8752 on 2018-09-07
Done; but still does not work.
I forgot a rule:
-A INPUT -s 10.1.1.0/24 -i eth0 -p tcp -m tcp --dport 445 -j ACCEPT

Edit:
Some possibly helpful output?:
```
sudo smbstatus

Samba version 4.3.11-Ubuntu
PID     Username      Group         Machine            Protocol Version
------------------------------------------------------------------------------


Service      pid     machine       Connected at
-------------------------------------------------------


No locked files



```
I was trying to list active smb shares... so I'm wondering if it's not a iptables rule issue?

---

### Post by sniper8752 on 2018-09-14
*bump*

---

