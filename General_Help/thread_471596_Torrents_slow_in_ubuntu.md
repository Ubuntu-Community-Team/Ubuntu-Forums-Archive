---
title: "Torrents slow in ubuntu"
date: 2007-06-12
forum: General Help
---

### Post by gamemage on 2007-06-12
When I try to download torrents in ubuntu using utorrent with wine or bittorrent with ubuntu. My max download speed is about 10 kb/s. But when I do the same in windows, my max download speed is from 100 kb/s to 400 kb/s.

How do I configure it so my speed is the fastest possible in ubuntu?

---

### Post by primski on 2007-06-12
try a different client, linux native. Bittorrent is lame and supports only basic functionality, i suggest 'qbittorrent' or 'deluge'. Even azureus perhaps, its based on java so it does work on ubuntu, tho pretty resource hungry :s

---

### Post by gamemage on 2007-06-12
I installed azureus but when I click to start it, it loads and then closes itself. 

Edit: Fixed Azureues. BUT the downloads are still very slow.

Edit2: I am using a linksys router and have firestarter installed but dont know how to do anything with ports on either.

---

### Post by Hallvor on 2007-06-12
> **gamemage said:**
> When I try to download torrents in ubuntu using utorrent with wine or bittorrent with ubuntu. My max download speed is about 10 kb/s. But when I do the same in windows, my max download speed is from 100 kb/s to 400 kb/s.

How do I configure it so my speed is the fastest possible in ubuntu?

You are probably just firewalled. By default, Ubuntu ships with no open ports. You need to open the right ports in iptables using a gui frontend called Firestarter. You install firestarter in Add/Remove, or open a terminal and write:

> sudo apt-get install firestarter 

(Secondly, changing the default ports of the BT application and opening them in your router is a good idea.) 

If you have done all this, and it doesn`t help, your ISP may be throttling you. Try a client with encryption, such as Azureus (if you are using a client with encryption in Windows).

Edit: Too slow.

---

### Post by gamemage on 2007-06-12
Thanks a lot. The speed is still not as high as I would like it to be but its good enough.

Edit: It turns out that my internet connection in linux is slower than my connection in windows. Weird right?

---

### Post by zodmaner on 2007-06-12
I had a similar problem, but lowering my router firewall setting from 'high' to 'low' help makes it a lot faster (I found out that my router firewall is blocking all the UDP connection used by BitTorrent, despite that fact that I've opened the port for them, weird huh?)

I also have similar problem with Firestarter, specifically, using it causes my BitTorrent speed to slow down to a crawl and it reports all kind of 'alert' when downloading a torrent.

I don't have any idea why this is happen but it seems that Torrent + firewall + Linux doesn't seems to mixes to well together.

---

### Post by primski on 2007-06-12
> **Hallvor said:**
> ...By default, Ubuntu ships with no open ports...

...as in no daemon is listening, therefore no ports open. Torrents should just work, regardless of your ubuntu firewall. I haven't installed any firewall applications and get max speeds.

This does not count for your external router tho, you need to forward port there accordingly.

---

### Post by robrmd9 on 2007-06-12
> **primski said:**
> ...as in no daemon is listening, therefore no ports open. Torrents should just work, regardless of your ubuntu firewall. I haven't installed any firewall applications and get max speeds.

This does not count for your external router tho, you need to forward port there accordingly.

Yea he's right, no need for firestarter etc...just forward the right ports in your router and everything should work fine.

---

### Post by Hallvor on 2007-06-12
Not opening the ports with Firestarter will make it impossible to connect to firewalled clients, thus making files with few sources much slower. With popular files and a lot of seeders, perhaps the difference is not that big. But with orher P2P applications, like aMule, not opening the ports with Firestarter will give you a low id, which is a real PITA and will make all downloads slow.

---

### Post by hadn on 2007-11-04
There is a couple of hints for the low download rate problem in Azureus/Ubuntu:

1. Make sure you are using Java JRE or Java JDK instead of GCJ/GIJ. You can install Java JRE with Automatix. Also, check if you are using JRE with the following shell command:

 sudo update-alternatives --config java

2. Disable the ipv6 protocol as described in [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4:](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4:)

 a) Open a terminal and type:
      gksudo gedit /etc/modprobe.d/blacklist
 b) Add this line:
      blacklist ipv6 
 c) Save the file and restart your computer

3. Set Azureus' parameters for working with your correct internet connection:

 a) Stop Azureus
 b) Remove Azureus' configuration directory - in a terminal, type: 
     cd ~
     \rm -rf .azureus/
 c) Run Azureus
 d) In the startup window, choose your internet connection type and speed

With these changes, I was able to improve Azureus' download rate by 2X to 3X. Nevertheless, uTorrent + Wine is giving me the highest (practically full) download rate. uTorrent website is [http://www.utorrent.com/](http://www.utorrent.com/)

Good luck
Hugo

---

### Post by brickbat on 2007-11-04
I found that bittorrent was actually 10% faster under ubuntu than xp.

---

