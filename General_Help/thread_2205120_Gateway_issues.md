---
title: "Gateway issues"
date: 2014-02-12
forum: General Help
---

### Post by rune_pedersen2 on 2014-02-12
Hi.

My linux-computer lost it's connection to the internet after I bought and installed a new router.
I'm having trouble with the gateways, and tried adding a new, resetting, and changing gateways, where nothing has worked so far.
My gateway-connection should be 192.168.1.2, and my local ip is a static 192.168.1.43.
Can anyone help me achieve this? :KS


route -n shows:
> 
[TABLE="width: 100"]
[TR]
[TD]Destination[/TD]
[TD]Gateway[/TD]
[TD]Genmask[/TD]
[TD]Flags[/TD]
[TD]Metric[/TD]
[TD]Ref[/TD]
[TD]Use[/TD]
[TD]Iface[/TD]
[/TR]
[TR]
[TD]0.0.0.0[/TD]
[TD]192.168.1.2[/TD]
[TD]0.0.0.0[/TD]
[TD]UG[/TD]
[TD]0[/TD]
[TD]0[/TD]
[TD]0[/TD]
[TD]eth0[/TD]
[/TR]
[TR]
[TD]169.254.0.0[/TD]
[TD]0.0.0.0[/TD]
[TD]255.255.0.0[/TD]
[TD]U[/TD]
[TD]1000[/TD]
[TD]0[/TD]
[TD]0[/TD]
[TD]eth0[/TD]
[/TR]
[TR]
[TD]192.168.1.0[/TD]
[TD]0.0.0.0[/TD]
[TD]255.255.255.0[/TD]
[TD]U[/TD]
[TD]0[/TD]
[TD]0[/TD]
[TD]0[/TD]
[TD]eth0[/TD]
[/TR]
[TR]
[TD]192.168.1.43[/TD]
[TD]192.168.1.2[/TD]
[TD]255.255.255.255[/TD]
[TD]UGH[/TD]
[TD]0[/TD]
[TD]0[/TD]
[TD]0[/TD]
[TD]eth0[/TD]
[/TR]
[TR]
[TD]192.168.122.0[/TD]
[TD]0.0.0.0[/TD]
[TD]255.255.255.0[/TD]
[TD]U[/TD]
[TD]0[/TD]
[TD]0[/TD]
[TD]0[/TD]
[TD]vibr0[/TD]
[/TR]
[/TABLE]


---

### Post by varunendra on 2014-02-13
Your routing table seems to be fine. Can you ping your router/gateway?

```
ping -c4 192.168.1.2
```

Can you access its web interface using the same IP? ([http://192.168.1.2](http://192.168.1.2))

Also, are you using Network Manager or the /etc/network/interfaces file for the network configuration?

If using Network Manager, please also show us the output of -
```
nm-tool
```

**PS:**
You should use 'Code' tags for posting terminal commands/outputs instead of the 'Quote' tags that you have used above. The code tags can preserve the original formatting and you won't need to do it manually. See the "Using Code Tags" link in my signature below to see a quick HowTo on using code tags.

---

