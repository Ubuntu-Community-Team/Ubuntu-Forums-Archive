---
title: "L2TP/IPSec not working; pppd dies"
date: 2014-09-24
forum: General Help
---

### Post by yuanzhoulu on 2014-09-24
Trying a pretty standard L2TP/IPSec+PSK setup with Ubuntu 14.04.
Android client is able to connect to said server without issues, but Ubuntu is a no-go. IPSec alone works fine, xl2tpd connects, but pppd seems to not do the final honors. Any advice?

I'm using Werner Jaeger's L2TP IPSec VPN Manager version 1.0.9.

Sep 24 18:42:07 my-hostname L2tpIPsecVpnControlDaemon: Executing command ipsec auto --ready
Sep 24 18:42:07 my-hostname L2tpIPsecVpnControlDaemon: Command ipsec auto --ready finished with exit code 0
Sep 24 18:42:08 my-hostname L2tpIPsecVpnControlDaemon: Executing command ipsec auto --up my-vpn-server.net
Sep 24 18:42:09 my-hostname L2tpIPsecVpnControlDaemon: Command ipsec auto --up my-vpn-server.net finished with exit code 0
Sep 24 18:42:10 my-hostname L2tpIPsecVpnControlDaemon: Closing client connection
Sep 24 18:42:10 my-hostname xl2tpd[12700]: Connecting to host my-vpn-server.net, port 1701
Sep 24 18:42:10 my-hostname xl2tpd[12700]: Connection established to 54.250.126.25, 1701.  Local: 36832, Remote: 30609 (ref=0/0).
Sep 24 18:42:10 my-hostname xl2tpd[12700]: Calling on tunnel 36832
Sep 24 18:42:10 my-hostname xl2tpd[12700]: Call established with 54.250.126.25, Local: 38255, Remote: 23972, Serial: 1 (ref=0/0)
Sep 24 18:42:10 my-hostname xl2tpd[12700]: start_pppd: I'm running: 
Sep 24 18:42:10 my-hostname xl2tpd[12700]: "/usr/sbin/pppd" 
Sep 24 18:42:10 my-hostname xl2tpd[12700]: "passive" 
Sep 24 18:42:10 my-hostname xl2tpd[12700]: "nodetach" 
Sep 24 18:42:10 my-hostname xl2tpd[12700]: ":" 
Sep 24 18:42:10 my-hostname xl2tpd[12700]: "file" 
Sep 24 18:42:10 my-hostname xl2tpd[12700]: "/etc/ppp/my-vpn-server.net.options.xl2tpd" 
Sep 24 18:42:10 my-hostname xl2tpd[12700]: "/dev/pts/12" 
Sep 24 18:42:10 my-hostname pppd[12764]: Plugin passprompt.so loaded.
Sep 24 18:42:10 my-hostname pppd[12764]: pppd 2.4.5 started by root, uid 0
Sep 24 18:42:10 my-hostname pppd[12764]: Using interface ppp0
Sep 24 18:42:10 my-hostname pppd[12764]: Connect: ppp0 <--> /dev/pts/12
Sep 24 18:42:10 my-hostname NetworkManager[1053]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Sep 24 18:42:10 my-hostname NetworkManager[1053]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Sep 24 18:42:10 my-hostname NetworkManager[1053]: <warn> /sys/devices/virtual/net/ppp0: couldn't determine device driver; ignoring...
Sep 24 18:42:14 my-hostname xl2tpd[12700]: control_finish: Connection closed to 54.250.126.25, serial 1 ()
Sep 24 18:42:14 my-hostname xl2tpd[12700]: Terminating pppd: sending TERM signal to pid 12764
Sep 24 18:42:14 my-hostname pppd[12764]: Modem hangup
Sep 24 18:42:14 my-hostname pppd[12764]: Connection terminated.
Sep 24 18:42:14 my-hostname NetworkManager[1053]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Sep 24 18:42:14 my-hostname pppd[12764]: Exit.
Sep 24 18:42:49 my-hostname L2tpIPsecVpnControlDaemon: Opening client connection
Sep 24 18:42:49 my-hostname L2tpIPsecVpnControlDaemon: Executing command service xl2tpd stop
Sep 24 18:42:49 my-hostname xl2tpd[12700]: death_handler: Fatal signal 15 received
Sep 24 18:42:49 my-hostname L2tpIPsecVpnControlDaemon: Command service xl2tpd stop finished with exit code 0
Sep 24 18:42:49 my-hostname L2tpIPsecVpnControlDaemon: Executing command ipsec setup stop
Sep 24 18:42:49 my-hostname ipsec_setup: Stopping Openswan IPsec...
Sep 24 18:42:50 my-hostname kernel: [18232.381511] NET: Unregistered protocol family 15
Sep 24 18:42:50 my-hostname ipsec_setup: ...Openswan IPsec stopped
Sep 24 18:42:50 my-hostname L2tpIPsecVpnControlDaemon: Command ipsec setup stop finished with exit code 0
Sep 24 18:42:50 my-hostname L2tpIPsecVpnControlDaemon: Closing client connection

