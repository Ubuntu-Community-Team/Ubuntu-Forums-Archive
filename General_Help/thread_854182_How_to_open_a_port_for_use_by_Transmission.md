---
title: "How to open a port for use by Transmission"
date: 2008-07-09
forum: General Help
---

### Post by pedrogent on 2008-07-09
Hello all:

I'm still relatively new to all this Ubuntu caper. When using torrents in the past (on Windows) I've used µTorrent and this has involved opening up a port so that the program functions correctly.

I've been using Transmission for quite a while now for my torrents but I don't think I'm getting the d/l rates I should be.

When I go to to *Edit > Preferences* I find that my assigned port is closed. This was always the case when I used µTorrent too mind you. But when I go into my router and open up the port in the way I used to in my Windows/µTorrent days I don't seem to be opening up the port at all (as reported by Transmission).

Can somebody help me out here? Are there any good guides for configuring Transmission out there?

Thanks a lot.

---

### Post by fedex1993 on 2008-07-11
yes ubuntu usually has all ports auto closed on the computer it self. Install firestarter and use it to open up the torrent port and make sure it is open on your router too.

---

### Post by kmh.putta on 2008-08-12
you must use static IP address to keep the port open

---

### Post by Subban on 2008-08-12
I didn't have to use Firestarter to open a port for Transmission here (your mileage may vary) but I did have to open a port on the router and point to my PC (using a static IP ofc).

Anyway that is what worked for me. If you already have ports forwarded on the router you should be ok to just change the port in Transmission to use one of those afaik.

---

### Post by Nepherte on 2008-08-12
> **fedex1993 said:**
> yes ubuntu usually has all ports auto closed on the computer it self. Install firestarter and use it to open up the torrent port and make sure it is open on your router too.
I don't think that's correct. The default policy is accept, but on a default ubuntu install, there's no service listening on any of those ports so it's completely safe. If you install for example openssh-server, it will listen on port 22 and will accept incoming requests: meaning the port is not closed.

---

### Post by Vivaldi Gloria on 2008-08-12
> **fedex1993 said:**
> yes ubuntu usually has all ports auto closed on the computer it self. Install firestarter and use it to open up the torrent port and make sure it is open on your router too.

No.

The default ubuntu comes with all ports open. No need to make any changes in ubuntu to use p2p programs. It's all about router port and router firewall settings.

Besides, firestarter is dead and ubuntu comes with ufw.

Open a terminal (Apps. > Access. > Term.) and give the command

```
sudo ufw status
```

If it comes back as

```
Firewall not loaded
```

then all ports are already open. See

```
man ufw
```

and especially the examples section for more info on it.

But I repeat again, in the default ubuntu install, firewall is not working and all ports are open. It's all about router port and router firewall settings.

---

### Post by Distortedgamer on 2008-08-13
This is going to sound super n00b but I can't figure this out. I am usingh the default torrent client, but I can't find the config to find the port number that its using. I can't find the program itself under Applications and when I am downloading a torrent (also I don't understand why it only lets me do one at a time, if you have a better suggestion for that, I am all ears as well) I can't find any preferences or anything. I looked in the /etc folder and couldn't find anything that was helpful. 

Does anyone know how I can find the config for the default torrent client, or has a better one that would work better (that doesn't need WINE)?

Any help would be greatly appreciated, these 25 kbps d/l's are killing me!!

---

### Post by mb_webguy on 2008-08-13
I use Deluge, which is very similar to uTorrent.  While there's a version in the repositories, the [Deluge website]("http://deluge-torrent.org/") offers a deb package for Ubuntu to install the most recent stable version.

You'll still need to set port forwarding on your router.  By default, Deluge uses random ports, but you can change that in the Deluge preferences.  The default ports for Deluge if you turn off the random ports function are 6881 to 6891.

If you tell us what kind of router you have, we can help you set the port forwarding.

---

### Post by Vivaldi Gloria on 2008-08-14
> **Distortedgamer said:**
> This is going to sound super n00b but I can't figure this out. I am usingh the default torrent client, but I can't find the config to find the port number that its using. I can't find the program itself under Applications 

In Hardy, Transmission is in Apps > Internet menu.

When you start transmission you can learn the port number it uses from its settings menu.

> (also I don't understand why it only lets me do one at a time, if you have a better suggestion for that, I am all ears as well) 

??

Transmission can definetely download more than one at a time. 

Are you using Hardy?

---

### Post by Vivaldi Gloria on 2008-08-14
This is my howto port forward in routers.

**1)** Enter the router settings. Every decent router has a setting or table where you can fix the adresses of particular computer (ethernet card). Find that setting which fixes your computer's adress. If there is no such setting then this guide is no good for you.  It can be something of the sorts "Always use the ip 192.168.XX.XX for the computer with the mac adres XX:XX:...". I choose a number like 192.168.1.35. Restart router.

**2)** In a terminal give the command ifconfig. Here is the top lines of its output from my box:

