---
title: "Cannot ping/ssh/telnet to local machines"
date: 2008-01-29
forum: General Help
---

### Post by vjayant on 2008-01-29
Hi,
I have just installed Gutsy and I am not able to ssh,ping or telnet to local machines in my LAN,while i can ping to addresses outside! When i try to ssh, it says
connect to host 172....... port 22: No route to host
Can anyone please help me out with this?Thanks

---

### Post by schallstrom on 2008-01-29
Please give us the output of the following commands:
```

sudo ip link
sudo ip route

```
And then the output of a ping command (including the command itself)  trying to ping a local machine.

---

### Post by dgermann on 2008-02-02
Hi--

I'm having a similar problem, so do you folks mind if I jump in here, too?

My symptoms are the same, except when I go to connect I get no response. For instance:
```
~$ ssh -vvv doug@192.168.0.83
OpenSSH_4.6p1 Debian-5ubuntu0.1, OpenSSL 0.9.8e 23 Feb 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.168.0.83 [192.168.0.83] port 22.

```
and then it just sits there, seemingly forever.

The commands you suggest yield:
```
doug@doug2:~$ sudo ip link
1: lo: <LOOPBACK,UP,10000> mtu 16436 qdisc noqueue 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eth0: <BROADCAST,MULTICAST,UP,10000> mtu 1500 qdisc pfifo_fast qlen 100
    link/ether [blanked] brd ff:ff:ff:ff:ff:ff
doug@doug2:~$ sudo ip route
192.168.0.0/24 dev eth0  proto kernel  scope link  src 192.168.0.3 
169.254.0.0/16 dev eth0  scope link  metric 1000 
default via 192.168.0.1 dev eth0 
doug@doug2:~$ 

```

The two machines I am having trouble with each have Gutsy 7.10: ~.3 is my desktop; ~.83 is a laptop. I cannot ssh into either machine. I can ping each of these machines from each other and from other machines on the network. I can ssh on each box to 127.0.0.1.

However, I have other linux boxes: 2 are 6.06LTS machines and one is a RedHat 9.0. I have no problem connecting to these other machines via ssh. Is this a Gutsy issue?

Same problem existed with and without firestarter turned on.

Those are about all the clues I have been able to discover.

Any ideas for troubleshooting this?

Thanks!

---

### Post by schallstrom on 2008-02-03
So you want to ssh from 192.168.0.3 to 192.168.0.83 and you are able to ping 192.168.0.83, right? If you are able to ssh to localhost that suggests that the ssh daemon is running on both machines, but you could double check:
```

# ps ax|grep sshd
23556 ?        Ss     0:00 /usr/sbin/sshd

```

I'm not sure if this is connected to the problem, but the red route seems strange to me
```

doug@doug2:~$ sudo ip route
192.168.0.0/24 dev eth0  proto kernel  scope link  src 192.168.0.3 
[COLOR="Red"]169.254.0.0/16 dev eth0  scope link  metric 1000 [/COLOR]
default via 192.168.0.1 dev eth0

```
Do you configure the networking of the machine manually or via DHCP?

