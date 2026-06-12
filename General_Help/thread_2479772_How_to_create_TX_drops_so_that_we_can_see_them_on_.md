---
title: "How to create TX drops so that we can see them on ifconfig output"
date: 2022-10-06
forum: General Help
---

### Post by zorrom on 2022-10-06
Hi Team,
   We are testing few negative parameters for our environment and one of them is to simulateTransmission packet drops. We applied traffic loss on one of our interface and we are able to see the packet drops happening on netem


$ tc qdisc add dev ens160 root netem loss 10%
 
We are applying 10% loss to the packets on ens160 interface and the same is show below


 
 $  tc -s disc show dev ens160


qdisc netem 8003: root refcnt 9 limit 1000 loss 10%
Sent 6838594 bytes 20381 pkt (dropped 2306, overlimits 0 requeues 0) 




As per the above output, we can see packets are getting dropped(dropped 2306) on the interface ens160 level. But ifconfing will not report these drops in Tx dropped or errors sections 


 
  $ ifconfig ens160 | grep -i Tx


    ether 00:50:56:b2:ea:23  txqueuelen 1  (Ethernet)
    TX packets 33711318  bytes 11028550746 (11.0 GB)
    TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
Here ifconfig is till showing dropped as "0" even though tranmission drops are happening on the same interface




So please let us know what can we do to simulate packet drops in such a way that we can see those getting updated on ifconfig command.

---

### Post by TheFu on 2022-10-06
ifconfig has been deprecated since 2017 with warnings that was happening starting in 2011. Nobody supports it.  Use the 'ip' command going forward.
[https://wiki.debian.org/NetToolsDeprecation](https://wiki.debian.org/NetToolsDeprecation) which refers to 
[https://dougvitale.wordpress.com/2011/12/21/deprecated-linux-networking-commands-and-their-replacements/](https://dougvitale.wordpress.com/2011/12/21/deprecated-linux-networking-commands-and-their-replacements/)

> Specifically, the deprecated Linux networking commands in question are: arp, ifconfig, iptunnel, iwconfig, nameif, netstat, and route. These programs (except iwconfig) are included in the net-tools package that has been unmaintained for years.
That quote is from 2011.

To create packet drops, we unplug the cable somewhere in the network path.

To see packet issues, use the 'ip -s  link' command, as shown here: [https://www.cyberciti.biz/faq/linux-show-dropped-packets-per-interface-command/](https://www.cyberciti.biz/faq/linux-show-dropped-packets-per-interface-command/)

---

### Post by MAFoElffen on 2022-10-06
You be able to see it better via WireShark... That's what I use for that.

---

