---
title: "Login timed out after 60 seconds"
date: 2014-11-13
forum: General Help
---

### Post by dilya on 2014-11-13
Booting server Ubuntu 10.04, no GUI installed, only console, inputing **correct** **username**, receiving "[COLOR=#000000][FONT=Tahoma]Login timed out after 60 seconds.". [/FONT][/COLOR]after around a minute with no password prompt. 
Trying with username "root", receiving password prompt, inputing correct password, receiving "[COLOR=#000000][FONT=Tahoma]Login timed out after 60 seconds.", [/FONT][/COLOR]trying incorrect password, also receiving "[COLOR=#000000][FONT=Tahoma]Login timed out after 60 seconds.". [/FONT][/COLOR]Trying several times, always the same output. No upgrades/updates were done. Any ideas what is possibly going on? I have very little sysadmin skills.

---

### Post by TheFu on 2014-11-13
Ubuntu server generally does not have a login allowed for root. You must login as a different userid and use the sudo tool to elevate privileges as needed.  Try the other userid - hopefully you know what it is.

With physical access to the machine, resetting any password is possible, but does require rebooting. There are howtos for this that google will find - the howtogeek version is good and easy.

---

### Post by dilya on 2014-11-14
Other users also tried to login, they get the same result as me.

What do you mean by physical access to the machine?

We brought machine from the server room, all passwords and usernames are configured via LDAP. But I have a feeling that machine is irresponsive even on username, it doesn't recognize any usernames, because when [COLOR=#000000] inputing [/COLOR]**correct [B]username, I receive "[COLOR=#000000][FONT=Tahoma]Login timed out after 60 seconds.". [/FONT][/COLOR]after around a minute with no password prompt.**[/B]

---

### Post by TheFu on 2014-11-14
> **dilya said:**
> Other users also tried to login, they get the same result as me.
Who was able to login to the machine before it was moved?

> **dilya said:**
> What do you mean by physical access to the machine?
Can you touch it? THAT is physical access.  If you cannot touch it, then you do not have physical access.

> **dilya said:**
> We brought machine from the server room, all passwords and usernames are configured via LDAP. But I have a feeling that machine is irresponsive even on username, it doesn't recognize any usernames, because when [COLOR=#000000] inputing [/COLOR]**correct [B]username, I receive "[COLOR=#000000][FONT=Tahoma]Login timed out after 60 seconds.". [/FONT][/COLOR]after around a minute with no password prompt.**[/B]

I think the issue is with the LDAP machine, not this one.  What happened to the machine running LDAP?

---