You could also run tcpdump on the machine you want to connect to and check if the ssh packets are arriving like this:
```

# tcpdump -ni eth0 port ssh

```
then try to connect from the client machine and you shuld see arriving packets which looks similar to this:
```

14:11:30.386622 IP 192.168.1.251.33534 > 192.168.2.25.22: S 3018239150:3018239150(0) win 5840 <mss 1460,sackOK,timestamp 79333 0,nop,wscale 5>
14:11:30.386724 IP 192.168.2.25.22 > 192.168.1.251.33534: S 3669313662:3669313662(0) ack 3018239151 win 5792 <mss 1460,sackOK,timestamp 153919305 79333,nop,wscale 6>
14:11:30.387922 IP 192.168.1.251.33534 > 192.168.2.25.22: . ack 1 win 183 <nop,nop,timestamp 79333 153919305>
14:11:30.438927 IP 192.168.2.25.22 > 192.168.1.251.33534: P 1:41(40) ack 1 win 91 <nop,nop,timestamp 153919318 79333>
14:11:30.440170 IP 192.168.1.251.33534 > 192.168.2.25.22: . ack 41 win 183 <nop,nop,timestamp 79339 153919318>
14:11:30.440437 IP 192.168.1.251.33534 > 192.168.2.25.22: P 1:21(20) ack 41 win 183 <nop,nop,timestamp 79339 153919318>
14:11:30.440546 IP 192.168.2.25.22 > 192.168.1.251.33534: . ack 21 win 91 <nop,nop,timestamp 153919318 79339>
14:11:30.441703 IP 192.168.2.25.22 > 192.168.1.251.33534: P 41:785(744) ack 21 win 91 <nop,nop,timestamp 153919318 79339>
14:11:30.442452 IP 192.168.1.251.33534 > 192.168.2.25.22: P 21:773(752) ack 41 win 183 <nop,nop,timestamp 79339 153919318>
14:11:30.481333 IP 192.168.1.251.33534 > 192.168.2.25.22: . ack 785 win 229 <nop,nop,timestamp 79343 153919318>
14:11:30.481406 IP 192.168.2.25.22 > 192.168.1.251.33534: . ack 773 win 114 <nop,nop,timestamp 153919328 79339>
14:11:30.482530 IP 192.168.1.251.33534 > 192.168.2.25.22: P 773:797(24) ack 785 win 229 <nop,nop,timestamp 79343 153919328>
14:11:30.509494 IP 192.168.2.25.22 > 192.168.1.251.33534: P 785:937(152) ack 797 win 114 <nop,nop,timestamp 153919335 79343>
14:11:30.510783 IP 192.168.1.251.33534 > 192.168.2.25.22: . ack 937 win 276 <nop,nop,timestamp 79346 153919335>
14:11:30.513836 IP 192.168.1.251.33534 > 192.168.2.25.22: P 797:941(144) ack 937 win 276 <nop,nop,timestamp 79346 153919335>
14:11:30.547224 IP 192.168.2.25.22 > 192.168.1.251.33534: P 937:1657(720) ack 941 win 138 <nop,nop,timestamp 153919345 79346>
14:11:30.591430 IP 192.168.1.251.33534 > 192.168.2.25.22: . ack 1657 win 322 <nop,nop,timestamp 79354 153919345>
14:11:32.464692 IP 192.168.1.251.33534 > 192.168.2.25.22: F 941:941(0) ack 1657 win 322 <nop,nop,timestamp 79541 153919345>
14:11:32.465789 IP 192.168.2.25.22 > 192.168.1.251.33534: F 1657:1657(0) ack 942 win 138 <nop,nop,timestamp 153919824 79541>
14:11:32.467113 IP 192.168.1.251.33534 > 192.168.2.25.22: . ack 1658 win 322 <nop,nop,timestamp 79541 153919824>

```

---

### Post by dgermann on 2008-02-03
schallstrom--

Well, the problem is at least partially solved for me. Somehow firestarter was blocking these connections. As I said earlier, it did not seem to make a difference whether firestarter was on or not in my prior tests, but now it seems to be the difference.

