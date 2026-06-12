---
title: "What is the Current fashion in distributed authentication"
date: 2021-05-12
forum: General Help
---

### Post by 7-vric-8 on 2021-05-12
I'm looking to move on from NIS to whatever the current fashion is for distributed authentication and auto mount for NFS filesystems. It looks like the current favorite is something based on LDAP but I could use a good how-to if one is available. So far most of the instructions make LDAP authentication look much more complicated than NIS. Hopefully I can find something that's of comparable complexity (or easier).

Suggestions on what authentication tech I should educate myself on would be greatly appreciated.

---

### Post by TheFu on 2021-05-12
Sadly, NIS is 1000x easier than the current solutions.  It is 1,000,000x less secure too. NIS shouldn't have been used the last 20 yrs - at least.

Here's the Ubuntu Server documentation on LDAP :  [https://ubuntu.com/server/docs/search?q=ldap](https://ubuntu.com/server/docs/search?q=ldap)

[https://help.ubuntu.com/community/SingleSignOn](https://help.ubuntu.com/community/SingleSignOn) seems comprehensive, though a little dated.  Their concerns over NFS were valid in 2005.  NFSv4 has Kerberos authentication and encryption. It is considered secure enough for use over the internet.

Canonical has dropped the ball on centralized user management. They haven't made a pretty interface for LDAP management. I don't know why. Their partnership with Microsoft means they generally expect customers with money to use MS-AD.  The 21.04 installer has a way to include a fresh workstation install into the MS-AD infrastructure for a location. No such love for OpenLDAP, I'm sad to say.

In Linux environments, people typically use FreeIPA to add and manage users centrally, but the server doesn't work on Ubuntu systems, only on RHEL and perhaps SuSE. There was a time around 2016-2018 that FreeIPA server did work on Ubuntu, but the RH team keeps moving it forward without constant, immediate, porting to other Linux flavors.  FreeIPA seems to be made up of 50 other projects, each trying to use every exotic language in the world. It is a mess and wants to have a powerful server just for itself.  The good news is that the FreeIPA client for Ubuntu probably works fine.Integrating with AD 

Also, Canonical has gone all-in on Snap packages. On the surface, that seems fine until you learn that **snaps don't work with any NFS storage.** THEY DON'T WORK. This has been a problem since at least 2017 with no effective effort to fix it.  NFS home directories will never support snaps, is Canonical's answer as far as I can see.  You might ask the Canonical Community Rep who joined these forums a few weeks ago for help with this.  I'd love to be wrong, but I'm afraid I am not.

Canonical seems to be about home users and cloud servers, not enterprise infrastructure needs.

IMHO.

---

### Post by 7-vric-8 on 2021-05-14
Sadly I think you're quite on target. I would expand the lack of love for enterprise Linux to include almost any other Linux distribution except for Red Hat, SUSE and Oracle. If I had the time or money, I would probably start a project to patch the holes in NIS and keep it as simple as it is now. I know Sun started NIS plus and it went nowhere.

---

### Post by TheFu on 2021-05-14
> **7-vric-8 said:**
> Sadly I think you're quite on target. I would expand the lack of love for enterprise Linux to include almost any other Linux distribution except for Red Hat, SUSE and Oracle. If I had the time or money, I would probably start a project to patch the holes in NIS and keep it as simple as it is now. I know Sun started NIS plus and it went nowhere.

NIS+ was used all over the place - in Sun Micro shops. The server was only available on Solaris. Most Unix places didn't want vendor lock-in, so they moved to NDS or x.500 directory servers.

There is no fixing NIS. The security architecture is broke.

I'd rather see an OpenLDAP User/Group/Hosts/Netgroups manager that wasn't dependent on a web server and definitely NOT on php or Java. There are a number of LDAP browsers available.  Since I've never seen nor used MS-AD, I don't have a good feel for what they did to become so popular.  

I've used other LDAP-based tools to manage users, groups, and POSIX fields, but at every upgrade, those other tools required removing the LDAP links, doing the upgrade, then manually putting those links back.  It was a huge pain, even with a pretty webGUI.  Some things should have minimal dependencies - user/group/POSIX login fields are definitely in that mandate to me.

---

### Post by rsteinmetz70112 on 2021-05-14
> **TheFu said:**
>   Since I've never seen nor used MS-AD, I don't have a good feel for what they did to become so popular.  


They mandated it for Windows. They continue to push Windows networks to it.

Another option may be to use the SAMBA AD-DC which has some tools to manipulate a DC and can interact with Windows and Linux. I'm playing with it now to migrate my Windows domains. I'm not there yet and definitely don't recommend it but it does combine LDAP, Kerberos and DNS in a single relatively manageable system.

---

### Post by TheFu on 2021-05-14
> **rsteinmetz70112 said:**
>  it does combine LDAP, Kerberos and DNS in a single relatively manageable system.

That sounds like a security nightmare.  DNS has a long history of being hacked. I've been hacked through DNS, in my younger days.

---

