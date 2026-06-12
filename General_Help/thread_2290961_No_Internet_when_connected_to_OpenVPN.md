---
title: "No Internet when connected to OpenVPN"
date: 2015-08-16
forum: General Help
---

### Post by lee48 on 2015-08-16
I've followed every bit of info that I could find on the web but still can't route my client thru the vpn tunnel to the internet. It's not a firewall issue since I can ping the vpn server. And I turned off all firewalls just to be sure. It just doesn't work. I've been testing it on my LAN using a laptop (ethernet, not wi-fi) for a client and a desktop for the server (ethernet) with a Linksys router in between. If anyone wants to see my setup info I'll be more than happy to provide it. Ubuntu 14.04 64 bit, OpenVPN 2.3.2 x86_64-pc-linux-gnu [SSL (OpenSSL)] [LZO] [EPOLL] [PKCS11] [eurephia] [MH] [IPv6] built on Dec  1 2014.

---

### Post by CharlesA on 2015-08-16
> **lee48 said:**
> I've followed every bit of info that I could find on the web but still can't route my client thru the vpn tunnel to the internet. It's not a firewall issue since I can ping the vpn server. And I turned off all firewalls just to be sure. It just doesn't work. I've been testing it on my LAN using a laptop (ethernet, not wi-fi) for a client and a desktop for the server (ethernet) with a Linksys router in between. If anyone wants to see my setup info I'll be more than happy to provide it. Ubuntu 14.04 64 bit, OpenVPN 2.3.2 x86_64-pc-linux-gnu [SSL (OpenSSL)] [LZO] [EPOLL] [PKCS11] [eurephia] [MH] [IPv6] built on Dec  1 2014.

What type of VPN server are you trying to connect to? Sounds like it is a problem with the server's routing, assuming you are getting a 10.x.y.z IP address after you connect to the VPN.

---

### Post by lee48 on 2015-08-16
> **CharlesA said:**
> What type of VPN server are you trying to connect to? Sounds like it is a problem with the server's routing, assuming you are getting a 10.x.y.z IP address after you connect to the VPN.

OpenVPN. OpenVPN 2.3.2 x86_64-pc-linux-gnu [SSL (OpenSSL)] [LZO] [EPOLL] [PKCS11] [eurephia] [MH] [IPv6] built on Dec  1 2014

---

### Post by CharlesA on 2015-08-16
Right... how did you install OpenVPN?

Also: I have moved your posts to a new thread since it didn't seem to relate to the existing solved one.

---

### Post by lee48 on 2015-08-16
> **CharlesA said:**
> Right... how did you install OpenVPN?

Not sure of what you're asking.

---

### Post by CharlesA on 2015-08-17
> **lee48 said:**
> Not sure of what you're asking.

What do you mean? Are you connecting to an OpenVPN server you own or through a third party's server?

This sounds like a server-side problem.

---