So the question then became how to get firestarter to allow the connection, since the connection is via dhcp and I cannot just enter a single address. I had in the the incoming policy to allow "localnet/24" but obviously that was not working for me. The answer ("192.168.0.1/24") was located here on the firestarter site: [http://www.fs-security.com/docs/faq.php#ranges]("http://www.fs-security.com/docs/faq.php#ranges")

schallstrom, you were very helpful, and I thank you.

Yes, that 169.254.0.0/16 looked strange to me too. I did a little checking on it and found that it is [http://iana.org/](http://iana.org/), which says it is part of ICANN. So perhaps it is legit. Wonder why, though, this is in there--I do not know enough to have changed this, so I have to think it was in Gutsy out of the box.

Anybody have any ideas about that one?

And the tcpdump worked as you advertised.

Thanks so much, schallstrom!

---

### Post by vjayant on 2008-02-04
Thanks a lot schallstrom for your response.Sorry for my late reply.
Well i've realised that the machine i am trying to ping is not so local after all.the problem however still remains.The output of the commands you mentioned are below:

sudo ip link

1: lo: <LOOPBACK,UP,10000> mtu 16436 qdisc noqueue 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
12: eth0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:16:d4:09:82:f2 brd ff:ff:ff:ff:ff:ff
13: eth1: <BROADCAST,MULTICAST,UP,10000> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:14:a5:aa:97:62 brd ff:ff:ff:ff:ff:ff

sudo ip route
172.17.16.0/23 dev eth1  proto kernel  scope link  src 172.17.16.148 
169.254.0.0/16 dev eth0  scope link  metric 1000 
172.16.0.0/16 dev eth0  proto kernel  scope link  src 172.16.2.138 
default via 172.17.16.1 dev eth1 
default via 172.16.2.1 dev eth0  metric 100


I am using a wireless connection,so my device is eth1.

the output of the ping command is below:

 ping 172.16.2.150
PING 172.16.2.150 (172.16.2.150) 56(84) bytes of data.
From 172.16.2.138 icmp_seq=1 Destination Host Unreachable
From 172.16.2.138 icmp_seq=2 Destination Host Unreachable
From 172.16.2.138 icmp_seq=3 Destination Host Unreachable

Regards,
Jayant

---

### Post by schallstrom on 2008-02-05
@dgermann: ICANN and IANA are central authorities which govern the worldwide use of IP addresses and domain names. So every IP address that could ever exists belongs to them in a certain sense, so that is not telling us very much in the end ;)

The interesting question is: How was this route inserted in your routing table? In an average home computer which is connected to the internet through a home router, there are normally only two entires in the routing table needed: To tell the kernel through which interface to reach the local network, and which gateway to use, to reach all other networks. At least when using IPv4 you will never deal with public IP addresses on the client computer. That looks sth like this:
```

# ip route
192.168.2.0/24 dev eth1  proto kernel  scope link  src 192.168.2.25 
default via 192.168.2.1 dev eth1 

```

@vjayant: I see two default gateways in your routing table. I would try and shut down the interface you are not using and then try the ping commands again. If you are using the Gnome network-manager you probably deactivate the interface through it, or you do it with the command
```

# ip link set eth0 down

```

---

### Post by vjayant on 2008-02-05
It worked! :) Thanks a lot schallstrom!
Jayant

---

### Post by dgermann on 2008-02-06
schallstrom--

Yup, I was kinda wondering how that got in there too. Think I'd ought to take it out?

Thanks!

---

### Post by schallstrom on 2008-02-07
@dgermann

If you wont to delete the route you could do it with the 'ip' command or the deprecated 'route' command, but I don't know the exact syntax from memory so you would have to look it up in the man pages.

More interesting would be to find out where it comes from. You could restart the network scripts with
```

# /etc/init.d/networking restart

```
and then check if its still there. Check the config of the DHCP server. Or do you use any VPN clients on the machine which could add routing information? That's all I can think of at the moment.

---

### Post by dgermann on 2008-02-07
schallstrom--

Interesting:
```
doug@doug2:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
                                                                         [ OK ]
doug@doug2:~$ sudo ip route
192.168.0.0/24 dev eth0  proto kernel  scope link  src 192.168.0.3 
169.254.0.0/16 dev eth0  scope link  metric 1000 
default via 192.168.0.1 dev eth0 
doug@doug2:~$ 

```

---

### Post by schallstrom on 2008-02-10
Hmm, maybe you want to post your /etc/network/interfaces file?

---

### Post by dgermann on 2008-02-11
Sure 'nuf:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp
~

```

That solves the mystery, huh? ;)

---

### Post by schallstrom on 2008-02-12
Uhm, what do you mean?

I would say that the line saying 'iface eth0 inet dhcp' should not be commented out.

---

### Post by dgermann on 2008-02-13
schallstrom--

<<Uhm, what do you mean?

Simply my failed attempt at wry humor. I thought it told us nothing about the strange 169.254.0.0 ip address....

But I did miss that that line was commented out. Thank you for catching that.

So here was the progression of what I tried:
```

