---
title: "samba not working after iredmail install"
date: 2022-09-26
forum: General Help
---

### Post by 21Jerry on 2022-09-26
OK, I'm pulling my hair out.  I installed iredmail and it works on my 20.04 ubuntu server.  I wanted it on its own interface, an external 50.x.x.x address, and to keep everything else on my internal network, 192.x.x.16 and 192.x.x.116.  This includes owncloud which is on the 192.x.x.16 network.  Iredmail with postfix, dovecot and pgsql all worked and owncloud worked as well.  iredmail is using Nginx and owncloud apache2.  All was fine after I coded the external 50.x.x.196 network with the gaeway on 50.x.x.198 mask 255.255.255.248 and added a routing statement.

Then I noticed that my timemachine backups were failing.  They use the ubuntu server with netatalk expecting it on 192.x.x.16.  In checking that, I then found smb wasn't working - can't see it on the network or add any shares to windows, mac or ubuntu clients, again on the 192.x.x.16 network. The smb logs have nothing other than startup messages.  UFW is inactive.  It's like the clients are never hitting the smb server code.  Funny thing is though, I can run smbclient to the ip address 192.x.x.16 or hostname on the server and that works!

So I assume this is a networking problem but it escapes me.  I removed the fixed external address, routing, rebooted and took the external 50.x.x.194 adapter down, no changes, it still fails the same way.  I can ping all the addresses and they reply.  I added another interface, 192.x.x.80 and that did't help.

I should also mention that I changed the hostname, but that is not in the local dns and I never use it to address the failing server.  I ssh and smb to the ip address unless I get tired of it and then on the client I will add a line to the hosts file.  I checked all the client 'hosts' files and deleted anything that was related to the old host name.  It's almost like smb has the hostname coded and checking or maybe checking it against another file related to the users?  Or domain name?  I can't figure this one out as like I said, smb isn't logging any errors.  Also, smb is not binding to adapters.  I tested with/without the network adapter bind and it's the same.

Where should I look?

Thanks

Jerry

---

### Post by 21Jerry on 2022-09-27
so iredmail adds nftable rules that rule-out samba.  WTF?  I fixed it by adding the samba ports for now and then I'll have to fix the interfaces as well as roll-back everything else I've tried for the past week!

Anyway, hope this finds someone else in the future.

jerry

---

