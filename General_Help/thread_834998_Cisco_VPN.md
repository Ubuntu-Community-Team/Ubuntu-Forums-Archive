---
title: "Cisco VPN"
date: 2008-06-20
forum: General Help
---

### Post by PhDP on 2008-06-20
I got trouble making my cisco VPN connection work, it's essential for my studies and I cannot get support for Ubuntu at the university (but it's supposed to work). I tried to get answers on the Network subforum but to no avail so I'll try here. I'm totally ignorant about networks, BTW. 

ifconfig (when I'm not connected to the VPN); 

eth0      Link encap:Ethernet  HWaddr 00:1d:09:58:38:aa  
          inet addr:74.210.236.52  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:9ff:fe58:38aa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:144882 errors:8 dropped:0 overruns:0 frame:0
          TX packets:3249 errors:0 dropped:0 overruns:0 carrier:0
          collisions:95 txqueuelen:1000 
          RX bytes:12039122 (11.4 MB)  TX bytes:417774 (407.9 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1936 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1936 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:96800 (94.5 KB)  TX bytes:96800 (94.5 KB)

ifconfig (after I'm connected); 

cipsec0   Link encap:Ethernet  HWaddr 00:0b:fc:f8:01:8f  
          inet addr:132.203.240.46  Mask:255.255.255.0
          inet6 addr: fe80::20b:fcff:fef8:18f/64 Scope:Link
          UP RUNNING NOARP  MTU:1356  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:5 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1326 (1.2 KB)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  HWaddr 00:1d:09:58:38:aa  
          inet addr:74.210.236.52  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:9ff:fe58:38aa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:152829 errors:8 dropped:0 overruns:0 frame:0
          TX packets:3351 errors:0 dropped:0 overruns:0 carrier:0
          collisions:95 txqueuelen:1000 
          RX bytes:12557960 (11.9 MB)  TX bytes:428953 (418.8 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1981 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1981 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:109972 (107.3 KB)  TX bytes:109972 (107.3 KB)

However, my IP remain the same and I don't have access to any science journal (and I should). When I type 'router' I get (after connection); 

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
vpn-externe1.ul 74-210-236-1.ri 255.255.255.255 UGH   0      0        0 eth0
132.203.240.0   *               255.255.255.0   U     0      0        0 cipsec0
74.210.236.0    *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
132.203.0.0     poste46-240.vp. 255.255.0.0     UG    0      0        0 cipsec0
10.0.0.0        poste46-240.vp. 255.0.0.0       UG    0      0        0 cipsec0
default         74-210-236-1.ri 0.0.0.0         UG    100    0        0 eth0

And before; 

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
74.210.236.0    *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         74-210-236-1.ri 0.0.0.0         UG    100    0        0 eth0

---

### Post by ilrudie on 2008-06-20
The cisco VPN does not change your IP because that would disconnect you from your local network.  Instead it creates a virtual interface with an ip on the private network.  This appears to be happening just fine but what's not happening is a correct update to the routing tables.  I'm not sure why the VPN set it up incorrectly but your default route looks like it is still going though eth0. You need to know what the default gateway for the private network should be.  I'm not sure if there is a way to find this out other than asking the IT people who run the VPN.  After you know that try the following as root;

```

route del default
route add default gw <yourgatewayinfo> dev cipsec0

```

Replace <yourgatewayinfo> with the ip address of the gateway and you should have a working VPN connection.  This probably won't be permanent and if you can't figure out why the default route is not updated correctly you will probably want to have a little script that does this for you.  If you don't know how to make one let me know and I will help you out.

Good Luck with your VPN and your studies.

---

### Post by PhDP on 2008-06-20
Right now, the #1 problem for my studies is Ubuntu, I really hope I can solve this problem fast, I already lost too much time. Thank you very much for the help, I appreciate it.

What I meant by 'change my IP' (I told you I know little about network) is that, when I go to [www.monip.org](www.monip.org) with the VPN connected and working (with another computer with WinXP), I get a new IP.

OK, here's the sequence of events; 

sudo /etc/init.d/vpnclient_init start
=> Starting /opt/cisco-vpnclient/bin/vpnclient: Done

Then I connect to the VPN... Welcome on the Network, bla bla bla, ...

route 

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
vpn-externe1.ul 74-210-236-1.ri 255.255.255.255 UGH   0      0        0 eth0
132.203.240.0   *               255.255.255.0   U     0      0        0 cipsec0
74.210.236.0    *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
132.203.0.0     poste81-240.vp. 255.255.0.0     UG    0      0        0 cipsec0
10.0.0.0        poste81-240.vp. 255.0.0.0       UG    0      0        0 cipsec0
default         74-210-236-1.ri 0.0.0.0         UG    100    0        0 eth0

sudo su
route del default

route

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
vpn-externe1.ul 74-210-236-1.ri 255.255.255.255 UGH   0      0        0 eth0
132.203.240.0   *               255.255.255.0   U     0      0        0 cipsec0
74.210.236.0    *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
132.203.0.0     poste81-240.vp. 255.255.0.0     UG    0      0        0 cipsec0
10.0.0.0        poste81-240.vp. 255.0.0.0       UG    0      0        0 cipsec0

About the gateway, when I go to [www.monip.org](www.monip.org), I get my ip (74.210.236.52) and 74-210-236-52.ri.cgocable.ca, the gateway is the IP, plain and simple right ? Because I can connect to the VPN with another computer and go to [www.monip.org](www.monip.org) to get these info.

route add default gw <mynewip> dev cipsec0

route

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
vpn-externe1.ul 74-210-236-1.ri 255.255.255.255 UGH   0      0        0 eth0
132.203.240.0   *               255.255.255.0   U     0      0        0 cipsec0
74.210.236.0    *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
132.203.0.0     poste81-240.vp. 255.255.0.0     UG    0      0        0 cipsec0
10.0.0.0        poste81-240.vp. 255.0.0.0       UG    0      0        0 cipsec0
default         poste71-240.vp. 0.0.0.0         UG    0      0        0 cipsec0

And now, internet doesn't work at all, I opened firefox and I cannot even reach my home page (and it's not a problem with FireFox, FileZilla, and all the other programs don't work either, Internet is dead and I need to restart the computer).

---

### Post by ilrudie on 2008-06-20
The gateway is the IP address through which traffic traveling to another network must pass.  The gateway shouldn't be the same as your IP.  With the default route the gateway is used for anything that doesn't have another route specified.  You won't be able to use any tools or websites that I know of to determine your VPN gateway because your computer doesn't know what it is.  If you can get VPN working in another OS you could find the gateway in that OS and try using it for your default route.  Otherwise the people who admin your VPN should be able to tell you that information if you ask nicely.  They may want you to explain why you need it because normally this should be configured automagically by the VPN client.  I have found that most admins will be helpful if you explain that you are using Linux and they are not too busy when you ask.  Some of them may even enjoy Linux at home and might be interested in you figuring out the VPN so they can use it at home.  This has been my experience but your mileage may vary.

Hope that helps.

---

### Post by PhDP on 2008-06-20
I'm able to make it work in another OS and I got; 132.203.240.71. Is it possible or the gateway should be in a different form ?

Anyway, I tried your method with this and nothing works...

---

### Post by ilrudie on 2008-06-20
Since you have it working in another OS check out the routing tables in your other OS.  For windows I think it is 'route print'  and for OSX a 'netstat -rn' should reveal the correct tables.  You can then use that information to create the correct routing tables in ubuntu.  Also you were correct above in that the IP address for the cipsec0 interface is the gateway for the default route.  This is because cipsec0 is actually inward facing and is acting as a virtual gateway (also encrypting your traffic).

Anyways once you know the correct routing information you need to delete all the routes you have once the VPN connects and then add the correct routes in.  This should get you up and running.

Also when adding your routes make sure to pay attention to what the VPN said when you connected as far as the client and server addresses.  The client address will be your gateway in the 3rd row.  The server address will be your destination in the first row.  If you can't find it or the VPN didn't print it 'vpnclient stat' should give you the information.

As far as why this is happening im not sure.  Perhaps you have an outdated version of the client installed.  Post the output of 'vpnclient stat' when not connected to the VPN.  It may also be a good idea to uninstall and reinstall the client incase some hook into the OS did not get properly created.

---

### Post by PhDP on 2008-06-20
I'll go back to WinXP, I liked many things about Ubuntu (especially the philosophy), but my VPN is very important, nothing seems to work, and I lost enough time because of this to create serious problems.

---

### Post by the_darkside_986 on 2008-08-08
I just use the Ubuntu vpnc client and converted my pcf file to conf with this nice script: [http://svn.unix-ag.uni-kl.de/vpnc/trunk/pcf2vpnc](http://svn.unix-ag.uni-kl.de/vpnc/trunk/pcf2vpnc)

A file produced such as foo.conf would be moved to /etc/vpnc/ and to use it one types 
```

sudo vpnc foo

```

I would go insane if I had to reboot to XP when I need to remotely log into a Windows server because of VPN. (We just moved some of our offices to a new location but the servers are still at the old place).

---