doug@doug2:~$ sudo gedit /etc/network/interfaces
[sudo] password for doug:
doug@doug2:~$ man interfaces
doug@doug2:~$ man ifup
doug@doug2:~$ sudo ifup -a
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:[blanked]
Sending on   LPF/eth0/00:[blanked]
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER from 192.168.0.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.3 -- renewal in 40352 seconds.
 * Stopping the Firestarter firewall...
   ...done.
 * Starting the Firestarter firewall...
   ...done.
mount: wrong fs type, bad option, bad superblock on earth:/exports,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so [Note: this was expected--there is no file at earth:/exports]

doug@doug2:~$ mount -l
/dev/sda1 on / type ext3 (rw,errors=remount-ro) []
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/sdb1 on /media/sdb1 type ext3 (rw) [/]
securityfs on /sys/kernel/security type securityfs (rw)
//samba1/vol22 on /sam/vol22 type cifs (rw,mand,noexec,nosuid,nodev)
//samba1/vol12 on /sam/vol12 type cifs (rw,mand,noexec,nosuid,nodev)
//samba1/doug2 on /sam/doug2 type cifs (rw,mand,noexec,nosuid,nodev)
doug@doug2:~$ sudo ip route
192.168.0.0/24 dev eth0  proto kernel  scope link  src 192.168.0.3 
169.254.0.0/16 dev eth0  scope link  metric 1000 [<<==== Still showing up]
default via 192.168.0.1 dev eth0  metric 100 
doug@doug2:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                           * Stopping the Firestarter firewall...
   ...done.
 * Starting the Firestarter firewall...
   ...done.
There is already a pid file /var/run/dhclient.eth0.pid with pid 12202
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:[blanked]
Sending on   LPF/eth0/00:[blanked]
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.0.1 port 67
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:[blanked]
Sending on   LPF/eth0/00:[blanked]
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPOFFER from 192.168.0.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.3 -- renewal in 35838 seconds.
 * Stopping the Firestarter firewall...
   ...done.
 * Starting the Firestarter firewall...
   ...done.
mount: wrong fs type, bad option, bad superblock on earth:/exports,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

                                                                         [ OK ]
doug@doug2:~$ sudo ip route
192.168.0.0/24 dev eth0  proto kernel  scope link  src 192.168.0.3 
169.254.0.0/16 dev eth0  scope link  metric 1000 [<<=== Still showing up]
default via 192.168.0.1 dev eth0  metric 100 
doug@doug2:~$ 

```

So I am not sure it helped nor whether it harmed anything. It did not get rid of the strange ip address....

Thanks, schallstrom!

---

### Post by schallstrom on 2008-02-14
My next guess would be that maybe it comes from firestarter. But I never used this program so I can't say anything about. Maybe just deactivate it, restart networking and see what happens?

---

### Post by dgermann on 2008-02-14
schallstrom--

Thanks for your continued help!

I tried disabling firestarter and then running /etc/init.d/networking restart--but its process stops and restarts firestarter. So every time I ran ip route, I get the same output--with that strange 169.254.0.0.

Does it seem safe to you as it is? Or should I just shrug my shoulders and give up?

Thanks!

---

### Post by schallstrom on 2008-02-15
I found out that the 169.254.0.0/16 address range is reserved for so called [link-local addresses]("http://en.wikipedia.org/wiki/Link-local_address") which are not routed in the internet. So I would guess that the route shouldn't be harmful in terms of malware or something. So if everything is working you could just ignore it. But the hackers approach would be to find out what is going on in your system at any cost ;)

To be honest I still don't have a clue how to systematically investigate that. If firestarter gets started by the networking scripts, you could uninstall firestarter temporary. If you uninstall with "aptitude remove firestarter" and *not* with "aptitude purge firestarter", the configuration will be kept so everything will be the same after reinstalling.

---

### Post by dgermann on 2008-02-16
schallstrom--

Thanks for all your help on this.

I removed firestarter using synaptic, ran networking restart and ip route still shows the 169.254.0.0/16 entry.

Your research has eased my mind.

Thanks for your help. I think I will let it stand where it is for now.

Another Gutsy box I have also has that entry.

---

