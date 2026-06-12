---
title: "How to change my DNS settings on Ubuntu"
date: 2015-10-11
forum: General Help
---

### Post by mhi2 on 2015-10-11
I've setup OpenDNS on my home router and set the security to high to block Facebook, YouTube after school.

On my Ubuntu laptop where I have admin access, I went to Network connections, selected my WiFi network and under IPV4 settings, I selected Automatic (DHCP) address only and set the Google DNS server of 8.8.8.8 under DNS servers.  I then disconnected my WiFi connection, reconnected and ran nmcli dev list iface wlan0 | grep IP4.DNS from terminal to confirm my DNS is 8.8.8.8.

However, when I go to YouTube, the site is still blocked.

Could someone help me correctly change my DNS settings on my laptop so that I can bypass OpenDNS.

Thank you

---

### Post by ajgreeny on 2015-10-11
As I understand things if your router uses openDNS of 8.8.8.8 it will not matter what the laptop is set to as openDNS will always be what is used when connected to that router.

I don't think there is any way around that, unless, of course, I have misunderstood what you want.

---

### Post by Ubunterrific on 2015-10-11
Hang on a sec, aren't **8.8.8.8** and **8.8.4.4** infact 'Google Public DNS' servers? OpenDNS has **208.67.222.222** and[B] 208.67.220.220 :P 

[/B]Since those are the actual addresses, give those a try. You can also change these settings in your router by selecting manual DNS addresses - and you can also block websites via the router's interface too, as it happens ;)

---

### Post by Ubunterrific on 2015-10-11
lol it's funny, the more i read OP's post, the more it sounds like someone **else **set up openDNS to block youtube/facebook (parent(s)?) and OP is trying to get around them. That's it isn't it :popcorn:

If this happens to be the case...try a proxy or something (as mentioned, I think it's correct to say that the router's DNS settings override the individual connectors' settings)
There's also tor and i think bypassing DNS altogether by loading pages from their IP will work - but consider your education, those blocks are probably for the best if you're addicted to YT and FB :o Parents know best ):P

---

### Post by mhi2 on 2015-10-11
@Ubunterrific Let me start by saying I am the parent :)

Perhaps I wasn't very clear in my original post as I see there was a bit of confusion as to what I need:

1.  On my router, I have set the DNS servers to point to the OpenDNS Servers (208.67.222.222 and 208.67.220.220).  My kids no longer have access to YouTube and social media.  The problem is I don't have access either.

2.  So, on my Ubuntu laptop, I went to Network Connections and for the WiFi connection that I used, I pointed the DNS server to the Google DNS server 8.8.8.8.

3.  When I run nm-tool | grep DNS from a terminal session, the output is DNS: 8.8.8.8

4.  When I go to YouTube, I still get a message that it is blocked by OpenDNS.  In other words, instead of using the DNS setting that I set on my Ubuntu laptop, it is using the DNS setting on the router. 

Should not the laptop settings now allow me access?

Thank you

---

### Post by papibe on 2015-10-11
Hi mhi2.

Could you open a terminal, run these commands, and post back the results? (Please copy/paste the text and use CODE tags)
```
nm-tool

nslookup youtube.com

dig youtube.com
```
Regards.

---

### Post by mhi2 on 2015-10-11
Hi,

Here is the output from the 3 commands.

I hope I have done the code tags correctly

