---
title: "Connecting to Windows Share using Place-&gt;Network"
date: 2007-10-26
forum: General Help
---

### Post by amsgwp on 2007-10-26
Ok so I want to be able to use the Places->Netowkr option without command lining anything...Why does it not work???

It asks for Username, Domain, Password.

There is NO DOMAIN(workgroup is workgroup).

I know the username and password 100%.  So why does this not work?

I've tried domain has nothing and workgroup to no avail.  Any ideas??

had xubuntu installed gnome 7.10

---

### Post by jusmurph on 2007-10-26
You need SAMBA, beyond that i have no idea sorry.

---

### Post by amsgwp on 2007-10-26
Well I did a SAMBA tutorial(samba was already installed so I just setup the smb.conf).  After that the windows computers can connect and transfer files to the Linux share but the Linux machine still can't connect to the windows computers.  Any ideas?

---

### Post by mahousaru on 2007-10-26
> **amsgwp said:**
> Ok so I want to be able to use the Places->Netowkr option without command lining anything...Why does it not work???

It asks for Username, Domain, Password.

There is NO DOMAIN(workgroup is workgroup).

I know the username and password 100%.  So why does this not work?

I've tried domain has nothing and workgroup to no avail.  Any ideas??

had xubuntu installed gnome 7.10

Usually domain and workgroup are interchangable in this type of situation.  Just insert workgroup in that field.  Where is your window share hosted?  is it a windows box or a samba server?  if it is a samba server have u added a samba password on the samba server?

If not the code is

```

 sudo smbpasswd -a existinglinuxusername

```

The user must exist on the linux server

*EDIT*

Opps I've just read your last post, ignore the last section please!

---

### Post by amsgwp on 2007-10-26
The share is hosted on a windows vista machine and another share is on a windows XP machine, niether work.  The username that is setup on the windows box is also setup on the linux box under samba.  I just did sudo adduser to add the user.  The password for the windows box is only 3 characters so I couldn't add the user using the normal user and group gui.

---

