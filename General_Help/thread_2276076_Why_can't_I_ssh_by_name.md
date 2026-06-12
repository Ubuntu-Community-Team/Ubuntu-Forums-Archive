---
title: "Why can't I ssh by name?"
date: 2015-04-30
forum: General Help
---

### Post by sim085 on 2015-04-30
Hello, I am not sure if this is an ubuntu issue or an issue with my router. I have a fresh install of ubuntu. I gave this the hostname of "mypc". When I ssh from another PC, if I do "ssh sim085@192.168.1.111" it works fine. However if I do "ssh sim085@mypc" it tells me "Could not resolve hostname mypc Name or service not known". When on mypc I check /etc/hostname and this is set to "mypc". When I check the router I can see that mypc is listed. So what might be the issue?

---

### Post by sim085 on 2015-04-30
Just to say that this happens only when I try to ssh from another linux machine. When I ssh from a Windows machine (through putty) I do manage to connect to the machines by the machine name. So the issue seems to be with the linux machine I am using to ssh to the other machine.

---

### Post by steeldriver on 2015-04-30
For that to work with *only* the computer name, you would need to add an entry to the /etc/hosts file on the computer you're sshing from

```

192.168.1.111         mypc

```

However, you should be able to use

```

ssh sim085@mypc**.local**

```

which uses the avahi discovery service to resolve names on the local network

---

### Post by TheFu on 2015-04-30
@Steeldriver - great post.  However, I see mixed results with .local lookups here. Tried 3 different pings for 3 different machines on the local network   "hostname.local"
* 1 is correct - worked as hoped.
* 1 is on an incorrect subnet (vnet* device address returned)
* 1 does not answer. failed.

This could be an issue with my network, since we have DNS and /etc/hosts setup for almost all the machines already.

Another workaround is to create a ~/.ssh/config file.  Then an alias for the hostname can be added, but the IP address can be put in for address resolution.
```
host regulus
 Ciphers arcfour
 user rooter
 hostname 172.22.22.44
 port 64022

```
Multiple stanzas like that can be used.  The manpage is pretty good **ssh_config** is the name. All tools which are built on ssh will support these settings.  ssh, sftp, scp, rsync, rdiff-backup, etc.... userid, ports, cyphers are added to those commands automatically. No more need to remember if a cmd required -p or -P to specify a port or what userid is setup on the other host!  ;)

Anyway - just another option to use with ssh.

---

### Post by steeldriver on 2015-04-30
Good point @TheFu! I completely forgot about the ~/.ssh.config, that would be the obvious choice in this case

*Note to self: don't post before coffee*

---

### Post by TheFu on 2015-04-30
About 4 months ago, I showed a Unix guy with 30 yrs experience the **~/.ssh/config** file - he'd never heard of it. This is a professional RHEL admin.  Just one more example of how flexible Linux is and how **nobody** can know it all.  BTW - the file name/path here is correct.

Don't know if this is the best choice, but whenever I need a non-default ssh-based connection to any other system, putting settings into my config file is the first thing I do. 

I see it as more than just a way to control options - it is also a handy-to-have document as a reminder.  For example, I manage some networks in Nepal, but don't have to do much there very often.  Clearly, I've been trying to see how the networks AND my friends there are doing.  Haven't been able to login and haven't seen any other communication from my friends yet.  They have a generator, but I suspect fuel ran out and their fibre link probably hasn't worked all week.

---

### Post by sim085 on 2015-04-30
Thanks to both for the replies. I tried "sim085@mypc.local" but this did not work out for me. Got the same error message. I would like to avoid having to write the IP Address in a file to get a connection with the name. The reason is that at the moment the router provides a different IP to the machine each time this is turned off / on. I would need to maintain these files if I write the IP. That is why I originally wanted to access the machine through the name not IP. I could use static IP's but I am trying to avoid that at the moment.

---

### Post by TheFu on 2015-04-30
What you want is a combination of DHCP reservations and DNS.
[http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management](http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management)

If you don't have static IPs, Unix services will move around. That is the way IPv4 works. Sorry.

---

### Post by sim085 on 2015-04-30
I could use static IPs; However I wonder why it works from putty but not from linux terminal? The routers knows that "mypc" ip address is xxx.xxx.xxx.xxx so shouldn't the linux machine I am using to connect to mypc be able to resolve the IP Address of mypc with the router?

---

