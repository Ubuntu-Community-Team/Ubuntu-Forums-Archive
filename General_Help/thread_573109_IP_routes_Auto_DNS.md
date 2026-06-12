---
title: "IP routes? Auto DNS?"
date: 2007-10-11
forum: General Help
---

### Post by phillips321 on 2007-10-11
Hi guys,

I have a website running on my lan

to get to it from outside my network i can just type in the domain name [www.phillips321.co.uk](www.phillips321.co.uk)

when ever i wish to browse to it from inside the LAN i have to go to **[http://192.168.1.100/phillips321.co.uk](http://192.168.1.100/phillips321.co.uk)** is there a way that i can set up on my pc that each time a request is made for phillips321.co.uk it directs to the internal ip rather than doing a dns lookup and getting my external ip and trying to connect to that?

cheers guys

---

### Post by thirddeep on 2007-10-11
You could put phillips321.co.uk in /etc/hosts and point it to that IP.

Thd.

---

### Post by phillips321 on 2007-10-11
just inserted this but it doesn't seem to work, do i need to reboot or reload the hosts file?

p.s. thanks for pointing me in the right direction

```
127.0.0.1       localhost
127.0.1.1       LinuxDesktop
192.168.1.100   phillips321.co.uk
192.168.1.100   forumpix.co.uk

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

---

### Post by thirddeep on 2007-10-11
127.0.0.1       localhost.localdomain localhost
192.168.1.100   phillips321.co.uk philips321
192.168.1.100   forumpix.co.uk forumpix

That is the correct format.  Now you can just type philips321 in your browser.

O, almost forgot, what is in /etc/nsswitch.conf ?  Make sure the 'hosts' line starts with 'files'.

Thd.

---

### Post by phillips321 on 2007-10-11
half way there!

now when i ping either phillips321 or phillips321.co.uk it works, my ping goes direct to the lan server and back without trying to breakout to the net

problem is now is that when i try to connect to phillips321.co.uk in the web browser it still looks up the ip and trys to point me to the external address

```
phillips321@LinuxDesktop:~$ cat /etc/hosts
127.0.0.1       localhost
127.0.1.1       LinuxDesktop
192.168.1.100   phillips321.co.uk       phillips321
192.168.1.100   forumpix.co.uk  forumpix

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
phillips321@LinuxDesktop:~$ ping phillips321
PING phillips321.co.uk (192.168.1.100) 56(84) bytes of data.
64 bytes from phillips321.co.uk (192.168.1.100): icmp_seq=1 ttl=64 time=0.139 ms
64 bytes from phillips321.co.uk (192.168.1.100): icmp_seq=2 ttl=64 time=0.118 ms
64 bytes from phillips321.co.uk (192.168.1.100): icmp_seq=3 ttl=64 time=0.121 ms

--- phillips321.co.uk ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 0.118/0.126/0.139/0.009 ms
phillips321@LinuxDesktop:~$ ping phillips321.co.uk
PING phillips321.co.uk (192.168.1.100) 56(84) bytes of data.
64 bytes from phillips321.co.uk (192.168.1.100): icmp_seq=1 ttl=64 time=0.113 ms
64 bytes from phillips321.co.uk (192.168.1.100): icmp_seq=2 ttl=64 time=0.116 ms
64 bytes from phillips321.co.uk (192.168.1.100): icmp_seq=3 ttl=64 time=0.141 ms

--- phillips321.co.uk ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 0.113/0.123/0.141/0.015 ms
phillips321@LinuxDesktop:~$ 

```

---

### Post by phillips321 on 2007-10-11
ok, i just tested my web browser by typing phillips321.co.uk into the address filed, it doesn't work

but if i try phillips321.co.uk/index.html it works fine seems odd to me??

---

### Post by thirddeep on 2007-10-11
You also need to fix your localhost entry in your hosts file.  This will not help for this particular problem, but it will be at least technically correct.

As for why your server is not serving pages:

a) Try to empty your cache
b) Use telnet first for testing
c) Check what the log files says.

Thd.

---

