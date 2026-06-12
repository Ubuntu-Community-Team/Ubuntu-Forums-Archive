---
title: "Will using iptables secure Ubuntu?"
date: 2020-06-01
forum: General Help
---

### Post by aboka on 2020-06-01
hi, just starting to learn Ubuntu and hv install the latest 20.04 on a vps along with Softether and everything is running fine.

Will iptables help secure a vps? It should be able to help, since what i understand iptables is actually the firewall

Where could we learn the basics like add/edit/delete iptables rules? hv read the help on ubuntu.com(and some others) but not too confident to try them out as might get lockout fr the vps if done something wrong :/

p/s - just need to learn the basics setup like adding loopback, ssh, etc for the vps to run correctly beside adding some more rules for the vpnserver

thank you,

---

### Post by SeijiSensei on 2020-06-01
First, out of the box, Ubuntu has no services that listen on ports.  So it's largely invulnerable to most attacks.

Does the machine present a publicly-visible interface?  Does anyone other than you need to connect to it at all?  If not, a really simple firewalling scheme would be 
```

/sbin/iptables -P INPUT -j DROP
/sbin/iptables -A INPUT -s your.local.ip.addr -d your.server.ip.addr -j ACCEPT

```
The first line drops all incoming packets that don't match a rule. The second rule allows packets from your local machine at your.local.ip.addr.

---

### Post by aboka on 2020-06-01
> **SeijiSensei said:**
> First, out of the box, Ubuntu has no services that listen on ports.  So it's largely invulnerable to most attacks.

Does the machine present a publicly-visible interface?  Does anyone other than you need to connect to it at all?  If not, a really simple firewalling scheme would be 
```

/sbin/iptables -P INPUT -j DROP
/sbin/iptables -A INPUT -s your.local.ip.addr -d your.server.ip.addr -j ACCEPT

```
The first line drops all incoming packets that don't match a rule. The second rule allows packets from your local machine at your.local.ip.addr.


hi, thanks for the reply. im the only one accessing the vps using ssh. here are the list of open ports utilize currently -
1194 vpnserver
5555 vpnserver
443 vpnserver
22 sshd
53 dnsmasq

do we need to add the loopback since i read lotsa program need that to work. and putting the 'drop all' at the top is ok?

yeah, forget to mention, i already hv one entry fr the vpnserver installation -
iptables -t nat -L
Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination
SNAT       all  --  192.168.7.0/24       anywhere             to:103.125.207.43

and lastly, my local ip is 192.168.7.1? i use dnsmasq to give out the ip address -
ip -address
inet 192.168.7.1/24 brd 192.168.7.255 scope global tap_soft

regards,

---

### Post by SeijiSensei on 2020-06-01
First, about the localhost address.  Yes, I forgot to exempt it in the rules above.  It's easier to write a rule that exempts the "lo" interface like this:

```

/sbin/iptables -P INPUT -j DROP
/sbin/iptables -A INPUT -i lo -j ACCEPT
/sbin/iptables -A INPUT -s your.local.ip.addr -d your.server.ip.addr -j ACCEPT

```

"your.local.ip.addr" is not one in the private 192.168.7.0/24 network behind your router.  It is your public IP address on the "WAN" side of your router.  If you don't know what that is, you can visit whatismyip.com.  While providers use DHCP to distribute addresses, meaning your address could change at any time, in practice many addresses remain functionally static.  I've had the same public IP for months now.  

As I said, if you're the only one connecting to this server, then you need only exempt your address.  However if you are supporting other people connecting to those ports, then you'd need specific rules.

1194 is the default port for OpenVPN, but you have two other ports listed as well, 5555 and 443.  OpenVPN should be listening on only one of those ports unless you have multiple VPN tunnels set up with other users.  443 is a bit surprising since it's the default for HTTPS connections.  Are you running a webserver listening on that port?  If you were, then you'd need another rule like
```

/sbin/iptables -A INPUT -p tcp -d your.server.ip.addr --dport 443 -j ACCEPT

```

The SNAT masquerading rule doesn't enter into any of this.  It just tells the machine to send all outbound traffic as if it were coming from 103.125.207.43.

---

### Post by TheFu on 2020-06-01
Firewalls aren't the only part to running a secure system, thought they are extremely important.
[LIST]
[*]Don't use passwords for authentication, use keys. Especially for ssh.
[*]Don't run unnecessary services.
[*]Don't allow the world access to any services they have no business using.
[*]Stay patched.
[*]Don't leave development or hacking tools on the system once it is used for production.
[*]Have daily, automatic, versioned, backups that are stored on a different system.  Backups have 1,001 uses, including a way to figure out what happened **AFTER** you get hacked.
[/LIST]

You are asking and doing all the right stuff so far.  Be aware that firewall interfaces are changing on other distros, so iptables isn't the only interface into the Linux kernel firewall.

i don't get why you'd run a DNS server on the internet.  i've been hacked 3 times since 1993.   One of those was via DNS in 2002.  Since then, i pay someone else to run my DNS for public services and only use my DNS servers for internal use.

---

### Post by aboka on 2020-06-02
hi, am reading lotsa info online rgd this and i think i will write the rules base on that and your advice here tomorrow. will post back here before applying them on the vps

p/s - will omit the lo(loopback) now and only add it if something not working. as first it wont lock me out, and second the rule is, the less the safer right?

cheers,

---

### Post by aboka on 2020-06-02
p/ss- Softether is using 4 ports by default 443, 992, 1194 & 5555. and 500 & 4500 if using L2TP, MS-SSTP etc. but i hv deleted 992 as read on couple sites saying it is'useless'

---

### Post by TheFu on 2020-06-02
We usually don't abbreviate common words here that aren't common technical terms. Clarity is important.

