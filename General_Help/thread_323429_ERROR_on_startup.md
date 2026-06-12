---
title: "ERROR on startup"
date: 2006-12-22
forum: General Help
---

### Post by holdinout on 2006-12-22
OK, I finally got Xubuntu installed and after the installation completed, I rebooted like asked. I logged in fine but as soon as I did:

Could not look up internet address for .
This will prevent Xfce from operating correctly.
It may be possible to correct the problem by adding
 to the file /etc/hosts on your system.

"Continue Anyway"            "Try Again"


It let me proceed, so I'm guessing it would be an easy fix?

---

### Post by xopher on 2006-12-22
> It may be possible to correct the problem by adding
to the file /etc/hosts on your system.

By adding what?

Maybe you haven't set the ip for localhost, which should be 127.0.0.1.

---

### Post by darrenm on 2006-12-22
Hmm it does sound like your hostname isn't in /etc/hosts

Try running:

```
hostname --fqdn
ifconfig -a
cat /etc/hostname
cat /etc/hosts
```
And can you post the output here please? thanks.

---

### Post by holdinout on 2006-12-22
administrator@:~$ hostname --fqdn
hostname: Unknown server error
administrator@:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:10:DC:3C:E5:C6  
          inet addr:24.60.88.49  Bcast:255.255.255.255  Mask:255.255.248.0
          inet6 addr: fe80::210:dcff:fe3c:e5c6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:80526 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4916 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9021236 (8.6 MiB)  TX bytes:696422 (680.0 KiB)
          Interrupt:193 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

administrator@:~$ cat /etc/hostname
-desktop
administrator@:~$ cat /etc/hosts
127.0.0.1       localhost
127.0.1.1       -desktop

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by holdinout on 2006-12-22
"administrator@:~$ hostname --fqdn"

Did I do this one wrong?

---

### Post by holdinout on 2006-12-22
> **xopher said:**
> By adding what?

Maybe you haven't set the ip for localhost, which should be 127.0.0.1.


Exactly, it seems to be a space? Anyways, localhosts set to that IP.

Sorry I didn't put this all in one post... Always forget about the Edit button.

---

### Post by darrenm on 2006-12-22
Aha edit the /etc/hosts file and change the -desktop to something like xubuntu. Do the same for /etc/hostname

Then reboot :)

---

### Post by holdinout on 2006-12-22
Still getting the error... Thinking about a fresh install... Is having Xfce a nuisance?

---

### Post by Co.Sinecure on 2007-01-28
I'm having the same problem, my hosts and hostname seems ok:

will@Leela:~$ cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 Leela.HOME

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

will@Leela:~$ cat /etc/hostname 
Leela

:confused: 

I've got a wireless PCMCIA card that i'm using, I can get to the network and internet fine. Doesn't seem to adversely affect the system..

---