### Post by TheFu on 2015-04-30
Exactly how does the router have this information?  Is it running DNS?  There are standard protocols for name resolution under every OS.  Linux supports those standards.  Non-standard extensions many or may not be supported and I don't have any idea why Windows works or doesn't work. Sorry.

I know that /etc/nsswitch.conf specifies the order and protocols used by Linux to resolve hostnames to IP addresses.  For a small network, /etc/hosts and DNS are normally used for Linux/Unix hostname resolution by other hosts on the network. In the old days, we might use NIS (also called yp) too, but that wasn't secure for all that is did - groups, userids, passwords, hosts, netgroups, .... and Windows didn't support NIS.  NIS+ has replaced NIS, but Sun (now Oracle) didn't release or license the server code to other vendors. There are NIS+ clients for every Unixen, but only Solaris has the NIS+ server code. Sorry - off topic.

So, if you want this to work ... 
* setup DHCP reservations and DNS on your router
OR
* manage /etc/hosts files across all the boxes.  Ansible is the tool I use for this.

I've made lots of assumptions here - like the network is relatively small (20 or less devices). If the network is larger, there are better ways, IMHO.

---

### Post by sim085 on 2015-04-30
> **TheFu said:**
> Exactly how does the router have this information?  Is it running DNS?

When I did the Ubuntu installation I was asked for a hostname. Here I entered "mypc". When I loging on my router I can see the IP Address given to "mypc" and "mypc" written next to this. If I delete this entry a different IP Address is given to "mypc" and again "mypc" is written next to this. If I change the hostname (let say to "mypc2") and I delete the entry (from router), mypc2 gets a new IP Address with (now) "mypc2" written next to this. So I guess the name is being provided to the router by mypc once a connection is establish (ip provided).

Mine is a small network (4 pc tops) and I am doing this mostly to learn. I could use static ips (either configure this from "mypc" or else the router itself). I had done this in the past. However this time round I would like to be able to access the machines with their name rather then IP Address. You said "setup DHCP reservations and DNS on your router"; To my knowledge DHCP means I get provided an IP Address by the router different each time. This works as I do get an IP Address. DNS means being able to associate a name with that IP Address. This also seems to be working as when I login to the router I can see the name next to the IP Address. 

Are there any logs I can look into to see what is going on when I enter "ssh sim085@mypc" to see if for example router is not returning any information or it is a question of my machine not asking the router for this information?

---

### Post by TheFu on 2015-04-30
"DHCP Reservation" - this uses MAC addresses to set the same IP for the same network adapter always. Effectively, static IPs.

The DHCP lease time can be changed too - 7 days is common for a small network.  If the device is on when the lease expires, then it will get the same IP again.

The PC provides the hostname it has to the router as part of the DHCP protocol. This data may or may not be used - suppose it depends on the router software. With DHCP reservations, the MAC address is **always** used.

ssh has verbosity settings
**ssh -vvvv user@server**
and the server side daemon has debug levels in the config file. These will be written to syslog/auth.log like always.  Handy to look at if there are issues.

---

### Post by Doug S on 2015-04-30
To me, it sounds like your router has DNS, but your Ubuntu box isn't using it. What does /etc/resolv.conf contain? Mine contain the address of my local DNS (which is also the address of my DHCP server) on the "nameserver" line.

---

### Post by sim085 on 2015-04-30
That file contains; 

nameserver 8.8.8.8,
nameserver 192.168.1.254

192.168.1.254 is the IP Address I use to access my router.

> **Doug S said:**
> To me, it sounds like your router has DNS, but your Ubuntu box isn't using it. What does /etc/resolv.conf contain? Mine contain the address of my local DNS (which is also the address of my DHCP server) on the "nameserver" line.

---

### Post by TheFu on 2015-04-30
The comma is a problem. Delete it.
You probably want to swap the order so the router is first. Should make all things a little faster.

Does the file say that you shouldn't edit it at the top? If so - read what it says and follow those instructions to make changes.

---

### Post by Doug S on 2015-04-30
Myself, I would get rid of the 8.8.8.8 nameserver, and let your router DNS take care of upstream requests when needed.
However, and as TheFu mentioned, the first step is to determine how your resolv.conf file is made.
Did you mention which version of Ubuntu you are using? It matters because things have changed in the last few years.

I suspect your router DNS entry is coming from your DHCP lease request. You can check via the */etc/dhcp/dhclient.conf* file, see if *domain-name-servers* is included in the request, it is by default. Here is mine (which is not the default)```
request subnet-mask, broadcast-address, time-offset, routers,
        [COLOR=#ff0000]domain-name-servers[/COLOR];
```

