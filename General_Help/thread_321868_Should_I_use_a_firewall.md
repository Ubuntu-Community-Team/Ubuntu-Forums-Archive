---
title: "Should I use a firewall?"
date: 2006-12-19
forum: General Help
---

### Post by BarfBag on 2006-12-19
Simple question.  My PC isn't connected directly to the internet.  It goes through a router (which I'm pretty sure has a firewall) and shares the same connection with other PC's.  Should I install a firewall, or am I generally safe?

---

### Post by OffHand on 2006-12-19
> **BarfBag said:**
> Simple question.  My PC isn't connected directly to the internet.  It goes through a router (which I'm pretty sure has a firewall) and shares the same connection with other PC's.  Should I install a firewall, or am I generally safe?
Generally speaking you should be safe.

---

### Post by bodhi.zazen on 2006-12-19
> **BarfBag said:**
> Simple question.  My PC isn't connected directly to the internet.  It goes through a router (which I'm pretty sure has a firewall) and shares the same connection with other PC's.  Should I install a firewall, or am I generally safe?

Ubuntu has a firewall installed with a default install, IP Tables.

All firewall programs, firestarter, guard dog, etc are GUI front ends for IP Tables.

IMO you should run a firewall.

---

### Post by gh0st on 2006-12-19
You might wanna check that your router definately has a working firewall though, just to be safe. Personally I have a router with a firewall and a software firewall on my PC's as well, that might be overkill but I'm paranoid :-)

---

### Post by Qew on 2006-12-19
A default install of Ubuntu should run with no world listening services installed, so no ports will be open for the world to exploit. If your router has NAT/firewall, then it should cover you. Then again, if you're in a network with other machines, then the router won't be enough if one of your other machines gets compromised and there's some exploitable service running on your machine. I suppose it depends on your setup, but the typical install won't really need a firewall, especially if behind a router.

---

### Post by fragos on 2006-12-19
Some of these posts are a little confusing.  IMHO -- IP Tables ='s Firewall.  Unless you specificaly removed IP Tables you have a firewall by default when installing from the live CD.  Programs like Firestarter aren't firewalls they are GUI frontend to modify the IP Tables configuration.  Ergo you only need run them to change the firewall setup you already have.

---

### Post by ciscosurfer on 2006-12-19
@BarfBag,

