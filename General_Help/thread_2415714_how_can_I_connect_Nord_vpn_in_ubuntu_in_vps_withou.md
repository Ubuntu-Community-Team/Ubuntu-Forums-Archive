---
title: "how can I connect Nord vpn in ubuntu in vps without fail?"
date: 2019-03-30
forum: General Help
---

### Post by doshcw on 2019-03-30
when with terminal connected successfully to nordvpn, vps failed and I should reset vps. how can I connect Nord vpn in ubuntu in vps without fail?  please tell me how can I enable vpn support in ubuntu. there is way to to prevent vps from out or fail. some people said there is a way to enable it(vpn) in ubuntu. I just want know that way

---

### Post by TheFu on 2019-03-30
If you are trying to access your remote VPS while it is connected to a VPN, then you'll need to have console access, since when a VPN is brought up, all the routes are modified to force any non-LAN traffic though the VPN.  Think about that for a second.  If you are on a different subnet, turn on the VPN on the remote VPS, any networking over the WAN will be dropped (like ssh).  I don't know if NordVPN allows inbound connections, but if it does, then you'll need to know THAT IP to connect back in if you want to use any IP networking from outside the LAN.

As for running an openvpn client on the Ubuntu you are sitting at, then that is pretty easy, provdied the service gives you correct .ovpn client files with the certs and you know the login credentials.  I do it from a command prompt, so I cannot help if you want to use a GUI.  The simple solution for a client is to install the openvpn package, then run it like this:  
```
$ sudo openvpn /path/to/nordvpn-somewhere.ovpn
```
Replace the /path/to/... part with the path to the .ovpn file they provided ... or one of the versions they provided, since I think Nord has exit VPNs all over the world.  But if you do this on a remote server, any WAN connection to it will drop immediately.  That's sorta the entire point of using a VPN.

If you don't have a full VPS, but only have a container, then I don't think you will have sufficient control over the networking to setup a VPN trivially.

Or did I misunderstand the issue?

Also, would be helpful to know the specific ubuntu release, since networking changed recently. ** lsb_release -a** will provide that data.

---

### Post by doshcw on 2019-03-31
```
$ sudo openvpn /path/to/nordvpn-somewhere.ovpn
```

I used this code but drop immediately
no one know this

> **TheFu said:**
> If you are trying to access your remote VPS while it is connected to a VPN, then you'll need to have console access, since when a VPN is brought up, all the routes are modified to force any non-LAN traffic though the VPN.  Think about that for a second.  If you are on a different subnet, turn on the VPN on the remote VPS, any networking over the WAN will be dropped (like ssh).  I don't know if NordVPN allows inbound connections, but if it does, then you'll need to know THAT IP to connect back in if you want to use any IP networking from outside the LAN.

As for running an openvpn client on the Ubuntu you are sitting at, then that is pretty easy, provdied the service gives you correct .ovpn client files with the certs and you know the login credentials.  I do it from a command prompt, so I cannot help if you want to use a GUI.  The simple solution for a client is to install the openvpn package, then run it like this:  
```
$ sudo openvpn /path/to/nordvpn-somewhere.ovpn
```
Replace the /path/to/... part with the path to the .ovpn file they provided ... or one of the versions they provided, since I think Nord has exit VPNs all over the world.  But if you do this on a remote server, any WAN connection to it will drop immediately.  That's sorta the entire point of using a VPN.

If you don't have a full VPS, but only have a container, then I don't think you will have sufficient control over the networking to setup a VPN trivially.

Or did I misunderstand the issue?

Also, would be helpful to know the specific ubuntu release, since networking changed recently. ** lsb_release -a** will provide that data.

---

### Post by TheFu on 2019-03-31
In English, punctuation is critical.

Also, will you be answering the questions asked?

---

