---
title: "OpenS/WAN configuration failed, please help me =("
date: 2008-04-01
forum: General Help
---

### Post by vpn_nukem on 2008-04-01
Hi there,
I have a problem due to OpenS/WAN!

Im using Ubuntu Gutsy (Kernel 2.6.22-14-generic) and want to set up a vpn connection.

My networkinfrastructure looks like this:

```
PC -> Switch -> VPN Gateway -> Switch -> Notebook

IPs:
PC
192.168.0.2
255.255.255.252
192.168.0.1

VPN GW
eth0
192.168.0.1
255.255.255.252

eth1
10.1.1.1
255.255.255.0

Notebook
10.1.1.2
255.255.255.0
10.1.1.1

```

I want to connect the Notebook with the 192.168.0.0 subnet!

My ipsec.conf:
```

version 2.0

config setup

interfaces=%defaultroute
nhelpers=1

conn %default

authby=secret
keyingtries=1

conn testnet
left=10.1.1.2/8
leftnexthop=10.1.1.1/8
leftsubnet=10.1.1.0/8
right=192.168.0.1/3   #??
rightsubnet=192.168.0.0/3


#Disable Opportunistic Encryption

include /etc/ipsec.d/examples/no_oe.conf

```


So, when i type
```
ipsec setup start
```

Im getting following message:

```
ipsec_setup: (/etc/ipsec.conf, line 28) parameter is not within a section -- `start` aborted
```

I also read thread like this [http://ubuntuforums.org/showthread.php?t=527423&highlight=openswan]("http://ubuntuforums.org/showthread.php?t=527423&highlight=openswan")

but it didnt help me :(

This have to be work till friday :frown:

Can you help me? My last hope.. :???:

Thanks!!!!

greets
nukem

Ah, i forgot, the clients are Windows XP Clients

---

### Post by vpn_nukem on 2008-04-01
Hi, i changed my ipsec.conf a little bit

```

version 2.0

config setup

interfaces="ipsec0=eth0" # can anyone explain me that?
nhelpers=1
plutodebug=none
klipsdebug=none

conn %default

authby=secret
keyingtries=1

conn testnet
type=tunnel
leftid=@remote
left=10.1.1.2
leftnexthop=10.1.1.1
leftsubnet=10.1.1.0/8
rightid=@lan
right=192.168.0.1   #??
rightsubnet=192.168.0.0/3
pfs=no
auto=add


#Disable Opportunistic Encryption

include /etc/ipsec.d/examples/no_oe.conf

```

I start with
```
ipsec setup start
```

Then I type
```
ipsec auto --add testnet
```
I dont get a message after that.

After this I type
```
ipsec auto --up testnet
```

and get following error:

```
whack: Pluto is not running (no "/var/run/pluto/pluto.ctl")
```

Pluto is not running?!

I type 
```
ipsec setup --status
```

and get this errors (the rest ist OK):

```
NETKEY detected, testing for disabled ICMP send_redirects [FAILED]
Please disable /proc/sys/net/ipv4/conf/*/send_redirects!
or NETKEY will cause the sending of bogus ICMP redirects!

NETKEY detected, testing for disabled ICMP accept_redirects [FAILED]
Please disable /proc/sys/net/ipv4/conf/*/accept_redirects!
or NETKEY will cause the sending of bogus ICMP redirects!

Checking for RSA private key (/etc/ipsec.secrets) [DISABLED]
hostname: Unknown host
ipsec showhostkey: no default key in "/etc/ipsec.secrets"

Checking that pluto is running [FAILED]
whack: Pluto is not running (no "/var/run/pluto/pluto.ctl")

Opportunistic Encryption Support [DISABLED]

```

oh my god, can anyone help me? 

:confused:

---

