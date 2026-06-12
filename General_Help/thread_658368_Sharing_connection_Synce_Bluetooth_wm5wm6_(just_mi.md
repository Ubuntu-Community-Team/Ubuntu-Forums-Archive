---
title: "Sharing connection Synce Bluetooth wm5/wm6 (just missing a last step)"
date: 2008-01-04
forum: General Help
---

### Post by zit on 2008-01-04
Lot of days i'm looking for sharing my kubuntu gutsy internet connection through bluetooth to my pda HTC Trinity (p3600) windows mobile 6.

I just success to make work activesync synchronisation  bluetooth between pda and pc.

-  odccm needed

dccm and vdccm doesn't work

- and dun

 dund --listen  --activesync --msdun  call dun

config :
 /etc/ppp/peers/dun

```

nodefaultroute
noauth
local
debug
192.168.1.1:192.168.1.11
ms-dns 192.168.1.1
linkname synce-device

```

log

```
dund[27007]: Bluetooth DUN daemon version 3.23
dund[27022]: New connection from 00:17:83:**:**:**
using channel 101
Using interface ppp0
Connect: ppp0 <--> /dev/rfcomm1
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x84f6de32> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x0 <asyncmap 0x0> <pcomp> <accomp>]
sent [LCP ConfAck id=0x0 <asyncmap 0x0> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x84f6de32> <pcomp> <accomp>]
rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0x84f6de32> <pcomp> <accomp>]
sent [LCP EchoReq id=0x0 magic=0x84f6de32]
sent [CCP ConfReq id=0x1 <deflate 15> <deflate(old#) 15> <bsd v1 15>]
sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 192.168.1.1>]
rcvd [CCP ConfReq id=0x0 <mppe -H -M -S -L -D +C>]
sent [CCP ConfRej id=0x0 <mppe -H -M -S -L -D +C>]
rcvd [IPCP ConfReq id=0x0 <compress VJ 0f 00> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-wins 0.0.0.0> <ms-dns3 0.0.0.0> <ms-wins 0.0.0.0>]
sent [IPCP ConfRej id=0x0 <ms-wins 0.0.0.0> <ms-wins 0.0.0.0>]
rcvd [IPV6CP ConfReq id=0x0 <addr fe80::0218:**ff:**06:**f7>]
Unsupported protocol 'IPv6 Control Protovol' (0x8057) received
sent [LCP ProtRej id=0x2 80 ** 01 00 ** 0e 01 0a ** 18 ** ff ** 06 32 f7]
rcvd [LCP EchoRep id=0x0 magic=0x0]
rcvd [CCP ConfRej id=0x1 <deflate 15> <deflate(old#) 15> <bsd v1 15>]
sent [CCP ConfReq id=0x2]
rcvd [IPCP ConfAck id=0x1 <compress VJ 0f 01> <addr 192.168.1.1>]
rcvd [CCP ConfReq id=0x1]
sent [CCP ConfAck id=0x1]
rcvd [IPCP ConfReq id=0x1 <compress VJ 0f 00> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
sent [IPCP ConfNak id=0x1 <addr 192.168.1.11> <ms-dns1 192.168.1.1> <ms-dns3 192.168.1.1>]
rcvd [CCP ConfNak id=0x2 <mppe -H -M -S -L -D +C>]
sent [CCP ConfReq id=0x3]
rcvd [IPCP ConfReq id=0x2 <compress VJ 0f 00> <addr 192.168.1.11> <ms-dns1 192.168.1.1> <ms-dns3 192.168.1.1>]
sent [IPCP ConfAck id=0x2 <compress VJ 0f 00> <addr 192.168.1.11> <ms-dns1 192.168.1.1> <ms-dns3 192.168.1.1>]
found interface eth0 for proxy arp
local  IP address 192.168.1.1
remote IP address 192.168.1.11
Script /etc/ppp/ip-up started (pid 27032)
rcvd [CCP ConfAck id=0x3]
Script /etc/ppp/ip-up finished (pid 27032), status = 0x0

```

ifconfig
```
eth0      Lien encap:Ethernet  HWaddr 00:**:**:**:**:DB  
          inet adr:192.168.1.1  Bcast:192.168.1.255  Masque:255.255.255.0
          adr inet6: fe80::*0e:a6**:fe**:3db/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:2350902 erreurs:0 :0 overruns:0 frame:0
          TX packets:3305484 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:329480642 (314.2 MB) Octets transmis:2971301749 (2.7 GB)
          Interruption:16 Adresse de base:0xa000 

eth1      Lien encap:Ethernet  HWaddr 00:**:**:**:**:8D  
          inet adr:192.168.0.1  Bcast:192.168.0.255  Masque:255.255.255.0
          adr inet6: fe80::20e:****f:fe**:738d/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 b) Octets transmis:1512 (1.4 KB)
          Interruption:19 

lo        Lien encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:157142 erreurs:0 :0 overruns:0 frame:0
          TX packets:157142 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:9564182 (9.1 MB) Octets transmis:9564182 (9.1 MB)

ppp0      Lien encap:Protocole Point-à-Point  
          inet adr:192.168.1.1  P-t-P:192.168.1.11  Masque:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          Packets reçus:29 erreurs:0 :0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:3 
          Octets reçus:2085 (2.0 KB) Octets transmis:670 (670.0 b)

```


So on pda activesync say connected. 
Command like pls & pstatus ok 
Explorer with synce:/// and rapip:// ok (just rapip display bad the files another story... )
Not yet test multisync....

ping pda from pc ok.
ping  pc and all my lan interfaces from pda ok. 
On pda with the freeware pocket ping 1.6 ping website like google.com works. And of course all website don't work in pocket internet explorer.
I already checked dns, iptable, ppp0 config but nothing

Is it dun problem? because when i make not a activesync server but a simple dialup network service (dund --listen --dialup call dun) pda internet also don't work.
Last 2 lines of dun log :
rcvd [CCP ConfAck id=0x3]
Script /etc/ppp/ip-up finished (pid 27032), status = 0x0


thx in advance

---

### Post by zit on 2008-01-04
Success dun works!!


new config /etc/ppp/peers/dun

```

debug
noauth
local
noipdefault
connect "/etc/ppp/at-cmd.pl -v"
115200
nodefaultroute
192.168.1.1:192.168.1.11
ms-dns 192.168.1.1
persist
linkname synce-device

```


Pocket pc needs AT simulation!
take at-cmd.pl  in [http://wiki.xda-developers.com/uploads/at-cmd.pl](http://wiki.xda-developers.com/uploads/at-cmd.pl) 
put that file in /etc/ppp/
and
```
sudo chmod u+x /etc/ppp/at-cmd.pl
```

So run now :
```
dund --listen --dialup call dun
```

```
Connect your PDA
Start>Settings>Connections>Connections>Add a new modem connection >

- Bluetooth 
- Select Device (pc) 
- dial : enter 0 (random number works)
- user/password/domain blank 
- Finish
- Go pocket internet explorer 
- Dialing 
- Internet ok!!

```

Just this tips works only with a dun (dund --dialup) service, activesync (dund --activesync) don't work simultanous.
I'll try to got dun and activesynce together...

---

