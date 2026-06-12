---
title: "Giving local user read/write access to a samba mount"
date: 2007-08-28
forum: General Help
---

### Post by jaradronald on 2007-08-28
How can I give a local user read/write access to a mounted samba share?  I've mounted the share with a windows account that has full control over the remote share, but all users on my linux box (besides root) have read-only access to the share...

As a little background info, I'm trying to get OS X & Win 2k3 to play together...  I can't get my G4 laptop to connect to one of my Win Servers, so I'm using the following configuration:

::Window 2k3 Environment:: (winserver)
//winserver/share
User: user01 (Full control over "share")
Password: pass01

::Ubuntu Environment:: (linserver)
adduser user02
passwd user02 pass02
mkdir /home/user02/share
mount -t smbfs -o username=user01,password=pass01,workgroup=home //winserver/share /home/user02/share
(I'm using vsftpd with chroot for local user user02)

::Mac Environment::
[ftp://user02:pass02@linserver/share](ftp://user02:pass02@linserver/share)

Everything is working fine with this "relay" approach, but as I mentioned before I want to give the user on my mac box read/write access (instead of the current read-only setup)...  I've tried assigning user02 to the "root" group, but no luck.  I'm hoping somebody can give me a quick fix for this one.  All the searches I do on "samba share permissions" are giving me results from a server perspective (as opposed to the client side setup in linux that I'm looking for).

Any help is much appreciated.

---

