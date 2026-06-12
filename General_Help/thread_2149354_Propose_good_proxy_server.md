---
title: "Propose good proxy server"
date: 2013-05-28
forum: General Help
---

### Post by prijic87 on 2013-05-28
Hello guru's,

This is my first post on forums, but I am not a new ubuntu user. I used linux before , but i am far away from a skilled user. I decided to use ubuntu, and some good proxy server for my friend's game caffe. What I actually want, is to set up proxy server, so the computers in the network can get windows updates and game updates through local network, instead from the Internet. I heard about squid, but I have also heard that it is hard to configure it for a beginner. I wanted to ask is that true, since i am not very skilled in linux, but have some knowledge, usually in Terminal. So i want a basic proxy server for HTTP protocol and probably for FTP. What do you say about installing proxy to this configuration?

Internet link will be about 40Mbps, but there will be about 12-13 machines running Windows. Is this feasible and reasonable to go into this configuration?

Thank you very much for your answers.

Sincerely prijic87

---

### Post by Lars Noodén on 2013-05-28
Squid is quite easy to configure if you read up on it first.  Only a few lines need to be changed to get it to work as a proxy/cache for your LAN.  

1. You have to decide on the size and directory location of the cache. Before you run squid the first time,  you have to have it create those directories (*sudo squid -z*).

2. You have to decide which subnet or hosts will have access.  That's down after the line that says "# INSERT YOUR OWN RULE(S) HERE..." and usually amounts to *http_access allow localnet*.  Though you can get really fancy with what and who is allowed.

But squid is your main choice if you are serving up generic http requests.

---

### Post by prijic87 on 2013-05-28
Thank you Lars, for the thorough and fast reply. 

So if I understand you correctly, i can run ubuntu as a Virtual Machine, and install squid on that. I will probably used bridged connection mode, to get IP address directly from DHCP. All hosts in the caffe, will have access. I will try this configuration, and I hope that squid will save bandwidth consumed by windows updates/ game updates.

---

### Post by Lars Noodén on 2013-05-28
Yes, you should be able to save bandwidth with that setup, but as a VM I'm not sure if it will be enough faster.  You'll have to try but if your network is slow or has little bandwidth compared to your LAN there should be a noticeable improvement at least for the second user to load that file.  The first user won't notice any change as the file will still have to come in over the Internet, but the second user will be getting the file over the LAN.

About the cache directory mentioned in #1 above, it is set with *cache_dir*.

---

### Post by prijic87 on 2013-05-28
The VM will be installed on main host computer, that is significantly faster and have more RAM Memory, than other computers. It will be connected to the internet via 40Mbps Internet link, and with 100mbit or 1Gbit LAN to other computers. I am just curious about game updates if they go via P2P protocol, can squid help there too? Thank you.

Sincerely prijic87.

---

### Post by Lars Noodén on 2013-05-28
Gigabit LAN should be nice, especially for the second and subsequent downloaders that can take advantage of the cache.  

squid can't help with P2P but if you set up the appropriate P2P client inside your LAN in a way that it is discoverable by your other machines, that should have similar effect.

---

### Post by prijic87 on 2013-05-28
Ok, that's great, because I think that in LAN through NAT every machine will be visible. If one computer downloads the patch, he can send to others at the full LAN speed. Thank you for your answers Lars, you have been very very helpful, and answered my questions fully. Now the next step is to test this in real life.

Sincerely
prijic87

---

### Post by Lars Noodén on 2013-05-28
Looking at the recent version of squid3.conf, you'll also have to set *acl localnet src*

Also, the access log is in /var/log/squid3/access.log and if you notice a lot of TCP_MISS for the same URLs over and over, it might be a sign to add or increase the cache_dir(s).

With the P2P, not all will be able to figure out that there are peers on the same LAN, you might have to adjust them or even spy with tcpdump or wireshark to be sure they are talking with each other.  

Keep us posted.  You project sounds quite interesting.

---

### Post by prijic87 on 2013-06-03
> **Lars Noodén said:**
> Looking at the recent version of squid3.conf, you'll also have to set *acl localnet src*

Also, the access log is in /var/log/squid3/access.log and if you notice a lot of TCP_MISS for the same URLs over and over, it might be a sign to add or increase the cache_dir(s).

With the P2P, not all will be able to figure out that there are peers on the same LAN, you might have to adjust them or even spy with tcpdump or wireshark to be sure they are talking with each other.  

Keep us posted.  You project sounds quite interesting.

Hello guys, im keeping u posted about this project. I installed ubuntu Ubuntu 12.04.2 LTS , and installed squid. I followed the Lars's steps, and configured the proxy server on ubuntu VM. Now when i fire up my Firefox on Windows7, and configure it to use proxy server, i can browse the web. When i disable squid on ubuntu, and try to browse the web, I cannot (as expected). Also the netstat is showing that Firefox is using the proxy server. So everything seems to be working...

