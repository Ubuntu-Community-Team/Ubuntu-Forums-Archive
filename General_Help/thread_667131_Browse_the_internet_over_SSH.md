---
title: "Browse the internet over SSH"
date: 2008-01-14
forum: General Help
---

### Post by TidusBlade on 2008-01-14
I have a server which I use SSH to connect to and control it, and due to my ISP crazily blocking sites, I have decided to use my server to browse the internet, tried a few different ways, and they all dont seem to work properly or I did them wrong. Anyways, I dont want to screw it up or anything now so does anyone know how can I browse the internet over SHH while letting the server do the downloading of the pages and I download it from them or something, in a way that I bypass my ISP's strict filtering?

---

### Post by njparton on 2008-01-14
There would need to be an ssh server at the other end of the connection too.

Every site you wish to view would have to run such a server and that's highly unlikely. The only sites that will do this by default are banks, payment sites (e.g. paypal), any other financial sites or sites that require personal info.

---

### Post by amo-ej1 on 2008-01-14
You could try tunneling through ssh, for example

```

ssh -L 4321:www.google.com:80 user@yourserver

```

This will create a tunnel which maps your local port 4321 to [www.google.com](www.google.com) port 80 but will tunnel through yourserver. A small example using localhost would be

```

ssh -L 4321:www.google.com:80 user@127.0.0.1
wget 127.0.0.1:4321

```

But here is a certain drawback, since you'd need a tunnel for each ip address. So you can only visit one ip address this way. And if that page links an image on another page that image will not be loaded. I would be better if you could be able to connect to a proxy server that way.

---

### Post by TidusBlade on 2008-01-14
Thanks nj for clearing that up, and amo too, didnt know those disadvantages existed :S
But ill still try out your method... 
So it there a way to make it like a proxy, like those proxies you get on other sites, or if anyone knows how can I VPN into the server with a GUI interface?

---

### Post by phillips321 on 2008-01-14
you considered using a proxy to allow you to bypass the isp content filtering?

