---
title: "How to stop avahi-daemon?"
date: 2019-08-26
forum: General Help
---

### Post by luca-dgh on 2019-08-26
For many reasons I want to stop avahi-daemon, but it looks like impossible.
I tried like this
```
sudo systemctl stop avahi-daemon.socket 
sudo systemctl stop avahi-daemon.service
sudo systemctl disable --no-reload avahi-daemon.socket 
sudo systemctl disable --no-reload avahi-daemon.service 

```

But after rebooting avahi-daemon is still working, worst than a virus it recreate itself from void.

How can I stop it?

---

### Post by TheFu on 2019-08-26
```
sudo apt purge avahi-daemon
 
```
worked here.  It is one of the first things I do on every new machine, right after purging nano.

---

### Post by luca-dgh on 2019-08-26
Hi TheFu, I was thinking to do the same, but I have read somewhere that there are some libavahi-xxxxx that are linked from many software and is not safe to purge avahi-daemon.
Now I see that you do it, are you using 18.04 or later?

Edit: Ok, I purged it, now I'll try the machine for a while.

---

### Post by TheFu on 2019-08-26
I strictly manage my network and actually prefer to manually configure static IPs, gateways, DNS and the resolv.conf.
If you want different systems to "automatically find" each other, then you need avahi.  I do not.  I hate that.

---

### Post by Morbius1 on 2019-08-27
When you "disable" a service it doesn't prevent something else from re-enabling / re-starting it again  - this is systemd here remember.

In order to truly prevent a service from running you need to "mask" it:
```
systemctl mask avahi-daemon
```
Now nothing else can restart / enable it.

---

### Post by cruzer001 on 2019-08-27
> **Morbius1 said:**
> When you "disable" a service it doesn't prevent something else from re-enabling / re-starting it again  - this is systemd here remember.

In order to truly prevent a service from running you need to "mask" it:
```
systemctl mask avahi-daemon
```
Now nothing else can restart / enable it.
mask!!

Thank you for that, I been using disable which will not always work and blaming systemd when it didn't ](*,)

---

### Post by HermanAB on 2019-08-27
Thanks for this information.

I really don't know who thought that running this useless service by default is a good idea.  Nothing at all ever uses Avahi service, so I consider it a potential security hole.

---

### Post by TheFu on 2019-08-27
> **HermanAB said:**
> Thanks for this information.

I really don't know who thought that running this useless service by default is a good idea.  Nothing at all ever uses Avahi service, so I consider it a potential security hole.

The systemd team has some smart idea, but they tend to use the NIH method (not invented here) way, way, too much.  They could have retained the previous expected behaviors that other init systems used, for example.  I suppose someone has written a script to hide systemd's funky interfaces.  I miss the days were we managed symbolic links. That was so much easier.

Avahi is mostly useful for home networks with media devices announcing themselves.  On a corporate environment or for internet servers, I can't think of any good reason for avahi.  That doesn't mean there aren't good reasons, just not obvious.

---

### Post by luca-dgh on 2019-08-27
The only good reason is a laptop portable pc that enter different environments continuously, in that case avahi gets the owner rid form annoying configurations.
I can't figure out other valuable uses.

---

### Post by HermanAB on 2019-08-28
Hmm, I have been using computers since the early 1970s and have never encountered *anything* that uses Avahi.  It is is simply useless.

Well, OK, not entirely useless:
It provides a kind of Built-In Test feature.  If your computer has a 169.x.y.z address, it means that your network router is faulty.

---

### Post by Holger_Gehrke on 2019-08-28
> **HermanAB said:**
> Hmm, I have been using computers since the early 1970s and have never encountered *anything* that uses Avahi.  It is is simply useless.


There's a server-less LAN IM in Pidgin that uses Avahi / Bonjour / ZeroConf to find other participants.

Holger

---

### Post by Morbius1 on 2019-08-28
The reason why disabling  ( rather than masking ) avahi-daemon.service doesn't prevent it from being re-enabled is because of CUPS.

On a desktop system CUPS provides a service called [highlight]cups-browsed[/highlight] that scans the network for printers, scanners, etc... using avahi. Once discovered it automatically creates local print queues for these printers. If you disable avahi-daemon.service cups-browsed.service simply re-enables it because it is dependent on it.

