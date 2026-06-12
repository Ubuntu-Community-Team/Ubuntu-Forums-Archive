---
title: "Weird RDP issue &quot;No route to host&quot;"
date: 2008-02-11
forum: General Help
---

### Post by kenpotf on 2008-02-11
Hoping someone can help.

I RDP from Gutsy to Windows servers. I can get to certain ones (on 172.x.x.x networks), but anything on the 192.x.x.x network throws a "No Route to Host" error. Now, here's the weird part:

I can ping by name server1 (replies)

I can ping by fqdn server1.domain.com replies

I can ping by IP: 192.168.x.x replies

rdesktop <name> OR <ip> = "No route to host"

My routing table shows a default route to go out my router which is a 10.x.x.x network. The thing that throws me is that I can ping and trace to these servers. When I trace, it shows the proper route. I'm lost at this point, and any help would be great!!

Oh, and this is a wired connection. When I'm tunneled in from my house (through a firewall), I can get to these just fine through my wireless connection on my laptop.


Thanks!

John

---

### Post by kenpotf on 2008-02-11
Oh, and one other thing:

I can RDP into a local server on my network, and then RDP out. I can RDP to anything on the 192.168.x.x network from a windows workstation on my desk, so I KNOW it's not a firewall issue.

thanks,
John

---

### Post by Zwack on 2008-02-11
It's a firewall issue...

No, Seriously... 

If you can ping them, you have a route to them... If you can't rdp to them and you're getting an error about no route to host then that implies that either you don't have a route to them and something else is responding to your pings, or you do have a route to them but something is sending you a packet back that says it can't get there.  

I'm guessing it's an ICMP type 3 that's causing your responses... and that is usually produced by a firewall telling you to get knotted.  [ICMP parameters]("http://http://www.iana.org/assignments/icmp-parameters")

And check this description of iptables [REJECT]("http://www.linuxtopia.org/Linux_Firewall_iptables/x4550.html")

Z.

---

### Post by kenpotf on 2008-02-11
You're right. I feel like an idiot. Last Friday, I placed an access list to block certain IPs from RDP'ing into our servers. Well, I got one of those from my pool. I have certain static addresses assigned for people to be able to, and I forgot to set it back up to that.

Thanks for your time, and I'm sorry to have wasted it. :(

---

### Post by Zwack on 2008-02-11
No problem...

It was an interesting question...

Z.

---

