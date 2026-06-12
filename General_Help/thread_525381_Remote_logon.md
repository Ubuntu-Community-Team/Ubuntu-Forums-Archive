---
title: "Remote logon"
date: 2007-08-14
forum: General Help
---

### Post by Hospadar on 2007-08-14
Hi, I'm wondering where I might want to start to setup some machines so that a group of machines all get their logon credentials from a single machine.

Not really a remote login, but so I can easily handle user accounts.  Also, how would I go about making it so that the users home directory on the fileserver is automatically mounted to the home directory in the local filesystem when they log in (*nix fileserver).

I'm interested in this for the purpose of let's say, setting up classrooms where I need to be able to easily add and remove students and allow students to work from any machine with their settings, data, etc.

I'm not really looking for a full howto, because I'm sure they already exist, but if someone could point me in the direction of which software and guides to use, It would be much appreciated.

---

### Post by renzokuken on 2007-08-14
sounds to me like you need a Domain Controller.

it use samba on your central server machine to allow client machines (windows based) to log onto the domain from any client PC with their own filestore folder and "roaming profiles" if you want.

i just set one up for my office using this guide as a basis (tweaked a few things though)

[http://www.howtoforge.com/samba_domaincontroller_setup_ubuntu_6.10](http://www.howtoforge.com/samba_domaincontroller_setup_ubuntu_6.10)

---

### Post by Hospadar on 2007-08-14
Well I don't want the clients to be windows based, all the machines, server and client will be *nix

---

### Post by renzokuken on 2007-08-14
ahh i see, but what you want is still a domain controller, but it may have to be done with NFS instead.

gimme a sec and i'll see what i can find

---

### Post by woorzel on 2007-08-14
lookup autofs and NFS - this will let you automatically mount a user's home folder via NFS when he logs in to a machine. no need for a domain controller :)

---

