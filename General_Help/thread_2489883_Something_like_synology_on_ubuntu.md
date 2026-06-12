---
title: "Something like synology on ubuntu?"
date: 2023-08-13
forum: General Help
---

### Post by josephchrzempiec on 2023-08-13
Hello, I was curious if there was something like synology that someone from the ubuntu community worked on or made? I'm looking to build my own nas but not a programmer by any means. I just wanted to make it a little easy like the synology software.

Joseph

---

### Post by pqwoerituytrueiwoq on 2023-08-13
There are dedicated projects for this like unraid and truenas

Nothing is stopping you from doing it yourself in ubuntu server, eg setup a raid in md or zfs and enable a samba service (you could run owncloud if want a synced local copy of data), you do not need to be a programmer, but there is a difference between a GIU point and click and a cli interface

---

### Post by TheFu on 2023-08-13
> **josephchrzempiec said:**
> Hello, I was curious if there was something like synology that someone from the ubuntu community worked on or made? I'm looking to build my own nas but not a programmer by any means. I just wanted to make it a little easy like the synology software.

Joseph

I don't have any deep knowledge of commercial NAS systems at the sub-$5000 cost level.  What, specifically, are the features you seek?  

Don't underestimate the effort they've spent to make the addon software "just work".  For many of those things, a snap package version could be used, but it wouldn't be nearly as clean.

As for setting up network shares, that is really very easy with NFS.  Getting CIFS/Samba working for every possible client is much harder. There are so many and many of those clients are only partial, old, implementations of the protocol.  Whereas NFSv4 has been around over 20 yrs now and "just works".

Making resilient storage isn't as easy as it seems.  That's where the commercial NAS vendors get to dictate specific drives, specific models of those drives, to keep the cheapest stuff out of their systems.  Anyone making a home-built NAS probably likes the cheapest disks possible, until they are burned enough times with poor performance or poor lifetimes from that storage.

How many disks are planned?
Will they be external eSATA/Infiniband or Internal SATA/SAS drives?  USB should never be considered.

For your google pleasure, try this search "truenas vs". Think you will find some options and comparisons.  The "vs" seems to be a keyword for comparison pages.

Updates:
Just saw that unraid isn't free.  That's a consideration for many people.  Also, Unraid doesn't guarantee no data lose, so beware about that.  Backups are always (ALWAYS) required, even for RAID1 or RAID10 or RAIDz2 setups.  Get your backups working perfect before adding any RAID at all.

Remember, RAID is for High-Availability and some better performance.  If the system can be unavailable for an hour, then you don't need RAID. Period. Don't waste your time. Backups are 1000x more important.

---

### Post by josephchrzempiec on 2023-08-13
Hello, Thank you for the reply back. I'm looking into owncloud. I have looked and unraid had a hard time using it. same with trunas. Owncloud seems to be a little more user friendly. Thank you.

---

### Post by josephchrzempiec on 2023-08-13
> **pqwoerituytrueiwoq said:**
> There are dedicated projects for this like unraid and truenas

Nothing is stopping you from doing it yourself in ubuntu server, eg setup a raid in md or zfs and enable a samba service (you could run owncloud if want a synced local copy of data), you do not need to be a programmer, but there is a difference between a GIU point and click and a cli interface



[COLOR=#000000][INDENT]Hello, Thank you for the reply back. I'm looking into owncloud. I have looked and unraid had a hard time using it. same with trunas. Owncloud seems to be a little more user friendly. Thank you.[/INDENT]


[/COLOR]
[COLOR=#000000][B][RIGHT][/RIGHT]
[/B][/COLOR]

---

### Post by josephchrzempiec on 2023-08-13
> **TheFu said:**
> I don't have any deep knowledge of commercial NAS systems at the sub-$5000 cost level.  What, specifically, are the features you seek?  

Don't underestimate the effort they've spent to make the addon software "just work".  For many of those things, a snap package version could be used, but it wouldn't be nearly as clean.

As for setting up network shares, that is really very easy with NFS.  Getting CIFS/Samba working for every possible client is much harder. There are so many and many of those clients are only partial, old, implementations of the protocol.  Whereas NFSv4 has been around over 20 yrs now and "just works".

Making resilient storage isn't as easy as it seems.  That's where the commercial NAS vendors get to dictate specific drives, specific models of those drives, to keep the cheapest stuff out of their systems.  Anyone making a home-built NAS probably likes the cheapest disks possible, until they are burned enough times with poor performance or poor lifetimes from that storage.

How many disks are planned?
Will they be external eSATA/Infiniband or Internal SATA/SAS drives?  USB should never be considered.

For your google pleasure, try this search "truenas vs". Think you will find some options and comparisons.  The "vs" seems to be a keyword for comparison pages.

Updates:
Just saw that unraid isn't free.  That's a consideration for many people.  Also, Unraid doesn't guarantee no data lose, so beware about that.  Backups are always (ALWAYS) required, even for RAID1 or RAID10 or RAIDz2 setups.  Get your backups working perfect before adding any RAID at all.

Remember, RAID is for High-Availability and some better performance.  If the system can be unavailable for an hour, then you don't need RAID. Period. Don't waste your time. Backups are 1000x more important.


Hello, Thank you for the reply back. I currently have 4 of the 4TB GHST drives and I have 4of the 1TB samsung vnme drives in a box. I have a second box with the same hardware specs offsite for backup. I have looked at trunas and unraid before But It wasn't very user friendly for someone like myself. I'm looking into owncloud and seems to be a lot better.

Box systems are small 3u servers that was pulled from a datacenter a friend of mine use to work for. All drives are internal, 4 cores 4 threads systems.

---

### Post by TheFu on 2023-08-13
> **josephchrzempiec said:**
> Hello, Thank you for the reply back. I'm looking into owncloud. I have looked and unraid had a hard time using it. same with trunas. Owncloud seems to be a little more user friendly. Thank you.

I use nextcloud, not owncloud, but that isn't an NAS and brings a completely different set of problems.  Best not to compare pears to corn.

---

### Post by ian-weisser on 2023-08-13
> **TheFu said:**
> Get your backups working perfect before adding any RAID at all.

Remember, RAID is for High-Availability and some better performance.  If the system can be unavailable for an hour, then you don't need RAID. Period. Don't waste your time. Backups are 1000x more important.

Thank you for saying this clearly and concisely!

It's so often muddled.

---

