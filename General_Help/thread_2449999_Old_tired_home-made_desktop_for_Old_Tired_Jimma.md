---
title: "Old tired home-made desktop for Old Tired Jimma"
date: 2020-09-05
forum: General Help
---

### Post by Old Jimma on 2020-09-05
Hi Forums

My home made desktop is old: I made it in 2013 from very inexpensive new parts.

It was nice and snappy in its day.

But now, URLS fail to resolve quickly on fire fox.... can take a minute or more, and stuff is just slow. For example, it takes my calculator app approx 7  sec to start.

However, it still works.

It does have private data on it however, and I'd hate for the computer to die. I keep daily and monthly backups.

Is it time to cash in my old computer and get a new one?

Thanks,
Old Old Old Old Jimma from the Old Country

---

### Post by Frogs Hair on 2020-09-05
Please post information about your computer hardware.

---

### Post by CatKiller on 2020-09-05
Seconding Frogs Hair's recommendation to tell us what the hardware is.

2013 would have been Haswell-era, which should be fine. I retired a Sandy Bridge system recently, and that was only because it actually died; it was still an adequate machine.

Browsers (or, rather, script-heavy websites) need RAM. Your issue there, though, sounds like a network problem rather than performance.

If you're using 18.04, as your profile suggests, the Gnome flavour came with the calculator application as a snap, as a means to test snaps in the real world. One of the less-desirable aspects of snaps is their incredibly long initial startup time.

---

### Post by Old Jimma on 2020-09-05
I think in good hands with a frog and a cat helping me out! They are my favorite extraterrestrials!

Here is what I have. It cost me 339 smackers. I thought it was alot of money at the time.

**SSD where the operating system is:**
Kingston HyperX 3K SH103S3/120G 2.5" 120GB SATA III MLC
Internal Solid State Drive

**Mother Board**
ASUS M5A97 LE R2.0 AM3+ AMD 970 SATA 6Gb/s USB 3.0 ATX
AMD Motherboard with UEFI BIOS

**Processor**
AMD Phenom II X4 965 Black Edition Deneb 3.4GHz Socket AM3
125W Quad-Core Processor HDZ965FBGMBOX
[B]
Memory[/B]
CORSAIR Vengeance 8GB (2 x 4GB) 240-Pin DDR3 SDRAM
DDR3 1600 (PC3 12800) Desktop Memory Model

**Video Card**
ASUS GT610-2GD3-CSM GeForce GT 610 2GB 64-bit DDR3 PCI
Express 2.0 x16 HDCP Ready Video Card

**Power Supply**
Antec BP550 Plus 550W Continuous Power
Power Supply


Old Jimma from the Old Country
Motto: "[COLOR="#0000CD"]**Been here since 6.04**[/COLOR]"

---

### Post by HermanAB on 2020-09-05
My 2012 Macbook works better than when it was new.

Modern desktop systems are slow for a multitude of reasons.  

If you want your machine to zoom faster than ever, install Slackware, OpenBSD or Xubuntu. 
(Xubuntu is a lot slower than the other two, though orders of magnitude better than Ubuntu with Gnome).

---

### Post by SeijiSensei on 2020-09-05
The machine I'm using right now is about a year younger than yours and displays none of problems you described.  I did upgrade it recently to 16GB of memory, but that was mostly to support virtualization. It was running fine with 8GB before. I have an older laptop that predates your machine and also works fine. All of them are running Kubuntu 20.04.

Let's start with investigating those lengthy DNS lookups.  Try this:
```

cd /etc
sudo mv resolv.conf resolv.conf.old
sudo echo 'nameserver 8.8.8.8' > resolv.conf

```
Now try going somewhere on the Internet. Any faster?

What are your times for "ping 8.8.8.8"?  I get about 24 ms or less.

After testing,
```
sudo rm -f resolv.conf
sudo mv resolv.conf.old resolv.conf

```
to revert to your prior installation.

Does your machine get its DNS server from your router at boot via DHCP?  If so, and if you can access the router's configuration, make sure all the DNS servers it offers during the DHCP handshake are working properly. To test, run "host [www.google.com](www.google.com) ip.addr.of.nameserver".

---

### Post by Old Jimma on 2020-09-05
SeijiSensei!!

Wow!! That worked better than my home-made behind-the-shed rheumatism  and all-around miracle elixir, by jiminy!!

And quicker thanb greased lightnin', to,  even with my VPN!!

Talk about speedy! Sure i'll see you at the speed races at the next Ubuntu Olympics!

You asked, " Does your machine get its DNS server from your router at boot via DHCP? If so, and if you can access the router's configuration, make sure all the DNS servers it offers during the DHCP handshake are working properly. To test, run "host [www.google.com](www.google.com) ip.addr.of.nameserver"."

My reply is: What's that? I guess I don't know! And I don't kn ow what "ip.addr.of.nameserver" could be. :-(

Pretty happy right now, SeijiSensei!!

Many thanks! If you are ever in the neighborhood drop by for coffee and a doughnut (with a all-around miracle elixir chaser to get your day goin' right!)

THANK YOU!!

Younger than Springtime Old Jimma from the Old Country

---

### Post by Old Jimma on 2020-09-05
here is the output

**host [www.google.com](www.google.com) 1.1.1.1**
Using domain server:
Name: 1.1.1.1
Address: 1.1.1.1#53
Aliases: 

[www.google.com](www.google.com) has address 64.233.177.106
[www.google.com](www.google.com) has address 64.233.177.104
[www.google.com](www.google.com) has address 64.233.177.147
[www.google.com](www.google.com) has address 64.233.177.99
[www.google.com](www.google.com) has address 64.233.177.105
[www.google.com](www.google.com) has address 64.233.177.103
[www.google.com](www.google.com) has IPv6 address 2607:f8b0:4002:c08::68
[www.google.com](www.google.com) has IPv6 address 2607:f8b0:4002:c08::6a
[www.google.com](www.google.com) has IPv6 address 2607:f8b0:4002:c08::93
[www.google.com](www.google.com) has IPv6 address 2607:f8b0:4002:c08::67

---

### Post by SeijiSensei on 2020-09-05
Most home routers are configured to act as the nameserver for the networks they serve. When you start up a client machine, it makes a request asking other machines on the network if they provide information via the "dynamic host configuration protocol" or DHCP. Usually your router answers this request and gives your computer an IP address and tells the client computer to use the router for DNS services. The router needs to be configured with some valid DNS server addresses.

On recent Ubuntu machines, the program systemd-resolved takes the address(es) given by the router and creates a mini DNS server of its own. It listens on the address 127.0.0.53 (see the original resolv.conf) and forwards the DNS queries it receives to the addresses it got during the DHCP handshake.

If you can resolve names quickly using Google's server at 8.8.8.8, you can set it as the default for your system by editing (as root with sudo) the file /etc/systemd/resolved.conf. Replace the line that reads "#DNS=" with "DNS=8.8.8.8". Now the resolver will use that server for all name resolution requests.  If you don't want to use Google's server you can use Cloudflare's at 1.1.1.1 as you did in the last posting.  Or you could put the Cloudflare server in the DNS= line in /etc/systemd/resolved.conf, and specify Google's server as the FallbackDNS in that file.  Here are some other options for free DNS servers: [https://www.allconnect.com/blog/best-free-dns-servers](https://www.allconnect.com/blog/best-free-dns-servers)

---

### Post by Old Jimma on 2020-09-07
Thank you!!!!!!

---

