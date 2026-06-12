---
title: "Help with OpenVPN on Ubuntu Server 15.04"
date: 2015-11-17
forum: General Help
---

### Post by Mirnesc92 on 2015-11-17
Hey guys,

I am trying to install OpenVPN so I can remotely connect to my office from home, I have been following documentation provided [HERE]("https://help.ubuntu.com/community/OpenVPN").


I install OpenVPN on my Windows 10 Laptop and added the following in the config folder located in "C:\Program Files\OpenVPN\config", as specified in the HOWTO but am getting the following error message..

```
Tue Nov 17 15:21:12 2015 TLS Error: TLS handshake failed
Tue Nov 17 15:21:12 2015 SIGUSR1[soft,tls-error] received, process restarting
Tue Nov 17 15:21:12 2015 MANAGEMENT: >STATE:1447791672,RECONNECTING,tls-error,,
Tue Nov 17 15:21:12 2015 Restart pause, 2 second(s)
Tue Nov 17 15:21:14 2015 WARNING: No server certificate verification method has been enabled.  See http://openvpn.net/howto.html#mitm for more info.
Tue Nov 17 15:21:14 2015 Socket Buffers: R=[65536->65536] S=[65536->65536]
Tue Nov 17 15:21:14 2015 UDPv4 link local: [undef]
Tue Nov 17 15:21:14 2015 UDPv4 link remote: [AF_INET]aaa.bbb.ccc.ddd:1194
Tue Nov 17 15:21:14 2015 MANAGEMENT: >STATE:1447791674,WAIT,,,
Tue Nov 17 15:22:14 2015 TLS Error: TLS key negotiation failed to occur within 60 seconds (check your network connectivity)
Tue Nov 17 15:22:14 2015 TLS Error: TLS handshake failed
Tue Nov 17 15:22:14 2015 SIGUSR1[soft,tls-error] received, process restarting
Tue Nov 17 15:22:14 2015 MANAGEMENT: >STATE:1447791734,RECONNECTING,tls-error,,
Tue Nov 17 15:22:14 2015 Restart pause, 2 second(s)
Tue Nov 17 15:22:16 2015 WARNING: No server certificate verification method has been enabled.  See http://openvpn.net/howto.html#mitm for more info.
Tue Nov 17 15:22:16 2015 Socket Buffers: R=[65536->65536] S=[65536->65536]
Tue Nov 17 15:22:16 2015 UDPv4 link local: [undef]
Tue Nov 17 15:22:16 2015 UDPv4 link remote: [AF_INET]aaa.bbb.ccc.ddd:1194
Tue Nov 17 15:22:16 2015 MANAGEMENT: >STATE:1447791736,WAIT,,,
``` 

aaa.bbb.ccc.ddd is my public IP. I only have my public ip set in the client.ovpn, should it be set somewhere else? or is something else causing this issue? Do I need to do anything on my router?

---

