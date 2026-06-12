---
title: "OpenVPN Client Does Not Stay Connected"
date: 2016-07-04
forum: General Help
---

### Post by tweezer on 2016-07-04
Hello!

I'm somewhat new with Ubuntu, and now running Ubuntu 16.05 LTS.  I have installed OpenVPN client to connect to my home network.  I have installed  network-manager-openvpn-gnome, and successfully imported my ovpn configuration.

The server is a Netgear R8000 router.  OpenVPN clients running on windows connect without issue.

When I try to connect from Ubuntu, I get the error message "*The VPN login failed because the VPN program received an invalid configuration from the VPN server*".

My syslog looks like this:
```
Jul  4 13:31:46 mysystem NetworkManager[755]: <info>  [1467613906.4370] audit: op="connection-activate" uuid="01b949ab-7940-4f73-b892-f4ae807eb88d" name="client2" pid=1977 uid=1000 result="success"
Jul  4 13:31:46 mysystem NetworkManager[755]: <info>  [1467613906.4439] vpn-connection[0xad05e0,01b949ab-7940-4f73-b892-f4ae807eb88d,"client2",0]: Started the VPN service, PID 4472
Jul  4 13:31:46 mysystem NetworkManager[755]: <info>  [1467613906.4526] vpn-connection[0xad05e0,01b949ab-7940-4f73-b892-f4ae807eb88d,"client2",0]: Saw the service appear; activating connection
Jul  4 13:31:46 mysystem NetworkManager[755]: nm-openvpn-Message: openvpn[4476] started
Jul  4 13:31:46 mysystem NetworkManager[755]: <info>  [1467613906.4631] vpn-connection[0xad05e0,01b949ab-7940-4f73-b892-f4ae807eb88d,"client2",0]: VPN plugin: state changed: starting (3)
Jul  4 13:31:46 mysystem NetworkManager[755]: <info>  [1467613906.4634] vpn-connection[0xad05e0,01b949ab-7940-4f73-b892-f4ae807eb88d,"client2",0]: VPN connection: (ConnectInteractive) reply received
Jul  4 13:31:46 mysystem nm-openvpn[4476]: OpenVPN 2.3.11 x86_64-pc-linux-gnu [SSL (OpenSSL)] [LZO] [EPOLL] [PKCS11] [MH] [IPv6] built on May 10 2016
Jul  4 13:31:46 mysystem nm-openvpn[4476]: library versions: OpenSSL 1.0.2g-fips  1 Mar 2016, LZO 2.08
Jul  4 13:31:46 mysystem nm-openvpn[4476]: WARNING: No server certificate verification method has been enabled.  See http://openvpn.net/howto.html#mitm for more info.
Jul  4 13:31:46 mysystem nm-openvpn[4476]: NOTE: the current --script-security setting may allow this configuration to call user-defined scripts
Jul  4 13:31:46 mysystem nm-openvpn[4476]: WARNING: file '/etc/openvpn/client.key' is group or others accessible
Jul  4 13:31:46 mysystem nm-openvpn[4476]: NOTE: chroot will be delayed because of --client, --pull, or --up-delay
Jul  4 13:31:46 mysystem nm-openvpn[4476]: NOTE: UID/GID downgrade will be delayed because of --client, --pull, or --up-delay
Jul  4 13:31:46 mysystem nm-openvpn[4476]: UDPv4 link local: [undef]
Jul  4 13:31:46 mysystem nm-openvpn[4476]: UDPv4 link remote: [AF_INET]11.222.33.444:12222
Jul  4 13:31:46 mysystem nm-openvpn[4476]: WARNING: 'dev-type' is used inconsistently, local='dev-type tun', remote='dev-type tap'
Jul  4 13:31:46 mysystem nm-openvpn[4476]: WARNING: 'link-mtu' is used inconsistently, local='link-mtu 1558', remote='link-mtu 1590'
Jul  4 13:31:46 mysystem nm-openvpn[4476]: WARNING: 'tun-mtu' is used inconsistently, local='tun-mtu 1500', remote='tun-mtu 1532'
Jul  4 13:31:46 mysystem nm-openvpn[4476]: [netgear] Peer Connection Initiated with [AF_INET]11.222.33.444:12222
Jul  4 13:31:48 mysystem ovpn-client[1041]: RESOLVE: Cannot resolve host address: my-server-1: Name or service not known
Jul  4 13:31:58 mysystem ovpn-client[1041]: message repeated 2 times: [ RESOLVE: Cannot resolve host address: my-server-1: Name or service not known]
Jul  4 13:31:59 mysystem nm-openvpn[4476]: TUN/TAP device tun0 opened
Jul  4 13:31:59 mysystem nm-openvpn[4476]: /usr/lib/NetworkManager/nm-openvpn-service-openvpn-helper --bus-name org.freedesktop.NetworkManager.openvpn.Connection_4 --tun -- tun0 1500 1558   init
Jul  4 13:31:59 mysystem NetworkManager[755]: <info>  [1467613919.5843] manager: (tun0): new Tun device (/org/freedesktop/NetworkManager/Devices/6)
Jul  4 13:31:59 mysystem NetworkManager[755]: <info>  [1467613919.6054] devices added (path: /sys/devices/virtual/net/tun0, iface: tun0)
Jul  4 13:31:59 mysystem NetworkManager[755]: <info>  [1467613919.6061] device added (path: /sys/devices/virtual/net/tun0, iface: tun0): no ifupdown configuration found.
Jul  4 13:31:59 mysystem NetworkManager[755]: <info>  [1467613919.6126] vpn-connection[0xad05e0,01b949ab-7940-4f73-b892-f4ae807eb88d,"client2",0]: VPN connection: (IP Config Get) reply received.
Jul  4 13:31:59 mysystem NetworkManager[755]: <info>  [1467613919.6143] vpn-connection[0xad05e0,01b949ab-7940-4f73-b892-f4ae807eb88d,"client2",7:(tun0)]: VPN connection: (IP4 Config Get) reply received
Jul  4 13:31:59 mysystem NetworkManager[755]: <warn>  [1467613919.6153] vpn-connection[0xad05e0,01b949ab-7940-4f73-b892-f4ae807eb88d,"client2",7:(tun0)]: invalid IP4 config received!
Jul  4 13:31:59 mysystem NetworkManager[755]: <warn>  [1467613919.6163] vpn-connection[0xad05e0,01b949ab-7940-4f73-b892-f4ae807eb88d,"client2",7:(tun0)]: VPN connection: did not receive valid IP config information
Jul  4 13:31:59 mysystem NetworkManager[755]: <info>  [1467613919.6197] vpn-connection[0xad05e0,01b949ab-7940-4f73-b892-f4ae807eb88d,"client2",0]: VPN plugin: state changed: started (4)
Jul  4 13:31:59 mysystem nm-openvpn[4476]: chroot to '/var/lib/openvpn/chroot' and cd to '/' succeeded
Jul  4 13:31:59 mysystem nm-openvpn[4476]: GID set to nm-openvpn
Jul  4 13:31:59 mysystem nm-openvpn[4476]: UID set to nm-openvpn
Jul  4 13:31:59 mysystem nm-openvpn[4476]: Initialization Sequence Completed
Jul  4 13:31:59 mysystem nm-openvpn[4476]: write to TUN/TAP : Invalid argument (code=22)
Jul  4 13:31:59 mysystem nm-openvpn[4476]: message repeated 6 times: [ write to TUN/TAP : Invalid argument (code=22)]
Jul  4 13:31:59 mysystem NetworkManager[755]: nm-openvpn-Message: openvpn[4476]: send SIGTERM
Jul  4 13:31:59 mysystem nm-openvpn[4476]: write to TUN/TAP : Invalid argument (code=22)
Jul  4 13:31:59 mysystem nm-openvpn[4476]: write to TUN/TAP : Invalid argument (code=22)
Jul  4 13:31:59 mysystem NetworkManager[755]: <info>  [1467613919.6257] vpn-connection[0xad05e0,01b949ab-7940-4f73-b892-f4ae807eb88d,"client2",0]: VPN plugin: state changed: stopping (5)
Jul  4 13:31:59 mysystem nm-openvpn[4476]: write to TUN/TAP : Invalid argument (code=22)
Jul  4 13:31:59 mysystem NetworkManager[755]: <info>  [1467613919.6257] vpn-connection[0xad05e0,01b949ab-7940-4f73-b892-f4ae807eb88d,"client2",0]: VPN plugin: state changed: stopped (6)
Jul  4 13:31:59 mysystem nm-openvpn[4476]: write to TUN/TAP : Invalid argument (code=22)
Jul  4 13:31:59 mysystem nm-openvpn[4476]: message repeated 21 times: [ write to TUN/TAP : Invalid argument (code=22)]
Jul  4 13:31:59 mysystem NetworkManager[755]: <info>  [1467613919.6332] devices removed (path: /sys/devices/virtual/net/tun0, iface: tun0)
Jul  4 13:31:59 mysystem nm-openvpn[4476]: write to TUN/TAP : Invalid argument (code=22)
Jul  4 13:31:59 mysystem nm-openvpn[4476]: message repeated 7 times: [ write to TUN/TAP : Invalid argument (code=22)]
Jul  4 13:31:59 mysystem nm-openvpn[4476]: SIGTERM[hard,] received, process exiting
Jul  4 13:31:59 mysystem NetworkManager[755]: nm-openvpn-Message: openvpn[4476] exited with success
Jul  4 13:32:03 mysystem ovpn-client[1041]: RESOLVE: Cannot resolve host address: my-server-1: Name or service not known
Jul  4 13:33:18 mysystem ovpn-client[1041]: message repeated 15 times: [ RESOLVE: Cannot resolve host address: my-server-1: Name or service not known]
Jul  4 13:33:22 mysystem ovpn-client2[1033]: Extracted DHCP router address: 192.168.1.2
Jul  4 13:33:23 mysystem ovpn-client[1041]: RESOLVE: Cannot resolve host address: my-server-1: Name or service not known
Jul  4 13:33:26 mysystem ovpn-client2[1033]: Extracted DHCP router address: 192.168.1.2
Jul  4 13:33:28 mysystem ovpn-client[1041]: RESOLVE: Cannot resolve host address: my-server-1: Name or service not known
Jul  4 13:33:48 mysystem ovpn-client[1041]: message repeated 4 times: [ RESOLVE: Cannot resolve host address: my-server-1: Name or service not known]
Jul  4 13:33:48 mysystem ovpn-client2[1033]: Extracted DHCP router address: 192.168.1.2
Jul  4 13:33:53 mysystem ovpn-client[1041]: RESOLVE: Cannot resolve host address: my-server-1: Name or service not known
```

On the VPN Server, (the router), the logs show:
"OpenVPN, connection successfully", and the one minute later, "OpenVPN, connection drop".

Can anyone shed any light on what is happening here and how I might address it?

Thanks in advance for any advice!
T.

---

