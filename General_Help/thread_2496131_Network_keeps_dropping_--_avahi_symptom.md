---
title: "Network keeps dropping -- avahi symptom?"
date: 2024-03-14
forum: General Help
---

### Post by armegeden on 2024-03-14
Hello!

I have Ubuntu 22.04.4 running on a Raspberry Pi3. 
 I have wlan0 connected to a SSID with Internet access. 
 I have eth0 with a static IP of 10.1.8.1 and running ISC DHCP running only on eth0 so that my Philips Hue (directly connected, requires ethernet) can get online.

Initially, all is working fine.  

```
syn@ubuntu:~$ ifconfig
eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 10.1.8.1  netmask 255.255.255.0  broadcast 10.1.8.255
        inet6 fe80::ba27:ebff:fe0a:83a2  prefixlen 64  scopeid 0x20<link>
        ether b8:27:eb:0a:83:a2  txqueuelen 1000  (Ethernet)
        RX packets 162874  bytes 13255072 (13.2 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 284389  bytes 388836661 (388.8 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


lo: flags=<Loopback info removed/unused>


wlan0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 172.20.4.106  netmask 255.255.0.0  broadcast 172.20.255.255
        inet6 fda4:2671:f77b:354e:ba27:ebff:fe5f:d6f7  prefixlen 64  scopeid 0x0<global>
        inet6 fe80::ba27:ebff:fe5f:d6f7  prefixlen 64  scopeid 0x20<link>
        ether b8:27:eb:5f:d6:f7  txqueuelen 1000  (Ethernet)
        RX packets 339165  bytes 395555279 (395.5 MB)
        RX errors 0  dropped 3  overruns 0  frame 0
        TX packets 162159  bytes 23644547 (23.6 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```

Route info: (my default route should be to wlan0)
```
syn@ubuntu:~$ ip route
default via 172.20.1.1 dev wlan0 proto dhcp src 172.20.4.106 metric 1
10.1.8.0/24 dev eth0 proto kernel scope link src 10.1.8.1
172.20.0.0/16 dev wlan0 proto kernel scope link src 172.20.4.106 metric 1
172.20.1.1 dev wlan0 proto dhcp scope link src 172.20.4.106 metric 1

```

After 9 minutes of operation (monitored via continuous ping to 8.8.8.8), I lose connection.  The symptoms I see (tail -f /var/log/syslog) when this happens is avahi shutting down the interface, bringing up a 169 address.  At some point the eth0 interface ends up with a 10.1.8.111 IP -- an address within it's own DHCP scope!  A default route gets installed to eth0 and I lose connection.
  
I'm able to reset everything with "sudo netplan apply" -- but rinse & repeat after 9 minutes.

Any idea?

