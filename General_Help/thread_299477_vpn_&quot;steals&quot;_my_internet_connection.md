---
title: "vpn &quot;steals&quot; my internet connection"
date: 2006-11-14
forum: General Help
---

### Post by harty83 on 2006-11-14
I have two vpns I use regularly.  One is an openvpn connection to my home server.  I also pptp to connect to my work server.  I user network-manager to interface both of them.  Both VPNs work fine.  I can get into both workgroups and do whatever I need with any of the pcs in them.  

My problem is that when I am connected to one of the vpns, I can not surf the internet.  It seems that everything is directed through the tunnel.  So, what do I need to do so that I can connect to my vpn server and access files on the vpn server, but yet still be able to surf the net, check my email, etc on my client?

Thanks!
Alan

---

### Post by marianom on 2006-11-14
I assume that the one that steals your connection is the pptp? is it right?

---

### Post by johnnymac on 2006-11-14
It sounds like you need to specify your own routing and use Client-To-LAN tunneling.  If I were you I'd check out this link:

[http://pptpclient.sourceforge.net/routing.phtml](http://pptpclient.sourceforge.net/routing.phtml)

That should show you any and every possible scenario you could want.

---

### Post by harty83 on 2006-11-14
> **marianom said:**
> I assume that the one that steals your connection is the pptp? is it right?

Actually both openvpn and pptp steal it.

---

### Post by darrenm on 2006-11-14
Dont know much about pptp but in openvpn the server has config options for redirect-gateway and push dns, both of which will lose your internet connection in different ways.

When you are connected to openvpn check the routing table
```
route
``` and see if the default gateway is now going through the VPN adapter.

If not then your /etc/resolv.conf file may be being changed. Check the nameservers in there before and after connecting to the VPN.

Either way you should be able to put options in /etc/dhcp3/dhclient.conf to use your own settings for the gateway and the DNS server. The section ```
#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}

``` should explain all.

---

### Post by marianom on 2006-11-14
Regarding pptp i'm with johnnymac: you might have All to Tunel in Routing Style, you need to change it.

Regarding openvpn, there's a conf parameter in the server that directos all your traffic through the vpn: push "redirect-gateway". It should be commented to prevent this. I quote de conf file:

```
# If enabled, this directive will configure
# all clients to redirect their default
# network gateway through the VPN, causing
# all IP traffic such as web browsing and
# and DNS lookups to go through the VPN
# (The OpenVPN server machine may need to NAT
# the TUN/TAP interface to the internet in
# order for this to work properly).
# CAVEAT: May break client's network config if
# client's local DHCP server packets get routed
# through the tunnel.  Solution: make sure
# client's local DHCP server is reachable via
# a more specific route than the default route
# of 0.0.0.0/0.0.0.0.
;push "redirect-gateway"


```

---

### Post by harty83 on 2006-11-14
Okay I got pptp to work correctly by unchecking "Use Peer DNS", "Exclusive Device Lock", "Peer DNS through Tunnel" in network manager.

In my openvpn server.conf, I have 'push "redirect-gateway"' already commented out.  

I'll try darrenm's suggestion and post back.

---

### Post by harty83 on 2006-11-14
Before connected to openvpn

```
alan@hartyslaptop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.30.211.0     *               255.255.255.0   U     0      0        0 eth1
default         10.30.211.1     0.0.0.0         UG    0      0        0 eth1

```

After
```

alan@hartyslaptop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
70.110.15.152   10.30.211.1     255.255.255.255 UGH   0      0        0 eth1
10.30.211.0     *               255.255.255.0   U     0      0        0 eth1
default         *               0.0.0.0         U     0      0        0 tun0

```

So the default is through my vpn (tun0). So I'm a bit confused as to what to do now.  Do I want it this way or not to get internet browsing to work with openvpn?

If not, then what do I do?

Like I said before, push "redirect-gateway" is already commented out in my openvpn server.conf.

---

### Post by NorthCoast on 2006-11-14
In your case I'd say turn off the route.  You usually only want to route to the host/subnet of the remote net.  Normal internet for everything else.

A nice feature is creating several profiles so that in a case where you *do* want to default route via the other end you can do so.  I had this case when my ISP had a few bad weeks and their routing was really bad to many places.  The routing was fine to the VPN endpoint so I defaulted that way until the ISP fixed thir problem.  Another reason is when you're out in the countryside and need Inet via a random wireless connection, VPN across the unencrypted wireless and stay safe....

---

### Post by harty83 on 2006-11-14
> **NorthCoast said:**
> In your case I'd say turn off the route.  You usually only want to route to the host/subnet of the remote net.  Normal internet for everything else.

A nice feature is creating several profiles so that in a case where you *do* want to default route via the other end you can do so.  I had this case when my ISP had a few bad weeks and their routing was really bad to many places.  The routing was fine to the VPN endpoint so I defaulted that way until the ISP fixed thir problem.  Another reason is when you're out in the countryside and need Inet via a random wireless connection, VPN across the unencrypted wireless and stay safe....

Problem is, I don't know how to turn off the route through openvpn.  From what I am reading, I should comment out push "redirect-gateway" in the server conf but that does not seem to be working. Do you think I need to something client side?

I would be okay with routing through my home server IF I could get that to work.  But when I uncomment push "redirect-gateway," I still can't browse the internet.

I have 
```
-A INPUT -i tun+ -j ACCEPT
-A FORWARD -i tun+ -j ACCEPT

```
in my servers iptable's firewall so it should be rerouting okay right?

I'm at a loss.

---

### Post by darrenm on 2006-11-14
Aha no. You need to masquerade it to the net. When the router at the server end sees packets from 10.8.0.0 (or whatever your VPN subnet is) it doesnt know where to route them back so you have to masquerade the packets which means the kernel will rewrite the source IP as the IP of the server.

something like

```
iptables -A INPUT -p udp --dport 1194 -j ACCEPT
iptables -A INPUT -i tun+ -j ACCEPT
iptables -A FORWARD -i tun+ -j ACCEPT
iptables -A INPUT -i tap+ -j ACCEPT
iptables -A FORWARD -i tap+ -j ACCEPT 
iptables -t nat -A POSTROUTING -s 10.8.0.0/24 -o eth0 -j MASQUERADE
```

But that's not the crux of the problem. With redirect-gateway commented you shouldn't have the gateway redirected.
You can just do a 
```
route del default gw dev tun0 && route add default gw 10.30.211.1
``` as soon as the VPN is connected by putting it in a script to run the VPN or something

but your routing table isnt right anyway - If you remove the default gw then nothing will go through the VPN as you dont have a route at all to it.

If you can post your openvpn server.conf and client.conf files (removing IP's if you like) I can have a look?

---

### Post by koenn on 2006-11-14
> I have
Code:

-A INPUT -i tun+ -j ACCEPT -A FORWARD -i tun+ -j ACCEPT

in my servers iptable's firewall so it should be rerouting okay right?
no, this tells your iptables firewall to allow traffic trough the tunnel.


possible sollution:
note how, after you start vpn, the final statement of your routing table says "everthing that does not match previus routes : send it through the tunnel". 

to light want to try
-add a route to the lan you want to conevct to, and then
-send everything else 'through eth1', or through your internetrouter - Not through the tunnel. 

you need the 'route command', something like
route add -net xxx.xxx.xxx.xxx tun0
route add default gw yyy.yyy.yyy.yyy.
route add -net 000.000.000.000 gw yyy.yyy.yyy.yyy

route --help or man route will show you exact syntax etc - my examples may be slightly incorrect.

---

### Post by harty83 on 2006-11-14
> **darrenm said:**
> 
but your routing table isnt right anyway - If you remove the default gw then nothing will go through the VPN as you dont have a route at all to it.

If you can post your openvpn server.conf and client.conf files (removing IP's if you like) I can have a look?

thanks!

server.conf

```
################################################
# Sample OpenVPN 2.0 config file for            #
# multi-client server.                          #
#                                               #
# This file is for the server side              #
# of a many-clients <-> one-server              #
# OpenVPN configuration.                        #
#                                               #
# OpenVPN also supports                         #
# single-machine <-> single-machine             #
# configurations (See the Examples page         #
# on the web site for more info).               #
#                                               #
# This config should work on Windows            #
# or Linux/BSD systems.  Remember on            #
# Windows to quote pathnames and use            #
# double backslashes, e.g.:                     #
# "C:\\Program Files\\OpenVPN\\config\\foo.key" #
#                                               #
# Comments are preceded with '#' or ';'         #
#################################################

# Which local IP address should OpenVPN
# listen on? (optional)
;local a.b.c.d

# Which TCP/UDP port should OpenVPN listen on?
# If you want to run multiple OpenVPN instances
# on the same machine, use a different port
# number for each one.  You will need to
# open up this port on your firewall.
port 1194

# TCP or UDP server?
proto tcp
;proto udp

# "dev tun" will create a routed IP tunnel,
# "dev tap" will create an ethernet tunnel.
# Use "dev tap" if you are ethernet bridging.
# If you want to control access policies
# over the VPN, you must create firewall
# rules for the the TUN/TAP interface.
# On non-Windows systems, you can give
# an explicit unit number, such as tun0.
# On Windows, use "dev-node" for this.
# On most systems, the VPN will not function
# unless you partially or fully disable
# the firewall for the TUN/TAP interface.
;dev tap0
dev tun

# Windows needs the TAP-Win32 adapter name
# from the Network Connections panel if you
# have more than one.  On XP SP2 or higher,
# you may need to selectively disable the
# Windows firewall for the TAP adapter.
# Non-Windows systems usually don't need this.
;dev-node MyTap

# SSL/TLS root certificate (ca), certificate
# (cert), and private key (key).  Each client
# and the server must have their own cert and
# key file.  The server and all clients will
# use the same ca file.
#
# See the "easy-rsa" directory for a series
# of scripts for generating RSA certificates
# and private keys.  Remember to use
# a unique Common Name for the server
# and each of the client certificates.
#
# Any X509 key management system can be used.
# OpenVPN can also use a PKCS #12 formatted key file
# (see "pkcs12" directive in man page).
ca /etc/openvpn/easy-rsa/keys/ca.crt
cert /etc/openvpn/easy-rsa/keys/server.crt
key /etc/openvpn/easy-rsa/keys/server.key  # This file should be kept secret

# Diffie hellman parameters.
# Generate your own with:
#   openssl dhparam -out dh1024.pem 1024
# Substitute 2048 for 1024 if you are using
# 2048 bit keys. 
dh /etc/openvpn/easy-rsa/keys/dh1024.pem

# Configure server mode and supply a VPN subnet
# for OpenVPN to draw client addresses from.
# The server will take 10.8.0.1 for itself,
# the rest will be made available to clients.
# Each client will be able to reach the server
# on 10.8.0.1. Comment this line out if you are
# ethernet bridging. See the man page for more info.
server 10.8.0.0 255.255.255.0

# Maintain a reOBcord of client <-> virtual IP address
# associations in this file.  If OpenVPN goes down or
# is restarted, reconnecting clients can be assigned
# the same virtual IP address from the pool that was
# previously assigned.
ifconfig-pool-persist ipp.txt

# Configure server mode for ethernet bridging.
# You must first use your OS's bridging capability
# to bridge the TAP interface with the ethernet
# NIC interface.  Then you must manually set the
# IP/netmask on the bridge interface, here we
# assume 10.8.0.4/255.255.255.0.  Finally we
# must set aside an IP range in this subnet
# (start=10.8.0.50 end=10.8.0.100) to allocate
# to connecting clients.  Leave this line commented
# out unless you are ethernet bridging.
;server-bridge 192.168.1.5 255.255.255.0 192.168.1.10 192.168.1.15

# Push routes to the client to allow it
# to reach other private subnets behind
# the server.  Remember that these
# private subnets will also need
# to know to route the OpenVPN client
# address pool (10.8.0.0/255.255.255.0)
# back to the OpenVPN server.
;push "route 192.168.1.0 255.255.255.0"
;push "route 192.168.20.0 255.255.255.0"

# To assign specific IP addresses to specific
# clients or if a connecting client has a private
# subnet behind it that should also have VPN access,
# use the subdirectory "ccd" for client-specific
# configuration files (see man page for more info).

# EXAMPLE: Suppose the client
# having the certificate common name "Thelonious"
# also has a small subnet behind his connecting
# machine, such as 192.168.40.128/255.255.255.248.
# First, uncomment out these lines:
;client-config-dir ccd
;route 192.168.40.128 255.255.255.248
# Then create a file ccd/Thelonious with this line:
#   iroute 192.168.40.128 255.255.255.248
# This will allow Thelonious' private subnet to
# access the VPN.  This example will only work
# if you are routing, not bridging, i.e. you are
# using "dev tun" and "server" directives.

# EXAMPLE: Suppose you want to give
# Thelonious a fixed VPN IP address of 10.9.0.1.
# First uncomment out these lines:
;client-config-dir ccd
;route 10.9.0.0 255.255.255.252
# Then add this line to ccd/Thelonious:
#   ifconfig-push 10.9.0.1 10.9.0.2

# Suppose that you want to enable different
# firewall access policies for different groups
# of clients.  There are two methods:
# (1) Run multiple OpenVPN daemons, one for each
#     group, and firewall the TUN/TAP interface
#     for each group/daemon appropriately.
# (2) (Advanced) Create a script to dynamically
#     modify the firewall in response to access
#     from different clients.  See man
#     page for more info on learn-address script.
;learn-address ./script

# If enabled, this directive will configure
# all clients to redirect their default
# network gateway through the VPN, causing
# all IP traffic such as web browsing and
# and DNS lookups to go through the VPN
# (The OpenVPN server machine may need to NAT
# the TUN/TAP interface to the internet in
# order for this to work properly).
# CAVEAT: May break client's network config if
# client's local DHCP server packets get routed
# through the tunnel.  Solution: make sure
# client's local DHCP server is reachable via
# a more specific route than the default route
# of 0.0.0.0/0.0.0.0.
;push "redirect-gateway def1" 

# Certain Windows-specific network settings
# can be pushed to clients, such as DNS
# or WINS server addresses.  CAVEAT:
# http://openvpn.net/faq.html#dhcpcaveats
;push "dhcp-option DNS 10.8.0.1"
;push "dhcp-option WINS 10.8.0.1"

# Uncomment this directive to allow different
# clients to be able to "see" each other.
# By default, clients will only see the server.
# To force clients to only see the server, you
# will also need to appropriately firewall the
# server's TUN/TAP interface.
;client-to-client

# Uncomment this directive if multiple clients
# might connect with the same certificate/key
# files or common names.  This is recommended
# only for testing purposes.  For production use,
# each client should have its own certificate/key
# pair.
#
# IF YOU HAVE NOT GENERATED INDIVIDUAL
# CERTIFICATE/KEY PAIRS FOR EACH CLIENT,
# EACH HAVING ITS OWN UNIQUE "COMMON NAME",
# UNCOMMENT THIS LINE OUT.
;duplicate-cn

# The keepalive directive causes ping-like
# messages to be sent back and forth over
# the link so that each side knows when
# the other side has gone down.
# Ping every 10 seconds, assume that remote
# peer is down if no ping received during
# a 120 second time period.
keepalive 10 120

# For extra security beyond that provided
# by SSL/TLS, create an "HMAC firewall"
# to help block DoS attacks and UDP port flooding.
#
# Generate with:
#   openvpn --genkey --secret ta.key
#
# The server and each client must have
# a copy of this key.
# The second parameter should be '0'
# on the server and '1' on the clients.
;tls-auth ta.key 0 # This file is secret

# Select a cryptographic cipher.
# This config item must be copied to
# the client config file as well.
;cipher BF-CBC        # Blowfish (default)
;cipher AES-128-CBC   # AES
;cipher DES-EDE3-CBC  # Triple-DES

# Enable compression on the VPN link.
# If you enable it here, you must also
# enable it in the client config file.
comp-lzo

# The maximum number of concurrently connected
# clients we want to allow.
;max-clients 100

# It's a good idea to reduce the OpenVPN
# daemon's privileges after initialization.
#
# You can uncomment this out on
# non-Windows systems.
;user nobody
;group nogroup

# The persist options will try to avoid
# accessing certain resources on restart
# that may no longer be accessible because
# of the privilege downgrade.
persist-key
persist-tun

# Output a short status file showing
# current connections, truncated
# and rewritten every minute.
status openvpn-status.log

# By default, log messages will go to the syslog (or
# on Windows, if running as a service, they will go to
# the "\Program Files\OpenVPN\log" directory).
# Use log or log-append to override this default.
# "log" will truncate the log file on OpenVPN startup,
# while "log-append" will append to it.  Use one
# or the other (but not both).
;log         openvpn.log
;log-append  openvpn.log

# Set the appropriate level of log
# file verbosity.
#
# 0 is silent, except for fatal errors
# 4 is reasonable for general usage
# 5 and 6 can help to debug connection problems
# 9 is extremely verbose
verb 3

# Silence repeating messages.  At most 20
# sequential messages of the same message
# category will be output to the log.
;mute 20


```

client.conf

```
client
dev tun
proto tcp
remote my-ip.com
resolv-retry infinite
nobind
persist-key
persist-tun
ca /etc/openvpn/keys/ca.crt
cert /etc/openvpn/keys/laptop_kubuntu.crt
key /etc/openvpn/keys/laptop_kubuntu.key
comp-lzo
verb 3
port 1194

```

---

### Post by darrenm on 2006-11-15
It all looks fine, cant see why it isnt adding the routes on your client. Do you run the openvpn client as root?

---

### Post by harty83 on 2006-11-15
> **darrenm said:**
> It all looks fine, cant see why it isnt adding the routes on your client. Do you run the openvpn client as root?

Yup,

```
sudo openvpn /etc/openvpn/client.conf
```

---

### Post by harty83 on 2006-11-15
When I added this to my iptables file

```
-t nat -A POSTROUTING -s 10.8.0.0/24 -o eth0 -j MASQUERADE
```

my network will not come up because it says there is an error.  It won't say exactly what.

Is the syntax correct?

---

### Post by balaji.ramasubramanian on 2008-01-18
Dudes,

Please help. I am a n00b. I only used the configuration file that my company gave me and configured my VPN. I had to install all the following:
vpnc, openvpn, pptp, network-manager-vpnc, network-manager-openvpn, network-manager-pptp etc. I removed resolvconf because it seems to interfere with my network manager's VPN connections. 

I am able to connect to VPN and browse the intranet of my company, but I can't browse normal internet. 

Recently I found that if I specify a proxy server, I can browse external websites, but I can't check gmail or personal mails for example. My company shuts off that traffic. 

When I see these comments here, I don't know what files you are talking about here. I checked the following files:

/etc/openvpn/update-resolv-conf
/etc/resolv.conf
/etc/pptpd.conf
/etc/vpnc/iec.conf

I don't know if there are any other config files. Can you please help?

Please give me complete instructions with full path of files. I can give you the files if you need. But please mention the exact files you want and where I can find them.

---

### Post by balaji.ramasubramanian on 2008-01-18
I don't have a file by the name server.conf in the first place:

$ find /etc -name "server.conf"
find: /etc/cups/ssl: Permission denied
find: /etc/lvm/cache: Permission denied
find: /etc/skel/.gnome2: Permission denied
find: /etc/skel/.kde: Permission denied
find: /etc/ssl/private: Permission denied
find: /etc/vpnc: Permission denied

sudo find /etc -name "server.conf"
[sudo] password for blackmaster:


Clearly the file does not exist in my case! What is going on? How does my VPN connect? Is there a log file for network-manager? Where are log files usually kept? How do I debug this?

---

### Post by lucidblue on 2008-02-01
> **darrenm said:**
> It all looks fine, cant see why it isnt adding the routes on your client. Do you run the openvpn client as root?

My config files look the same, and the same happens to me.  Personally, I think the issue has something to do with me using it inside my lan.  there's no IP conflict, because I've got it setup with 10.x.x.x for the vpn, but after connecting, I lose internet on the laptop.

The client is XP Home (the wife's) with linux server.  I'm using the openvpn gui for windows on the client, I can even connect fine from work to home, and internet connection will persist.

I haven't been able to try connecting the laptop from work or anywhere "out side" the lan, but I have a cheap router that for some reason decides on it's own to block ports between wired and wireless traffic, so I wanted this to just always connect, so I can bypass that...

Any one figure this out yet, or have any ideas?

--Lucidblue

---

### Post by kultex on 2008-02-01
@harty83

> **harty83 said:**
> Okay I got pptp to work correctly by unchecking "Use Peer DNS", "Exclusive Device Lock", "Peer DNS through Tunnel" in network manager.


I have the same problem like you had - I unchecked all three points, but still all traffic goes through the tunnel - as soon as I choose under Routing "Only use VPN connection for theses addresses" and add just one number - the apply butten is not any more available. I thought, this can help, but is not possible - did you do something else?

---

### Post by wired00 on 2008-04-15
Hi There,

this is my first post in the forums so Hi :)

anyway I've been getting pretty frustrated with this for most of the day now... i just finally found a solution although it seems temporary... anyway...

I had exactly the same issues, connect to my work VPN and lose internet connection.

I found a solution by unchecking the following from the "VPN Connections" gui accessable by clicking the networking icon: "Use Peer DNS", "Exclusive Device access (UUCP-style lock) - PPP options tab, and "Peer DNS Through tunnel" - Routing tab.

I ran:
```
route
``` and saw the following :

```

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

```

You can see my default gateway is 192.168.1.1 which is great for eth0 and it works. **But** after connecting to the VPN it changes to this:

```

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
<blah.net> 192.168.1.1     255.255.255.255 UGH   0      0        0 eth0
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         *               0.0.0.0         U     0      0        0 ppp0

```
* NOTE: i've changed the domain to <blah.net>

As you can see after connecting, the default gateway for ppp0 (vpn tunnel) changes to * im not entirely sure what this means (??) but i know its wrong. 

so i run:
```
sudo route del default
``` to remove that default entry (im not sure if this is necessary though because it should try using all possible default gateways?

i then run:
```
sudo route add default gw 192.168.1.1
``` which adds the same default gateway from my eth0 connection before connecting to VPN. 

Huzzah, it should now work. **BUT** as soon as you disconnect then reconnect to VPN the  network GUI resets the default gateway again :( im trying to figure this out now...anyone have a solution?

i originally read to add "sudo route add default gw 192.168.1.1" to /etc/rc.local but of course this is overwritten as soon as you connect to VPN : /

anyone?

i can't believe VPN like this are listed as "LOW" priority under the bug forum. I bet i know why though, its because everyone feels "Oh it can be done from the command prompt, why use the gui?" rar rar. I think far more priority should go into GUI issues... Ex or current windows and MAC users are 99.9% used to GUI's not shell... it really grates me!

---

### Post by wired00 on 2008-04-16
grrr sorry ignore my post above. once you do "route add default gw 192.168.1.1" it kills the vpn access :( Still trying to find a fix

---

### Post by wired00 on 2008-04-16
finally got it working ...

entering "192.168.12.0/24" into the "Only use VPN connection for these addresses" fixed it right away and resulted in this route once i connect...

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
<domain> 192.168.1.1     255.255.255.255 UGH   0      0        0 eth0
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
192.168.12.0    *               255.255.255.0   U     0      0        0 ppp0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

```

there was a gui bug with the "only use VPN connection for these addresses".  It seemed to disable the "APPLY" button until i'd entered "192.168.12.0/24" I assume it has auto validation and only enables the "APPLY" button when the IP address is correct.

---

