---
title: "apt-get stuck on 0%"
date: 2006-12-06
forum: General Help
---

### Post by doodman on 2006-12-06
hi i'm new in this forum and new to ubuntu too.
i've installed ubuntu a few weeks ago and encounterred a broblem with accessing the net with fire-fox.
so i switched back to windows and found the answer: to change the ipv6 configuration in about:config.

now i'm trying to install new packages:
g++, vim, zsh etc...
but yet another problem with apt-get; it gets stuck on 0%, and after a few minutes it gets a timeout with the message 'no route to host'.
does someone now how to solve this problem?
thanks.

---

### Post by bscbrit on 2006-12-06
It sounds like apt is having a problem finding your network connection, so the problem either lies in the apt configuration or your network.  For apt, have you recently changed your repositories?  Has apt / Synaptic been working correctly up to now?  Has the update icon been telling you of regular updates that might be available?  For the network, please give me details of your network (modem, whether DHCP or static IP etc), and let me know the results of running 'ifconfig' in a terminal.  Are you able to surf the web correctly?

---

### Post by doodman on 2006-12-06
Wow thanks for the quick answer...

I havn't changed any apt configuration what so ever, it's the same configuration as after the installation.

At first I had problems surfing the web with firefox, but when I disabled the IPv6 configuration on firefox's about:config it started to work.

I thought that the apt-get problem might be relative to the disabling/enabling IPv6, so i tried changing the /etc/modprobe.d/aliases line:
"alias net-pf-10 ipv6"
to this line:
"alias net-pf-10 off"
and restarting but it didn't work.
I even put it in the blacklist but that didn't work to.

I don't realy know much about my network details but i think that i don't have a static ip, i have a modem, this is the ifconfig output:


```
eth0      Link encap:Ethernet  HWaddr 00:11:D8:6F:C5:42
          inet addr:10.0.0.2  Bcast:10.255.255.255  Mask:255.0.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:868 errors:0 dropped:0 overruns:0 frame:0
          TX packets:846 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:947505 (925.2 KiB)  TX bytes:123164 (120.2 KiB)
          Interrupt:217 Base address:0xe400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)
```

Can you spot the problem.

---

### Post by gitargr8 on 2006-12-06
You look to have a 10. IP address, are you on a corporate network? 

I know that when I am on certain networks that require a proxy to connect to the Internet, apt doesn't work, since the DNS server won't resolve outside IPs. 

See if you can get on a network that connects directly to the Internet, and try apt again.

~Ryan

---

### Post by bscbrit on 2006-12-06
gitargr8 made a good point about your network address but, in theory at least, I don't think it _should_ make a difference, although it _might_ do.

Most home networks, if you are on a home network, use a 192.168. series of IP addresses.  Most home adsl and cable modems are set to default to an address in this series, such as 192.168.0.1 or 192.168.1.1.  It might be one possible cause of not being able to access the outside world.  You didn't answer my earlier question regarding whether you can now browse the www using firefox. If you are using one of these modems, then it might also be your DNS and thus could also be a cause of network problems.  The DNS is what converts [www.somename.com](www.somename.com) into the sequence of numbers that your computer actually needs e.g. 123.234.10.20, or whatever. Let us have a description of your hardware and we can try to help.

---

### Post by doodman on 2006-12-06
I use an eci router with the address of 10.0.0.138 where the username and password are in the router.

As for your question i **can surf the web using firefox** (it started to work only after i disabled the IPv6 in the about:config)

---

### Post by doodman on 2006-12-06
> **doodman said:**
> I use an eci router with the address of 10.0.0.138 where the username and password are in the router.

As for your question i **can surf the web using firefox** (it started to work only after i disabled the IPv6 in the about:config)

maybe a screen shot will help:


```
&#9484;&#9472;(doody@pariz)&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;(~)&#9472;&#9488;
&#9492;&#9472;(1:22:47)&#9472;&#9472; sudo apt-get install g++                                                                        &#9472;&#9472;(Wed,Dec06)&#9472;&#9496;
Password:
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  g++-4.0 libc6-dev libstdc++6-4.0-dev linux-kernel-headers
Suggested packages:
  gcc-4.0-doc lib64stdc++6 glibc-doc manpages-dev libstdc++6-4.0-doc stl-manual
The following NEW packages will be installed:
  g++ g++-4.0 libc6-dev libstdc++6-4.0-dev linux-kernel-headers
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 7604kB of archives.
After unpacking 32.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  linux-kernel-headers libc6-dev libstdc++6-4.0-dev g++-4.0 g++
Install these packages without verification [y/N]? y
Err http://archive.ubuntu.com dapper/main linux-kernel-headers 2.6.11.2-0ubuntu18
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://archive.ubuntu.com dapper/main libc6-dev 2.3.6-0ubuntu20
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
0% [Connecting to archive.ubuntu.com (1.0.0.0)]

```

---

### Post by bscbrit on 2006-12-07
You are trying to connect to an address of 1.0.0.0, which does not exist.  Check your settings under System -> Administration -> Synaptic -> Settings -> Network to ensure that you have 'Direct Connection to the Internet' selected.

---

### Post by doodman on 2006-12-07
Direct connection to the internet was selected already...

---

### Post by bscbrit on 2006-12-07
Can you install software using Synaptic rather than apt-get?  Does Synaptic behave when you press the 'Reload' button?

From the command line in a terminal let me know what the results of the following commands are:

ping 127.0.0.1
ping 10.0.0.2
ping 10.0.0.138
ping [www.ubuntuforums.org](www.ubuntuforums.org)

---

### Post by brimbleshoes on 2006-12-08
I have a wicked cheap ZyXel WAP-router deal-ee-oh, and another cheap ActionTec DSL modem.

Standard DNS is no worky.  try this:

Change the /etc/resolv.conf DNS address from your WAP(router) address to 4.2.2.1

and then in /etc/dhcp3/dhclient-script 

commented out the entire function

```
make_resolv_conf() {
...
blah blah
...
}

```

that should work.

Seems to be a problem of hardware makers catering to the broken non-standard Winders DNS resolution forwarding vs. service.  (or something... I just inferred that from what I read somewhere else).

---

### Post by bscbrit on 2006-12-08
Brimbleshoes, you might be right but I suspect not.  Doodman has installed several other computers with the same software and they have worked.  His problem is the one that he is trying to set up now is not working with the same versions of software, so I suspect that it is either hardware related or he has inadvertantly set the wrong value somewhere.  If the problem was caused by a Windows server then I would expect none of them to work.  But I've been proven wrong before and I'll happily accept any advice from wherever it comes, so thank you for your suggestion.

---

