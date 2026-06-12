---
title: "CIFS+Linksys=slow"
date: 2008-01-15
forum: General Help
---

### Post by cdenley on 2008-01-15
I have an odd problem with my gutsy machine reading files from a gutsy server. I'm using a Linksys Gigabit network adapter (EG1032). When I mount a samba share as CIFS, it is incredibly slow. If I switch to the onboard 100Mbps NIC, the problem goes away. I've seen similar problems posted, but haven't found a solution. How can I change the speed of my NIC to help troubleshoot? "ifconfig eth1 media 100BaseT" doesn't work.

```

cdenley@client:~$ sudo ethtool eth1
Settings for eth1:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 1000Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000033 (51)
        Link detected: yes
cdenley@client:~$ sudo ethtool eth2
Settings for eth2:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: umbg
        Wake-on: g
        Current message level: 0x00000007 (7)
        Link detected: yes
cdenley@client:~$ sudo mount -t cifs //ubuntu/cdenley /media/cdenley -o domain=MYDOMAIN,user=cdenley
Password:
cdenley@client:~$ sudo ifconfig eth2 down
cdenley@client:~$ date && cp /media/cdenley/openbsd42.iso ./ && date
Tue Jan 15 16:02:17 CST 2008
Tue Jan 15 16:05:11 CST 2008
cdenley@client:~$ sudo ifconfig eth1 down
cdenley@client:~$ sudo ifconfig eth2 up
cdenley@client:~$ date && cp /media/cdenley/openbsd42.iso ./ && date
Tue Jan 15 16:05:48 CST 2008
Tue Jan 15 16:05:52 CST 2008

```

It doesn't seem to be a network, server, or samba problem. I have a windows computer with identical hardware. Windows copied the file in about 5 seconds. I created a bridge on my Ubuntu system with 2 identical gigabit nic's. When windows goes through the bridge on my ubuntu computer, it takes about one minute to copy the file. When the windows computer uses the same cable/connection that had the problem on my ubuntu compter, it copies the file in under 10 seconds. Any ideas?

---

### Post by cdenley on 2008-01-16
I fixed it by using the Linksys driver. I had to fix some code, compile it, then blacklist the r8169 module, but I'm now transferring files at about 325 Mbps in Linux.

---

### Post by donmiguel on 2008-01-28
hey!

Did you detect a difference between the smbfs and the cifs mounts?

Could you give the instructions or a link to instructions to what you've done exactly? And is there a bug on launchpad already?

Thanks for any help, it will be highly appreciated :)

donmiguel

---

### Post by cdenley on 2008-02-05
If I remember correctly, smbfs was actually a little faster, but not much. I downloaded the source code for the driver online. I made some changes (see attached file below) so it would compile. I compiled and installed it. I blacklisted r8169

```

sudo bash
echo blacklist r8169>/etc/modprobe.d/blacklist-r8169
update-initramfs -u

```

[ATTACH]58823[/ATTACH]

I saw some bugs on launchpad which may be related, but I'm not sure.

---