have a go with one of these [http://www.privax.us/]("http://www.privax.us/"), the popular one is [http://www.hidemyass.com/](http://www.hidemyass.com/)[http://www.hidemyass.com/]("http://www.hidemyass.com/") simply tyoe the domain u want to view in the url box and click hide my ***

---

### Post by TidusBlade on 2008-01-14
I know those proxies, but my ISP blocks proxies by detecting the scripts on the page or something, and I usually use ones that start with **https://**, since they are usually not blocked, but was thinking of using my own server as a proxy or something, unless it takes alot of work or not worth the time since it's the same as other proxies?

---

### Post by phillips321 on 2008-01-14
what about setting up a gui on ur server and vnc into it? im sure as it's a server it has decent upload bandwidth?

---

### Post by jken146 on 2008-01-14
I don't know if this'll work -- it depends on the setup of your ssh server.  Anyway, you could try sshing into the server with X11 forwarding.

```
ssh -Y username@server.domain
```

Then launch a web browser.

```
firefox
```

---

### Post by TidusBlade on 2008-01-14
> **phillips321 said:**
> what about setting up a gui on ur server and vnc into it? im sure as it's a server it has decent upload bandwidth?
Yeah, bandwith exceeds mine by alot so that shouldn't be a problem, but I got no idea how to set up VNC on the server's side :(

Thanks jken, ill try it as soon as I get back home :)

---

### Post by njparton on 2008-01-14
> **jken146 said:**
> I don't know if this'll work -- it depends on the setup of your ssh server.  Anyway, you could try sshing into the server with X11 forwarding.

```
ssh -Y username@server.domain
```

Then launch a web browser.

```
firefox
```


But how does that effect the server to internet connection which is what he's trying to encrypt?

---

### Post by phillips321 on 2008-01-16
make sure the server has a gui, if it doesn't then run this command when connected over ssh
```
sudo apt-get install gnome-core gdm gnome-system-monitor gnome-system-tools xarchiver x-window-system-core synaptic
```
that will give you a base system.

then you must install x11vnc
```
sudo apt-get install x11vnc
```

the once installed create a password
```
sudo vncpasswd
```

then run the vnc server
```
x11vnc
```

to edit some of the options create a fille named "~/.x11vncrc" and add some options from
[http://www.karlrunge.com/x11vnc/](http://www.karlrunge.com/x11vnc/)[http://www.karlrunge.com/x11vnc/]("http://www.karlrunge.com/x11vnc/")

---

### Post by jeffus_il on 2008-01-16
Seems like VPN is your way to go, use synaptic to find vpn software for your client and server.

---

### Post by TidusBlade on 2008-01-16
Thanks, hope I can get the GUI working without much hassle ^_^

---

### Post by apfsdsdu on 2008-01-16
You can use ssh as a SOCKS proxy. 
```
ssh -D 9000 server.ip
```
And then configure your browser to use a SOCKS proxy at localhost:9000

---

### Post by TidusBlade on 2008-01-16
Thanks apf, ill try it out, sounds promising :)

---

### Post by bubbalouie on 2008-01-16
> **TidusBlade said:**
> I have a server which I use SSH to connect to and control it, and due to my ISP crazily blocking sites, I have decided to use my server to browse the internet, tried a few different ways, and they all dont seem to work properly or I did them wrong. Anyways, I dont want to screw it up or anything now so does anyone know how can I browse the internet over SHH while letting the server do the downloading of the pages and I download it from them or something, in a way that I bypass my ISP's strict filtering?
I have a system set up with as a server which runs SSH and squid. I can connect to it from work etc via SSH and tunnel to the squid proxy, there is no real way to tell the difference between a normal SSH session and what I am doing, it gets past content filters with ease as all the traffic is totally encrypted.

This can be done on both windows (putty) and *nix (SSH), unfortunately I configured it in a fashion that is a bit adhoc and don't recall the exact details but I'll we see if I can dig up the necessary SSH commands when I get to work tomorrow.

Off hamd ** sudo apt-get install squid** installs squid, you then need to configure it, here is my /etc/squid/squid.conf file:

```
http_port 3128

#by ryan
visible_hostname localhost
#end by ryan

hierarchy_stoplist cgi-bin ?
acl QUERY urlpath_regex cgi-bin \?
cache deny QUERY
acl apache rep_header Server ^Apache
broken_vary_encoding allow apache
access_log /var/log/squid/access.log squid
hosts_file /etc/hosts
refresh_pattern ^ftp:		1440	20%	10080
refresh_pattern ^gopher:	1440	0%	1440
refresh_pattern .		0	20%	4320
acl all src 0.0.0.0/0.0.0.0
acl manager proto cache_object
acl localhost src 127.0.0.1/255.255.255.255
acl to_localhost dst 127.0.0.0/8
acl SSL_ports port 443		# https
acl SSL_ports port 563		# snews
acl SSL_ports port 873		# rsync
acl Safe_ports port 80		# http
acl Safe_ports port 21		# ftp
acl Safe_ports port 443		# https
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

#by ryan
acl Safe_ports port 2082         # uTorrent
#end by ryan

acl purge method PURGE
acl CONNECT method CONNECT
http_access allow manager localhost
http_access deny manager
http_access allow purge localhost
http_access deny purge
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports
http_access allow localhost
http_access deny all
icp_access allow all
coredump_dir /var/spool/squid
extension_methods REPORT MERGE MKACTIVITY CHECKOUT

```

As far as I can tell that should sort you out, basically you tunnel to port 3128 on the server from where ever using SSH (ONLY FORWARD YOUR SSH PORT in your gateway, it is better to use a weird SSH port on your gateway too, I have had a few people try dictionary attacks), that way no one can tell it is a proxy (well most people anyway). The main benefits here are, relatively low bandwidth requirements to do this, and total privacy when using public networks.

Good luck

My SSH command:

ssh -C -X -L 3128:localhost:3128 <MY SERVER ADDRESS> -p <MY SSH PORT> -l <MY USER>

As a side note I use dyndns.org to set up a domain name as I use a dynamic IP with my ISP, this way I have a simple domain name.

---

### Post by Vajk on 2008-03-15
> **TidusBlade said:**
> Thanks apf, ill try it out, sounds promising :)

