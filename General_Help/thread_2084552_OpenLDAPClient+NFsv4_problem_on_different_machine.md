---
title: "OpenLDAPClient+NFsv4 problem on different machine"
date: 2012-11-15
forum: General Help
---

### Post by borjamf on 2012-11-15
Hi all,

I'm trying to build a lan network for a small group of my university and I need to set up nfsv4 + openldap (kerberos is optional, thanks god). I've started with ubuntu and system administration the last week, but I'm spending too many hours since then. So, this is the problem:

I'm testing with three VM's:
- 12.04 Ubuntu Server LTS 
- 11.04 ubuntu Desktop (Client1)
- 11.04 Ubuntu Desktop (Client2)

I've created two LDAP users (ldapu and ldapu2) and I can login successfully on the Client1, running nfs4 and automount homes without problem. But there is something wrong with the Client2: 
- I can login with LDAP user, but a bit time later three kinds of errors appears: 

 [IMG]http://oi47.tinypic.com/206mvsh.jpg[/IMG]
[IMG]http://oi49.tinypic.com/nd3rt4.jpg[/IMG][IMG]http://oi50.tinypic.com/npqc6q.jpg[/IMG]

How can I fix it?
Thanks all and apologizes for my english.

---

### Post by luvshines on 2012-11-16
Do these errors break anything ?

Maybe those files in the home folder for the respective users are not owned by those user, hence the permission errors and not being able to update

Try this in the home folder for the user
```
# Replace username with your user's name
sudo chown <username>:<username> .ICEauthority
```

Similarly for the other files in nautilus

---

### Post by borjamf on 2012-11-20
Hi, thanks for the answer.

The users of LDAP doesn't 'exists' on the Server machine, but I can login on the clients. 

chown ldapu2:ldapu2 .ICEauthority

-> invalid user

However, with ldapsearch -x or slapcat the LDAP users appear. 

What can I do? Thanks for your help.

---

### Post by luvshines on 2012-11-21
I am having bit confusion

Does invalid user appear on server OR client ?

---

### Post by borjamf on 2012-11-21
It's 'almost' solved. 
ldap: uid 10000 gid 10000
ldapu2: uid 10001 gid 10000

With chown <uid:gid> the folders of /home/<nameldapuser> I can login on the Clients and the Desktop it's running and working, but .ICEauthority error still appears. 

Thanks!

---

### Post by luvshines on 2012-11-21
> **borjamf said:**
> It's 'almost' solved. 
ldap: uid 10000 gid 10000
ldapu2: uid 10001 gid 10000

With chown <uid:gid> the folders of /home/<nameldapuser> I can login on the Clients and the Desktop it's running and working, but .ICEauthority error still appears. 

Thanks!

The reason I asked earlier question was to propose using UID/GID directly, instead of their names, in the chown command, but looks like you already figured that out :)

Anyways, did you check who owns the .ICEauthority file under the users' home folders. If the user doesn't have permission to update those, chown the file for their respective users

---