Another fun use of avahi is Samba. Someone over at Debian ( or maybe it was Ubuntu ) finally got around to reading the user manual on how to package samba and realized there was a switch that could be set that enables samba  to broadcast its presence to the rest of the network via avahi ( and not just the deprecated NetBIOS method ):
> **multicast dns register (G)**


If compiled with proper support for it, Samba will         announce itself with multicast DNS services like for example         provided by the Avahi daemon.



This all happened around the Ubuntu 17.04/17.10 time frame. With that enabled on the server all Linux and MacOS clients will be able to "browse" or "discover" the samba server seamlessly without user intervention and without the use of the old deprecated ( from a Win10 perspective ) Microsoft NetBIOS mechanism ... you know ... Workgroups, netbios names, etc..... and without all the rules, complications, and smb dialect restrictions that go with it.

---

### Post by luca-dgh on 2019-08-28
I marked the thread as  "solved" because uninstalling avahi-daemon I fixed my issue and the computer is not blaming the departure of the daemon.

Anyway I stay on my position, is a very useful tool for portables machines, but in a stationary environment is quite useless. If I have a Samba server I decide who can access it and how, I bet that no system manager wishes to open automatically a server to everyone without control. The same with printers: which is my interest in printing a document on a printer installed in an office 10 floors above or below me? Normally I will use the nearest printer for a standard work or a specified printer for a special work. IMO

---

### Post by Morbius1 on 2019-08-29
> If I have a Samba server I decide who can access it and how, I bet that  no system manager wish to open automatically a server to everyone  without control.
Avahi doesn't allow free and open access to your samba server. It allows it to be discovered ( in the case of Linux and MacOS clients ) or addressed with a hostname.local ( in the case of Linux, MacOS, or Win10 clients ).

In any event if you had a Samba Server in the type of network you described in your last post where you had so many assets they they span different floors you should be using Ubuntu Server not Ubuntu Desktop. Ubuntu Server does not install avahi-daemon or cups-browsed by default leaving it up to the SysAdmin to decide how he wants to set things up..

---

### Post by luca-dgh on 2019-08-29
Actually avahi-daemon works on client side, not server side. Avahi-daemon scan the network looking for services that my workstation can access to, the server broadcast a service, avahi-daemon discover it, so avahi-daemon has to be installed on a desktop pc, not a server system. If I were a sysadmin I would remove that daemon from every desktop pc I admin.

Yes I know that avahi-daemon doesn't grant access to a service, but on a network you can have public services opened to everyone and private or reserved services opened only to the target users of the service and I guess that a network admin (and/or a sysadmin) makes everything to hide the private services, because malicious hackers are everywhere.
I think that avahi-daemon, in this way, produces a lack of security

---

### Post by Morbius1 on 2019-08-29
Actually avahi-deamon works on the server side in the case where you want Samba to announce itself to the rest of the network. Samba was capable of doing that for a while but it took Ubuntu to enable that function just as the man page said: " [COLOR=#0000cd]**If compiled with proper support for it**, Samba will         announce itself with multicast DNS services[/COLOR] ..."

To be sure in order for a Linux or MacOS client to "discover" that server via mDNS avahi or bonjour has to be already installed on that client. But the client can't "discover" it if the server doesn't announce it.

---

### Post by Morbius1 on 2019-08-29
This is really none of my business but what problem are you having with avahi that you need to disable it on the clients?

Is this just a religious thing in that you believe it is just somehow insecure? Or are you getting errors that point to avahi running. Maybe using .local as a domain on your network and avahi is just making a mess of things under that condition?

---

### Post by luca-dgh on 2019-08-29
When you install a server do you compile every single package? or, probably, you will install compiled packages from a repos.

I don't like avahi-daemon because I'm working in a language school and in each classroom we have a pc (ubuntu 18.04), this machines are for educational purpose and available for the students and teachers. In my case we have seen printing job sent to inappropriate printers (as I said before, two floors below the classroom) and I realized that every single machine could access some folders on the server reserved to specified purpose (shared with Samba). Yes, the folders was protected by a password, but you never know who is working on the client side.

Now I removed all the avahi-daemon packages from the classroom machines: now every machine can print only on the assigned printer and the samba server is accessed only from the machines / users I defined.

I'm more relaxed now.

---

### Post by HermanAB on 2019-08-30
OK, so there are about three obscure use cases for Avahi and therefore it must be inflicted upon all users?  No thanks.

---

