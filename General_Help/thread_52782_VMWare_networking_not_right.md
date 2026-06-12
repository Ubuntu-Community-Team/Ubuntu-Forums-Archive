---
title: "VMWare networking not right"
date: 2005-07-28
forum: General Help
---

### Post by starNIX on 2005-07-28
Ok,  I just setup dhcp and everything to create a LAN and I don't know if the configuration issue is with WinXP, with VMWare or with my Ubuntu Setup.

Ok,  I have eth0 configured with a static IP of 10.3.2.1.  The subnet mask is set to 255.255.255.0.   I have the gateway address set to blank. 

I have DNS servers set to my DNS server IP's and I have Search Domains set to my search domain address.  (All this is in Gnome Network Settings).

I have eth1 configured for connection to my cable modem with DHCP.  This works fine.

When I boot up Windows (in VMWare) and look at the network properties for Local area connection,  it says it is getting an IP address from my dhcp server. and it shows the IP as 10.3.2.200.  Vmware is set to use "Bridged" networking.

an ipconfig shows:
Ethernet adapter Local Area Connection:
  Connection-specific DNS Suffix                              the-hollow.net
  IP Address                                                            10.3.2.200
  Subnet Mask                                                        255.255.255.0
  Default Gateway                                                   <blank>

If I do an ifconfig on LINUX I get:

eth0      Link encap:Ethernet  HWaddr 00:0D:61:04:17:F2
          inet addr:10.3.2.1  Bcast:10.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:61ff:fe04:17f2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9811 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2076 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:600352 (586.2 KiB)  TX bytes:306226 (299.0 KiB)
          Interrupt:22 Base address:0x2000

eth1      Link encap:Ethernet  HWaddr 00:0D:61:05:2A:88
          inet addr:71.10.112.173  Bcast:255.255.255.255  Mask:255.255.240.0
          inet6 addr: fe80::20d:61ff:fe05:2a88/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1479466 errors:0 dropped:0 overruns:0 frame:0
          TX packets:90259 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:207779268 (198.1 MiB)  TX bytes:10617595 (10.1 MiB)
          Base address:0x9000 Memory:e5000000-e5020000



From Windows I can ping the LINUX box by IP and by hostname.

From LINUX I can ping the windows box by IP and by hostname.

I cannot ping anything on the internet from Windows. 

When I try from windows it shows the IP address of the site I am trying to ping which means that DNS is working(?)   I just get "Destination host unreachable".

In firestarter,  I have eth0 set to the "Local network connected device" and I have "Enable internet connection sharing" checked.  However,  I don't have "Enable DHCP for local network" enabled because when I have them both enabled,  firestarter spits out an error 

"Failed to start the firewall :
An unknown error occurred

Please check your network device settings and make sure your internet connection is active."

Do I need dnsmasq installed?  I have it,  but what does it do and why do I need it?


Anyone able to tell me if it is my Windows, LINUX or VMWare setup?

---

### Post by MrCheese on 2005-07-29
> Ok,  I have eth0 configured with a static IP of 10.3.2.1.  The subnet mask is set to 255.255.255.0.   I have the gateway address set to blank. 

Try doing a manual ip config on XP using the same address as dhcp gave you but add a default gateway (without this there is no path out of the local network). Use the gateway address which works for the systems which can access the 'net.

---

### Post by kassetra on 2005-08-01
[QUOTE=starNIX]
Anyone able to tell me if it is my Windows, LINUX or VMWare setup?[/QUOTE]

When you ran vmware-config.pl - what network settings did you give it?  Did you setup all of the special vpn's it asks about?  What kind of networking did you tell it you wanted to use?  Did you give it a username/pass?

---

