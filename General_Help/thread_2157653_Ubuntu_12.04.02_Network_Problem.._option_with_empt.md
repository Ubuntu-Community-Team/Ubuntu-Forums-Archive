---
title: "Ubuntu 12.04.02 Network Problem.. option with empty value... couldn't read interfaces"
date: 2013-06-26
forum: General Help
---

### Post by acecott on 2013-06-26
Hi, Im  new to Linux. In fact I dont know any of Linux OS, Linux Environmet, Command etc...

The problem is:

[B]/etc/network/interfaces:14: option with empty value
ifup: couldn't read interfaces file "etc/network/interfaces"

Current config: (I saw this in /etc/network/interfaces)

#This file describes the network interfaces available on your system[/B]**#and how to activate them. For more information, see interfaces(5).**
[B]
[COLOR=#000000]# The loopback network interface[/COLOR]
auto lo eth0 eth1
iface lo inet loopback

[COLOR=#000000]# The primary network interface
[/COLOR]iface eth0 inet static
              address 192.168.12.108
              netmask 255.255.255.0
              broadcast 192.168.12.255
              dns-nameservers
iface eth1 inet static
              address 192.168.12.109
              netmask 255.255.255.0
              broadcast 192.168.12.255
              network 192.168.12.0
iface eth2 inet dhcp
iface eth3 inet dhcp

[/B]
Other commands:[B]
ls -lah /etc/network/interfaces

        -rw-r--r-- 1 root root 545 Jun 26 12:32 /etc/network/interfaces

ls -l /etc/network | grep interfaces

       -rw-r--r-- 1 root root 545 Jun 26 12:32 interfaces
[/B][B]       -rw-r--r-- 1 root root 525 May 10 14:14 interfaces'
[/B][B]
ifconfig
      Link encap: Local Loopback
      inet addr:127.0.0.1 Mask:255.0.0.0
      inet6 addr: ::1/128 Scope:Host
      UP LOOPBACK RUNNING MTU:16436 METRIC:1
      RX packets:100 errors:0 dropped:0 overruns:0 frame:0
      TX packets:100 errors:0 dropped:0 overruns:0 carrier:0
      collisions:0 txqueuelen:0
      RX bytes:6528 (6.5 KB) TX bytes:6258 (6.5 KB)

      

              
all the commands I learned, from researching,..  cat, cat view, editor /etc/network/interfaces  etc..
when I run:

sudo /etc/init.d/networking restart

the same error message.

the server have a pci ethernet for the 10gbe cable and also built-in ethernet for cat 5/6.
[/B]anything you want to know? just let me know.

Here is the scenario. I have a colleague who thought me how to shutdown the Linux server that we have, using webmin.
I shutdown the server. Pulled the ethernet plug. I pulled the the 10gbe plug, for purpose of the maintenance of our TOC, so it will not be hit or accidentally hit by the people who are going to work inside the TOC..

My colleague is on leave, or should I say "awol".

I booted up the server. I'm trying to access the server through webmin, but i cant get through.
I tried to go to the server itself, I just log-in through command line.. where I typed the username and password. (which my colleague thaught me, for the purpose of the command htop, so I can view also whats going in server..

So, curious that I am and I also think there is a problem.. I tried to search for a solution through google. I learned a thing or two by searching alone.
But, still I still dont have a solution yet. Dont know what to do else, so I try to post here.
Please, please help me..

THANK YOU!

---

### Post by steeldriver on 2013-06-26
Well at a guess the problem is the dns-nameservers option in your eth1 stanza - it needs to be followed by at least one actual DNS server IP

```

# The primary network interface
iface eth0 inet static
address 192.168.12.108
netmask 255.255.255.0
broadcast 192.168.12.255
[COLOR=#ff0000]**dns-nameservers**[/COLOR]

```

You will need to contact your network admin to find out the appropriate nameserver(s) to use (it may just be the router IP, if your router is running a forwarding DNS service); failing that you could use OpenDNS or Google's public nameservers

```

# The primary network interface
iface eth0 inet static
address 192.168.12.108
netmask 255.255.255.0
broadcast 192.168.12.255
dns-nameservers 8.8.8.8 8.8.4.4

```

---

### Post by acecott on 2013-06-26
ok. I'll try that.. Thank you.
is there anyway i can know the dns-nameserver in our server. I mean like in /etc/network/interfaces?
because i saw the previous config that he did. maybe also that.
i cant open **resolv.conf**
forgive me i really dont know linux..

---

### Post by acecott on 2013-06-26
AHA!!! THANK YOU! THANK YOU! the server is now accesible.. i found the dns in our firewall server. thank you!

---

### Post by steeldriver on 2013-06-26
You're welcome - make sure you make a note of the changes you made in case your awol colleague (or their replacement) needs to follow up

EDIT: and welcome to the forum btw, I just noticed this is your first thread

---

### Post by acecott on 2013-06-26
yes this is my first thread. yes i did make notes. everything i did and saw. 
the dns is the problem. thank you very much.

---

