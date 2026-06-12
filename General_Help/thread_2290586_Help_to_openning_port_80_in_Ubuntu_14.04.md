---
title: "Help to openning port 80 in Ubuntu 14.04"
date: 2015-08-13
forum: General Help
---

### Post by Daniyal_Javani on 2015-08-13
Hello
I want running a home server but can't open port 80. [http://localhost](http://localhost), 127.0.0.1, 192.168.1.2,internet ip address (check via my computer), (even with another computer that connected to my adsl modem router) works but when I check with internet tools like [(http://localhost), 127.0.0.1, 192.168.1.2 works but when I check with internet tools like Open Port Check Tool - Test Port Forwarding on Your Router"]this ]("http://Hello I can't open port 80, [http://localhost)show the port is closed and I can't access to the page behind the internet (another computer) and get Unable to connect error in Firefox and timed out in chrome.
I disable ufw and check with both bridge and pppoe mode of my adsl mode router.
Please tell me if you want additional details!
```
$ sudo netstat -punta | grep 80
tcp        0      0 192.168.1.2:34172       91.189.94.12:80         TIME_WAIT   -               
tcp        0      0 192.168.1.2:36542       91.108.4.10:80          ESTABLISHED 9334/Telegram   
tcp        0      0 192.168.1.2:34184       91.189.94.12:80         TIME_WAIT   -               
tcp        1      0 192.168.1.2:38091       91.189.89.144:80        CLOSE_WAIT  2750/ubuntu-geoip-p
tcp        0      0 192.168.1.2:34171       91.189.94.12:80         TIME_WAIT   -               
tcp        0      0 192.168.1.2:38806       217.12.1.36:80          TIME_WAIT   -               
tcp        0      0 192.168.1.2:43688       64.233.184.95:80        TIME_WAIT   -               
tcp        0      0 192.168.1.2:38811       217.12.1.36:80          TIME_WAIT   -               
tcp        0      0 192.168.1.2:34173       91.189.94.12:80         TIME_WAIT   -               
tcp        0      0 192.168.1.2:43681       64.233.184.95:80        TIME_WAIT   -               
tcp        0      0 192.168.1.2:34170       91.189.94.12:80         TIME_WAIT   -               
tcp        0      0 192.168.1.2:34183       91.189.94.12:80         TIME_WAIT   -               
tcp        0      0 192.168.1.2:34181       91.189.94.12:80         TIME_WAIT   -               
tcp        0      0 192.168.1.2:34169       91.189.94.12:80         TIME_WAIT   -               
tcp        0      0 192.168.1.2:34180       91.189.94.12:80         TIME_WAIT   -               
tcp6       0      0 :::80                   :::*                    LISTEN      2949/apache2

```
Could you please help me?

---

### Post by QDR06VV9 on 2015-08-13
Find the port forwarding settings in your routers admin page and set up a  rule that forwards all incoming traffic on port 80 to your web servers  internal IP address.
Regards

---

### Post by Daniyal_Javani on 2015-08-14
> **runrickus said:**
> Find the port forwarding settings in your routers admin page and set up a  rule that forwards all incoming traffic on port 80 to your web servers  internal IP address.
Regards

Thanks for your attention
I create this rule but still have the same problem
[IMG]http://i.imgur.com/p3EPHhu.png[/IMG]

---

### Post by steeldriver on 2015-08-14
Based on your netstat output, it looks like your webserver is only accepting IPv6 ("tcp6") connections - that may explain why you are seeing different results on your LAN versus WAN

---

### Post by Daniyal_Javani on 2015-08-14
> **steeldriver said:**
> Based on your netstat output, it looks like your webserver is only accepting IPv6 ("tcp6") connections - that may explain why you are seeing different results on your LAN versus WAN

Thanks, do you have any idea to check that or disable ipv6? I can't find any thing about that.

---

### Post by QDR06VV9 on 2015-08-14
See this [https://hackertarget.com/firewalling-ubuntu-ufw-ipv4-ipv6/](https://hackertarget.com/firewalling-ubuntu-ufw-ipv4-ipv6/)
And another helpful link
Firewall UFW Uncomplicated Firewall [https://www.youtube.com/watch?v=nc3A5Dy4xE0](https://www.youtube.com/watch?v=nc3A5Dy4xE0)

---

### Post by Daniyal_Javani on 2015-08-14
> **runrickus said:**
> See this [https://hackertarget.com/firewalling-ubuntu-ufw-ipv4-ipv6/](https://hackertarget.com/firewalling-ubuntu-ufw-ipv4-ipv6/)And another helpful linkFirewall UFW Uncomplicated Firewall [https://www.youtube.com/watch?v=nc3A5Dy4xE0](https://www.youtube.com/watch?v=nc3A5Dy4xE0)

Thanks, excuse me I disable ufw at all, so is it possible that my problem related to iptables?

---

### Post by QDR06VV9 on 2015-08-14
> **Daniyal_Javani said:**
> Thanks, excuse me I disable ufw at all, so is it possible that my problem related to iptables?
Yes iptables.
Have you issued any of the commands from the first link [URL="https://hackertarget.com/firewalling-ubuntu-ufw-ipv4-ipv6/"]https://hackertarget.com/firewalling...ufw-ipv4-ipv6/ 





[/URL]

---

### Post by Daniyal_Javani on 2015-08-14
> **runrickus said:**
> Yes iptables.
Have you issued any of the commands from the first link [URL="https://hackertarget.com/firewalling-ubuntu-ufw-ipv4-ipv6/"]https://hackertarget.com/firewalling...ufw-ipv4-ipv6/ 





[/URL]

Thanks again
I run 
```
sudo ufw enable
sudo ufw default allow 
sudo ufw logging on
tail -f /var/log/syslog
```
And check again but still have the same problem without any log.
Any other idea?

---

### Post by QDR06VV9 on 2015-08-14
I'm not thinking we are on the same page.


Set the default rule, in case you are wondering this should be default DENY.

```
sudo ufw default deny

```
Logging is generally another good idea, lets enable it.

```
sudo ufw logging on
```

If you are connected over SSH then set your SSH allow rule now.

```
sudo ufw allow 22/tcp
```

Now turn the firewall on (this applies the iptables commands).

```
sudo ufw enable
```

To turn the firewall off.

```
sudo ufw disable
```

Allow port 80 (for your webserver to server HTTP).

```
sudo ufw allow 80/tcp
```

Allow port 443 (as we have SSL enabled for our clients security).

```
sudo ufw allow 443/tcp
```

Allow port 25 (for your Email SMTP)

```
sudo ufw allow 25/tcp
```

You get the idea, it is also possible to enable rules that allow and block from specific IP addresses, after all it is just a script for iptables. See the Ubuntu Docs for details on this.

```
sudo ufw status
```

---

### Post by Daniyal_Javani on 2015-08-15
> **runrickus said:**
> I'm not thinking we are on the same page.




I run all these commands but still have the problem.
Is there any test to check if my problem related to my ISP (because my ISP is very strange!)?
Thank you so much

---

### Post by The Cog on 2015-08-15
The screenshot of the router config looks good to me.

The fact that apache is listening on :::80 is not a problem. This listens on both ipv4 and ipv6.

I'm not familiar with UFW, but it shoudl be OK to disable it briefly, as the router is only configured to forward port 80.

It would be useful to take a network trace while someone tries to connect to the server from across the internet. Then we should be able to see if any connect request reaches the server, and whether the server replies in any way. This will help figuer out where the problem lies. Run this command in a console window - and leave it running while someone tries to connect:
**sudo tcpdump -np**
Stop capturing with Ctrl-C when you're done. If you can't understand the trace output, post it here and we will have a look.

---

### Post by Daniyal_Javani on 2015-08-15
> **The Cog said:**
> 
**sudo tcpdump -np**
Stop capturing with Ctrl-C when you're done. If you can't understand the trace output, post it here and we will have a look.

Thanks for your attention
```

$  sudo tcpdump -np
tcpdump: WARNING: eth0: no IPv4 address assigned
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 65535 bytes
^C
0 packets captured
0 packets received by filter
0 packets dropped by kernel


```

Is there any way to check through a client computer? I check with ICMP (ping) and there is no problem with that, but is there any way to check with port 80? can mtr do that with "mtr -p 80"? (I check with mtr and there is no problem)

---

### Post by The Cog on 2015-08-15
Ah, it defaults to eth0. You will need to specify which interface to trace on. Assuming it's eth1, use this:
```
sudo tcpdump -np -i eth1
```

---

### Post by Daniyal_Javani on 2015-08-16
I recently found, as  soon as changing port 80 to 8080 every thing will be OK. Even I check  it with router remote management. Is it possible that this problem  related to ISP?

---

### Post by The Cog on 2015-08-16
Yes it could be. Some ISPs block port 80, or so I have heard. Although how they can do that and still claim to provide internet connectivity is a mystery to me.

---

### Post by QDR06VV9 on 2015-08-16
> **Daniyal_Javani said:**
> I recently found, as  soon as changing port 80 to 8080 every thing will be OK. Even I check  it with router remote management. Is it possible that this problem  related to ISP?

One reason, they don't want you running a web server off of a residential connection.
more info below  but bare in mind I have no first hand knowledge of this kind.
My ISP is blocking port 80

[https://support.sitelutions.com/index.php?/Knowledgebase/Article/View/40/2/my-isp-is-blocking-port-80--how-can-i-host-my-own-site](https://support.sitelutions.com/index.php?/Knowledgebase/Article/View/40/2/my-isp-is-blocking-port-80--how-can-i-host-my-own-site)

[http://faq.dnsexit.com/index.php?action=artikel&cat=3&id=53&artlang=en](http://faq.dnsexit.com/index.php?action=artikel&cat=3&id=53&artlang=en)


[https://www.dnsexit.com/Direct.sv?cmd=webforward](https://www.dnsexit.com/Direct.sv?cmd=webforward)

Might want to check with your ISP first?
Kind Regards

---