---

### Post by yuanzhoulu on 2014-09-24
I added a password line to my configuration, enabled debug on pppd and got this, which might be more helpful. Still not sure exactly how I should approach this. Any pointers would be appreciated!

Sep 24 19:01:25 my-hostname L2tpIPsecVpnControlDaemon: Executing command ipsec auto --ready
Sep 24 19:01:25 my-hostname L2tpIPsecVpnControlDaemon: Command ipsec auto --ready finished with exit code 0
Sep 24 19:01:26 my-hostname L2tpIPsecVpnControlDaemon: Executing command ipsec auto --up my-vpn-server
Sep 24 19:01:27 my-hostname L2tpIPsecVpnControlDaemon: Command ipsec auto --up my-vpn-server finished with exit code 0
Sep 24 19:01:28 my-hostname L2tpIPsecVpnControlDaemon: Closing client connection
Sep 24 19:01:28 my-hostname xl2tpd[13892]: Connecting to host my-vpn-server, port 1701
Sep 24 19:01:28 my-hostname xl2tpd[13892]: Connection established to 54.250.126.25, 1701.  Local: 63772, Remote: 29421 (ref=0/0).
Sep 24 19:01:28 my-hostname xl2tpd[13892]: Calling on tunnel 63772
Sep 24 19:01:28 my-hostname xl2tpd[13892]: Call established with 54.250.126.25, Local: 53446, Remote: 22517, Serial: 1 (ref=0/0)
Sep 24 19:01:28 my-hostname xl2tpd[13892]: start_pppd: I'm running: 
Sep 24 19:01:28 my-hostname xl2tpd[13892]: "/usr/sbin/pppd" 
Sep 24 19:01:28 my-hostname xl2tpd[13892]: "passive" 
Sep 24 19:01:28 my-hostname xl2tpd[13892]: "nodetach" 
Sep 24 19:01:28 my-hostname xl2tpd[13892]: ":" 
Sep 24 19:01:28 my-hostname xl2tpd[13892]: "file" 
Sep 24 19:01:28 my-hostname xl2tpd[13892]: "/etc/ppp/my-vpn-server.options.xl2tpd" 
Sep 24 19:01:28 my-hostname xl2tpd[13892]: "/dev/pts/16" 
Sep 24 19:01:28 my-hostname pppd[13950]: Plugin passprompt.so loaded.
Sep 24 19:01:28 my-hostname pppd[13950]: pppd options in effect:
Sep 24 19:01:28 my-hostname pppd[13950]: debug#011#011# (from /etc/ppp/my-vpn-server.options.xl2tpd)
Sep 24 19:01:28 my-hostname pppd[13950]: nodetach#011#011# (from command line)
Sep 24 19:01:28 my-hostname pppd[13950]: idle 72000#011#011# (from /etc/ppp/my-vpn-server.options.xl2tpd)
Sep 24 19:01:28 my-hostname pppd[13950]: ktune#011#011# (from /etc/ppp/my-vpn-server.options.xl2tpd)
Sep 24 19:01:28 my-hostname pppd[13950]: dump#011#011# (from /etc/ppp/my-vpn-server.options.xl2tpd)
Sep 24 19:01:28 my-hostname pppd[13950]: plugin passprompt.so#011#011# (from /etc/ppp/my-vpn-server.options.xl2tpd)
Sep 24 19:01:28 my-hostname pppd[13950]: noauth#011#011# (from /etc/ppp/my-vpn-server.options.xl2tpd)
Sep 24 19:01:28 my-hostname pppd[13950]: refuse-eap#011#011# (from /etc/ppp/my-vpn-server.options.xl2tpd)
Sep 24 19:01:28 my-hostname pppd[13950]: name beigua#011#011# (from /etc/ppp/my-vpn-server.options.xl2tpd)
Sep 24 19:01:28 my-hostname pppd[13950]: password ??????#011#011# (from /etc/ppp/my-vpn-server.options.xl2tpd)
Sep 24 19:01:28 my-hostname pppd[13950]: remotename #011#011# (from /etc/ppp/my-vpn-server.options.xl2tpd)
Sep 24 19:01:28 my-hostname pppd[13950]: promptprog /usr/bin/L2tpIPsecVpn#011#011# (from /etc/ppp/my-vpn-server.options.xl2tpd)
Sep 24 19:01:28 my-hostname pppd[13950]: /dev/pts/16#011#011# (from command line)
Sep 24 19:01:28 my-hostname pppd[13950]: lock#011#011# (from /etc/ppp/my-vpn-server.options.xl2tpd)
Sep 24 19:01:28 my-hostname pppd[13950]: record /var/log/pppd#011#011# (from /etc/ppp/my-vpn-server.options.xl2tpd)
Sep 24 19:01:28 my-hostname pppd[13950]: crtscts#011#011# (from /etc/ppp/my-vpn-server.options.xl2tpd)
Sep 24 19:01:28 my-hostname pppd[13950]: modem#011#011# (from /etc/ppp/my-vpn-server.options.xl2tpd)
Sep 24 19:01:28 my-hostname pppd[13950]: asyncmap 0#011#011# (from /etc/ppp/my-vpn-server.options.xl2tpd)
Sep 24 19:01:28 my-hostname pppd[13950]: passive#011#011# (from command line)
Sep 24 19:01:28 my-hostname pppd[13950]: lcp-echo-failure 4#011#011# (from /etc/ppp/options)
Sep 24 19:01:28 my-hostname pppd[13950]: lcp-echo-interval 30#011#011# (from /etc/ppp/options)
Sep 24 19:01:28 my-hostname pppd[13950]: hide-password#011#011# (from /etc/ppp/my-vpn-server.options.xl2tpd)
Sep 24 19:01:28 my-hostname pppd[13950]: ipcp-accept-local#011#011# (from /etc/ppp/my-vpn-server.options.xl2tpd)
Sep 24 19:01:28 my-hostname pppd[13950]: ipcp-accept-remote#011#011# (from /etc/ppp/my-vpn-server.options.xl2tpd)
Sep 24 19:01:28 my-hostname pppd[13950]: ipparam L2tpIPsecVpn-my-vpn-server#011#011# (from /etc/ppp/my-vpn-server.options.xl2tpd)
Sep 24 19:01:28 my-hostname pppd[13950]: noproxyarp#011#011# (from /etc/ppp/my-vpn-server.options.xl2tpd)
Sep 24 19:01:28 my-hostname pppd[13950]: :#011#011# (from command line)
Sep 24 19:01:28 my-hostname pppd[13950]: noipx#011#011# (from /etc/ppp/my-vpn-server.options.xl2tpd)
Sep 24 19:01:28 my-hostname pppd[13950]: pppd 2.4.5 started by root, uid 0
Sep 24 19:01:28 my-hostname pppd[13950]: using channel 16
Sep 24 19:01:28 my-hostname pppd[13950]: Using interface ppp0
Sep 24 19:01:28 my-hostname pppd[13950]: Connect: ppp0 <--> /dev/pts/18
Sep 24 19:01:28 my-hostname pppd[13950]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xfa6eb181> <pcomp> <accomp>]
Sep 24 19:01:28 my-hostname NetworkManager[1053]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Sep 24 19:01:28 my-hostname NetworkManager[1053]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Sep 24 19:01:28 my-hostname NetworkManager[1053]: <warn> /sys/devices/virtual/net/ppp0: couldn't determine device driver; ignoring...
Sep 24 19:01:28 my-hostname pppd[13950]: rcvd [LCP ConfReq id=0x1 <mru 1280> <asyncmap 0x0> <auth chap MD5> <magic 0xace6ea3a> <pcomp> <accomp>]
Sep 24 19:01:28 my-hostname pppd[13950]: sent [LCP ConfAck id=0x1 <mru 1280> <asyncmap 0x0> <auth chap MD5> <magic 0xace6ea3a> <pcomp> <accomp>]
Sep 24 19:01:28 my-hostname pppd[13950]: rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0xfa6eb181> <pcomp> <accomp>]
Sep 24 19:01:28 my-hostname pppd[13950]: sent [LCP EchoReq id=0x0 magic=0xfa6eb181]
Sep 24 19:01:29 my-hostname pppd[13950]: rcvd [LCP EchoRep id=0x0 magic=0xace6ea3a]
Sep 24 19:01:29 my-hostname pppd[13950]: rcvd [LCP EchoReq id=0x0 magic=0xace6ea3a]
Sep 24 19:01:29 my-hostname pppd[13950]: sent [LCP EchoRep id=0x0 magic=0xfa6eb181]
Sep 24 19:01:29 my-hostname pppd[13950]: rcvd [CHAP Challenge id=0x97 <c67e9c1e652113643be27a7f3b423f21ebd15df6695bff>, name = "l2tpd"]
Sep 24 19:01:29 my-hostname pppd[13950]: sent [CHAP Response id=0x97 <9637e7c94ff5338c091fe4f402d4500c>, name = "beigua"]
Sep 24 19:01:29 my-hostname pppd[13950]: rcvd [CHAP Success id=0x97 "Access granted"]
Sep 24 19:01:29 my-hostname pppd[13950]: CHAP authentication succeeded: Access granted
Sep 24 19:01:29 my-hostname pppd[13950]: CHAP authentication succeeded
Sep 24 19:01:29 my-hostname pppd[13950]: sent [CCP ConfReq id=0x1 <deflate 15> <deflate(old#) 15> <bsd v1 15>]
Sep 24 19:01:29 my-hostname pppd[13950]: sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0>]
Sep 24 19:01:29 my-hostname pppd[13950]: rcvd [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 192.168.42.1>]
Sep 24 19:01:29 my-hostname pppd[13950]: sent [IPCP ConfAck id=0x1 <compress VJ 0f 01> <addr 192.168.42.1>]
Sep 24 19:01:29 my-hostname pppd[13950]: rcvd [LCP ProtRej id=0x2 80 fd 01 01 00 0f 1a 04 78 00 18 04 78 00 15 03 2f]
Sep 24 19:01:29 my-hostname pppd[13950]: Protocol-Reject for 'Compression Control Protocol' (0x80fd) received
Sep 24 19:01:29 my-hostname pppd[13950]: rcvd [IPCP ConfNak id=0x1 <addr 192.168.42.10>]
Sep 24 19:01:29 my-hostname pppd[13950]: sent [IPCP ConfReq id=0x2 <compress VJ 0f 01> <addr 192.168.42.10>]
Sep 24 19:01:29 my-hostname pppd[13950]: rcvd [IPCP ConfAck id=0x2 <compress VJ 0f 01> <addr 192.168.42.10>]
Sep 24 19:01:29 my-hostname pppd[13950]: local  IP address 192.168.42.10
Sep 24 19:01:29 my-hostname pppd[13950]: remote IP address 192.168.42.1
Sep 24 19:01:29 my-hostname acvpnagent[1951]: A new network interface has been detected.
Sep 24 19:01:29 my-hostname acvpnagent[1951]: Function: logInterfaces File: ../../vpn/AgentUtilities/Routing/InterfaceRouteMonitorCommon.cpp Line: 477 IP Address Interface List: 18.62.13.176 18.62.13.175 192.168.42.10 FE80:0:0:0:2AD2:44FF:FEC4:9917 FE80:0:0:0:2AB2:BDFF:FE80:BBBE 
Sep 24 19:01:29 my-hostname acvpnagent[1951]: Function: netInterfaceNoticeCategoryHandler File: ../../vpn/Agent/MainThread.cpp Line: 7388 Network Interface change detected, refreshing physical MAC addresses
Sep 24 19:01:29 my-hostname pppd[13950]: Script /etc/ppp/ip-up started (pid 13961)
Sep 24 19:01:29 my-hostname pppd[13950]: Script /etc/ppp/ip-up finished (pid 13961), status = 0x0
Sep 24 19:01:29 my-hostname whoopsie[1222]: message repeated 4 times: [ online]
Sep 24 19:01:49 my-hostname whoopsie[1222]: offline
Sep 24 19:02:15 my-hostname L2tpIPsecVpnControlDaemon: Opening client connection
Sep 24 19:02:15 my-hostname L2tpIPsecVpnControlDaemon: Executing command service xl2tpd stop
Sep 24 19:02:15 my-hostname xl2tpd[13892]: death_handler: Fatal signal 15 received
Sep 24 19:02:15 my-hostname L2tpIPsecVpnControlDaemon: Command service xl2tpd stop finished with exit code 0
Sep 24 19:02:15 my-hostname L2tpIPsecVpnControlDaemon: Executing command ipsec setup stop
Sep 24 19:02:15 my-hostname pppd[13950]: Script pppd (charshunt) finished (pid 13951), status = 0x0
Sep 24 19:02:15 my-hostname pppd[13950]: Modem hangup
Sep 24 19:02:15 my-hostname pppd[13950]: Connect time 0.8 minutes.
Sep 24 19:02:15 my-hostname pppd[13950]: Sent 39605 bytes, received 0 bytes.
Sep 24 19:02:15 my-hostname pppd[13950]: Script /etc/ppp/ip-down started (pid 14013)
Sep 24 19:02:15 my-hostname pppd[13950]: Connection terminated.
Sep 24 19:02:15 my-hostname acvpnagent[1951]: A network interface has gone down.
Sep 24 19:02:15 my-hostname acvpnagent[1951]: Function: logInterfaces File: ../../vpn/AgentUtilities/Routing/InterfaceRouteMonitorCommon.cpp Line: 477 IP Address Interface List: 18.62.13.176 18.62.13.175 FE80:0:0:0:2AD2:44FF:FEC4:9917 FE80:0:0:0:2AB2:BDFF:FE80:BBBE 
Sep 24 19:02:15 my-hostname acvpnagent[1951]: Function: netInterfaceNoticeCategoryHandler File: ../../vpn/Agent/MainThread.cpp Line: 7388 Network Interface change detected, refreshing physical MAC addresses
Sep 24 19:02:10 my-hostname whoopsie[1222]: offline
Sep 24 19:02:15 my-hostname whoopsie[1222]: online
Sep 24 19:02:15 my-hostname NetworkManager[1053]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Sep 24 19:02:15 my-hostname ipsec_setup: Stopping Openswan IPsec...
Sep 24 19:02:15 my-hostname pppd[13950]: Script /etc/ppp/ip-down finished (pid 14013), status = 0x0
Sep 24 19:02:15 my-hostname pppd[13950]: Exit.
Sep 24 19:02:16 my-hostname kernel: [19399.203726] NET: Unregistered protocol family 15
Sep 24 19:02:16 my-hostname ipsec_setup: ...Openswan IPsec stopped
Sep 24 19:02:16 my-hostname L2tpIPsecVpnControlDaemon: Command ipsec setup stop finished with exit code 0
Sep 24 19:02:16 my-hostname L2tpIPsecVpnControlDaemon: Closing client connection

---