But, my main goal of installing squid is to have it as cache server. But cache is not working. For eg. when i download something for the first time, the file is downloaded at speed of about 8Mbit (my max data transfer from the Internet), but when i redownload the file, the speed is the same. I think that the speed for the already downloaded file, should be the LAN or near LAN (1Gbit) speed. I have configured the cache dir:

# Uncomment and adjust the following to add a disk cache directory.
cache_dir ufs /var/spool/squid3 1000 16 256


also in the spool folder there are physical files...

@ubuntu:/var/spool$ sudo du -s -h squid3/
35M    squid3/


When i browse, the size of spool folder is growing...

but there are lot TCP_MISS in access.log

Is there a fast way to test if squid is working correctly? I tried 'sudo squid3 -k check' but i got this in access.log>

html
1370119008.515     81 127.0.0.1 TCP_MISS/304 415 GET [http://wiki.squid-cache.org/wiki/squidtheme/js/kutils.js](http://wiki.squid-cache.org/wiki/squidtheme/js/kutils.js) - DIRECT/77.93.254.178 application/x-javascript
1370119008.532     96 127.0.0.1 TCP_MISS/304 399 GET [http://wiki.squid-cache.org/wiki/squidtheme/css/print.css](http://wiki.squid-cache.org/wiki/squidtheme/css/print.css) - DIRECT/77.93.254.178 text/css
1370119008.650   1791 127.0.0.1 TCP_MISS/200 43146 GET [http://wiki.squid-cache.org/SquidFaq/InstallingSquid](http://wiki.squid-cache.org/SquidFaq/InstallingSquid) - DIRECT/77.93.254.178 text/html
1370119008.793     52 127.0.0.1 TCP_MISS/304 401 GET [http://wiki.squid-cache.org/wiki/squidtheme/img/attention.png](http://wiki.squid-cache.org/wiki/squidtheme/img/attention.png) - DIRECT/77.93.254.178 image/png

there is always just TCP_MISS-es.

How to fix this issue?

Thanks in advance.

Sincerely, prijic87.

---

### Post by Lars Noodén on 2013-06-03
TCP_MISS means that the file was not in the cache.  You see a lot of them for different files because you get one such entry the first time a file is fetched from the net.  If the cache is too small, then files are removed from the cache and you'll get several misses over time for the same file.  It's only if you keep seeing TCP_MISS for the same files again and again that there is an issue.  Otherwise, it is normal operation.

---

### Post by prijic87 on 2013-06-03
Thank you Lars for the fast reply. Yes, i am seeing this quite often, but there are also TCP_REFRESH_UNMODIFIED so i assume that the cache is doing okay. But, for example, i go to speedtest.net couple of times, and measure the speed. I know that his flash app is sending me an img file, that should be cached, but i see in log this:

1370276716.173   1127 192.168.0.10 TCP_MISS/200 505921 GET [http://metrics.verat.net/speedtest/speedtest/random500x500.jpg?](http://metrics.verat.net/speedtest/speedtest/random500x500.jpg?) - DIRECT/217.26.64.149 image/jpeg
1370276716.233   1179 192.168.0.10 TCP_MISS/200 505921 GET [http://metrics.verat.net/speedtest/speedtest/random500x500.jpg?](http://metrics.verat.net/speedtest/speedtest/random500x500.jpg?) - DIRECT/217.26.64.149 image/jpeg

Im now installing webmin, maybe this GUI will help me to figure out squid.

Im mainly installing squid for caching, for eg. if i download 100mb file with 8mbps speed, i want to download it on another computer with LAN speed.

Thank you, 
Prijic87

---

### Post by Lars Noodén on 2013-06-03
Some objects will have [headers that tell any handlers not to cache](https://en.wikipedia.org/wiki/List_of_HTTP_header_fields#Avoiding_caching) them.  If we use wget to show us the headers from those objects (and dump the content to the bit bucket) then we, unfortunately don't get any clue -- this time.  Maybe some other objects will have those headers set.

```

wget -S -O /dev/null http://metrics.verat.net/speedtest/speedtest/random500x500.jpg?

```

You can use [awk](http://manpages.ubuntu.com/manpages/raring/en/man1/awk.1posix.html) and [uniq](http://manpages.ubuntu.com/manpages/raring/en/man1/uniq.1.html) to help with the search through the access logs for misses in a more automated manner.

```

awk '$4 ~ /^TCP_MISS/ { print $7 }' /var/log/squid3/access.log | uniq -c | less

```

$4 is the 4th column
~ // means search that for a pattern
{} means if that pattern is found, do something
$7 is the 7th column

---

