---
title: "Cant get subdomain to work on apache2"
date: 2013-06-21
forum: General Help
---

### Post by mcraul on 2013-06-21
I am running Ubuntu Linux 10.04.1 with Apache2 version 2.2.14 and I"m trying to configure a virtual host file for a subdomain but I cant get the subdomain to resolve. This is what I have my configuration as of now

```
<VirtualHost *:80>                                            
ServerName www.demo.site.com                                                    
ServerAdmin xxx@gmail.com                             
ServerAlias demo.site.com                                    
DocumentRoot /var/www/demo                                      
ErrorLog /var/www/error.log    
</VirtualHost> 
```

When you go to the site it does not even resolve of give any error. So I must be missing something in my host file.
I already enabled the site using a2ensite. 

Any ideas?

Thanks!

---

### Post by ahallubuntu on 2013-06-21
~

---

### Post by mcraul on 2013-06-21
> **ahallubuntu said:**
> Are you mapping your DNS names properly?   [www.demo.site.com](www.demo.site.com) must resolve to the right IP address before it can even get to your server.

[http://techtitbits.com/2008/07/how-to-set-up-a-sub-subdomain/](http://techtitbits.com/2008/07/how-to-set-up-a-sub-subdomain/)


Thanks for the reply.

Where do i do this at? would it be in the apache config file or in the ports file?

thanks!

---

### Post by mcraul on 2013-06-21
Or should I put the ip address of the server in the virtual host file?
Or should this be done in the DNS control panel where our domain is registered at? 

Thanks!

---

### Post by mcraul on 2013-06-21
So what I did this morning is go to my domain console, the server is using Route 53 dns service by amazon and I set the A record to point the subdomain to the ip address of the server.
It still is not routing. I feel like I"m so close that I'm missing something simple.

---

### Post by ahallubuntu on 2013-06-21
~

---

### Post by mcraul on 2013-06-21
Yes I can ping the main domain fine. 

```
Ping 54.245.65.104
[meritsystemservices.com]
Round trip time to 54.245.65.104: 60 ms
Round trip time to 54.245.65.104: 59 ms
Round trip time to 54.245.65.104: 59 ms
Round trip time to 54.245.65.104: 59 ms
Round trip time to 54.245.65.104: 59 ms
Round trip time to 54.245.65.104: 59 ms
Round trip time to 54.245.65.104: 59 ms
Round trip time to 54.245.65.104: 59 ms
Round trip time to 54.245.65.104: 59 ms
Round trip time to 54.245.65.104: 59 ms
Average time over 10 pings: 59.1 ms
```

Im trying to resolve demo.meritsystemservices.com .

---

### Post by mcraul on 2013-06-21
So I did a lookup on demo.meritsystemservices.com and i got the following issue.

PARENT
Status	Test Name	Information
WARN
Parent zone provides NS records	Parent zone does not provide glue for nameservers, which will cause delays in resolving your domain name. The following nameserver addresses were not provided by the parent 'glue' and had to be looked up individually. This is perfectly acceptable behavior per the RFCs. This will usually occur if your DNS servers are not in the same TLD as your domain (for example, a DNS server of "ns1.example.org" for the domain "example.com"). In this case, you can speed up the connections slightly by having NS records that are in the same TLD as your domain.

ns-646.awsdns-16.net. | 205.251.194.134 | TTL=172800
ns-319.awsdns-39.com. | 205.251.193.63 | TTL=172800
ns-1487.awsdns-57.org. | No Glue | TTL=172800

SOA
Status	Test Name	Information
FAIL
SOA record check	No nameservers provided an SOA record for the zone. You should configure your nameservers to have a master slave relationship. The update of the zone information to the slave nameservers should be handled through the SOA record.



Could either of these issues prevent the subdomain to route correctly?

---

### Post by PaulW2U on 2013-06-21
```
paul@G620:~$ host  meritsystemservices.com                                                                                                                                                           
meritsystemservices.com has address 54.245.65.104
paul@G620:~$ host  demo.meritsystemservices.com                                                                                                                                                      
Host demo.meritsystemservices.com not found: 3(NXDOMAIN)
```

 That tells me you haven't set up the 'demo' subdomain at your dns provider. The output of 'dig' also suggests that to be the case.

```
paul@G620:~$ ping -c 1  meritsystemservices.com 
PING meritsystemservices.com (54.245.65.104) 56(84) bytes of data.
64 bytes from ec2-54-245-65-104.us-west-2.compute.amazonaws.com (54.245.65.104): icmp_req=1 ttl=43 time=164 ms

 --- meritsystemservices.com ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 164.497/164.497/164.497/0.000 ms
paul@G620:~$ ping -c 1  demo.meritsystemservices.com 
ping: unknown host demo.meritsystemservices.com
```

The same for 'ping'.

---

### Post by mcraul on 2013-06-21
This is how I have the DNS setup now

demo.meritsystemservices.com.    A          54.245.65.104

demo.meritsystemservices.com.
NS
ns-1614.awsdns-09.co.uk. 
ns-217.awsdns-27.com. 
ns-1410.awsdns-48.org. 
ns-800.awsdns-36.net.
-


demo.meritsystemservices.com.   SOA              ns-1614.awsdns-09.co.uk. awsdns-hostmaster.amazon.com. 



Thanks!

---

### Post by PaulW2U on 2013-06-21
```
paul@G620:~$ dig -t a  demo.meritsystemservices.com @ns-1614.awsdns-09.co.uk                                                                                             

; <<>> DiG 9.9.2-P1 <<>> -t a demo.meritsystemservices.com @ns-1614.awsdns-09.co.uk
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 25596
;; flags: qr aa rd; QUERY: 1, ANSWER: 1, AUTHORITY: 4, ADDITIONAL: 1
;; WARNING: recursion requested but not available

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;demo.meritsystemservices.com.  IN      A

;; ANSWER SECTION:
demo.meritsystemservices.com. 300 IN    A       54.245.65.104

;; AUTHORITY SECTION:
demo.meritsystemservices.com. 172800 IN NS      ns-1410.awsdns-48.org.
demo.meritsystemservices.com. 172800 IN NS      ns-1614.awsdns-09.co.uk.
demo.meritsystemservices.com. 172800 IN NS      ns-217.awsdns-27.com.
demo.meritsystemservices.com. 172800 IN NS      ns-800.awsdns-36.net.

;; Query time: 47 msec
;; SERVER: 205.251.198.78#53(205.251.198.78)
;; WHEN: Fri Jun 21 19:05:29 2013
;; MSG SIZE  rcvd: 210
``` 

How long ago did you set that A record?

I think you might find that you have access to your site shortly. NS records take a while to propagate around the internet.

---

### Post by mcraul on 2013-06-21
Hmm I did that this morning actually around 9 am eastern.

So did those records look correct to you?
Usually amazon dns records propagate really fast so if its correct it should be routing correctly but i'll wait some more.

---

### Post by PaulW2U on 2013-06-21
That TTL time of 300 is not counting down as it should. I've checked all four nameservers too.

Sorry, I'm out of ideas.

---

### Post by mcraul on 2013-06-21
Should I increase the ttl time ? 

Thanks!

---

### Post by mcraul on 2013-06-22
So after waiting more than 24 hours the subdomain is still not routing. 
I went over my vhost configuration and the domain setup and didn't see anything wrong.
See there somewhere else I should be checking at?

Thanks!

---

