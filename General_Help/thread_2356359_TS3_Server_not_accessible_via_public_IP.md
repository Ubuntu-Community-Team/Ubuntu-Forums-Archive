---
title: "TS3 Server not accessible via public IP"
date: 2017-03-22
forum: General Help
---

### Post by studner on 2017-03-22
Hey guys,

I am trying to figure this out for a few days now and tried a lot of solutions, but with no luck.

I have a Lubuntu (Ubuntu 16.04.2 LTS) pc working as a home NAS and I want to use it as TS3 server. Everything is working perfectly **inside **my own network, but I cannot access it via public IP.

Network is set-up like this: modem -> router (**Asus RT-N18U**) -> switch -> Lubuntu pc

I have a Teamspeak3 server 3.0.11.4 32bit and I've done following:

PC which runs the TS3 server has **static IP**.
I've **forwarded ports** 9987 (UDP), 10011 (TCP) and 30033 (TCP) to that static IP and tested if they are open (they are)
Router **firewall **is switched off[B].
[/B]Tried to connect from a different network to see if it is not caused by my router not beeing able to connect to its own public IP.
I edited **iptables **according to what I read online.** "**iptables -L" gives me:
--------------------------------------------------------------------------------------
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     udp  --  anywhere             anywhere             udp spt:9987
ACCEPT     udp  --  anywhere             anywhere             udp dpt:9987
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:10011
ACCEPT     tcp  --  anywhere             anywhere             tcp spt:10011
ACCEPT     tcp  --  anywhere             anywhere             tcp spt:30033
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:30033


Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         


Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
----------------------------------------------------------------------------------


And I still get error (failed to connect to server) when trying to connect to TS3 server via public IP.
But I **can** reach TS3 server query via public IP and telnet on 10011 port.

Any idea where the problem might be? At this point, I have no idea if the problem is caused by the Lubuntu pc running the TS server or by my router...

Thanks a lot for any input. I am still quite a noob in this :D

---

### Post by TheFu on 2017-03-22
Probably the router.

Draw a picture.
Label all the IP addresses.
Label all the ports necessary.
Forward all the ports from the router WAN to the server LAN. 
For a short time, it is ok to completely disable the firewall on the server.

[https://support.teamspeakusa.com/index.php?/Knowledgebase/Article/View/44/16/which-ports-does-the-teamspeak-3-server-use](https://support.teamspeakusa.com/index.php?/Knowledgebase/Article/View/44/16/which-ports-does-the-teamspeak-3-server-use) shows 4inbound different port ranges are needed, not just 3.  There are 3 outbound ports that need to be allowed too, but most home networks wouldn't block them.

I saw a few youtube videos that show what to do too.

I've never setup or used TS3, BTW.

---

### Post by efflandt on 2017-03-24
If you go to [http://www.canyouseeme.org/](http://www.canyouseeme.org/) does it show those ports open? Does the TS3 server itself have any configuration to allow/deny IP address ranges (like apache, etc.).

---

### Post by studner on 2017-03-27
> **TheFu said:**
> Probably the router.

Draw a picture.
Label all the IP addresses.
Label all the ports necessary.
Forward all the ports from the router WAN to the server LAN. 
For a short time, it is ok to completely disable the firewall on the server.

[https://support.teamspeakusa.com/index.php?/Knowledgebase/Article/View/44/16/which-ports-does-the-teamspeak-3-server-use](https://support.teamspeakusa.com/index.php?/Knowledgebase/Article/View/44/16/which-ports-does-the-teamspeak-3-server-use) shows 4inbound different port ranges are needed, not just 3.  There are 3 outbound ports that need to be allowed too, but most home networks wouldn't block them.

I saw a few youtube videos that show what to do too.

I've never setup or used TS3, BTW.

I forwarded the 4th port. firewall was disabled and it still doesen't work :/ Is it possible, that a ethernet switch might be the problem? I don't see reason why it would cause this...

> **efflandt said:**
> If you go to [http://www.canyouseeme.org/](http://www.canyouseeme.org/) does it show those ports open? Does the TS3 server itself have any configuration to allow/deny IP address ranges (like apache, etc.).

Those two TCP ports are open (tested it before), 9987 used for VOIP is UDP and I tested it succesfully on another site for USP testing. 
I even tried to change the port on which TS3 listens and still nothing...the router is blocking it and I have no idea why...

EDIT: I even tried allowing DMZ for that server and it still won't work

---

### Post by TheFu on 2017-03-27
Check the log files.  All of them. Enable logging for the server firewall. See what is being blocked. Check the other, application, log files.  Watch them as you try to connect. If nothing is seen, then either the server isn't listening correctly or a firewall is blocking.  Just need to find which firewall, right?

If the switch is layer2, it probably doesn't do any blocking.  Layer2 is only ethernet, so things on the same physical LAN. If it is layer3, then it could be a simple router with blocking.

Whenever I find that my attempts aren't working, I reset everything (mostly my mind) and start over going step-by-step, extremely carefully, with a checklist for everything that needs to be done.  Also check that the RANGE of REQUIRED PORTS is opened, not just 1 port inside each range.

If you step back and read what you've written here, you will see what we see - claims that you did everything correctly, but ZERO proof of that. *Go and get some proof that you post here.*  Proof about the router, port forwards, all IPs involved, and server configs.  Proof that the firewalls ARE NOT blocking anything necessary to get through.  That will be in the firewall logs for the server AND on the router.  Often, doing that will help me see what I've missed, just trying to prove to someone else I didn't miss anything.  I always did miss something or didn't understand something to the level necessary. My bad.

DMZ is not a good long term solution, as you know. Quick testing with it isn't too bad, provided you don't leave it that way on a non-hardened server. Assuming everything is setup correctly and still doesn't work, (I'm not 100% certain you did get things setup correctly - need PROOF) anyway - check your server configs for each part of the solution.

---

