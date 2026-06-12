---
title: "aMule works for root but not for users"
date: 2007-12-11
forum: General Help
---

### Post by mmichielin on 2007-12-11
I'm having this strange behavior from aMule:
1) I installed aMule with my administrator user (let's say root) and, apart from the well known crash problem, it works "quite" perfectly
2) I just added a new user (not administrator) and for this user aMule downloads the server list but REFUSES TO CONNECT to whatsoever server (the message is "connection lost"). aMule still works with my administrator user

Any suggestion or idea?
Thanks in advance

---

### Post by ruibernardo on 2007-12-11
Hi mmichielin,

you must have executed amule with sudo (just guessing). The ~/.aMule drectory must now belong to root user. 

Try changing the owner of that directory and its content with:
```
sudo chown -R yourusername.yourusername ~/.aMule
```

---

### Post by mmichielin on 2007-12-12
> **epimeteo said:**
> Hi mmichielin,

you must have executed amule with sudo (just guessing). The ~/.aMule drectory must now belong to root user. 

Try changing the owner of that directory and its content with:
```
sudo chown -R yourusername.yourusername ~/.aMule
```

Thanks but unfortunately this is not the case: .aMule directory was made by the user (and not by root) and I'm running aMule as a user (and not as root)
I add some more information:
- even if I add "administration" capability to my user, aMule still doesn't work
- my 4662, 4665 and 4672 ports are wide open on my DLINK DI 624 router (that's why amule works with root)
- this is my connection log:
```
2007-12-12 19:55:25: Credit file loaded, 0 clients are known

2007-12-12 19:55:25:  - This is aMule 2.1.3 using wxGTK2 v2.8.4 (Unicoded) based on eMule.
2007-12-12 19:55:25:    Running on Linux 2.6.22-14-generic x86_64
2007-12-12 19:55:25:  - Visit http://www.amule.org to check if a new version is available.

2007-12-12 19:55:25: Loading ipfilter.dat files.
2007-12-12 19:55:25: Loaded 0 IP-ranges from 'ipfilter.dat'. 0 malformed lines were discarded.
2007-12-12 19:55:25: Loaded 0 IP-ranges from 'ipfilter_static.dat'. 0 malformed lines were discarded.
2007-12-12 19:55:25: Loading server.met file: /home/silvia/.aMule/server.met
2007-12-12 19:55:25: 10 servers in server.met found
2007-12-12 19:55:25: No file parts found
2007-12-12 19:55:25: External connections disabled in config file
2007-12-12 19:55:25: MuleUDPSocket: Created Server UDP-Socket at port 4665
2007-12-12 19:55:25: MuleUDPSocket: Created Client UDP-Socket at port 4672
2007-12-12 19:55:25: Found 0 known shared files
2007-12-12 19:55:25: Connecting
2007-12-12 19:55:25: Servers: Trying to connect
2007-12-12 19:55:25: Connecting to muellbomber (38.107.164.21 - 38.107.164.21:0)
2007-12-12 19:55:25: Read 0 Kad contacts
2007-12-12 19:55:25: AICH Thread: Syncronization thread started.
2007-12-12 19:55:25: AICH Thread: Masterhashes of known files have been loaded.
2007-12-12 19:55:25: AICH Thread: No new files found.
2007-12-12 19:55:25: AICH Thread: Terminated.
2007-12-12 19:55:25: Lost connection to muellbomber (38.107.164.21:4661)
2007-12-12 19:55:25: Connection lost
2007-12-12 19:55:25: Servers: Trying to connect
2007-12-12 19:55:25: Connecting to muelbomber (38.107.161.51 - 38.107.161.51:0)
2007-12-12 19:55:28: Lost connection to muelbomber (38.107.161.51:4661)
2007-12-12 19:55:28: Connection lost
2007-12-12 19:55:49: Connection attempt to muellbomber (38.107.164.21:4661) timed out.
2007-12-12 19:55:49: Servers: Trying to connect
2007-12-12 19:55:49: Connecting to eDonkeyServer No2 (38.107.164.14 - 38.107.164.14:0)
2007-12-12 19:55:50: Lost connection to eDonkeyServer No2 (38.107.164.14:4661)
2007-12-12 19:55:50: Connection lost
2007-12-12 19:55:50: Connection attempt to muelbomber (38.107.161.51:4661) timed out.
2007-12-12 19:55:50: Servers: Trying to connect
2007-12-12 19:55:50: Connecting to MaBell (38.107.164.5 - 38.107.164.5:0)
2007-12-12 19:55:51: Lost connection to MaBell (38.107.164.5:4661)
2007-12-12 19:55:51: Connection lost
2007-12-12 19:56:15: Connection attempt to eDonkeyServer No2 (38.107.164.14:4661) timed out.
2007-12-12 19:56:15: Servers: Trying to connect
2007-12-12 19:56:15: Connecting to Dangerous Liasons (38.107.164.8 - 38.107.164.8:0)
2007-12-12 19:56:15: Lost connection to Dangerous Liasons (38.107.164.8:4661)
2007-12-12 19:56:15: Connection lost
...
```
and so on...

I've read in some other posts that windows emule works with wine but I'd like to solve the issue and keep using "ubuntu" amule

And other suggestion?
Thanks

---

### Post by ruibernardo on 2007-12-12
> **mmichielin said:**
> - even if I add "administration" capability to my user, aMule still doesn't workDon't, and if you do run aMule with "sudo" or as root, put back the files ownership to the right username with the command I posted before if the files inside - /.aMule changed.
> **mmichielin said:**
>  - my 4662, 4665 and 4672 ports are wide open on my DLINK DI 624 routerAh, you need to forward the router ports to the right computer, not just opening them. The router must know where (which computer IP) it has to forward the connections. This webpage might help you to set up your router for this: [http://portforward.com/english/routers/port_forwarding/Dlink/DI-624+/BitTornado.htm](http://portforward.com/english/routers/port_forwarding/Dlink/DI-624+/BitTornado.htm)
> **mmichielin said:**
> (that's why amule works with root)Now I'm confused again. Are you running aMule as root or with sudo or not? Anyway I would bet on a router port forward problem.

I hope this helps you somehow.

---

### Post by mmichielin on 2007-12-13
> **epimeteo said:**
> Don't, and if you do run aMule with "sudo" or as root, put back the files ownership to the right username with the command I posted before if the files inside - /.aMule changed.
Ah, you need to forward the router ports to the right computer, not just opening them. The router must know where (which computer IP) it has to forward the connections. This webpage might help you to set up your router for this: [http://portforward.com/english/routers/port_forwarding/Dlink/DI-624+/BitTornado.htm](http://portforward.com/english/routers/port_forwarding/Dlink/DI-624+/BitTornado.htm)
Now I'm confused again. Are you running aMule as root or with sudo or not? Anyway I would bet on a router port forward problem.

I hope this helps you somehow.

My previous post wasn't clear enough. I try to explain once again.
I have 2 users:
- michele (me, administrator)
- silvia (my wife, standard user)

If I enter ubuntu with michele, aMule WORKS
If I enter ubuntu with silvia aMule DOES NOT WORK

Is it clear now?
Thanks

---

### Post by ruibernardo on 2007-12-13
Yes, loud and clear :)

Are both amule running at the same time on different desktops using different ports and being forwarded by the router? For example, amule1 should use 4662 and amule2 use 5662, etc.

---

### Post by mmichielin on 2007-12-14
No, I don't use two concurrent running version of aMule.
I simply:
- log in as "michele", aMule WORKS
- log off
- log in as "silvia", aMule DOES NOT WORK

My goal is to be able to have aMule working with user "silvia"

Ciao

---

