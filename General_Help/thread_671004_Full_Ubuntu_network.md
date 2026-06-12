---
title: "Full Ubuntu network"
date: 2008-01-18
forum: General Help
---

### Post by dan0z on 2008-01-18
Hi,

I new to linux and have now completely switched all the computers on my network over to ubuntu :)

So far so good, i am really enjoying the challenge of learning a new OS and set of commands.

My problem/question is this:

I have setup Ubuntu with Samba on one of my machines that i wish to use as a domain controller, i have this up and running and can access all the shares, and can mount the shares on startup. What i would like to be able to do is connect my linux machines to the domain and to the domain at startup so they authenticate with the server when they login?

All the tutorials for Samba just seem to be for connecting MS OS's to a linux domain, there seems to be no information regarding connecting linux machines to a linux domain?

As I said i am new, so do not know if this is possible? If it is I would love some tips to get it working, also if you cannot connect linux to the domain, why?


Thanks

Dan

---

### Post by BillDozer on 2008-01-18
Try and take a look at the LDAP configuration [https://help.ubuntu.com/7.10/server/C/]("https://help.ubuntu.com/7.10/server/C/") is a good starting point for server applications.

---

### Post by dan0z on 2008-01-18
> **BillDozer said:**
> Try and take a look at the LDAP configuration [https://help.ubuntu.com/7.10/server/C/]("https://help.ubuntu.com/7.10/server/C/") is a good starting point for server applications.
Thanks BillDozer,

I have read through the pages in the link you gave me, it is a very good reference point.

Could you please confirm for me: From what I read the Samba  domain controler that i have setup is purley for windows clients. To have a domain that linux machines can connect to i need to setup and configure LDAP with it?

From what I have read LDAP is a more advanced domain controller as it have more features for users and groups and uses OU's which i am used to in Active Directory.

Finally although the explinations are very detailed it does not state how once setup, you configure a client ubuntu machine to connect to the domain on startup.

Thanks

Dan

---

### Post by BillDozer on 2008-01-18
Hi Dan,

As far as I know, SAMBA is mainly used share folders for windows clients (although you also can access these files from linux machines). You should consider using NFS if you only want to share folders between linux machines, this is the native linux way of sharing folders and it is faster than using SAMBA. It is probably even more simple to set up than SAMBA.

Unfortunately I haven't tried myself setting up a LDAP environment yet. But it is what I am aiming to in the end. So I can't help you there.

---

