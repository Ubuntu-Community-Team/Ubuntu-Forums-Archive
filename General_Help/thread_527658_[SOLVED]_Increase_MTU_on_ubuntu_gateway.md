---
title: "[SOLVED] Increase MTU on ubuntu gateway"
date: 2007-08-16
forum: General Help
---

### Post by jedcred on 2007-08-16
I finally set up my box with two interfaces, shorewall for firewall, dhcp3 for dhcp, and bind9 for dns. All the computers behind the gateway work fine on the internets, as does the PS3, but my Xbox 360 complains about a too-small MTU (the minimum it requires is 1384). ifconfig reveals a MTU of 1500 on my statically assigned, internal nic, and a MTU of 576 on the external nic DHCPed by the cable modem. How can I increase the MTU of the second card?  ifconfig is listed below, with private info removed. eth0 is the internal, and eth1 is the external nic.  TIA.

eth0      Link encap:Ethernet  HWaddr 
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr:  Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:113087 errors:0 dropped:0 overruns:0 frame:0
          TX packets:202390 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:8752273 (8.3 MiB)  TX bytes:296721173 (282.9 MiB)
          Interrupt:201

eth1      Link encap:Ethernet  HWaddr 
          inet addr:  Bcast:255.255.255.255  Mask:255.255.240.0
          UP BROADCAST RUNNING MULTICAST  MTU:576  Metric:1
          RX packets:232543 errors:0 dropped:0 overruns:0 frame:0
          TX packets:111571 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:297612853 (283.8 MiB)  TX bytes:8050174 (7.6 MiB)
          Interrupt:169 Base address:0x1000

---

### Post by lloyd_b on 2007-08-16
First off, an experiment.  In a terminal window:
```
sudo ifconfig eth1 mtu 1384
```

Then test and make sure you still have internet access.  Some ISPs drop any packet that exceeds a certain MTU value.  If you are getting that MTU from DHCP, then it may be that your ISP won't allow packets larger than that through their network (though 576 is a *very* low limit to set).

If you have problems getting to web sites after making that change, then you need to give your ISP a call and find out why they have their MTU set so low.

If you *do* still have internet access after making that change, there are a couple of options.  The "correct" way to handle this is to have DHCP set the MTU correctly.  I have no clue how to do this - I *think* it involves setting a "supercede" condition for eth1 in the file "/etc/dhcp3/dhclient.conf", but I'm not really that familiar with DHCP.  The "cheap" way to do this - add the line:
```
ifconfig eth1 mtu 1384
```
into the file "/etc/rc.local" (before the "exit 0" line).  Note: you'll need a sudo in order to edit this file.

Hopefully, somebody more familiar with DHCP will wander by with better instructions on how to do this the "right" way...

Lloyd B.

---

### Post by jedcred on 2007-08-16
Indeed. I did find that option in ifconfig, and it works fine with a set MTU of 1500. Right now I'm trying to figure out how to get dhclient to fix the MTU to my liking.  If anyone knows how to do that, please chime in.

---

### Post by jedcred on 2007-08-16
OK. So there is an option in dhclient.conf called 'option interface-mtu #', which unfortunately seems to go ignored by dhclient.  However, adding this line below 'auto eth1 inet dhcp' in /etc/network/interfaces works fine.

post-up /sbin/ifconfig eth1 mtu 1500

Hopefully this post will show up better in a search for others with the same issue.

---