```
administrator@administrator:~$ nm-tool

NetworkManager Tool


State: connected (global)


- Device: wlan0  [Wi-Fi connection 1] ------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        A7:CC:C2:FC:89:EA


  Capabilities:
    Speed:           144 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    <Removed>


  IPv4 Settings:
    Address:         10.1.1.7
    Prefix:          24 (255.255.255.0)
    Gateway:         10.1.1.11


    DNS:             8.8.8.8




- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        A2:28:68:82:F7:82


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


*******


administrator@administrator:~$ nslookup youtube.com
Server:        127.0.1.1
Address:    127.0.1.1#53


Non-authoritative answer:
Name:    youtube.com
Address: 24.244.19.167
Name:    youtube.com
Address: 24.244.19.157
Name:    youtube.com
Address: 24.244.19.173
Name:    youtube.com
Address: 24.244.19.153
Name:    youtube.com
Address: 24.244.19.172
Name:    youtube.com
Address: 24.244.19.178
Name:    youtube.com
Address: 24.244.19.177
Name:    youtube.com
Address: 24.244.19.182
Name:    youtube.com
Address: 24.244.19.148
Name:    youtube.com
Address: 24.244.19.158
Name:    youtube.com
Address: 24.244.19.187
Name:    youtube.com
Address: 24.244.19.163
Name:    youtube.com
Address: 24.244.19.168
Name:    youtube.com
Address: 24.244.19.183
Name:    youtube.com
Address: 24.244.19.162
Name:    youtube.com
Address: 24.244.19.152

administrator@administrator:~$ dig youtube.com


; <<>> DiG 9.9.5-3ubuntu0.5-Ubuntu <<>> youtube.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 64476
;; flags: qr rd ra; QUERY: 1, ANSWER: 16, AUTHORITY: 0, ADDITIONAL: 1


;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 1280
;; QUESTION SECTION:
;youtube.com.			IN	A


;; ANSWER SECTION:
youtube.com.		226	IN	A	24.244.19.158
youtube.com.		226	IN	A	24.244.19.187
youtube.com.		226	IN	A	24.244.19.163
youtube.com.		226	IN	A	24.244.19.168
youtube.com.		226	IN	A	24.244.19.183
youtube.com.		226	IN	A	24.244.19.162
youtube.com.		226	IN	A	24.244.19.152
youtube.com.		226	IN	A	24.244.19.167
youtube.com.		226	IN	A	24.244.19.157
youtube.com.		226	IN	A	24.244.19.173
youtube.com.		226	IN	A	24.244.19.153
youtube.com.		226	IN	A	24.244.19.172
youtube.com.		226	IN	A	24.244.19.178
youtube.com.		226	IN	A	24.244.19.177
youtube.com.		226	IN	A	24.244.19.182
youtube.com.		226	IN	A	24.244.19.148


;; Query time: 13 msec
;; SERVER: 127.0.1.1#53(127.0.1.1)
;; WHEN: Sun Oct 11 14:39:11 PDT 2015
;; MSG SIZE  rcvd: 296

```

---

### Post by papibe on 2015-10-11
It looks OK from here.

The browser may be having a cache of the previous resolved addresses. Try restarting the browser, and may be even cleaning up the history (if that doesn't produce you any problems).

Hope it helps. Let us know how it goes.
Regards.

P.S.: you may want to add a second Google DNS. The standard is to add both **8.8.8.8** and **8.8.4.4**

---

### Post by Ubunterrific on 2015-10-11
> **mhi2 said:**
> **@Ubunterrific Let me start by saying I am the parent** :)




LOL! Delicious :D

As an aside, on the router, provided you are able to tolerate assigning connecting device on the LAN to a specific address (e.g. **192.168.0.4**), you can tell the router to block access to certain websites for anyone connected at 192.168.0.4. 
OR more stringently, but a lot easier, you could block access to youtube.com e.t.c. for *everyone* on the LAN **except **e.g.**192.168.0.10** and just ass[FONT=arial]ign your [/FONT]device's MAC address to always get 192.168.0.10 via DHCP (in your case, you would set [FONT=arial]A7:CC:C2:FC:89:EA to always get it) (then manually punch those numbers into NetworkManager. Netmask is probably **255.255.255.0** (check on "Connection Information") and the default route is just whatever the router's address is e.g. **192.168.1.1 **or similar)[/FONT]

Web browsers (i know firefox does at least) do cache DNS related entries. You could try disabling it temporarily by setting **network.dnsCacheEntries** to **0** if flushing its cache isn't working (assuming you're on firefox!)

---

### Post by mhi2 on 2015-10-11
@papibe, thanks for the tips, I did try restarting the browser and clearing history, no luck.  

@Ubunterric, I know I can block individual pages through the router, but I'd prefer to use a service like OpenDNS so that I can keep the kids away from other less desirable places on the net as well.

I am really at a loss as to why this is not working.  

1.  Is there an option like on Windows where you can flush the DNS?
2.  I noticed that the logs posted show 127.0.0.1 before it goes out to the net.  Could this be manually changed to point to 8.8.8.8?  Just a thought

administrator@administrator:~$ nslookup youtube.com
Server:        127.0.1.1
Address:    127.0.1.1#53

---

### Post by Ubunterrific on 2015-10-11
What's written in /etc/resolv.conf? Try changing to read 
```

nameserver 8.8.8.8
nameserver 8.8.4.4 
``` Think that ought to do it.

Assuming you're not using BIND9 e.t.c. ```
sudo /etc/init.d/nscd restart
``` should flush since something's caching.

You can also do ```
dig @8.8.8.8 www.something-here.com
``` to try pinging a site using a different DNS server like 8.8.8.8

---

### Post by mhi2 on 2015-10-11
> **Ubunterrific said:**
> What's written in /etc/resolv.conf? Try changing to read 
```

