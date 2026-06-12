---
title: "Python simple http server help"
date: 2020-03-23
forum: General Help
---

### Post by r0ckst4r on 2020-03-23
I am running Ubuntu 16.04 on a desktop.  I just wanted make a simple server to share some files with other systems on my home network so here is what I used

```
python -m SimpleHTTPServer 8000

```

and what I get

```
Serving HTTP on 0.0.0.0 port 8000 ...
```

If I access 0.0.0.0:8000 on firefox on my Ubuntu machine that is running the server I get access to the files exactly as expected however if I try from any other laptop or my Android phone I get "ERR_CONNECTION_REFUSED."  I suspect that something is blocking the connection so I checked the firewall

```
sudo ufw status
Status: inactive

```

I imagine that it is my wireless router blocking the port or I just do not know the proper syntax to access this server.  I tried using 0.0.0.0:8000 as well as my machines IP address at port 8000 and even me routers IP address at port 8000.  Any help would be appreciated as it's clear I am missing something fundamental.

---

### Post by TheFu on 2020-03-23
You need to use the specific ip for the ubuntu machine.  Best if it is setup as a static ip.
0.0.0.0 is not a valid ip.
```
$  ip addr 
```
will show the ip address.

if you plan to do any network configurations, you'll want a better understanding of both ipv4 and ipv6 networking. 
[https://web.stanford.edu/class/msande91si/www-spr04/readings/week1/InternetWhitepaper.htm](https://web.stanford.edu/class/msande91si/www-spr04/readings/week1/InternetWhitepaper.htm)

Most LAN ips will begin with 192.168.x.x or 10.x.x.x or 172.16.x.x.  These are all private address spaces by world-wide agreement. They cannot be used on the internet, just on internal LANs.

---

### Post by HermanAB on 2020-03-24
0.0.0.0 means either all addresses, or invalid address.

You cannot use it as a destination address.

---

### Post by r0ckst4r on 2020-03-24
I suppose I was not clear.  Yes, i already did try to use my machine's IP as well as trying the router IP which yielded the same results.

---

### Post by HermanAB on 2020-03-24
Can you ping or traceroute the machine?

---

### Post by r0ckst4r on 2020-03-24
> **HermanAB said:**
> Can you ping or traceroute the machine?

Not sure I know how.  Just for some more clarification, I'm running Ubuntu on my desktop which is what I am starting the python simple http server on in terminal.  I have a non-linux laptop and an android phone which I am trying to access the server through.  The only time I have managed to "connect" to the server was not really a connection since I was using firefox on the machine that was running the server.  My laptop and phone seem to keep getting blocked.

---

### Post by TheFu on 2020-03-24
Exactly what URL is being used?

Certain versions of Android can only locate other systems using DNS names. if you don't have DNS running on your LAN, configured for all the systems there, then it won't work w/o rooting the device.

Every networked OS has a ping command.

---

### Post by r0ckst4r on 2020-03-24
I solve the issue.  A stupid problem as I imagined.  I was using the IP address provided by my ISP (I was just googling "find my IP address").  When I used the IP address from the code you posted it worked perfectly.  Thank you for the help.

---

