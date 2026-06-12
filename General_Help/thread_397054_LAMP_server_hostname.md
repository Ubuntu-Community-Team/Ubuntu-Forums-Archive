---
title: "LAMP server hostname"
date: 2007-03-30
forum: General Help
---

### Post by psykro on 2007-03-30
I have recently done my first ubuntu lamp server installation using 5.10. 

The server is setup for DHCP on my local DSL's router network.

If I want to browse the web server I can use the ip address, but how would I go about setting things up to be able to browse by means of the server hostname from my XP machine. (i.e. [http://servername](http://servername) instead of [http://10.0.0.x](http://10.0.0.x))

I have added the ip and hostname in my C:\WINDOWS\system32\drivers\etc\hosts file on my XP box, but is there something I can set on my server to enable this without needing to add it to my XP hosts file ?

---

### Post by bernied on 2007-03-30
In case you don't get a better answer:
I believe that to achieve this you need a DNS server on your local network. I think that the most commonly used software for this is [bind](http://packages.ubuntulinux.org/breezy/source/bind).

 You will probably currently be using a DNS server specified by your ISP. If you've only got a few machines on your network, it is probably easier to manage the hosts files on the machines, rather than manage a DNS server.

If you didn't know, the corresponding place for linux hosts files is (curiously): /etc/hosts
(I was very surprised when I found out that Windows had an etc directory - which was first I wonder?)

---

### Post by ScatterBrain on 2007-03-30
> **bernied said:**
> In case you don't get a better answer:
I believe that to achieve this you need a DNS server on your local network. I think that the most commonly used software for this is [bind]("http://packages.ubuntulinux.org/breezy/source/bind").
 
You will probably currently be using a DNS server specified by your ISP. If you've only got a few machines on your network, it is probably easier to manage the hosts files on the machines, rather than manage a DNS server.
 
If you didn't know, the corresponding place for linux hosts files is (curiously): /etc/hosts
(I was very surprised when I found out that Windows had an etc directory - which was first I wonder?)
 
 
I qgree. The way to do this is with a DNS server on a large scale.
 
If you only need to do this for one or two machines, the hosts file is much easier to maintain.
 
In either event, you need to stop having the LAMP system configure its IP settings via DHCP. For DNS and the hosts file to work, they depend on the recordied IP address information being accurate. If the DHCP-assigned addresses changes (and it can), you'll need to update the information.
 
Look [HERE]("http://www.ubuntugeek.com/change-ubuntu-system-from-dhcp-to-a-static-ip-address.html") for help going from DHCP to Static IP for the LAMP system.
 
I hope I helped.

---

### Post by psykro on 2007-03-30
ok thanks guys. its only for one machine (my testing server) so i'll stick with the hosts file. thanks for the assistance

---