syslog event:
```
Mar 14 13:05:07 ubuntu dhclient[914]: DHCPREQUEST for 10.1.8.111 on eth0 to 255.255.255.255 port 67 (xid=0x529d6045)
Mar 14 13:05:07 ubuntu dhcpd[19924]: reuse_lease: lease age 37 (secs) under 25% threshold, reply with unaltered, existing lease for 10.1.8.111
Mar 14 13:05:07 ubuntu dhcpd[19924]: DHCPREQUEST for 10.1.8.111 from b8:27:eb:0a:83:a2 (ubuntu) via eth0
Mar 14 13:05:07 ubuntu dhcpd[19924]: DHCPACK on 10.1.8.111 to b8:27:eb:0a:83:a2 (ubuntu) via eth0
Mar 14 13:05:21 ubuntu dhclient[914]: DHCPREQUEST for 10.1.8.111 on eth0 to 255.255.255.255 port 67 (xid=0x529d6045)
Mar 14 13:05:21 ubuntu dhcpd[19924]: reuse_lease: lease age 51 (secs) under 25% threshold, reply with unaltered, existing lease for 10.1.8.111
Mar 14 13:05:21 ubuntu dhcpd[19924]: DHCPREQUEST for 10.1.8.111 from b8:27:eb:0a:83:a2 (ubuntu) via eth0
Mar 14 13:05:21 ubuntu dhcpd[19924]: DHCPACK on 10.1.8.111 to b8:27:eb:0a:83:a2 (ubuntu) via eth0


Mar 14 13:05:34 ubuntu avahi-autoipd(eth0)[2545]: Found user 'avahi-autoipd' (UID 116) and group 'avahi-autoipd' (GID 125).
Mar 14 13:05:34 ubuntu avahi-autoipd(eth0)[2545]: Successfully called chroot().
Mar 14 13:05:34 ubuntu avahi-autoipd(eth0)[2545]: Successfully dropped root privileges.
Mar 14 13:05:34 ubuntu avahi-autoipd(eth0)[2545]: Starting with address 169.254.11.75
Mar 14 13:05:40 ubuntu avahi-autoipd(eth0)[2545]: Callout BIND, address 169.254.11.75 on interface eth0
Mar 14 13:05:44 ubuntu avahi-autoipd(eth0)[2545]: Successfully claimed IP address 169.254.11.75
Mar 14 13:05:44 ubuntu avahi-autoipd(eth0)[2545]: Got SIGTERM, quitting.
Mar 14 13:05:44 ubuntu avahi-autoipd(eth0)[2545]: Callout STOP, address 169.254.11.75 on interface eth0
Mar 14 13:05:45 ubuntu dhclient[914]: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3 (xid=0x753c1e37)
Mar 14 13:05:45 ubuntu dhcpd[19924]: reuse_lease: lease age 75 (secs) under 25% threshold, reply with unaltered, existing lease for 10.1.8.111
Mar 14 13:05:45 ubuntu dhcpd[19924]: DHCPDISCOVER from b8:27:eb:0a:83:a2 (ubuntu) via eth0
Mar 14 13:05:45 ubuntu dhcpd[19924]: DHCPOFFER on 10.1.8.111 to b8:27:eb:0a:83:a2 (ubuntu) via eth0
Mar 14 13:05:45 ubuntu dhclient[914]: DHCPOFFER of 10.1.8.111 from 10.1.8.1
Mar 14 13:05:45 ubuntu dhclient[914]: DHCPREQUEST for 10.1.8.111 on eth0 to 255.255.255.255 port 67 (xid=0x371e3c75)
Mar 14 13:05:45 ubuntu dhcpd[19924]: reuse_lease: lease age 75 (secs) under 25% threshold, reply with unaltered, existing lease for 10.1.8.111
Mar 14 13:05:45 ubuntu dhcpd[19924]: DHCPREQUEST for 10.1.8.111 (10.1.8.1) from b8:27:eb:0a:83:a2 (ubuntu) via eth0
Mar 14 13:05:45 ubuntu dhcpd[19924]: DHCPACK on 10.1.8.111 to b8:27:eb:0a:83:a2 (ubuntu) via eth0
Mar 14 13:05:45 ubuntu dhclient[914]: DHCPACK of 10.1.8.111 from 10.1.8.1 (xid=0x753c1e37)
Mar 14 13:05:45 ubuntu dhclient[914]: bound to 10.1.8.111 -- renewal in 204 seconds.

```

Ping when event happens:
```
syn@ubuntu:~$ ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=8 ttl=118 time=14.5 ms
64 bytes from 8.8.8.8: icmp_seq=9 ttl=118 time=15.0 ms
64 bytes from 8.8.8.8: icmp_seq=10 ttl=118 time=17.0 ms
!  syslog event:  Mar 14 13:05:34 ubuntu avahi-autoipd(eth0)[2545]: Found user 'avahi-autoipd' (UID 116) and group 'avahi-autoipd' (GID 125).
From 10.1.8.111 icmp_seq=11 Destination Host Unreachable
From 10.1.8.111 icmp_seq=12 Destination Host Unreachable
From 10.1.8.111 icmp_seq=13 Destination Host Unreachable
From 10.1.8.111 icmp_seq=14 Destination Host Unreachable
From 10.1.8.111 icmp_seq=15 Destination Host Unreachable
From 10.1.8.111 icmp_seq=18 Destination Host Unreachable

```


ifconfig after syslog event:
```
syn@ubuntu:~$ ifconfig
eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 10.1.8.111  netmask 255.255.255.0  broadcast 10.1.8.255
        inet6 fe80::ba27:ebff:fe0a:83a2  prefixlen 64  scopeid 0x20<link>
        ether b8:27:eb:0a:83:a2  txqueuelen 1000  (Ethernet)
        RX packets 163050  bytes 13264506 (13.2 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 284601  bytes 388854663 (388.8 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


lo: flags=<Lo removed>


wlan0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 172.20.4.106  netmask 255.255.0.0  broadcast 172.20.255.255
        inet6 fda4:2671:f77b:354e:ba27:ebff:fe5f:d6f7  prefixlen 64  scopeid 0x0<global>
        inet6 fe80::ba27:ebff:fe5f:d6f7  prefixlen 64  scopeid 0x20<link>
        ether b8:27:eb:5f:d6:f7  txqueuelen 1000  (Ethernet)
        RX packets 339545  bytes 395588544 (395.5 MB)
        RX errors 0  dropped 3  overruns 0  frame 0
        TX packets 162485  bytes 23737055 (23.7 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```

