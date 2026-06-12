---
title: "Unable to ping Ubuntu server (via hostname)"
date: 2008-05-31
forum: General Help
---

### Post by st11x on 2008-05-31
G'day,

I have 6.0.6 server running under VMWare Workstation 6.0.3. The server uses DHCP and I can ping the hostname of it from the host (XP). There are no connection issues.

I just installed 8.0.4 server under the same VMWare and I have no troubles with network connectivity except that I just cannot ping it (from the host) using the hostname. 

Any suggestions? I do not want to have to add it to the XP's host file. I already tried seeding the host-name in dhclient.conf, the solution being floated around the net, but it didn't work.

thanks
  Matt

---

### Post by fragos on 2008-05-31
Make sure you have an /etc/hostname file. It has a single line with the hostname in it -- in my case Geo. next check /etc/hosts and make sure the hostname is referenced. In my case there should be a line:

127.0.1.1  Geo

---

### Post by st11x on 2008-06-01
> **fragos said:**
> Make sure you have an /etc/hostname file. It has a single line with the hostname in it -- in my case Geo. next check /etc/hosts and make sure the hostname is referenced. In my case there should be a line:
127.0.1.1  Geo

It does. I have the hostname file with the entry "chang", and in /etc/hosts, I have 127.0.1.1 chang.localdomain chang

I can ping chang in the server, but I cannot ping chang from XP which is very strange. If I fire up the 6.0.6 image, it works. I couldn't figure out what the difference is, but I am guessing XP + VMWare cannot be the problem given that they are the constants in both experiments.

---

### Post by fragos on 2008-06-01
If this is a LAN, "chang.local" may work -- no need to reflect .local in /etc/hosts. Between 2 Ubuntu boxes on a LAN adding .local to the host name works.

---

