---
title: "Setting up BIND?"
date: 2006-11-17
forum: General Help
---

### Post by Airjoe on 2006-11-17
Right now I use mydomain.com for my website name servers. The domain was registerred with godaddy.com. I'm running Kubuntu 6.06.

I wanted to host my own nameservers, so I checked out the tutorial at [http://ubuntuforums.org/showthread.php?t=236093&highlight=Domain+Name+Server](http://ubuntuforums.org/showthread.php?t=236093&highlight=Domain+Name+Server)

I installed bind9. 

I edited name.conf as follows:

```

//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

zone "atpdevelopment.com" {
        type master;
        file "/etc/bind/zones/atpdevelopment.com.db";
        };

zone "1.168.192.in-addr.arpa" {
        type master;
        file "/etc/bind/zones/rev.1.168.192.in-addr.arpa";
        };

```

I edited named.conf.options "forwarders" as follows:
```

         forwarders {
                207.69.188.185;
         };

```

I made the zones directory and created atpdevelopment.com.db
It is as follows:
```

// replace example.com with your domain name. do not forget the . after the dom$
// Also, replace ns1 with the name of your DNS server
atpdevelopment.com.      IN      SOA     ns1.atpdevelopment.com. admin.atpdevel$
// Do not modify the following lines!
                                                        2006081401
                                                        28800
                                                        3600
                                                        604800
                                                        38400
 )

atpdevelopment.com.      IN      NS              ns1.atpdevelopment.com.
www              IN      A       192.168.1.102
ns1              IN      A       192.168.1.102

```

Then I made the reverse, rev.1.168.192.in-addr.arpa
It is as follows:
```

//replace example.com with yoour domain name, ns1 with your DNS server name.
// The number before IN PTR example.com is the machine address of the DNS serve$
@ IN SOA ns1.atpdevelopment.com. admin.atpdevelopment.com. (
                        2006081401;
                        28800;
                        604800;
                        604800;
                        86400
)

                     IN    NS     ns1.atpdevelopment.com.
1                    IN    PTR    atpdevelopment.com

```

I did 
/etc/init.d/bind9 force-reload
and it just said "*Reloading domain name service". 
After a while it said

rndc: connect failed: timed out

When I went to godaddy.com to change my nameservers, I set the first one to NS1.ATPDEVELOPMENT.COM but it just says "errors were detected."

Can anyone help me? Am I doing anything wrong? How do I fix this?

Thank you SO MUCH

Also I have a router do I need to forward a port for BIND?

---

### Post by Swab on 2006-11-17
How is godaddy.com supposed to resolve NS1.ATPDEVELOPMENT.COM , surely that won't mean anything to them?

---

### Post by Airjoe on 2006-11-17
Eek.

Well, what exactly am I supposed to do?

I just want to be able to have my own nameserver, because right now using mydomain.com, whenever my IP address changes it takes like 8 hours untill it works again.

---

### Post by Swab on 2006-11-17
> **Airjoe said:**
> Eek.

Well, what exactly am I supposed to do?

I just want to be able to have my own nameserver, because right now using mydomain.com, whenever my IP address changes it takes like 8 hours untill it works again.

I don't think it's that simple to set up your own authorative server, all you can have is a caching server, which won't suit your needs....

---

### Post by Swab on 2006-11-17
What about using something like no-ip.com or dyndns.com ? Still be some times when you can't access your server when your IP changes, but it should be minimal.

---

### Post by Airjoe on 2006-11-17
Looks like dyndns.org is going to charge me to use it with my domain.

I just want to be able to control the... err... "A Records" so that my domain (atpdevelopment.com) can point to my IP and the changes will take into effect immediatly after I submit the new IP. With my current setup (mydomain.com nameservers), it takes between 4 and 24 hours before the domain works again after I submit the new IP.

Anyone have any solutions?

---

### Post by koenn on 2006-11-18
> **Swab said:**
> I don't think it's that simple to set up your own authorative server, all you can have is a caching server, which won't suit your needs....

hm. While it's not all that difficult to install bind and edit a few zone files and config to make it work (re that howto and your post #1), designing and maintaining a dns infrastructure (which is waht you are actually trying to do) is a bit more complicated. You'll need to have some notion of tcp/ip and networking in order to get it right. Keeping kan also be quite complex.

I suppose you want eg to have a website at [www.atpdevelopment.com](www.atpdevelopment.com), and you want to have it public, on the internet, right ?

The addresses you're using are private addresses. If your DNS would work, and my browser would want to go to your web site, it would be told by your dns to go to address  192.168.1.102. Those addresses aren't routed on the internet, so there's no way for my browser to connect to your web server.
(==> this is what I mean with 'you need some knowledge of TCP/IP)

Even before that, to figure out which dns server to ask for the address of [www.atpdevelopment.com](www.atpdevelopment.com), my browser would need to find out
1- who is authoritive ns for atpdevelopment.com
2- what is its address
3- even if it finds the address, it's a private address again, so unreachable.

so, apart from registering your domain, you need addresses that are publically accessible, either through NAT and portforwarding, either by leasing real public addresses. This will open up routes into your network, so there are security issues here.

Also - assuming you get all the above sorted out : you don't want that DNS server to reveil too much information about your internal network. How to deal with that depends on what your own network looks like (just one PC behind a broadband router ? several PC's / servers / ... ? Who needs to talk to who ?)

Basically : running a web server on a dynamic IP address, or changing IP addresses every so often, which I assulme is what you need your own authoritave name server for, does not sound like a good idea.

> Eek. 
kinda tells me you lack the background (tcpip, dns, network administration) to pull this off. 

> 
Well, what exactly am I supposed to do?
read up on network basics so you understand the context of what you're trying to do.

---

### Post by Airjoe on 2006-11-18
> **koenn said:**
> hm. While it's not all that difficult to install bind and edit a few zone files and config to make it work (re that howto and your post #1), designing and maintaining a dns infrastructure (which is waht you are actually trying to do) is a bit more complicated. You'll need to have some notion of tcp/ip and networking in order to get it right. Keeping kan also be quite complex.

Oh, I know plenty about TCP/IP; I'm currently taking and have almost completed CCNA 1. 


> **koenn said:**
> I suppose you want eg to have a website at [www.atpdevelopment.com](www.atpdevelopment.com), and you want to have it public, on the internet, right ?

The addresses you're using are private addresses. If your DNS would work, and my browser would want to go to your web site, it would be told by your dns to go to address  192.168.1.102. Those addresses aren't routed on the internet, so there's no way for my browser to connect to your web server.
(==> this is what I mean with 'you need some knowledge of TCP/IP)

I had figured that, but those what were in the tutorial so I figured I'd go for it.

> **koenn said:**
> Even before that, to figure out which dns server to ask for the address of [www.atpdevelopment.com](www.atpdevelopment.com), my browser would need to find out
1- who is authoritive ns for atpdevelopment.com
2- what is its address
3- even if it finds the address, it's a private address again, so unreachable.

so, apart from registering your domain, you need addresses that are publically accessible, either through NAT and portforwarding, either by leasing real public addresses. This will open up routes into your network, so there are security issues here.


Yeah, that's why I was asking about portforwarding in my initial post. 

> **koenn said:**
> Also - assuming you get all the above sorted out : you don't want that DNS server to reveil too much information about your internal network. How to deal with that depends on what your own network looks like (just one PC behind a broadband router ? several PC's / servers / ... ? Who needs to talk to who ?)

I have 3-6 computers on a linksys WRT54G wireless broadband router.

> **koenn said:**
> Basically : running a web server on a dynamic IP address, or changing IP addresses every so often, which I assulme is what you need your own authoritave name server for, does not sound like a good idea.


kinda tells me you lack the background (tcpip, dns, network administration) to pull this off. 


read up on network basics so you understand the context of what you're trying to do.

I know what I'm trying to do; I'm just not very linux-prone. I've never used something like BIND or come close to anything like configuring a DNS server.


However, I installed Webmin last night and set everything up the right way with the help of a friend. Although he said that I'll still have downtime when my IP changes, at least I can manage my own nameserver now, rather than with mydomain.com.

But there's something weird going on. I set up godaddy to use ns1.atpdevelopment.com and ns2.atpdevelopment.com, but when I "dig atpdevelopment.com", sometimes it comes up with 

```
; <<>> DiG 9.3.2 <<>> atpdevelopment.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 49015
;; flags: qr rd ra; QUERY: 1, ANSWER: 4, AUTHORITY: 9, ADDITIONAL: 9

;; QUESTION SECTION:
;atpdevelopment.com.            IN      A

;; ANSWER SECTION:
atpdevelopment.com.     86400   IN      CNAME   wc.traffic.puredns.com.
wc.traffic.puredns.com. 38710   IN      CNAME   wc.funnel.revenuedirect.com.akadns.net.
wc.funnel.revenuedirect.com.akadns.net. 300 IN A 66.150.161.58
wc.funnel.revenuedirect.com.akadns.net. 300 IN A 69.25.47.165

;; AUTHORITY SECTION:
akadns.net.             34474   IN      NS      usw5.akadns.net.
akadns.net.             34474   IN      NS      asia4.akadns.net.
akadns.net.             34474   IN      NS      asia9.akadns.net.
akadns.net.             34474   IN      NS      za.akadns.org.
akadns.net.             34474   IN      NS      zb.akadns.org.
akadns.net.             34474   IN      NS      zc.akadns.org.
akadns.net.             34474   IN      NS      zd.akadns.org.
akadns.net.             34474   IN      NS      eur1.akadns.net.
akadns.net.             34474   IN      NS      eur7.akadns.net.

;; ADDITIONAL SECTION:
za.akadns.org.          31852   IN      A       204.2.178.133
zb.akadns.org.          31849   IN      A       206.132.100.105
zc.akadns.org.          31842   IN      A       69.45.78.3
zd.akadns.org.          31843   IN      A       63.209.3.132
eur1.akadns.net.        42407   IN      A       213.254.204.197
eur7.akadns.net.        44627   IN      A       193.108.94.88
usw5.akadns.net.        96266   IN      A       63.241.73.200
asia4.akadns.net.       102957  IN      A       61.213.147.96
asia9.akadns.net.       106376  IN      A       220.73.220.4

;; Query time: 183 msec
;; SERVER: 207.69.188.185#53(207.69.188.185)
;; WHEN: Sat Nov 18 08:09:02 2006
;; MSG SIZE  rcvd: 472

```

Which is totally wrong, and sometimes it comes up with

```
; <<>> DiG 9.3.2 <<>> atpdevelopment.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 17843
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;atpdevelopment.com.            IN      A

;; ANSWER SECTION:
atpdevelopment.com.     12323   IN      A       24.239.185.63

;; AUTHORITY SECTION:
atpdevelopment.com.     12323   IN      NS      ns1.atpdevelopment.com.

;; Query time: 37 msec
;; SERVER: 207.69.188.185#53(207.69.188.185)
;; WHEN: Sat Nov 18 08:02:07 2006
;; MSG SIZE  rcvd: 70

```

What could be causing this?

Thanks again for taking the time to help out.

---

### Post by koenn on 2006-11-18
looks to me you're on the right track.

I find :
```
; <<>> DiG 9.3.2 <<>> atpdevelopment.com in NS

;; ANSWER SECTION:
atpdevelopment.com.     172800  IN      NS      ns1.atpdevelopment.com.
atpdevelopment.com.     172800  IN      NS      ns2.atpdevelopment.com.

;; ADDITIONAL SECTION:
ns1.atpdevelopment.com. 172800  IN      A       24.239.185.63
ns2.atpdevelopment.com. 172800  IN      A       24.239.185.63
```

and I can query for your web server's address :

```
; <<>> DiG 9.3.2 <<>> www.atpdevelopment.com in A @24.239.185.63
; (1 server found)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 45614
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 2, ADDITIONAL: 0

;; QUESTION SECTION:
;www.atpdevelopment.com.                IN      A

;; ANSWER SECTION:
www.atpdevelopment.com. 0       IN      CNAME   atpdevelopment.com.
atpdevelopment.com.     38400   IN      A       24.239.185.63
```

(and even browse to it with e web browser).

You still experiencing problems ?

---

### Post by Airjoe on 2006-11-18
It works fine in the browser, but dig is still switching back and forth. 

I just ran "dig www.atpdevelopment.com" and got:
```
root@Nereid:/# dig www.atpdevelopment.com

; <<>> DiG 9.3.2 <<>> www.atpdevelopment.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 47892
;; flags: qr rd ra; QUERY: 1, ANSWER: 4, AUTHORITY: 9, ADDITIONAL: 9

;; QUESTION SECTION:
;www.atpdevelopment.com.                IN      A

;; ANSWER SECTION:
www.atpdevelopment.com. 86319   IN      CNAME   wc.traffic.puredns.com.
wc.traffic.puredns.com. 4775    IN      CNAME   wc.funnel.revenuedirect.com.akadns.net.
wc.funnel.revenuedirect.com.akadns.net. 204 IN A 66.150.161.58
wc.funnel.revenuedirect.com.akadns.net. 204 IN A 69.25.47.165

;; AUTHORITY SECTION:
akadns.net.             74058   IN      NS      usw5.akadns.net.
akadns.net.             74058   IN      NS      asia4.akadns.net.
akadns.net.             74058   IN      NS      asia9.akadns.net.
akadns.net.             74058   IN      NS      za.akadns.org.
akadns.net.             74058   IN      NS      zb.akadns.org.
akadns.net.             74058   IN      NS      zc.akadns.org.
akadns.net.             74058   IN      NS      zd.akadns.org.
akadns.net.             74058   IN      NS      eur1.akadns.net.
akadns.net.             74058   IN      NS      eur7.akadns.net.

;; ADDITIONAL SECTION:
za.akadns.org.          19671   IN      A       204.2.178.133
zb.akadns.org.          19677   IN      A       206.132.100.105
zc.akadns.org.          19677   IN      A       69.45.78.3
zd.akadns.org.          19671   IN      A       63.209.3.132
eur1.akadns.net.        106908  IN      A       213.254.204.197
eur7.akadns.net.        28741   IN      A       193.108.94.88
usw5.akadns.net.        80667   IN      A       63.241.73.200
asia4.akadns.net.       32509   IN      A       61.213.147.96
asia9.akadns.net.       85401   IN      A       220.73.220.4

;; Query time: 103 msec
;; SERVER: 207.69.188.185#53(207.69.188.185)
;; WHEN: Sat Nov 18 11:55:45 2006
;; MSG SIZE  rcvd: 476

```

running "dig [www.atpdevelopment.com](www.atpdevelopment.com) NS" gives me:
```
root@Nereid:/# dig atpdevelopment.com NS

; <<>> DiG 9.3.2 <<>> atpdevelopment.com NS
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 61255
;; flags: qr rd ra; QUERY: 1, ANSWER: 4, AUTHORITY: 0, ADDITIONAL: 4

;; QUESTION SECTION:
;atpdevelopment.com.            IN      NS

;; ANSWER SECTION:
atpdevelopment.com.     24751   IN      NS      ns4.mydomain.com.
atpdevelopment.com.     24751   IN      NS      ns1.mydomain.com.
atpdevelopment.com.     24751   IN      NS      ns2.mydomain.com.
atpdevelopment.com.     24751   IN      NS      ns3.mydomain.com.

;; ADDITIONAL SECTION:
ns1.mydomain.com.       133172  IN      A       64.94.117.213
ns2.mydomain.com.       41176   IN      A       216.52.121.233
ns3.mydomain.com.       114062  IN      A       66.150.161.130
ns4.mydomain.com.       142977  IN      A       63.251.83.74

;; Query time: 36 msec
;; SERVER: 207.69.188.185#53(207.69.188.185)
;; WHEN: Sat Nov 18 11:56:26 2006
;; MSG SIZE  rcvd: 181

```

Which is really odd, because mydomain no longer has any connection with my site. 

Eh, I guess I'll just wait out the full 48 hours and see if everything fixes itself. 

Thanks for all your help.

[edit]
See, I just ran it again and now it seems fine.
```

root@Nereid:/# dig www.atpdevelopment.com

; <<>> DiG 9.3.2 <<>> www.atpdevelopment.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 54554
;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 2, ADDITIONAL: 0

;; QUESTION SECTION:
;www.atpdevelopment.com.                IN      A

;; ANSWER SECTION:
www.atpdevelopment.com. 38350   IN      CNAME   atpdevelopment.com.
atpdevelopment.com.     38364   IN      A       24.239.185.63

;; AUTHORITY SECTION:
atpdevelopment.com.     38364   IN      NS      ns1.atpdevelopment.com.
atpdevelopment.com.     38364   IN      NS      ns2.atpdevelopment.com.

;; Query time: 34 msec
;; SERVER: 207.69.188.185#53(207.69.188.185)
;; WHEN: Sat Nov 18 12:17:41 2006
;; MSG SIZE  rcvd: 106

```

---

### Post by phormion on 2006-11-18
Airjoe, you might want to check this out: 

[http://www.dnsreport.com/tools/dnsreport.ch?domain=atpdevelopment.com](http://www.dnsreport.com/tools/dnsreport.ch?domain=atpdevelopment.com)

Your nameservers are somewhat misconfigured, so I understand koenn's recommendation to read up a bit before trying to set up your own DNS. Setting up BIND is not something that easy to do, and maintaining it can be painful if you don't understand some basic things. I recommend "DNS & BIND, 4th edition" by Paul Albitz and Cricket Liu as a good starter. There's also other online resources. Understand that I'm not being patronizing or mean, it's for your own good. Not all software is made to be 'easy to use'. 

Oh, and there's also the BIND administrator's reference manual: 

[http://www.isc.org/sw/bind/arm93/](http://www.isc.org/sw/bind/arm93/)

Now on to your problems: you haven't defined an A records for one of your nameservers (ns2) - that's what shows up in the zones you posted; dnsreport reports that both are missing IP addresses. Also, it reports your nameserver is open, that is, anybody can use it to make queries. You most likely don't want to do that. Look up 'allow-query' and 'allow-recursion' in the ARM.

---

### Post by koenn on 2006-11-18
Also, keep in mind that with your current setup, you're allowing direct access from the internet to your LAN. A small configuration error your bind or web server, a silly mistake in a web server script, ... could lead to an exploit and if someone should manage to compromise your wen or dns server, they may also get access to the other machines on the same LAN.

There's people out there actively looking for such oportunities - and finding out that your web server is used to distribute    "warez" or your computer was used to break in to other peoples computer is not really a great experience. 

Best practise is to isolate public servers in a DMZ.

---

