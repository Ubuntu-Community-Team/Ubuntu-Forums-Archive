---
title: "Openswan - tunnel up but no traffic"
date: 2014-08-06
forum: General Help
---

### Post by rollyah on 2014-08-06
i have a tunnel set between my pc and a cisco ASA
the goal is :
- my pc which is natted behind a public ip to access the LAN side of the ASA router. (two ips)
here is my config:

   ```
     type=tunnel
        authby=secret
        left=%defaultroute
        leftid=$MY_public_IP
        leftsubnet=10.0.0.2/32
        right=$ASA_IP
        rightsubnets={192.168.1.153/32 192.168.70.15/32}
        esp=3des-sha1
        keyexchange=ike
        ike=3des-sha1
        salifetime=3600s
        ikelifetime=86400s
        pfs=no
        auto=start
        dpdaction=restart
```



When i execute the following

ipsec auto --down remote_asa


```

000 initiating all conns with alias='remote_asa' 
104 "remote_asa/0x2" #7: STATE_MAIN_I1: initiate
003 "remote_asa/0x2" #7: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-02_n] method set to=106 
003 "remote_asa/0x2" #7: ignoring Vendor ID payload [FRAGMENTATION c0000000]
106 "remote_asa/0x2" #7: STATE_MAIN_I2: sent MI2, expecting MR2
003 "remote_asa/0x2" #7: received Vendor ID payload [Cisco-Unity]
003 "remote_asa/0x2" #7: received Vendor ID payload [XAUTH]
003 "remote_asa/0x2" #7: ignoring unknown Vendor ID payload [754e113a4c933790c1299eedcb]
003 "remote_asa/0x2" #7: ignoring Vendor ID payload [Cisco VPN 3000 Series]
003 "remote_asa/0x2" #7: NAT-Traversal: Result using draft-ietf-ipsec-nat-t-ike-02/03: i am NATed
108 "remote_asa/0x2" #7: STATE_MAIN_I3: sent MI3, expecting MR3
003 "remote_asa/0x2" #7: received Vendor ID payload [Dead Peer Detection]
004 "remote_asa/0x2" #7: STATE_MAIN_I4: ISAKMP SA established {auth=OAKLEY_PRESHARED_KEY cipher=oakley_3des_cbc_192 prf=oakley_sha group=modp1024}
117 "remote_asa/0x1" #8: STATE_QUICK_I1: initiate
117 "remote_asa/0x2" #9: STATE_QUICK_I1: initiate
010 "remote_asa/0x2" #9: STATE_QUICK_I1: retransmission; will wait 20s for response
010 "remote_asa/0x1" #8: STATE_QUICK_I1: retransmission; will wait 20s for response
010 "remote_asa/0x1" #8: STATE_QUICK_I1: retransmission; will wait 40s for response
010 "remote_asa/0x2" #9: STATE_QUICK_I1: retransmission; will wait 40s for response
031 "remote_asa/0x2" #9: max number of retransmissions (2) reached STATE_QUICK_I1
000 "remote_asa/0x2" #9: starting keying attempt 2 of an unlimited number, but releasing whack
031 "remote_asa/0x1" #8: max number of retransmissions (2) reached STATE_QUICK_I1.  No acceptable response to our first Quick Mode message: perhaps peer likes no proposal
000 "remote_asa/0x1" #8: starting keying attempt 2 of an unlimited number, but releasing whack
```


i cannot ping any of the 192.168.* IPs unless the remote LAN pings my left subnet
when they stop, i lose the ability to reach them again.

The remote cisco admin has set the type of tunnel to L2L

Any hint on what is going on ?

---

