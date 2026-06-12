---
title: "If on Windows CMD is &quot;net view&quot; how bout on Ubuntu?"
date: 2008-01-21
forum: General Help
---

### Post by xdefconx on 2008-01-21
Hye all! I would like to know how by using terminal we can check/show any PC/machine in same network/workgroup/rig/etc. For example on Windows platform when we using shell/CMD we can use this command "net view" to list all of available connected PC on LAN . So by using terminal in Ubuntu how we can do that?

Thanxs

---

### Post by banewman on 2008-01-21
netstat -tup 
will show all connections for your user
sudo netstat -tup
will show all connections
man netstat 
will give you the manual for the command netstat
Hope this helps :)

---

### Post by sgla1 on 2008-01-21
```
nmap -sP network/netmask
```

---

### Post by xdefconx on 2008-01-21
Thanxs for fast reply on this thread. Actually what i want is to view any available PC under my workgroup. For example let set on Windows Shell Command by using this command :

**net view**

We will get this output which a list of PC/Machine under a same network/workgroup.

```

C:\Documents and Settings\xkarimx>net view
Server Name            Remark

---------------------------------------------------------------------
\\ACER-2
\\ACER-2ECE1C0C08
\\ACER-38
\\ACER-D-01
\\ACER-D-04
\\ACER-D-17
\\ACER-D36
\\CN                   CN
\\DEVA
\\EGN_FAIRUZ           EGN Fairuz
\\FREDO
\\IGOR
\\ISAA
\\JOHANNB              WSL
\\MAIL                 MAILServer
\\MCRUDY
\\PC172659062206
\\USER39

```

Therefor i would like to know it is possible using terminal i can get this result? 

Thanxs

---

### Post by disturbed1 on 2008-01-21
Try smbtree to display possible samba workgroups/machine names, which looks like what is posted above.

> 
WORKGROUP
        \\JEWELS         
\\JEWELS1
\\JEWELS2
\\DISTURBED
\\DISTURBED1
\\DISTURBED2
\\DISTURBED3

HOME
        \\RICKY          
                \\RICKY\C$              Default share
                \\RICKY\ADMIN$          Remote Admin
                \\RICKY\IPC$            Remote IPC

\\KITCHEN KITCHEN server (Samba, Ubuntu)
\\KITCHEN\print$ Printer Drivers
\\KITCHEN\Share Shared
\\KITCHEN\IPC$ IPC Service (KITCHEN server (Samba, Ubuntu))

\\NAS                           NAS server (Samba, Ubuntu)
                \\NAS\print$            Printer Drivers
                \\NAS\NAS               Music and Movies
                \\NAS\IPC$              IPC Service (NAS server (Samba, Ubuntu))

\\VOD VOD server (Samba, Debian)
\\VOD\Pub Movies
\\VOD\Inc Incoming
\\VOD\IPC$ IPC Service (VOD server (Samba, Debian))


---

### Post by xdefconx on 2008-01-22
> **disturbed1 said:**
> Try smbtree to display possible samba workgroups/machine names, which looks like what is posted above.

Yes! That's what i mean. Thanxs **disturbed1**. Ok now i can see all of PC on that network so how by using terminal i can get others LAN IP? Let say on Windows i just ping that PC name so i will get a LAN IP. So how's on terminal?

Thanxs

---

### Post by disturbed1 on 2008-01-22
You can do the same in Linux. For example -

> 
$ ping NAS
PING NAS (192.168.1.25) 56(84) bytes of data.
64 bytes from NAS (192.168.1.25): icmp_seq=1 ttl=64 time=0.100 ms
64 bytes from NAS (192.168.1.25): icmp_seq=2 ttl=64 time=0.100 ms
64 bytes from NAS (192.168.1.25): icmp_seq=3 ttl=64 time=0.083 ms
64 bytes from NAS (192.168.1.25): icmp_seq=4 ttl=64 time=0.086 ms


The ping command is the same in Linux as in Windows. Trace route in Linux is tracepath or tracepath6 (for IPv6). Ipconfig = ifconfig.

---

### Post by xdefconx on 2008-01-25
> **disturbed1 said:**
> You can do the same in Linux. For example -



The ping command is the same in Linux as in Windows. Trace route in Linux is tracepath or tracepath6 (for IPv6). Ipconfig = ifconfig.

Hye! Thanxs again for ur posting. I already follow ur step but why i got a wrong LAN IP although i got a reply. For example **webxsukma** running on WinXP using this IP: **192.168.1.3**

But i got this:

```

xkarimx@xkarimx-ubuntu:~$ ping webxsukma
PING webxsukma (203.106.203.238) 56(84) bytes of data.
64 bytes from 203.106.203.238: icmp_seq=1 ttl=56 time=17.7 ms
64 bytes from 203.106.203.238: icmp_seq=2 ttl=56 time=14.9 ms
64 bytes from 203.106.203.238: icmp_seq=3 ttl=56 time=17.3 ms
64 bytes from 203.106.203.238: icmp_seq=4 ttl=56 time=17.7 ms
64 bytes from 203.106.203.238: icmp_seq=5 ttl=56 time=16.0 ms
64 bytes from 203.106.203.238: icmp_seq=6 ttl=56 time=14.4 ms

--- webxsukma ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 25192ms
rtt min/avg/max/mdev = 14.429/16.371/17.730/1.317 ms

```

So that's mean my LAN IP is 203.106.203.238?

Thanxs

---