nameserver 8.8.8.8
nameserver 8.8.4.4 
``` Think that ought to do it.

My resolve.conf currently shows ```
nameserver 127.0.1.1
```.  I can change it to 8.8.8.8 and 8.8.4.4 but I it won't let me save the file with the same file name.  I'm assuming it is a read only file.  When I right click on it, all of the permissions are greyed out and it says "You are not the owner so you cannot change these permissions".

> Assuming you're not using BIND9 e.t.c. ```
sudo /etc/init.d/nscd restart
``` should flush since something's caching.

I'm not sure what Bind9 is.  I am essentially running a vanilla version of Ubuntu 14.04.

> You can also do ```
dig @8.8.8.8 www.something-here.com
``` to try pinging a site using a different DNS server like 8.8.8.8

Here is the output from the dig command

```
administrator@administrator:~$ dig @8.8.8.8 www.google.com

; <<>> DiG 9.9.5-3ubuntu0.5-Ubuntu <<>> @8.8.8.8 www.google.com
; (1 server found)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 58809
;; flags: qr rd ra; QUERY: 1, ANSWER: 16, AUTHORITY: 0, ADDITIONAL: 1


;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 1280
;; QUESTION SECTION:
;www.google.com.			IN	A


;; ANSWER SECTION:
www.google.com.		300	IN	A	24.244.19.173
www.google.com.		300	IN	A	24.244.19.168
www.google.com.		300	IN	A	24.244.19.162
www.google.com.		300	IN	A	24.244.19.148
www.google.com.		300	IN	A	24.244.19.167
www.google.com.		300	IN	A	24.244.19.152
www.google.com.		300	IN	A	24.244.19.177
www.google.com.		300	IN	A	24.244.19.157
www.google.com.		300	IN	A	24.244.19.178
www.google.com.		300	IN	A	24.244.19.153
www.google.com.		300	IN	A	24.244.19.172
www.google.com.		300	IN	A	24.244.19.158
www.google.com.		300	IN	A	24.244.19.182
www.google.com.		300	IN	A	24.244.19.183
www.google.com.		300	IN	A	24.244.19.187
www.google.com.		300	IN	A	24.244.19.163


;; Query time: 77 msec
;; SERVER: 8.8.8.8#53(8.8.8.8)
;; WHEN: Sun Oct 11 19:02:28 PDT 2015
;; MSG SIZE  rcvd: 299

```

---

### Post by Ubunterrific on 2015-10-11
> **mhi2 said:**
> My resolve.conf currently shows ```
nameserver 127.0.1.1
```.  I can change it to 8.8.8.8 and 8.8.4.4 but I it won't let me save the file with the same file name.  I'm assuming it is a read only file.  When I right click on it, all of the permissions are greyed out and it says "You are not the owner so you cannot change these permissions".


change it via

```
sudo gedit /etc/resolv.conf
```
which will give you permission to edit and save the file.

---

### Post by mhi2 on 2015-10-12
> **Ubunterrific said:**
> change it via

```
sudo gedit /etc/resolv.conf
```
which will give you permission to edit and save the file.

I found some instructions to create a static resolv.conf file here [http://askubuntu.com/questions/627899/nameserver-127-0-1-1-in-resolv-conf-wont-go-away](http://askubuntu.com/questions/627899/nameserver-127-0-1-1-in-resolv-conf-wont-go-away) and these instructions did exactly what they said they would.

However, the OpenDNS DNS settings on the router still supersede the settings on my laptop.

Is it possible that the router settings take precedence over what is set on the PC?  From everything that I read on the OpenDNS forum, setting the DNS settings on the PC to Google's DNS should work as a workaround.

---

### Post by SeijiSensei on 2015-10-12
Any changes you make to /etc/resolv.conf will be overwritten at reboot.  To force nameservers, the simplest solution is to edit the file /etc/resolvconf/resolv.conf.d/head which is used to construct resolv.conf at boot.  The default file simply contains these comment lines:
```

# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN

```
You'll see these same lines at the top of /etc/resolv.conf.  Simply add the nameserver(s) you want to use below those lines in the "head" file:
```

# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 8.8.8.8
nameserver 8.8.4.4

```
Now reboot.  You should see both these servers listed above "nameserver 127.0.1.1."  You can delete the comments from the head file if you like.

---

### Post by btindie on 2015-10-12
Ubuntu runs it's own local caching dns server ( dnsmasq ) which is why you're seeing
```
nameserver 127.0.0.1
```
in your /etc/resolv.conf file.

When you connect to a network, NetworkManager will send the DNS setting to dnsmasq via DBus. You can view the settings it gets by looking in syslog
```
grep dnsmasq /var/log/syslog{,.1}
```
That will check the files /var/log/syslog and /var/log/syslog.1 in case it's recently been rotated.

If you use *curl* you can eliminate your browser as being the issue.
```
 curl -s -i https://www.youtube.com | less
