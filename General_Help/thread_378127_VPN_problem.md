---
title: "VPN problem"
date: 2007-03-06
forum: General Help
---

### Post by FIONEX on 2007-03-06
I connect to the wireless network at my University, and then I log in to the VPN server and a secure connection is established.  Well that's what nm-applet shows me.  If I do "ip tunnel show", I see a line that says something like "default tun0 ...".  But when I try to access any website, I get the university page saying "Please login to the VPN".  Is this a routing/tunneling problem?

---

### Post by ZERO_SHIFT on 2007-03-07
I cant connect to my university VPN how did yuou manage that?

---

### Post by paulyche on 2007-03-07
I suggest vpnc for cisco compliant VPNs. It's in the Repos. I found it much easier than the cisco client your university may give you.

You setup a configuration file in /etc/vpnc along the lines of example.conf

then you can connect to the vpn with
```

sudo vpnc example (or whatever you called your configuration file)

```

you can also enter your vpn details manually if you just type
```
sudo vpnc
```

and disconnect with
```

sudo vpnc-disconnect

```

I think kvpnc is a gui as well.

---

### Post by FIONEX on 2007-03-07
Hey

To start, thank you so much for the reply, it's been a while since anyone has replied to my threads :P.

To get vpnc, go into synaptic package manager and search for 'vpnc'.  Or type 'sudo apt-get install vpnc' in your terminal.

It's funny because I'm at the university right now and I just tried vpnc in the terminal before I read your reply.  And I am on the wireless network typing this post.  Yeah, my university doesn't even give a VPN for linux (ignorant %@*@#*!$).

I got a copy of the routing table that vpnc makes and a copy of the routing table that network-manager-vpnc makes (which doesn't work).  Any idea how I can get the nm-applet to make the proper routing table?  After all, isn't network-manager-vpnc just a plugin that uses vpnc?

```

vpnc routing table:
--------------------------
172.16.32.6 dev eth1  scope link  src 172.16.45.182  mtu 1500 advmss 1460 hoplimit 64
172.16.32.0/20 dev eth1  proto kernel  scope link  src 172.16.45.182 
default dev tun0  scope link

network-manager-vpnc
--------------------------------
172.16.32.6 via 172.16.32.1 dev eth1 
172.16.32.0/20 dev eth1  proto kernel  scope link  src 172.16.45.182 
default dev tun0  scope link 

```

---

### Post by paulyche on 2007-03-08
I'm sorry I have now exhausted my networking knowledge! But may this reply serve as a bump.

Alternatively, you could try posting your question on [linuxquestions.org](linuxquestions.org), I've found that more technical queries get answered quicker there..

---