```
vivaldi@narval:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:07:c4:d2:17:ba  
          inet addr:192.168.1.35 ...
...
...
```

Here eth0 is the my main ethernet card. The ip 192.168.1.35 is the ip fixed by the router for that card. So at this step we verify that you indeed get the ip the router reserved for your computer.

**3)** Now since your computer's ip is fixed to 192.168.1.35 you can forward the ports you want to 192.168.1.35. Use your port forward settings (or NAT) of your router to do this. For example when you start transmission you can learn the port number it uses from its settings menu. Mine uses TCP 51413. For transmission I the use the following 

start & end ports: TCP 51413, ip:192.168.1.35

in my router.

**4)** Some routers also have a seperate firewall settings in which you may also need to enable ports.

---

### Post by hyper_ch on 2008-08-14
> **fedex1993 said:**
> yes ubuntu usually has all ports auto closed on the computer it self. Install firestarter and use it to open up the torrent port
That's quite wrong.

By default all ports are closed because no application listens to any of those ports. They are not force-closed by the system.

So there's no need to install firestarter. However if you do, then firestarter will really close all ports so that they must be opened manually.

---

### Post by zipperback on 2008-08-14
> **fedex1993 said:**
> yes ubuntu usually has all ports auto closed on the computer it self. Install firestarter and use it to open up the torrent port and make sure it is open on your router too.

Incorrect. There is no need to do this. By default they are not closed.

A default installation of Ubuntu does not have any rules setup for a firewall.

You can see what rules iptables has configured by using the following in a terminal window.

Applications -> Accessories -> Terminal

> 
**sudo iptables --list**


If you are using a provider such as Comcast or similar broadband service provider, you might want to be aware that they intentionally be interfering with torrent based data transfers.

[http://www.geek.com/comcast-blocks-bit-torrent-traffic/]("http://www.geek.com/comcast-blocks-bit-torrent-traffic/")

If you are able to download with transmission even very slowly, then your firewall isn't the problem. You're traffic is probably being messed with by your isp.

- zipperback
:popcorn:

---

### Post by hyper_ch on 2008-08-14
and if you want to test whether your ISP messes around with your internet connection try the Switzerland tool as recommended by the EFF: [http://www.eff.org/testyourisp/switzerland](http://www.eff.org/testyourisp/switzerland)

---

### Post by zipperback on 2008-08-14
If you want to know what ports are responding on your system, you can always use something like the shields up website.

[http://www.grc.com/intro.htm](http://www.grc.com/intro.htm)

Click on "shields up" and then click proceed, and then click the "all service ports" option. It will scan you, and display the responses.

- zipperback
:popcorn:

---

### Post by yahia999 on 2010-06-15
yeah but how would you set your MODEM for that? i have a netgear, so it asks for 'Service/Port Name' as the name of the app that uses this port...
Let me guess, should it be like,,,, 'TRANSMISSION'??
firestarter has some ports (6881-6889) for bittorrent, but THAT didnt do it for transmission..
thx in advance anyway :D

---

### Post by Linuxforall on 2010-06-15
If your router supports UPnP, its enabled by default in Transmission and therfore it would get inbound on its own, otherwise you need to specify a port number in network and also set your router for it.

---

### Post by yahia999 on 2010-06-15
yeah i've done all of that and even set the traffic thingy to TCP/UDP, and simply did everything just like windows and utorrent, but it tells me port is closed, any ideas??? 
thx for passing by :D
EDIT: i found a site that worked for utorrent b4, and it actually got a tutorial for transmission now! it's [https://trac.transmissionbt.com/wiki/PortForwardingGuide](https://trac.transmissionbt.com/wiki/PortForwardingGuide) better see it :D

---

### Post by 3rdalbum on 2010-06-15
> **Linuxforall said:**
> If your router supports UPnP, its enabled by default in Transmission and therfore it would get inbound on its own, otherwise you need to specify a port number in network and also set your router for it.

+1

This.

There's no need to mess around with port forwarding and static IPs these days, UPnP does all this for you. Just turn it on in your router and make sure it's turned on in Transmission.

---

### Post by yahia999 on 2010-06-15
> **3rdalbum said:**
> +1

This.

There's no need to mess around with port forwarding and static IPs these days, UPnP does all this for you. Just turn it on in your router and make sure it's turned on in Transmission.
the problem is that i actually have it enabled 3rdalbum, and i have reset everything to how it was, and the funny thing it finally worked lol. looks i have tweaked alot of stuffs the other way round but it works great now, thx for attention  :D

---

### Post by yahia999 on 2010-06-15
even better, i'll be switching to Lucid Lynx this weekend (it's thursday considering i'm middle-eastern :D ) as soon i back up my info first :D

---

