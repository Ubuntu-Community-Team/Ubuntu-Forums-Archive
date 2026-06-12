---
title: "Can't ssh to ubuntu server anymore"
date: 2013-01-06
forum: General Help
---

### Post by helal on 2013-01-06
first, I am fairly new to linux and just experimenting. With help of friend, we setup an ubuntu 12.x server and everything was going just fine. I could ssh on port 22. Yesterday, I installed webmin and wondershaper to perhaps do easier admin and control upload and download speed. I rebooted the server and now I can't ssh any more. the message says connection on the server on port 22 is refused. Any help will be greatly appreciated but please be reminded that I am fairly new and need detailed instructions. I am using my mac to ssh to the server.

Thank You, 

Helal

---

### Post by Cheesehead on 2013-01-06
Well, unless you can access the server via webmin, you need to go over and hook a monitor and keyboard up to the server.

Maybe it didn't boot after the changes. Webmin isn't supported in Ubuntu.
Maybe it errored.
Maybe you changed a setting that closed the port.

---

### Post by steeldriver on 2013-01-06
iirc you also get 'connection refused' if the ssh service simply isn't running

---

### Post by conradin on 2013-01-06
open up "networking tools"
and do a port scan, see if the port is open.
also, use the look up tools to see whats running. 
This tool is for windows, but is nice:
[http://download.cnet.com/Whats-running-on-that-server/3000-18506_4-11204.html](http://download.cnet.com/Whats-running-on-that-server/3000-18506_4-11204.html)
If i knew a linux equal I would point you to that.

---

### Post by steeldriver on 2013-01-06
There's nmap

```
nmap -T4 -A *remotehost*
```

---

### Post by helal on 2013-01-06
well, I am doing a port scan from my mac to see what ports are open. I can login to my Apache server though but not ssh. Server site is [www.gorgybarfi.com](www.gorgybarfi.com).

---

### Post by helal on 2013-01-06
after forwarding port 10000 for webmin, I was able to login via webmin....now what do I need to do to not mess up more and make sure ssh server is running and port 22 is open?

---

### Post by fdrake on 2013-01-06
> 
Nmap scan report for [www.gorgybarfi.com](www.gorgybarfi.com) (66.7.124.42)
Host is up (0.44s latency).
Not shown: 995 filtered ports
PORT     STATE  SERVICE
[COLOR="Red"]**22/tcp   closed ssh**[/COLOR]


ssh port is closed

---

### Post by helal on 2013-01-06
how do I open it via webmin? I do see the Start Server (ssh) on SSH Server screen. However, when I click on Start Server, it doesn't do anything. I tried to do port forwarding of ssh to 24 and login with no avail.

---

### Post by tgalati4 on 2013-01-06
Did you start a firewall?  If you have a firewall running, you need to poke a hole to allow port 22 (ssh) traffic.

---

### Post by helal on 2013-01-07
everything was the same except that I installed wondershaper to control bandwidth, reboot the server and no longer could ssh. as far as firewal, I didn't install any...two packages that I insatlled bedoer losing ssh connection were webmin and wondershare.

---

