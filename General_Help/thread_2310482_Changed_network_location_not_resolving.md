---
title: "Changed network location not resolving"
date: 2016-01-19
forum: General Help
---

### Post by jamesisin on 2016-01-19
I have a domain joined Ubuntu 14.04 (x64) machine.  We recently deployed new servers to replace some old ones.  The new servers now have those old server names on our network.  When I attempt to access them (via smb://server/share/) I get an error:

> Oops! Something went wrong.

Unhandled error message: Failed to mount Windows share: Name not unique on network

Windows machines and Mac machines are not having this issue.  What might I flush to resolve this issue?

(Pinging the server by name resolves to the correct IP for the new server.)

---

### Post by jamesisin on 2016-01-19
Looks like this may be a Windows Master Browser issue.  At the very least it's not local to my machine.

I confirmed this is a non-local issue by booting a Live CD (Ubuntu) and receiving the same error when attempting to connect.

---

### Post by bab1 on 2016-01-19
> **jamesisin said:**
> Looks like this may be a Windows Master Browser issue.  At the very least it's not local to my machine.

I confirmed this is a non-local issue by booting a Live CD (Ubuntu) and receiving the same error when attempting to connect.

Check what machine is the master browser for the network and stop the smbd and nmbd for on that host for a few minutes.  The system should elect a new Local Browse Master (BM).  It does sound like the Master Browse List is stale.

I just commissioned 2 new hosts with names of the hosts that decommissioned.  I had the same craziness for a while.

---

### Post by jamesisin on 2016-01-19
Yeah, we are making progress.  We have two offices (one in Costa Rica) and we use Mac mostly but also Windows and a few Ubuntu machines.  The Ubuntu machines are not liking the change at all.  Same goes for Clonezilla; it can't mount our image server now that it has moved (to a new IP).  IP works.  I wonder if there is a way to kick off a network wide re-election/purge.

---

### Post by bab1 on 2016-01-19
> **jamesisin said:**
> Yeah, we are making progress.  We have two offices (one in Costa Rica) and we use Mac mostly but also Windows and a few Ubuntu machines.  The Ubuntu machines are not liking the change at all.  Same goes for Clonezilla; it can't mount our image server now that it has moved (to a new IP).  IP works.  I wonder if there is a way to kick off a network wide re-election/purge.
I would leave it alone.  Mount the shares via IP address for today.  The entire thing is refreshed multiple times during the day.  If you have problems tomorrow, it will be due to misconfigured name services somewhere.

---

### Post by jamesisin on 2016-01-22
Leaving it alone hasn't helped.  It's effecting any Linux system on the network (Ubuntu, Clonezilla, &c).  Can't make that name connect.  Still digging.

---

### Post by bab1 on 2016-01-22
> **jamesisin said:**
> Leaving it alone hasn't helped.  It's effecting any Linux system on the network (Ubuntu, Clonezilla, &c).  Can't make that name connect.  Still digging.
Interesting.  We have gone from not resolving NetBIOS names to not resolving DNS names here.  Clonzilla uses  [s]SSH[/s]  DNS to do it's business.  There is no NetBIOS involved.  

What have you set up to resolve hostnames (i.e. <hostname>) on the LAN and your DNS naming (i.e. <hostname.your-domain.tld>) via the Internet?

FYI, by default Samba uses the *local* hostname (via the /etc/hosts file) to convert its NetBIOS name.  So it is logical to assume that if the hostname is not configured correctly the NetBIOS name may not be correct either.

[COLOR="#0000FF"]Edit:  My mistake above.  Clonzilla does not need SSH but it does need normal name services such as hostnames or DNS [/COLOR]

---

### Post by jamesisin on 2016-01-22
Yeah, the old machines (virtual) have had their NIC's removed so there is no chance they exist on our network.  Yet my Ubuntu laptop throws this error every time I attempt to attach to one of those shares:

[IMG]http://soundunreason.com/slopbucket/oopserror.png[/IMG]

---

### Post by bab1 on 2016-01-22
> **jamesisin said:**
> Yeah, the old machines (virtual) have had their NIC's removed so there is no chance they exist on our network.  

Removing the NIC (whatever that means) does not remove the references to those interfaces.  At this point we are just bemoaning your current situation.  I prefer to diagnose things in a more considered manor.  If you want help in that way let me know.

---

### Post by jamesisin on 2016-01-22
They are VM's.  We can access them through the VMware stack but they have no network cards so they cannot be on any network.

The problem seems to have been centered around the way we were using C names to get to the new shares.  We have tested some registry changes and this ought to fix the matter.  We'll be implementing these registry changes next week to find out for certain.

Thanks for listening to my tale of woe.

---

