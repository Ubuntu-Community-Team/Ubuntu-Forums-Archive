---
title: "I need help configuring squid"
date: 2006-09-29
forum: General Help
---

### Post by CameronCalver on 2006-09-29
Hello i have read many threads on configuring squid but i cant get any of them to work.
This proxy will be running on a 10gb hd and i want 6 gb for the proxy cache and ot has about 380mb ram and a 500mhz proccesor.
The server's ip address is 192.168.1.103 and the other computer on the network are 192.168.1.101 and 192.168.1.102 so could someone tell me a config that will cache for me and work with those ip addresses thanks in advance
,Cameron

---

### Post by kidders on 2006-09-30
Squid should behave fairly close to what you're describing out of the box. What are your problems, exactly?

---

### Post by CameronCalver on 2006-10-01
well i need help setting the cache dir the cache size the the mem it uses coz i want it to use like 250mb of ram and also set only to alow those three ip addresses

---

### Post by CameronCalver on 2006-10-01
im now using a how to from 
[http://www.ubuntuforums.org/showthread.php?t=229249&highlight=restart+squid](http://www.ubuntuforums.org/showthread.php?t=229249&highlight=restart+squid) 
but it still seam not to work i try to restart squid with
```
sudo /etc/init.d/squid restart
``` but it did not work so i did squid start and it said sqiuid started and when i try to use it it says 
```
The proxy server is refusing connections     
          

Firefox is configured to use a proxy server that is refusing connections.
       
  


    *   Check the proxy settings to make sure that they are correct.

    *   Contact your network administrator to make sure the proxy server is
          working.
```

i attached my conf file for you

and the ip of the squid machine is 192.168.1.103

---

### Post by kidders on 2006-10-01
Hi there,

I removed all the comments from your squid.conf to make it easier to understand ...

```
http_port 192.168.1.103:3128
http_port 192.168.1.103:80

hierarchy_stoplist cgi-bin ?

acl QUERY urlpath_regex cgi-bin \?
no_cache deny QUERY

cache_mem 32 MB

maximum_object_size 153600 KB

cache_replacement_policy heap LFUDA

hosts_file /etc/hosts

refresh_pattern ^ftp:		1440	20%	10080
refresh_pattern ^gopher:	1440	0%	1440
refresh_pattern .		0	20%	4320
refresh_pattern -i .deb$ 129600 100% 129600
refresh_pattern -i .rpm$ 129600 100% 129600
refresh_pattern -i .tgz$ 129600 100% 129600
refresh_pattern -i .exe$ 129600 100% 129600
refresh_pattern -i .cab$ 129600 100% 129600
refresh_pattern -i .zip$ 129600 100% 129600
refresh_pattern -i .rar$ 129600 100% 129600
refresh_pattern -i .arj$ 129600 100% 129600
refresh_pattern -i .jpg$ 129600 100% 129600
refresh_pattern -i .gif$ 129600 100% 129600
refresh_pattern -i .bmp$ 129600 100% 129600
refresh_pattern -i .mov$ 129600 100% 129600
refresh_pattern -i .avi$ 129600 100% 129600
refresh_pattern -i .mpg$ 129600 100% 129600
refresh_pattern -i .mpeg$ 129600 100% 129600
refresh_pattern -i .wmv$ 129600 100% 129600
refresh_pattern -i .mp3$ 129600 100% 129600
refresh_pattern -i .wav$ 129600 100% 129600
refresh_pattern -i .bin$ 129600 100% 129600

acl all src 0.0.0.0/0.0.0.0
acl manager proto cache_object
acl localhost src 127.0.0.1/255.255.255.255
acl to_localhost dst 127.0.0.0/8
acl SSL_ports port 443 563	# https, snews
acl SSL_ports port 873		# rsync
acl Safe_ports port 80		# http
acl Safe_ports port 21		# ftp
acl Safe_ports port 443 563	# https, snews
acl Safe_ports port 70		# gopher
acl Safe_ports port 210		# wais
acl Safe_ports port 1025-65535	# unregistered ports
acl Safe_ports port 280		# http-mgmt
acl Safe_ports port 488		# gss-http
acl Safe_ports port 591		# filemaker
acl Safe_ports port 777		# multiling http
acl Safe_ports port 631		# cups
acl Safe_ports port 873		# rsync
acl Safe_ports port 901		# SWAT
acl purge method PURGE
acl CONNECT method CONNECT

http_access allow manager localhost
http_access deny manager
http_access allow purge localhost
http_access deny purge
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports

acl our_networks src 192.168.1.0
http_access allow localhost

http_access deny all

http_reply_access allow all

icp_access allow all


visible_hostname ubuntu

coredump_dir /var/spool/squid
```

The first thing that strikes me is:

> acl our_networks src 192.168.1.0
http_access allow localhost

http_access deny all
Afaik, squid will obey the first applicable access control directive. You define the "our_networks" ACL, but you never permit access by it, so squid will reject any incoming connections from your LAN. Of course, what you *really* want to do is restrict access to a very small subset of your network's IP range, so you might like to make your own ACL and grant access by that instead.

---

### Post by CameronCalver on 2006-10-01
So do i just replace that one you gave me with my one or just edit the things you gave me?

---

### Post by kidders on 2006-10-03
Either...

I didn't do anything special to the config I posted ... I just hoped it would be easier for you to read once all the crap got stripped away. You might prefer to leave all the comments in your real version, for reference.

Have you managed to create an ACL that limits access to the two IPs you mentioned?

---

### Post by CameronCalver on 2006-10-03
well i  did 192.168.1.0 and that allows the to ips so yes but another thing the schools proxy bloock 90 percent of the legit stuff so if just say i wanted to allow an ip just say 203.0.178.102 is this what i would do for the alc thing
```
acl ... al0w.... 192.168.1.0/24 203.0.178.102
```
or do i need to put a /24 or anything becuase it is over the internet

---

### Post by kidders on 2006-10-04
Just write the IP you want to allow access from. "/24" is a netmask (corresponding to 255.255.255.0), which is not useful information unless you're specifying an IP range or subnet.
```

acl permitted_hosts src 203.0.178.102
http_access allow permitted_hosts

```
Then that single host will be allowed to access the proxy.

---

### Post by CameronCalver on 2006-10-04
thanks alot everything is going fine but just a question what happens when the cache folder gets up to the alocated space.
Also if the cache folder gets to like 7gb would it get slower becuase it  has more to look through so if so the squid server is got 380mb ram and it is server linux so can i bump up the cache_mem to like just say 300mb?

---

### Post by kidders on 2006-10-05
Hey again,

When your cache fills up, squid will probably start progressively expunging it to make space. Quite often, keeping a massive cache is counter-productive though, since:

[LIST]
[*]Cached items may be outdated and need to be re-fetched anyway, making caching them in the first place a waste of time.
[*]Your users' working set may not be as big as you think.
[/LIST]

If you examine the behaviour of your squid in practice, you will soon get a clearer idea of where the boundary lies in terms of how much space you need to set aside.

With regard to your performance question, it would be hard to argue that a bigger cache doesn't lead to slower responses. Having said that, the difference should be almost imperceptible in most cases. Modern caching/indexing applications use very smart hashing mechanisms, (some of the b-tree variants can perform quite amazingly), so I wouldn't be terribly concerned by this issue. What *will* degrade your performance is operations like swapping, since you only have 380M RAM.

---

### Post by CameronCalver on 2006-10-07
Ok another thing is blocking certain url's and certain keywords i understand all you have to do is do a acl command but none of them work

---

### Post by kidders on 2006-10-07
Hey again,

Perhaps the most convenient way of doing this is to install a squid extention, like DansGuardian. Many of these give you much more fine-grained control, far more easily.

Basically, there are two types of content filter out there. The simpler ones, just block specific sites/content based on predefined keywords & rules. These have the advantage of being straightforward, but can drag down performance ever so slightly ... moreso if you've got lots of users. The second tries to "learn" as time goes by, by analysing peoples' requests after the fact. These have the advantage of being more asynchronous (so you take less of a performance hit), but by their nature, they often allow access to certain content once or twice, before eventually deciding to block it.

---

### Post by CameronCalver on 2006-10-08
Well can you help me set up the first one becuase i d not really care about speed becuase this is only a muk around proxy

---

### Post by kidders on 2006-10-09
Most content filters work the "first" way. Pick any one you like the sound of and give it a try :-) I mentioned DansGuardian because I vaguely remember trying it once ... but don't let that influence your choice! As I recall, it's pretty featureful, and trivial to set up, though.

Let me know what you pick ... I'd be more than happy to help!

> This proxy will be running on a 10gb hd and i want 6 gb for the proxy cache
Incidentally, if you're just mucking around, 6GB is *waaaaaay* too big a cache. That figure kinda lead me to assume you were planning on serving several hundred users!

---

### Post by CameronCalver on 2006-10-09
ok ill do about 4gb and also try blocking the word gun

---

### Post by Abhi Kalyan on 2007-01-28
dansguardian is what you could use right now.
Its got the best features and is not a hog.
i use it to server about 50 people.
The cache size could be around 2 Gb max to have a Super good performance.
Try setting th strings that alter the weight of the content stored.
All the best.

---

