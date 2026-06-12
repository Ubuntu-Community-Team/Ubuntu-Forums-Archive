---
title: "Can't start OpenVPN client- tap0 device doesn't appear in ifconfig"
date: 2013-08-07
forum: General Help
---

### Post by danep on 2013-08-07
I've been struggling for a few days to figure this out, and I'd appreciate any advice.

I'm on Raring, using OpenVPN from repos (2.2.1), trying to connect to an OpenVPN server on an Asus router.

Here's my config (cortex.conf):

```

client
remote cortex.example.com 1194
[ca, cert, etc... don't think this is the problem]
dev tap
proto udp

```

If I try to connect using sudo openvpn --config cortex.conf, authentication succeeds, but then I see...

```

TUN/TAP device tap0 opened
SIOCADDRT: Network is unreachable
ERROR: Linux route add command failed: external program existed with error status: 7

```

If I run ifconfig at this point, tap0 does not exist, even though it was supposedly opened. I can add route-nopull to the config, and this gets rid of the errors, but still tap0 does not seem to be brought up. There are no errors in the OpenVPN server's logs.

Can anyone please help me figure out what's going on here? I'm at my wits' end.

---

### Post by SeijiSensei on 2013-08-08
Have you tried using the tun device instead?  That's the only one I use for OpenVPN, and it has worked flawlessly for years.

---

### Post by danep on 2013-08-08
tun works fine, but I was hoping to use bridging (hence tap) because I want to be able to access other devices on the network (media servers, samba shares, etc).

Maybe I should listen to the advice in the OpenVPN wiki:
> [COLOR=#000000][FONT=Verdana]Bridging looks easier at first glance, but it brings a completely different can of worms. Make no mistake: [/FONT][/COLOR]**There are no shortcuts in making networking easier**[COLOR=#000000][FONT=Verdana]- except learning how to do it properly.
[/FONT][/COLOR] :)

So maybe I should first see if what I want to accomplish is possible in a routing configuration with tun.

---

### Post by SeijiSensei on 2013-08-08
Better to use the "up" directive to run a script that sets up a route between the tunnel and the subnet(s) you need to reach.  I avoid bridging except in very unusual situations like making a VirtualBox VM appear to other machines on the host's network.

---

### Post by danep on 2013-08-09
Thanks for the advice! I was able to get everything working as desired using a TUN connection.

I think I was thrown off because I was following the advice of [this howtogeek article on OpenVPN using Tomato]("http://www.howtogeek.com/60774/connect-to-your-home-network-from-anywhere-with-openvpn-and-tomato/") that recommended using TAP, without any sort of qualification. In retrospect, I think that's pretty bad advice for beginners.

---