I was thinking to try out something similar. The only difference is that I would like to connect from my work to my home linux box. Our proxy at work blocks a lot of things. A few weeks ago I could listen to internet radio but now the adress is blocked. Others are watching youtube videos, so I think it's not really a bandwith problem. 
Could you setup your server to ssh to it ? If you want gui I could recommend [FreeNX]("http://www.nomachine.com/download.php") from NoMachine. It's encrypted traffic on default. 
In my case the ssh is blocked also, maybe on one of the ports I could go out. Our proxy server port is 8080. Unfortunately I don't know to much about proxies, if they can block connection types (ssh in this case) also or just IPs. For example we were using [Yourfreedom]("http://www.your-freedom.net/") but yesterday I found out that somehow they could block that also.

---

### Post by kevdog on 2008-03-16
If you are lucky to have a router that you can flash with the dd-wrt firmware, this basically takes out the need for a second computer.  Because the router runs a ssh daemon (if activated), its possible remotely to ssh into the box, and then establish a SOCKS proxy from the client to your personal router.  The benefit of doing this, is that the connection between client and router is encrypted. (Good for Wireless Hot Spots such as cafe's).  Because the sshd is on the router, you don't have to worry about leaving a computer on all the time either.  A very low cost, low power consumption alternative.  Not as robust as running a full blown proxy server such as squid, but very economical.

---

### Post by Vajk on 2008-03-16
> **kevdog said:**
> If you are lucky to have a router that you can flash with the dd-wrt firmware, this basically takes out the need for a second computer.  Because the router runs a ssh daemon (if activated), its possible remotely to ssh into the box, and then establish a SOCKS proxy from the client to your personal router.  The benefit of doing this, is that the connection between client and router is encrypted. (Good for Wireless Hot Spots such as cafe's).  Because the sshd is on the router, you don't have to worry about leaving a computer on all the time either.  A very low cost, low power consumption alternative.  Not as robust as running a full blown proxy server such as squid, but very economical.

Thanks, it surely would be a nice alternative. I checked their website and it looks really interesting. I have a SpeedTouch 780, sort of a modem and router combo, my ISP installed it. I don't think this would be compatible with the firmware but I'll bookmark it for future. I won't stick to long with this ISP anyway, it's not the best deal on the market, I only have a few months left from the contract. 
If this works - which I believe it is - then you could use your home connection - if it's fast enough - from anywhere on the road to have a secure connection.

---

### Post by kevdog on 2008-03-17
> If this works - which I believe it is - then you could use your home connection - if it's fast enough - from anywhere on the road to have a secure connection.

Yes ssh tunneling is a beautiful thing.  The only benefit to having ssh capabilities on the router rather than on a computer sitting behind the router is that you dont have to leave the computer on all the time -- saves energy.

---

### Post by sirlancelot on 2008-04-29
> **apfsdsdu said:**
> You can use ssh as a SOCKS proxy. 
```
ssh -D 9000 server.ip
```
And then configure your browser to use a SOCKS proxy at localhost:9000This is just what I was going to say!

[Lifehacker](http://lifehacker.com/) has a more refined walkthrough (for Window$, but it's still SSH): [Encrypt your web browsing session with SSH (link)](http://lifehacker.com/software/notag/geek-to-live--encrypt-your-web-browsing-session-with-an-ssh-socks-proxy-237227.php)

---

### Post by skibrianski on 2008-07-21
> **apfsdsdu said:**
> You can use ssh as a SOCKS proxy. 
```
ssh -D 9000 server.ip
```
And then configure your browser to use a SOCKS proxy at localhost:9000

Thanks apfsdsdu, i was looking for that...

---