Be certain you know how to access the console on the VPS before doing too much with the firewall.  Some people setup a "try mode" that enables the firewall for 5 minutes, then disables it. That provides the needed time to ensure it is working, but a way to get back in without console access if the rules are bad.  Good habit to get into. After the initial setup, it is those "quick changes" next month where we humans can lock ourselves out.  I've done it, but always ensure I have console access.

I think you should always allow all lo traffic. Unix systems commonly use network sockets for IPC (interprocess communications), rather than using the other methods like shared memory.  Any 127.x.x.x/8 should be allowed.  You'll see 127.0.0.53 used or 127.1.53.1, these all resolve to "localhost", but provide effectively unlimited IPs and ports for local uses.

---

### Post by aboka on 2020-06-02
> **TheFu said:**
> Firewalls aren't the only part to running a secure system, thought they are extremely important.
[LIST]
[*]Don't use passwords for authentication, use keys. Especially for ssh.
[*]Don't run unnecessary services.
[*]Don't allow the world access to any services they have no business using.
[*]Stay patched.
[*]Don't leave development or hacking tools on the system once it is used for production.
[*]Have daily, automatic, versioned, backups that are stored on a different system. Backups have 1,001 uses, including a way to figure out what happened **AFTER** you get hacked.
[/LIST]

You are asking and doing all the right stuff so far. Be aware that firewall interfaces are changing on other distros, so iptables isn't the only interface into the Linux kernel firewall.

i don't get why you'd run a DNS server on the internet. i've been hacked 3 times since 1993. One of those was via DNS in 2002. Since then, i pay someone else to run my DNS for public services and only use my DNS servers for internal use.


hi, the ultimate goal is to secure the whole vps, will do the rest of what you suggest after done with iptables.

I suppose you are talking about the dnsmasq when you say 'dns server on the internet'? im also curios why it is exposed. I install all this by following an online guideand the the reason to install dnsmasq is for assigning IPs(as DHCP server) to the connected vpn users. What I understand, a DHCP server should be working offline inside the network and not expose to the WAN. So what do you think? Am i doing it wrong and is there a 'real dhcp server' that i could use?

and you suggest we add the localhost to the iptables as a precaution right? how do we do that? like this-
iptables -A INPUT -i [COLOR=#000000]127.x.x.x/8[/COLOR] -j ACCEPT

thank you,

---

### Post by TheFu on 2020-06-02
Securing a server isn't just a checklist. It takes smarts to think about all the different attack methods possible and restrict access for any of those attacks for only the people who need access.  There's always more that can be done. It takes many years to learn, decades to understand, longer to become an expert.  

I don't use iptables on my application servers enough to know the syntax off the top of my head. My network is protected using pf on BSD.  I would guess that 127.x.x.x/8 should be 127.0.0.0/8. Most subnetting doesn't like letters.

I segment my services onto different VMs and different containers where there is any chance of conflicting software stacks.

Open ports as seen on the server are always different than open ports seen from outside.  Plus, these days we need to check both IPv4 and IPv6 networking.  In my networks, we still disable IPv6 for now. We aren't ready for it and don't have any driving need to switch, though some CAs have changed some things and our renewals seem to be having issues since we don't have IPv6 AAAA records.

---

### Post by aboka on 2020-06-03
@TheFu - for the localhost, i will just use what @SeijiSensei suggest as i find out localhost is the same as loopback.

Can you pls explain this - 'Open ports as seen on the server are always different than open ports seen from outside' like how do we check if the port are exposed to the world?

read an article yerterday saying that dnsmasq is actually DNS+DHCP so that might be the reason why it has an open port? hv also read about dhcpd. do you think dnsmasq will create a security risk since it has an open port and we should replace it with dhcpd?

thank you,

---

### Post by TheFu on 2020-06-03
The only way to see what the outside world sees is to run a port scan using an external address, not on the system. Use **nmap** for that.

On the same machine, we can ask netstat.
```
# Open ports with listeners, not localhost
$ ss -lnt|egrep -v 127
$ netstat -tunl|grep LISTEN|grep -v 127
$ sudo netstat -tulpn |grep LISTEN|grep -v 127
```
Note which need and don't need sudo.

---

### Post by aboka on 2020-06-03
> **TheFu said:**
> The only way to see what the outside world sees is to run a port scan using an external address, not on the system. Use **nmap** for that.

On the same machine, we can ask netstat.
```
# Open ports with listeners, not localhost
$ ss -lnt|egrep -v 127
$ netstat -tunl|grep LISTEN|grep -v 127
$ sudo netstat -tulpn |grep LISTEN|grep -v 127
```
Note which need and don't need sudo.

hi, thanks for the prompt reply :) could we do it on Windows or use web service like canyouseeme.org?

i just check on my Windows(while connected to the server using Softether vpn) and goto canyouseeme.org and it say 'Success: I can see your service on' on all the port here - 22, 53, 443, 1194, 5555

here is the result running the netstat command-
LISTEN   0        128              0.0.0.0:1194          0.0.0.0:*
LISTEN   0        128              0.0.0.0:5555          0.0.0.0:*
LISTEN   0        32               0.0.0.0:53            0.0.0.0:*
LISTEN   0        128              0.0.0.0:22            0.0.0.0:*
LISTEN   0        128              0.0.0.0:443           0.0.0.0:*

so do you think we need to replace the dnsmasq with dhcpd? or we could just block the port and not expose the port to the world. thank you.

---

### Post by aboka on 2020-06-03
Please take a look and see if this is ok, and if there is anything left out.