This topic has been discussed many, many times (so you'll probably get many, many different types of responses).  Here's a good thread for you to take a look at: [http://ubuntuforums.org/showthread.php?t=131616](http://ubuntuforums.org/showthread.php?t=131616) (it will discuss using Firewalls, Anti-Virus apps, etc.)

---

### Post by Dubbayoo on 2006-12-19
> **fragos said:**
> Some of these posts are a little confusing.  IMHO -- IP Tables ='s Firewall.  Unless you specificaly removed IP Tables you have a firewall by default when installing from the live CD.  Programs like Firestarter aren't firewalls they are GUI frontend to modify the IP Tables configuration.  Ergo you only need run them to change the firewall setup you already have.
Well if you're telling to use the built-in firewall he DOES have to run them because by default the firewall is wide open.....accept all in, let all out, forward all

---

### Post by stanjam on 2006-12-19
> **BarfBag said:**
> Simple question.  My PC isn't connected directly to the internet.  It goes through a router (which I'm pretty sure has a firewall) and shares the same connection with other PC's.  Should I install a firewall, or am I generally safe?

YES!  You should have a firewall on each machine!  IPTABLES is good.  Your router should have a firewall and should have NAT (network address translation) at a minimum.

---

### Post by OffHand on 2006-12-20
> **Dubbayoo said:**
> Well if you're telling to use the built-in firewall he DOES have to run them because by default the firewall is wide open.....accept all in, let all out, forward all

+1 
Iptables doesn't do anything if you do not configure it. I hear this Iptables argument a lot. People should realize it is USELESS when it is not configured.

---

### Post by compwiz18 on 2006-12-20
And nothing can get in if there are no services listening, ie all ports are closed, right?

---

### Post by Circus-Killer on 2006-12-20
> **OffHand said:**
> +1 
Iptables doesn't do anything if you do not configure it. I hear this Iptables argument a lot. People should realize it is USELESS when it is not configured.

iptables is already configured in ubuntu by default. its set up to deny all incoming connection and allow all outgoing connections. to change this you can use firestarter to configure iptables to you liking.

---

### Post by OffHand on 2006-12-20
> **Circus-Killer said:**
> iptables is already configured in ubuntu by default. its set up to deny all incoming connection and allow all outgoing connections. to change this you can use firestarter to configure iptables to you liking.

No: [http://www.ubuntuforums.org/showpost.php?p=1860396&postcount=27](http://www.ubuntuforums.org/showpost.php?p=1860396&postcount=27)

I might totally misunderstand this. In that case please enlighten me.

---

### Post by chrisccoulson on 2006-12-20
Running iptables -L on my system (having made absoultely no changes to the firewall) definately show that my machine is wide open.

---

### Post by az on 2006-12-20
> **bodhi.zazen said:**
> Ubuntu has a firewall installed with a default install, IP Tables..

What people think is a firewall in windows is an applications layer firewall - a program that sits on top of other programs dissalowing some of them to talk to the rest of the world.  Those kinds of firewall are often just a false sense of security, since there is a lot that can actually bypass them.

The linux kernel routes packets.  It does so using a table.  This is called a packet filter.  Just like your router, it routes, drops or ignores packets according to what you tell it to do.  By default, it does nothing.

> **bodhi.zazen said:**
> 
All firewall programs, firestarter, guard dog, etc are GUI front ends for IP Tables..

Unless you are running a server, there is no reason to use a firewall.  There is nothing a firewall can do for a desktop system.


> **bodhi.zazen said:**
> 
IMO you should run a firewall.

IMHO, you are wasting your time.  Just stay up-to-date with security updates.

---

### Post by bodhi.zazen on 2006-12-20
azz:

Thank you for your time and the infromation. Certainly an interesting topic.

Oh, but I do run a small server :p

---

### Post by compwiz18 on 2006-12-20
> **bodhi.zazen said:**
> azz:

Thank you for your time and the infromation. Certainly an interesting topic.

Oh, but I do run a small server :p
For my server, I have the router forward only the ports I want accessible, thus using a hardware firewall.  Everything else is simply dropped.

---

### Post by fragos on 2006-12-20
> **OffHand said:**
> +1 
Iptables doesn't do anything if you do not configure it. I hear this Iptables argument a lot. People should realize it is USELESS when it is not configured.

Very true.  My confusion on the subject is based on the fact that another distro I used came with a configured firewall.  I suppose I incorrectly assumed Ubuntu was the same way.  Kinb of give one a gun without bullets.  Firewalls are conceptually easy to understand.  What ports to block is another issue all together.  I see functional description of commands but little help on a strategy for using them.  A try these first would sure help.  I'll take a look at Firestarter to see it can help me with recommendations.  I've used firewalls on Windows that by default blocked everything but informed you when a packet was blocked in real time so you could make a decision on a configuration change.  Obviously anything that worked that well was 3rd party.

---

### Post by compwiz18 on 2006-12-20
> **fragos said:**
> Very true.  My confusion on the subject is based on the fact that another distro I used came with a configured firewall.  I suppose I incorrectly assumed Ubuntu was the same way.  Kinb of give one a gun without bullets.  Firewalls are conceptually easy to understand.  What ports to block is another issue all together.  I see functional description of commands but little help on a strategy for using them.  A try these first would sure help.  I'll take a look at Firestarter to see it can help me with recommendations.  I've used firewalls on Windows that by default blocked everything but informed you when a packet was blocked in real time so you could make a decision on a configuration change.  Obviously anything that worked that well was 3rd party.
But doesn't Ubuntu ship with all ports closed, so this isn't a problem?

---

### Post by fragos on 2006-12-20
> **compwiz18 said:**
> But doesn't Ubuntu ship with all ports closed, so this isn't a problem?

Hardly the expert on Linux, I ran "sudo iptables -L"  and the output I got looked like everything was open.  I installed Firestarter and ran the wizard which added a bunch of configuration items to iptables but it still appears that all is open since no ports are blocked.  I ran Networking Tools to the IP assigned to me via DHCP and do Port Scan which gets only ports 25 and 80 open although, without regularity, the ports open and close rapidly.  Perhaps the port scan only indicates in use and not "unblocked."  I'm not sure what I'm looking at.

---

### Post by compwiz18 on 2006-12-20
Everything is open, but nothing is listening.  At least that is the way is was explained to me.  So in effect nothing But I wrote myself a firewall script that drops everything coming in unless I requested it :D That was I don't accidentally open a port :P

---

### Post by fragos on 2006-12-20
> **compwiz18 said:**
> Everything is open, but nothing is listening.  At least that is the way is was explained to me.  So in effect nothing But I wrote myself a firewall script that drops everything coming in unless I requested it :D That was I don't accidentally open a port :P

That's makes perfectly good sense given which ports were always labeled "open".  I appreciate answer.  Would it be unreasonable to ask for a copy of your script?  I'm sure I can learn a lot from it -- actually we all could.

---

### Post by compwiz18 on 2006-12-21
um...save this as a file and run  **sudo iptables-restore < /name/of/file**

I actually used Webmin to create this, it makes it so much easier :D  It lets you add everything via your web browser and save the script to load at boot.

see screenshot attached

and make sure to set interface lo to accept all, otherwise GNOME won't start...if you screw up, **sudo iptables -F** do reset iptables via the terminal.

```

# Generated by iptables-save v1.3.5 on Fri Dec 15 23:29:50 2006
*nat
:PREROUTING ACCEPT [0:0]
:POSTROUTING ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]
COMMIT
# Completed on Fri Dec 15 23:29:50 2006
# Generated by iptables-save v1.3.5 on Fri Dec 15 23:29:50 2006
*mangle
:PREROUTING ACCEPT [1963:2362042]
:INPUT ACCEPT [1961:2359954]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [1412:77106]
:POSTROUTING ACCEPT [1412:77106]
COMMIT
# Completed on Fri Dec 15 23:29:50 2006
# Generated by iptables-save v1.3.5 on Fri Dec 15 23:29:50 2006
*filter
:FORWARD DROP [0:0]
:INPUT DROP [0:0]
:OUTPUT ACCEPT [0:0]
# accept all on loopback
-A INPUT -i lo -j ACCEPT
# allow established connections
-A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
COMMIT
# Completed on Fri Dec 15 23:29:50 2006

```

---

### Post by fragos on 2006-12-21
Compwiz18 -- Thank you very much.

---

### Post by compwiz18 on 2006-12-21
No problem, hope it helps you somehow.

---

