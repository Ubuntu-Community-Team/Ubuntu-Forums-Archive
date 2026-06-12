---
title: "Ubuntu (Unity?) always connects to Amazon?"
date: 2017-08-05
forum: General Help
---

### Post by yuki2005w on 2017-08-05
I just installed 2 computers with Ubuntu 17.04. When I connected the ethernet cable for the first time, both computers made a brief connection to Amazon cloud servers. I opted out of diagnostics in the privacy settings BEFORE connecting to the internet. This only happened once per computer (restarting didn't make them connect again). Is this normal for vanilla Ubuntu? I only used flavors until now and this never happened in Kubuntu or Ubuntu Mate.

---

### Post by TheFu on 2017-08-06
All sorts of services run on Amazon, not just that company trying to sell us stuff.  Many F/LOSS projects have their own data collection servers running all sorts of places, including on Amazon EC2.  That isn't something controllable by Canonical in the global privacy settings if any specific project wants to be notified about usage.

Or it could be resetting the system time using NTP.  Or it could be a systemd thing.

So, if you can narrow down the exact protocol, port, and target IP/URL, then someone might be able to look at the service and see what is does.

---

### Post by yuki2005w on 2017-08-06
Thank you for your reply. How can I find the protocol and service making the connection? [netstat -natp] tells me these but net-tools isn't installed by default. I can only use [ss -natp] when connecting internet for the first time.

---

### Post by TheFu on 2017-08-06
Sorry, I don't understand the issue.  

Install all the tools you need, power off the machine. Unplug the cord.  Power on the machine. Setup your watching (wireshark, fuser, lsof, whatever) and bring the network up last.

Plus any non-bad router will have the data in the logs, so you could just watch there.

Is there some difficulty that I'm missing?

---

### Post by vocx on 2017-08-06
> **TheFu said:**
> Sorry, I don't understand the issue.  

Install all the tools you need, power off the machine. Unplug the cord.  Power on the machine. Setup your watching (wireshark, fuser, lsof, whatever) and bring the network up last.

Plus any non-bad router will have the data in the logs, so you could just watch there.

Is there some difficulty that I'm missing?
See his previous thread. Apparently he wants to have absolute certainty that he is connecting to the correct server, before even attempting to download anything to his system.

> **yuki2005w said:**
> It it is not a problem to install it, but it gives me peace of mind to know that I am downloading from the correct mirror if I can see the ip address. Luckily I can use [ss -natp] before I have netstat installed.

---

### Post by TheFu on 2017-08-06
That quote isn't in this thread that I can see.

There are many different repo servers around the world. They all have signed packages. Those signatures are validated during installation via GPG, so if the signature doesn't match, there will be an error/warning AND positive override will be necessary to screw it up.  Besides that, I wouldn't worry.

But we all have different levels of comfort.  I haven't used Unity (stock Ubuntu distro) in a very long time.

---

### Post by yuki2005w on 2017-08-06
Just installed a few more computers with 17.04. "gnome-software" was making the connection (port 443). The ip was always slightly different, but always started with [52.216...]. I've never used a distro with gnome-software before so makes sense I've never seen this (&#65307;´&#8704;&#65344;)

---

### Post by TheFu on 2017-08-07
? [http://popcon.debian.org/](http://popcon.debian.org/) ?  Without the exact URL and IP and port, how can someone else look at the service?

---