sudo iptables -A INPUT -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT   # for the current session
sudo iptables -A INPUT -i lo -j ACCEPT    # for loopback/localhost
sudo iptables -A INPUT -p icmp -j ACCEPT    # for ping response
sudo iptables -A INPUT -p tcp --dport ssh -j ACCEPT    # for ssh connection
sudo iptables -A INPUT -p tcp --dport 443 -j ACCEPT    # for vpn
sudo iptables -A INPUT -p all --dport 1194 -j ACCEPT    # for vpn and 'all' bcoz it could use both protocol
sudo iptables -A INPUT -p tcp --dport 5555 -j ACCEPT    # vpn
sudo iptables -A INPUT -j DROP    # drop everything not in the list above

thank you,

---

### Post by TheFu on 2020-06-03
Do you really want to try and manually setup all the stuff yourself?   There are a number of firewall script tools. CNF is one that is well-regarded and used by professionals: [https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-config-server-firewall-csf-on-ubuntu](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-config-server-firewall-csf-on-ubuntu)  Those instructions are from 2013, but iptables hasn't changed THAT much since then.  Looking through all the things CNF handles will give you some ideas for things missing.

UFW silently handles many things too, while being uncomplicated.

But if you want to have your own wheel, great!

---

### Post by aboka on 2020-06-03
> **TheFu said:**
> Do you really want to try and manually setup all the stuff yourself?   There are a number of firewall script tools. CNF is one that is well-regarded and used by professionals: [https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-config-server-firewall-csf-on-ubuntu](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-config-server-firewall-csf-on-ubuntu)  Those instructions are from 2013, but iptables hasn't changed THAT much since then.  Looking through all the things CNF handles will give you some ideas for things missing.

UFW silently handles many things too, while being uncomplicated.

But if you want to have your own wheel, great!

hi, thanks for the suggestion and it really sounds great with so many protections. but think will just stick with iptables for now as it is the 'default'. perhaps will 'upgrade' to it after all is done.

cheers,

---

### Post by TheFu on 2020-06-03
> **aboka said:**
> hi, thanks for the suggestion and it really sounds great with so many protections. but think will just stick with iptables for now as it is the 'default'. perhaps will 'upgrade' to it after all is done.

cheers,

Sorry. Perhaps i wasn't clear.   iptables is still used.  CNF is just a script to create the iptables rules.  CNF handles all the things you and i don't remember or don't know are necessary for a more secure firewall.  it puts them in the correct order and addresses abusive connections.

it is very common for a script to make a script in the Unix world.  i write scripts that make scripts a few times every week.

But there's nothing wrong with learning the ugly parts yourself either.  That helps to get the lower level knowledge so later you can concentrate on getting the solution solved, better, faster, easier.

Also, UFW sets up iptables rules too.  UFW is the ubuntu standard tool, but there are times when dropping down to iptables is necessary.  Ufw is just a little too lite sometimes.   CNF isn't, though both allow adding direct iptables rules when needed.

---

### Post by aboka on 2020-06-03
@TheFu thanks for explaining that. Will try out the iptables and then decide if wanna try ConfigServer. It is great looking at all the things it could do, but it is just little overwhelming, especially now. Could you let me know if the rules below are ok? Thank you very much

