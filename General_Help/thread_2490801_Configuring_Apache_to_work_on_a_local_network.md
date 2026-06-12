---
title: "Configuring Apache to work on a local network"
date: 2023-09-16
forum: General Help
---

### Post by kwinsw on 2023-09-16
Hi,

I've installed Apache on Ubuntu server. I want to use it to mod and test two or three WordPress themes, before I pick one and use it on my real website.

These means running several sites on Apache simultaneously. All the tutorials I find online, seem to assume you have local DNS. Their goal is to get you to a point at which Apache can server:

[INDENT]site1.mydomain.home
site2.mydomain.home[/INDENT]

I don't have a local DNS set up. I just want to be able to achieve something like this:

192.168.1.10/site1
192.168.1.10/site2

Or whatever the URLs should look like, if I'm just using the server's IP address.

Can anyone tell me how to do this or point me to a tutorial?

Any help or hints much appreciated.

Thanks

---

### Post by TheFu on 2023-09-16
It is much easier to use SNI which uses "names" to go to different sites.  

```
site1.something.local
site2.something.local
```

Then just use normal Apache multi-site setups with 2 different sites-available/ config files, 1 for each.  
If your clients and the server have the same entries in the /etc/hosts file, you can just add 1 or 2 lines to all of them:
```
192.168.1.10 site1.something.local site1
192.168.1.10 site2.something.local  site2
```

Perhaps using the .local TLD isn't a good idea, since that is what Avahi uses based on the {hostname}.local for mDNS.  Maybe .lan would make more sense?  I use .foo, but that wasn't well thought out. Most of my web servers have public names even if they can only be reached from the LAN. I have about 20 domains registered, but tend to use subdomains rather than register more.

If you have Android/iPhone clients to be tested, you'll need a DNS.  You can use a pihole setup for that. I run mine in an lxd managed lxc container.  Then have my DHCP server provide the nameserver IPs (I have 2 piholes) to all dhcp clients. For systems with static IPs, I manually set the resolv.conf to use my dual nameservers (pihole1/pihole2) and prevent systemd-resolved from being used.  After all, let the pihole do the caching for all DNS, no need to have any LAN system do extra caching.

Setting up a pihole for filtering and LAN DNS, once you know what you are doing, takes about 10 minutes. It uses a simple /etc/hosts-like file for the LAN DNS settings. The only trick I know is that the order for each entry line matters.
```
172.22.22.5 deneb   deneb.example.foo
172.22.22.6 hadar    hadar.example.foo
...
```
The short-name  needs to come first.  I have over 100 entries in the local DNS file.  Any change to it needs ```
$ pihole restartdns
```
I've posted the directions followed to setup the pihole inside LXD and later to enable it for LAN DNS to these forums. It has been a few years, but I'd do it again and wish I'd done it 10 yrs sooner.  Not seeing most ads when using a browser really is nice.

---

### Post by kwinsw on 2023-09-16
Thank you! I will try and let you know how I get on. 

Very much appreciated.

---

### Post by SeijiSensei on 2023-09-16
Using the IP address is fine if you configure things so that each site has URLs like those you listed.

You would only have a problem if you wanted to use name-based virtual servers, since those are tied to the domain names. Then you'd need to handle things like site1.domain.name. 

You can also just use localhost if you're accessing the sites from the same machine that the server is running on like [https://localhost/site1](https://localhost/site1).

---

### Post by MAFoElffen on 2023-09-17
I have done all three, (with local DNS, via IP address, and localhost).... To create, and test webpages, web forms and web apps for local use. 

There is also another cheat, where you just add the hostnames and mapped IP addresses in the/etc/hosts file of the client machine.

RE: man hosts
```

   Historical notes
       RFC 952 gave the original format for the host table, though it has since changed.

       Before the advent of DNS, the host table was the only way of resolving hostnames on the fledgling Internet.  Indeed, this file could be created from the official host data base maintained at the
       Network Information Control Center (NIC), though local changes were often required to bring it up to date regarding unofficial aliases and/or unknown hosts.  The  NIC  no  longer  maintains  the
       hosts.txt files, though looking around at the time of writing (circa 2000), there are historical hosts.txt files on the WWW.  I just found three, from 92, 94, and 95.

```
Before I added my local DNS servers, I used to add the fdqn and IP's on my workstation in a host table in file /etc/hosts to map my servers so I could test them as if they were in DNS.

This is the way I did this 10-15 years ago... Then there are no DNS security concerns of anything outside of your local LAN...

---