---

### Post by sim085 on 2015-04-30
I do not remember editing it. In fact I have removed the comma from the file but each time I am restarting I am getting that comma back :(
It says generated by resolveconf(8). There is a directory /resolveconf. Had a look but cannot find from where 8.8.8.8 is coming from.

EDIT: 
I did a fresh install which /etc/resolv.conf does not have that 8.8.8.8 entry and I can ssh with host name from that so it seems that is the culprit. This was an old installation. Cannot remember from where that 8.8.8.8 came from.


> **TheFu said:**
> The comma is a problem. Delete it.
You probably want to swap the order so the router is first. Should make all things a little faster.

Does the file say that you shouldn't edit it at the top? If so - read what it says and follow those instructions to make changes.

---

### Post by Doug S on 2015-04-30
What version of Ubuntu are you using?

Look in */etc/network/interfaces*. It could also be forced via a prepend statement in */etc/dhcp/dhclient.conf*.

---

### Post by sim085 on 2015-04-30
Originally I had Ubunti 12.04 but had upgraded to 14.04. 

In /etc/network/interfaces I have the following entry:

"dns-nameservers 8.8.8.8, 192.168.1.254"


> **Doug S said:**
> What version of Ubuntu are you using?

Look in */etc/network/interfaces*. It could also be forced via a prepend statement in */etc/dhcp/dhclient.conf*.

---

### Post by TheFu on 2015-04-30
That's where the comma is coming from - delete it - generally I would have 2 separate lines, but I've seen it both ways. Don't know if one way is better than the other.

---

### Post by Doug S on 2015-04-30
My input is to delete the entire line. Let your Ubuntu computer be told what to use as a DNS via the DHCP lease request (that is as long as it is asking for it). That way there is less for you to think about in the future if you change your router address or if you take your Ubuntu computer to another sub-net or whatever.

---

### Post by efflandt on 2015-04-30
By default Ubuntu runs avahi-daemon which acts like Apple zeroconfig to resolve hostname.local for other computers running that daemon (somewhat differently than Windows networking). If you are running some other Linux (like Raspbian on a Raspberry Pi) you might need to install **avahi-daemon** for that to work (and **avahi-utils** to use avahi-browse). I seem to remember Apple Bonjour in Windows being a little different in that I think you leave off the .local, but have not used that much.

This is an example of just my local computer and Chromecast shows up on it too (ham0 is Hamachi).```
efflandt@XPS-8100-1404:~$ avahi-browse -art
+   ham0 IPv6 XPS-8100-1404 [76:de:ea:d0:d5:ca]             Workstation          local
+   ham0 IPv4 XPS-8100-1404 [76:de:ea:d0:d5:ca]             Workstation          local
+  wlan0 IPv6 XPS-8100-1404 [78:e4:00:26:b8:ac]             Workstation          local
+  wlan0 IPv4 XPS-8100-1404 [78:e4:00:26:b8:ac]             Workstation          local
=   ham0 IPv6 XPS-8100-1404 [76:de:ea:d0:d5:ca]             Workstation          local
   hostname = [XPS-8100-1404.local]
   address = [2620:9b::1967:6b3e]
   port = [9]
   txt = []
=  wlan0 IPv6 XPS-8100-1404 [78:e4:00:26:b8:ac]             Workstation          local
   hostname = [XPS-8100-1404.local]
   address = [fe80::7ae4:ff:fe26:b8ac]
   port = [9]
   txt = []
=   ham0 IPv4 XPS-8100-1404 [76:de:ea:d0:d5:ca]             Workstation          local
   hostname = [XPS-8100-1404.local]
   address = [25.103.107.62]
   port = [9]
   txt = []
=  wlan0 IPv4 XPS-8100-1404 [78:e4:00:26:b8:ac]             Workstation          local
   hostname = [XPS-8100-1404.local]
   address = [172.16.0.50]
   port = [9]
   txt = []
+  wlan0 IPv4 DE-CCast1                                     _googlecast._tcp     local
=  wlan0 IPv4 DE-CCast1                                     _googlecast._tcp     local
   hostname = [DE-CCast1.local]
   address = [172.16.0.126]
   port = [8009]
   txt = ["rs=" "st=0" "ca=5" "fn=DE-CCast1" "ic=/setup/icon.png" "md=Chromecast" "ve=04" "id=9d610a432b04ae259ea1264c43708418"]
```

---

