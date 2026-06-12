---
title: "Internet Sharing Autostart"
date: 2005-10-23
forum: General Help
---

### Post by faraco on 2005-10-23
My Ubuntu is sharing an Internet connection to a Windows machine.

But after every Ubuntu system boot, I have to manually execute the following commands:

[INDENT]sudo /etc/init.d/dhcp3-server start
sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
sudo sh -c 'echo 1 > /proc/sys/net/ipv4/ip_forward'[/INDENT]

How can I have these commands executed automatically on Ubuntu startup?


Thank you.

---

### Post by ymmotrojam on 2005-10-23
I'm a noob, but can't you put them in the Startup tab under... System>Sessions?

;)

---

### Post by faraco on 2005-10-23
I think I can. But...

...is that the best way to do it?

---

### Post by Bitmastro on 2005-10-23
The best thing should be making an init script (a script that is executed even before gnome starts), for example dhcp3-server should already have an init script in /etc/init.d/dhcp3-server... it is executed if there is a link in /etc/rc2.d/... 
I suggest using guarddog (or maybe firestarter?) that will do this for you.
Hope this help, bye :-D

---

### Post by kingbanditjing on 2005-10-24
update-rc.d will add init.d scripts to various run levels.  use this to add dhcpd to the default run level.

you should put all your iptable rules in init.d/firewall or similar.  read a script that's in there right now for how to detect start, stop, restart etc.  use iptables -F, -L, you get the idea.

faraco, i'm unused to ubuntu, what are you trying to acomplish with: ```
sudo sh -c 'echo 1 > /proc/sys/net/ipv4/ip_forward'
```

---

### Post by faraco on 2005-10-24
Take a look at

[https://wiki.ubuntu.com/RootSudo]("https://wiki.ubuntu.com/RootSudo")

specially the section named _**Possible issues with the "sudo" model**_

Best Regards,

--
Pedro Faraco

---

### Post by kingbanditjing on 2005-10-25
sorry, i meant the sh -c 'echo 1 > /proc/sys/net/ipv4/ip_forward' part.  i don't recall having to mess with anything in /proc/sys/net/ on slackware or gentoo.  thanks!

---

### Post by MasterPi on 2005-10-28
Firestarter may be a good option, I believe it starts either with the system or with the network.  That said, I havent gotten it working on Debian yet (Ubuntu D/l is in process).  Although, that could just be because i have a really screwed up network setup with 2 subnets for 3 computers and two routers. ugh.

---

### Post by Plagued on 2005-11-06
> 
echo 1 > /proc/sys/net/ipv4/ip_forward



This can be accomplished by adding these lines to /etc/sysctl.conf:

```

#Turn on IP forwarding
net.ipv4.ip_forward=1

```

That will set the value of /proc/sys/net/ipv4/ip_forward to 1 during the boot process.

I do have to agree tho it is very disappointing that k/ubuntu does not include an iptables init.d script by default. Seems like an oversight.

---