Finally, ip route after issue:
```
syn@ubuntu:~$ ip route
default via 10.1.8.1 dev eth0
default via 172.20.1.1 dev wlan0 proto dhcp src 172.20.4.106 metric 1
10.1.8.0/24 dev eth0 proto kernel scope link src 10.1.8.111
172.20.0.0/16 dev wlan0 proto kernel scope link src 172.20.4.106 metric 1
172.20.1.1 dev wlan0 proto dhcp scope link src 172.20.4.106 metric 1



```

Any idea?  I've seen forum posts say that it isn't avahi, rather, avahi sees the change and adjusts -- it's a symptom of the problem.

But I'm at a loss of what it could be.

Any tips greatly appreciated

---

### Post by jonads on 2024-03-14
[h=2]Re: Network Connection Loss on Ubuntu 22.04 with Raspberry Pi 3[/h][COLOR=#1F1F1F][FONT=&quot]I understand you're facing an issue where your Raspberry Pi loses internet connection after 9 minutes. The logs you provided offer valuable clues to diagnose the problem.[/FONT][/COLOR]
[COLOR=#1F1F1F][FONT=&quot]Here's a breakdown of the situation and some potential solutions:[/FONT][/COLOR]
[COLOR=#1F1F1F][FONT=&quot]The Issue:[/FONT][/COLOR]

[LIST]
[*]You have a Raspberry Pi running Ubuntu 22.04 with two network interfaces:
[LIST]
[*]wlan0 connected to the internet with a DHCP lease.
[*]eth0 configured with a static IP for your Philips Hue device and serving DHCP for it.
[/LIST]

[*]After 9 minutes, the internet connection drops.
[*]Analysis of logs reveals:
[LIST]
[*]isc-dhcpd on eth0 assigns an IP address (10.1.8.111) to your device (ubuntu) even though it shouldn't.
[*]avahi-autoipd service kicks in on eth0, likely due to the missing internet connection, and assigns a 169.254.x.x address (self-assigned IP).
[*]Your default route gets switched to eth0 with the conflicting IP, causing internet connectivity loss.
[/LIST]
[/LIST]
[COLOR=#1F1F1F][FONT=&quot]Possible Causes:[/FONT][/COLOR]

[LIST]
[*]Conflicting DHCP Server:
The presence of isc-dhcpd running on eth0 might be causing conflicts with the DHCP server on your internet connection. Even though it's configured for eth0, it might be interfering with the overall network setup.
[*]Network Interface Interaction:
There might be an issue with how the two network interfaces (wlan0 and eth0) are interacting. This could lead to unexpected behavior like eth0 obtaining a DHCP lease or avahi-autoipd activating on it.
[/LIST]
[COLOR=#1F1F1F][FONT=&quot]Solutions to Try:[/FONT][/COLOR]

[LIST=1]
[*]Disable isc-dhcpd on eth0:
Since your Philips Hue device likely has a static IP configured, you might not need a DHCP server running on eth0. Disabling isc-dhcpd can prevent address conflicts.

[LIST]
[*]Edit the /etc/dhcp/dhcpd.conf file and comment out any configuration related to eth0.
[*]Restart the isc-dhcpd service: sudo systemctl restart isc-dhcpd
[/LIST]

[*]Investigate Network Interface Interaction:

[LIST]
[*]Check firewall rules that might be affecting traffic flow between interfaces.
[*]Explore advanced network configuration options like bridge interfaces, which can manage multiple physical interfaces as a single logical unit. However, this solution might be more complex to implement.
[/LIST]
[/LIST]
[COLOR=#1F1F1F][FONT=&quot]Additional Tips:[/FONT][/COLOR]

[LIST]
[*]Double-check your network configuration files for any errors or inconsistencies.
[*]Consider temporarily disabling avahi-autoipd to see if it affects the issue (not recommended as a long-term solution).
[*]Research network troubleshooting guides for Raspberry Pi specifically.
[/LIST]
[COLOR=#1F1F1F][FONT=&quot]If these suggestions don't resolve the issue, consider providing more details about your network configuration and any additional logs you might have. This can help narrow down the cause and identify a more specific solution.[/FONT][/COLOR]

---

### Post by armegeden on 2024-03-14
Hi jonads, 

Thank you for taking the time to reply.

Unfortunately I cannot assign a Static IP to the Philips Hue. So, I do need a DHCP server.

I've been troubleshooting, and it's definitely something to do with eth0 receiving a DHCP IP address in addition to the Static IP.  Once the DHCP is assigned, the route gets injected and points towards itself, causing the system to lose internet connection (via wlan0).  eth0 also appears to lose the Static config!

I can even see the DHCP Leases with an address dynamically assigned to b8:27:eb:0a:83:a2, which is the eth0 interface itself.

Also, output:
```
sudo ip link
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP mode DEFAULT group default qlen 1000
    link/ether b8:27:eb:0a:83:a2 brd ff:ff:ff:ff:ff:ff
3: wlan0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP mode DORMANT group default qlen 1000
    link/ether b8:27:eb:5f:d6:f7 brd ff:ff:ff:ff:ff:ff
syn@ubuntu:~$ sudo ip addr show
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: **eth0: **<BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether **b8:27:eb:0a:83:a2** brd ff:ff:ff:ff:ff:ff
**    inet 10.1.8.111/24 brd 10.1.8.255 scope global dynamic eth0**
       valid_lft 120sec preferred_lft 120sec
    inet6 fe80::ba27:ebff:fe0a:83a2/64 scope link
       valid_lft forever preferred_lft forever
3: wlan0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether b8:27:eb:5f:d6:f7 brd ff:ff:ff:ff:ff:ff
    inet 172.20.4.106/16 metric 1 brd 172.20.255.255 scope global dynamic wlan0
       valid_lft 84832sec preferred_lft 84832sec
    inet6 fda4:2671:f77b:354e:ba27:ebff:fe5f:d6f7/64 scope global dynamic mngtmpaddr noprefixroute
       valid_lft 1470sec preferred_lft 1470sec
    inet6 fe80::ba27:ebff:fe5f:d6f7/64 scope link
       valid_lft forever preferred_lft forever



```


My netplan:
```

more /etc/netplan/50-cloud-init.yaml
# This file is generated from information provided by the datasource.  Changes
# to it will not persist across an instance reboot.  To disable cloud-init's
# network configuration capabilities, write a file
# /etc/cloud/cloud.cfg.d/99-disable-network-config.cfg with the following:
# network: {config: disabled}
network:
    version: 2
    wifis:
        renderer: networkd
        wlan0:
            access-points:
                Elem:
                    password: !
            dhcp4: true
            dhcp4-overrides:
              route-metric: 1
            optional: true
    ethernets:
**        eth0:**
**            dhcp4: false**
            addresses:
              - **10.1.8.1/24**
            routes:
              - to: default
                via: 172.20.1.1
            nameservers:
                addresses: [8.8.8.8,8.8.4.4]
syn@ubuntu:~$



```

Insuring eth0 should NOT be a DHCP Client:

```
more /etc/dhcpcd.conf


**denyinterfaces eth0**



```

One again, I'm at a loss as to why my eth0 interface (MAC b8:27:eb:0a:83:a2) is requesting a DHCP address.  And more importantly why ISC on eth0 is assigning one.





ISC DHCP lease:
```
cat /var/lib/dhcp/dhcpd.leases
# The format of this file is documented in the dhcpd.leases(5) manual page.
# This lease file was written by isc-dhcp-4.4.1


# authoring-byte-order entry is generated, DO NOT DELETE
authoring-byte-order little-endian;


lease 10.1.8.111 {
  starts 4 2024/03/14 18:35:19;
  ends 4 2024/03/14 18:45:19;
  tstp 4 2024/03/14 18:45:19;
  cltt 4 2024/03/14 18:35:19;
  binding state free;
  hardware ethernet **b8:27:eb:0a:83:a2**;
}

```

---

### Post by armegeden on 2024-03-14
I think I figured it out.  It turned out to be an **indentation issue in the Netplan's YAML file**.  I copied & pasted the file into ChatGPT and asked it to fix any formatting errors.  I threw the results back into my YAML and did Netplan Apply and I've been stable for about 20 minutes.

So, if that's the case, then:

Netplan YAML line that disabled DHCP (dhcp4: no) was not indented correctly.  So DHCP Client was running on Eth0 while it also had a Static IP.

So, the interface would come up with 10.1.8.1, request & receive an IP of 10.1.8.111 along with routing information, then blackhole itself.

I'm surprised a DHCP Client address would overwrite a Static, but here we are &#55358;&#56631;*&#9794;&#65039;  There goes a day of troubleshooting due to spacebar.

---