```
you should get the HTML page and it shouldn't mention anything about it being blocked.

Have you got any plugins installed that could be causing the issue?

---

### Post by mhi2 on 2015-10-12
Thanks everyone for your suggestions and input.

I only have two more questions and then I guess I will give up on this :(

1.  Is it possible that my router DNS is superseding the DNS settings that are setup on my laptop.  Below is the output from a terminal command that seems to show everything is setup correctly.

administrator@administrator:~$ nmcli dev list iface wlan0 | grep IP4
IP4.ADDRESS[1]:                         ip = 10.1.1.9/24, gw = 10.1.1.11
IP4.DNS[1]:                             8.8.8.8
administrator@administrator:~$

2.  Is there any command that would let me see whether my laptop is using the laptop or the router DNS settings?

Thank you

---

### Post by SeijiSensei on 2015-10-12
```

$ nslookup www.google.com
Server:         127.0.1.1
Address:        127.0.1.1#53

Non-authoritative answer:
Name:   www.google.com
Address: 216.58.219.196

```
My machine is using the local dnsmasq server at 127.0.1.1.

If I edit the "head" file to add Google's servers as I described above, and restart resolvconf with "sudo service resolvconf restart", I get:
```

$ nslookup www.google.com
Server:         8.8.8.8
Address:        8.8.8.8#53

Non-authoritative answer:
Name:   www.google.com
Address: 216.58.219.228

```

---

### Post by mhi2 on 2015-10-12
> **SeijiSensei said:**
> ```

$ nslookup www.google.com
Server:         127.0.1.1
Address:        127.0.1.1#53

Non-authoritative answer:
Name:   www.google.com
Address: 216.58.219.196

```
My machine is using the local dnsmasq server at 127.0.1.1.

If I edit the "head" file to add Google's servers as I described above, and restart resolvconf with "sudo service resolvconf restart", I get:
```

$ nslookup www.google.com
Server:         8.8.8.8
Address:        8.8.8.8#53

Non-authoritative answer:
Name:   www.google.com
Address: 216.58.219.228

```

I received the exact same output as you did (see below) so it does look like my laptop is set correct.  Is it safe to assume then that in my situation, the router DNS is superseding the laptop DNS settings for whatever reason and there is no way around this?

Is there some kind of a packet sniffer that would let me tell just where the DNS information is coming from.  It's not so much that I have to get this to work, but more than anything, I've always been a tinkerer and am more curious as to why this isn't working.

administrator@administrator:~$ nslookup [www.google.com]("http://www.google.com")
Server:        8.8.8.8
Address:    8.8.8.8#53


Non-authoritative answer:
Name:    [www.google.com]("http://www.google.com")
Address: 24.244.19.216

---

### Post by SeijiSensei on 2015-10-12
[Your problem is with ShawCable]("http://www.dslreports.com/forum/r28361850-BC-Shaw-DNS-redirect-for-google").  While some people in that thread claim what Shaw is doing isn't "hijacking," it sure looks that way to me.

Here's what I see for that address you posted, and what should be the results for [www.google.com:](www.google.com:)
```

$ host 24.244.19.216 
Host 216.19.244.24.in-addr.arpa. not found: 3(NXDOMAIN)

$ host www.google.com
www.google.com has address 173.194.123.52
www.google.com has address 173.194.123.50
www.google.com has address 173.194.123.49
www.google.com has address 173.194.123.51
www.google.com has address 173.194.123.48
www.google.com has IPv6 address 2607:f8b0:4006:80d::1010

```

I use Verizon FiOS here in the US and see none of the shenanigans that Shaw engages in.  Shaw appears to be intercepting all requests on port 53 and responding to them rather than letting them get to the actual nameservers upstream.

As I see it, you only have a couple of options.  Get a less intrusive provider, or set up an virtual machine at some place like Linode or AWS and route your DNS queries to it over a virtual private network using OpenVPN.

---

### Post by tristan16 on 2015-10-12
After all this complicated computer talk, this is going to sound insanely stupid: Have you tried using Manual setup instead of Automatic Addresses Only?

I have Google Public DNS set up on my computer, and our router is set up to automatically use the ISP DNS. In my settings, I manually specified the router address, netmask, gateway, and DNS servers. My computer uses Google Public DNS and all other devices use TWC.

---

