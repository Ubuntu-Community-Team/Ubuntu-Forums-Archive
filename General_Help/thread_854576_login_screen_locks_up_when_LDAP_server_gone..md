---
title: "login screen locks up when LDAP server gone."
date: 2008-07-09
forum: General Help
---

### Post by goathens on 2008-07-09
Hey, I've been using a fresh install of ubuntu 8.04 and using it as an ldap/nfs client to an apple Xserve running the latest leopard.

I followed the directions here:
[https://help.ubuntu.com/community/OSXLDAPClientAuthentication](https://help.ubuntu.com/community/OSXLDAPClientAuthentication)
(that should stave off the need for any huge config file dumps)

The instructions work great when the ldap server is present.  It's just that when the ldap server is rebooting (you know, because a new iTunes means reboot is needed!), network goes down, etc, I can't do a thing with my computer.

I keep a local account for such occasions as loss of the ldap server, so I *should* be able to log in to my local account and use it.  No dice.  The login screen is pretty much locked up, if I was already logged in as a local user, unplug the network (cut off from ldap) and try to use sudo- no dice.  All authentication methods (that I have tried) hang.

The instructions in the link seem to implicate that ldap is sufficient but NOT required- and yet my system is a paperweight when it can't reach the Xserve.  Maybe I am mis-ordering something in nsswitch or pam? I don't know.  Any thoughts?

---

