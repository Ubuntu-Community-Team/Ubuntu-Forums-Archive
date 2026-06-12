---
title: "Best way to block large lists of ips"
date: 2005-08-03
forum: General Help
---

### Post by g7yh7uj8k on 2005-08-03
With Windows I used Protowall with Bocklist manager. What would be the best way to accomplish the same thing under linux? 

thanks Dave

---

### Post by varunus on 2005-08-03
I think firestarter has some functionality like ip address blocking, don't remember though, its been a while.  You can try it, install it from synaptic.

---

### Post by djmadkins on 2005-08-03
Theres many methods for blocking IP's.

If your aim is to allow only a select list of users you might try the following:

edit your /etc/hosts.deny file and add:

sshd: ALL EXCEPT /etc/hosts.good

The line above serves a few purposes. It only  blocks SSHD access to all (except ip's in your good list) while leaving all other access to whatever other services you may have online.

You would need to create a hosts.good file with a line by line listing of the IP's allowed.

There are other solutions that can run as either a daemon or cron job to assess your logfiles and add entries into hosts.deny based on criteria.. Google DenyHosts

---

### Post by g7yh7uj8k on 2005-08-04
I tried firestarter, but there is no easy way to import large blocks of addresses.
I set it up with shorewall and it seems to work but the blacklist takes forever to load, 
too long to be used on a daily basis. I noticed peerguardian now has a linux version  
but when I used to use that on windows it really hogged cpu and memory. Any other ideas would be greatly appreciated.

thanks Dave

---

### Post by HeavyAl on 2005-08-12
Peerguardian 2 which is now out is amazingly resource friendly. I wish there was a repository that included it so I didnt have to dl and install it by hand (#include laziness_factor).

Just my 2c

---

### Post by bone2006 on 2007-10-15
where is peerguardian for linux?  Their site says they don't have/support linux

[http://phoenixlabs.org/pglinux/](http://phoenixlabs.org/pglinux/)

---

### Post by Cable on 2007-10-15
Try [MoBlock]("http://moblock-deb.sourceforge.net/").

---