[COLOR=#000000]sudo iptables -A INPUT -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT # for the current session[/COLOR]
[COLOR=#000000]sudo iptables -A INPUT -i lo -j ACCEPT # for loopback/localhost[/COLOR]
[COLOR=#000000]sudo iptables -A INPUT -p icmp -j ACCEPT # for ping response[/COLOR]
[COLOR=#000000]sudo iptables -A INPUT -p tcp --dport ssh -j ACCEPT # for ssh connection[/COLOR]
[COLOR=#000000]sudo iptables -A INPUT -p tcp --dport 443 -j ACCEPT # for vpn[/COLOR]
[COLOR=#000000]sudo iptables -A INPUT -p all --dport 1194 -j ACCEPT # for vpn and 'all' bcoz it could use both protocol[/COLOR]
[COLOR=#000000]sudo iptables -A INPUT -p tcp --dport 5555 -j ACCEPT # vpn[/COLOR]
[COLOR=#000000]sudo iptables -A INPUT -j DROP # drop everything not in the list above

anything left out? and do we need FORWARD or OUTPUT rules?[/COLOR]

---

### Post by aboka on 2020-06-03
hi guys, i hv create another vps and hv applied the rules. here are the 'output' -

root@NY-UBUNTU-01:~# iptables -S
-P INPUT DROP
-P FORWARD DROP
-P OUTPUT ACCEPT
-A INPUT -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
-A INPUT -i lo -j ACCEPT
-A INPUT -p icmp -j ACCEPT
-A INPUT -p tcp -m tcp --dport 22 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 443 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 5555 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 1194 -j ACCEPT
-A INPUT -j DROP
-A OUTPUT -o lo -j ACCEPT

does it look ok?

thanks,

---

### Post by The Cog on 2020-06-03
Looks OK to me. But the "-A INPUT -j DROP" is redundant because your policy for undecided packets is to drop them anyway. It doesn't do any harm though, except that it makes it harder to add another ACCEPT clause on the fly.

---

### Post by aboka on 2020-06-03
> **The Cog said:**
> Looks OK to me. But the "-A INPUT -j DROP" is redundant because your policy for undecided packets is to drop them anyway. It doesn't do any harm though, except that it makes it harder to add another ACCEPT clause on the fly.

hi, @The Cog, thanks for inputting. im new on all this, so could u elaborate more  on '...makes it harder to add another ACCEPT clause on the fly'? i mean i could still add new rules to it right later? what will you suggest - to delete the rules, etc? but isnt thats 'to catch and drop anything not on the rules'?

thank you,

---

### Post by TheFu on 2020-06-03
> **aboka said:**
> @TheFu thanks for explaining that. Will try out the iptables and then decide if wanna try ConfigServer. It is great looking at all the things it could do, but it is just little overwhelming, especially now. Could you let me know if the rules below are ok? Thank you very much 

i don't feel qualified to say whether those rules are or are not sufficient.  it must be 15 yrs since i did anything directly w/ iptables that wasn't part of a recipe.  Sorry.  Most of the time, i use ufw. When that isn't sufficient i pull out a book read just enough to solve the issue and move on.  My router doesn't run Linux.

Good luck. Hope you solve it.

---

### Post by aboka on 2020-06-03
@TheFu it is ok and thanks for all the help and info :)

---

### Post by SeijiSensei on 2020-06-04
> **aboka said:**
> so could u elaborate more  on '...makes it harder to add another ACCEPT clause on the fly'?

If you were to run a command like
```
/sbin/iptables -A INPUT ...
```
after those other rules are in place, that command will fail because the "-A INPUT -j DROP" command will precede it. Without that directive, any additional ACCEPT statements will simply be treated as exceptions to the overall INPUT policy.

You can get around this limitation in some cases by using "-I INPUT" to put the added rule at the top of the chain. That might not be the correct place for it though.

As for forwarding, first off, Ubuntu like most modern distributions blocks the forwarding of packets between interfaces.  Without a change to the file /etc/sysctl.conf, the default forwarding policy is thus DENY.  If you enable packet forwarding in sysctl.conf, then you would need FORWARD rules to control which packets can be passed between interfaces.

I usually set the default OUTPUT policy to ACCEPT unless there's some specific reason not to.  Those cases are rare.

---

### Post by aboka on 2020-06-04
Thanks for all the info guys, will apply the rules listed earlier, tomorrow, and update you people :)

---

### Post by jmginer on 2020-06-05
You can also consider to install webmin, has a nice panel to manage de firewall.
[http://www.webmin.com/deb.html](http://www.webmin.com/deb.html)

---

### Post by ActionParsnip on 2020-06-05
Ubuntu listens on a lot of ports. It's why the "lo" interface is needed and is how services talk to each other. Spin up a VM with just the live CD and use netstat. Lots of things listening on lots of ports. It's used a lot

---

### Post by aboka on 2020-06-06
hi guys, not good as just apply the rules and i cant connect to the vpn now - vpn client cant connect to the vpn server. but i could connect to the server using ssh. here is the rules i hv applied-
sudo iptables -A INPUT -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
sudo iptables -A INPUT -i lo -j ACCEPT
sudo iptables -A INPUT -p icmp -j ACCEPT
sudo iptables -A INPUT -p tcp --dport ssh -j ACCEPT
sudo iptables -A INPUT -p tcp --dport 443 -j ACCEPT
sudo iptables -A INPUT -p tcp --dport 1194 -j ACCEPT
sudo iptables -A INPUT -p udp --dport 1194 -j ACCEPT
sudo iptables -A INPUT -p tcp --dport 5555 -j ACCEPT
sudo iptables -A INPUT -j DROP
sudo iptables -P INPUT DROP
sudo iptables -P FORWARD DROP

iptables-save > /etc/iptables/rules.v4  #saving the iptables then reboot the server

here is the rules.v4 file-
root@SG-UBUNTU-1:~# nano /etc/iptables/rules.v4  GNU nano 4.8                                                             /etc/iptables/rules.v4
# Generated by iptables-save v1.8.4 on Sun Jun  7 00:56:49 2020
*filter
:INPUT ACCEPT [0:0]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [142:22839]
-A INPUT -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
-A INPUT -i lo -j ACCEPT
-A INPUT -p icmp -j ACCEPT
-A INPUT -p tcp -m tcp --dport 22 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 443 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 1194 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 5555 -j ACCEPT
-A INPUT -p udp -m udp --dport 1194 -j ACCEPT
-A INPUT -j DROP
-A OUTPUT -o lo -j ACCEPT
COMMIT
# Completed on Sun Jun  7 00:56:49 2020
# Generated by iptables-save v1.8.4 on Sun Jun  7 00:56:49 2020
*nat
:PREROUTING ACCEPT [281:26125]
:INPUT ACCEPT [45:2700]
:OUTPUT ACCEPT [90:6340]
:POSTROUTING ACCEPT [90:6340]
-A POSTROUTING -s 192.168.7.0/24 -j SNAT --to-source 103.125.217.43
COMMIT
# Completed on Sun Jun  7 00:56:49 2020


what hv i done wrong? pls help....

p/s - when i use openvpn to connect it will prompt to login again and again, and if use softether client, it could connect but would not get IP fr the vpn server. so it seems like i could connect to the server but the issue might be forward or output? im not sure as im not experience, just what i hv observe

---

### Post by The Cog on 2020-06-06
That NAT stuff looks suspect to me. Try without that.

---

### Post by aboka on 2020-06-06
> **The Cog said:**
> That NAT stuff looks suspect to me. Try without that.

hi, are you saying to remove this line -A POSTROUTING -s 192.168.7.0/24 -j SNAT --to-source 103.125.217.43

it was add in the vpn setup guide. thank you.

---

### Post by aboka on 2020-06-07
ok guys, here is the latest update - i found and use a bash script from github([https://gist.github.com/cmdwhoami/b35606eadfdc81ff173942a9e2ba5214](https://gist.github.com/cmdwhoami/b35606eadfdc81ff173942a9e2ba5214)) and make minor modifications to suit the setup. the issue is the same as before - can only use ssh and ping, but vpn are not working - screen shot [http://ge.tt/7WuM9Q43](http://ge.tt/7WuM9Q43)


so i try change 'iptables -P INPUT DROP' to 'iptables -P INPUT ACCEPT' then everything seems to work. so the question are, why and how to fix this? would using 'ACCEPT' be less secure?

#!/bin/bash
#
#######################################################################
#      iptables rules
#######################################################################
#
# Flush current V4 polices
iptables -t nat -F
iptables -t mangle -F
iptables -F
iptables -X


# Set default chain policies
iptables -P OUTPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -P INPUT DROP


# Drop null packets
iptables -I INPUT -p tcp --tcp-flags ALL NONE -j DROP


# DROP syn-flood packets
iptables -I INPUT -p tcp ! --syn -m state --state NEW -j DROP


# DROP XMAS packets
iptables -I INPUT -p tcp --tcp-flags ALL ALL -j DROP


# Accept on localhost
iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT


# Accept on local network (optional)
iptables -A INPUT -s 192.168.7.1/24 -j ACCEPT
iptables -A OUTPUT -s 192.168.7.1/24 -j ACCEPT


# Accept incoming SSH (default)
iptables -I INPUT -p tcp --dport 22 -j ACCEPT


# Accept incoming SSH
#iptables -A INPUT -p tcp -s 55.55.55.55 -m tcp --dport 19780 -j ACCEPT
#iptables -A INPUT -p tcp -s 55.55.55.55 -m tcp --dport 19780 -j ACCEPT


# Accept incoming HTTPS for SoftEther (default)
iptables -A INPUT -p tcp --dport 443 -j ACCEPT


# Accept incoming OpenVPN
iptables -A INPUT -p udp --dport 1194 -j ACCEPT


# Accept incoming IPsec
#iptables -A INPUT -p udp --dport 500 -j ACCEPT
#iptables -A INPUT -p udp --dport 4500 -j ACCEPT


# Allow established sessions to receive traffic
iptables -A INPUT -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT

# Reply to PING
iptables -A INPUT -p icmp -j ACCEPT


# SNAT for vpn to work
iptables -t nat -A POSTROUTING -s 192.168.7.0/24 -j SNAT --to-source 103.125.217.43


#########################################
###      End of rules
#########################################

p/s - hvto put the snat else it would connect but no internet activity

---

### Post by SeijiSensei on 2020-06-07
What happened to 
```
sudo iptables -A INPUT -p tcp --dport 5555 -j ACCEPT
```

For OpenVPN, you may need both a [TCP]("https://openvpn.net/faq/why-does-openvpn-use-udp-and-tcp/") rule and a UDP rule. 

Try adding
```
iptables -A INPUT -p tcp --dport 1194 -j ACCEPT
```
after the UDP rule above.

If this still doesn't help, try adding this rule to the bottom of the INPUT chain:

```

iptables -A INPUT -j LOG

```
which will log all packets that don't fit an existing rule.  You can find the results in /var/log/kern.log.

---

### Post by aboka on 2020-06-07
> **SeijiSensei said:**
> What happened to 
```
sudo iptables -A INPUT -p tcp --dport 5555 -j ACCEPT
```

For OpenVPN, you may need both a [TCP]("https://openvpn.net/faq/why-does-openvpn-use-udp-and-tcp/") rule and a UDP rule. 

Try adding
```
iptables -A INPUT -p tcp --dport 1194 -j ACCEPT
```
after the UDP rule above.

If this still doesn't help, try adding this rule to the bottom of the INPUT chain:

```

iptables -A INPUT -j LOG

```
which will log all packets that don't fit an existing rule.  You can find the results in /var/log/kern.log.

hi, i add 5555 and also 53 as wanna add all of the open ports to test now and eliminate one by one after its working. i also add both udp and tcp to all the ports.

it is still not working so i enable logging. it got so many things in there so i just copy the last few lines i think is relevant -
Jun  7 21:56:29 SG-UBUNTU-1 kernel: [   27.933286] IN=eth0 OUT= MAC=00:16:3e:5c:e4:1b:40:01:7a:eb:7c:40:08:00 SRC=156.96.156.73 DST=103.125.217.43 LEN=40 TOS=0x00 PREC>
Jun  7 21:56:36 SG-UBUNTU-1 kernel: [   34.567521] IN=eth0 OUT= MAC=00:16:3e:5c:e4:1b:40:01:7a:eb:7c:40:08:00 SRC=157.245.81.162 DST=103.125.217.43 LEN=40 TOS=0x00 PRE>
Jun  7 21:56:47 SG-UBUNTU-1 kernel: [   46.167560] IN=tap_soft OUT= MAC=ff:ff:ff:ff:ff:ff:ca:4e:96:e2:2c:4f:08:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=305 TOS=0x00 PREC>
Jun  7 21:56:49 SG-UBUNTU-1 kernel: [   47.735651] IN=tap_soft OUT= MAC=ff:ff:ff:ff:ff:ff:ca:4e:96:e2:2c:4f:08:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=305 TOS=0x00 PREC>
Jun  7 21:56:50 SG-UBUNTU-1 kernel: [   49.303715] IN=tap_soft OUT= MAC=ff:ff:ff:ff:ff:ff:ca:4e:96:e2:2c:4f:08:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=305 TOS=0x00 PREC>
Jun  7 21:56:52 SG-UBUNTU-1 kernel: [   50.871781] IN=tap_soft OUT= MAC=ff:ff:ff:ff:ff:ff:ca:4e:96:e2:2c:4f:08:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=305 TOS=0x00 PREC>
Jun  7 21:56:54 SG-UBUNTU-1 kernel: [   52.461980] IN=eth0 OUT= MAC=00:16:3e:5c:e4:1b:40:01:7a:eb:7c:40:08:00 SRC=195.54.167.120 DST=103.125.217.43 LEN=40 TOS=0x00 PRE>
Jun  7 21:56:59 SG-UBUNTU-1 kernel: [   58.191247] IN=eth0 OUT= MAC=00:16:3e:5c:e4:1b:40:01:7a:eb:7c:40:08:00 SRC=82.209.223.12 DST=103.125.217.43 LEN=44 TOS=0x00 PREC>
Jun  7 21:57:03 SG-UBUNTU-1 kernel: [   62.395490] IN=eth0 OUT= MAC=00:16:3e:5c:e4:1b:40:01:7a:eb:7c:40:08:00 SRC=185.153.199.53 DST=103.125.217.43 LEN=40 TOS=0x00 PRE>
Jun  7 21:57:18 SG-UBUNTU-1 kernel: [   76.524958] IN=eth0 OUT= MAC=00:16:3e:5c:e4:1b:40:01:7a:eb:7c:40:08:00 SRC=111.47.28.78 DST=103.125.217.43 LEN=40 TOS=0x04 PREC=>

I suspect we hv not add the tap device to the rules? but i hv tries few times adding them like this '[COLOR=inherit][FONT=Menlo]iptables -t nat -A POSTROUTING -s 255.255.255.0 -o tap_soft -j MASQUERADE'

pls advice. thank you.

[/FONT][/COLOR]-P INPUT DROP
-P FORWARD ACCEPT
-P OUTPUT ACCEPT
-A INPUT -p tcp -m tcp --dport 22 -j ACCEPT
-A INPUT -p tcp -m tcp --tcp-flags FIN,SYN,RST,PSH,ACK,URG FIN,SYN,RST,PSH,ACK,URG -j DROP
-A INPUT -p tcp -m tcp ! --tcp-flags FIN,SYN,RST,ACK SYN -m state --state NEW -j DROP
-A INPUT -p tcp -m tcp --tcp-flags FIN,SYN,RST,PSH,ACK,URG NONE -j DROP
-A INPUT -i lo -j ACCEPT
-A INPUT -s 192.168.7.0/24 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 53 -j ACCEPT
-A INPUT -p udp -m udp --dport 53 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 443 -j ACCEPT
-A INPUT -p udp -m udp --dport 443 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 1194 -j ACCEPT
-A INPUT -p udp -m udp --dport 1194 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 5555 -j ACCEPT
-A INPUT -p udp -m udp --dport 5555 -j ACCEPT
-A INPUT -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
-A INPUT -p icmp -j ACCEPT
-A INPUT -j LOG
-A OUTPUT -o lo -j ACCEPT
-A OUTPUT -s 192.168.7.0/24 -j ACCEPT

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination
SNAT       all  --  192.168.7.0/24       anywhere             to:103.125.217.43

---

### Post by SeijiSensei on 2020-06-07
Usually OpenVPN uses the tun device, not tap.

Do you have "dev tun" or "dev tap" in your openvpn.conf files?  

If the problem is that the traffic is not traveling over the tunnel, first, make sure you're using tun, then add these rules
```

iptables -A INPUT  -i tun+ -j ACCEPT
iptables -A OUTPUT -o tun+ -j ACCEPT

```
If you have only one tunnel, you can specify tun0 instead.  tun+ is a convenient way to permit all the tunnels if you have more than one.

Those rule excerpts don't include important information like PROTO=TCP SPT=xxxxx DPT=xxxxx.

---

### Post by aboka on 2020-06-07
> **SeijiSensei said:**
> Usually OpenVPN uses the tun device, not tap.

Do you have "dev tun" or "dev tap" in your openvpn.conf files?  

If the problem is that the traffic is not traveling over the tunnel, first, make sure you're using tun, then add these rules
```

iptables -A INPUT  -i tun+ -j ACCEPT
iptables -A OUTPUT -o tun+ -j ACCEPT

```
If you have only one tunnel, you can specify tun0 instead.  tun+ is a convenient way to permit all the tunnels if you have more than one.

Those rule excerpts don't include important information like PROTO=TCP SPT=xxxxx DPT=xxxxx.

hi, it is using 'dev tun' in the ovpn config file. hv tried adding the 'tun+' but still not working T.T

root@SG-UBUNTU-1:~# iptables -S
-P INPUT DROP
-P FORWARD ACCEPT
-P OUTPUT ACCEPT
-A INPUT -p tcp -m tcp --dport 22 -j ACCEPT
-A INPUT -p tcp -m tcp --tcp-flags FIN,SYN,RST,PSH,ACK,URG FIN,SYN,RST,PSH,ACK,URG -j DROP
-A INPUT -p tcp -m tcp ! --tcp-flags FIN,SYN,RST,ACK SYN -m state --state NEW -j DROP
-A INPUT -p tcp -m tcp --tcp-flags FIN,SYN,RST,PSH,ACK,URG NONE -j DROP
-A INPUT -j LOG
-A INPUT -i tun+ -j ACCEPT
-A INPUT -i lo -j ACCEPT
-A INPUT -s 192.168.7.0/24 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 53 -j ACCEPT
-A INPUT -p udp -m udp --dport 53 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 443 -j ACCEPT
-A INPUT -p udp -m udp --dport 443 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 1194 -j ACCEPT
-A INPUT -p udp -m udp --dport 1194 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 5555 -j ACCEPT
-A INPUT -p udp -m udp --dport 5555 -j ACCEPT
-A INPUT -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
-A INPUT -p icmp -j ACCEPT
-A OUTPUT -o tun+ -j ACCEPT
-A OUTPUT -o lo -j ACCEPT
-A OUTPUT -s 192.168.7.0/24 -j ACCEPT

pls advice,

---

### Post by SeijiSensei on 2020-06-07
If you run "ip addr" from a prompt, do you see an entry for tun0? Does it have the right address? If you run "ip route" do you see routing set up to send packets from your computer to the remote?  And, on the remote, do you have a route back to the host?

On my OpenVPN client I have
```

$ ip addr
[stuff]
3: tun0: <POINTOPOINT,MULTICAST,NOARP,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN qlen 100
    link/[65534] 
    inet 10.1.1.30 peer 10.1.1.1/32 scope global tun0

```
and
```

$ ip route
[stuff]
10.1.1.1 dev tun0  proto kernel  scope link  src 10.1.1.30 

```
On the server I have an equivalent entry for tun0 with the IP addresses reversed:
```

14: tun0: <POINTOPOINT,MULTICAST,NOARP,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UNKNOWN qlen 100
    link/[65534] 
    inet 10.1.1.1 peer 10.1.1.30/32 scope global tun0

```
and these routes
```

$ ip route
[stuff]
10.1.1.30 dev tun0  proto kernel  scope link  src 10.1.1.1 
192.168.100.0/24 via 10.1.1.30 dev tun0 

```
The first of these sends traffic from the server end of the tunnel, 10.1.1.1, to the client in my office, 10.1.1.30. The second route sends all traffic for hosts within my private home network at 192.168.100.0/24 down the tunnel.  The second route is added via an "up" directive in openvpn.conf.

I use a static tunnel as described in [https://openvpn.net/community-resources/static-key-mini-howto/](https://openvpn.net/community-resources/static-key-mini-howto/)

---

### Post by aboka on 2020-06-07
> **SeijiSensei said:**
> If you run "ip addr" from a prompt, do you see an entry for tun0? Does it have the right address? If you run "ip route" do you see routing set up to send packets from your computer to the remote?  And, on the remote, do you have a route back to the host?

On my OpenVPN client I have
```

$ ip addr
[stuff]
3: tun0: <POINTOPOINT,MULTICAST,NOARP,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN qlen 100
    link/[65534] 
    inet 10.1.1.30 peer 10.1.1.1/32 scope global tun0

```
and
```

$ ip route
[stuff]
10.1.1.1 dev tun0  proto kernel  scope link  src 10.1.1.30 

```
On the server I have an equivalent entry for tun0 with the IP addresses reversed:
```

14: tun0: <POINTOPOINT,MULTICAST,NOARP,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UNKNOWN qlen 100
    link/[65534] 
    inet 10.1.1.1 peer 10.1.1.30/32 scope global tun0

```
and these routes
```

$ ip route
[stuff]
10.1.1.30 dev tun0  proto kernel  scope link  src 10.1.1.1 
192.168.100.0/24 via 10.1.1.30 dev tun0 

```
The first of these sends traffic from the server end of the tunnel, 10.1.1.1, to the client in my office, 10.1.1.30. The second route sends all traffic for hosts within my private home network at 192.168.100.0/24 down the tunnel.  The second route is added via an "up" directive in openvpn.conf.

I use a static tunnel as described in [https://openvpn.net/community-resources/static-key-mini-howto/](https://openvpn.net/community-resources/static-key-mini-howto/)

The client is running on Windows so i could only run this(of what i understand) on the server. the rest i hv no idea where and how to run them -

root@SG-UBUNTU-1:~# ip route
default via 103.125.217.1 dev eth0 onlink
103.125.217.0/24 dev eth0 proto kernel scope link src 103.125.217.43
192.168.7.0/24 dev tap_soft proto kernel scope link src 192.168.7.1

thank you,

---

### Post by SeijiSensei on 2020-06-08
I have a client with Windows users who all connect to a router I maintain using OpenVPN.  Here are the server and client .conf files:

Server running Linux
```

dev tun
port NNNNN

# create a tunnel with 10.1.33.1 as the address on the server
# and 10.1.33.2 as the address on the client
ifconfig 10.1.33.1 10.1.33.2 

# the key file
secret /etc/openvpn/keys/mykeyfile.key

--auth-nocache
user nobody
group nogroup

# run a script when tunnel set up; usually to add static routes
#up ./add_routes

# logging
verb 3

# use various methods to keep the tunnel alive
ping 15
ping-restart 45
ping-timer-rem
persist-tun
persist-key

```

On the Windows client
```

# works out of the box on Windows 10 I'm told with no special driver
dev tun

remote ip.addr.of.server
port NNNNN

# assign the tunnel IP addresses of the endpoints # client first, then server
ifconfig 10.1.33.2 10.1.33.1

#key file
secret xxxxx.key

verb 3
--auth-nocache
ping 15
ping-restart 45
ping-timer-rem
persist-tun
persist-key

```

My client says he doesn't need to do anything special to support "dev tun" on Windows 10.  They just install OpenVPN, use the configuration file above, and a shared key. Don't know about Win7 or before.  If you only have tap in Windows, then try tap on the Linux side as well.

This implements the static-key method described here: [https://openvpn.net/community-resources/static-key-mini-howto/](https://openvpn.net/community-resources/static-key-mini-howto/)

---

### Post by aboka on 2020-06-08
@SeijiSensei you want me to use the ovpn file you share? but i thought the reason is with iptables, epspecially the first line 'drop all', as i could connect and use the vpn as normal if it is set to 'ACCEPT' or if iptabes is 'disabled'

am reading a lot and bit confuse the more i read and try as nothing works so far. here is what i hv in mind tomorrow if hv the time -

1) use 'ACCEPT' at the top line, and only use 'drop all' at the bottom after all rules are set. then use nmap to test if it is secure. still reading on nmap, install and running them is not hard, but hvto learn how to read the output and understand if it is secure thats the tricky part

what do you think?

thank you,

 
[COLOR=#DD4814][[COLOR=#000000]SeijiSensei[/COLOR]]("https://ubuntuforums.org/member.php?u=698195")[COLOR=#000000] [/COLOR][COLOR=#000000][SeijiSensei]("https://ubuntuforums.org/member.php?u=698195")[/COLOR][/COLOR][COLOR=#000000] [/COLOR]

---

### Post by SeijiSensei on 2020-06-09
I think you should drop the firewall for the time being until you are sure you can establish a tunnel between the two computers.  Or else use a very simple firewall like
```

iptables -P INPUT -j DROP

iptables -A INPUT -i lo -j ACCEPT
iptables -A INPUT -i tun+ -j ACCEPT
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -s your.local.ip.addr -j ACCEPT

```
Replace "your.local.ip.addr" with the public address of the machine from which you are connecting. These rules let your machine communicate with the remote server and block all other traffic.  You should be able to set up a tunnel between the two devices.

---

### Post by aboka on 2020-06-09
> **SeijiSensei said:**
> I think you should drop the firewall for the time being until you are sure you can establish a tunnel between the two computers.  Or else use a very simple firewall like
```

iptables -P INPUT -j DROP

iptables -A INPUT -i lo -j ACCEPT
iptables -A INPUT -i tun+ -j ACCEPT
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -s your.local.ip.addr -j ACCEPT

```
Replace "your.local.ip.addr" with the public address of the machine from which you are connecting. These rules let your machine communicate with the remote server and block all other traffic.  You should be able to set up a tunnel between the two devices.

hi, we only use it as a vpn server so no need anything fancy i guess, just secure.

i do not notice there a ssh in the rules? will i be lockout from the vps after applying them?

and last, in my earlier post, i meantion about using nmap to test if the vps is secure, could you give some advice on that? i would like to run a 'before' and 'after' and compare the results so i will know it is really secure.

thank you,

---

### Post by SeijiSensei on 2020-06-09
The last rule provides unrestricted access to your.local.ip.addr on all ports and using all protocols.  So if you're using SSH from the machine with your.local.ip.addr then you'll be able to connect.

You would need to run nmap from another, unrelated host on the Internet with a public IP.  I'll tell you right now, with those firewalling rules, any other host will see nothing of interest.

---

### Post by aboka on 2020-06-10
hi SeijiSensei, great news hv manage to make it work(hopefully as i could connect and use vpn now). read a post on howto troubleshoot iptables issue by using 'watch' and making sure its connecting and to which port then by following that i found an article on openvpn about firewall rules. first i read about adding tun+ as what you have advice, then tap+. then i thought why not. so i add tap+ and it works. so the issue is im using tap and thats why.

am still playing and removing whats not need in there and will play with nmap afterwards.

really confusing now as if adding tap to the iptables work, then server should be running tap, but in client ovpn file is 'dev tun' and when i change the ovpn file to 'dev tap' then it will disconnect after few seconds. any idea why and is it ok to use tap on server and tun on client? but i read that both has to be the same :/

thank you very much

---

### Post by SeijiSensei on 2020-06-10
Can't help with tap/tun.  Other than that one project I mentioned for a client, I've never used OpenVPN on Windows. My implementations have been static tunnels between machines running Linux, and all of them use tun.

Glad you got it running.

How did nmap go?  I scanned 103.125.207.43 from one of my public servers and got nothing.  Is that still the remote server's public IP address?  If so, it doesn't show any exposures to nmap.

```

# ping 103.125.207.43

PING 103.125.207.43 (103.125.207.43) 56(84) bytes of data.
4 packets transmitted, 0 received, 100% packet loss, time 3674ms

# nmap 103.125.207.43

Starting Nmap 5.51 ( http://nmap.org ) at 2020-06-10 08:30 EDT
Note: Host seems down. If it is really up, but blocking our ping probes, try -Pn
Nmap done: 1 IP address (0 hosts up) scanned in 3.16 seconds

# nmap -P0 103.125.207.43

Starting Nmap 5.51 ( http://nmap.org ) at 2020-06-10 08:30 EDT
Nmap scan report for 103.125.207.43
Host is up.
All 1000 scanned ports on 103.125.207.43 are filtered

Nmap done: 1 IP address (1 host up) scanned in 201.51 seconds

```

---

### Post by aboka on 2020-06-10
> **SeijiSensei said:**
> Can't help with tap/tun.  Other than that one project I mentioned for a client, I've never used OpenVPN on Windows. My implementations have been static tunnels between machines running Linux, and all of them use tun.

Glad you got it running.

How did nmap go?  I scanned 103.125.207.43 from one of my public servers and got nothing.  Is that still the remote server's public IP address?  If so, it doesn't show any exposures to nmap.

hi, thought of coming in here to edit my last post to stick with the original topic - 'securing vps with iptables' but you beats me to it ;)

yup, server still running on that IP and am connected to here with its vpn. so lets get back to our original questions-

1) do we still need this rule at the end 'iptables -A INPUT -j DROP'  since we already hv this at the top 'iptables -P INPUT DROP'?

2) and could u pls let us know how you scan with the nmap(using built-in script etc?) and how do you know it is safe from the results? the scan i hv show 

p/s - we run nmap with the script download from github and some other found online, but we dont know howto interpret the results :/

thank you,

---

### Post by SeijiSensei on 2020-06-10
No, you don't need a -j DROP rule if the INPUT policy is DROP.

I showed you the results of the scans.  If there were open ports, it would say so.  For instance, here's another machine I maintain:
```

# nmap xxx.example.com

Starting Nmap 5.51 ( [http://nmap.org](http://nmap.org) ) at 2020-06-10 16:18 EDT
Nmap scan report for xxx.example.com
Host is up (0.032s latency).
rDNS record for nnn.nnn.nnn.nnn: xxx.example.com
Not shown: 997 filtered ports
PORT    STATE SERVICE
25/tcp  open  smtp
80/tcp  open  http
443/tcp open  https

```
Because this host accepts pings, nmap doesn't complain about that. If the remote blocks pings, you can use the -P0 switch to turn off pinging.

nmap scans 1000 ports by default. You can force it scan every port with
```
nmap -p 1-65554 server_name_or_ip
```
Start this at night and come back in the morning.

You need to run scans like these as the root user, e.g., "sudo nmap server_name_or_ip".  Ordinary users can run ping scans, but nothing more interesting.

I don't know what scripts you would need.  nmap itself is a binary program.  Install it with "sudo apt install nmap".

---

